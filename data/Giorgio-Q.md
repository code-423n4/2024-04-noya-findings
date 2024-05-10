# Unnecessary token approval when withdrawing collateral 

## Links

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L45-L48

## Details

There is a futile token approval when withdrawing collateral. 

```solidity

    function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
        // Deposit
        _approveOperations(_token, address(SNXCoreProxy), _amount);
```

Consider removing it.


# Excessive Aura tokens approval prior to deposit.

## Link

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L102-L111

## Details

The function `openPosition` in the `BalancerConnector.sol` contract allows to deposit aura tokens. Here is that the amount of aura tokens approved don't match the amount deposited. The connector will approve the total current balance of aura but only sending auraAmount. 

Consider approving auraAmount only.   


# addLiquidityInMaverickPool has to create a new position in order to add liquidity

## Links

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L98-L100

## Details

The `addLiquidityInMaverickPool()` function in the MaverickConnector has the ability to create a new liquidity position but not to add liquidity to an already existing position because `id` is hardcoded to 0, which creates a new position by default.


```solidity
(tokenId,,,) = IMaverickRouter(maverickRouter).addLiquidityToPool{ value: sendEthAmount }(
  @>              p.pool, 0, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline
            );
```

Consider adding a tokenId param to the `MavericAddLiquidityParams` struct. This will enable the protocol to increase an already existing position without needing to create a new one. 

