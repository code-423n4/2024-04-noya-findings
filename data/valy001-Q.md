Function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) in AccountingManager may changer the modifier from view to pure since no state variables are accessed. 
 https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L649
```solidity
- function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory)
+ function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public pure returns (address[] memory)
```