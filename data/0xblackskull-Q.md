### [L-1] Incorrect event emission in `GenericSwapAndBridgeHandler::setEnableRoute`
The function `setEnableRoute` is designed to update the status of a route by enabling or disabling it. However, the event emitted upon updating the route status incorrectly always sets the event parameter to `false`, regardless of the actual status.
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160
```
- emit RouteUpdate(_routeId, false);
+ emit RouteUpdate(_routeId, enable);
```
### [L-2] `_slippageTolerance` can be set 100% or greater than 100% in `setGeneralSlippageTolerance` and `setSlippageTolerance`
Make a constant MAX_SLIPPAGE_TOLERANCE and use require statement to check 
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L60
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L74
```
require(_slippageTolerance < MAX_SLIPPAGE_TOLERANCE)
```
### [L-3] Missing array length check
BaseConnector::transferPositionToAnotherConnector
BaseConnector::addLiquidity
BaseConnector::swapHoldings
ChainlinkOracleConnector::setAssetSources
NoyaValueOracle::updateAssetPriceSource
PositionRegistry::addConnector
### [L-4] Missing Pool Existence Check in `BalancerConnector::openPosition` and `UNIv3Connector::_getPositionTVL
We can add this line after getPool()
```
require(pool != address(0), "pool doesn't exist");
```
