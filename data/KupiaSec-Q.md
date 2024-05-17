# L-01 Incorrect amounts are emitted 

When adding liquidity to the dex pools, only required amounts are taken by the pool not the input parameters.
However, when emitting event, input parameter are emitted not the correct required amounts.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L72

```solidity
    emit Supply(data.pool, data.amount0, data.amount1);
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L68

```solidity
    emit Withdraw(siloToken, wToken, amount, oC, closePosition); 
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L106

```solidity
    emit Repay(siloToken, rToken, amount);
```

# L-02 Underflows could occur and revert.

When calculating `poolBaseAmount` by utilizing `totalCollateralBase` and `totalDebtBase`, if the collateral value is decreased under some circumstances like price drop, `totalCollateralBase` could be smaller than the `totalDebtBase` and underflow could occur. Hence it will revert.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L116

```solidity
    uint256 poolBaseAmount = totalCollateralBase - totalDebtBase;
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L127

```solidity
    tvl = totalDepositAmount - totalBAmount;
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L154

```solidity
    return _getValue(collateral, base, collateralBalance) - _getValue(debTtoken, base, debtBalance);
```

# L-03 UpdateHoldingPosition should be called when the balance of token of connector is lower than `DUST_LEVEL`
In some connectors, when a keeper contract removes position from the vault, it checks if the balance of a token is `0`. Usually, there are cases that the token can't be removed completely, it is better to remove position from the vault when the balance of token is lower than `DUST_LEVEL`.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L92-L94
```solidity
        if (IERC20(data.pool).balanceOf(address(this)) == 0) {
            registry.updateHoldingPosition(vaultId, positionId, "", "", true);
        }
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L146-L153
```solidity
        if (totalLpBalanceOf(p.poolId) == 0) {
            registry.updateHoldingPosition(
                vaultId,
                registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(p.poolId)),
                "",
                "",
                true
            );
        }
```
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L77-L85
```solidity
        if (IERC20(pool).balanceOf(address(this)) == 0) {
            registry.updateHoldingPosition(
                vaultId,
                registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),
                "",
                "",
                true
            );
        }
```
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L53-L57
```solidity
        if (getCollBlanace(IComet(_market), false) == 0) {
            registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true
            );
        }
```

# L-04 Current Fraxlend codebase has some breaking changes
Details

https://github.com/FraxFinance/fraxlend/blob/main/src/contracts/FraxlendPair.sol#L172-L183
https://github.com/FraxFinance/fraxlend/blob/main/src/contracts/FraxlendPairCore.sol#L109-L115

The codebase of Fraxlend is updated and some function signatures are changed. 
`FraxlendPair.toBorrowAmount()` had two parameters before, but one more parameter is added now.
From `FraxlendPair.exchangeRateInfo()`, `exchangeRate` is removed and `lowExchangeRate`, `highExchangeRate` are added. So the current Frax connector doesn't work for current version of Frax.

# L-05 In the function `Dolomite.sol::openBorrowPosition`, the parameter of `updateHoldingPosition` should be set as `false`
Details

When a keeper borrows from Dolomite, the position should be added to registry.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L72-L74
```solidity
        registry.updateHoldingPosition(
            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true // @audit-issue true -> false
        );
```
