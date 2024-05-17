# NOYA QA REPORT

<details>
  <summary>DISCLAIMER</summary>

---
After spending numerous hours analyzing the Noya codebase, the following Low and Non-critical vulnerabilities have been summarized in this report which we hope would help improve the functionality and operation of the entire protocol. Note that this list is by no means exhaustive. 
Also, no finding in this list has been identified through an automated method.
---
</details>

## LOWS

## [1] Any connector can transfer an arbitrary amount of tokens at any time from another connector by calling `sendTokensToTrustedAddress` from that connector.

**File:** `BaseConnector.sol`

```solidity
if (msg.sender == accountingManager) {
            (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);

            (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
            Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData);

            IERC20(token).safeTransfer(address(accountingManager), newAmount);
            amount = newAmount;
        }
        else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {
 @>           IERC20(token).safeTransfer(address(msg.sender), amount);
        } else {
            uint256 routeId = abi.decode(data, (uint256));
            //note: checks if route is msg.sender
            swapHandler.verifyRoute(routeId, msg.sender);
            if (caller != address(this)) revert IConnector_InvalidAddress(caller);
            IERC20(token).safeTransfer(msg.sender, amount);
        }
```

`sendTokensToTrustedAddress` although being a system design basically allows any Connector address which has been enabled in the system to send out any arbitrary amount of tokens out of other Connector contracts.
This really becomes an issue if access of one of the Connectors becomes compromised, then all other Connectors become at risk. The entire system can be affected arbitrarily by a malicious Connector's actions.

## [2] Allowing the management to completely lose fees whenever the tvl drops drastically can accumulate loss of funds for protocol in long term

**File:** `AccountingManager.sol`

```solidity
function checkIfTVLHasDroped() public nonReentrant {
        uint256 currentProfit = getProfit();
        if (currentProfit < storedProfitForFee) {
            emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
            preformanceFeeSharesWaitingForDistribution = 0;
            profitStoredTime = 0;
        }
    }
```

As part of the `AccountingManager` logic, the system allows the performanceFees gathered for the protocol to be reset once the TVL has dropped more than the previous time of calculating profit. This function can be called by anyone to reset the fees gathered once this condition is met.
While a noble design, this may cause losses to accumulate for the protocol on the long run since if tvl drops by even a very tiny amount, the entire performance fees gathered is completely reset.
It may also be possible (although difficult) for an actor with sufficient resources to directly manipulate the tvl to drop and cause the performance fees to be reset.

## [3] Any connector can transfer any amount of token at any time out of `AccountingManager` which can lead to problems with other processes in the syste

**File:** `AccountingManager.sol`

```solidity
function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
        external
        returns (uint256)
    {

        emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
        if (registry.isAnActiveConnector(vaultId, msg.sender)) {
            IERC20(token).safeTransfer(address(msg.sender), amount);
            return amount;
        }
        return 0;
    }
```

Similar to **[1]** above, any enabled Connector can send out any amount of tokens from the AccountingManager at any time.
This would damage all processes within the AccountingManager including the deposit and withdrawal.
Any malicious Connector can completely damage the protocol functionality .

## [4] `Manager` cannot remove malicious deposits or rearrange the depositQueue

**File:** `AccountingManager.sol`

```solidity
 function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
        public
        onlyManager
        whenNotPaused
        nonReentrant
    {
        uint256 firstTemp = depositQueue.first;
        uint64 i = 0;
        uint256 processedBaseTokenAmount = 0;

        while (
            depositQueue.middle > firstTemp
                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
        ) {
            i += 1;
            DepositRequest memory data = depositQueue.queue[firstTemp];
```

When deposit occurs, the deposit request is added to the depositQueue from which they are processed on a rolling basis. The manager can calculate the shares for each deposit and then run execute on the queue. However, since calculation and execution are done in a loop, this can cause issues for all others in the queue if any deposit request is malicious or faulty. The manager should be allowed to remove malicious requests from the depositQueue.

#### Recommendation

Implement a functionality for the manager to remove any malicious deposit request from the queue.

## [5] `Manager` cannot remove malicious withdraw requests or rearrange the withdraw group

**File:** `AccountingManager.sol`

```solidity
 function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {
        if (balanceOf(msg.sender) < share + withdrawRequestsByAddress[msg.sender]) {
            revert NoyaAccounting_INSUFFICIENT_FUNDS(
                balanceOf(msg.sender), share, withdrawRequestsByAddress[msg.sender]
            );
        }
        withdrawRequestsByAddress[msg.sender] += share;
        withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);
        emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);
        withdrawQueue.last += 1;
    }
```

The withdraw process is executed after creation in a queue which can lead to numerous problems when a malicious request in included into the queue. There is no functionality for a manager to remove malicious request or bloated requests from the queue.

### Recommendation

Implement functionality to remove requests from the queue which may be malicious or spam.

## [6] Execution of the withdraw group in a loop can become very expensive and cause other problems with execution

**File:** `AccountingManager.sol`
Execution of withdraw requests are carried out in a loop like this

```solidity
    currentWithdrawGroup.lastId > firstTemp
                && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
                && i < maxIterations
        ) {
              .............................
        }
```

Considering `AccountingManager` is going to be deployed on ethereum mainnet, calculating and then executing all withdraw requests in the system can end up being very expensive to maintain due to gas fees.
There is no prediction of how many withdraw requests there may be at any time during operation of the system. Overtime, this would accumulate in loss for the protocol and cause long withdraw times, causing huge backlog of unfulfilled withdraw requests. Also, this process can very easily be DOS by a malicious user.

### Recommendation

Consider other methods of processing requests including a pull mechanism for withdrawal, where withdraw requests are calculated and executed when the withdraw owner calls the function once sufficient `withdrawWaitingTime` has passed. This pushes gas use to the user.

## [7] There is no time limit between when deposits are created and when they're calculated by the manager, creating a scenario where users cannot reliable predict how long their deposits would take

**File:** `AccountingManager.sol`
Once users create a deposit request there is a limit of `depositWaitingTime` they must wait before their request can be completed.

```solidity
    uint256 public depositWaitingTime = 30 minutes;
```

However, this is only set after the deposit queue is calculated by the manager. Then the time starts counting towards this waiting time.

```solidity
while (
            depositQueue.middle > firstTemp &&
@>           depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp
            && i < maxI
        )
```

Currently there is no limit set between when a deposit is created and when the deposit is calculated, users have no method of actually estimating when their deposit would be executed and completed. Users also have no mapping they can use to retrieve the time remaining for their deposit to complete.
Considering a users would make use of this protocol for business and many other activities, then this can cause grief to the users of the protocol.

### Recommendation

Consider updating the time of deposit at the point of deposit and then validating this during execution instead of only after calculation

## [8] There is no time limit between when withdraw are created and when they're executed by the manager, causing users to wait longer than the `WithdrawWaitingTime` for their withdrawn assets

**File:** `AccountingManager.sol`

Similar to **[7]** above, users have a limit of waiting time before their withdraw requests can be executed or fulfilled.

```solidity
    uint256 public withdrawWaitingTime = 6 hours;
```

This is however not recorded at withdraw request creation but rather after calculating the assets by the manager. It is important to note that withdraw requests may not be calculated if there is a currentWithdrawGroup which has not be completed. Therefore users really have no means of predicting when a withdraw request they make would be completed. This would cause grief to users of the protocol who really on smooth functionality for deposit and withdraw.

### Recommendation

Consider updating the time of withdraw at the point of deposit and then validating this during execution instead of only after calculation.

## [9] Not allowing the manager to manually end a `currentWithdrawGroup` and start a new one unless it is completely executed leads to numerous problems and can cause withdraw by legit users to be griefed

**File:** `AccountingManager.sol`
In the current implementation, once a manager starts the `currentWithdrawGroup`, there is no way to end or skip over this group until the withdraw group is executed or fulfilled

```solidity
function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
        require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);
        currentWithdrawGroup.isStarted = true;
        currentWithdrawGroup.lastId = withdrawQueue.middle;
        emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);
    }
```

This prevents any more withdraw group from being started and therefore all withdraw requests after that withdraw group can never be completed. There are numerous issues that may occur while a `currentWithdrawGroup` is being fulfilled and some of these include complete DOS of the system, or even withdraw groups with bloated withdraw requests. Once a `currentWithdrawGroup` bricks, the entire system is DOSsed forever.
Even attempts by the manager to `resetMiddle` of the `currentWithdrawGroup` would fail.

```solidity
 function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager {
    ...........................................................
     if (newMiddle > withdrawQueue.middle || newMiddle < withdrawQueue.first || currentWithdrawGroup.isStarted) {
                revert NoyaAccounting_INVALID_AMOUNT();
            }
            .......................................
```

### Recommendation

- The manager should be able to manually end the `currentWithdrawGroup` if it proves to be malicious or encounters problems with that group.

## [10] uniswapV3 slot0 price is used to getPositionTvl in `UNIv3Connector` which is prone to manipulation.

**File:** `UNIv3Connector.sol`
To get the position tvl in the `UNIv3Connector`, the `sqrtPriceX96` is used to calculate the liquidity of the tokens in the position.

```solidity
    @>        (uint160 sqrtPriceX96,,,,,,) = pool.slot0();
```

`sqrtPriceX96` are vulnerable to manipulation by a malicious actor with control of a pool or with sufficient resources. Therefore the tvl can possibly be manipulative if the `UNIv3Connector` is being used.

### Recommendation

- Implement the twap feature from Uniswap instead of directly using the sqrtPriceX96 to reduce risks of manipulation

## [11] Execution of deposits in a loop can become very expensive and cause other problems with execution

Deposit requests are calculated and executed in a loop using a push mechanism rather than a pull mechanism. Therefore the entire gas costs of processing requests is spent by the protocol.

This may become very expensive for the protocol time and lead to accumulation of deposit backlogs

### Recommendation

- Implement a pull mechanism rather than a push mechanism in the execution of deposits

## [12] `BaseConnector::executeSwap` would revert if any of the amounts for any token is 0.

**File:** `BaseConnector.sol`

Execution of swaps in `BaseConnector` is done in a loop, any error in the execution of any swap would result in all other swap for the other tokens reverting.

```solidity
 function swapHoldings(
        address[] memory tokensIn,
        address[] memory tokensOut,
        uint256[] memory amountsIn,
        bytes[] memory swapData,
        uint256[] memory routeIds
    ) external onlyManager nonReentrant {

        //audit: If the amountsIn for any token is 0 this whole function reverts
        for (uint256 i = 0; i < tokensIn.length; i++) {
            _executeSwap(
                SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
            );
```

```solidity
src:  SwapAndBridgeHandler::executeSwap

        if (_swapRequest.amount == 0) revert InvalidAmount();
```

## [13] `BaseConnector` should implement the erc165 interface in the BaseConnector to ensure any connector which inherits from it is completely compatible with it.

**File:** `BaseConnector.sol`
ERC165 is a standard which standardizes how a contract's interface is identified and how it is meant to interact.
The `BaseConnector` is a contract inherited by all connectors in the protocol, which constitute very important parts of the system.
Implementing erc165 in the BaseConnector would make it possible for identification of all Connectors in the system and make interaction between these connectors more seamless.

## [14] Eligible users in `GenericSwapAndBridgeHandler` can be added but cannot be removed by the maintainer or emergency.

**File:** `GenericSwapAndBridgeHandler.sol`

Users can be added to the swapHandler but can never be removed. Once a user is set as eligible, this cannot be revoked.

```solidity
 function addEligibleUser(address _user) external onlyMaintainerOrEmergency {
        isEligibleToUse[_user] = true;
        emit AddEligibleUser(_user);
    }
```

It should be possible for the maintainer or emergency to remove users if they become malicious

### Recommendation

- Implement a method for admin addresses to remove users just as they were added.

## [15] Routes in `GenericSwapAndBridgeHandler` should be removeable by the maintainer or emergency

**File:** `GenericSwapAndBridgeHandler.sol`

Similar to **[14]**, routes can be added in the swapHandler but can never actually be removed once added

```solidity
 function addRoutes(RouteData[] memory _routes) public onlyMaintainer {
        for (uint256 i = 0; i < _routes.length;) {
            routes.push(_routes[i]);
            emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);
            unchecked {
                i++;
            }
        }
    }
```

### Recommendation

- Admin addresses should be able to remove routes from the routes array

## [16] Looping over all current positions when getting the position tvl can be expensive and gas-intensive. Depending on number of positions this can be DOSsed

**File:** `TvlHelper.sol`

```solidity
 function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
        uint256 totalTVL;
        uint256 totalDebt;
        HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
        for (uint256 i = 0; i < positions.length; i++) {
            if (positions[i].calculatorConnector == address(0)) {
                continue;
            }
            uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);
            bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);
            if (isPositionDebt) {
                totalDebt += tvl;
            } else {
                totalTVL += tvl;
            }
        }

```

In the `TvlHelper` in other to get the tvl of a vault, all holding positions are retrieved from the vault and then calculated within a loop.
Depending on the number of positions in that vault, this process can be very expensive considering this function is used frequently in other very important parts of the system.

## [17] `WETH_Oracle` does not implement `INoyaValueOracle` interface.

**File:** `WETH_Oracle.sol`

```solidity
contract WETH_Oracle {
  //
}
```

The `WETH_Oracle` does not implement the `INoyaValueOracle` interface. Being part of the value oracles and considering that all oracles in the system rely on the `INoyaValueOracle` interface, this may cause incompatibility if the `WETH_Oracle` is to be used.

### Recommendation

- The `WETH_Oracle` should inherit from the `INoyaValueOracle` interface

## [18] Encoding the WETH_Oracle answer as 1e18 can cause problems when calculating value.

**File:** `WETH_Oracle.sol`

```solidity

    function latestRoundData()
        external
        view
        returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)
    {
 @>      return (0, 1e18, 0, block.timestamp, 0);
    }
}
```

It may be problematic to hardcode the price of WETH in the oracle as 1e18, since there may be slight differences between the prices of WETH and ETH and extreme market scenarios.

## [19] The `AccountingManager` for a vault can never be changed.

**File:** `Registry.sol`

```solidity
function changeVaultAddresses(
        uint256 vaultId,
        address _governer,
        address _maintainer,
        address _maintainerWithoutTimelock,
        address _keeperContract,
        address _watcher,
        address _emergency
    ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {
        // audit: the AccountingManager can never be changed
        .......................................
```

The `AccountingManager` can never be changed once set by the `Registry`. In cases of emergency or a malicious `AccountingManager` then it should be possible to change the contract by a trusted admin.

## [21] `Vault` struct does not implement all parameters in documentation

**File:** `IPositionRegistry.sol`

The `Vault` struct is implemeneted in `IPositionRegistry.sol#L39-L70`. However there are various discrepancies between the `params` in the _Natspec_ and what is actually contained in the struct.

Some of the `params` listed in the _Natspec_ include the `VaultManager` and `StrategyContract`.

It is recommended that either the _Natspec_ or the Vault is corrected to completely correlate.

## [22] The placeholder of ETH being `address(0)` in `ChainlinkOracleConnector` can cause problems with other aspects of the protocol.

**File:** `ChainlinkOracleConnector.sol`

Currently, the placeholder for `ETH` is address(0) while the placeholder for `USD` is address()

```solidity
    address public constant ETH = address(0);
    address public constant USD = address(840);
```

This can create scenarios in other parts of the system where a token return address(0) i.e. not implemented may be mistaken for being ETH.

It is recommended to change the placeholder for `ETH` to the standard `0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE` instead.

## [23] Allowing the price threshold of chainlink to be set up to 10 days can create arbitrage opportunities

**File:** `ChainlinkOracleConnector.sol`

The price threshold for chainlink answers is allowed to be altered between 1 hour and 10 days.

```solidity
    function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {
       if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {
           revert NoyaChainlinkOracle_INVALID_INPUT();
       }
       chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold;
       emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
   }

```

Chainlink pricefeeds are usually updated every hour. Therefore, if the threshold is ever set even above 24 hours, then arbitrage opportunities would be possible.

It is recommended to limit the threshold which the maintainer can set between 1 hour and 24 hours

## NC/INFO

## [1] Missing 0 address checks in critical aspects of the system
When setting some very important addresses in the system, several instances exist where the function parameter is not check for address(0).

```solidity
src: Registry.sol
 function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {
        emit updateFlashloanAddress(_flashLoan, flashLoan);
        flashLoan = _flashLoan;
   }

```



## [2] Difference in filename and contract name in `Registry.sol`

```solidity
 src: Registry.sol
 contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

## [3] `vaults[vaultId]` should be cached once in `Registry::changeVaultAddresses` to save gas

```solidity
src: Registry::changeVaultAddresses
       ..........................
        vaults[vaultId].governer = _governer;
        vaults[vaultId].maintainer = _maintainer;
        vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock;
        vaults[vaultId].keeperContract = _keeperContract;
        vaults[vaultId].watcherContract = _watcher;
        vaults[vaultId].emergency = _emergency;
        emit VaultAddressesChanged()
        .....................
```

## [4] Discrepancy in access control mechanism in `PositionRegistry`

An example is `Registry.addTrustedPosition` which is only callable by the `maintainerWithoutTimeLock` address and `Registry.removeTrustedPosition` which is callable by the `maintainer` which is a different address

## [5] Use of same function name in the same contract can be confusing for users and other devs

#### instances:

File: `NoyaValueOracle.sol`

- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L81
- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L95

File: `NoyaValueOracle.sol`

- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L293
- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L335

## [6] When 2 arrays are accepted in a function, it is recommended to first check if both array lengths match before carrying out execution with them

```solidity
src: BaseConnector.sol

function swapHoldings(
        address[] memory tokensIn,
        address[] memory tokensOut,
        uint256[] memory amountsIn,
        bytes[] memory swapData,
        uint256[] memory routeIds
    ) external onlyManager nonReentrant {
        //audit-info: Should first check if they all have same length
```

Other instances

- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L169
- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70

## [7] Routes can be added multiple times in `GenericSwapAndBridgeHandler`

Routes being added is not checked for whether it already exists before adding it to the `routes` array

```solidity
 function addRoutes(RouteData[] memory _routes) public onlyMaintainer {
        for (uint256 i = 0; i < _routes.length;) {
            routes.push(_routes[i]);
            emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);
            unchecked {
                i++;
            }
        }
    }
```

## [8] Wrong parameter documentation in various parts of the system


## [9] `Governer` should be corrrected to `Governor` in `Registry` and `IPositionRegistry`

```solidity
src: Registry.sol

    bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE");

```
