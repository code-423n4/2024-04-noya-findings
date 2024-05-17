
# INFORMATIONAL REPORT

## [QA] : Informational Findings on NoyaFeeReceiver.sol

***Description:***

The NoyaFeeReciever contract should use Ownable2Step instead of Ownable

**Impact:**
This is technically not a vulnerablity , but openZeppelin Ownable can lead to loss of contract ownership if ownership is transferred to a non-existent address. Ownable2step requires the reciever o confirm ownership. this insures against accidentally sending ownership to a mistyped address 

## [QA] : Informational Findings on Omnichainlogic.sol
### [QA-1] : Change updateChainInfo() to updateDstChainInfo(); https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46
### [QA-2] : Instead of this, why noy use the TimeLock contract ; https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71
### [QA-3] TITLE : Adherence to the Checks-Effects-Interactions(CEI) pattern;https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L83

***Description:***
This report analyzes the Omnichainlogic::startBridgeTransaction function, for adherence to the Checks-effects-Interactions pattern; the function initially isolated this pattern by updating the state after an external call. this report details the neccesary corrections, ensuring all state changes occur before any external Intercations, thereby enhancing the contract's security and robustness.

**Impact:**
Although the Omnichainlogic::startBridgeTransaction function uses a non-reentrancy guard, which mitigates the risk of reentrancy attacks, strictly following the Checks-Effects-Interactions (CEI) pattern is still important for coding best practices and ethical standards. Adhering to the CEI pattern ensures a clear and structured approach to function execution, enhancing the readability and maintainability of the code. It also provides an additional layer of security, reinforcing the function's robustness against potential vulnerabilities. Therefore, even with the non-reentrancy guard in place, following the CEI pattern is a prudent practice that upholds high standards of smart contract development.

**Proof of Concept:**

<details>
<summary>code</summary>

```javascript
function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
        bytes32 txn = keccak256(abi.encode(bridgeRequest));
        emit StartBridgeTransaction(bridgeRequest, txn);
        if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {
            revert IConnector_BridgeTransactionNotApproved(txn);
        }
        if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();
        if (
            destChainAddress[bridgeRequest.destChainId] == address(0)
                || destChainAddress[bridgeRequest.destChainId] != bridgeRequest.receiverAddress
        ) {
            revert IConnector_InvalidDestinationChain();
        }
        approvedBridgeTXN[txn] = 0;
        swapHandler.executeBridge(bridgeRequest);
      @>  _updateTokenInRegistry(bridgeRequest.inputToken);
    }
```
</details>

**Recommended Mitigation:**

The call to swapHandler.executeBridge(bridgeRequest) happens before the internal call to _updateTokenInRegistry, which is a state change.
To strictly follow the CEI pattern, all state changes should be made before calling external contracts. Let’s correct the function to adhere to the CEI pattern:

Corrected Function
solidity

```diff
function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
        bytes32 txn = keccak256(abi.encode(bridgeRequest));
        emit StartBridgeTransaction(bridgeRequest, txn);
        if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {
            revert IConnector_BridgeTransactionNotApproved(txn);
        }
        if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();
        if (
            destChainAddress[bridgeRequest.destChainId] == address(0)
                || destChainAddress[bridgeRequest.destChainId] != bridgeRequest.receiverAddress
        ) {
            revert IConnector_InvalidDestinationChain();
        }
        approvedBridgeTXN[txn] = 0;
+        _updateTokenInRegistry(bridgeRequest.inputToken);
        swapHandler.executeBridge(bridgeRequest);
-        _updateTokenInRegistry(bridgeRequest.inputToken);
    }
```
Changes Made:
Moved _updateTokenInRegistry(bridgeRequest.inputToken); before the call to swapHandler.executeBridge(bridgeRequest); to ensure all state updates are completed before interacting with external contracts.
Now, the function correctly follows the CEI pattern by performing all checks first, then updating the state, and finally interacting with external contracts.


## [QA] Informational Findings on LZHelperSender.sol

### [QA-1] : Use Ownable2Step instead of Ownable; https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L4
### [QA-2] : Change lzChainId to normalchainId; https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L10C12-L10C21


## [QA] Informational Findings on LZHelperReciever.sol

### [QA-1] : Use Ownable2Step instead of Ownable;https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L4
### [QA-2] : Use `uint32` for chainId to save gas

## [QA] Informational Findings on AccountingManager.sol
## [QA-1] : Misinformation in natspec for `AccountingManager::valueOracle` definition
**Summary:**

Natspec states _/// @notice valueOracle is the **address** of the value oracle that is used to calculate the price of the assets (used to get TVL of holding tokens)_. Referred to `valueOracle` as an `address`.


**Tool used**

- Manual review

**Recommended Mitigation:**

Improve natspec for `valueOracle` to be:

```diff
-   /// @notice valueOracle is the address of the value oracle that is used to calculate the price of the assets (used to get TVL of holding tokens)
+   /// @notice valueOracle is the interface of the value oracle that is used to calculate the price of the assets (used to get TVL of holding tokens)
```

### [QA-2] Misplaced event fields when emitting `event ExecuteDeposit` and `CalculateDeposit` in `AccountingManager::executeDeposit`

**Summary:**

Misplacement of `uint256 amount` with `data.shares` and `uint256 shares` with `data.amount` field when emitting `event ExecuteDeposit` in `executeDeposit` function

**Vulnerability Detail**

**Impact:**

Misplaced event fields causes incorrect data to be emitted which can cause unexpected behaviour from dapps or external services that are dependent on the emitted event

**Proof of Concept:**

**Tool used**

- Manual review

**Recommended Mitigation:**

Refactor `event ExecuteDeposit` emission in `executeDeposit` as follows:

```diff
-   emit ExecuteDeposit(
-       firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
-   );
+   emit ExecuteDeposit(
+       firstTemp, data.receiver, block.timestamp, data.amount, data.shares, data.shares * 1e18 / data.amount
+   );
```

Refactor `event  CalculateDeposit` emission in ` CalculateDeposit` as follows:

```diff
-   emit  CalculateDeposit(
-       firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
-   );
+   emit CalculateDeposit(
+       firstTemp, data.receiver, block.timestamp, data.amount, data.shares, data.shares * 1e18 / data.amount
+   );
```

## [QA-3] Misplaced event fields when emitting `event ResetFee` in `AccountingManager::checkIfTVLHasDropped`

**Summary:**

Passed `currentProfit` for `uint256 storedProfitAmount` and `storedProfitForFee` for `uint256 currentProfit` when emitting `ResetFee` event.

**Vulnerability Detail**

**Impact:**

Any dapp or service dependent on `event ResetFee` would have unexpected behaviour as a result of the misplacement of fields when emitting `event Reset`

**Proof of Concept:**

**Tool used**

- Manual review

**Recommended Mitigation:**

Refactor `checkIfTVLHasDroped` event emission code block as follows:

```diff
-   emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
+   emit ResetFee(storedProfitForFee, currentProfit, block.timestamp);
```