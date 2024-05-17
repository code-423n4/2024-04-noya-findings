## Summary

| No | Title |
| --- | --- |
| [L-01] | In GenericSwapAndBridgeHandler.sol, An eligible user's privilege cannot be revoked |
| [L-02] | In Stargate connector, lack of integration with emergency withdraw |
| [L-03] | `MaverickConnector::addliquidity` hardcode nft token ID as 0  |
| [L-04] | In `AccountManager.sol`, change of deposit and withdraw waiting time applies to active deposit and withdraw request |
| [L-05] | Miss match calculation of `currentPositionLTV` to FraxlendPairCore | 
| [L-06] | In PendleConnector.sol, the code is not compatible with RouterV3 |
| NC-01|  `Watchers::verifyRemoveLiquidity()` has no function body |

## Low findings
### [L-01] In GenericSwapAndBridgeHandler.sol, An eligible user's privilege cannot be revoked
#### Impact
In `GenericSwapAndBridgeHandler` the `onlyMaintainerOrEmergency` role can add users to use the handler but these users are unable to remove from `isEligibleToUse` in future. This will lead to problem is he/she become malicious.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80C1-L83C6

#### Recommendation
Add a function to revoke eligible user's by managers.

### [L-02] In StargateConnector, lack of integration with emergency withdraw
#### Impact
In StargateConnector contract, lack of integration with emergency withdraw like the Stargate implement onchain here: https://etherscan.io/address/0xB0D502E938ed5f4df2E681fE6E419ff29631d62b#code#F1#L184

#### Recommendation
Implement this function in the StargateConnector:
https://etherscan.io/address/0xB0D502E938ed5f4df2E681fE6E419ff29631d62b#code#F1#L184


### [L-03] `MaverickConnector::addliquidity` hardcoded nft token ID as 0
#### Impact
In `MaverickConnector::addliquidity` hardcoded the nft token ID as 0 which means the contract cannot increase the liquidity for a minted NFT ID.

NFT ID should be chosen as input params to increase the liquidity of already minted NFT.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L98C13-L100C15

```solidity
        (tokenId,,,) = IMaverickRouter(maverickRouter).addLiquidityToPool{ value: sendEthAmount }(
                p.pool, 0, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline
            );  

```
#### Recommendation
Let the NFT ID as input params of the function.
https://docs.mav.xyz/v1-technical-reference/v1-contracts/router#fn-addliquiditytopool

### [L-04] In AccountManager.sol, change of deposit and withdraw waiting time applies to active deposit and withdraw request
#### Impact
`AccountManager::changeDepositWaitingTime` function is used to update the `depositWaitingTime` for deposit requests. But if a certain deposit request is already made and `depositWaitingTime` it will impact the current  request. Similarly `AccountManager::changeWithdrawWaitingTime`  function is used to update the `withdrawWaitingTime` for withdraw requests. But if a certain withdraw request is already made and `withdrawWaitingTime` it will impact the current  request.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L673C1-L681C6

```solidity
    function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {
        depositWaitingTime = _depositWaitingTime;
        emit SetDepositWaitingTime(_depositWaitingTime);
    }

    function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {
        withdrawWaitingTime = _withdrawWaitingTime;
        emit SetWithdrawWaitingTime(_withdrawWaitingTime);
    }
```
#### Recommendation
When there is a deposit/withdraw request already, prevent calling the function.

### [L-05] Miss match calculation of `currentPositionLTV` to FraxlendPairCore
#### Impact
In the `FraxConnector::_getHealthFactor()` the `currentPositionLTV` miscalculated in compared to how FraxlendPairCore already implemented here:
https://etherscan.io/address/0x794F6B13FBd7EB7ef10d1ED205c9a416910207Ff#code#F8#L311

```solidity
        uint256 _ltv = (((_borrowerAmount * _exchangeRate) / EXCHANGE_PRECISION) * LTV_PRECISION) / _collateralAmount;

```
But the `FraxConnector::_getHealthFactor()` is calculated as here:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L128C9-L130C1

```solidity
    function _getHealthFactor(IFraxPair _fraxlendPair, uint256 _exchangeRate) internal view virtual returns (uint256) {
        // calculate the borrowShares
        uint256 borrowerShares = _fraxlendPair.userBorrowShares(address(this));
        uint256 _borrowerAmount = _fraxlendPair.toBorrowAmount(borrowerShares, true);
        if (_borrowerAmount == 0) return type(uint256).max;
        uint256 _collateralAmount = _fraxlendPair.userCollateralBalance(address(this));
        if (_collateralAmount == 0) return 0;
        (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();
@>       uint256 currentPositionLTV =
            (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;

        // get maxLTV from fraxlendPair
        uint256 fraxlendPairMaxLTV = _fraxlendPair.maxLTV();
        if (currentPositionLTV == 0) return type(uint256).max; // loan is small

        // // convert LTVs to HF
        uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;

        // // compare HF to current HF.
        return currentHF;
    }
```
This difference in implement might cause rounding issues in the protocol leading to miscalculation of health factor.

#### Recommendation
Change the following.
```diff
-     uint256 _ltv = (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;
+    uint256 _ltv = (((_borrowerAmount * _exchangeRate) / EXCHANGE_PRECISION) * LTV_PRECISION) / _collateralAmount;
```

### [L-06]  In PendleConnector.sol, the code is not compatible with `PendleRouterV3`
#### Impact
The functions `swapYTForPT()` and `swapYTForSY()` are basically incompatible with the new RouterV3

Similar issue: https://github.com/code-423n4/2024-02-wise-lending-findings/issues/133

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L149C1-L174C6

```solidity
 function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
        external
        onlyManager
    {
        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
        _approveOperations(address(_YT), address(pendleRouter), exactYTIn);
        pendleRouter.swapExactYtForPt(address(this), market, exactYTIn, min, guess);
        emit SwapYTForPT(market, exactYTIn, min, guess);
    }

    /**
     * @notice Swaps Yield Tokens (YT) for Standardized Yield (SY) tokens in a specified market
     * @param market Address of the market
     * @param exactYTIn Amount of YT to swap
     * @param min Minimum amount of SY to receive
     * @param orderData Specifies the type of swap to perform
     */
    function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
        public
        onlyManager
    {
        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
        _approveOperations(address(_YT), address(pendleRouter), exactYTIn);
        pendleRouter.swapExactYtForSy(address(this), market, exactYTIn, min, orderData);
        emit SwapYTForSY(market, exactYTIn, min, orderData);
    }
```
PendleRouterV3 (latest): https://arbiscan.io/address/0x00000000005BBB0EF59571E58418F9a4357b68A0
#### Recommendation
Support only the latest router (V3) or add conditional checks to use the respective selector for each router version.


### [NC-01] `Watchers::verifyRemoveLiquidity()` has no function body.

`Watchers::verifyRemoveLiquidity()` has no function body should be removed. 

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Watchers.sol#L8

```solidity
    function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
```

