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

# Unsafe casting to uint128

## Link

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L61

## Description

In the UniswapValueOracle contract, the `getValue()` function is used to determine the value amount of tokenIn to base token. However, the `amount` is unsafely casted from uint256 to uint128. Meaning that any amount above uint128 will be inaccurate and thus return lower amounts of base token.
This will break the system's profit calculation.

Consider using safecast or making sure the amount is indeed lower than `type(uint128).max`.

# Unsafe casting from int to uint

## Links
 https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L124

## Details

The fetched price from chainlink oracle is a int which can be negative in some rare occasion. If a negative int is unsafely casted to a uint it will overflow and return a humongous number.
This will break the system's profit calculation.

## Mitigation route

Make sure the fetched price is >= than 0 before casting unsafely

```diff
    function getValueFromChainlinkFeed(
        AggregatorV3Interface source,
        uint256 amountIn,
        uint256 sourceTokenUnit,
        bool isInverse
    ) public view returns (uint256) {
        int256 price;
        uint256 updatedAt;
        (, price,, updatedAt,) = source.latestRoundData();
+       require(price >= 0, "negative price ... revert ...");
        uint256 uintprice = uint256(price);
```

# The current registry is missing missing a replacement contract for AccountingManager on side chains

## Links

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L108-L110

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L84-L90

## Details

`AccountingManagers.sol` are only deployed on basechain only. But in order to add a vault to the registry we should provide an "AccountingManager.sol", the current system is missing a replacement contract.

## Impact

Currently the system cannot be correctly deployed on side chains, this severely limits the protocol. 
This will impact the position monitoring in the `BaseConnector`

A new type of contract has to be designed before expansion on side chains can be achieved. 



## Proof of Concept

When [adding a new Vault](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L108-L110) in the `registry` the address of the accountManager is supposed to be provided.


```solidity
function addVault(
        uint256 vaultId,
        address _accountingManager,
```
This is however not possible on side chains because AccountingManagers will only be deployed on base chain only.

Actions performed in the BaseConnector require a registered AccountingManager in order to manage vault position appropriately. Such as sending tokens, swaps ect.


## Mitigation Route

In order to mitigate this issue craft an appropriate contract that would replace AccountingManager.
It should be a contract that fetches the `TVL` only, the withdrawals and deposits handling can be skipped.

# Typos

here are a few typos that I spotted.

**CurveConnector**

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L208-L209

appears many times in throughoutt that very contract  

```solidity
     * @param depostiToken - Prisma pool address

```

**CompoundConnector**

`    function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) {`

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L95

**AccountingMananger**

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L52

```solidity
    uint256 public preformanceFeeSharesWaitingForDistribution;
```

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L185

```solidity
/// @notice _update is an internal function that is used to update the balances of the users in ERC20 statndard 
```
Here should be user's in ERC20 standard