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

## In `AccountingManager` the `CalculateDeposit` and `ExecuteDeposit` events are wrongly emitted

## Impact
The parameters in the `CalculateDeposit` and `ExecuteDeposit` when emitting from `AccountingManager` are misplaced, which when emitted will display wrong informations.

## Code
In the `IAccountingManager` the following events looks like this :
`CalculateDeposit` event :
```javascript
    event CalculateDeposit(
        uint256 depositId, address receiver, uint256 recordTime, uint256 amount, uint256 shares, uint256 sharePrice
    );
```
https://github.com/code-423n4/2024-04-noya/blame/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L117-L119

`ExecuteDeposit` event:
```javascript
    event ExecuteDeposit(
        uint256 depositId, address receiver, uint256 recordTime, uint256 amount, uint256 shares, uint256 sharePrice
    );
```
https://github.com/code-423n4/2024-04-noya/blame/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L121-L123C7

When emitting event in `AccountingManager::calculateDepositShares` the parameters are placed like this:
```javascript
            emit CalculateDeposit(
                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
            );
```
https://github.com/code-423n4/2024-04-noya/blame/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L242-L244
And when emitting event in `AccountingManager::executeDeposit` the parameters are placed like this:
```javascript
            emit ExecuteDeposit(
                firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
            );
```
https://github.com/code-423n4/2024-04-noya/blame/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L274-L276
The issue is that place of shares and amount are misplaced resulting that events emit wrong information's.
## Recommendations
This would be the right way to emit the following events :
`CalculateDeposit` event :
```diff
-            emit CalculateDeposit(
-                middleTemp, data.receiver, block.timestamp, shares, data.amount,  shares * 1e18 / data.amount
            );
+            emit CalculateDeposit(
+                middleTemp, data.receiver, block.timestamp, data.amount, shares,  shares * 1e18 / data.amount
            );
```
`ExecuteDeposit` event:
```diff
-            emit ExecuteDeposit(
-                firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
            );
+            emit ExecuteDeposit(
+                firstTemp, data.receiver, block.timestamp, data.amount, data.shares, data.shares * 1e18 / data.amount
            );
```