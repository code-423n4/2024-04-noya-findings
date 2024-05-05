# `LZHelperSender::updateTVL()`
## Impact
`LZHelperSender::updateTVL()`missing event sending
```js
    function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
        if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();


        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
        bytes memory data = abi.encode(vaultId, tvl, updateTime);
@>        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
    }
```
## Proof of Concept
## Tools Used
Manual Review
## Recommended Mitigation Steps
Add event sending code


# `SwapAndBridgeHandler::setEnableRoute()`
## Impact
`SwapAndBridgeHandler::setEnableRoute()` emit RouteUpdate(_routeId, false);` regardless of the call
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L157-L161
```js
    ///@notice disables the route  if required.
    function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {
        routes[_routeId].isEnabled = enable;
        emit RouteUpdate(_routeId, false);
    }
```
But when we look at the following call of the test content, we will find that the call to this method is not limited to `disables the route`, so when the following call occurs, the wrong event is emitted
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/testFoundry/utils/testStarter.sol#L103
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/testFoundry/testSwapHandler.sol#L99
```js
@>        swapHandler.setEnableRoute(0, true);
```
## Proof of Concept

## Tools Used
Manual Review
## Recommended Mitigation Steps
```diff
    ///@notice disables the route  if required.
    function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {
        routes[_routeId].isEnabled = enable;
-        emit RouteUpdate(_routeId, false);
+        emit RouteUpdate(_routeId, enable);
    }
```