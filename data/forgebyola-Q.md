
# LOWS

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
While a noble design, this may cause losses to accumulate for the protocol on the long run since if profit drops by even a very tiny amount, the entire performance fees gathered is completely reset.
It may also be possible (although difficult) for an actor with sufficient resources to directly manipulate the tvl to drop and cause the performance fees to be reset.

## [3] Any connector can transfer any amount of token at any time out of `AccountingManager` which can lead to problems with other processes in the system

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

## [4] Use of `safeTransferFrom` in `AccountingManager::deposit` may fail if deployed on arbitrum and WETH is set as the basetoken

**File:** `AccountingManager.sol`

```solidity

```

## [5] `Manager` cannot remove malicious deposit requests or rearrange the depositQueue

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

## [6] `Manager` cannot remove malicious withdraw requests or rearrange the withdraw group

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

## [7] Execution of the withdraw group in a loop can become very expensive and cause other problems with execution

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

## [8] There is no time limit between when deposits are created and when they're calculated by the manager, creating a scenario where users cannot reliable predict how long their deposits would take

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

## [9] There is no time limit between when withdraw are created and when they're executed by the manager, causing users to wait longer than the `WithdrawWaitingTime` for their withdrawn assets

**File:** `AccountingManager.sol`

Similar to **[8]** above, users have a limit of waiting time before their withdraw requests can be executed or fulfilled.

```solidity
    uint256 public withdrawWaitingTime = 6 hours;
```

This is however not recorded at withdraw request creation but rather after calculating the assets by the manager. It is important to note that withdraw requests may not be calculated if there is a currentWithdrawGroup which has not be completed. Therefore users really have no means of predicting when a withdraw request they make would be completed. This would cause grief to users of the protocol who really on smooth functionality for deposit and withdraw.

### Recommendation

Consider updating the time of withdraw at the point of deposit and then validating this during execution instead of only after calculation.

## [10] Not allowing the manager to manually end a `currentWithdrawGroup` and start a new one unless it is completely executed leads to numerous problems and can cause withdraw by legit users to be griefed

**File:** `AccountingManager.sol

## [11] uniswapV3 slot0 price is used to getPositionTvl in `UNIv3Connector` which is prone to manipulation.

## [12] Execution of deposits in a loop can become very expensive and cause other problems with execution

## [13] `BaseConnector::executeSwap` would revert if any of the amounts for any token is 0.

## [14] `BaseConnector` should implement the erc165 interface in the BaseConnector to ensure any connector which inherits from it is completely compatible with it.

## [15] Eligible users in `GenericSwapAndBridgeHandler` can be added but cannot be removed by the maintainer or emergency.

## [16] Routes in `GenericSwapAndBridgeHandler` should be removeable by the maintainer or emergency

## [17] Looping over all current positions when getting the position tvl can be expensive and gas-intensive. Depending on number of positions this can be DOSsed

## [18] `WETH_Oracle` does not implement `INoyaValueOracle` interface.

## [19] Encoding the WETH_Oracle answer as 1e18 can cause problems when calculating value.

## [20] The `AccountingManager` for a vault can never be changed.

## [21] `Vault` struct does not implement all parameters in documentation

## [22] The placeholder of ETH being `address(0)` in `ChainlinkOracleConnector` can cause problems with other aspects of the protocol.

## NC/INFO

## [1] Missing 0 address checks in critical aspects of the system

## [2] Wrong parameter documentation in various parts of the system

## [3] `Governer` should be corrrected to `Governor` in `Registry`

## [4] Difference in filename and contract name in `Registry.sol`

## [5] `vaults[vaultId]` should be cached once in `Registry::changeVaultAddresses` to save gas

## [6] Discrepancy in access control mechanism in `PositionRegistry`

## [7] Use of same function name in the same contract can be confusing for users and other devs

## [8] When 2 arrays are accepted in a function, it is recommended to first check if both array lengths match before carrying out execution with them

## [9] Routes can be added multiple times in `GenericSwapAndBridgeHandler`

## [10] Wrong event emission in multiple parts of the system

## [11] Allowing the price threshold of chainlink to be set up to 10 days can create arbitrage opportunities

## [12] Chainlink's library should be used directly in `AggregatorV3Interface`

