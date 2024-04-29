## [G-01] Use immutable variables for variable that don't change

Using the `constant` and the `immutable` keywords for variables that do not change helps to save on gas used. The reason been that `constant` and `immutable` variables do not occupy a storage slot when compiled. They are saved inside the contract byte code. 

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L60
```solidity
IERC20 public baseToken;
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L7-L8
```solidity
PositionRegistry public registry;
uint256 public vaultId;
```