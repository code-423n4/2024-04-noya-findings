## In `GenericSwapAndBridgeHandler::setEnableRoute` will emit `RouteUpdate` event that is always false

## Code
https://github.com/code-423n4/2024-04-noya/blame/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L157-L161

```javascript
    ///@notice disables the route  if required.
    function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {
        routes[_routeId].isEnabled = enable;
        emit RouteUpdate(_routeId, false);
    }
```
The function `setEnableRoute` when updating route will always emit false in `RouteUpdate` event because it is hardcoded to `false`.

## Recommendation
To correctly emit `RouteUpdate` event it should be set to emit `enable` parameter (which can be true or false, which will tell if route is enabled or not) instead of `false`.
```diff
    ///@notice disables the route  if required.
    function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {
        routes[_routeId].isEnabled = enable;
-        emit RouteUpdate(_routeId, false);
+        emit RouteUpdate(_routeId, enable);
    }
```