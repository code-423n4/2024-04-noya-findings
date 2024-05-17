# The Owner of the LZHelpers would not be the expected owner.
## Summary & Impact
The  `LZHelperReceiver` & `LZHelperSender` Inherit from the `OAppReceiver` & `OAppSender` respectively The issue is that the owner specified on the call to the constructor will not be the owner of the helper contracts:

[LZHelperReceiver.sol#L31-L31](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31C5-L31C98)
```solidity
constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }
```
[LZHelperSender.sol#L29-L29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L29C1-L29C96)
```solidity
    constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
```
The issue is that the `LZHelpers` make use of the `OpenzeppelinV5.0` ownable contract meanwhile the LayerZero contracts make use of the `OpenzeppelinV4.8.1` ownable contract.
The difference is that on v5.0 the owner is specified but on v4.8.1 the owner is the msg,sender.
- https://github.com/LayerZero-Labs/LayerZero-v2/blob/1fde89479fdc68b1a54cda7f19efa84483fcacc4/oapp/package.json#L16
- https://github.com/LayerZero-Labs/LayerZero-v2/blob/1fde89479fdc68b1a54cda7f19efa84483fcacc4/oapp/package.json#L17

When the LZHelper contracts are deployed the owner will be the deployer and not the specified owner called in the constructor
## Mitigation
Adjust the ownable contracts to match the same one used by layer zero