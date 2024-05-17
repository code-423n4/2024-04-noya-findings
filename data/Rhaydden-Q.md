
## Quality Assurance



<details>
  <summary>NOTE</summary>

---

To maintain clarity and brevity, we have selectively shortened the provided code snippets to highlight the most pertinent parts. Some sections may be condensed, and certain references are accessible through search commands due to the project's scope and time limitations.

---

Note to the judge: To avoid spamming the judging repo with issues that may still end up as QA, we have included some potentially subjective findings in this report that could be considered either _`medium or low severity`_. If the judge deems it appropriate, we would appreciate these findings being upgraded accordingly.

---

</details>





## Table of Contents

| Issue ID | Description |
| -------- | ----------- |
| [QA-01](#qa-01-potential-exploitation-of-share-to-token-conversion-rate-in-accountingmanagersol) | Potential Exploitation of Share-to-Token Conversion Rate in `AccountingManager.sol` |
| [QA-02](#qa-02-unfair-liquidation-risk-due-to-emergency-pausing-and-unpausing) | Unfair Liquidation Risk Due to Emergency Pausing and Unpausing |
| [QA-03](#qa-03-assumption-that-the-receiver-or-the-baseconnector-contract-will-correctly-and-successfully-send-all-the-tokens-back-to-the-balancerflashloan) | Assumption that the `receiver` (or the `BaseConnector` contract) will correctly and successfully send all the tokens back to the `BalancerFlashLoan` |
| [QA-04](#qa-04-handling-of-the-positionindex-and-the-vaultispositionused-mapping) | Handling of the `positionIndex` and the `vault.isPositionUsed` mapping |
| [QA-05](#qa-05-unreliable-balance-check-in-receiveflashloan-function) | Unreliable Balance Check in `receiveFlashLoan` Function |
| [QA-06](#qa-06-lack-of-slippage-protection-in-openposition-function) | Lack of Slippage Protection in `openPosition` Function |
| [QA-07](#qa-07-potential-withdrawal-inequity-in-executewithdraw-function) | Potential Withdrawal Inequity in `executeWithdraw` Function |
| [QA-08](#qa-08-the-owner-can-borrow-tokens-in-the-rescuefunds-function) | The owner can borrow tokens in the `rescueFunds` function |
| [QA-09](#qa-09-unnecessary-token-approval-in-mintorburnsusd-function) | Unnecessary Token Approval in `mintOrBurnSUSD` Function |
| [QA-10](#qa-10-issues-in-updateconnectortrustedtokens-function-implementation) | Issues in `updateConnectorTrustedTokens` Function Implementation |
| [QA-11](#qa-11-improper-handling-of-eth-in-addliquidityinmaverickpool-function) | Improper Handling of ETH in `addLiquidityInMaverickPool` Function |
| [QA-12](#qa-12-misleading-constructor-call-in-keepers-contract) | Misleading Constructor Call in `Keepers` Contract |
| [QA-13](#qa-13-hardcoded-invalid-ethereum-address-in-_getpositiontvl-function) | Hardcoded Invalid Ethereum Address in `_getPositionTVL` Function |
| [QA-14](#qa-14-potential-security-risk-due-to-token-approval-reuse-in-openposition-function) | Potential Security Risk Due to Token Approval Reuse in `openPosition` Function |
| [QA-15](#qa-15-incorrect-handling-of-first-position-removal-in-updateholdingposition-function) | Incorrect Handling of First Position Removal in `updateHoldingPosition` Function |
| [QA-16](#qa-16-revise-balance-check-in-addliquidity-function) | Revise Balance Check in `addLiquidity` Function |
| [QA-17](#qa-17-lack-of-validation-for-actions-within-calldata-in-executecommands-function) | Lack of Validation for Actions within `callData` in `executeCommands` Function |
| [QA-18](#qa-18-uncleared-state-in-removetrustedposition-function-may-cause-inconsistencies) | Uncleared State in `removeTrustedPosition` Function May Cause Inconsistencies |
| [QA-19](#qa-19-incorrect-permission-checks-in-onlyvaultmaintainer-modifier) | Incorrect Permission Checks in `onlyVaultMaintainer` Modifier |
| [QA-20](#qa-20-deposit-in-depositintoconvexbooster-may-revert) | Deposit in `depositIntoConvexBooster` may revert |
| [QA-21](#qa-21-receiveflashloan-function-not-protected-against-reentrancy) | `receiveFlashLoan` Function Not Protected Against Reentrancy |
| [QA-22](#qa-22-fix-typos-and-documentations-multiple-instances) | Fix Typos and Documentations (Multiple instances) |
| [QA-23](#qa-23-multiple-instances-of-todos) | Multiple Instances of TODOs |






## [QA-01] Potential Exploitation of Share-to-Token Conversion Rate in `AccountingManager.sol`

In the `AccountingManager.sol` contract, early withdrawals before a profit recalculation or fee distribution might exploit the available base tokens. The current implementation does not lock the share-to-token conversion rate at the time of withdrawal queuing, which could lead to inconsistencies if the underlying conditions change before the withdrawal is executed.


https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol

### Recommendations
Consider implementing a locking mechanism that locks the share-to-token conversion rate at the time of withdrawal queuing. This ensures that the conversion rate remains consistent from the time the withdrawal request is made until it is executed.


1. **Modify the `withdraw` function to store the current share-to-token conversion rate:**

```diff
- function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {
+ function queueWithdraw(uint256 shares, address receiver) public nonReentrant whenNotPaused {
+     uint256 currentRate = getCurrentShareToTokenRate();
      if (balanceOf(msg.sender) < share + withdrawRequestsByAddress[msg.sender]) {
          revert NoyaAccounting_INSUFFICIENT_FUNDS(
              balanceOf(msg.sender), share, withdrawRequestsByAddress[msg.sender]
          );
      }
      withdrawRequestsByAddress[msg.sender] += share;

      // adding the withdraw request to the withdraw queue
-     withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);
+     withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, shares, currentRate);
      emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, shares, block.timestamp);
      withdrawQueue.last += 1;
  }
```

2. **Modify the `executeWithdraw` function to use the stored rate for calculations:**

```diff
  function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
      if (currentWithdrawGroup.isFullfilled == false) {
          revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
      }
      uint64 i = 0;
      uint256 firstTemp = withdrawQueue.first;

      uint256 withdrawFeeAmount = 0;
      uint256 processedBaseTokenAmount = 0;
      // loop through the withdraw queue and execute the withdraws
      while (
          currentWithdrawGroup.lastId > firstTemp
              && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
              && i < maxIterations
      ) {
          i += 1;
          WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
          uint256 shares = data.shares;
          // calculate the base token amount that the user will receive based on the stored rate
-         uint256 baseTokenAmount = data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
+         uint256 baseTokenAmount = data.shares * data.storedRate / 1e18;

          withdrawRequestsByAddress[data.owner] -= shares;
          _burn(data.owner, shares);

          processedBaseTokenAmount += data.amount;
    
```

3. **Add a function to get the current share-to-token conversion rate:**

```diff
+ function getCurrentShareToTokenRate() public view returns (uint256) {
+     uint256 totalShares = totalSupply();
+     uint256 totalAssets = totalAssets();
+     if (totalShares == 0) {
+         return 1e18; // 1:1 rate if no shares exist
+     }
+     return totalAssets * 1e18 / totalShares;
+ }
```

By implementing these changes, you ensure that the conversion rate from shares to base tokens is fixed at the time the withdrawal is queued, preventing any changes in underlying conditions from affecting the amount withdrawn. This approach is similar to fixing the scaleFactor at the time of market closure in the reported issue.











## [QA-02] Unfair Liquidation Risk Due to Emergency Pausing and Unpausing

The admin's ability to pause the AccountingManager contract can result in users being unable to manage their positions, potentially leading to unfair liquidations and loss of funds. MEV actors can exploit the situation by front-running user transactions and liquidating vulnerable positions immediately after the protocol is unpaused, causing significant financial harm to affected users.

Users' positions may become at risk of liquidation by MEV bots during the pause period initiated by an admin, leading to potential losses without the opportunity for users to take preventive action.

Also, on unpause, it is unlikely that any human users will be able to secure their positions before MEV/liquidation bots capture the available profit. Hence the loss is 100% certain.


>Considering, the new C4 rules on Admin actions, would be key to note this is also a centralization risk.

##### Code snippet:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L659

When emergencyStop() is called, it triggers _pause(), which disables all functions with whenNotPaused modifiers. This includes critical user functions such as:

- deposit()
- withdraw()
- calculateDepositShares()
- executeDeposit()
- calculateWithdrawShares()
- executeWithdraw()

##### Scenario:

1. The admin pauses the AccountingManager contract using the emergencyStop() function.
2. During the paused state, market conditions change, causing some vaults' positions to become unhealthy or undercollateralized.
3. Users are unable to deposit more collateral, repay debt, or withdraw funds to maintain the health of their positions due to the contract being paused.
4. The admin unpauses the contract using the unpause() function.
5. MEV actors quickly identify the vulnerable positions and front-run user transactions to liquidate these positions before the users can take corrective actions.
6. Affected users suffer financial losses due to the unfair liquidations.


>Scenarios affected: Any situation where rapid response from a user is required post-unpausal due to changing market conditions that occurred while paused.


Though, real prices from oracles will surely move up or down during this paused period. If the oracle prices go down, the users won't be allowed to allocate more collateral to their positions or close their positions. Hence their positions will get under-collateralized (based upon real prices).

And just for reference, similar issue were acknowledged in [Lumin](https://solodit.xyz/issues/m-02-instant-liquidations-can-happen-after-unpausing-the-protocol-pashov-none-lumin-markdown), [Blueberry](https://github.com/sherlock-audit/2023-02-blueberry-judging/issues/290), [Notional V3](https://github.com/sherlock-audit/2023-03-notional-judging/issues/203) and [Symmetrical](https://github.com/sherlock-audit/2023-06-symmetrical-judging/issues/336) audits.

### Recommended Mitigation Steps

Consider implementing a time-delayed unpausal mechanism (grace period) with an announcement period allowing users ample notice before resuming full functionality or introduce transaction prioritization for original position holders post-unpaused state








## [QA-03] Assumption that the `receiver` (or the `BaseConnector` contract) will correctly and successfully send all the tokens back to the `BalancerFlashLoan`

In the `BalancerFlashLoan.sol` contract, the `receiveFlashLoan` function handles the logic after receiving a flash loan. The function processes the tokens received, executes transactions with them, and then returns the tokens to the vault. However, there is a potential issue related to the handling of token transfers and balances similar to the one described in the audit report for the Loopy contract.


The potential issue arises in the assumption that the `receiver` (or the `BaseConnector` contract) will correctly and successfully send all the tokens back to the `BalancerFlashLoan` contract. If the tokens are not sent back, or not all tokens are sent back, the final check (`tokens[i].balanceOf(address(this)) == 0`) will fail, causing the transaction to revert.

Here's a breakdown of the relevant parts of the `receiveFlashLoan` function:


1. **Token Transfer to Receiver**:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L74-L77
   ```solidity
   for (uint256 i = 0; i < tokens.length; i++) {
       tokens[i].safeTransfer(receiver, amounts[i]);
       amounts[i] = amounts[i] + feeAmounts[i];
   }
   ```
   Here, the tokens are transferred to the `receiver`. The `amounts` array is then updated to include the fee amounts.


3. **Execution of Transactions**:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L79-L82
   ```solidity
   for (uint256 i = 0; i < destinationConnector.length; i++) {
       (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
       require(success, "BalancerFlashLoan: Flash loan failed");
   }
   ```

4. **Token Transfer Back to This Contract**:
   ```solidity
   for (uint256 i = 0; i < tokens.length; i++) {
       BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
   }
   ```
   This step assumes that the `receiver` (or the `BaseConnector` contract) will send the tokens back to the `BalancerFlashLoan` contract. However, there is no explicit check to ensure that the tokens are actually received by the `BalancerFlashLoan` contract before proceeding to the next step.

5. **Token Transfer Back to the Vault**:
   ```solidity
   for (uint256 i = 0; i < tokens.length; i++) {
       tokens[i].safeTransfer(msg.sender, amounts[i]);
       require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
   }
   ```
The contract sends the tokens back to the vault and checks if the balance of each token in the contract is zero. This check assumes that all tokens have been successfully returned to the vault.


### Recommended Mitigation Steps
Consider implementing a check after the `BaseConnector(receiver).sendTokensToTrustedAddress(...)` call to ensure that the expected amount of tokens has been received by the `BalancerFlashLoan` contract.
Also handle exceptions or errors in token transfers more gracefully to avoid reverting the entire transaction, especially in scenarios where partial success in operations might be acceptable.








## [QA-04] Handling of the `positionIndex` and the `vault.isPositionUsed` mapping

The `updateHoldingPosition` function has a potential issue related to the handling of the `positionIndex` and the `vault.isPositionUsed` mapping. Specifically, the function does not correctly handle the case where `positionIndex` is `0`, which is the default value for uninitialized mappings in Solidity. This can lead to incorrect behavior when updating or removing holding positions.

Look at this part of the code:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L346-L362

```solidity
uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
if (positionIndex == 0 && removePosition) return type(uint256).max;
if (removePosition) {
    if (positionIndex < vault.holdingPositions.length - 1) {
        vault.holdingPositions[positionIndex] = vault.holdingPositions[vault.holdingPositions.length - 1];
        vault.isPositionUsed[keccak256(
            abi.encode(
                vault.holdingPositions[positionIndex].calculatorConnector,
                vault.holdingPositions[positionIndex].positionId,
                vault.holdingPositions[positionIndex].data
            )
        )] = positionIndex;
    }
    vault.holdingPositions.pop();
    vault.isPositionUsed[holdingPositionId] = 0;
    emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);
    return type(uint256).max;
}
```

>This issue arises because `positionIndex` being `0` can mean either the position is not used or it is the first position in the `holdingPositions` array. This ambiguity can cause incorrect behavior when removing or updating positions.

### Recommended Mitigation Steps

Introduce a sentinel value to indicate an unused position. For example, you can use `type(uint256).max` as a sentinel value to indicate that a position is not used.  Like this:

```diff
-         uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
-         if (positionIndex == 0 && removePosition) return type(uint256).max;
+         uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
+         if (positionIndex == 0 && vault.holdingPositions.length > 0 && vault.holdingPositions[0].positionId != _positionId) {
+             // If positionIndex is 0 but the first position is not the one we are looking for, it means the position is not used
+             positionIndex = type(uint256).max;
+         }
+         if (positionIndex == type(uint256).max && removePosition) return type(uint256).max;
          if (removePosition) {
              if (positionIndex < vault.holdingPositions.length - 1) {
                  vault.holdingPositions[positionIndex] = vault.holdingPositions[vault.holdingPositions.length - 1];
                  vault.isPositionUsed[keccak256(
                      abi.encode(
                          vault.holdingPositions[positionIndex].calculatorConnector,
                          vault.holdingPositions[positionIndex].positionId,
                          vault.holdingPositions[positionIndex].data
                      )
                  )] = positionIndex;
              }
              vault.holdingPositions.pop();
-             vault.isPositionUsed[holdingPositionId] = 0;
+             vault.isPositionUsed[holdingPositionId] = type(uint256).max;
              emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);
              return type(uint256).max;
          }
          return
              updateHoldingPosition(vault, vaultId, _positionId, _data, additionalData, positionIndex, holdingPositionId);
```

In this updated code, we check if `positionIndex` is `0` and the first position in the `holdingPositions` array does not match the `_positionId`. If so, we set `positionIndex` to `type(uint256).max` to indicate that the position is not used. This ensures that the function correctly handles the case where `positionIndex` is `0` due to an uninitialized mapping.











## [QA-05] Unreliable Balance Check in `receiveFlashLoan` Function

The `receiveFlashLoan` function contains a balance check after transferring tokens back to the vault. This check is intended to ensure that no extra tokens remain in the contract after the flash loan operation. However, this approach is unreliable because the balance of the contract could be affected by other operations or factors, leading to a false positive or negative result. This could potentially allow for incorrect behavior, such as not returning all borrowed tokens or incorrectly assuming that extra tokens are present.

### Proof of Concept
Look at this part of the code:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L89-L92

```solidity
for (uint256 i = 0; i < tokens.length; i++) {
    // send the tokens back to the vault
    tokens[i].safeTransfer(msg.sender, amounts[i]);
    require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
}
```
Here, after transferring the tokens back to the vault (`msg.sender`), the contract checks if the balance of each token in the contract is 0. This check is problematic because it does not account for other potential operations that might affect the token balance in the contract.

## Recommended Mitigation Steps:
The contract should ensure that the exact amount of tokens borrowed is returned to the vault, rather than relying on a post-transfer balance check. We can achieve this by tracking the initial balance of each token before the transfer and ensuring that the correct amount is transferred back. 
Here is a revised version of the loop:

```diff
for (uint256 i = 0; i < tokens.length; i++) {
+    uint256 initialBalance = tokens[i].balanceOf(address(this));
    tokens[i].safeTransfer(msg.sender, amounts[i]);
+    uint256 finalBalance = tokens[i].balanceOf(address(this));
-      require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
+    require(finalBalance == initialBalance - amounts[i], "BalancerFlashLoan: Flash loan extra tokens");
}
```

This ensures that the contract accurately verifies the return of the borrowed tokens, avoiding the potential issues associated with the unreliable balance check.









## [QA-06] Lack of Slippage Protection in `openPosition` Function

### Impact

Lack of comprehensive slippage protection in the `openPosition` function can lead to unfavorable exchange rates for the tokens being deposited into a Balancer pool. This could result in the contract receiving less value than expected, potentially leading to financial losses or suboptimal investment positions. 

>This issue is particularly relevant in volatile markets or pools with low liquidity, where the actual exchange rates can deviate significantly from the expected rates.

### Proof of Concept

The `openPosition` function uses the `IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT` join kind when calling `IBalancerVault(balancerVault).joinPool`. This specifies the exact amount of tokens to be deposited for a minimum amount of BPT out, without explicitly accounting for the exchange rates of individual tokens.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L64-L94

```solidity
function openPosition(
    bytes32 poolId,
    uint256[] memory amounts,
    uint256[] memory amountsWithoutBPT,
    uint256 minBPT,
    uint256 auraAmount
) public onlyManager nonReentrant {
    address[] memory tokens;
    {
        (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(poolId);
    }
    address pool = IBalancerVault(balancerVault).getPool(poolId);

    for (uint256 i = 0; i < tokens.length; i++) {
        if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
    }

    IBalancerVault(balancerVault).joinPool(
        poolId,
        address(this), // sender
        address(this), // recipient
        IBalancerVault.JoinPoolRequest(
            tokens,
            amounts,
            abi.encode(
                IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
                amountsWithoutBPT, //_noBptAmounts,
                minBPT // minimumBPT
            ),
            false
        )
    );
    // ... Rest of the code
}
```

### Recommended Mitigation Steps

Consider implementing slippage checks. Before executing the `joinPool` call, calculate the expected rates based on current pool balances and prices. Compare these rates to the rates implied by the `amounts` and `minBPT` parameters. If the implied rates are too far from the expected rates, abort the transaction.
Also consider allowing the contract manager or the transaction initiator to specify a maximum acceptable slippage percentage. The contract should then verify that the transaction does not exceed this slippage tolerance before proceeding.





## [QA-07] Potential Withdrawal Inequity in `executeWithdraw` Function


In AccountingManager, when users request a withdrawal via the `withdraw` function, their shares are recorded in the `withdrawRequestsByAddress` mapping and added to the `withdrawQueue`. Later, when the `executeWithdraw` function is called by the manager to process withdrawals, it calculates the base token amount each user should receive based on their share of the total shares in the current withdraw group:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L416

```solidity
uint256 baseTokenAmount = data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
```

The issue here is that if the total available base tokens in the contract (`currentWithdrawGroup.totalABAmount`) is less than the total calculated base tokens owed (`currentWithdrawGroup.totalCBAmountFullfilled`), then early withdrawers may receive their full expected amount while later withdrawers receive less than expected. This can lead to an inequitable distribution of funds.

>This is more of a potential fairness issue than a vulnerability, but worth considering to ensure all users are treated equitably in withdrawal scenarios


### Recommended Mitigation Steps

We should ensure that the `totalABAmount` always matches the actual base token balance before processing withdrawals and process withdrawals in a more equitable way if there is a shortfall. Here are the recommended changes:

```diff
function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
    if (currentWithdrawGroup.isFullfilled == false) {
        revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
    }
    uint64 i = 0;
    uint256 firstTemp = withdrawQueue.first;

    uint256 withdrawFeeAmount = 0;
    uint256 processedBaseTokenAmount = 0;
+   uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;

+   // Ensure totalABAmount matches actual base token balance
+   if (availableAssets < currentWithdrawGroup.totalCBAmountFullfilled) {
+       currentWithdrawGroup.totalABAmount = availableAssets;
+   }

    // loop through the withdraw queue and execute the withdraws
    while (
        currentWithdrawGroup.lastId > firstTemp
            && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
            && i < maxIterations
    ) {
        i += 1;
// ......
```
















## [QA-08] The owner can borrow tokens in the `rescueFunds` function

### Impact
The `rescueFunds` function allows the owner to withdraw any tokens or Ether from the contract. This can potentially be exploited by the owner to perform actions similar to a free flash loan, where the owner can withdraw tokens, use them temporarily, and then return them. This could lead to unintended consequences and potential misuse of the contract's funds.

There’s no restriction on which funds the owner can try to withdraw and which token to call. It’s theoretically possible to transfer pool tokens and then return them to the contract (e.g. in the case of ERC-777). That action would be similar to a free flash loan.

### Proof of Concept
The `rescueFunds` function does not restrict which tokens can be withdrawn. Look at this part of the code:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L202

```solidity
function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {
    if (token == address(0)) {
        (bool success,) = payable(userAddress).call{ value: amount }("");
        require(success, "Transfer failed.");
    } else {
        IERC20(token).safeTransfer(userAddress, amount);
    }
    emit Rescued(token, userAddress, amount);
}
```

There is no check to ensure that the token being rescued is not one of the tokens involved in the contract's core functionalities, such as tokens used in swaps or bridges.

### Recommended Mitigation Steps
So as to prevent potential misuse, add a check to ensure that the token being rescued is not one of the tokens involved in the contract's operations. This can be done by maintaining a list or mapping of restricted tokens and checking against it in the `rescueFunds` function. Here is an example of how this can be implemented:

```solidity
// Add a mapping to track restricted tokens
mapping(address => bool) public restrictedTokens;

// Function to add a token to the restricted list
function addRestrictedToken(address token) external onlyOwner {
    restrictedTokens[token] = true;
}

// Modify the rescueFunds function to check against the restrictedTokens mapping
function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {
    require(!restrictedTokens[token], "LifiImplementation: Token is restricted");
    if (token == address(0)) {
        (bool success,) = payable(userAddress).call{ value: amount }("");
        require(success, "Transfer failed.");
    } else {
        IERC20(token).safeTransfer(userAddress, amount);
    }
    emit Rescued(token, userAddress, amount);
}
```

This will restrict certain tokens from being rescued, which can help prevent the kind of exploitation described.










## [QA-09] Unnecessary Token Approval in `mintOrBurnSUSD` Function

The `mintOrBurnSUSD` function in the `SNXV3Connector` contract unnecessarily approves the USD token for each burn operation, leading to potential gas inefficiencies and repeated approvals without checking the current allowance.

### Proof of Concept
Look at the following snippet from the `mintOrBurnSUSD` function; it shows the approval being made without checking the current allowance.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L111-L114

```solidity
if (mintOrBurn) {
    SNXCoreProxy.mintUsd(_accountId, poolId, collateralType, _amount);
} else {
    _approveOperations(usdToken, address(SNXCoreProxy), _amount); // Unconditional approval
    SNXCoreProxy.burnUsd(_accountId, poolId, collateralType, _amount);
}
```

### Recommended Mitigation Steps
Before approving the USD token, check the current allowance and only proceed with the approval if the existing allowance is insufficient. This reduces unnecessary transactions and saves gas.

```diff
else {
+    uint256 currentAllowance = IERC20(usdToken).allowance(address(this), address(SNXCoreProxy));
+    if (currentAllowance < _amount) {
        _approveOperations(usdToken, address(SNXCoreProxy), _amount);
    }
    SNXCoreProxy.burnUsd(_accountId, poolId, collateralType, _amount);
}
```










## [QA-10] Issues in `updateConnectorTrustedTokens` Function Implementation

The `updateConnectorTrustedTokens` function has several issues that can lead to unintended behavior, confusion, and potential security risks. 

1. The `trusted` parameter is not an array, which means all tokens in `_tokens` will be set to the same trust status. This may not be the intended behavior if different tokens require different trust statuses.
2. The NatSpec comment does not match the function signature, leading to confusion for developers and auditors.
3. There is no check to prevent setting the trust status of a non-existent connector, which could lead to unexpected behavior.


### Proof of Concept
Current Function Implementation:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L207-L218

```solidity
function updateConnectorTrustedTokens(
    uint256 vaultId,
    address _connectorAddress,
    address[] calldata _tokens,
    bool trusted
) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
    Vault storage vault = vaults[vaultId];
    for (uint256 i = 0; i < _tokens.length; i++) {
        vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = trusted;
    }
    emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted);
}
```

Current NatSpec Comment:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L200-L206

```solidity
/*
* @dev This function is used to add or remove new trusted tokens to an specific connector
* @param vaultId The id of the vault
* @param _connectorAddress The address of the connector
* @param _tokens An array of token addresses
* @param _trusteds An array of booleans indicating if the token is trusted or not
*/
```

### More explanation
1. **Single `trusted` Parameter Sets Same Trust Status for All Tokens**:
   - The function uses a single boolean parameter `trusted` to set the trust status for an array of tokens `_tokens`. This means all tokens in `_tokens` will be set to the same trust status, which may not be the intended behavior.

2. **NatSpec Comment Does Not Match Function Signature**:
   - The NatSpec comment mentions `_trusteds` as an array of booleans, but the function only takes a single boolean `trusted`. This discrepancy causes confusion for developers and auditors.

3. **No Check to Prevent Setting Trust Status of Non-Existent Connector**:
   - The function does not check if the connector exists before updating the trust status of tokens. This could lead to unexpected behavior if the connector does not exist.

### Recommended Mitigation Steps
1. **Allow Different Trust Statuses for Different Tokens**:
   - Change the `trusted` parameter to an array of booleans to allow different trust statuses for different tokens.
   - Update the NatSpec comment to accurately reflect the function signature.
   - Add a check to ensure the connector exists before updating the trust status of tokens.

### Updated code
```solidity
function updateConnectorTrustedTokens(
    uint256 vaultId,
    address _connectorAddress,
    address[] calldata _tokens,
    bool[] calldata _trusteds
) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
    require(_tokens.length == _trusteds.length, "Array lengths must match");
    Vault storage vault = vaults[vaultId];
    require(vault.connectors[_connectorAddress].enabled, "Connector does not exist");
    for (uint256 i = 0; i < _tokens.length; i++) {
        vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = _trusteds[i];
    }
    emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, _trusteds);
}
```











## [QA-11] Improper Handling of ETH in `addLiquidityInMaverickPool` Function

The current implementation of the `addLiquidityInMaverickPool` function does not properly handle scenarios where one of the tokens involved in adding liquidity is Ethereum (ETH). Specifically, the function incorrectly attempts to approve ETH as if it were an ERC20 token, which leads to transaction failures when interacting with pools that involve ETH. 

>This issue affects the functionality of adding liquidity to such pools, potentially causing financial loss due to failed transactions and impacting the overall usability of the contract for users intending to interact with ETH-based pools.

### Proof of Concept

Look at this part of the function:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L91-L107

```solidity
_approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); // TODO: check token A is eth
_approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);
```

This part of the function does not differentiate between ERC20 tokens and ETH when attempting to approve tokens for spending by the `maverickRouter`. The comment `// TODO: check token A is eth` indicates an awareness of the issue but lacks an actual implementation to address it.

### Recommended Mitigation Steps

1. **Check Token Type Before Approval**: Implement a check to determine if `p.pool.tokenA()` represents ETH (using the common placeholder address for ETH) before attempting to call `_approveOperations`.

2. **Skip Approval for ETH**: If `p.pool.tokenA()` is determined to be ETH, skip the approval step for this token, as ETH does not support the ERC20 `approve` mechanism.

3. **Apply Approval Only to ERC20 Tokens**: Ensure that `_approveOperations` is called only for tokens confirmed to be ERC20 tokens.

Something like this:

```solidity
if (p.pool.tokenA()!= address(0)) { // Check if tokenA is not ETH
    _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance);
}
_approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);
```

This will ensure that the contract correctly handles both ETH and ERC20 tokens when adding liquidity, preventing transaction failures and ensuring smoother interactions with various types of pools.









## [QA-12]  Misleading Constructor Call in `Keepers` Contract

The constructor of the `Keepers` contract contains a misleading call to `Ownable(msg.sender)`, suggesting an inheritance from `Ownable` that does not exist in the contract's imports. This could lead to confusion about the contract's inheritance hierarchy and its initialization process. It might also imply that the contract is using features from `Ownable` that are actually provided by `Ownable2Step`, potentially leading to misunderstandings about the contract's functionality and security model.

### Proof of Concept
The constructor in question is defined as follows:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L27

```solidity
constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
    require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);
    for (uint256 i = 0; i < _owners.length; i++) {
        isOwner[_owners[i]] = true;
    }
    numOwners = _owners.length;
    threshold = _threshold;
}
```

However, the contract's imports do not include `Ownable`:

```solidity
import "@openzeppelin/contracts-5.0/utils/cryptography/EIP712.sol";
import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";
import "@openzeppelin/contracts-5.0/utils/cryptography/ECDSA.sol";
```

This discrepancy between the constructor call and the actual imports indicates a potential misunderstanding or miscommunication about the contract's design and functionality.

### Recommended Mitigation Steps
To clarify the contract's inheritance and ensure that the constructor accurately reflects the contract's structure, the misleading call to `Ownable(msg.sender)` should be removed. The corrected constructor should initialize only the inherited contracts that are actually imported and used:













## [QA-13] Hardcoded Invalid Ethereum Address in `_getPositionTVL` Function


The `_getPositionTVL` function within the `Gearboxv3` smart contract incorrectly uses `address(840)` as an argument in the `_getValue` function call. This usage suggests an attempt to pass an Ethereum address, but `address(840)` is not a valid Ethereum address representation. Ethereum addresses are 20-byte values, typically represented as 40 hexadecimal characters prefixed with `0x`. The incorrect address handling could lead to unexpected behavior or failure when calculating the total value locked (TVL) of a credit account, potentially affecting financial calculations and decision-making based on the TVL.

### Proof of Concept

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L103

```solidity
return _getValue(address(840), base, (d.totalValueUSD - d.totalDebtUSD));
```

Here, `address(840)` is passed as the first argument to the `_getValue` function. However, `address(840)` does not conform to the expected format of an Ethereum address, which should be a 20-byte value represented as a 40-character hexadecimal string prefixed with `0x`.

### Recommended Mitigation Steps:

If the intention was to use a specific Ethereum address for the valuation of the collateral and debt, it should be replaced with a valid Ethereum address. If address(840) was meant to be a placeholder, it needs to be corrected to ensure the function works as intended.








## [QA-14] Potential Security Risk Due to Token Approval Reuse in `openPosition` Function

The `openPosition` function in the `BalancerConnector.sol` contract approves tokens for spending by the `balancerVault` without subsequently revoking or resetting these approvals. This behavior could lead to a security vulnerability where, if the `balancerVault` were compromised, an attacker could exploit the existing approvals to transfer more tokens than intended. This risk is heightened because the approvals remain valid indefinitely until explicitly changed, allowing for potential unauthorized transfers beyond the scope of the initial operation.

### Proof of Concept

In the `openPosition` function, tokens are approved for the `balancerVault` as follows:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L77-L79

```solidity
for (uint256 i = 0; i < tokens.length; i++) {
    if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
}
```

After this loop, there is no action taken to revoke or reset these approvals. The `_approveOperations` function presumably calls the ERC20 `approve` function to grant the `balancerVault` permission to spend the specified amounts of each token. Without revoking these approvals, any future interactions with the `balancerVault` could potentially be exploited if the `balancerVault`'s security were compromised.

### Recommended Mitigation Steps

Modify the `_approveOperations` function to implement a safe approval pattern. This can be achieved by setting the allowance to 0 before setting it to the desired amount, ensuring that the allowance cannot be reused maliciously.

Something like this:

```solidity
    function _safeApprove(address token, address spender, uint256 amount) internal {
        uint256 currentAllowance = IERC20(token).allowance(address(this), spender);
        if (currentAllowance!= amount) {
            // Reset the allowance to prevent re-use
            IERC20(token).approve(spender, 0);
            // Set the new allowance
            IERC20(token).approve(spender, amount);
        }
    }
```









## [QA-15] Incorrect Handling of First Position Removal in `updateHoldingPosition` Function

The function `updateHoldingPosition` may incorrectly assume that a position with index `0` does not exist when attempting to remove it. This can lead to false negatives, where valid positions are not correctly removed or updated, resulting in inconsistent state management.

### Proof of Concept

This is the current implementation:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L293-L326

```solidity
function updateHoldingPosition(
    uint256 vaultId,
    bytes32 _positionId,
    bytes calldata _data,
    bytes calldata additionalData,
    bool removePosition
) public vaultExists(vaultId) returns (uint256) {
    Vault storage vault = vaults[vaultId];
    if (!vault.connectors[msg.sender].enabled) revert UnauthorizedAccess();
    if (!vault.trustedPositionsBP[_positionId].isEnabled) revert InvalidPosition(_positionId);
    bytes32 holdingPositionId = keccak256(abi.encode(msg.sender, _positionId, _data));
    uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
    if (positionIndex == 0 && removePosition) return type(uint256).max;
    if (removePosition) {
        if (positionIndex < vault.holdingPositions.length - 1) {
            vault.holdingPositions[positionIndex] = vault.holdingPositions[vault.holdingPositions.length - 1];
            vault.isPositionUsed[keccak256(
                abi.encode(
                    vault.holdingPositions[positionIndex].calculatorConnector,
                    vault.holdingPositions[positionIndex].positionId,
                    vault.holdingPositions[positionIndex].data
                )
            )] = positionIndex;
        }
        vault.holdingPositions.pop();
        vault.isPositionUsed[holdingPositionId] = 0;
        emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);
        return type(uint256).max;
    }
    return updateHoldingPosition(vault, vaultId, _positionId, _data, additionalData, positionIndex, holdingPositionId);
}
```

### Scenario

1. **First Position Added**:
   - When the first position is added to the `holdingPositions` array, its index will be `0`.
   - The `isPositionUsed` mapping will store `0` for the `holdingPositionId` of this first position.

2. **Removing the First Position**:
   - If the first position is to be removed, the `positionIndex` will be `0` (since it is the first position).
   - The check `if (positionIndex == 0 && removePosition)` will evaluate to `true` because `positionIndex` is `0` and `removePosition` is `true`.

3. **Incorrect Behavior**:
   - The function will return `type(uint256).max`, indicating that the position does not exist, even though it actually does.
   - This is because the check `positionIndex == 0` is not sufficient to determine if the position exists or not. It only checks if the index is `0`, which is a valid index for the first position.


### Recommended Mitigation Steps

Add a more robust check to ensure that the position actually exists before attempting to remove it. Consider checking if `vault.isPositionUsed[holdingPositionId]` is not equal to the default value for non-existent positions, which should be set when positions are added.










## [QA-16] Revise Balance Check in `addLiquidity` Function

The current balance check logic in the `addLiquidity` function may be less intuitive and harder to understand. This could potentially lead to misunderstandings or errors during code maintenance or review. 

>Although the logic is functionally correct, improving its readability will enhance code quality.

### Proof of Concept

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L183

```solidity
for (uint256 i = 0; i < tokens.length; i++) {
    // gather all of the tokens
    uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
    ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
    uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
    if (_balanceAfter < amounts[i] + _balance) {
        revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
    }
}
```

The condition `if (_balanceAfter < amounts[i] + _balance)` can be less intuitive. A more straightforward approach would be to directly compare the difference between `_balanceAfter` and `_balance` with `amounts[i]`.

### Recommended Mitigation Steps
Update the balance check logic to make it more intuitive:

```diff
for (uint256 i = 0; i < tokens.length; i++) {
    // gather all of the tokens
    uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
    ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
    uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
+    if (_balanceAfter - _balance < amounts[i]) {
        revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
    }
}
```






## [QA-17] Lack of Validation for Actions within `callData` in `executeCommands` Function

### Impact
The `executeCommands` function in the `Gearboxv3` contract checks if the target of each `MultiCall` is the `facade` address, but it does not validate the specific actions within the `callData`. This means that while the target must be the `facade`, the `callData` could contain calls to any function, including potentially sensitive or restricted ones. This could lead to unauthorized actions being executed, posing a security risk.

### Proof of Concept

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L62-L86

```solidity
function executeCommands(
    address facade,
    address creditAccount,
    MultiCall[] calldata calls,
    address approvalToken,
    uint256 amount
) public onlyManager nonReentrant {
    for (uint256 i = 0; i < calls.length; i++) {
        if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
        bytes4 method = bytes4(calls[i].callData[:4]);

        if (method == ICreditFacadeV3Multicall.enableToken.selector) {
            (address token) = abi.decode(calls[i].callData[4:], (address));
            _updateTokenInRegistry(token);
        }
    }
    if (approvalToken != address(0)) {
        _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount);
    }
    ICreditFacadeV3(facade).multicall(creditAccount, calls);
    if (approvalToken != address(0)) {
        _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());
    }
    emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);
}
```

### Recommended Mitigation Steps
Consider implementing a whitelist of allowed methods to ensure only intended actions can be executed. Here is an example:

```diff
mapping(bytes4 => bool) private allowedMethods;

constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
    allowedMethods[ICreditFacadeV3Multicall.enableToken.selector] = true;
    // Add other allowed methods here
}

function executeCommands(
    address facade,
    address creditAccount,
    MultiCall[] calldata calls,
    address approvalToken,
    uint256 amount
) public onlyManager nonReentrant {
    for (uint256 i = 0; i < calls.length; i++) {
        if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
        bytes4 method = bytes4(calls[i].callData[:4]);

+        if (!allowedMethods[method]) {
+            revert("Method not allowed");
        }

        if (method == ICreditFacadeV3Multicall.enableToken.selector) {
            (address token) = abi.decode(calls[i].callData[4:], (address));
            _updateTokenInRegistry(token);
        }
    }
    if (approvalToken != address(0)) {
        _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount);
    }
    ICreditFacadeV3(facade).multicall(creditAccount, calls);
    if (approvalToken != address(0)) {
        _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());
    }
    emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);
}
```

This ensures that only allowed methods can be executed, reducing the risk of unauthorized actions.








## [QA-18] Uncleared State in removeTrustedPosition Function May Cause Inconsistencies

The `removeTrustedPosition` function fails to clear the isPositionUsed mapping when a trusted position is removed. This could result in state inconsistencies if the same position ID is reused.

### Impacts
The `removeTrustedPosition` function is broken in the edge case when the maintainer tries to add the same position back into the vault after removing it. This affects all operations of NOYA protocol that rely on the vault registry and the correct state of the `isPositionUsed` mapping.

### Recommended Mitigation Steps
Clear the `isPositionUsed` mapping when removing a trusted position from the registry.

```diff
function removeTrustedPosition(uint256 vaultId, bytes32 _positionId)
    external
    onlyVaultMaintainer(vaultId)
    vaultExists(vaultId)
{
    Vault storage vault = vaults[vaultId];
    if (!vault.trustedPositionsBP[_positionId].isEnabled) revert NotExist();
    uint256 length = vault.holdingPositions.length;
    for (uint256 i = 0; i < length; i++) {
        if (vault.holdingPositions[i].positionId == _positionId) {
            revert CannotRemovePosition(vaultId, _positionId);
        }
    }
    emit TrustedPositionRemoved(vaultId, _positionId);
+   bytes32 holdingPositionId = keccak256(abi.encode(
+       vault.trustedPositionsBP[_positionId].calculatorConnector,
+       _positionId,
+       vault.trustedPositionsBP[_positionId].data
+   ));
    delete vault.trustedPositionsBP[_positionId];
+   delete vault.isPositionUsed[holdingPositionId]; // Corrected key for deletion
}
```

This ensures that all related states are cleared when a trusted position is removed, preventing potential issues when adding the same position back into the vault.


















## [QA-19] Incorrect Permission Checks in `onlyVaultMaintainer` Modifier


The incorrect use of logical operator in the permission check within the `onlyVaultMaintainer`  modifier can lead to unauthorized users gaining access to restricted functionalities. Specifically, the current implementation incorrectly reverts transactions even when the sender is authorized, potentially locking out legitimate maintainers from performing their duties unless they also hold the `EMERGENCY_ROLE`.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L33

```solidity
modifier onlyVaultMaintainer(uint256 _vaultId) {
    if (msg.sender!= vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {
        revert UnauthorizedAccess();
    }
    _;
}

```

The condition in the modifier use the logical OR operator (`||`) instead of AND (`&&`). This means that even if `msg.sender` is the correct maintainer, the transaction will revert if `msg.sender` does not also have the `EMERGENCY_ROLE`. This is contrary to the expected behavior, where a transaction should only revert if `msg.sender` is neither the correct maintainer nor holds the `EMERGENCY_ROLE`.

### Recommended Mitigation Steps:

If this is not the intended logic, replace the logical OR operator (`||`) with AND (`&&`) to correctly enforce the intended permission logic. This ensures that transactions only revert when `msg.sender` is neither the specified maintainer nor has the `EMERGENCY_ROLE`.










## [QA-20]  Deposit in `depositIntoConvexBooster` may revert 

The `depositIntoConvexBooster` function incorrectly retrieves the LP token address using `poolInfo.lpToken` instead of `poolInfo[pid].lptoken`. This can lead to reverts and incorrect token approvals and deposit failures when interacting with the Convex Booster contract.

>While the risk of loss of funds is non-existant because all calls will revert, I believe the core functionality of the code can be broken.

### Proof of Concept
Look at the `depositIntoConvexBooster` function in the `CurveConnector` contract:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L103-L108

```solidity
function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {
    PoolInfo memory poolInfo = _getPoolInfo(pool);

    _approveOperations(poolInfo.lpToken, address(convexBooster), amount);
    convexBooster.deposit(pid, amount, stake);
}
```
According to Booster's code:  
https://etherscan.io/address/0xF403C135812408BFbE8713b5A23a04b3D48AAE31#code

```solidity
function deposit(uint256 _pid, uint256 _amount, bool _stake) public returns(bool){
    require(!isShutdown,"shutdown");
    PoolInfo storage pool = poolInfo[_pid];
    require(pool.shutdown == false, "pool is closed");

    //send to proxy to stake
    address lptoken = pool.lptoken;
    IERC20(lptoken).safeTransferFrom(msg.sender, staker, _amount);
    // ...
}
```

The `depositIntoConvexBooster` doesn't consider the `pid` parameter as done in the booster contract

### Recommended Mitigation Steps:

modify it to:

```diff
function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {
-          PoolInfo memory poolInfo = _getPoolInfo(pool);
+          PoolInfo memory poolInfo = _getPoolInfo(pool(pid));
     
        _approveOperations(poolInfo.lpToken, address(convexBooster), amount);
        convexBooster.deposit(pid, amount, stake);
    }
```

By directly accessing the LP token address using `convexBooster.poolInfo(pid).lptoken`, the function will correctly identify the LP token associated with the specified pool ID when interacting with the Convex Booster contract.







## [QA-21]  `receiveFlashLoan` Function Not Protected Against Reentrancy

The `receiveFlashLoan` function in the `BalancerFlashLoan` contract is not protected against reentrancy attacks. This function involves transferring tokens and calling external contracts, making it susceptible to reentrancy exploits. An attacker could potentially re-enter the function and manipulate the state or drain funds from the contract. Notably, the `receiveFlashLoan` function is not marked with the `nonReentrant` modifier, whereas the `makeFlashLoan` function is.

### Proof of Concept
The `receiveFlashLoan` function is defined as follows without the `nonReentrant` modifier:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L54-L94

```solidity
function receiveFlashLoan(
    IERC20[] memory tokens,
    uint256[] memory amounts,
    uint256[] memory feeAmounts,
    bytes memory userData
) external override {
    emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
    require(msg.sender == address(vault));
    // ... (rest of the function)
}
```

>In contrast, the `makeFlashLoan` function is protected with the `nonReentrant` modifier:

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L37-L44

```solidity
function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
    external
    nonReentrant
{
    caller = msg.sender;
    emit MakeFlashLoan(tokens, amounts);
    vault.flashLoan(this, tokens, amounts, userData);
    caller = address(0);
}
```

### Recommended Mitigation Steps
Add a nonReentrant modifier to the `receiveFlashLoan` function just as it is done in the `makeFlashLoan` function








## [QA-22] Fix Typos and Documentations _(Multiple instances)_

### Proof of Concept

- At many instances, _deposit_ is mispelled as _deposti_ 
Use this search command to see the instances: https://github.com/search?q=repo%3Acode-423n4%2F2024-04-noya+deposti+-language%3Amarkdown&type=code


- _Preformance_ should be spelled as _Performance_
Use this search command to see the instances: https://github.com/search?q=repo%3Acode-423n4%2F2024-04-noya+preformance+-language%3Amarkdown&type=code


### Impact
Bad documentation code structure, making it hard for users/developers to understand code.



### Recommended Mitigation Steps
Fix the instances highlighted above




## [QA-23]  Multiple Instances of TODOs

- Look at this:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L80

```solidity
_lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
```

It appears that the dev team intend to add an event emission here, as indicated by the `TODO` comment. This note serves as a reminder to emit an event when sending the TVL update. Emitting events is crucial for logging important actions and state changes, which can be useful for off-chain applications and monitoring tools.


For other instances, use this search command: https://github.com/search?q=repo%3Acode-423n4%2F2024-04-noya+TODO+-language%3Amarkdown&type=code


### Impact
Open Todos often hint that the codes are not ready for final production/deployment.


### Recommended Mitigation Steps:
Fix the TODOs




















