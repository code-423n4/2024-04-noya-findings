# `[L-01]` Function `sendTokensToTrustedAddress` wouldn't pass all needed validation

## Summary

One of the many validations in the function [sendTokensToTrustedAddress](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol#L84-L108), ensures that before a transfer is initiated, the liquidity intended to be used for that same transfer is removed. The aforementioned validation is done via [verifyRemoveLiquidity](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Watchers.sol#L8), which has no code in it whatsoever.

## Recommendations

Even if `verifyRemoveLiquidity` isn't going to be used, there should be some kind of validation added that confirms the caller's balance is lowered by the sent `amount`.

# `[C-01]` Withdrawals should be allowed even when the protocol is paused

## Summary

In the [AccountingManager](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol) contract, the function used to withdraw the shares of the users, has the `whenNotPaused` modifier, which would result in the users being unable to have their assets withdrawn if the protocol gets paused. This leads to a centralization issue, where the protocol is in a state in which users don't have access to their tokens.

## Recommendations

Remove the `whenNotPaused` modifier from [withdraw](), or at the very least implement a TimeLock in which the users would be able to withdraw their assets.

# `[NC-01]` Usage of the already created internal helper function

## Recommmendations

In the contract `CurveConnector`, within the function [openCurvePosition](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L117), a call to the function [_getPoolInfo](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L258-L262) can be used instead of decoding the [additionalData](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L124)