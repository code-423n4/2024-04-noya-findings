Prefix internal version of `updateHoldingPosition()` in the registry with an underscore to avoid confusion

## ISSUE
**NON-CRITICAL**

 [`Registry.updateHoldingPosition()`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L283-L326) (`internal`) and [`Registry.updateHoldingPosition()`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L328-L366) (`public`) are two functions with the same name. The `internal` function can be prefixed with an underscore to differentiate it from the `public` one that calls it. This helps prevent confusion and makes the code more readable/maintainable.

```diff
- function updateHoldingPosition(
+ function _updateHoldingPosition(
            Vault storage vault,
            uint256 vaultId,
            bytes32 _positionId,
            bytes calldata d,
            bytes calldata AD,
            uint256 index,
            bytes32 holdingPositionId
        ) internal returns (uint256) {
            //...
    }
```

## TOOLS USED

Manual Review

## RECOMMNEDATION

Prefix the internal version of the function with an underscore.


---
---


Setter function and variable name in `GenericSwapAndBridgeHandler` should be consistent

## ISSUE
**NON-CRITICAL**

The function [`setGeneralSlippageTolerance()`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L53) and variable name  [`genericSlippageTolerance`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L16) should be consistent in using either "generic" or "general" to describe the slippage tolerance. This makes the code clearer and more consistent.

```solidity
    //GenericSwapAndBridgeHandler.sol

    //...
    uint256 public genericSlippageTolerance = 50_000; // 5% slippage tolerance
    //...

    /**
     * @notice function responsible for setting the slippage tolerance
     * @param _slippageTolerance uint256 value of the slippage tolerance
     */
    function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {   //@audit - Function and variable name should reflect the same parameter. Either use the word "generic" or "general".
        genericSlippageTolerance = _slippageTolerance;
        emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);
    }

```

## TOOLS USED

Manual review

## RECOMMENDATION

Rename the function or variable for consistency. Either use the word "generic" or "general".


---
---


Inconsistency between the comment and implementation in `ChainlinkOracleConnector.updateChainlinkPriceAgeThreshold()`

## ISSUE

**LOW**

In [`ChainlinkOracleConnector.updateChainlinkPriceAgeThreshold()`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L51), the `@dev` states that "the threshold should be between 1 day and 10 days", while the implementation checks between 1 hour and 10 days.

```solidity
    /*
    * @notice Updates the threshold for the age of the price data
    * @param _chainlinkPriceAgeThreshold The new threshold
    * @dev The threshold should be between 1 day and 10 days
    */
    function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {
        if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) { //@audit - Comment and code are not consistent. Comment is between 1 - 10 days. Code is 1 hour - 10 days.
            revert NoyaChainlinkOracle_INVALID_INPUT();
        }
        chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold;
        emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
    }


```