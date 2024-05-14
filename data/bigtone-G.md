
## Summary
Once isAnActiveConnector(vaultId, receiver) is false, it should be reverted.

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