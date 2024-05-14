
# G1. Once isAnActiveConnector(vaultId, receiver) is false, it should be reverted.

##
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol#L70~L88
```diff
-    if (!(caller == keeperContract)) {
+    if (!(caller == keeperContract) || !registry.isAnActiveConnector(vaultId, receiver)) { 
        revert Unauthorized(caller);
    }
-    if (registry.isAnActiveConnector(vaultId, receiver)) {
        for (uint256 i = 0; i < tokens.length; i++) {
            // send the tokens to the receiver
            tokens[i].safeTransfer(receiver, amounts[i]);
            amounts[i] = amounts[i] + feeAmounts[i];
        }
        for (uint256 i = 0; i < destinationConnector.length; i++) {
            // execute the transactions
            (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
            require(success, "BalancerFlashLoan: Flash loan failed");
        }
        for (uint256 i = 0; i < tokens.length; i++) {
            // send the tokens back to this contract
            BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
        }
-    }
```

# G2. Remove the unnecessary approval

[mintOrBurnSUSD](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol#L114)
```diff
    function mintOrBurnSUSD(
        uint256 _amount,
        uint128 _accountId,
        uint128 poolId,
        address collateralType,
        bool mintOrBurn
    ) public onlyManager {
        // Mint or burn
        address usdToken = SNXCoreProxy.getUsdToken();
        if (mintOrBurn) {
            SNXCoreProxy.mintUsd(_accountId, poolId, collateralType, _amount);
        } else {
-            _approveOperations(usdToken, address(SNXCoreProxy), _amount); // @audit it doesn't need?
            SNXCoreProxy.burnUsd(_accountId, poolId, collateralType, _amount);
        }
        _updateTokenInRegistry(collateralType);
        _updateTokenInRegistry(usdToken);
    }
```


# G3. isTokenTrusted should be checked first before withdraw or approve
[supply](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol#L31)
[withdrawOrBorrow](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol#L50)

# G4. [getCollBlanace](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol#L102)
```diff
-   CollValue += principalInBase;
+   CollValue = principalInBase;
```

# G5. [openCurvePosition](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L128~L148)
```diff
-    if (poolInfo.tokens.length == 2) {
-        uint256[2] memory amounts;
-        amounts[depositIndex] = amount;
-        ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
-    } else if (poolInfo.tokens.length == 3) {
-        uint256[3] memory amounts;
-        amounts[depositIndex] = amount;
-        ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
-    } else if (poolInfo.tokens.length == 4) {
-        uint256[4] memory amounts;
-        amounts[depositIndex] = amount;
-        ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
-    } else if (poolInfo.tokens.length == 5) {
-        uint256[5] memory amounts;
-        amounts[depositIndex] = amount;
-        ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
-    } else if (poolInfo.tokens.length == 6) {
-        uint256[6] memory amounts;
-        amounts[depositIndex] = amount;
-        ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
-    }

+    uint256[] memory amounts = new uint256[](poolInfo.tokens.length);
+    amounts[depositIndex] = amount;
+    ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);

```
