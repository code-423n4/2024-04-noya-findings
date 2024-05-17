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
