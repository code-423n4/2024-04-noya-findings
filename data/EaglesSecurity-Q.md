## [L-1] Missing event for ```setMaxNumHoldingPositions()``` in Registry.sol

### Impact
The ```setMaxNumHoldingPositions()``` function sets a new storage value to ```maxNumHoldingPositions``` and there is no event and emit for the off-chain monitoring tools to observe this change on-chain.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L79


### Recommended Mitigation Steps
Add a MaxNumHoldingPositions event and then emit at the end of ```setMaxNumHoldingPositions()``` function.


## [L-2] Missing address(0) check in Registry::addVault and Registry::changeVaultAddresses for ```_emergency```.

### Description
In this protocol emergency role is crucial as is going to be used in situations where a position is stuck or another role of NOYA is compromised. In the current implementation of ```addVault()``` and ```changeVaultAddresses()``` is missing address(0)  check for the emergency parameter. This could potentially leave the vault without the protection and functionality of this role in rare cases.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L106-L146
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L158-L181

### Recommended Mitigation Steps
Consider implementing ```require(_emergency != address(0))``` in both of the functions.


## [L-3] Hardcoded ```false``` parameter in emit may lead to confusion

### Description
In GenericSwapAndBridgeHandler.sol the function setEnableRoute() emits RouteUpdate event.  In the emit the second parameter is hardcoded to false. 
This could be a issue since the bool parameter ```enable``` of the function could be true. So the event in some cases will contain wrong information.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L158-L161

### Recommended Mitigation Steps
Consider using ```enable``` besides of ```false``` in the emit.
```emit RouteUpdate(_routeId, enable);```

## [NC-1] Missing natspec for _flashLoan parameter in Registry.sol constructor

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L66 