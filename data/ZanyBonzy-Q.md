## 1. Redundant check in `rescue` function for `ETH`

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691

### Impact
Rescue function holds a check for address(0) token, i.e ETH. But the contract holds no payable or receive function and has no way to receive ETH, making the check redundant.

```solidity
    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { //only emergency manager
        if (token == address(0)) {
            (bool success,) = payable(msg.sender).call{ value: amount }(""); 
            require(success, "Transfer failed.");
        } else {
            IERC20(token).safeTransfer(msg.sender, amount); 
        }
        emit Rescue(msg.sender, token, amount);
    }
```

### Recommended Mitigation Steps
Consider removing the check, or introducing receive() payable function

***

## 2. Introduce a check that token being withdrawn is not `baseToken`

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691

### Impact

The rescue function prevent the withdrawer from withdrawing the baseToken, which can be used maliciously to drain the contract. Should introduce balance checks incase the basetoken is one with multiple addresses. Consider also introducing a receiver parameter to which tokens can be rescued.


```solidity
    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { 
        if (token == address(0)) {
            (bool success,) = payable(msg.sender).call{ value: amount }(""); 
            require(success, "Transfer failed.");
        } else {
            IERC20(token).safeTransfer(msg.sender, amount); 
        }
        emit Rescue(msg.sender, token, amount);
    }
```

***

## 3. Use of a general staleness threshold for multiple chain feeds is not advisable

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L14

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L56

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L125

### Impact
The `chainlinkPriceAgeThreshold` is set to two hours which for certain price feeds might be too small or too large.
```solidity
  uint256 public chainlinkPriceAgeThreshold = 2 hours;
```

While this can be changed, the issue is that whatever parameter is set will be in use for all the price feeds being queried by the contract, so the aforementioned issue about threshold being to large or too small still remains. This can lead to a number of issues when querying prices. For instance, if the price feed is one that is slow to update e.g (most LSTs/ETH feeds), after a certain point, their price become unqueriable because the currently set threshold will be too small for their last update time, if its one that updates very fast, stale prices may be allowed if the oracle for some reason fails to update. 

### Recommended Mitigation Steps
Consider using a more feed specific threshold instead.

***

## 4. Signature should allow more signers than threshold,

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L95

### Impact

The execute function requires that the amount of provided signatures is exactly equal to the threshold. Since, a majority of owner can be potentially interested in execution, it makes more sense to allow as many signatures as possible regardless of the threshold, provided the threshold is met. 
```solidity
    function execute(
        address destination,
        bytes calldata data,
        uint256 gasLimit,
        address executor,
        bytes32[] memory sigR,
        bytes32[] memory sigS,
        uint8[] memory sigV,
        uint256 deadline
    ) public {
        ...
        require(sigR.length == threshold, "Not enough signatures");
        ...
        {
```

### Recommended Mitigation Steps

Consider using the => operator instead.
```solidity
        require(sigR.length == threshold, "Not enough signatures");
```

***

## 5. `setPeriod` should check that `_period` is not less than 1800

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L42


### Impact

The `setPeriod` is used to set uniswap oracle's twap duration and only checks for 0 `_period`. By default, the set period is 1800.

```solidity
    function setPeriod(uint32 _period) external onlyMaintainer { 
        if (_period == 0) revert INoyaValueOracle_InvalidInput();
        period = _period;
        emit NewPeriod(_period); 
    }
```
```solidity
    // Period for the oracle
    uint32 public period = 1800;
```
1800 secs is the typical that is used by [Uniswap](https://blog.uniswap.org/uniswap-v3-oracles) in their studies. This is done because it makes manipulations very expensive and manipulators risk heavy losses. Setting any lower risk actual manipulations taking place as attackers have been known to use their own capital (instead of flash loan) to keep the price manipulated for more than a block, making them vulnerable to arbitrage as shown in [Rari's Fuse hack](https://cmichel.io/replaying-ethereum-hacks-rari-fuse-vusd-price-manipulation/), where the attacker risked their capital and waited for multiple blocks. 
The root cause of that hack was due to price manipulation of the Uniswap V3 TWAP oracle, which had a TWAP duration of 600 secs.

### Recommended Mitigation Steps
Recommended updating the check to ensure period is not less than 1800 seconds.

***

## 6. ChainlinkOracleConnector.sol doesn't check for active sequencer

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L115

### Impact

The protocol aims to deploy on major chains including L2s. But the ChainlinkOracleConnector contract doesn't query for an active sequencer. Chainlink recommends that all L2 oracles consult the Sequencer Uptime Feed to ensure that the sequencer is live before trusting the data returned by the oracle. If the sequencer goes down, the protocol will allow users to continue to operate at the previous (stale) rates

```solidity
    function getValueFromChainlinkFeed(
        AggregatorV3Interface source,
        uint256 amountIn,
        uint256 sourceTokenUnit,
        bool isInverse
    ) public view returns (uint256) {
        int256 price;
        uint256 updatedAt;
        (, price,, updatedAt,) = source.latestRoundData();
        uint256 uintprice = uint256(price);
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
        }
        if (price <= 0) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
        if (isInverse) {
            return (amountIn * sourceTokenUnit) / uintprice;
        }
        return (amountIn * uintprice) / (sourceTokenUnit);
    }
```

### Recommended Mitigation Steps

Include a check for active sequencer.

***

## 7. `setGeneralSlippageTolerance` should ensure slippage cannot be set above 1e6

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L61

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L16

### Impact
GenericSwapAndBridgeHandler.sol sets the default `genericSlippageTolerance` to 5e4, 5%.

```solidity
    uint256 public genericSlippageTolerance = 50_000; // 5% slippage tolerance
```
This value can be changed through the `setGeneralSlippageTolerance` function and can be set to any value, including 0 and greater that 1e6. 

```solidity
    function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {
        genericSlippageTolerance = _slippageTolerance;
        emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);
    }

```

Doing this will dos swap executions.

```solidity
            if (_slippageTolerance == 0) {
                _slippageTolerance = genericSlippageTolerance;
            }
            INoyaValueOracle _priceOracle = INoyaValueOracle(valueOracle);
            uint256 _outputTokenValue =
                _priceOracle.getValue(_swapRequest.inputToken, _swapRequest.outputToken, _swapRequest.amount);

            _swapRequest.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);
        }
```

### Recommended Mitigation Steps
Consider introducing a check that the set tolerance is not > 1e6

***

## 8. User exit functions should not be pausable

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L304

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L328

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L360

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L370

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L396

### Impact

The withdrawal functions in AccountingManager.sol have a `whenNotPaused` modifier meaning that users will not be able to withdraw their tokens if the protocol is paused. This should be avoided as it risks users funds getting trapped in the contract if it is paused for malicious reasons.
### Recommended Mitigation Steps
Remove the `whenNotPaused` modifier from the functions.

***

## 9. Should introduce a `remove_liquidity` function in case curve pool gets killed

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L160-L175
### Impact

`decreaseCurvePosition` function in CurveConnector.sol uses `remove_liquidity_one_coin` function to remove tokens from curve when decreasing position. The issue is that the function is will always revert if `self.is_killed` in the curve pool contract becomes true. This will cause position decrement to become impossible. If the pool is killed permanently, the tokens will be locked forever.
```solidity
    function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
        public
        onlyManager
        nonReentrant
    {
        PoolInfo memory poolInfo = _getPoolInfo(pool);
        address token = poolInfo.tokens[withdrawIndex];
        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));

        ICurveSwap(poolInfo.pool).remove_liquidity_one_coin(amount, int128(uint128(withdrawIndex)), minAmount);
        _updateTokenInRegistry(token);
        if (totalLpBalanceOf(poolInfo) == 0) {
            registry.updateHoldingPosition(vaultId, positionId, "", "", true);
        }
        emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount);
    }
```
### Recommended Mitigation Steps
When killed, it is only possible for existing LPs to remove liquidity via `remove_liquidity`, so introduce a function that queries this to prevent permanent loss of funds.

***

## 10. `harvestAuraRewards`, `harvestConvexRewards`  is not as secure as the protocol might intend.

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L56

https://github.com/aurafinance/convex-platform/blob/6c8abb264022b0f83f8ddd8bec56ddedfd83d741/contracts/contracts/BaseRewardPool.sol#L311-L335

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L250

https://github.com/convex-eth/sidechain-platform/blob/49c1c3e6d216d6c7a64da051d0711b93151d3944/contracts/contracts/ConvexRewardPool.sol#L349
### Impact

The `harvestAuraRewards` in intended to be called by only the manager. It transfers the rewards from aura pool to the contract while updating the token amount in the registry. Aura allows for users to claim [on behalf](https://github.com/aurafinance/convex-platform/blob/6c8abb264022b0f83f8ddd8bec56ddedfd83d741/contracts/contracts/BaseRewardPool.sol#L311) of other users. Users can claim the protocol's aura rewards, the function will succeed without updating token in registry. This defeats the intended access control put in place on the function.

```solidity
    function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
        for (uint256 i = 0; i < rewardsPools.length; i++) {
            IRewardPool baseRewardPool = IRewardPool(rewardsPools[i]);
            baseRewardPool.getReward();
        }
        _updateTokenInRegistry(address(AURA));
    }
```
The same can be observed in `harvestConvexRewards` which can be bypassed by users calling the [getReward](https://github.com/convex-eth/sidechain-platform/blob/49c1c3e6d216d6c7a64da051d0711b93151d3944/contracts/contracts/ConvexRewardPool.sol#L349) directly in the reward pool contract.

```solidity
    function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
        for (uint256 i = 0; i < rewardsPools.length; i++) {
            IConvexBasicRewards baseRewardPool = IConvexBasicRewards(rewardsPools[i]);
            baseRewardPool.getReward(address(this), true);
        }
        _updateTokenInRegistry(CVX);
        _updateTokenInRegistry(CRV);
        emit HarvestConvexRewards(rewardsPools);
    }
```

***

## 11. Balancer flashloans can potentially be dossed by donations

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L89-L93

### Impact

When user makes flashloan in BalancerFlashLoan.sol, the vault calls the `receiveFlashLoan` which executes the loan. AN important part is when the tokens being loaned are sent back to the vault. The function holds a check to ensure that no tokens exist in the contract after the tokens are sent back. This is dangerous because users can dos this by sending at least 1 wei of the tokens being loaned into the contract. Considering the amount + fees being sent back will not necessarily be the token balance of the contract, an extra wei would cause the function to fail, dossing the flashloan process. 

```solidity
    function receiveFlashLoan(
        IERC20[] memory tokens,
        uint256[] memory amounts,
        uint256[] memory feeAmounts,
        bytes memory userData
    ) external override {
        emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
        require(msg.sender == address(vault));
        (
            uint256 vaultId,
            address receiver,
            address[] memory destinationConnector,
            bytes[] memory callingData,
            uint256[] memory gas
        ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
        if (!(caller == keeperContract)) {
            revert Unauthorized(caller);
        }
        if (registry.isAnActiveConnector(vaultId, receiver)) {
            for (uint256 i = 0; i < tokens.length; i++) {
                // send the tokens to the receiver
                tokens[i].safeTransfer(receiver, amounts[i]);
                amounts[i] = amounts[i] + feeAmounts[i];
            }
            for (uint256 i = 0; i < destinationConnector.length; i++) {
                // execute the transactions
                (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
                require(success, "BalancerFlashLoan: Flash loan failed");
            }
            for (uint256 i = 0; i < tokens.length; i++) {
                // send the tokens back to this contract
                BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
            }
        }
        for (uint256 i = 0; i < tokens.length; i++) {
            // send the tokens back to the vault
            tokens[i].safeTransfer(msg.sender, amounts[i]);
            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
        }
    }
```

***

## 12.