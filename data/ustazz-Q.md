### [Non Critical - 1] Potential for Unnecessary Emits

***Description:***
When the function is invoked, it promptly emits an event and subsequently evaluates a condition to determine whether to proceed with an action. If the condition is not satisfied, no action is taken but potentially emit unnecessary event.

**Link to code**

```solidity
File: contracts/accountingManager/AccountingManager.sol#L154-L159

        emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
        if (registry.isAnActiveConnector(vaultId, msg.sender)) {
            IERC20(token).safeTransfer(address(msg.sender), amount);
            return amount;
        }
        return 0;
```

**Recommended Mitigation:**
Move `emit` inside `if` block

