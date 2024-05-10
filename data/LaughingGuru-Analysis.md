1. Incorrect usage of SafeERC20:
   You have imported `SafeERC20` but haven't used it in your contract. `SafeERC20` provides `safeTransfer`, `safeTransferFrom`, and `safeApprove` which you should be using for any ERC20 token operations to ensure they don't fail silently.

2. Missing nonReentrant modifier on some functions:
   Functions like `burnShares` and other sensitive functions that could potentially change the contract state should have the `nonReentrant` modifier to prevent re-entrancy attacks.

3. Unclear if certain revert conditions are met:
   The function `startCurrentWithdrawGroup` checks that both `isStarted` and `isFullfilled` are false. However, there's a missing validation of `withdrawQueue.middle == withdrawQueue.last`. If the withdrawal queue is empty, starting the withdraw group may not make sense.

4. No checks for overflows & underflows:
   Solidity 0.8 introduces checks for arithmetic operations, but if the contract interacts with contracts compiled with an older version, it might be a good idea to add explicit checks or use a library like SafeMath to handle potential over/underflows.

5. Accounting for price manipulation:
   The function `calculateWithdrawShares` uses the TVL to calculate shares in a withdrawal process. If the TVL can be manipulated by an external actor, it could result in unfair calculations. Consider adding mitigations against such manipulations.

6. No use or unclear usage of Pausable contract:
   The contract imports Pausable but does not call `_pause()` or `_unpause()` anywhere. It's essential to have mechanisms to pause contract functions in case of an emergency.

7. Possible DOS attacks in withdrawal:
   The `executeWithdraw()` function could potentially run out of gas if `maxIterations` is too high, due to the while loop processing many withdrawals.

8. Ownership Transferability:
   Neither `AccountingManager` nor `NoyaFeeReceiver` provides a way to transfer ownership or other admin roles. This might be intentional but could also pose a risk if the original owner loses access to their account, or there is a need to upgrade the admin.

9. Missing checks for zero addresses in `sendTokensToTrustedAddress`:
   It would make sense to validate that the `token` and `_caller` parameters are not zero addresses for security reasons.

10. No event emitters for some state-changing functions:
    Some functions which can alter the contract state (such as `burnShares` and `retrieveTokensForWithdraw`) do not emit events. These are beneficial for tracking changes.

11. Lack of interface checks:
    The contract assumes that connectors will have a specific method signature for `addLiquidity` and `sendTokensToTrustedAddress`. It should ideally use `InterfaceID` checks to ensure that these connectors implement the required methods.

12. Functions that could expose the contract to risks if misused:
    `resetMiddle` allows manipulating the queue's middle index and could distort the fair queue processing if not secured properly.

13. Inconsistent error reporting:
    Solidity conventions suggest using require with error messages or revert with custom error types. The code is using `revert` with custom error types along with error messages.

14. Hardcoded values for max fees within the contract:
    These values (e.g., `WITHDRAWAL_MAX_FEE`) are hardcoded, which can be a problem if they ever need to be changed. Consider implementing an upgradeable pattern or admin functionality to adjust these values as needed.

15. Unhandled return value of `call`:
    In `rescue()`, the return value of `call` used for ETH transfers is not checked. It should have a `require` statement to ensure the call didn't fail.

### Time spent:
5 hours