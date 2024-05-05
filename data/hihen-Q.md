# QA Report

Issues not included in the 4naly3er-report.

## Summary

### Low Issues

Total **153 instances** over **16 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[L-01]](#l-01-array-length-is-not-checked-before-access-its-index) | Array length is not checked before access its index | 30 |
| [[L-02]](#l-02-a-year-is-not-always-365-days) | A year is not always 365 days | 1 |
| [[L-03]](#l-03-variables-shadowing-other-definitions) | Variables shadowing other definitions | 2 |
| [[L-04]](#l-04-missing-zero-address-check-in-constructor) | Missing zero address check in constructor | 13 |
| [[L-05]](#l-05-named-return-variable-used-before-assignment) | Named return variable used before assignment | 1 |
| [[L-06]](#l-06-array-is-pushed-but-not-poped) | Array is `push()`ed but not `pop()`ed | 3 |
| [[L-07]](#l-07-state-variables-not-limited-to-reasonable-values) | State variables not limited to reasonable values | 3 |
| [[L-08]](#l-08-vulnerable-versions-of-packages-are-being-used) | Vulnerable versions of packages are being used | 12 |
| [[L-09]](#l-09-constructor--initialization-function-lacks-parameter-validation) | Constructor / initialization function lacks parameter validation | 3 |
| [[L-10]](#l-10-unsafe-solidity-low-level-call-can-cause-gas-grief-attack) | Unsafe solidity low-level call can cause gas grief attack | 4 |
| [[L-11]](#l-11-functions-calling-contractsaddresses-with-transfer-hooks-should-be-protected-by-reentrancy-guard) | Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard | 9 |
| [[L-12]](#l-12-critical-functions-should-be-controlled-by-time-locks) | Critical functions should be controlled by time locks | 41 |
| [[L-13]](#l-13-missing-contract-existence-checks-before-low-level-calls) | Missing contract existence checks before low-level calls | 3 |
| [[L-14]](#l-14-tokens-may-be-minted-to-the-zero-address) | Tokens may be minted to the zero address | 8 |
| [[L-15]](#l-15-sending-tokens-within-loops) | Sending tokens within loops | 3 |
| [[L-16]](#l-16-code-does-not-follow-the-best-practice-of-check-effects-interaction) | Code does not follow the best practice of check-effects-interaction | 17 |

### Non Critical Issues

Total **1816 instances** over **79 issues**:

|ID|Issue|Instances|
|:--:|:---|:--:|
| [[N-01]](#n-01-abiencodepacked-should-be-replaced-with-bytesconcat) | `abi.encodePacked()` should be replaced with `bytes.concat()` | 1 |
| [[N-02]](#n-02-import-declarations-should-import-specific-identifiers-rather-than-the-whole-file) | Import declarations should import specific identifiers, rather than the whole file | 110 |
| [[N-03]](#n-03-visibility-of-state-variables-is-not-explicitly-defined) | Visibility of state variables is not explicitly defined | 15 |
| [[N-04]](#n-04-names-of-constants-should-use-the-upper_case_with_underscores-style) | Names of constants should use the UPPER_CASE_WITH_UNDERSCORES style | 1 |
| [[N-05]](#n-05-names-of-privateinternal-functions-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` functions should be prefixed with an underscore | 1 |
| [[N-06]](#n-06-names-of-privateinternal-state-variables-should-be-prefixed-with-an-underscore) | Names of `private`/`internal` state variables should be prefixed with an underscore | 18 |
| [[N-07]](#n-07-the-nonreentrant-modifier-should-occur-before-all-other-modifiers) | The `nonReentrant` `modifier` should occur before all other modifiers | 92 |
| [[N-08]](#n-08-use-of-override-is-unnecessary) | Use of `override` is unnecessary | 49 |
| [[N-09]](#n-09-unused-structs) | Unused `struct`s | 2 |
| [[N-10]](#n-10-custom-errors-should-be-used-rather-than-revertrequire) | Custom errors should be used rather than `revert()`/`require()` | 88 |
| [[N-11]](#n-11-add-inline-comments-for-unnamed-parameters) | Add inline comments for unnamed parameters | 17 |
| [[N-12]](#n-12-consider-providing-a-ranged-getter-for-array-state-variables) | Consider providing a ranged getter for array state variables | 2 |
| [[N-13]](#n-13-consider-splitting-complex-checks-into-multiple-steps) | Consider splitting complex checks into multiple steps | 3 |
| [[N-14]](#n-14-missing-checks-for-empty-bytes-when-updating-bytes-state-variables) | Missing checks for empty bytes when updating bytes state variables | 1 |
| [[N-15]](#n-15-complex-casting) | Complex casting | 1 |
| [[N-16]](#n-16-complex-math-should-be-split-into-multiple-steps) | Complex math should be split into multiple steps | 3 |
| [[N-17]](#n-17-consider-adding-a-blockdeny-list) | Consider adding a block/deny-list | 7 |
| [[N-18]](#n-18-convert-simple-if-statements-to-ternary-expressions) | Convert simple `if`-statements to ternary expressions | 4 |
| [[N-19]](#n-19-contract-name-does-not-match-its-filename) | Contract name does not match its filename | 6 |
| [[N-20]](#n-20-consider-using-accesscontroldefaultadminrules-rather-than-accesscontrol) | Consider using `AccessControlDefaultAdminRules` rather than `AccessControl` | 1 |
| [[N-21]](#n-21-upper_case-names-should-be-reserved-for-constantimmutable-variables) | UPPER_CASE names should be reserved for `constant`/`immutable` variables | 44 |
| [[N-22]](#n-22-consider-emitting-an-event-at-the-end-of-the-constructor) | Consider emitting an event at the end of the constructor | 39 |
| [[N-23]](#n-23-empty-function-body-without-comments) | Empty function body without comments | 4 |
| [[N-24]](#n-24-events-are-emitted-without-the-sender-information) | Events are emitted without the sender information | 39 |
| [[N-25]](#n-25-function-state-mutability-can-be-restricted-to-pure) | Function state mutability can be restricted to pure | 15 |
| [[N-26]](#n-26-imports-could-be-organized-more-systematically) | Imports could be organized more systematically | 30 |
| [[N-27]](#n-27-invalid-natspec-comment-style) | Invalid NatSpec comment style | 2 |
| [[N-28]](#n-28-openzeppelincontracts-should-be-upgraded-to-a-newer-version) | @openzeppelin/contracts should be upgraded to a newer version | 34 |
| [[N-29]](#n-29-lib-openzeppelincontracts-upgradeable-should-be-upgraded-to-a-newer-version) | Lib @openzeppelin/contracts-upgradeable should be upgraded to a newer version | 1 |
| [[N-30]](#n-30-expressions-for-constant-values-should-use-immutable-rather-than-constant) | Expressions for constant values should use `immutable` rather than `constant` | 4 |
| [[N-31]](#n-31-consider-moving-duplicated-strings-to-constants) | Consider moving duplicated strings to constants | 2 |
| [[N-32]](#n-32-contracts-containing-only-utility-functions-should-be-made-into-libraries) | Contracts containing only utility functions should be made into libraries | 1 |
| [[N-33]](#n-33-contract-uses-both-requirerevert-as-well-as-custom-errors) | Contract uses both `require()`/`revert()` as well as custom errors | 16 |
| [[N-34]](#n-34-error-names-should-use-capwords-style) | Error names should use CapWords style | 5 |
| [[N-35]](#n-35-contract-name-does-not-follow-the-solidity-style-guide) | Contract name does not follow the Solidity Style Guide | 1 |
| [[N-36]](#n-36-functions-should-be-named-in-mixedcase-style) | Functions should be named in mixedCase style | 42 |
| [[N-37]](#n-37-variable-names-for-immutables-should-use-upper_case_with_underscores) | Variable names for `immutable`s should use UPPER_CASE_WITH_UNDERSCORES | 5 |
| [[N-38]](#n-38-names-of-publicexternal-functions-and-state-variables-should-not-be-prefixed-with-underscore) | Names of `public`/`external` functions and state variables should NOT be prefixed with underscore | 35 |
| [[N-39]](#n-39-named-imports-of-parent-contracts-are-missing) | Named imports of parent contracts are missing | 51 |
| [[N-40]](#n-40-constants-should-be-put-on-the-left-side-of-comparisons) | Constants should be put on the left side of comparisons | 154 |
| [[N-41]](#n-41-else-block-not-required) | `else`-block not required | 1 |
| [[N-42]](#n-42-large-multiples-of-ten-should-use-scientific-notation) | Large multiples of ten should use scientific notation | 3 |
| [[N-43]](#n-43-todos-left-in-the-code) | `TODO`s left in the code | 2 |
| [[N-44]](#n-44-high-cyclomatic-complexity) | High cyclomatic complexity | 1 |
| [[N-45]](#n-45-typos) | Typos | 77 |
| [[N-46]](#n-46-consider-bounding-input-array-length) | Consider bounding input array length | 31 |
| [[N-47]](#n-47-unnecessary-casting) | Unnecessary casting | 16 |
| [[N-48]](#n-48-unused-contract-variables) | Unused contract variables | 1 |
| [[N-49]](#n-49-unused-function-parameters) | Unused function parameters | 25 |
| [[N-50]](#n-50-unused-import) | Unused import | 26 |
| [[N-51]](#n-51-unused-local-variables) | Unused local variables | 12 |
| [[N-52]](#n-52-unused-modifiers) | Unused modifiers | 2 |
| [[N-53]](#n-53-unused-named-return) | Unused named return | 22 |
| [[N-54]](#n-54-use-delete-instead-of-assigning-values-to-false) | Use delete instead of assigning values to `false` | 1 |
| [[N-55]](#n-55-consider-using-delete-rather-than-assigning-zero-to-clear-values) | Consider using `delete` rather than assigning zero to clear values | 9 |
| [[N-56]](#n-56-consider-using-eip-5267-to-securely-describe-eip-712-domains) | Consider using EIP-5267 to securely describe EIP-712 domains | 2 |
| [[N-57]](#n-57-use-the-latest-solidity-version) | Use the latest Solidity version | 41 |
| [[N-58]](#n-58-use-transfer-libraries-instead-of-low-level-calls-to-transfer-native-tokens) | Use transfer libraries instead of low level calls to transfer native tokens | 2 |
| [[N-59]](#n-59-use-a-struct-to-encapsulate-multiple-function-parameters) | Use a struct to encapsulate multiple function parameters | 12 |
| [[N-60]](#n-60-returning-a-struct-instead-of-a-bunch-of-variables-is-better) | Returning a struct instead of a bunch of variables is better | 6 |
| [[N-61]](#n-61-events-that-mark-critical-parameter-changes-should-contain-both-the-old-and-the-new-value) | Events that mark critical parameter changes should contain both the old and the new value | 18 |
| [[N-62]](#n-62-contract-variables-should-have-comments) | Contract variables should have comments | 13 |
| [[N-63]](#n-63-missing-event-when-a-state-variables-is-set-in-constructor) | Missing event when a state variables is set in constructor | 68 |
| [[N-64]](#n-64-empty-bytes-check-is-missing) | Empty bytes check is missing | 20 |
| [[N-65]](#n-65-dont-define-functions-with-the-same-name-in-a-contract) | Don't define functions with the same name in a contract | 7 |
| [[N-66]](#n-66-multiple-mappings-with-same-keys-can-be-combined-into-a-single-struct-mapping-for-readability) | Multiple mappings with same keys can be combined into a single struct mapping for readability | 7 |
| [[N-67]](#n-67-function-state-mutability-can-be-restricted-to-view) | Function state mutability can be restricted to view | 1 |
| [[N-68]](#n-68-missing-event-for-critical-changes) | Missing event for critical changes | 6 |
| [[N-69]](#n-69-duplicated-requirerevert-checks-should-be-refactored) | Duplicated `require()`/`revert()` checks should be refactored | 21 |
| [[N-70]](#n-70-consider-adding-emergency-stop-functionality) | Consider adding emergency-stop functionality | 32 |
| [[N-71]](#n-71-avoid-the-use-of-sensitive-terms) | Avoid the use of sensitive terms | 20 |
| [[N-72]](#n-72-missing-checks-for-uint-state-variable-assignments) | Missing checks for uint state variable assignments | 6 |
| [[N-73]](#n-73-use-the-modern-upgradeable-contract-paradigm) | Use the Modern Upgradeable Contract Paradigm | 39 |
| [[N-74]](#n-74-large-or-complicated-code-bases-should-implement-invariant-tests) | Large or complicated code bases should implement invariant tests | 1 |
| [[N-75]](#n-75-the-default-value-is-manually-set-when-it-is-declared) | The default value is manually set when it is declared | 60 |
| [[N-76]](#n-76-contracts-should-have-all-publicexternal-functions-exposed-by-interfaces) | Contracts should have all `public`/`external` functions exposed by `interface`s | 37 |
| [[N-77]](#n-77-top-level-declarations-should-be-separated-by-at-least-two-lines) | Top-level declarations should be separated by at least two lines | 174 |
| [[N-78]](#n-78-consider-adding-formal-verification-proofs) | Consider adding formal verification proofs | 41 |
| [[N-79]](#n-79-use-scopes-sparingly) | Use scopes sparingly | 7 |

## Low Issues

### [L-01] Array length is not checked before access its index

Accessing the elements of the array without checking or ensuring the validity of the access index in advance. It may result in an unexpected out-of-bounds error, or may result in missing elements when trying to traverse the entire array.

<details>
<summary>There are 30 instances (click to show):</summary>

- *Registry.sol* ( [195-195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L195-L195) ):

```solidity
195:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
```

- *BalancerConnector.sol* ( [78-78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L78-L78), [78-78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L78-L78) ):

```solidity
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);

78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
```

- *BalancerFlashLoan.sol* ( [76-76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L76-L76), [77-77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L77-L77), [77-77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L77-L77), [77-77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L77-L77), [86-86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L86-L86), [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L91-L91) ):

```solidity
76:                 tokens[i].safeTransfer(receiver, amounts[i]);

77:                 amounts[i] = amounts[i] + feeAmounts[i];

77:                 amounts[i] = amounts[i] + feeAmounts[i];

77:                 amounts[i] = amounts[i] + feeAmounts[i];

86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");

91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
```

- *Keepers.sol* ( [45-45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L45-L45), [48-48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L48-L48) ):

```solidity
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) {

48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
```

- *BaseConnector.sol* ( [181-181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L181-L181), [183-183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L183-L183), [184-184](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L184-L184), [213-213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L213-L213), [213-213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L213-L213), [213-213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L213-L213), [213-213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L213-L213), [216-216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L216-L216), [217-217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L217-L217), [217-217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L217-L217), [217-217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L217-L217) ):

```solidity
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

183:             if (_balanceAfter < amounts[i] + _balance) {

184:                 revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);

213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)

213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)

213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)

213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)

216:             _updateTokenInRegistry(tokensOut[i]);

217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);

217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);

217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
```

- *ConnectorMock2.sol* ( [44-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L44-L44) ):

```solidity
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
```

- *NoyaValueOracle.sol* ( [42-42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L42-L42), [56-56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56), [56-56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56) ):

```solidity
42:             defaultPriceSource[baseCurrencies[i]] = oracles[i];

56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);

56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
```

- *ChainlinkOracleConnector.sol* ( [75-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), [75-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), [76-76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L76-L76), [76-76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L76-L76) ):

```solidity
75:             assetsSources[assets[i]][baseTokens[i]] = sources[i];

75:             assetsSources[assets[i]][baseTokens[i]] = sources[i];

76:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);

76:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);
```

</details>

### [L-02] A year is not always 365 days

A year is not always 365 days or any fixed days or seconds. On leap years, the number of days is 366, so calculations during those years will return the wrong value.

There is 1 instance:

- *AccountingManager.sol* ( [518-518](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L518-L518) ):

```solidity
518:             (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;
```

### [L-03] Variables shadowing other definitions

A variable declaration shadowing any other existing definition is error-prone. It can cause confusion for developers, potentially introduce bugs, and reduce the readability and maintainability.

There are 2 instances:

- *LZHelperReceiver.sol* ( [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31-L31) ):

```solidity
/// @audit Shadows `state variable _owner`
31:     constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }
```

- *LZHelperSender.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L29-L29) ):

```solidity
/// @audit Shadows `state variable _owner`
29:     constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
```

### [L-04] Missing zero address check in constructor

Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

<details>
<summary>There are 13 instances (click to show):</summary>

- *Registry.sol* ( [66-66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L66-L66) ):

```solidity
/// @audit `_flashLoan not checked`
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
```

- *AerodromeConnector.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L40-L40) ):

```solidity
/// @audit `_voter not checked`
40:     constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)
```

- *Dolomite.sol* ( [18-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L18-L23) ):

```solidity
/// @audit `_dolomiteMargin not checked`
/// @audit `_borrowPositionProxy not checked`
18:     constructor(
19:         address _depositWithdrawalProxy,
20:         address _dolomiteMargin,
21:         address _borrowPositionProxy,
22:         BaseConnectorCP memory baseConnectorParams
23:     ) BaseConnector(baseConnectorParams) {
```

- *UNIv3Connector.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L27-L27) ):

```solidity
/// @audit `_positionManager not checked`
/// @audit `_factory not checked`
27:     constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
```

- *Keepers.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L27-L27) ):

```solidity
/// @audit `_owners not checked`
27:     constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
```

- *ConnectorMock2.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L22-L22) ):

```solidity
/// @audit `_registry not checked`
22:     constructor(address _registry, uint256 _vaultId) {
```

- *GenericSwapAndBridgeHandler.sol* ( [34-34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L34) ):

```solidity
/// @audit `usersAddresses not checked`
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
```

- *LifiImplementation.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L27) ):

```solidity
/// @audit `swapHandler not checked`
/// @audit `_lifi not checked`
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
```

- *UniswapValueOracle.sol* ( [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L31) ):

```solidity
/// @audit `_factory not checked`
/// @audit `_registry not checked`
31:     constructor(address _factory, PositionRegistry _registry) {
```

</details>

### [L-05] Named return variable used before assignment

As no value is written to the variable, the default value is always read. This is usually due to a bug in the code logic that causes an invalid value to be used.

There is 1 instance:

- *FraxConnector.sol* ( [162-162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L162-L162) ):

```solidity
/// @audit tvl
162:         return tvl;
```

### [L-06] Array is `push()`ed but not `pop()`ed

Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

There are 3 instances:

- *Registry.sol* ( [141-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L141-L141), [312-321](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L312-L321) ):

```solidity
141:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));

312:             vault.holdingPositions.push(
313:                 HoldingPI(
314:                     vaults[vaultId].trustedPositionsBP[_positionId].calculatorConnector,
315:                     msg.sender,
316:                     _positionId,
317:                     d,
318:                     AD,
319:                     type(uint256).max
320:                 )
321:             );
```

- *GenericSwapAndBridgeHandler.sol* ( [149-149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L149-L149) ):

```solidity
149:             routes.push(_routes[i]);
```

### [L-07] State variables not limited to reasonable values

Consider adding appropriate minimum/maximum value checks to ensure that the following state variables can never be used to excessively harm users, including via griefing.

There are 3 instances:

- *AccountingManager.sol* ( [668-668](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L668-L668), [669-669](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L669-L669) ):

```solidity
668:         depositLimitPerTransaction = _depositLimitPerTransaction;

669:         depositLimitTotalAmount = _depositTotalAmount;
```

- *UniswapValueOracle.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L40-L40) ):

```solidity
40:         period = _period;
```

### [L-08] Vulnerable versions of packages are being used

This project is using specific package versions which are vulnerable to the specific CVEs listed below. Consider switching to more recent versions of these packages that don't have these vulnerabilities.
- [CVE-2023-49798](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-49798) - **HIGH** - (`@openzeppelin/contracts 4.9.4`): OpenZeppelin Contracts is a library for smart contract development. A merge issue when porting the 5.0.1 patch to the 4.9 branch caused a line duplication. In the version of `Multicall.sol` released in `@openzeppelin/contracts@4.9.4` and `@openzeppelin/contracts-upgradeable@4.9.4`, all subcalls are executed twice. Concretely, this exposes a user to unintentionally duplicate operations like asset transfers. The duplicated delegatecall was removed in version 4.9.5. The 4.9.4 version is marked as deprecated. Users are advised to upgrade. There are no known workarounds for this issue.

- [CVE-2023-49798](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-49798) - **HIGH** - (`@openzeppelin/contracts-upgradeable 4.9.4`): OpenZeppelin Contracts is a library for smart contract development. A merge issue when porting the 5.0.1 patch to the 4.9 branch caused a line duplication. In the version of `Multicall.sol` released in `@openzeppelin/contracts@4.9.4` and `@openzeppelin/contracts-upgradeable@4.9.4`, all subcalls are executed twice. Concretely, this exposes a user to unintentionally duplicate operations like asset transfers. The duplicated delegatecall was removed in version 4.9.5. The 4.9.4 version is marked as deprecated. Users are advised to upgrade. There are no known workarounds for this issue.

- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`@openzeppelin/contracts >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-40014](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-40014) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.0.0 <4.9.3`): OpenZeppelin Contracts is a library for secure smart contract development. Starting in version 4.0.0 and prior to version 4.9.3, contracts using `ERC2771Context` along with a custom trusted forwarder may see `_msgSender` return `address(0)` in calls that originate from the forwarder with calldata shorter than 20 bytes. This combination of circumstances does not appear to be common, in particular it is not the case for `MinimalForwarder` from OpenZeppelin Contracts, or any deployed forwarder the team is aware of, given that the signer address is appended to all calls that originate from these forwarders. The problem has been patched in v4.9.3.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`@openzeppelin/contracts >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

- [CVE-2023-34459](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-34459) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.7.0 <4.9.2`): OpenZeppelin Contracts is a library for smart contract development. Starting in version 4.7.0 and prior to version 4.9.2, when the `verifyMultiProof`, `verifyMultiProofCalldata`, `procesprocessMultiProof`, or `processMultiProofCalldat` functions are in use, it is possible to construct merkle trees that allow forging a valid multiproof for an arbitrary set of leaves. A contract may be vulnerable if it uses multiproofs for verification and the merkle tree that is processed includes a node with value 0 at depth 1 (just under the root). This could happen inadvertedly for balanced trees with 3 leaves or less, if the leaves are not hashed. This could happen deliberately if a malicious tree builder includes such a node in the tree. A contract is not vulnerable if it uses single-leaf proving (`verify`, `verifyCalldata`, `processProof`, or `processProofCalldata`), or if it uses multiproofs with a known tree that has hashed leaves. Standard merkle trees produced or validated with the @openzeppelin/merkle-tree library are safe. The problem has been patched in version 4.9.2. Some workarounds are available. For those using multiproofs: When constructing merkle trees hash the leaves and do not insert empty nodes in your trees. Using the @openzeppelin/merkle-tree package eliminates this issue. Do not accept user-provided merkle roots without reconstructing at least the first level of the tree. Verify the merkle tree structure by reconstructing it from the leaves.

- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** - (`@openzeppelin/contracts >=4.7.0 <4.8.2`): OpenZeppelin Contracts is a library for secure smart contract development. The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.

- [CVE-2023-30542](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30542) - **HIGH** - (`@openzeppelin/contracts-upgradeable >=4.7.0 <4.8.2`): OpenZeppelin Contracts is a library for secure smart contract development. The proposal creation entrypoint (`propose`) in `GovernorCompatibilityBravo` allows the creation of proposals with a `signatures` array shorter than the `calldatas` array. This causes the additional elements of the latter to be ignored, and if the proposal succeeds the corresponding actions would eventually execute without any calldata. The `ProposalCreated` event correctly represents what will eventually execute, but the proposal parameters as queried through `getActions` appear to respect the original intended calldata. This issue has been patched in 4.8.3. As a workaround, ensure that all proposals that pass through governance have equal length `signatures` and `calldatas` parameters.

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`@openzeppelin/contracts >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

- [CVE-2023-30541](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-30541) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=3.2.0 <4.8.3`): OpenZeppelin Contracts is a library for secure smart contract development. A function in the implementation contract may be inaccessible if its selector clashes with one of the proxy's own selectors. Specifically, if the clashing function has a different signature with incompatible ABI encoding, the proxy could revert while attempting to decode the arguments from calldata. The probability of an accidental clash is negligible, but one could be caused deliberately and could cause a reduction in availability. The issue has been fixed in version 4.8.3. As a workaround if a function appears to be inaccessible for this reason, it may be possible to craft the calldata such that ABI decoding does not fail at the proxy and the function is properly proxied through.

- [CVE-2023-26488](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-26488) - **MEDIUM** - (`@openzeppelin/contracts >=4.8.0 <4.8.2`): OpenZeppelin Contracts is a library for secure smart contract development. The ERC721Consecutive contract designed for minting NFTs in batches does not update balances when a batch has size 1 and consists of a single token. Subsequent transfers from the receiver of that token may overflow the balance as reported by `balanceOf`. The issue exclusively presents with batches of size 1. The issue has been patched in 4.8.2.

- [CVE-2023-26488](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-26488) - **MEDIUM** - (`@openzeppelin/contracts-upgradeable >=4.8.0 <4.8.2`): OpenZeppelin Contracts is a library for secure smart contract development. The ERC721Consecutive contract designed for minting NFTs in batches does not update balances when a batch has size 1 and consists of a single token. Subsequent transfers from the receiver of that token may overflow the balance as reported by `balanceOf`. The issue exclusively presents with batches of size 1. The issue has been patched in 4.8.2.

There are 12 instances:

- Global finding

### [L-09] Constructor / initialization function lacks parameter validation

Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

There are 3 instances:

- *NoyaGovernanceBase.sol* ( [21-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L21-L21) ):

```solidity
/// @audit `_vaultId`
21:     constructor(PositionRegistry _registry, uint256 _vaultId) {
```

- *ConnectorMock2.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L22-L22) ):

```solidity
/// @audit `_vaultId`
22:     constructor(address _registry, uint256 _vaultId) {
```

- *OmnichainManagerBaseChain.sol* ( [19-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L21) ):

```solidity
/// @audit `dl`
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
20:         OmnichainLogic(_lzHelper, baseConnectorParams)
21:     {
```

### [L-10] Unsafe solidity low-level call can cause gas grief attack

Using the low-level calls of a solidity address can leave the contract open to gas grief attacks. These attacks occur when the called contract returns a large amount of data.
So when calling an external contract, it is necessary to check the length of the return data before reading/copying it (using `returndatasize()`).

There are 4 instances:

- *BalancerFlashLoan.sol* ( [81-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L81-L81) ):

```solidity
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
```

- *Keepers.sol* ( [116-116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L116-L116) ):

```solidity
116:         (bool success,) = destination.call{ gas: gasLimit }(data);
```

- *LifiImplementation.sol* ( [176-176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176), [195-195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195) ):

```solidity
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);

195:             (bool success,) = payable(userAddress).call{ value: amount }("");
```

### [L-11] Functions calling contracts/addresses with transfer hooks should be protected by reentrancy guard

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks opens the users of this protocol up to [read-only reentrancy vulnerability](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect them except by block-listing the entire protocol.

<details>
<summary>There are 9 instances (click to show):</summary>

- *AccountingManager.sol* ( [156-156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L156-L156) ):

```solidity
156:             IERC20(token).safeTransfer(address(msg.sender), amount);
```

- *BalancerFlashLoan.sol* ( [76-76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L76-L76), [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L91-L91) ):

```solidity
76:                 tokens[i].safeTransfer(receiver, amounts[i]);

91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
```

- *BaseConnector.sol* ( [96-96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L96-L96), [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L99-L99), [104-104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L104-L104) ):

```solidity
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);

99:             IERC20(token).safeTransfer(address(msg.sender), amount);

104:             IERC20(token).safeTransfer(msg.sender, amount);
```

- *ConnectorMock2.sol* ( [32-32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L32-L32), [36-36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L36-L36) ):

```solidity
32:             IERC20(token).safeTransfer(msg.sender, amount);

36:         IERC20(token).safeTransfer(msg.sender, amountToSend);
```

- *LifiImplementation.sol* ( [198-198](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L198-L198) ):

```solidity
198:             IERC20(token).safeTransfer(userAddress, amount);
```

</details>

### [L-12] Critical functions should be controlled by time locks

It is a good practice to give time for users to react and adjust to critical changes. A timelock provides more guarantees and reduces the level of trust required, thus decreasing risk for users. It also indicates that the project is legitimate (less risk of a malicious owner making a sandwich attack on a user).

<details>
<summary>There are 41 instances (click to show):</summary>

- *AccountingManager.sol* ( [124-124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L124-L124), [135-139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L135-L139), [185-185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L185-L185), [360-360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L360-L360) ):

```solidity
124:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {

135:     function setFeeReceivers(
136:         address _withdrawFeeReceiver,
137:         address _performanceFeeReceiver,
138:         address _managementFeeReceiver
139:     ) public onlyMaintainer {

185:     function _update(address from, address to, uint256 amount) internal override {

360:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
```

- *Registry.sol* ( [84-84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L84-L84), [106-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L106-L117), [158-166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L158-L166) ):

```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

106:     function addVault(
107:         uint256 vaultId,
108:         address _accountingManager,
109:         address _baseToken,
110:         address _governer,
111:         address _maintainer,
112:         address _maintainerWithoutTimelock,
113:         address _keeperContract,
114:         address _watcher,
115:         address _emergency,
116:         address[] calldata _trustedTokens
117:     ) external onlyRole(MAINTAINER_ROLE) {

158:     function changeVaultAddresses(
159:         uint256 vaultId,
160:         address _governer,
161:         address _maintainer,
162:         address _maintainerWithoutTimelock,
163:         address _keeperContract,
164:         address _watcher,
165:         address _emergency
166:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {
```

- *BalancerConnector.sol* ( [64-70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64-L70) ):

```solidity
64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant {
```

- *CamelotConnector.sol* ( [43-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L43-L43), [65-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L65-L69) ):

```solidity
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {

65:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
66:         external
67:         onlyManager
68:         nonReentrant
69:     {
```

- *CurveConnector.sol* ( [117-121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L117-L121) ):

```solidity
117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant
121:     {
```

- *Dolomite.sol* ( [58-62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L58-L62), [98-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L98-L98) ):

```solidity
58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager
61:         nonReentrant
62:     {

98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
```

- *GearBoxV3.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L24-L24), [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L41-L41) ):

```solidity
24:     function openAccount(address facade, uint256 ref) public onlyManager {

41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {
```

- *MaverickConnector.sol* ( [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L91-L91), [115-119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L115-L119) ):

```solidity
91:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {

115:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
116:         external
117:         onlyManager
118:         nonReentrant
119:     {
```

- *PancakeswapConnector.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L40-L40) ):

```solidity
40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant {
```

- *PrismaConnector.sol* ( [52-56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L52-L56), [75-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L75-L75), [129-129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L129-L129) ):

```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {

75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {

129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {
```

- *UNIv3Connector.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L40-L40) ):

```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {
```

- *Keepers.sol* ( [42-42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42-L42), [63-63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L63-L63) ):

```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {

63:     function setThreshold(uint8 _threshold) public onlyOwner {
```

- *BaseConnector.sol* ( [153-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L153-L153) ):

```solidity
153:     function updateTokenInRegistry(address token) public onlyManager {
```

- *ConnectorMock2.sol* ( [79-79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L79-L79), [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L91-L91) ):

```solidity
79:     function _updateTokenInRegistry(address token, bool remove) internal {

91:     function _updateTokenInRegistry(address token) internal {
```

- *LZHelperReceiver.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40), [52-52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52) ):

```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {

52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
```

- *LZHelperSender.sol* ( [51-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L51-L51), [63-63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L63-L63) ):

```solidity
51:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {

63:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
```

- *OmnichainLogic.sol* ( [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46-L46), [57-57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57-L57), [68-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68) ):

```solidity
46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer {

57:     function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {

68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
```

- *OmnichainManagerNormalChain.sol* ( [28-28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28) ):

```solidity
28:     function updateTVLInfo() external onlyManager {
```

- *GenericSwapAndBridgeHandler.sol* ( [48-48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L48), [68-71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L71), [80-80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80) ):

```solidity
48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {

68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     {

80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency {
```

- *LifiImplementation.sol* ( [45-45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45) ):

```solidity
45:     function addHandler(address _handler, bool state) external onlyOwner {
```

- *NoyaValueOracle.sol* ( [61-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61) ):

```solidity
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {
```

- *UniswapValueOracle.sol* ( [48-48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48) ):

```solidity
48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {
```

</details>

### [L-13] Missing contract existence checks before low-level calls

Low-level calls return success if there is no code present at the specified address. In addition to the zero-address checks, add a check to verify that `<address>.code.length > 0`.

There are 3 instances:

- *BalancerFlashLoan.sol* ( [81-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L81-L81) ):

```solidity
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
```

- *Keepers.sol* ( [116-116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L116-L116) ):

```solidity
116:         (bool success,) = destination.call{ gas: gasLimit }(data);
```

- *LifiImplementation.sol* ( [176-176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176) ):

```solidity
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);
```

### [L-14] Tokens may be minted to the zero address

Neither the listed functions, nor `_mint()` prevent minting to `address(0x0)`

<details>
<summary>There are 8 instances (click to show):</summary>

- *AccountingManager.sol* ( [278-278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L278-L278), [519-519](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L519-L519), [534-534](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L534-L534), [693-693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L693-L693) ):

```solidity
278:             _mint(data.receiver, data.shares);

519:         _mint(managementFeeReceiver, managementFeeAmount);

534:         _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);

693:     function mint(uint256 shares, address receiver) public override returns (uint256) {
```

- *PendleConnector.sol* ( [97-97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L97-L97), [116-116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L116-L116) ):

```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {

116:         market.mint(address(this), SYamount, PTamount);
```

- *SNXConnector.sol* ( [102-108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L102-L108) ):

```solidity
102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager {
```

- *UNIv3Connector.sol* ( [49-49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L49-L49) ):

```solidity
49:         (tokenId,,,) = positionManager.mint(p);
```

</details>

### [L-15] Sending tokens within loops

Performing token transfers in a loop is not recommended due to the "Fail-Silently" issue. If one transfer fails, the entire transaction fails, which can be problematic when dealing with multiple transfers. This can prevent subsequent recipients from receiving their transfers. Additionally, it can be exploited by malicious contracts to disrupt transfers. To mitigate this, the "withdraw pattern" is recommended, where each recipient triggers their own payment, separating transfer operations and reducing the chance of interference.

<details>
<summary>There are 3 instances (click to show):</summary>

- *AccountingManager.sol* ( [406-435](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L406-L435) ):

```solidity
406:         while (
407:             currentWithdrawGroup.lastId > firstTemp
408:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
409:                 && i < maxIterations
410:         ) {
411:             i += 1;
412:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
413:             uint256 shares = data.shares;
414:             // calculate the base token amount that the user will receive based on the total available amount
415:             uint256 baseTokenAmount =
416:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
417: 
418:             withdrawRequestsByAddress[data.owner] -= shares;
419:             _burn(data.owner, shares);
420: 
421:             processedBaseTokenAmount += data.amount;
422:             {
423:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
424:                 withdrawFeeAmount += feeAmount;
425:                 baseTokenAmount = baseTokenAmount - feeAmount;
426:             }
427: 
428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);
429:             emit ExecuteWithdraw(
430:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
431:             );
432:             delete withdrawQueue.queue[firstTemp];
433:             // increment the first index of the withdraw queue
434:             firstTemp += 1;
435:         }
```

- *BalancerFlashLoan.sol* ( [74-78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L78), [89-93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L93) ):

```solidity
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 // send the tokens to the receiver
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }

89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             // send the tokens back to the vault
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
```

</details>

### [L-16] Code does not follow the best practice of check-effects-interaction

Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary>There are 17 instances (click to show):</summary>

- *AccountingManager.sol* ( [215-215](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L215-L215), [217-217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L217-L217), [218-218](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L218-L218), [298-298](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L298-L298), [432-432](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L432-L432), [434-434](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L434-L434), [436-436](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L436-L436), [441-441](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L441-L441), [444-444](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L444-L444), [561-561](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L561-L561), [569-569](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L569-L569) ):

```solidity
/// @audit `safeTransferFrom()` is called on line 205
215:         depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);

/// @audit `safeTransferFrom()` is called on line 205
217:         depositQueue.last += 1;

/// @audit `safeTransferFrom()` is called on line 205
218:         depositQueue.totalAWFDeposit += amount;

/// @audit `isAnActiveConnector()` is called on line 288
298:         depositQueue.first = firstTemp;

/// @audit `safeTransfer()` is called on line 428
432:             delete withdrawQueue.queue[firstTemp];

/// @audit `safeTransfer()` is called on line 428
434:             firstTemp += 1;

/// @audit `safeTransfer()` is called on line 428
436:         totalWithdrawnAmount += processedBaseTokenAmount;

/// @audit `safeTransfer()` is called on line 428
441:         withdrawQueue.first = firstTemp;

/// @audit `safeTransfer()` is called on line 428
444:             delete currentWithdrawGroup;

/// @audit `neededAssetsForWithdraw()` is called on line 550, triggering an external call - `balanceOf()`
561:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;

/// @audit `neededAssetsForWithdraw()` is called on line 550, triggering an external call - `balanceOf()`
569:         amountAskedForWithdraw += amountAskedForWithdraw_temp;
```

- *BalancerFlashLoan.sol* ( [44-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L44-L44) ):

```solidity
/// @audit `flashLoan()` is called on line 43
44:         caller = address(0);
```

- *PendleConnector.sol* ( [244-244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244) ):

```solidity
/// @audit `redeemRewards()` is called on line 242
244:         for (uint256 i = 0; i < rewardTokens.length; i++) {
```

- *BaseConnector.sol* ( [189-189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189) ):

```solidity
/// @audit `isAddressTrusted()` is called on line 174
189:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *ConnectorMock2.sol* ( [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L46-L46) ):

```solidity
/// @audit `sendTokensToTrustedAddress()` is called on line 44
46:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *LifiImplementation.sol* ( [94-94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L94-L94), [96-96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L96-L96) ):

```solidity
/// @audit `_forward()` is called on line 91, triggering an external call - `call()`
94:             balanceOut1 = address(_request.from).balance;

/// @audit `_forward()` is called on line 91, triggering an external call - `call()`
96:             balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);
```

</details>

## Non Critical Issues

### [N-01] `abi.encodePacked()` should be replaced with `bytes.concat()`

Solidity version 0.8.4 introduces `bytes.concat()`, which can be used to replace `abi.encodePacked()` on bytes/strings. It can make the intended operation clearer, leading to less reviewer confusion.

There is 1 instance:

- *Keepers.sol* ( [102-102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L102-L102) ):

```solidity
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
```

### [N-02] Import declarations should import specific identifiers, rather than the whole file

Using import declarations of the form `import {<identifier_name>} from "some/file.sol"` avoids polluting the symbol namespace making flattened files smaller, and speeds up compilation (but does not save any gas).

<details>
<summary>There are 110 instances (click to show):</summary>

- *AccountingManager.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L4), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L6), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L8) ):

```solidity
4: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";

6: import "../interface/Accounting/IAccountingManager.sol";

8: import "../helpers/TVLHelper.sol";
```

- *NoyaFeeReceiver.sol* ( [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L5) ):

```solidity
5: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```

- *Registry.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/AccessControl.sol";

5: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";

6: import "../interface/IPositionRegistry.sol";
```

- *AaveConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L4) ):

```solidity
4: import "../helpers/BaseConnector.sol";
```

- *AerodromeConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L8) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Aerodrome/IPool.sol";

6: import "../external/interfaces/Aerodrome/IRouter.sol";

7: import "../external/interfaces/Aerodrome/IVoter.sol";

8: import "../external/interfaces/Aerodrome/IGauge.sol";
```

- *BalancerConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L5) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Balancer/IBalancerVault.sol";
```

- *BalancerFlashLoan.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L8), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L10) ):

```solidity
8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";

10: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *CamelotConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L4), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L8), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L9) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";

6: import "../helpers/BaseConnector.sol";

7: import "../external/interfaces/Camelot/ICamelotRouter.sol";

8: import "../external/interfaces/Camelot/ICamelotFactory.sol";

9: import "../external/interfaces/Camelot/ICamelotPair.sol";
```

- *CompoundConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L4) ):

```solidity
4: import "../helpers/BaseConnector.sol";
```

- *CurveConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L6) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Curve/IRewardsGauge.sol";

6: import "../external/interfaces/Convex/IConvexBasicRewards.sol";
```

- *Dolomite.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L7) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Dolomite/IDepositWithdrawalProxy.sol";

6: import "../external/interfaces/Dolomite/IBorrowPositionProxyV1.sol";

7: import "../external/interfaces/Dolomite/IDolomiteMargin.sol";
```

- *FraxConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L5) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Frax/IFraxPair.sol";
```

- *GearBoxV3.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L6) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Gearbox/ICreditManagerV3.sol";

6: import "../external/interfaces/Gearbox/ICreditFacadeV3.sol";
```

- *LidoConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L5) ):

```solidity
4: import "../external/interfaces/Lido/ILidoWithdrawal.sol";

5: import "../helpers/BaseConnector.sol";
```

- *MaverickConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L5), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";

5: import "../external/interfaces/Maverick/IMaverickRouter.sol";

7: import "../helpers/BaseConnector.sol";
```

- *MorphoBlueConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L6) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Morpho/IMorpho.sol";

6: import "../external/libraries/Morpho/SharesMathLib.sol";
```

- *PancakeswapConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L6) ):

```solidity
4: import "./UNIv3Connector.sol";

5: import "../external/interfaces/Pancakeswap/IMasterChefV3.sol";

6: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721.sol";
```

- *PendleConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L5), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L8) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/libraries/Pendle/PendleLpOracleLib.sol";

8: import "../external/interfaces/Pendle/IPendleRouter.sol";
```

- *PrismaConnector.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L9) ):

```solidity
9: import "../helpers/BaseConnector.sol";
```

- *SNXConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L5) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/SNXV3/IV3CoreProxy.sol";
```

- *SiloConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L6) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Silo/ISilo.sol";

6: import "../external/libraries/Silo/SolvencyV2.sol";
```

- *StargateConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L5) ):

```solidity
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/Stargate/IStargateRouter.sol";
```

- *UNIv3Connector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L6) ):

```solidity
4: import "../external/interfaces/UNIv3/INonfungiblePositionManager.sol";

5: import "../external/interfaces/UNIv3/IUniswapV3Factory.sol";

6: import "../helpers/BaseConnector.sol";
```

- *Keepers.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-5.0/utils/cryptography/EIP712.sol";

5: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";

6: import "@openzeppelin/contracts-5.0/utils/cryptography/ECDSA.sol";
```

- *TimeLock.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/governance/TimelockController.sol";
```

- *Watchers.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L4) ):

```solidity
4: import "./Keepers.sol";
```

- *BaseConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L4), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L8), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L10), [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L11), [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L13) ):

```solidity
4: import "../interface/IConnector.sol";

7: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

8: import "@openzeppelin/contracts-5.0/token/ERC721/utils/ERC721Holder.sol";

10: import "../interface/valueOracle/INoyaValueOracle.sol";

11: import "../governance/Watchers.sol";

12: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721Receiver.sol";

13: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *ConnectorMock2.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *LZHelperReceiver.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

5: import "../OmniChainHandler/OmnichainManagerBaseChain.sol";

6: import "@layerzerolabs/lz-evm-oapp-v2/contracts/oapp/OApp.sol";
```

- *LZHelperSender.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L7) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

5: import "../OmniChainHandler/OmnichainManagerNormalChain.sol";

6: import "../OmniChainHandler/OmnichainManagerBaseChain.sol";

7: import "@layerzerolabs/lz-evm-oapp-v2/contracts/oapp/OApp.sol";
```

- *OmnichainLogic.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L5) ):

```solidity
4: import "../../helpers/SwapHandler/GenericSwapAndBridgeHandler.sol";

5: import "../BaseConnector.sol";
```

- *OmnichainManagerBaseChain.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L6) ):

```solidity
4: import "./OmnichainLogic.sol";

5: import "../../interface/IConnector.sol";

6: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *OmnichainManagerNormalChain.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L4), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L8) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

6: import "./OmnichainLogic.sol";

7: import "../TVLHelper.sol";

8: import "../LZHelpers/LZHelperSender.sol";
```

- *GenericSwapAndBridgeHandler.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L6), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L8) ):

```solidity
4: import "../../interface/valueOracle/INoyaValueOracle.sol";

5: import "../../governance/NoyaGovernanceBase.sol";

6: import "../../interface/SwapHandler/ISwapAndBridgeHandler.sol";

8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *LifiImplementation.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L4), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L8) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";

6: import "../../../interface/SwapHandler/ISwapAndBridgeHandler.sol";

7: import "../../../interface/ITokenTransferCallBack.sol";

8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *NoyaValueOracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

5: import "../../interface/valueOracle/INoyaValueOracle.sol";

6: import "../../accountingManager/Registry.sol";
```

- *ChainlinkOracleConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8) ):

```solidity
4: import "../../../interface/valueOracle/INoyaValueOracle.sol";

5: import "../../../interface/valueOracle/AggregatorV3Interface.sol";

6: import "../../../accountingManager/Registry.sol";

7: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

8: import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol";
```

- *UniswapValueOracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L6), [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L8) ):

```solidity
4: import "@uniswap/v3-core/contracts/interfaces/IUniswapV3Factory.sol";

5: import "../../../external/libraries/uniswap/OracleLibrary.sol";

6: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

7: import "../../../interface/valueOracle/INoyaValueOracle.sol";

8: import "../../../accountingManager/Registry.sol";
```

</details>

### [N-03] Visibility of state variables is not explicitly defined

To avoid misunderstandings and unexpected state accesses, it is recommended to explicitly define the visibility of each state variable.

<details>
<summary>There are 15 instances (click to show):</summary>

- *AaveConnector.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L18-L18), [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L22-L22) ):

```solidity
18:     address immutable pool;

22:     address immutable poolBaseToken;
```

- *AerodromeConnector.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L33-L33), [34-34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L34-L34) ):

```solidity
33:     IRouter aerodromeRouter;

34:     IVoter voter;
```

- *BalancerFlashLoan.sol* ( [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L17-L17) ):

```solidity
17:     address caller;
```

- *MaverickConnector.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L30-L30), [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L31-L31), [32-32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L32-L32), [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L33-L33) ):

```solidity
30:     address mav;

31:     address veMav;

32:     address maverickRouter;

33:     IPositionInspector positionInspector;
```

- *MorphoBlueConnector.sol* ( [14-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L14-L14) ):

```solidity
14:     uint256 constant ORACLE_PRICE_SCALE = 1e36;
```

- *StargateConnector.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L22-L22), [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L23-L23), [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L24-L24) ):

```solidity
22:     IStargateLPStaking LPStaking;

23:     IStargateRouter stargateRouter;

24:     address rewardToken;
```

- *LZHelperReceiver.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24) ):

```solidity
24:     uint32 constant TVL_UPDATE = 1;
```

- *LZHelperSender.sol* ( [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L23-L23) ):

```solidity
23:     bytes messageSetting;
```

</details>

### [N-04] Names of constants should use the UPPER_CASE_WITH_UNDERSCORES style

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html)

There is 1 instance:

- *ConnectorMock2.sol* ( [20-20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L20-L20) ):

```solidity
20:     uint256 public constant positionType = 1;
```

### [N-05] Names of `private`/`internal` functions should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

There is 1 instance:

- *Registry.sol* ( [293-301](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L293-L301) ):

```solidity
293:     function updateHoldingPosition(
294:         Vault storage vault,
295:         uint256 vaultId,
296:         bytes32 _positionId,
297:         bytes calldata d,
298:         bytes calldata AD,
299:         uint256 index,
300:         bytes32 holdingPositionId
301:     ) internal returns (uint256) {
```

### [N-06] Names of `private`/`internal` state variables should be prefixed with an underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.20/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 18 instances (click to show):</summary>

- *AaveConnector.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L18-L18), [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L22-L22) ):

```solidity
18:     address immutable pool;

22:     address immutable poolBaseToken;
```

- *AerodromeConnector.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L33-L33), [34-34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L34-L34) ):

```solidity
33:     IRouter aerodromeRouter;

34:     IVoter voter;
```

- *BalancerConnector.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L27-L27) ):

```solidity
27:     address internal balancerVault;
```

- *BalancerFlashLoan.sol* ( [15-15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L15-L15), [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L17-L17) ):

```solidity
15:     IBalancerVault internal vault;

17:     address caller;
```

- *MaverickConnector.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L30-L30), [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L31-L31), [32-32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L32-L32), [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L33-L33) ):

```solidity
30:     address mav;

31:     address veMav;

32:     address maverickRouter;

33:     IPositionInspector positionInspector;
```

- *MorphoBlueConnector.sol* ( [14-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L14-L14) ):

```solidity
14:     uint256 constant ORACLE_PRICE_SCALE = 1e36;
```

- *StargateConnector.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L22-L22), [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L23-L23), [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L24-L24) ):

```solidity
22:     IStargateLPStaking LPStaking;

23:     IStargateRouter stargateRouter;

24:     address rewardToken;
```

- *LZHelperReceiver.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24) ):

```solidity
24:     uint32 constant TVL_UPDATE = 1;
```

- *LZHelperSender.sol* ( [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L23-L23) ):

```solidity
23:     bytes messageSetting;
```

- *ChainlinkOracleConnector.sol* ( [20-20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L20-L20) ):

```solidity
20:     mapping(address => mapping(address => address)) private assetsSources;
```

</details>

### [N-07] The `nonReentrant` `modifier` should occur before all other modifiers

This is a best-practice to protect against reentrancy in other modifiers

<details>
<summary>There are 92 instances (click to show):</summary>

- *AccountingManager.sol* ( [226-226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L226-L226), [257-261](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L257-L261), [328-328](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L328-L328), [360-360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L360-L360), [370-370](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L370-L370), [396-396](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L396-L396), [475-475](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L475-L475), [505-505](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L505-L505), [526-526](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L526-L526), [548-548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L548-L548), [683-683](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L683-L683) ):

```solidity
226:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

257:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
258:         public
259:         onlyManager
260:         whenNotPaused
261:         nonReentrant

328:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

360:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {

370:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {

396:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

475:     function recordProfitForFee() public onlyManager nonReentrant {

505:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {

526:     function collectPerformanceFees() public onlyManager nonReentrant {

548:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {

683:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {
```

- *Registry.sol* ( [238-246](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L238-L246) ):

```solidity
238:     function addTrustedPosition(
239:         uint256 vaultId,
240:         uint256 _positionTypeId,
241:         address calculatorConnector,
242:         bool onlyOwner,
243:         bool _isDebt,
244:         bytes calldata _data,
245:         bytes calldata _additionalData
246:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {
```

- *AaveConnector.sol* ( [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L46-L46), [62-65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L62-L65), [81-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L81-L81), [100-100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L100-L100) ):

```solidity
46:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {

62:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
63:         external
64:         onlyManager
65:         nonReentrant

81:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {

100:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {
```

- *AerodromeConnector.sol* ( [53-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L53-L53), [79-79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L79-L79), [100-100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L100-L100), [106-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L106-L106), [111-111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L111-L111) ):

```solidity
53:     function supply(DepositData memory data) public onlyManager nonReentrant {

79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant {

100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {

106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {

111:     function claim(address pool) public onlyManager nonReentrant {
```

- *BalancerConnector.sol* ( [53-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L53-L53), [64-70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64-L70), [109-109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L109-L109), [115-115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L115-L115) ):

```solidity
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant {

109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {

115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {
```

- *CamelotConnector.sol* ( [43-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L43-L43), [65-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L65-L68) ):

```solidity
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {

65:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
66:         external
67:         onlyManager
68:         nonReentrant
```

- *CompoundConnector.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L29-L29), [48-48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L48-L48), [63-63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L63-L63) ):

```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {

48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {

63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {
```

- *CurveConnector.sol* ( [68-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L68-L68), [81-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L81-L81), [117-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L117-L120), [160-163](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L160-L163), [221-221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L221-L221), [233-233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L233-L233), [247-247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L247-L247) ):

```solidity
68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {

81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {

117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant

160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant

221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {

233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {

247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
```

- *Dolomite.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L30-L30), [43-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L43-L43), [58-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L58-L61), [77-80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L77-L80), [98-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L98-L98) ):

```solidity
30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager
61:         nonReentrant

77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
78:         public
79:         onlyManager
80:         nonReentrant

98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
```

- *FraxConnector.sol* ( [38-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L38-L41), [68-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L68-L68), [87-87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L87-L87) ):

```solidity
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant

68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {

87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
```

- *GearBoxV3.sol* ( [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L41-L41), [62-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L62-L68) ):

```solidity
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {

62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {
```

- *LidoConnector.sol* ( [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L37-L37), [51-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L51-L51), [69-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L69-L69) ):

```solidity
37:     function deposit(uint256 amountIn) external onlyManager nonReentrant {

51:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {

69:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {
```

- *MaverickConnector.sol* ( [64-64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L64-L64), [78-78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L78-L78), [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L91-L91), [115-118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L115-L118), [137-137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L137-L137) ):

```solidity
64:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant {

78:     function unstake(uint256 lockupId) external onlyManager nonReentrant {

91:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {

115:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
116:         external
117:         onlyManager
118:         nonReentrant

137:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {
```

- *MorphoBlueConnector.sol* ( [35-35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L35-L35), [58-58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L58-L58), [80-80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L80-L80), [95-95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L95-L95) ):

```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {

58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {

80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant {

95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant {
```

- *PancakeswapConnector.sol* ( [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L31-L31), [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L40-L40), [50-50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L50-L50) ):

```solidity
31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {

40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant {

50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant {
```

- *PendleConnector.sol* ( [78-78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L78-L78), [97-97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L97-L97), [112-112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L112-L112), [126-126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L126-L126), [137-137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L137-L137), [183-186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L183-L186), [203-203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L203-L203), [216-216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L216-L216), [241-241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L241-L241) ):

```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant {

97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {

112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {

126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant

203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {

216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {

241:     function claimRewards(IPMarket market) external onlyManager nonReentrant {
```

- *PrismaConnector.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L33-L33), [52-55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L52-L55), [75-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L75-L75), [97-104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L97-L104), [129-129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L129-L129) ):

```solidity
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {

52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant

75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {

97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant {

129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {
```

- *SiloConnector.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L33-L33), [52-55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L52-L55), [85-85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L85-L85), [98-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L98-L98) ):

```solidity
33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {

52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant

85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {

98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {
```

- *StargateConnector.sol* ( [49-49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L49-L49), [76-76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L76-L76), [103-103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L103-L103) ):

```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {

76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant {

103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {
```

- *UNIv3Connector.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L40-L40), [63-63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L63-L63), [87-87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L87-L87), [101-101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L101-L101) ):

```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {

63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {

87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {

101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
```

- *BaseConnector.sol* ( [122-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122-L127), [204-210](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L210) ):

```solidity
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant {

204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {
```

- *OmnichainLogic.sol* ( [68-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68) ):

```solidity
68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
```

- *GenericSwapAndBridgeHandler.sol* ( [90-95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L95), [126-131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L131) ):

```solidity
90:     function executeSwap(SwapRequest memory _swapRequest)
91:         external
92:         payable
93:         onlyEligibleUser
94:         onlyExistingRoute(_swapRequest.routeId)
95:         nonReentrant

126:     function executeBridge(BridgeRequest calldata _bridgeRequest)
127:         external
128:         payable
129:         onlyEligibleUser
130:         onlyExistingRoute(_bridgeRequest.routeId)
131:         nonReentrant
```

</details>

### [N-08] Use of `override` is unnecessary

[Starting from Solidity 0.8.8](https://docs.soliditylang.org/en/v0.8.20/contracts.html#function-overriding), the override keyword is not required when overriding an interface function, except for the case where the function is defined in multiple bases.

<details>
<summary>There are 49 instances (click to show):</summary>

- *AccountingManager.sol* ( [185-185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L185-L185), [591-591](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L591-L591), [693-693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L693-L693), [697-697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L697-L697), [701-701](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L701-L701), [705-705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L705-L705) ):

```solidity
185:     function _update(address from, address to, uint256 amount) internal override {

591:     function totalAssets() public view override returns (uint256) {

693:     function mint(uint256 shares, address receiver) public override returns (uint256) {

697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

701:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {

705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {
```

- *AaveConnector.sol* ( [114-114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114-L114), [120-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L120-L120) ):

```solidity
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {

120:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *AerodromeConnector.sol* ( [117-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L117-L117), [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L125-L125) ):

```solidity
117:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {

125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *BalancerConnector.sol* ( [162-162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L162-L162) ):

```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *BalancerFlashLoan.sol* ( [54-59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54-L59) ):

```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
```

- *CamelotConnector.sol* ( [88-88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L88-L88), [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L99-L99) ):

```solidity
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

99:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *CompoundConnector.sol* ( [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L125-L125), [134-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L134-L134) ):

```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *CurveConnector.sol* ( [265-265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L265-L265) ):

```solidity
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *Dolomite.sol* ( [106-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L106-L106) ):

```solidity
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *FraxConnector.sol* ( [142-142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L142-L142), [150-150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L150-L150) ):

```solidity
142:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {

150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *GearBoxV3.sol* ( [93-93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L93-L93) ):

```solidity
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *LidoConnector.sol* ( [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L91-L91) ):

```solidity
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *MaverickConnector.sol* ( [149-149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L149-L149), [153-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L153-L153), [161-161](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L161-L161) ):

```solidity
149:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {

153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

161:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *MorphoBlueConnector.sol* ( [118-118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L118-L118), [141-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L141-L141) ):

```solidity
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

141:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PendleConnector.sol* ( [257-257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L257-L257), [311-311](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L311-L311) ):

```solidity
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

311:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PrismaConnector.sol* ( [145-145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L145-L145), [164-164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L164-L164) ):

```solidity
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

164:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *SNXConnector.sol* ( [64-64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L64-L64), [121-121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L121-L121), [128-128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L128-L128) ):

```solidity
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {

121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

128:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *SiloConnector.sol* ( [109-109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L109-L109), [143-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L143-L143) ):

```solidity
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

143:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *StargateConnector.sol* ( [110-110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L110-L110), [123-123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L123-L123) ):

```solidity
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

123:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *UNIv3Connector.sol* ( [127-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L127-L127), [152-152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L152-L152) ):

```solidity
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

152:     function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
```

- *BaseConnector.sol* ( [169-173](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L169-L173) ):

```solidity
169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
170:         external
171:         override
172:         nonReentrant
173:     {
```

- *LZHelperReceiver.sol* ( [65-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L65-L68) ):

```solidity
65:     function _lzReceive(Origin calldata _origin, bytes32, bytes calldata _message, address, bytes calldata)
66:         internal
67:         override
68:     {
```

- *LZHelperSender.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L40-L40) ):

```solidity
40:     function _payNative(uint256 amount) internal override returns (uint256) {
```

- *OmnichainManagerBaseChain.sol* ( [51-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51-L51) ):

```solidity
51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {
```

- *OmnichainManagerNormalChain.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33-L33) ):

```solidity
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {
```

- *LifiImplementation.sol* ( [77-82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L82), [110-110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L110-L110), [133-138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133-L138), [150-150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L150-L150) ):

```solidity
77:     function performSwapAction(address caller, SwapRequest calldata _request)
78:         external
79:         payable
80:         override
81:         onlyHandler
82:         returns (uint256)

110:     function verifySwapData(SwapRequest calldata _request) public view override returns (bool) {

133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
134:         external
135:         payable
136:         override
137:         onlyHandler
138:     {

150:     function verifyBridgeData(BridgeRequest calldata _request) public view override returns (bool) {
```

</details>

### [N-09] Unused `struct`s

Note that there may be cases where a struct superficially appears to be used, but this is only because there are multiple definitions of the struct in different files. In such cases, the struct definition should be moved into a separate file. The instances below are the unused definitions.

There are 2 instances:

- *FraxConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L7), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L13) ):

```solidity
7: struct FraxPoolInfo {

13: struct FraxBorrowRequest {
```

### [N-10] Custom errors should be used rather than `revert()`/`require()`

Custom errors are available from solidity version 0.8.4. Custom errors are more easily processed in try-catch blocks, and are easier to re-use and maintain.

<details>
<summary>There are 88 instances (click to show):</summary>

- *AccountingManager.sol* ( [106-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L106-L106), [107-107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L107-L107), [108-108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L108-L108), [109-109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L109-L109), [110-110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L110-L110), [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L125-L125), [140-140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L140-L140), [141-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L141-L141), [142-142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L142-L142), [361-361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361-L361), [371-371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371-L371), [686-686](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L686-L686) ):

```solidity
106:         require(p._baseTokenAddress != address(0));

107:         require(p._valueOracle != address(0));

108:         require(p._withdrawFeeReceiver != address(0));

109:         require(p._performanceFeeReceiver != address(0));

110:         require(p._managementFeeReceiver != address(0));

125:         require(address(_valueOracle) != address(0));

140:         require(_withdrawFeeReceiver != address(0));

141:         require(_performanceFeeReceiver != address(0));

142:         require(_managementFeeReceiver != address(0));

361:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);

371:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);

686:             require(success, "Transfer failed.");
```

- *NoyaFeeReceiver.sol* ( [15-15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L15-L15), [16-16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L16-L16), [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L17-L17) ):

```solidity
15:         require(_accountingManager != address(0));

16:         require(_baseToken != address(0));

17:         require(_receiver != address(0));
```

- *Registry.sol* ( [67-67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L67-L67), [68-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L68-L68), [69-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L69-L69), [80-80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L80-L80), [120-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L120-L120), [121-121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L121-L121), [122-122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L122-L122), [123-123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L123-L123), [124-124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L124-L124), [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L125-L125), [167-167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L167-L167), [168-168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L168-L168), [169-169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L169-L169), [170-170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L170-L170) ):

```solidity
67:         require(_governer != address(0));

68:         require(_maintainer != address(0));

69:         require(_emergency != address(0));

80:         require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);

120:         require(_governer != address(0));

121:         require(_accountingManager != address(0));

122:         require(_baseToken != address(0));

123:         require(_maintainer != address(0));

124:         require(_keeperContract != address(0));

125:         require(_watcher != address(0));

167:         require(_governer != address(0));

168:         require(_maintainer != address(0));

169:         require(_keeperContract != address(0));

170:         require(_watcher != address(0));
```

- *AaveConnector.sol* ( [36-36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L37-L37) ):

```solidity
36:         require(_pool != address(0));

37:         require(_poolBaseToken != address(0));
```

- *AerodromeConnector.sol* ( [43-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L43-L43) ):

```solidity
43:         require(_router != address(0));
```

- *BalancerConnector.sol* ( [45-45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L45-L45), [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L46-L46), [47-47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L47-L47) ):

```solidity
45:         require(_balancerVault != address(0));

46:         require(bal != address(0));

47:         require(aura != address(0));
```

- *BalancerFlashLoan.sol* ( [25-25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L26-L26), [61-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L61-L61), [82-82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L82-L82), [92-92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92) ):

```solidity
25:         require(_balancerVault != address(0));

26:         require(address(_registry) != address(0));

61:         require(msg.sender == address(vault));

82:                 require(success, "BalancerFlashLoan: Flash loan failed");

92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
```

- *CamelotConnector.sol* ( [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L37-L37), [38-38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L38-L38) ):

```solidity
37:         require(_router != address(0));

38:         require(_factory != address(0));
```

- *CurveConnector.sol* ( [52-52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L52-L52), [53-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L53-L53), [54-54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L54-L54), [55-55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L55-L55) ):

```solidity
52:         require(_convexBooster != address(0));

53:         require(cvx != address(0));

54:         require(crv != address(0));

55:         require(prisma != address(0));
```

- *Dolomite.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L24-L24) ):

```solidity
24:         require(_depositWithdrawalProxy != address(0));
```

- *LidoConnector.sol* ( [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L23-L23), [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L24-L24), [25-25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L25-L25), [26-26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L26-L26) ):

```solidity
23:         require(_lido != address(0));

24:         require(_lidoW != address(0));

25:         require(_steth != address(0));

26:         require(w != address(0));
```

- *MaverickConnector.sol* ( [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L46-L46), [47-47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L47-L47), [48-48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L48-L48), [49-49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L49-L49) ):

```solidity
46:         require(_mav != address(0));

47:         require(_veMav != address(0));

48:         require(mr != address(0));

49:         require(pi != address(0));
```

- *MorphoBlueConnector.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L24-L24) ):

```solidity
24:         require(MB != address(0));
```

- *PancakeswapConnector.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L22-L22) ):

```solidity
22:         require(MC != address(0));
```

- *PendleConnector.sol* ( [60-60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L60-L60), [61-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L61-L61), [62-62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L62-L62) ):

```solidity
60:         require(_pendleMarketDepositHelper != address(0));

61:         require(_pendleRouter != address(0));

62:         require(SR != address(0));
```

- *SNXConnector.sol* ( [21-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L21-L21) ):

```solidity
21:         require(_SNXCoreProxy != address(0));
```

- *SiloConnector.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L18-L18) ):

```solidity
18:         require(SR != address(0));
```

- *StargateConnector.sol* ( [36-36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L36-L36), [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L37-L37) ):

```solidity
36:         require(lpStacking != address(0));

37:         require(_stargateRouter != address(0));
```

- *Keepers.sol* ( [28-28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L28-L28), [53-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L53-L53), [64-64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L64-L64), [94-94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L94-L94), [95-95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L95-L95), [96-96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L96-L96), [97-97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L97-L97), [98-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L98-L98), [106-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L106-L106), [117-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L117-L117) ):

```solidity
28:         require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);

53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);

64:         require(_threshold <= numOwners && _threshold > 1);

94:         require(isOwner[msg.sender], "Not an owner");

95:         require(sigR.length == threshold, "Not enough signatures");

96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");

97:         require(executor == msg.sender, "Invalid executor");

98:         require(block.timestamp <= deadline, "Transaction expired");

106:                 require(recovered > lastAdd && isOwner[recovered]);

117:         require(success, "Transaction execution reverted.");
```

- *NoyaGovernanceBase.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L22-L22) ):

```solidity
22:         require(address(_registry) != address(0));
```

- *LZHelperReceiver.sol* ( [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L41-L41), [53-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L53-L53) ):

```solidity
41:         require(lzHelperAddress != address(0));

53:         require(omniChainManager != address(0));
```

- *LZHelperSender.sol* ( [52-52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L52-L52) ):

```solidity
52:         require(lzHelperAddress != address(0));
```

- *OmnichainLogic.sol* ( [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L37-L37), [47-47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L47-L47) ):

```solidity
37:         require(_lzHelper != address(0));

47:         require(destinationAddress != address(0));
```

- *GenericSwapAndBridgeHandler.sol* ( [25-25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L25-L25), [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L41-L41) ):

```solidity
25:         require(isEligibleToUse[msg.sender], "NoyaSwapHandler: Not eligible to use");

41:         require(_valueOracle != address(0));
```

- *LifiImplementation.sol* ( [35-35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35-L35), [84-84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L84-L84), [196-196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L196-L196) ):

```solidity
35:         require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER");

84:         require(verifySwapData(_request), "LifiImplementation: INVALID_SWAP_DATA");

196:             require(success, "Transfer failed.");
```

- *NoyaValueOracle.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L30-L30) ):

```solidity
30:         require(address(_registry) != address(0));
```

- *ChainlinkOracleConnector.sol* ( [47-47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L47-L47) ):

```solidity
47:         require(_reg != address(0));
```

- *UniswapValueOracle.sol* ( [50-50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L50-L50) ):

```solidity
50:         require(pool != address(0), "pool doesn't exist");
```

</details>

### [N-11] Add inline comments for unnamed parameters

`function func(address a, address)` -> `function func(address a, address /* b */)`

<details>
<summary>There are 17 instances (click to show):</summary>

- *AaveConnector.sol* ( [114-114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114-L114), [120-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L120-L120) ):

```solidity
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {

120:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *CompoundConnector.sol* ( [134-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L134-L134) ):

```solidity
134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *MaverickConnector.sol* ( [149-149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L149-L149) ):

```solidity
149:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {
```

- *MorphoBlueConnector.sol* ( [141-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L141-L141) ):

```solidity
141:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PendleConnector.sol* ( [311-311](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L311-L311) ):

```solidity
311:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PrismaConnector.sol* ( [164-164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L164-L164) ):

```solidity
164:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *SNXConnector.sol* ( [64-64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L64-L64), [128-128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L128-L128) ):

```solidity
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {

128:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *SiloConnector.sol* ( [143-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L143-L143) ):

```solidity
143:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *StargateConnector.sol* ( [123-123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L123-L123) ):

```solidity
123:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *UNIv3Connector.sol* ( [152-152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L152-L152) ):

```solidity
152:     function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
```

- *BaseConnector.sol* ( [263-263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L263-L263), [267-267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267), [271-271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271-L271) ):

```solidity
263:     function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {

267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {

271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
```

- *LZHelperReceiver.sol* ( [65-65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L65-L65) ):

```solidity
65:     function _lzReceive(Origin calldata _origin, bytes32, bytes calldata _message, address, bytes calldata)
```

- *OmnichainManagerBaseChain.sol* ( [51-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51-L51) ):

```solidity
51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {
```

</details>

### [N-12] Consider providing a ranged getter for array state variables

While the compiler automatically provides a getter for accessing single elements within a public state variable array, it doesn't provide a way to fetch the whole array, or subsets thereof. Consider adding a function to allow the fetching of slices of the array, especially if the contract doesn't already have multicall functionality.

There are 2 instances:

- *GenericSwapAndBridgeHandler.sol* ( [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L17-L17) ):

```solidity
17:     RouteData[] public routes;
```

- *NoyaValueOracle.sol* ( [14-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L14-L14) ):

```solidity
14:     mapping(address => mapping(address => address[])) public priceRoutes;
```

### [N-13] Consider splitting complex checks into multiple steps

Assign the expression's parts to intermediate local variables, and check against those instead.

There are 3 instances:

- *AccountingManager.sol* ( [528-529](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528-L529) ):

```solidity
528:             preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours
529:                 || block.timestamp - profitStoredTime > 48 hours
```

- *BaseConnector.sol* ( [142-142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L142-L142) ):

```solidity
142:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
```

- *ConnectorMock2.sol* ( [86-86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L86-L86) ):

```solidity
86:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
```

### [N-14] Missing checks for empty bytes when updating bytes state variables

Unless the code is attempting to `delete` the state variable, the caller shouldn't have to write `""` to the state variable

There is 1 instance:

- *LZHelperSender.sol* ( [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L37-L37) ):

```solidity
37:         messageSetting = _messageSetting;
```

### [N-15] Complex casting

Consider whether the number of casts is really necessary, or whether using a different type would be more appropriate. Alternatively, add comments to explain in detail why the casts are necessary, and any implicit reasons why the cast does not introduce an overflow.

There is 1 instance:

- *UniswapValueOracle.sol* ( [81-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81-L81) ):

```solidity
81:         int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));
```

### [N-16] Complex math should be split into multiple steps

Consider splitting long arithmetic calculations into multiple steps to improve the code readability.

There are 3 instances:

- *AccountingManager.sol* ( [517-518](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L517-L518) ):

```solidity
517:         uint256 managementFeeAmount =
518:             (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;
```

- *CompoundConnector.sol* ( [117-118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L117-L118) ):

```solidity
117:                 uint256 collateralValueInVirtualBase =
118:                     collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice;
```

- *FraxConnector.sol* ( [128-129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L128-L129) ):

```solidity
128:         uint256 currentPositionLTV =
129:             (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;
```

### [N-17] Consider adding a block/deny-list

Doing so will significantly increase centralization, but will help to prevent hackers from using stolen tokens

<details>
<summary>There are 7 instances (click to show):</summary>

- *AccountingManager.sol* ( [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16) ):

```solidity
16: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
```

- *BalancerFlashLoan.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L12) ):

```solidity
12: contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {
```

- *PancakeswapConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8) ):

```solidity
8: contract PancakeswapConnector is UNIv3Connector {
```

- *PendleConnector.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12) ):

```solidity
12: contract PendleConnector is BaseConnector {
```

- *BaseConnector.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L22) ):

```solidity
22: contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {
```

- *ConnectorMock2.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L14) ):

```solidity
14: contract ConnectorMock2 {
```

- *LifiImplementation.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10) ):

```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {
```

</details>

### [N-18] Convert simple `if`-statements to ternary expressions

Converting some if statements to ternaries (such as `z = (a < b) ? x : y`) can make the code more concise and easier to read.

<details>
<summary>There are 4 instances (click to show):</summary>

- *AccountingManager.sol* ( [380-384](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L380-L384) ):

```solidity
380:         if (availableAssets >= currentWithdrawGroup.totalCBAmount) {
381:             currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;
382:         } else {
383:             currentWithdrawGroup.totalABAmount = availableAssets;
384:         }
```

- *CompoundConnector.sol* ( [119-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L119-L120) ):

```solidity
119:                 if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;
120:                 else CollValue += collateralValueInVirtualBase;
```

- *LifiImplementation.sol* ( [86-90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L86-L90), [93-97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L93-L97) ):

```solidity
86:         if (_request.outputToken == address(0)) {
87:             balanceOut0 = address(_request.from).balance;
88:         } else {
89:             balanceOut0 = IERC20(_request.outputToken).balanceOf(_request.from);
90:         }

93:         if (_request.outputToken == address(0)) {
94:             balanceOut1 = address(_request.from).balance;
95:         } else {
96:             balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);
97:         }
```

</details>

### [N-19] Contract name does not match its filename

According to the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names), contract and library names should also match their filenames.

<details>
<summary>There are 6 instances (click to show):</summary>

- *Registry.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12) ):

```solidity
/// @audit Not match filename `Registry.sol`
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

- *Dolomite.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9) ):

```solidity
/// @audit Not match filename `Dolomite.sol`
9: contract DolomiteConnector is BaseConnector {
```

- *GearBoxV3.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8) ):

```solidity
/// @audit Not match filename `GearBoxV3.sol`
8: contract Gearboxv3 is BaseConnector {
```

- *SNXConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7) ):

```solidity
/// @audit Not match filename `SNXConnector.sol`
7: contract SNXV3Connector is BaseConnector, IERC721Receiver {
```

- *TimeLock.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L6) ):

```solidity
/// @audit Not match filename `TimeLock.sol`
6: contract NoyaTimeLock is TimelockController {
```

- *GenericSwapAndBridgeHandler.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10) ):

```solidity
/// @audit Not match filename `GenericSwapAndBridgeHandler.sol`
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
```

</details>

### [N-20] Consider using `AccessControlDefaultAdminRules` rather than `AccessControl`

The `AccessControlDefaultAdminRules` implements multiple [security best practices](https://docs.openzeppelin.com/contracts/4.x/api/access#AccessControlDefaultAdminRules) on top of the normal `AccessControl` rules, so consider using it instead.

There is 1 instance:

- *Registry.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12-L12) ):

```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

### [N-21] UPPER_CASE names should be reserved for `constant`/`immutable` variables

If the variable needs to be different based on which class it comes from, a `view`/`pure` _function_ should be used instead (e.g. like [this](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/76eee35971c2541585e05cbf258510dda7b2fbc6/contracts/token/ERC20/extensions/draft-IERC20Permit.sol#L59)).

<details>
<summary>There are 44 instances (click to show):</summary>

- *Registry.sol* ( [298](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L298) ):

```solidity
298:         bytes calldata AD,
```

- *BalancerConnector.sol* ( [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L29), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L30), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L32), [163](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L163) ):

```solidity
29:     address public BAL;

30:     address public AURA;

32:     uint256 public BALANCER_LP_POSITION = 1;

163:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
```

- *CompoundConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L8) ):

```solidity
8:     uint256 public COMPOUND_LP = 2;
```

- *CurveConnector.sol* ( [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L29), [266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L266) ):

```solidity
27:     address public CVX;

28:     address public CRV;

29:     address public PRISMA;

266:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
```

- *FraxConnector.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L22), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L127), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L127) ):

```solidity
22:     uint256 public COLLATERAL_AND_DEBT_POSITION_TYPE = 1;

127:         (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();

127:         (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();
```

- *LidoConnector.sol* ( [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L13) ):

```solidity
13:     uint256 public LIDO_WITHDRAWAL_REQUEST_ID = 10;
```

- *MaverickConnector.sol* ( [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L35) ):

```solidity
35:     uint256 public MAVERICK_LP = 10;
```

- *MorphoBlueConnector.sol* ( [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L23) ):

```solidity
23:     constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```

- *PancakeswapConnector.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19) ):

```solidity
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
```

- *PendleConnector.sol* ( [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L57), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L79), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L79), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L98), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L98), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L98), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L113), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L113), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L188), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L188), [217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L217), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L262), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L262), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L262), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L313) ):

```solidity
57:     constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)

79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

153:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

153:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

153:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

170:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

170:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

170:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

188:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

188:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

217:         (IPStandardizedYield SY,,) = market.readTokens();

262:             (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

262:             (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

262:             (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

304:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

304:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

304:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

313:         (IPStandardizedYield SY,,) = IPMarket(market).readTokens();
```

- *SiloConnector.sol* ( [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L17) ):

```solidity
17:     constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```

- *BaseConnector.sol* ( [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L28), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L31) ):

```solidity
28:     uint256 public MINIMUM_HEALTH_FACTOR = 15e17;

31:     uint256 public DUST_LEVEL = 1;
```

</details>

### [N-22] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary>There are 39 instances (click to show):</summary>

- *AccountingManager.sol* ( [94-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L94-L98) ):

```solidity
94:     constructor(AccountingManagerConstructorParams memory p)
95:         ERC4626(IERC20(p._baseTokenAddress))
96:         ERC20(p._name, p._symbol)
97:         NoyaGovernanceBase(PositionRegistry(p._registry), p._vaultId)
98:     {
```

- *NoyaFeeReceiver.sol* ( [14-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L14-L14) ):

```solidity
14:     constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
```

- *Registry.sol* ( [66-66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L66-L66) ):

```solidity
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
```

- *AaveConnector.sol* ( [33-35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L33-L35) ):

```solidity
33:     constructor(address _pool, address _poolBaseToken, BaseConnectorCP memory baseConnectorParams)
34:         BaseConnector(baseConnectorParams)
35:     {
```

- *AerodromeConnector.sol* ( [40-42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L40-L42) ):

```solidity
40:     constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)
41:         BaseConnector(baseConnectorParams)
42:     {
```

- *BalancerConnector.sol* ( [42-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L42-L44) ):

```solidity
42:     constructor(address _balancerVault, address bal, address aura, BaseConnectorCP memory baseConnectorParams)
43:         BaseConnector(baseConnectorParams)
44:     {
```

- *BalancerFlashLoan.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L24-L24) ):

```solidity
24:     constructor(address _balancerVault, PositionRegistry _registry) {
```

- *CamelotConnector.sol* ( [36-36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L36-L36) ):

```solidity
36:     constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```

- *CompoundConnector.sol* ( [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L17-L17) ):

```solidity
17:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```

- *CurveConnector.sol* ( [45-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L45-L51) ):

```solidity
45:     constructor(
46:         address _convexBooster,
47:         address cvx,
48:         address crv,
49:         address prisma,
50:         BaseConnectorCP memory baseConnectorParams
51:     ) BaseConnector(baseConnectorParams) {
```

- *Dolomite.sol* ( [18-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L18-L23) ):

```solidity
18:     constructor(
19:         address _depositWithdrawalProxy,
20:         address _dolomiteMargin,
21:         address _borrowPositionProxy,
22:         BaseConnectorCP memory baseConnectorParams
23:     ) BaseConnector(baseConnectorParams) {
```

- *FraxConnector.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L29-L29) ):

```solidity
29:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```

- *GearBoxV3.sol* ( [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L17-L17) ):

```solidity
17:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```

- *LidoConnector.sol* ( [20-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L20-L22) ):

```solidity
20:     constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)
21:         BaseConnector(baseConnectorParams)
22:     {
```

- *MaverickConnector.sol* ( [43-45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L43-L45) ):

```solidity
43:     constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)
44:         BaseConnector(baseCP)
45:     {
```

- *MorphoBlueConnector.sol* ( [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L23-L23) ):

```solidity
23:     constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```

- *PancakeswapConnector.sol* ( [19-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19-L21) ):

```solidity
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
20:         UNIv3Connector(_positionManager, _factory, baseConnectorParams)
21:     {
```

- *PendleConnector.sol* ( [57-59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L57-L59) ):

```solidity
57:     constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)
58:         BaseConnector(baseCP)
59:     {
```

- *PrismaConnector.sol* ( [25-25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L25-L25) ):

```solidity
25:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```

- *SNXConnector.sol* ( [20-20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L20-L20) ):

```solidity
20:     constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```

- *SiloConnector.sol* ( [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L17-L17) ):

```solidity
17:     constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```

- *StargateConnector.sol* ( [33-35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L33-L35) ):

```solidity
33:     constructor(address lpStacking, address _stargateRouter, BaseConnectorCP memory baseConnectorParams)
34:         BaseConnector(baseConnectorParams)
35:     {
```

- *UNIv3Connector.sol* ( [27-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L27-L29) ):

```solidity
27:     constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
28:         BaseConnector(baseConnectorParams)
29:     {
```

- *Keepers.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L27-L27) ):

```solidity
27:     constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
```

- *NoyaGovernanceBase.sol* ( [21-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L21-L21) ):

```solidity
21:     constructor(PositionRegistry _registry, uint256 _vaultId) {
```

- *TimeLock.sol* ( [7-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L7-L9) ):

```solidity
7:     constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)
8:         TimelockController(minDelay, proposers, executors, owner)
9:     { }
```

- *Watchers.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L7-L7) ):

```solidity
7:     constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
```

- *BaseConnector.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L33-L33) ):

```solidity
33:     constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {
```

- *ConnectorMock2.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L22-L22) ):

```solidity
22:     constructor(address _registry, uint256 _vaultId) {
```

- *LZHelperReceiver.sol* ( [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31-L31) ):

```solidity
31:     constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }
```

- *LZHelperSender.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L29-L29) ):

```solidity
29:     constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
```

- *OmnichainLogic.sol* ( [33-35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33-L35) ):

```solidity
33:     constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
34:         BaseConnector(baseConnectorParams)
35:     {
```

- *OmnichainManagerBaseChain.sol* ( [19-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L21) ):

```solidity
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
20:         OmnichainLogic(_lzHelper, baseConnectorParams)
21:     {
```

- *OmnichainManagerNormalChain.sol* ( [11-13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L11-L13) ):

```solidity
11:     constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
12:         OmnichainLogic(_lzHelper, baseConnectorParams)
13:     { }
```

- *GenericSwapAndBridgeHandler.sol* ( [34-36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L36) ):

```solidity
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
35:         NoyaGovernanceBase(_registry, _vaultId)
36:     {
```

- *LifiImplementation.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L27) ):

```solidity
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
```

- *NoyaValueOracle.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L29-L29) ):

```solidity
29:     constructor(PositionRegistry _registry) {
```

- *ChainlinkOracleConnector.sol* ( [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L46-L46) ):

```solidity
46:     constructor(address _reg) {
```

- *UniswapValueOracle.sol* ( [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L31) ):

```solidity
31:     constructor(address _factory, PositionRegistry _registry) {
```

</details>

### [N-23] Empty function body without comments

Empty function body in solidity is not recommended, consider adding some comments to the body.

There are 4 instances:

- *LidoConnector.sol* ( [89-89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L89-L89) ):

```solidity
89:     receive() external payable { }
```

- *MaverickConnector.sol* ( [56-56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L56-L56) ):

```solidity
56:     receive() external payable { }
```

- *Watchers.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L8-L8) ):

```solidity
8:     function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
```

- *LZHelperSender.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L27-L27) ):

```solidity
27:     receive() external payable { }
```

### [N-24] Events are emitted without the sender information

When an action is triggered based on a user's action, not being able to filter based on who triggered the action makes event processing a lot more cumbersome. Including the `msg.sender` the events of these types of action will make events much more useful to end users, especially when `msg.sender` is not `tx.origin`.

<details>
<summary>There are 39 instances (click to show):</summary>

- *AccountingManager.sol* ( [127-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L127-L127), [146-146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L146-L146), [180-180](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L180-L180), [216-216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L216-L216), [496-496](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L496-L496), [670-670](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L670-L670), [675-675](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L675-L675), [680-680](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L680-L680) ):

```solidity
127:         emit ValueOracleUpdated(address(_valueOracle));

146:         emit FeeRecepientsChanged(_withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver);

180:         emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee);

216:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);

496:             emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);

670:         emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount);

675:         emit SetDepositWaitingTime(_depositWaitingTime);

680:         emit SetWithdrawWaitingTime(_withdrawWaitingTime);
```

- *Registry.sol* ( [196-196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L196-L196), [217-217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L217-L217), [262-262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L262-L262), [279-279](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L279-L279), [302-302](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L302-L302), [361-361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L361-L361) ):

```solidity
196:             emit ConnectorAdded(vaultId, _connectorAddresses[i]);

217:         emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted);

262:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data);

279:         emit TrustedPositionRemoved(vaultId, _positionId);

302:         emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index);

361:             emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);
```

- *BalancerFlashLoan.sol* ( [42-42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L42-L42), [60-60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L60-L60) ):

```solidity
42:         emit MakeFlashLoan(tokens, amounts);

60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
```

- *Keepers.sol* ( [115-115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L115-L115) ):

```solidity
115:         emit Execute(destination, data, gasLimit, executor, deadline);
```

- *BaseConnector.sol* ( [50-50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L50-L50), [60-60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L60-L60), [69-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L69-L69), [192-192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L192-L192) ):

```solidity
50:         emit MinimumHealthFactorUpdated(_minimumHealthFactor);

60:         emit SwapHandlerUpdated(_swapHandler);

69:         emit ValueOracleUpdated(_valueOracle);

192:         emit AddLiquidity(tokens, amounts, data);
```

- *OmnichainLogic.sol* ( [49-49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L49-L49) ):

```solidity
49:         emit UpdateChainInfo(chainId, destinationAddress);
```

- *GenericSwapAndBridgeHandler.sol* ( [50-50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L50-L50), [59-59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59-L59), [73-73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L73-L73), [82-82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L82-L82), [117-119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L117-L119), [139-139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L139-L139), [150-150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L150-L150), [160-160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160-L160) ):

```solidity
50:         emit SetValueOracle(_valueOracle);

59:         emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);

73:         emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance);

82:         emit AddEligibleUser(_user);

117:         emit ExecutionCompleted(
118:             _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
119:         );

139:         emit BridgeExecutionCompleted(_bridgeRequest);

150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);

160:         emit RouteUpdate(_routeId, false);
```

- *LifiImplementation.sol* ( [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L99-L99), [141-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L141-L141) ):

```solidity
99:         emit Swapped(balanceOut0, balanceOut1, _request.outputToken);

141:         emit Bridged(_request.from, _request.inputToken, _request.amount, _request.data);
```

- *NoyaValueOracle.sol* ( [44-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L44-L44), [58-58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L58-L58), [63-63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L63-L63) ):

```solidity
44:         emit UpdatedDefaultPriceSource(baseCurrencies, oracles);

58:         emit UpdatedAssetPriceSource(asset, baseToken, oracle);

63:         emit UpdatedPriceRoute(asset, base, s);
```

- *ChainlinkOracleConnector.sol* ( [61-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L61-L61), [76-76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L76-L76) ):

```solidity
61:         emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);

76:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);
```

- *UniswapValueOracle.sol* ( [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L41-L41), [52-52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L52-L52) ):

```solidity
41:         emit NewPeriod(_period);

52:         emit PoolsForAsset(tokenIn, baseToken, pool);
```

</details>

### [N-25] Function state mutability can be restricted to pure

Function state mutability can be restricted to pure

<details>
<summary>There are 15 instances (click to show):</summary>

- *AccountingManager.sol* ( [649-649](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L649-L649), [693-693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L693-L693), [697-697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L697-L697), [701-701](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L701-L701), [705-705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L705-L705) ):

```solidity
649:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {

693:     function mint(uint256 shares, address receiver) public override returns (uint256) {

697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

701:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {

705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {
```

- *CamelotConnector.sol* ( [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L99-L99) ):

```solidity
99:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *CompoundConnector.sol* ( [134-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L134-L134) ):

```solidity
134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *MaverickConnector.sol* ( [149-149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L149-L149) ):

```solidity
149:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {
```

- *Watchers.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L8-L8) ):

```solidity
8:     function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
```

- *BaseConnector.sol* ( [263-263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L263-L263), [267-267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267), [271-271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271-L271) ):

```solidity
263:     function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {

267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {

271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
```

- *ConnectorMock2.sol* ( [71-71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L71-L71), [75-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L75-L75) ):

```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
```

- *LZHelperSender.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L40-L40) ):

```solidity
40:     function _payNative(uint256 amount) internal override returns (uint256) {
```

</details>

### [N-26] Imports could be organized more systematically

The contract's interface should be imported first, followed by each of the interfaces it uses, followed by all other files. The examples below do not follow this layout.

<details>
<summary>There are 30 instances (click to show):</summary>

- *AccountingManager.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "../interface/Accounting/IAccountingManager.sol";
```

- *Registry.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "../interface/IPositionRegistry.sol";
```

- *AaveConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import { IPool } from "../external/interfaces/Aave/IPool.sol";
```

- *AerodromeConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Aerodrome/IPool.sol";
```

- *BalancerConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Balancer/IBalancerVault.sol";
```

- *CamelotConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../external/interfaces/Camelot/ICamelotRouter.sol";
```

- *CompoundConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import { IComet, IRewards } from "../external/interfaces/Compound/ICompound.sol";
```

- *CurveConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Curve/IRewardsGauge.sol";
```

- *Dolomite.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Dolomite/IDepositWithdrawalProxy.sol";
```

- *FraxConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Frax/IFraxPair.sol";
```

- *GearBoxV3.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Gearbox/ICreditManagerV3.sol";
```

- *MorphoBlueConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Morpho/IMorpho.sol";
```

- *PancakeswapConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Pancakeswap/IMasterChefV3.sol";
```

- *PendleConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import { IPendleMarketDepositHelper } from "../external/interfaces/Pendle/IPendleMarketDepositHelper.sol";
```

- *PrismaConnector.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L6-L6) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import { IBorrowerOperations } from "../external/interfaces/Prisma/IBorrowerOperations.sol";
```

- *SNXConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/SNXV3/IV3CoreProxy.sol";
```

- *SiloConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Silo/ISilo.sol";
```

- *StargateConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../external/interfaces/Stargate/IStargateRouter.sol";
```

- *BaseConnector.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L10-L10), [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L12-L12) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
10: import "../interface/valueOracle/INoyaValueOracle.sol";

/// @audit Out of order with the prev import️ ⬆
12: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721Receiver.sol";
```

- *ConnectorMock2.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L10-L10), [11-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L11-L11) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
10: import { ITokenTransferCallBack } from "contracts/interface/ITokenTransferCallBack.sol";

/// @audit Out of order with the prev import️ ⬆
11: import { HoldingPI } from "contracts/interface/IConnector.sol";
```

- *OmnichainManagerBaseChain.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../../interface/IConnector.sol";
```

- *GenericSwapAndBridgeHandler.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L6-L6), [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
6: import "../../interface/SwapHandler/ISwapAndBridgeHandler.sol";

/// @audit Out of order with the prev import️ ⬆
7: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *LifiImplementation.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *TVLHelper.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import { IConnector } from "../interface/IConnector.sol";
```

- *NoyaValueOracle.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L5-L5) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
5: import "../../interface/valueOracle/INoyaValueOracle.sol";
```

- *ChainlinkOracleConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8-L8) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
8: import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol";
```

- *UniswapValueOracle.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L7-L7) ):

```solidity
/// @audit Out of order with the prev import️ ⬆
7: import "../../../interface/valueOracle/INoyaValueOracle.sol";
```

</details>

### [N-27] Invalid NatSpec comment style

NatSpec comment in solidity should use `///` or `/* ... */` syntax.

There are 2 instances:

- *Registry.sol* ( [264-265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L264-L265) ):

```solidity
264: 
265:     // @dev This function is used to remove trusted positions from a vault
```

- *BaseConnector.sol* ( [133-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L133-L134) ):

```solidity
133: 
134:     // @dev the following functions are used to manage holding tokens in the registry
```

### [N-28] @openzeppelin/contracts should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

The imported version is `^4.8.1`.

<details>
<summary>There are 34 instances (click to show):</summary>

- *AccountingManager.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";

5: import { ERC4626, ERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/extensions/ERC4626.sol";
```

- *NoyaFeeReceiver.sol* ( [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L5) ):

```solidity
5: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```

- *Registry.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L5) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/AccessControl.sol";

5: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *BalancerFlashLoan.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L8), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L10) ):

```solidity
8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";

10: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *CamelotConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";
```

- *MaverickConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";
```

- *PancakeswapConnector.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L6) ):

```solidity
6: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721.sol";
```

- *PendleConnector.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L10) ):

```solidity
10: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *PrismaConnector.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L4) ):

```solidity
4: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *Keepers.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L5), [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L6) ):

```solidity
4: import "@openzeppelin/contracts-5.0/utils/cryptography/EIP712.sol";

5: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";

6: import "@openzeppelin/contracts-5.0/utils/cryptography/ECDSA.sol";
```

- *TimeLock.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/governance/TimelockController.sol";
```

- *BaseConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L8), [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L13) ):

```solidity
7: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

8: import "@openzeppelin/contracts-5.0/token/ERC721/utils/ERC721Holder.sol";

12: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721Receiver.sol";

13: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *ConnectorMock2.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *LZHelperReceiver.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```

- *LZHelperSender.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```

- *OmnichainManagerBaseChain.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L6) ):

```solidity
6: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *OmnichainManagerNormalChain.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *GenericSwapAndBridgeHandler.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L8) ):

```solidity
7: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *LifiImplementation.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L5), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L8) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";

5: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```

- *NoyaValueOracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L4) ):

```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```

- *ChainlinkOracleConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8) ):

```solidity
7: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

8: import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol";
```

- *UniswapValueOracle.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L6) ):

```solidity
6: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```

</details>

### [N-29] Lib @openzeppelin/contracts-upgradeable should be upgraded to a newer version

These contracts import contracts from `@openzeppelin/contracts-upgradeable`, but they are not using [the latest version](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/releases). Using the latest version ensures contract security with fixes for known vulnerabilities, access to the latest feature updates, and enhanced community support and engagement.

The imported version is `^4.8.1 || ^5.0.0`.

There is 1 instance:

- Global finding

### [N-30] Expressions for constant values should use `immutable` rather than `constant`

While it doesn't save any gas because the compiler knows that developers often make this mistake, it's still best to use the right tool for the task at hand. There is a difference between `constant` variables and `immutable` variables, and they should each be used in their appropriate contexts. `constants` should be used for literal values written into the code, and `immutable` variables should be used for expressions, or values calculated in, or passed into the constructor.

There are 4 instances:

- *Registry.sol* ( [15-15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L15-L15), [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L17-L17), [19-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L19-L19) ):

```solidity
15:     bytes32 public constant MAINTAINER_ROLE = keccak256("MAINTAINER_ROLE");

17:     bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE");

19:     bytes32 public constant EMERGENCY_ROLE = keccak256("EMERGENCY_ROLE");
```

- *Keepers.sol* ( [11-13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L11-L13) ):

```solidity
11:     bytes32 public constant TXTYPE_HASH = keccak256(
12:         "Execute(uint256 nonce,address destination,bytes data,uint256 gasLimit,address executor, uint256 deadline)"
13:     );
```

### [N-31] Consider moving duplicated strings to constants

Moving duplicate strings to constants can improve code maintainability and readability.

There are 2 instances:

- *AccountingManager.sol* ( [686-686](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L686-L686) ):

```solidity
686:             require(success, "Transfer failed.");
```

- *LifiImplementation.sol* ( [196-196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L196-L196) ):

```solidity
196:             require(success, "Transfer failed.");
```

### [N-32] Contracts containing only utility functions should be made into libraries

Consider using a `library` instead of a `contract` to provide utility functions.

There is 1 instance:

- *WETH_Oracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L4) ):

```solidity
4: contract WETH_Oracle {
```

### [N-33] Contract uses both `require()`/`revert()` as well as custom errors

Consider using just one method in a single file.

<details>
<summary>There are 16 instances (click to show):</summary>

- *AccountingManager.sol* ( [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16) ):

```solidity
16: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
```

- *Registry.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12) ):

```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

- *AaveConnector.sol* ( [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L11) ):

```solidity
11: contract AaveConnector is BaseConnector {
```

- *BalancerFlashLoan.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L12) ):

```solidity
12: contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {
```

- *Dolomite.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9) ):

```solidity
9: contract DolomiteConnector is BaseConnector {
```

- *MorphoBlueConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8) ):

```solidity
8: contract MorphoBlueConnector is BaseConnector {
```

- *PendleConnector.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12) ):

```solidity
12: contract PendleConnector is BaseConnector {
```

- *SiloConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8) ):

```solidity
8: contract SiloConnector is BaseConnector {
```

- *NoyaGovernanceBase.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L6) ):

```solidity
6: contract NoyaGovernanceBase {
```

- *LZHelperSender.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19) ):

```solidity
19: contract LZHelperSender is OAppSender {
```

- *OmnichainLogic.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L14) ):

```solidity
14: abstract contract OmnichainLogic is BaseConnector {
```

- *GenericSwapAndBridgeHandler.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10) ):

```solidity
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
```

- *LifiImplementation.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10) ):

```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {
```

- *NoyaValueOracle.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L10) ):

```solidity
10: contract NoyaValueOracle is INoyaValueOracle {
```

- *ChainlinkOracleConnector.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L10) ):

```solidity
10: contract ChainlinkOracleConnector is INoyaValueOracle {
```

- *UniswapValueOracle.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L12) ):

```solidity
12: contract UniswapValueOracle is INoyaValueOracle {
```

</details>

### [N-34] Error names should use CapWords style

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html)

There are 5 instances:

- *NoyaGovernanceBase.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L14) ):

```solidity
14:     error NoyaGovernance_Unauthorized(address sender);
```

- *NoyaValueOracle.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L18) ):

```solidity
18:     error NoyaOracle_PriceOracleUnavailable(address asset, address baseToken);
```

- *ChainlinkOracleConnector.sol* ( [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L37), [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L38), [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L39) ):

```solidity
37:     error NoyaChainlinkOracle_DATA_OUT_OF_DATE();

38:     error NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address asset, address baseToken, address source);

39:     error NoyaChainlinkOracle_INVALID_INPUT();
```

### [N-35] Contract name does not follow the Solidity Style Guide

According to the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names), contracts and libraries should be named using the CapWords style.

There is 1 instance:

- *WETH_Oracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L4) ):

```solidity
4: contract WETH_Oracle {
```

### [N-36] Functions should be named in mixedCase style

As the [Solidity Style Guide](https://docs.soliditylang.org/en/v0.8.21/style-guide.html#function-names) suggests: functions should be named in mixedCase style.

<details>
<summary>There are 42 instances (click to show):</summary>

- *AccountingManager.sol* ( [493](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L493), [627](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L627), [632](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L632) ):

```solidity
493:     function checkIfTVLHasDroped() public nonReentrant {

627:     function TVL() public view returns (uint256) {

632:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {
```

- *Registry.sol* ( [224](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L224) ):

```solidity
224:     function getPositionBP(uint256 vaultId, bytes32 _positionId) public view returns (PositionBP memory) {
```

- *AaveConnector.sol* ( [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114) ):

```solidity
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {
```

- *AerodromeConnector.sol* ( [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L125) ):

```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *BalancerConnector.sol* ( [162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L162) ):

```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *CamelotConnector.sol* ( [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L88) ):

```solidity
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *CompoundConnector.sol* ( [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L125) ):

```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *CurveConnector.sol* ( [265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L265), [279](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L279), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L335) ):

```solidity
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

279:     function LPToUnder(PoolInfo memory info, uint256 balance) public view returns (uint256, address) {

335:     function balanceOfLPToken(PoolInfo memory info) public view returns (uint256) {
```

- *Dolomite.sol* ( [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L106) ):

```solidity
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *FraxConnector.sol* ( [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L150) ):

```solidity
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *GearBoxV3.sol* ( [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L93) ):

```solidity
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *LidoConnector.sol* ( [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L91) ):

```solidity
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *MaverickConnector.sol* ( [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L153) ):

```solidity
153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *MorphoBlueConnector.sol* ( [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L118), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L137) ):

```solidity
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {
```

- *PendleConnector.sol* ( [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L97), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L149), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L166), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L183), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L203), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L257), [293](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L293) ):

```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {

149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)

166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)

183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)

203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {

257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

293:     function getYTValue(address market, uint256 balance) public view returns (uint256) {
```

- *PrismaConnector.sol* ( [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L145) ):

```solidity
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *SNXConnector.sol* ( [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L102), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L121) ):

```solidity
102:     function mintOrBurnSUSD(

121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *SiloConnector.sol* ( [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L109) ):

```solidity
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *StargateConnector.sol* ( [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L110) ):

```solidity
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *UNIv3Connector.sol* ( [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L127) ):

```solidity
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *BaseConnector.sol* ( [249](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L249), [271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271) ):

```solidity
249:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
```

- *ConnectorMock2.sol* ( [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L71) ):

```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
```

- *LZHelperSender.sol* ( [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L75) ):

```solidity
75:     function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
```

- *OmnichainManagerBaseChain.sol* ( [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L32), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51) ):

```solidity
32:     function updateTVL(uint256 chainId, uint256 tvl, uint256 updateTime) external nonReentrant {

51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {
```

- *OmnichainManagerNormalChain.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L19), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33) ):

```solidity
19:     function getTVL() public view returns (uint256) {

28:     function updateTVLInfo() external onlyManager {

33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {
```

- *TVLHelper.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L14) ):

```solidity
14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
```

</details>

### [N-37] Variable names for `immutable`s should use UPPER_CASE_WITH_UNDERSCORES

For `immutable` variable names, each word should use all capital letters, with underscores separating each word (UPPER_CASE_WITH_UNDERSCORES)

There are 5 instances:

- *AaveConnector.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L18-L18), [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L22-L22) ):

```solidity
18:     address immutable pool;

22:     address immutable poolBaseToken;
```

- *MorphoBlueConnector.sol* ( [13-13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L13-L13) ):

```solidity
13:     IMorpho public immutable morphoBlue;
```

- *UNIv3Connector.sol* ( [16-16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L16-L16), [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L17-L17) ):

```solidity
16:     INonfungiblePositionManager public immutable positionManager;

17:     IUniswapV3Factory public immutable factory;
```

### [N-38] Names of `public`/`external` functions and state variables should NOT be prefixed with underscore

It is recommended by the [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html#underscore-prefix-for-non-external-functions-and-variables).

<details>
<summary>There are 35 instances (click to show):</summary>

- *AaveConnector.sol* ( [114-114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114-L114), [120-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L120-L120) ):

```solidity
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {

120:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *AerodromeConnector.sol* ( [117-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L117-L117), [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L125-L125) ):

```solidity
117:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {

125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *BalancerConnector.sol* ( [162-162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L162-L162) ):

```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *CamelotConnector.sol* ( [88-88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L88-L88), [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L99-L99) ):

```solidity
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

99:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *CompoundConnector.sol* ( [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L125-L125), [134-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L134-L134) ):

```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *CurveConnector.sol* ( [265-265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L265-L265) ):

```solidity
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *Dolomite.sol* ( [106-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L106-L106) ):

```solidity
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *FraxConnector.sol* ( [142-142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L142-L142), [150-150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L150-L150) ):

```solidity
142:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {

150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *GearBoxV3.sol* ( [93-93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L93-L93) ):

```solidity
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *LidoConnector.sol* ( [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L91-L91) ):

```solidity
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *MaverickConnector.sol* ( [153-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L153-L153), [161-161](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L161-L161) ):

```solidity
153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

161:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *MorphoBlueConnector.sol* ( [118-118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L118-L118), [141-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L141-L141) ):

```solidity
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

141:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PendleConnector.sol* ( [257-257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L257-L257), [311-311](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L311-L311) ):

```solidity
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

311:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PrismaConnector.sol* ( [145-145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L145-L145), [164-164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L164-L164) ):

```solidity
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

164:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *SNXConnector.sol* ( [121-121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L121-L121), [128-128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L128-L128) ):

```solidity
121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

128:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *SiloConnector.sol* ( [109-109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L109-L109), [143-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L143-L143) ):

```solidity
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

143:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *StargateConnector.sol* ( [110-110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L110-L110), [123-123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L123-L123) ):

```solidity
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

123:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *UNIv3Connector.sol* ( [127-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L127-L127), [152-152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L152-L152) ):

```solidity
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

152:     function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
```

- *BaseConnector.sol* ( [263-263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L263-L263), [271-271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271-L271) ):

```solidity
263:     function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {

271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
```

- *OmnichainManagerBaseChain.sol* ( [51-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51-L51) ):

```solidity
51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {
```

- *OmnichainManagerNormalChain.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33-L33) ):

```solidity
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {
```

</details>

### [N-39] Named imports of parent contracts are missing

Consider adding named imports for all parent contracts.

<details>
<summary>There are 51 instances (click to show):</summary>

- *AccountingManager.sol* ( [16-16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16-L16) ):

```solidity
/// @audit IAccountingManager
/// @audit ReentrancyGuard
/// @audit Pausable
16: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
```

- *NoyaFeeReceiver.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7-L7) ):

```solidity
/// @audit Ownable
7: contract NoyaFeeReceiver is Ownable {
```

- *Registry.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12-L12) ):

```solidity
/// @audit AccessControl
/// @audit IPositionRegistry
/// @audit ReentrancyGuard
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

- *AaveConnector.sol* ( [11-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L11-L11) ):

```solidity
/// @audit BaseConnector
11: contract AaveConnector is BaseConnector {
```

- *AerodromeConnector.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L27-L27) ):

```solidity
/// @audit BaseConnector
27: contract AerodromeConnector is BaseConnector {
```

- *BalancerConnector.sol* ( [26-26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L26-L26) ):

```solidity
/// @audit BaseConnector
26: contract BalancerConnector is BaseConnector {
```

- *BalancerFlashLoan.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L12-L12) ):

```solidity
/// @audit ReentrancyGuard
12: contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {
```

- *CamelotConnector.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L30-L30) ):

```solidity
/// @audit BaseConnector
30: contract CamelotConnector is BaseConnector {
```

- *CompoundConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L7-L7) ):

```solidity
/// @audit BaseConnector
7: contract CompoundConnector is BaseConnector {
```

- *CurveConnector.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L24-L24) ):

```solidity
/// @audit BaseConnector
24: contract CurveConnector is BaseConnector {
```

- *Dolomite.sol* ( [9-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9-L9) ):

```solidity
/// @audit BaseConnector
9: contract DolomiteConnector is BaseConnector {
```

- *FraxConnector.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L18-L18) ):

```solidity
/// @audit BaseConnector
18: contract FraxConnector is BaseConnector {
```

- *GearBoxV3.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8-L8) ):

```solidity
/// @audit BaseConnector
8: contract Gearboxv3 is BaseConnector {
```

- *LidoConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7-L7) ):

```solidity
/// @audit BaseConnector
/// @audit ERC721Holder
7: contract LidoConnector is BaseConnector, ERC721Holder {
```

- *MaverickConnector.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29-L29) ):

```solidity
/// @audit BaseConnector
/// @audit IERC721Receiver
29: contract MaverickConnector is BaseConnector, IERC721Receiver {
```

- *MorphoBlueConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8-L8) ):

```solidity
/// @audit BaseConnector
8: contract MorphoBlueConnector is BaseConnector {
```

- *PancakeswapConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8-L8) ):

```solidity
/// @audit UNIv3Connector
8: contract PancakeswapConnector is UNIv3Connector {
```

- *PendleConnector.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12-L12) ):

```solidity
/// @audit BaseConnector
12: contract PendleConnector is BaseConnector {
```

- *PrismaConnector.sol* ( [11-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L11-L11) ):

```solidity
/// @audit BaseConnector
11: contract PrismaConnector is BaseConnector {
```

- *SNXConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7-L7) ):

```solidity
/// @audit BaseConnector
/// @audit IERC721Receiver
7: contract SNXV3Connector is BaseConnector, IERC721Receiver {
```

- *SiloConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8-L8) ):

```solidity
/// @audit BaseConnector
8: contract SiloConnector is BaseConnector {
```

- *StargateConnector.sol* ( [19-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L19-L19) ):

```solidity
/// @audit BaseConnector
19: contract StargateConnector is BaseConnector {
```

- *UNIv3Connector.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L12-L12) ):

```solidity
/// @audit BaseConnector
/// @audit ERC721Holder
12: contract UNIv3Connector is BaseConnector, ERC721Holder {
```

- *Keepers.sol* ( [9-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L9-L9) ):

```solidity
/// @audit EIP712
/// @audit Ownable2Step
9: contract Keepers is EIP712, Ownable2Step {
```

- *TimeLock.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L6-L6) ):

```solidity
/// @audit TimelockController
6: contract NoyaTimeLock is TimelockController {
```

- *Watchers.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L6-L6) ):

```solidity
/// @audit Keepers
6: contract Watchers is Keepers {
```

- *BaseConnector.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L22-L22) ):

```solidity
/// @audit IConnector
/// @audit ReentrancyGuard
22: contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {
```

- *LZHelperReceiver.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L18-L18) ):

```solidity
/// @audit OAppReceiver
18: contract LZHelperReceiver is OAppReceiver {
```

- *LZHelperSender.sol* ( [19-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19-L19) ):

```solidity
/// @audit OAppSender
19: contract LZHelperSender is OAppSender {
```

- *OmnichainLogic.sol* ( [14-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L14-L14) ):

```solidity
/// @audit BaseConnector
14: abstract contract OmnichainLogic is BaseConnector {
```

- *OmnichainManagerBaseChain.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L8-L8) ):

```solidity
/// @audit OmnichainLogic
8: contract OmnichainManagerBaseChain is OmnichainLogic {
```

- *OmnichainManagerNormalChain.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L10-L10) ):

```solidity
/// @audit OmnichainLogic
10: contract OmnichainManagerNormalChain is OmnichainLogic {
```

- *GenericSwapAndBridgeHandler.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10-L10) ):

```solidity
/// @audit NoyaGovernanceBase
/// @audit ISwapAndBridgeHandler
/// @audit ReentrancyGuard
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
```

- *LifiImplementation.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10-L10) ):

```solidity
/// @audit ISwapAndBridgeImplementation
/// @audit Ownable2Step
/// @audit ReentrancyGuard
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {
```

- *NoyaValueOracle.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L10-L10) ):

```solidity
/// @audit INoyaValueOracle
10: contract NoyaValueOracle is INoyaValueOracle {
```

- *ChainlinkOracleConnector.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L10-L10) ):

```solidity
/// @audit INoyaValueOracle
10: contract ChainlinkOracleConnector is INoyaValueOracle {
```

- *UniswapValueOracle.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L12-L12) ):

```solidity
/// @audit INoyaValueOracle
12: contract UniswapValueOracle is INoyaValueOracle {
```

</details>

### [N-40] Constants should be put on the left side of comparisons

Putting constants on the left side of comparison statements is a best practice known as [Yoda conditions](https://en.wikipedia.org/wiki/Yoda_conditions).
Although solidity's static typing system prevents accidental assignments within conditionals, adopting this practice can improve code readability and consistency, especially when working across multiple languages.

<details>
<summary>There are 154 instances (click to show):</summary>

- *AccountingManager.sol* ( [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L106), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L107), [108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L108), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L109), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L110), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L140), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L141), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L142), [186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186), [201](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L201), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L335), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L335), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371), [374](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L374), [397](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L397), [528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528), [619](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L619), [619](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L619), [634](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L634), [650](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L650), [684](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L684) ):

```solidity
/// @audit put `address(0)` on the left
106:         require(p._baseTokenAddress != address(0));

/// @audit put `address(0)` on the left
107:         require(p._valueOracle != address(0));

/// @audit put `address(0)` on the left
108:         require(p._withdrawFeeReceiver != address(0));

/// @audit put `address(0)` on the left
109:         require(p._performanceFeeReceiver != address(0));

/// @audit put `address(0)` on the left
110:         require(p._managementFeeReceiver != address(0));

/// @audit put `address(0)` on the left
140:         require(_withdrawFeeReceiver != address(0));

/// @audit put `address(0)` on the left
141:         require(_performanceFeeReceiver != address(0));

/// @audit put `address(0)` on the left
142:         require(_managementFeeReceiver != address(0));

/// @audit put `address(0)` on the left
186:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {

/// @audit put `0` on the left
201:         if (amount == 0) {

/// @audit put `false` on the left
335:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {

/// @audit put `true` on the left
335:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {

/// @audit put `false` on the left
361:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);

/// @audit put `false` on the left
361:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);

/// @audit put `true` on the left
371:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);

/// @audit put `false` on the left
371:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);

/// @audit put `0` on the left
374:         if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {

/// @audit put `false` on the left
397:         if (currentWithdrawGroup.isFullfilled == false) {

/// @audit put `0` on the left
528:             preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours

/// @audit put `false` on the left
619:             currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true

/// @audit put `true` on the left
619:             currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true

/// @audit put `0` on the left
634:         if (p.positionTypeId == 0) {

/// @audit put `0` on the left
650:         if (positionTypeId == 0) {

/// @audit put `address(0)` on the left
684:         if (token == address(0)) {
```

- *NoyaFeeReceiver.sol* ( [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L17) ):

```solidity
/// @audit put `address(0)` on the left
15:         require(_accountingManager != address(0));

/// @audit put `address(0)` on the left
16:         require(_baseToken != address(0));

/// @audit put `address(0)` on the left
17:         require(_receiver != address(0));
```

- *Registry.sol* ( [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L54), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L67), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L68), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L69), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L80), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L118), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L120), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L121), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L122), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L123), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L125), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L167), [168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L168), [169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L169), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L170), [251](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L251), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L304), [347](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L347) ):

```solidity
/// @audit put `address(0)` on the left
54:         if (vaults[_vaultId].accountManager == address(0)) revert NotExist();

/// @audit put `address(0)` on the left
67:         require(_governer != address(0));

/// @audit put `address(0)` on the left
68:         require(_maintainer != address(0));

/// @audit put `address(0)` on the left
69:         require(_emergency != address(0));

/// @audit put `MAX_NUM_HOLDING_POSITIONS` on the left
80:         require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);

/// @audit put `address(0)` on the left
118:         if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();

/// @audit put `address(0)` on the left
120:         require(_governer != address(0));

/// @audit put `address(0)` on the left
121:         require(_accountingManager != address(0));

/// @audit put `address(0)` on the left
122:         require(_baseToken != address(0));

/// @audit put `address(0)` on the left
123:         require(_maintainer != address(0));

/// @audit put `address(0)` on the left
124:         require(_keeperContract != address(0));

/// @audit put `address(0)` on the left
125:         require(_watcher != address(0));

/// @audit put `address(0)` on the left
167:         require(_governer != address(0));

/// @audit put `address(0)` on the left
168:         require(_maintainer != address(0));

/// @audit put `address(0)` on the left
169:         require(_keeperContract != address(0));

/// @audit put `address(0)` on the left
170:         require(_watcher != address(0));

/// @audit put `false` on the left
251:             if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();

/// @audit put `0` on the left
304:         if (index == 0) {

/// @audit put `0` on the left
347:         if (positionIndex == 0 && removePosition) return type(uint256).max;
```

- *AaveConnector.sol* ( [36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L36), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L37) ):

```solidity
/// @audit put `address(0)` on the left
36:         require(_pool != address(0));

/// @audit put `address(0)` on the left
37:         require(_poolBaseToken != address(0));
```

- *AerodromeConnector.sol* ( [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L43) ):

```solidity
/// @audit put `address(0)` on the left
43:         require(_router != address(0));
```

- *BalancerConnector.sol* ( [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L45), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L47), [177](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L177) ):

```solidity
/// @audit put `address(0)` on the left
45:         require(_balancerVault != address(0));

/// @audit put `address(0)` on the left
46:         require(bal != address(0));

/// @audit put `address(0)` on the left
47:         require(aura != address(0));

/// @audit put `address(0)` on the left
177:         if (pool.auraPoolAddress != address(0)) {
```

- *BalancerFlashLoan.sol* ( [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L25) ):

```solidity
/// @audit put `address(0)` on the left
25:         require(_balancerVault != address(0));
```

- *CamelotConnector.sol* ( [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L37), [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L38) ):

```solidity
/// @audit put `address(0)` on the left
37:         require(_router != address(0));

/// @audit put `address(0)` on the left
38:         require(_factory != address(0));
```

- *CompoundConnector.sol* ( [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L77), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L86) ):

```solidity
/// @audit put `0` on the left
77:         if (borrowBalanceInBase == 0) return type(uint256).max;

/// @audit put `0` on the left
86:         if (borrowBalanceInBase == 0) return 0;
```

- *CurveConnector.sol* ( [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L53), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L54), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L55), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L126), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L128), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L132), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L136), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L140), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L144), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L280), [283](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L283), [326](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L326), [345](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L345), [355](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L355) ):

```solidity
/// @audit put `address(0)` on the left
52:         require(_convexBooster != address(0));

/// @audit put `address(0)` on the left
53:         require(cvx != address(0));

/// @audit put `address(0)` on the left
54:         require(crv != address(0));

/// @audit put `address(0)` on the left
55:         require(prisma != address(0));

/// @audit put `address(0)` on the left
126:         address poolAddress = (poolInfo.tokens.length > 2 && poolInfo.zap != address(0)) ? poolInfo.zap : pool;

/// @audit put `2` on the left
128:         if (poolInfo.tokens.length == 2) {

/// @audit put `3` on the left
132:         } else if (poolInfo.tokens.length == 3) {

/// @audit put `4` on the left
136:         } else if (poolInfo.tokens.length == 4) {

/// @audit put `5` on the left
140:         } else if (poolInfo.tokens.length == 5) {

/// @audit put `6` on the left
144:         } else if (poolInfo.tokens.length == 6) {

/// @audit put `0` on the left
280:         if (balance == 0) return (0, info.tokens[info.defaultWithdrawIndex]);

/// @audit put `address(0)` on the left
283:         if (info.poolAddressIfDefaultWithdrawTokenIsAnotherPosition != address(0)) {

/// @audit put `address(0)` on the left
326:         if (info.convexRewardPool == address(0)) return 0;

/// @audit put `address(0)` on the left
345:         if (info.gauge == address(0)) return 0;

/// @audit put `address(0)` on the left
355:         if (prismaPool == address(0)) return 0;
```

- *Dolomite.sol* ( [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L24), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L51) ):

```solidity
/// @audit put `address(0)` on the left
24:         require(_depositWithdrawalProxy != address(0));

/// @audit put `0` on the left
51:         if (markets.length == 0) {
```

- *FraxConnector.sol* ( [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L124), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L126), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L133) ):

```solidity
/// @audit put `0` on the left
124:         if (_borrowerAmount == 0) return type(uint256).max;

/// @audit put `0` on the left
126:         if (_collateralAmount == 0) return 0;

/// @audit put `0` on the left
133:         if (currentPositionLTV == 0) return type(uint256).max; // loan is small
```

- *GearBoxV3.sol* ( [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L78), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L82) ):

```solidity
/// @audit put `address(0)` on the left
78:         if (approvalToken != address(0)) {

/// @audit put `address(0)` on the left
82:         if (approvalToken != address(0)) {
```

- *LidoConnector.sol* ( [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L24), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L26) ):

```solidity
/// @audit put `address(0)` on the left
23:         require(_lido != address(0));

/// @audit put `address(0)` on the left
24:         require(_lidoW != address(0));

/// @audit put `address(0)` on the left
25:         require(_steth != address(0));

/// @audit put `address(0)` on the left
26:         require(w != address(0));
```

- *MaverickConnector.sol* ( [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L47), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L49), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L141) ):

```solidity
/// @audit put `address(0)` on the left
46:         require(_mav != address(0));

/// @audit put `address(0)` on the left
47:         require(_veMav != address(0));

/// @audit put `address(0)` on the left
48:         require(mr != address(0));

/// @audit put `address(0)` on the left
49:         require(pi != address(0));

/// @audit put `0` on the left
141:             if (earnedInfo[i].earned != 0) {
```

- *MorphoBlueConnector.sol* ( [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L24), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L66), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L66), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L112), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L120) ):

```solidity
/// @audit put `address(0)` on the left
24:         require(MB != address(0));

/// @audit put `0` on the left
66:         if (p.collateral == 0 && p.supplyShares == 0) {

/// @audit put `0` on the left
66:         if (p.collateral == 0 && p.supplyShares == 0) {

/// @audit put `0` on the left
112:         if (borrowAmount == 0) return type(uint256).max;

/// @audit put `MORPHO_POSITION_ID` on the left
120:         if (positionInfo.positionTypeId == MORPHO_POSITION_ID) {
```

- *PancakeswapConnector.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L22) ):

```solidity
/// @audit put `address(0)` on the left
22:         require(MC != address(0));
```

- *PendleConnector.sol* ( [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L60), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L61), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L62), [259](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L259) ):

```solidity
/// @audit put `address(0)` on the left
60:         require(_pendleMarketDepositHelper != address(0));

/// @audit put `address(0)` on the left
61:         require(_pendleRouter != address(0));

/// @audit put `address(0)` on the left
62:         require(SR != address(0));

/// @audit put `PENDLE_POSITION_ID` on the left
259:         if (positionInfo.positionTypeId == PENDLE_POSITION_ID) {
```

- *PrismaConnector.sol* ( [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L147) ):

```solidity
/// @audit put `PRISMA_POSITION_ID` on the left
147:         if (positionInfo.positionTypeId == PRISMA_POSITION_ID) {
```

- *SNXConnector.sol* ( [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L21), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L51) ):

```solidity
/// @audit put `address(0)` on the left
21:         require(_SNXCoreProxy != address(0));

/// @audit put `0` on the left
51:         if (c == 0) {
```

- *SiloConnector.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L18), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L120), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L120) ):

```solidity
/// @audit put `address(0)` on the left
18:         require(SR != address(0));

/// @audit put `0` on the left
120:             if (depositAmount == 0 && borrowAmount == 0) {

/// @audit put `0` on the left
120:             if (depositAmount == 0 && borrowAmount == 0) {
```

- *StargateConnector.sol* ( [36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L36), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L37), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L115) ):

```solidity
/// @audit put `address(0)` on the left
36:         require(lpStacking != address(0));

/// @audit put `address(0)` on the left
37:         require(_stargateRouter != address(0));

/// @audit put `0` on the left
115:         if (lpAmount == 0) {
```

- *Keepers.sol* ( [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L28), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L53) ):

```solidity
/// @audit put `10` on the left
28:         require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);

/// @audit put `10` on the left
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
```

- *BaseConnector.sol* ( [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L142), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L233), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L257) ):

```solidity
/// @audit put `0` on the left
142:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {

/// @audit put `0` on the left
233:         if (positionTypeId == 0) {

/// @audit put `0` on the left
257:         if (amount == 0) {
```

- *ConnectorMock2.sol* ( [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L31), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L86) ):

```solidity
/// @audit put `0` on the left
31:         if (data.length == 0) {

/// @audit put `0` on the left
86:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
```

- *LZHelperReceiver.sol* ( [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L41), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L53) ):

```solidity
/// @audit put `address(0)` on the left
41:         require(lzHelperAddress != address(0));

/// @audit put `address(0)` on the left
53:         require(omniChainManager != address(0));
```

- *LZHelperSender.sol* ( [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L52) ):

```solidity
/// @audit put `address(0)` on the left
52:         require(lzHelperAddress != address(0));
```

- *OmnichainLogic.sol* ( [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L37), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L47), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L58), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L76) ):

```solidity
/// @audit put `address(0)` on the left
37:         require(_lzHelper != address(0));

/// @audit put `address(0)` on the left
47:         require(destinationAddress != address(0));

/// @audit put `0` on the left
58:         if (approvedBridgeTXN[transactionHash] != 0) delete approvedBridgeTXN[transactionHash];

/// @audit put `0` on the left
71:         if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {

/// @audit put `address(0)` on the left
76:             destChainAddress[bridgeRequest.destChainId] == address(0)
```

- *OmnichainManagerBaseChain.sol* ( [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L53) ):

```solidity
/// @audit put `OMNICHAIN_POSITION_ID` on the left
53:         if (positionTypeId == OMNICHAIN_POSITION_ID) {
```

- *OmnichainManagerNormalChain.sol* ( [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L35) ):

```solidity
/// @audit put `0` on the left
35:         if (bp.positionTypeId == 0) {
```

- *GenericSwapAndBridgeHandler.sol* ( [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L41), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L98), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L102), [105](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L105) ):

```solidity
/// @audit put `address(0)` on the left
30:         if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();

/// @audit put `address(0)` on the left
41:         require(_valueOracle != address(0));

/// @audit put `0` on the left
98:         if (_swapRequest.amount == 0) revert InvalidAmount();

/// @audit put `0` on the left
102:         if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {

/// @audit put `0` on the left
105:             if (_slippageTolerance == 0) {
```

- *LifiImplementation.sol* ( [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L86), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L93), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L112), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L154), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L194) ):

```solidity
/// @audit put `true` on the left
35:         require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER");

/// @audit put `address(0)` on the left
86:         if (_request.outputToken == address(0)) {

/// @audit put `address(0)` on the left
93:         if (_request.outputToken == address(0)) {

/// @audit put `LI_FI_GENERIC_SWAP_SELECTOR` on the left
112:         if (selector != LI_FI_GENERIC_SWAP_SELECTOR) {

/// @audit put `false` on the left
153:         if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();

/// @audit put `false` on the left
154:         if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId();

/// @audit put `address(0)` on the left
194:         if (token == address(0)) {
```

- *TVLHelper.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L19), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L45), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L49) ):

```solidity
/// @audit put `address(0)` on the left
19:             if (positions[i].calculatorConnector == address(0)) {

/// @audit put `0` on the left
45:             if (latestUpdateTime == 0 || positions[i].positionTimestamp < latestUpdateTime) {

/// @audit put `0` on the left
49:         if (latestUpdateTime == 0) {
```

- *NoyaValueOracle.sol* ( [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L72) ):

```solidity
/// @audit put `0` on the left
72:         if (asset == baseToken || amount == 0) {
```

- *ChainlinkOracleConnector.sol* ( [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L47), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L57), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L57), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L95), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L99), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L99), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L128), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L144), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L146) ):

```solidity
/// @audit put `address(0)` on the left
47:         require(_reg != address(0));

/// @audit put `1 hours` on the left
57:         if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {

/// @audit put `10 days` on the left
57:         if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {

/// @audit put `address(0)` on the left
95:         if (primarySource == address(0)) {

/// @audit put `ETH` on the left
99:         decimalsSource = decimalsSource == ETH || decimalsSource == USD ? primarySource : decimalsSource;

/// @audit put `USD` on the left
99:         decimalsSource = decimalsSource == ETH || decimalsSource == USD ? primarySource : decimalsSource;

/// @audit put `0` on the left
128:         if (price <= 0) {

/// @audit put `address(0)` on the left
144:         if (assetsSources[asset][baseToken] != address(0)) {

/// @audit put `address(0)` on the left
146:         } else if (assetsSources[baseToken][asset] != address(0)) {
```

- *UniswapValueOracle.sol* ( [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L39), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L50), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L63), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L66) ):

```solidity
/// @audit put `0` on the left
39:         if (_period == 0) revert INoyaValueOracle_InvalidInput();

/// @audit put `address(0)` on the left
50:         require(pool != address(0), "pool doesn't exist");

/// @audit put `address(0)` on the left
63:         if (pool == address(0)) {

/// @audit put `address(0)` on the left
66:         if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
```

</details>

### [N-41] `else`-block not required

One level of nesting can be removed by not having an `else` block when the `if`-block always jumps at the end. For example:
```solidity
if (condition) {
    body1...
    return x;
} else {
    body2...
}
```
can be changed to:
```solidity
if (condition) {
    body1...
    return x;
}
body2...
```

There is 1 instance:

- *ChainlinkOracleConnector.sol* ( [144-146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L144-L146) ):

```solidity
144:         if (assetsSources[asset][baseToken] != address(0)) {
145:             return (assetsSources[asset][baseToken], false);
146:         } else if (assetsSources[baseToken][asset] != address(0)) {
```

### [N-42] Large multiples of ten should use scientific notation

Use a scientific notation rather than decimal literals (e.g. `1e6` instead of `1000000`), for better code readability.

There are 3 instances:

- *AccountingManager.sol* ( [87-87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L87-L87), [89-89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L89-L89) ):

```solidity
/// @audit 200_000 -> 2e5
87:     uint256 public depositLimitTotalAmount = 1e6 * 200_000;

/// @audit 2000 -> 2e3
89:     uint256 public depositLimitPerTransaction = 1e6 * 2000;
```

- *GenericSwapAndBridgeHandler.sol* ( [16-16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L16-L16) ):

```solidity
/// @audit 50_000 -> 5e4
16:     uint256 public genericSlippageTolerance = 50_000; // 5% slippage tolerance
```

### [N-43] `TODO`s left in the code

TODOs may signal that a feature is missing or not ready for audit, consider resolving the issue and removing the TODO comment

There are 2 instances:

- *MaverickConnector.sol* ( [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L93) ):

```solidity
93:         _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); // TODO: check token A is eth
```

- *LZHelperSender.sol* ( [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L80) ):

```solidity
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
```

### [N-44] High cyclomatic complexity

Consider breaking down these blocks into more manageable units, by splitting things into utility functions, by reducing nesting, and by using early returns.

<details>
<summary>There is 1 instance (click to show):</summary>

- *CurveConnector.sol* ( [117-151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L117-L151) ):

```solidity
117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant
121:     {
122:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));
123:         PositionBP memory p = registry.getPositionBP(vaultId, positionId);
124:         PoolInfo memory poolInfo = abi.decode(p.additionalData, (PoolInfo));
125:         address token = poolInfo.tokens[depositIndex];
126:         address poolAddress = (poolInfo.tokens.length > 2 && poolInfo.zap != address(0)) ? poolInfo.zap : pool;
127:         _approveOperations(token, poolAddress, amount);
128:         if (poolInfo.tokens.length == 2) {
129:             uint256[2] memory amounts;
130:             amounts[depositIndex] = amount;
131:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
132:         } else if (poolInfo.tokens.length == 3) {
133:             uint256[3] memory amounts;
134:             amounts[depositIndex] = amount;
135:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
136:         } else if (poolInfo.tokens.length == 4) {
137:             uint256[4] memory amounts;
138:             amounts[depositIndex] = amount;
139:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
140:         } else if (poolInfo.tokens.length == 5) {
141:             uint256[5] memory amounts;
142:             amounts[depositIndex] = amount;
143:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
144:         } else if (poolInfo.tokens.length == 6) {
145:             uint256[6] memory amounts;
146:             amounts[depositIndex] = amount;
147:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
148:         }
149:         emit OpenCurvePosition(pool, depositIndex, amount, minAmount);
150:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
151:     }
```

</details>

### [N-45] Typos

All typos should be corrected.

<details>
<summary>There are 77 instances (click to show):</summary>

- *AccountingManager.sol* ( [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L29), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L48), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L50), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L76), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L77), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L78), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L146), [224](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L224), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L335), [358](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L358), [359](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L359), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371), [377](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L377), [385](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L385), [397](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L397), [416](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L416), [442](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L442), [483](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L483), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L486), [490](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L490), [493](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L493), [497](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L497), [515](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L515), [528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528), [534](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L534), [538](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L538), [540](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L540), [614](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L614), [618](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L618), [619](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L619) ):

```solidity
/// @audit fullfilled
29:     /// @dev we use this variable to prevent the withdraw group from being fullfilled before the needed amount is gathered

/// @audit preformance
48:     /// @notice preformanceFeeSharesWaitingForDistribution is the total amount of shares that are waiting for distribution of the performance fee

/// @audit preformance
50:     uint256 public preformanceFeeSharesWaitingForDistribution;

/// @audit Fullfilled
76:     /// @dev if isStarted is true and isFullfilled is false, it means that the withdraw group is active and we are gethering funds for these withdrawals

/// @audit Fullfilled
77:     /// @dev if isStarted is false and isFullfilled is false, it means that there is no active withdraw group

/// @audit Fullfilled
/// @audit fullfilled
78:     /// @dev if isStarted is true and isFullfilled is true, it means that the withdraw group is fullfilled and but there are still some withdraws that are waiting for execution

/// @audit Recepients
146:         emit FeeRecepientsChanged(_withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver);

/// @audit desposit
224:     * @dev this function is used to calculate the users desposit shares that has been deposited before the oldest update time of the vault

/// @audit Fullfilled
335:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {

/// @audit fullfilled
358:     /// @dev after starting the withdraw group, we can not start another withdraw group until the current withdraw group is fullfilled

/// @audit fullfilled
359:     /// @dev after starting the withdraw group, we can not calculate the withdraw shares until the withdraw group is fullfilled

/// @audit Fullfilled
361:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);

/// @audit Fullfilled
371:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);

/// @audit Fullfilled
377:         currentWithdrawGroup.isFullfilled = true;

/// @audit Fullfilled
385:         currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;

/// @audit Fullfilled
397:         if (currentWithdrawGroup.isFullfilled == false) {

/// @audit Fullfilled
416:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;

/// @audit fullfilled
442:         // if the withdraw group is fullfilled and there are no withdraws that are waiting for execution, we delete the withdraw group

/// @audit preformance
483:         preformanceFeeSharesWaitingForDistribution =

/// @audit preformance
486:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp

/// @audit Droped
490:     /// @notice checkIfTVLHasDroped is a function that is used to check if the TVL has dropped

/// @audit Droped
493:     function checkIfTVLHasDroped() public nonReentrant {

/// @audit preformance
497:             preformanceFeeSharesWaitingForDistribution = 0;

/// @audit preformance
515:             + preformanceFeeSharesWaitingForDistribution;

/// @audit preformance
528:             preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours

/// @audit preformance
534:         _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);

/// @audit preformance
538:         emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);

/// @audit preformance
540:         preformanceFeeSharesWaitingForDistribution = 0;

/// @audit fullfilled
614:     /// @notice if the withdraw group is not fullfilled, we can get the needed assets for the withdraw using this function

/// @audit fullfilled
618:         if ( // check if the withdraw group is fullfilled

/// @audit Fullfilled
619:             currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true
```

- *Registry.sol* ( [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L17), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L47), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L60), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L64), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L66), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L67), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L70), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L73), [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L74), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L75), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L94), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L110), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L120), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L129), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L144), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L149), [151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L151), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L160), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L166), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L167), [172](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L172), [179](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L179), [370](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L370), [455](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L455) ):

```solidity
/// @audit governer
/// @audit governer
16:     // The id of the governer role (used to change the maintainer and governer addresses of the vaults)

/// @audit GOVERNER
/// @audit GOVERNER
17:     bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE");

/// @audit Governer
46:     modifier onlyVaultGoverner(uint256 _vaultId) {

/// @audit governer
47:         if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {

/// @audit governer
/// @audit governer
60:      * @param _governer The address of the governer

/// @audit governer
64:      * @dev The governer role is the admin of itself, the maintainer role and the emergency role

/// @audit governer
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {

/// @audit governer
67:         require(_governer != address(0));

/// @audit GOVERNER
/// @audit governer
70:         _grantRole(GOVERNER_ROLE, _governer);

/// @audit GOVERNER
/// @audit GOVERNER
73:         _setRoleAdmin(GOVERNER_ROLE, GOVERNER_ROLE);

/// @audit GOVERNER
74:         _setRoleAdmin(MAINTAINER_ROLE, GOVERNER_ROLE);

/// @audit GOVERNER
75:         _setRoleAdmin(EMERGENCY_ROLE, GOVERNER_ROLE);

/// @audit governer
/// @audit governer
94:     * @param _governer The address of the governer

/// @audit governer
110:         address _governer,

/// @audit governer
120:         require(_governer != address(0));

/// @audit governer
/// @audit governer
129:         vault.governer = _governer;

/// @audit governer
144:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency

/// @audit governer
149:     * @dev The function is used to change the governer of a vault

/// @audit governer
/// @audit governer
151:     * @param _governer The address of the new governer

/// @audit governer
160:         address _governer,

/// @audit Governer
166:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

/// @audit governer
167:         require(_governer != address(0));

/// @audit governer
/// @audit governer
172:         vaults[vaultId].governer = _governer;

/// @audit governer
179:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency

/// @audit Postion
370:     function updateHoldingPostionWithTime(

/// @audit governer
455:             vaults[vaultId].governer,
```

- *CompoundConnector.sol* ( [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L53), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L78), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L95), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L128) ):

```solidity
/// @audit Blanace
53:         if (getCollBlanace(IComet(_market), false) == 0) {

/// @audit Blanace
78:         return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase;

/// @audit Blanace
95:     function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) {

/// @audit Blanace
128:         uint256 positiveBalance = getCollBlanace(IComet(market), false);
```

- *LidoConnector.sol* ( [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L39) ):

```solidity
/// @audit recieved
39:         // deposit recieved eth into Lido
```

- *NoyaGovernanceBase.sol* ( [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L81), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L86), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L87) ):

```solidity
/// @audit governer
81:      * @notice Ensures the caller is the governance (governer) for the vault

/// @audit governer
86:         (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);

/// @audit governer
87:         if (msg.sender != governer) revert NoyaGovernance_Unauthorized(msg.sender);
```

- *OmnichainManagerBaseChain.sol* ( [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L35) ):

```solidity
/// @audit Postion
35:         registry.updateHoldingPostionWithTime(
```

- *ChainlinkOracleConnector.sol* ( [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L113) ):

```solidity
/// @audit claculate
113:     * @dev The Chainlink price is the price of a token based on another token(or currency) so if we need to claculate the price of the later based on the first, we should put isInverse to true
```

</details>

### [N-46] Consider bounding input array length

The functions below take in an unbounded array, and make function calls for entries in the array. While the function will revert if it eventually runs out of gas, it may be a nicer user experience to require() that the length of the array is below some reasonable maximum, so that the user doesn't have to use up a full transaction's gas only to see that the transaction reverts.

<details>
<summary>There are 31 instances (click to show):</summary>

- *AccountingManager.sol* ( [551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608) ):

```solidity
551:         for (uint256 i = 0; i < retrieveData.length; i++) {

603:             for (uint256 i = 0; i < items.length; i++) {

608:             for (uint256 i = 0; i < items.length; i++) {
```

- *Registry.sol* ( [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214) ):

```solidity
138:         for (uint256 i = 0; i < _trustedTokens.length; i++) {

194:         for (uint256 i = 0; i < _connectorAddresses.length; i++) {

214:         for (uint256 i = 0; i < _tokens.length; i++) {
```

- *BalancerConnector.sol* ( [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77) ):

```solidity
54:         for (uint256 i = 0; i < rewardsPools.length; i++) {

77:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *BalancerFlashLoan.sol* ( [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89) ):

```solidity
74:             for (uint256 i = 0; i < tokens.length; i++) {

79:             for (uint256 i = 0; i < destinationConnector.length; i++) {

84:             for (uint256 i = 0; i < tokens.length; i++) {

89:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *CurveConnector.sol* ( [222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248) ):

```solidity
222:         for (uint256 i = 0; i < gauges.length; i++) {

234:         for (uint256 i = 0; i < pools.length; i++) {

248:         for (uint256 i = 0; i < rewardsPools.length; i++) {
```

- *GearBoxV3.sol* ( [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69) ):

```solidity
69:         for (uint256 i = 0; i < calls.length; i++) {
```

- *UNIv3Connector.sol* ( [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102) ):

```solidity
102:         for (uint256 i = 0; i < tokenIds.length; i++) {
```

- *Keepers.sol* ( [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L104) ):

```solidity
29:         for (uint256 i = 0; i < _owners.length; i++) {

44:         for (uint256 i = 0; i < _owners.length; i++) {

104:             for (uint256 i = 0; i < threshold;) {
```

- *BaseConnector.sol* ( [178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211) ):

```solidity
178:         for (uint256 i = 0; i < tokens.length; i++) {

189:         for (uint256 i = 0; i < tokens.length; i++) {

211:         for (uint256 i = 0; i < tokensIn.length; i++) {
```

- *ConnectorMock2.sol* ( [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L41), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L46) ):

```solidity
41:         for (uint256 i = 0; i < tokens.length; i++) {

46:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *GenericSwapAndBridgeHandler.sol* ( [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37), [148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148) ):

```solidity
37:         for (uint256 i = 0; i < usersAddresses.length; i++) {

148:         for (uint256 i = 0; i < _routes.length;) {
```

- *NoyaValueOracle.sol* ( [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88) ):

```solidity
41:         for (uint256 i = 0; i < baseCurrencies.length; i++) {

55:         for (uint256 i = 0; i < oracle.length; i++) {

88:         for (uint256 i = 0; i < sources.length; i++) {
```

- *ChainlinkOracleConnector.sol* ( [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74) ):

```solidity
74:         for (uint256 i = 0; i < assets.length; i++) {
```

</details>

### [N-47] Unnecessary casting

Unnecessary castings can be removed.

<details>
<summary>There are 16 instances (click to show):</summary>

- *AccountingManager.sol* ( [156-156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L156-L156) ):

```solidity
/// @audit address(msg.sender)
156:             IERC20(token).safeTransfer(address(msg.sender), amount);
```

- *AerodromeConnector.sol* ( [102-102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L102-L102) ):

```solidity
/// @audit address(gauge)
102:         IERC20(pool).forceApprove(address(gauge), liquidity);
```

- *BalancerConnector.sol* ( [58-58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L58-L58) ):

```solidity
/// @audit address(AURA)
58:         _updateTokenInRegistry(address(AURA));
```

- *CompoundConnector.sol* ( [65-65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L65-L65) ):

```solidity
/// @audit address(market)
65:         IRewards(rewardContract).claim(address(market), address(this), true);
```

- *FraxConnector.sol* ( [95-95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L95-L95) ):

```solidity
/// @audit IFraxPair(pool)
95:         IFraxPair(pool).repayAsset(sharesToRepay, address(this));
```

- *MorphoBlueConnector.sol* ( [128-128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L128-L128) ):

```solidity
/// @audit uint256(pos.supplyShares)
128:                 uint256(pos.supplyShares).toAssetsUp(market.totalSupplyAssets, market.totalSupplyShares);
```

- *PendleConnector.sol* ( [113-113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L113-L113), [188-188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L188-L188), [304-304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304-L304) ):

```solidity
/// @audit IPMarket(market)
113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

/// @audit IPMarket(market)
188:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

/// @audit IPMarket(market)
304:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
```

- *PrismaConnector.sol* ( [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L41-L41) ):

```solidity
/// @audit IBorrowerOperations(zap.borrowerOps())
41:         IBorrowerOperations(zap.borrowerOps()).setDelegateApproval(address(zap), approve);
```

- *StargateConnector.sol* ( [80-80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L80-L80) ):

```solidity
/// @audit IStargateLPStaking(LPStaking)
80:             IStargateLPStaking(LPStaking).withdraw(withdrawRequest.poolId, withdrawRequest.LPStakingAmount);
```

- *BaseConnector.sol* ( [96-96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L96-L96), [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L99-L99) ):

```solidity
/// @audit address(accountingManager)
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);

/// @audit address(msg.sender)
99:             IERC20(token).safeTransfer(address(msg.sender), amount);
```

- *GenericSwapAndBridgeHandler.sol* ( [108-108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L108-L108) ):

```solidity
/// @audit INoyaValueOracle(valueOracle)
108:             INoyaValueOracle _priceOracle = INoyaValueOracle(valueOracle);
```

- *LifiImplementation.sol* ( [87-87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L87-L87), [94-94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L94-L94) ):

```solidity
/// @audit address(_request.from)
87:             balanceOut0 = address(_request.from).balance;

/// @audit address(_request.from)
94:             balanceOut1 = address(_request.from).balance;
```

</details>

### [N-48] Unused contract variables

The following state variables are defined but not used.
It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.

There is 1 instance:

- *LZHelperReceiver.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24) ):

```solidity
24:     uint32 constant TVL_UPDATE = 1;
```

### [N-49] Unused function parameters

Function parameters that are defined but not used may be logical errors and need to be checked to see if any logic is missing.
If the parameter is not really needed, it should be removed, otherwise it will repeatedly cause confusion and make code maintenance difficult.
If the parameter cannot be removed directly (for example, if it is an override function), its name should be removed and some comment can be appended.

<details>
<summary>There are 25 instances (click to show):</summary>

- *AccountingManager.sol* ( [693-693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L693-L693), [697-697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L697-L697), [701-701](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L701-L701), [705-705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L705-L705) ):

```solidity
/// @audit shares
/// @audit receiver
693:     function mint(uint256 shares, address receiver) public override returns (uint256) {

/// @audit assets
/// @audit receiver
/// @audit owner
697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

/// @audit shares
/// @audit receiver
/// @audit shareOwner
701:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {

/// @audit assets
/// @audit receiver
705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {
```

- *AerodromeConnector.sol* ( [117-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L117-L117) ):

```solidity
/// @audit p
117:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
```

- *CamelotConnector.sol* ( [99-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L99-L99) ):

```solidity
/// @audit id
99:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *CompoundConnector.sol* ( [134-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L134-L134) ):

```solidity
/// @audit data
134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *FraxConnector.sol* ( [142-142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L142-L142) ):

```solidity
/// @audit p
142:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
```

- *MaverickConnector.sol* ( [161-161](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L161-L161) ):

```solidity
/// @audit id
161:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *MorphoBlueConnector.sol* ( [137-137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L137-L137) ):

```solidity
/// @audit collateral
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {
```

- *Watchers.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L8-L8) ):

```solidity
/// @audit withdrawAmount
/// @audit sentAmount
/// @audit data
8:     function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
```

- *ConnectorMock2.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L27-L27), [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L40-L40), [71-71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L71-L71), [75-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L75-L75) ):

```solidity
/// @audit caller
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)

/// @audit data
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {

/// @audit p
/// @audit baseToken
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

/// @audit positionTypeId
/// @audit data
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
```

</details>

### [N-50] Unused import

The identifier is imported but never used within the file.

<details>
<summary>There are 26 instances (click to show):</summary>

- *AccountingManager.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L5-L5), [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L7-L7) ):

```solidity
/// @audit ERC4626
/// @audit ERC20
5: import { ERC4626, ERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/extensions/ERC4626.sol";

/// @audit NoyaGovernanceBase
/// @audit PositionBP
7: import { NoyaGovernanceBase, PositionBP } from "../governance/NoyaGovernanceBase.sol";
```

- *BalancerFlashLoan.sol* ( [4-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L4-L4), [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L6-L6) ):

```solidity
/// @audit IERC20
4: import { IBalancerVault, IERC20 } from "../external/interfaces/Balancer/IBalancerVault.sol";

/// @audit IFlashLoanRecipient
5: import { IFlashLoanRecipient } from "../external/interfaces/Balancer/IFlashLoanRecipient.sol";

/// @audit PositionRegistry
/// @audit PositionBP
6: import { PositionRegistry, PositionBP } from "../accountingManager/Registry.sol";
```

- *PendleConnector.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L6-L6), [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L10-L10) ):

```solidity
/// @audit MarketApproxPtInLib
/// @audit MarketApproxPtOutLib
6: import { MarketApproxPtInLib, MarketApproxPtOutLib } from "../external/libraries/Pendle/MarketApproxPtInLib.sol";

/// @audit SafeERC20
10: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *PrismaConnector.sol* ( [4-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L4-L4) ):

```solidity
/// @audit SafeERC20
4: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *NoyaGovernanceBase.sol* ( [4-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L4-L4) ):

```solidity
/// @audit PositionRegistry
/// @audit PositionBP
4: import { PositionRegistry, PositionBP } from "../accountingManager/Registry.sol";
```

- *BaseConnector.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L5-L5), [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L6-L6) ):

```solidity
/// @audit NoyaGovernanceBase
5: import { NoyaGovernanceBase } from "../governance/NoyaGovernanceBase.sol";

/// @audit PositionRegistry
/// @audit PositionBP
6: import { PositionRegistry, PositionBP } from "../accountingManager/Registry.sol";
```

- *ConnectorMock2.sol* ( [5-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L5-L9), [11-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L11-L11) ):

```solidity
/// @audit SwapAndBridgeHandler
/// @audit SwapRequest
/// @audit BridgeRequest
5: import {
6:     SwapAndBridgeHandler,
7:     SwapRequest,
8:     BridgeRequest
9: } from "contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol";

/// @audit HoldingPI
11: import { HoldingPI } from "contracts/interface/IConnector.sol";
```

- *GenericSwapAndBridgeHandler.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L7-L7) ):

```solidity
/// @audit SafeERC20
/// @audit IERC20
7: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *LifiImplementation.sol* ( [5-5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L5-L5) ):

```solidity
/// @audit SafeERC20
5: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```

- *TVLHelper.sol* ( [4-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L4-L4) ):

```solidity
/// @audit PositionRegistry
/// @audit HoldingPI
4: import { PositionRegistry, HoldingPI } from "../accountingManager/Registry.sol";
```

</details>

### [N-51] Unused local variables

The following local variables are not used. It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.

<details>
<summary>There are 12 instances (click to show):</summary>

- *BalancerConnector.sol* ( [117-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L117-L117) ):

```solidity
117:             (PoolInfo memory _poolInfo, bytes32 positionId) = _getPoolInfo(p.poolId);
```

- *BalancerFlashLoan.sol* ( [69-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L69-L69) ):

```solidity
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
```

- *PendleConnector.sol* ( [79-79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L79-L79), [98-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L98-L98), [153-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153-L153), [153-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153-L153), [170-170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170-L170), [170-170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170-L170), [188-188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L188-L188), [190-190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L190-L190) ):

```solidity
79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

153:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

153:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

170:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

170:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();

188:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

190:         (uint256 netSyOut, uint256 netSyFee) = market.swapExactPtForSy(address(this), exactPTIn, swapData);
```

- *SNXConnector.sol* ( [123-123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L123-L123) ):

```solidity
123:         (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =
```

- *UNIv3Connector.sol* ( [129-129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L129-L129) ):

```solidity
129:         uint256 tokenId = abi.decode(p.data, (uint256));
```

</details>

### [N-52] Unused modifiers

The following `modifier`s are not used. It is recommended to check the code for logical omissions that cause them not to be used. If it's determined that they are not needed anywhere, it's best to remove them from the codebase to improve code clarity and minimize confusion.

There are 2 instances:

- *NoyaGovernanceBase.sol* ( [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L53), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L85) ):

```solidity
53:     modifier onlyEmergencyOrWatcher() {

85:     modifier onlyGovernance() {
```

### [N-53] Unused named return

Declaring named returns, but not using them, is confusing to the reader. Consider either completely removing them (by declaring just the type without a name), or remove the return statement and do a variable assignment. This would improve the readability of the code, and it may also help reduce regressions during future code refactors.

<details>
<summary>There are 22 instances (click to show):</summary>

- *AaveConnector.sol* ( [114-114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114-L114) ):

```solidity
/// @audit tvl
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {
```

- *CamelotConnector.sol* ( [88-88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L88-L88) ):

```solidity
/// @audit tvl
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *CurveConnector.sol* ( [265-265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L265-L265) ):

```solidity
/// @audit tvl
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *Dolomite.sol* ( [106-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L106-L106) ):

```solidity
/// @audit tvl
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *GearBoxV3.sol* ( [93-93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L93-L93) ):

```solidity
/// @audit tvl
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *LidoConnector.sol* ( [91-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L91-L91) ):

```solidity
/// @audit tvl
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *MaverickConnector.sol* ( [153-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L153-L153) ):

```solidity
/// @audit tvl
153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *PrismaConnector.sol* ( [145-145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L145-L145) ):

```solidity
/// @audit tvl
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *SiloConnector.sol* ( [71-74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L71-L74) ):

```solidity
/// @audit userLTV
/// @audit LiquidationThreshold
/// @audit isSolvent
71:     function getData(address siloToken)
72:         public
73:         view
74:         returns (uint256 userLTV, uint256 LiquidationThreshold, bool isSolvent)
```

- *StargateConnector.sol* ( [110-110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L110-L110) ):

```solidity
/// @audit tvl
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *BaseConnector.sol* ( [271-271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271-L271) ):

```solidity
/// @audit tvl
271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
```

- *LifiImplementation.sol* ( [189-189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L189-L189) ):

```solidity
/// @audit isNative
189:     function _isNative(IERC20 token) internal pure returns (bool isNative) {
```

- *NoyaValueOracle.sol* ( [81-84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L84) ):

```solidity
/// @audit value
81:     function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
82:         internal
83:         view
84:         returns (uint256 value)
```

- *ChainlinkOracleConnector.sol* ( [143-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L143-L143) ):

```solidity
/// @audit source
/// @audit isInverse
143:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) {
```

- *WETH_Oracle.sol* ( [5-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L5-L8) ):

```solidity
/// @audit roundId
/// @audit answer
/// @audit startedAt
/// @audit updatedAt
/// @audit answeredInRound
5:     function latestRoundData()
6:         external
7:         view
8:         returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)
```

</details>

### [N-54] Use delete instead of assigning values to `false`

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

There is 1 instance:

- *Keepers.sol* ( [49-49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L49-L49) ):

```solidity
49:                 isOwner[_owners[i]] = false;
```

### [N-55] Consider using `delete` rather than assigning zero to clear values

The `delete` keyword more closely matches the semantics of what is being done, and draws more attention to the changing of state, which may lead to a more thorough audit of its associated logic.

<details>
<summary>There are 9 instances (click to show):</summary>

- *AccountingManager.sol* ( [378-378](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L378-L378), [386-386](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L386-L386), [497-497](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L497-L497), [498-498](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L498-L498), [540-540](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L540-L540) ):

```solidity
378:         amountAskedForWithdraw = 0;

386:         currentWithdrawGroup.totalCBAmount = 0;

497:             preformanceFeeSharesWaitingForDistribution = 0;

498:             profitStoredTime = 0;

540:         preformanceFeeSharesWaitingForDistribution = 0;
```

- *Registry.sol* ( [360-360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L360-L360) ):

```solidity
360:             vault.isPositionUsed[holdingPositionId] = 0;
```

- *BalancerFlashLoan.sol* ( [44-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L44-L44) ):

```solidity
44:         caller = address(0);
```

- *OmnichainLogic.sol* ( [81-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L81-L81) ):

```solidity
81:         approvedBridgeTXN[txn] = 0;
```

- *UniswapValueOracle.sol* ( [71-71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L71-L71) ):

```solidity
71:         secondsAgos[1] = 0;
```

</details>

### [N-56] Consider using EIP-5267 to securely describe EIP-712 domains

[EIP-5267](https://eips.ethereum.org/EIPS/eip-5267) is a standard which allows for the retrieval and description of EIP-712 hash domains. This allows external tools to allow users to not just view the struct fields being signed, but the fields the domain the signature contains as well. This is especially useful when a project may exist on multiple chains and or in multiple contracts, and allows users/tools to verify that the signature is for the right fork, chain, version, contract, etc.

There are 2 instances:

- *Keepers.sol* ( [102-102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L102-L102), [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L125-L125) ):

```solidity
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));

125:         return _domainSeparatorV4();
```

### [N-57] Use the latest Solidity version

Upgrading to the [latest solidity version](https://github.com/ethereum/solc-js/tags) (0.8.19 for L2s) can optimize gas usage, take advantage of new features and improve overall contract efficiency. Where possible, based on compatibility requirements, it is recommended to use newer/latest solidity version to take advantage of the latest optimizations and features.

<details>
<summary>There are 41 instances (click to show):</summary>

- *AccountingManager.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *NoyaFeeReceiver.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *Registry.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *AaveConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *AerodromeConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *BalancerConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *BalancerFlashLoan.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *CamelotConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *CompoundConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *CurveConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *Dolomite.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *FraxConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *GearBoxV3.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *LidoConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *MaverickConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *MorphoBlueConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *PancakeswapConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *PendleConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *PrismaConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *SNXConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *SiloConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *StargateConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *UNIv3Connector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *Keepers.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *NoyaGovernanceBase.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *TimeLock.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *Watchers.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *BaseConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *ConnectorMock2.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *LZHelperReceiver.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *LZHelperSender.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *OmnichainLogic.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *OmnichainManagerBaseChain.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *OmnichainManagerNormalChain.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *GenericSwapAndBridgeHandler.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *LifiImplementation.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *TVLHelper.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *NoyaValueOracle.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *ChainlinkOracleConnector.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *UniswapValueOracle.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

- *WETH_Oracle.sol* ( [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L2) ):

```solidity
2: pragma solidity 0.8.20;
```

</details>

### [N-58] Use transfer libraries instead of low level calls to transfer native tokens

Consider using [`SafeTransferLib.safeTransferETH`](https://github.com/transmissions11/solmate/blob/fadb2e2778adbf01c80275bfb99e5c14969d964b/src/utils/SafeTransferLib.sol#L15) or [`Address.sendValue`](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/9e3f4d60c581010c4a3979480e07cc7752f124cc/contracts/utils/Address.sol#L41) for clearer semantic meaning instead of using a low level `call`.

There are 2 instances:

- *AccountingManager.sol* ( [685-685](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L685-L685) ):

```solidity
685:             (bool success,) = payable(msg.sender).call{ value: amount }("");
```

- *LifiImplementation.sol* ( [195-195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195) ):

```solidity
195:             (bool success,) = payable(userAddress).call{ value: amount }("");
```

### [N-59] Use a struct to encapsulate multiple function parameters

If a function has too many parameters, replacing them with a struct can improve code readability and maintainability, increase reusability, and reduce the likelihood of errors when passing the parameters.

<details>
<summary>There are 12 instances (click to show):</summary>

- *Registry.sol* ( [106-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L106-L117), [158-166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L158-L166), [238-246](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L238-L246), [293-301](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L293-L301), [335-341](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L335-L341), [370-377](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L370-L377) ):

```solidity
106:     function addVault(
107:         uint256 vaultId,
108:         address _accountingManager,
109:         address _baseToken,
110:         address _governer,
111:         address _maintainer,
112:         address _maintainerWithoutTimelock,
113:         address _keeperContract,
114:         address _watcher,
115:         address _emergency,
116:         address[] calldata _trustedTokens
117:     ) external onlyRole(MAINTAINER_ROLE) {

158:     function changeVaultAddresses(
159:         uint256 vaultId,
160:         address _governer,
161:         address _maintainer,
162:         address _maintainerWithoutTimelock,
163:         address _keeperContract,
164:         address _watcher,
165:         address _emergency
166:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

238:     function addTrustedPosition(
239:         uint256 vaultId,
240:         uint256 _positionTypeId,
241:         address calculatorConnector,
242:         bool onlyOwner,
243:         bool _isDebt,
244:         bytes calldata _data,
245:         bytes calldata _additionalData
246:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {

293:     function updateHoldingPosition(
294:         Vault storage vault,
295:         uint256 vaultId,
296:         bytes32 _positionId,
297:         bytes calldata d,
298:         bytes calldata AD,
299:         uint256 index,
300:         bytes32 holdingPositionId
301:     ) internal returns (uint256) {

335:     function updateHoldingPosition(
336:         uint256 vaultId,
337:         bytes32 _positionId,
338:         bytes calldata _data,
339:         bytes calldata additionalData,
340:         bool removePosition
341:     ) public vaultExists(vaultId) returns (uint256) {

370:     function updateHoldingPostionWithTime(
371:         uint256 vaultId,
372:         bytes32 _positionId,
373:         bytes calldata _data,
374:         bytes calldata additionalData,
375:         bool removePosition,
376:         uint256 positionTimestamp
377:     ) external vaultExists(vaultId) {
```

- *BalancerConnector.sol* ( [64-70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64-L70) ):

```solidity
64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant {
```

- *CurveConnector.sol* ( [45-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L45-L51) ):

```solidity
45:     constructor(
46:         address _convexBooster,
47:         address cvx,
48:         address crv,
49:         address prisma,
50:         BaseConnectorCP memory baseConnectorParams
51:     ) BaseConnector(baseConnectorParams) {
```

- *GearBoxV3.sol* ( [62-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L62-L68) ):

```solidity
62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {
```

- *LidoConnector.sol* ( [20-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L20-L22) ):

```solidity
20:     constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)
21:         BaseConnector(baseConnectorParams)
22:     {
```

- *MaverickConnector.sol* ( [43-45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L43-L45) ):

```solidity
43:     constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)
44:         BaseConnector(baseCP)
45:     {
```

- *PrismaConnector.sol* ( [52-56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L52-L56) ):

```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {
```

</details>

### [N-60] Returning a struct instead of a bunch of variables is better

If a function returns [too many variables](https://docs.soliditylang.org/en/v0.8.21/contracts.html#returning-multiple-values), replacing them with a struct can improve code readability, maintainability and reusability.

<details>
<summary>There are 6 instances (click to show):</summary>

- *AccountingManager.sol* ( [505-505](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L505-L505), [596-599](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L596-L599) ):

```solidity
505:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {

596:     function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
597:         public
598:         view
599:         returns (DepositRequest[] memory depositData, WithdrawRequest[] memory withdrawData)
```

- *Registry.sol* ( [449-452](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L449-L452), [516-516](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L516-L516) ):

```solidity
449:     function getGovernanceAddresses(uint256 vaultId)
450:         public
451:         view
452:         returns (address, address, address, address, address, address)

516:     function getVaultAddresses(uint256 vaultId) public view returns (address, address) {
```

- *BalancerConnector.sol* ( [189-189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L189-L189) ):

```solidity
189:     function _getPoolInfo(bytes32 pooId) internal view returns (PoolInfo memory, bytes32) {
```

- *CurveConnector.sol* ( [279-279](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L279-L279) ):

```solidity
279:     function LPToUnder(PoolInfo memory info, uint256 balance) public view returns (uint256, address) {
```

</details>

### [N-61] Events that mark critical parameter changes should contain both the old and the new value

This should especially be done if the new value is not required to be different from the old value.

<details>
<summary>There are 18 instances (click to show):</summary>

- *AccountingManager.sol* ( [127-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L127-L127), [675-675](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L675-L675), [680-680](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L680-L680) ):

```solidity
127:         emit ValueOracleUpdated(address(_valueOracle));

675:         emit SetDepositWaitingTime(_depositWaitingTime);

680:         emit SetWithdrawWaitingTime(_withdrawWaitingTime);
```

- *Registry.sol* ( [217-217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L217-L217) ):

```solidity
217:         emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted);
```

- *GearBoxV3.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L33-L33) ):

```solidity
33:         emit OpenAccount(facade, ref);
```

- *PancakeswapConnector.sol* ( [43-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L43-L43) ):

```solidity
43:         emit UpdatePosition(tokenId);
```

- *UNIv3Connector.sol* ( [56-56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L56-L56) ):

```solidity
56:         emit OpenPosition(p, tokenId);
```

- *Keepers.sol* ( [66-66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L66-L66) ):

```solidity
66:         emit UpdateThreshold(_threshold);
```

- *BaseConnector.sol* ( [50-50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L50-L50), [60-60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L60-L60), [69-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L69-L69), [143-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L143-L143) ):

```solidity
50:         emit MinimumHealthFactorUpdated(_minimumHealthFactor);

60:         emit SwapHandlerUpdated(_swapHandler);

69:         emit ValueOracleUpdated(_valueOracle);

143:             emit UpdateTokenInRegistry(token, remove);
```

- *OmnichainLogic.sol* ( [49-49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L49-L49), [60-60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L60-L60), [70-70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L70-L70) ):

```solidity
49:         emit UpdateChainInfo(chainId, destinationAddress);

60:         emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp);

70:         emit StartBridgeTransaction(bridgeRequest, txn);
```

- *GenericSwapAndBridgeHandler.sol* ( [50-50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L50-L50), [160-160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160-L160) ):

```solidity
50:         emit SetValueOracle(_valueOracle);

160:         emit RouteUpdate(_routeId, false);
```

- *ChainlinkOracleConnector.sol* ( [61-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L61-L61) ):

```solidity
61:         emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
```

</details>

### [N-62] Contract variables should have comments

Consider adding some comments on non-public contract variables to explain what they are supposed to do. This will help for future code reviews.

<details>
<summary>There are 13 instances (click to show):</summary>

- *AerodromeConnector.sol* ( [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L33-L33), [34-34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L34-L34) ):

```solidity
33:     IRouter aerodromeRouter;

34:     IVoter voter;
```

- *BalancerConnector.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L27-L27) ):

```solidity
27:     address internal balancerVault;
```

- *BalancerFlashLoan.sol* ( [15-15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L15-L15), [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L17-L17) ):

```solidity
15:     IBalancerVault internal vault;

17:     address caller;
```

- *MaverickConnector.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L30-L30), [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L31-L31), [32-32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L32-L32), [33-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L33-L33) ):

```solidity
30:     address mav;

31:     address veMav;

32:     address maverickRouter;

33:     IPositionInspector positionInspector;
```

- *StargateConnector.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L22-L22), [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L23-L23), [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L24-L24) ):

```solidity
22:     IStargateLPStaking LPStaking;

23:     IStargateRouter stargateRouter;

24:     address rewardToken;
```

- *LZHelperSender.sol* ( [23-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L23-L23) ):

```solidity
23:     bytes messageSetting;
```

</details>

### [N-63] Missing event when a state variables is set in constructor

The initial states set in a constructor are important and should be recorded in the event.

<details>
<summary>There are 68 instances (click to show):</summary>

- *AccountingManager.sol* ( [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L99), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L100), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L101), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L102), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L103), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L104), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L119), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L120) ):

```solidity
99:         baseToken = IERC20(p._baseTokenAddress);

100:         valueOracle = INoyaValueOracle(p._valueOracle);

101:         lastFeeDistributionTime = block.timestamp;

102:         withdrawFeeReceiver = p._withdrawFeeReceiver;

103:         performanceFeeReceiver = p._performanceFeeReceiver;

104:         managementFeeReceiver = p._managementFeeReceiver;

118:         withdrawFee = p._withdrawFee;

119:         performanceFee = p._performanceFee;

120:         managementFee = p._managementFee;
```

- *NoyaFeeReceiver.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L18), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L19), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L20) ):

```solidity
18:         accountingManager = _accountingManager;

19:         baseToken = _baseToken;

20:         receiver = _receiver;
```

- *Registry.sol* ( [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L76) ):

```solidity
76:         flashLoan = _flashLoan;
```

- *AerodromeConnector.sol* ( [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L44), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L45) ):

```solidity
44:         aerodromeRouter = IRouter(_router);

45:         voter = IVoter(_voter);
```

- *BalancerConnector.sol* ( [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L49), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L50) ):

```solidity
48:         AURA = aura;

49:         BAL = bal;

50:         balancerVault = _balancerVault;
```

- *BalancerFlashLoan.sol* ( [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L28) ):

```solidity
27:         vault = IBalancerVault(_balancerVault);

28:         registry = _registry;
```

- *CamelotConnector.sol* ( [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L39), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L40) ):

```solidity
39:         router = ICamelotRouter(_router);

40:         factory = ICamelotFactory(_factory);
```

- *CurveConnector.sol* ( [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L56), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L57), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L58), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L59) ):

```solidity
56:         convexBooster = IBooster(_convexBooster);

57:         CVX = cvx;

58:         CRV = crv;

59:         PRISMA = prisma;
```

- *Dolomite.sol* ( [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L26), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L27) ):

```solidity
25:         depositWithdrawalProxy = IDepositWithdrawalProxy(_depositWithdrawalProxy);

26:         dolomiteMargin = IDolomiteMargin(_dolomiteMargin);

27:         borrowPositionProxy = IBorrowPositionProxyV1(_borrowPositionProxy);
```

- *LidoConnector.sol* ( [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L29), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L30) ):

```solidity
27:         lido = _lido;

28:         lidoWithdrawal = _lidoW;

29:         steth = _steth;

30:         weth = w;
```

- *MaverickConnector.sol* ( [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L50), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L51), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L53) ):

```solidity
50:         mav = _mav;

51:         veMav = _veMav;

52:         maverickRouter = mr;

53:         positionInspector = IPositionInspector(pi);
```

- *PancakeswapConnector.sol* ( [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L23) ):

```solidity
23:         masterchef = IMasterchefV3(MC);
```

- *PendleConnector.sol* ( [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L63), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L64), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L65) ):

```solidity
63:         pendleMarketDepositHelper = IPendleMarketDepositHelper(_pendleMarketDepositHelper);

64:         pendleRouter = IPAllActionV3(_pendleRouter);

65:         staticRouter = IPendleStaticRouter(SR);
```

- *SNXConnector.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L22) ):

```solidity
22:         SNXCoreProxy = IV3CoreProxy(_SNXCoreProxy);
```

- *SiloConnector.sol* ( [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L20), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L21), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L23) ):

```solidity
20:         siloRepository = ISiloRepository(SR);

21:         MINIMUM_HEALTH_FACTOR = 5e17;

23:         minimumHealthFactor = MINIMUM_HEALTH_FACTOR;
```

- *StargateConnector.sol* ( [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L39), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L40), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L41) ):

```solidity
39:         LPStaking = IStargateLPStaking(lpStacking);

40:         stargateRouter = IStargateRouter(_stargateRouter);

41:         rewardToken = LPStaking.stargate();
```

- *Keepers.sol* ( [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L30), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L33) ):

```solidity
30:             isOwner[_owners[i]] = true;

32:         numOwners = _owners.length;

33:         threshold = _threshold;
```

- *NoyaGovernanceBase.sol* ( [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L24) ):

```solidity
23:         registry = _registry;

24:         vaultId = _vaultId;
```

- *BaseConnector.sol* ( [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L34), [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L35), [36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L36) ):

```solidity
34:         swapHandler = params.swapHandler;

35:         valueOracle = params.valueOracle;

36:         minimumHealthFactor = MINIMUM_HEALTH_FACTOR;
```

- *ConnectorMock2.sol* ( [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L24) ):

```solidity
23:         registry = PositionRegistry(_registry);

24:         vaultId = _vaultId;
```

- *OmnichainLogic.sol* ( [36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L36) ):

```solidity
36:         lzHelper = _lzHelper;
```

- *OmnichainManagerBaseChain.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L22) ):

```solidity
22:         DUST_LEVEL = dl;
```

- *GenericSwapAndBridgeHandler.sol* ( [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L38), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L40) ):

```solidity
38:             isEligibleToUse[usersAddresses[i]] = true;

40:         valueOracle = INoyaValueOracle(_valueOracle);
```

- *LifiImplementation.sol* ( [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L29) ):

```solidity
28:         isHandler[swapHandler] = true;

29:         lifi = _lifi;
```

- *NoyaValueOracle.sol* ( [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L31) ):

```solidity
31:         registry = _registry;
```

- *ChainlinkOracleConnector.sol* ( [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L48) ):

```solidity
48:         registry = PositionRegistry(_reg);
```

- *UniswapValueOracle.sol* ( [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L33) ):

```solidity
32:         factory = _factory;

33:         registry = _registry;
```

</details>

### [N-64] Empty bytes check is missing

Passing empty bytes to a function can cause unexpected behavior, such as certain operations failing, producing incorrect results, or wasting gas. It is recommended to check that all byte parameters are not empty.

<details>
<summary>There are 20 instances (click to show):</summary>

- *AccountingManager.sol* ( [150-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L150-L153), [257-262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L257-L262) ):

```solidity
/// @audit _data
150:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
151:         external
152:         returns (uint256)
153:     {

/// @audit addLPdata
257:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
258:         public
259:         onlyManager
260:         whenNotPaused
261:         nonReentrant
262:     {
```

- *Registry.sol* ( [238-246](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L238-L246), [335-341](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L335-L341), [370-377](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L370-L377) ):

```solidity
/// @audit _data
/// @audit _additionalData
238:     function addTrustedPosition(
239:         uint256 vaultId,
240:         uint256 _positionTypeId,
241:         address calculatorConnector,
242:         bool onlyOwner,
243:         bool _isDebt,
244:         bytes calldata _data,
245:         bytes calldata _additionalData
246:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {

/// @audit _data
/// @audit additionalData
335:     function updateHoldingPosition(
336:         uint256 vaultId,
337:         bytes32 _positionId,
338:         bytes calldata _data,
339:         bytes calldata additionalData,
340:         bool removePosition
341:     ) public vaultExists(vaultId) returns (uint256) {

/// @audit _data
/// @audit additionalData
370:     function updateHoldingPostionWithTime(
371:         uint256 vaultId,
372:         bytes32 _positionId,
373:         bytes calldata _data,
374:         bytes calldata additionalData,
375:         bool removePosition,
376:         uint256 positionTimestamp
377:     ) external vaultExists(vaultId) {
```

- *BalancerFlashLoan.sol* ( [37-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L37-L40), [54-59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54-L59) ):

```solidity
/// @audit userData
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
38:         external
39:         nonReentrant
40:     {

/// @audit userData
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
```

- *PendleConnector.sol* ( [183-187](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L183-L187) ):

```solidity
/// @audit swapData
183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant
187:     {
```

- *Keepers.sol* ( [84-93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L84-L93) ):

```solidity
/// @audit data
84:     function execute(
85:         address destination,
86:         bytes calldata data,
87:         uint256 gasLimit,
88:         address executor,
89:         bytes32[] memory sigR,
90:         bytes32[] memory sigS,
91:         uint8[] memory sigV,
92:         uint256 deadline
93:     ) public {
```

- *BaseConnector.sol* ( [84-87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L84-L87), [122-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122-L127), [169-173](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L169-L173) ):

```solidity
/// @audit data
84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
85:         external
86:         returns (uint256)
87:     {

/// @audit data
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant {

/// @audit data
169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
170:         external
171:         override
172:         nonReentrant
173:     {
```

- *ConnectorMock2.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L40-L40), [51-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L51-L51), [59-59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L59-L59), [65-65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L65-L65) ):

```solidity
/// @audit data
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {

/// @audit data
51:     function updatePositionToRegistryUsingType(bytes32 _positionId, bytes memory data, bool remove) external {

/// @audit data
59:     function addPositionToRegistryUsingType(uint256 _positionType, bytes memory data) external {

/// @audit data
65:     function addPositionToRegistry(bytes memory data) external {
```

- *LZHelperSender.sol* ( [36-36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36) ):

```solidity
/// @audit _messageSetting
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
```

</details>

### [N-65] Don't define functions with the same name in a contract

In Solidity, while function overriding allows for functions with the same name to coexist, it is advisable to avoid this practice to enhance code readability and maintainability. Having multiple functions with the same name, even with different parameters or in inherited contracts, can cause confusion and increase the likelihood of errors during development, testing, and debugging. Using distinct and descriptive function names not only clarifies the purpose and behavior of each function, but also helps prevent unintended function calls or incorrect overriding. By adopting a clear and consistent naming convention, developers can create more comprehensible and maintainable smart contracts.

<details>
<summary>There are 7 instances (click to show):</summary>

- *AccountingManager.sol* ( [697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L697), [705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L705) ):

```solidity
/// @audit Different function with same name found on line 304
697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

/// @audit Different function with same name found on line 200
705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {
```

- *Registry.sol* ( [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L335) ):

```solidity
/// @audit Different function with same name found on line 293
335:     function updateHoldingPosition(
```

- *BalancerConnector.sol* ( [184](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L184) ):

```solidity
/// @audit Different function with same name found on line 175
184:     function totalLpBalanceOf(bytes32 poolId) public view returns (uint256) {
```

- *BaseConnector.sol* ( [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L158) ):

```solidity
/// @audit Different function with same name found on line 135
158:     function _updateTokenInRegistry(address token) internal {
```

- *ConnectorMock2.sol* ( [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L91) ):

```solidity
/// @audit Different function with same name found on line 79
91:     function _updateTokenInRegistry(address token) internal {
```

- *NoyaValueOracle.sol* ( [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L95) ):

```solidity
/// @audit Different function with same name found on line 81
95:     function _getValue(address quotingToken, address baseToken, uint256 amount) internal view returns (uint256) {
```

</details>

### [N-66] Multiple mappings with same keys can be combined into a single struct mapping for readability

Well-organized data structures make code reviews easier, which may lead to fewer bugs. Consider combining related mappings into mappings to structs, so it's clear what data is related.

There are 7 instances:

- *LZHelperSender.sol* ( [20-20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L20-L20), [21-21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L21-L21) ):

```solidity
20:     mapping(uint256 => ChainInfo) public chainInfo; // chainId => ChainInfo

21:     mapping(uint256 => VaultInfo) public vaultIdToVaultInfo; // vaultId => VaultInfo
```

- *GenericSwapAndBridgeHandler.sol* ( [13-13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L13-L13), [15-15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L15-L15) ):

```solidity
13:     mapping(address => bool) public isEligibleToUse;

15:     mapping(address => mapping(address => uint256)) public slippageTolerance;
```

- *NoyaValueOracle.sol* ( [13-13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L13-L13), [14-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L14-L14), [16-16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L16-L16) ):

```solidity
13:     mapping(address => INoyaValueOracle) public defaultPriceSource;

14:     mapping(address => mapping(address => address[])) public priceRoutes;

16:     mapping(address => mapping(address => INoyaValueOracle)) public priceSource;
```

### [N-67] Function state mutability can be restricted to view

Function state mutability can be restricted to view

There is 1 instance:

- *BaseConnector.sol* ( [267-267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267) ):

```solidity
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {
```

### [N-68] Missing event for critical changes

Events should be emitted when critical changes are made to the contracts.

<details>
<summary>There are 6 instances (click to show):</summary>

- *Registry.sol* ( [79-82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L79-L82) ):

```solidity
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) {
80:         require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);
81:         maxNumHoldingPositions = _maxNumHoldingPositions;
82:     }
```

- *LZHelperReceiver.sol* ( [40-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L43), [52-55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L55) ):

```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
41:         require(lzHelperAddress != address(0));
42:         chainInfo[lzChainId] = ChainInfo(chainId, lzHelperAddress);
43:     }

52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
53:         require(omniChainManager != address(0));
54:         vaultIdToVaultInfo[vaultId] = VaultInfo(baseChainId, omniChainManager);
55:     }
```

- *LZHelperSender.sol* ( [36-38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L38), [51-54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L51-L54), [63-65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L63-L65) ):

```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
37:         messageSetting = _messageSetting;
38:     }

51:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
52:         require(lzHelperAddress != address(0));
53:         chainInfo[chainId] = ChainInfo(lzChainId, lzHelperAddress);
54:     }

63:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
64:         vaultIdToVaultInfo[vaultId] = VaultInfo(baseChainId, omniChainManager);
65:     }
```

</details>

### [N-69] Duplicated `require()`/`revert()` checks should be refactored

Refactoring duplicate `require()`/`revert()` checks into a modifier or function can make the code more concise, readable and maintainable, and less likely to make errors or omissions when modifying the `require()` or `revert()`.

<details>
<summary>There are 21 instances (click to show):</summary>

- *AccountingManager.sol* ( [116-116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L116-L116), [202-202](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L202-L202), [336-336](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L336-L336) ):

```solidity
/// @audit Duplicated on line 175
116:             revert NoyaAccounting_INVALID_FEE();

/// @audit Duplicated on line 465, 458, 571
202:             revert NoyaAccounting_INVALID_AMOUNT();

/// @audit Duplicated on line 398
336:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
```

- *Registry.sol* ( [67-67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L67-L67), [68-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L68-L68), [118-118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L118-L118), [124-124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L124-L124), [125-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L125-L125), [306-306](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L306-L306) ):

```solidity
/// @audit Duplicated on line 120, 167
67:         require(_governer != address(0));

/// @audit Duplicated on line 123, 168
68:         require(_maintainer != address(0));

/// @audit Duplicated on line 250
118:         if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();

/// @audit Duplicated on line 169
124:         require(_keeperContract != address(0));

/// @audit Duplicated on line 170
125:         require(_watcher != address(0));

/// @audit Duplicated on line 344
306:                 revert InvalidPosition(_positionId);
```

- *AaveConnector.sol* ( [73-73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L73-L73) ):

```solidity
/// @audit Duplicated on line 104
73:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
```

- *CompoundConnector.sol* ( [31-31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L31-L31) ):

```solidity
/// @audit Duplicated on line 50
31:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
```

- *Dolomite.sol* ( [66-66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L66-L66) ):

```solidity
/// @audit Duplicated on line 85
66:             revert IConnector_UntrustedToken(token);
```

- *PrismaConnector.sol* ( [38-38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L38-L38) ):

```solidity
/// @audit Duplicated on line 80, 108
38:                 revert IConnector_InvalidPosition(positionId);
```

- *SiloConnector.sol* ( [66-66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L66-L66) ):

```solidity
/// @audit Duplicated on line 104
66:             revert IConnector_LowHealthFactor(0);
```

- *GenericSwapAndBridgeHandler.sol* ( [100-100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L100-L100) ):

```solidity
/// @audit Duplicated on line 135
100:         if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();
```

- *LifiImplementation.sol* ( [119-119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L119-L119) ):

```solidity
/// @audit Duplicated on line 159
119:         if (receivingAmount < _request.minAmount) revert InvalidMinAmount();
```

</details>

### [N-70] Consider adding emergency-stop functionality

Adding a way to quickly halt protocol functionality in an emergency, rather than having to pause individual contracts one-by-one, will make in-progress hack mitigation faster and much less stressful.

<details>
<summary>There are 32 instances (click to show):</summary>

- *AccountingManager.sol* ( [16-16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16-L16) ):

```solidity
16: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
```

- *NoyaFeeReceiver.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7-L7) ):

```solidity
7: contract NoyaFeeReceiver is Ownable {
```

- *AaveConnector.sol* ( [11-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L11-L11) ):

```solidity
11: contract AaveConnector is BaseConnector {
```

- *AerodromeConnector.sol* ( [27-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L27-L27) ):

```solidity
27: contract AerodromeConnector is BaseConnector {
```

- *BalancerConnector.sol* ( [26-26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L26-L26) ):

```solidity
26: contract BalancerConnector is BaseConnector {
```

- *CamelotConnector.sol* ( [30-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L30-L30) ):

```solidity
30: contract CamelotConnector is BaseConnector {
```

- *CompoundConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L7-L7) ):

```solidity
7: contract CompoundConnector is BaseConnector {
```

- *CurveConnector.sol* ( [24-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L24-L24) ):

```solidity
24: contract CurveConnector is BaseConnector {
```

- *Dolomite.sol* ( [9-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9-L9) ):

```solidity
9: contract DolomiteConnector is BaseConnector {
```

- *FraxConnector.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L18-L18) ):

```solidity
18: contract FraxConnector is BaseConnector {
```

- *GearBoxV3.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8-L8) ):

```solidity
8: contract Gearboxv3 is BaseConnector {
```

- *LidoConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7-L7) ):

```solidity
7: contract LidoConnector is BaseConnector, ERC721Holder {
```

- *MaverickConnector.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29-L29) ):

```solidity
29: contract MaverickConnector is BaseConnector, IERC721Receiver {
```

- *MorphoBlueConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8-L8) ):

```solidity
8: contract MorphoBlueConnector is BaseConnector {
```

- *PancakeswapConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8-L8) ):

```solidity
8: contract PancakeswapConnector is UNIv3Connector {
```

- *PendleConnector.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12-L12) ):

```solidity
12: contract PendleConnector is BaseConnector {
```

- *PrismaConnector.sol* ( [11-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L11-L11) ):

```solidity
11: contract PrismaConnector is BaseConnector {
```

- *SNXConnector.sol* ( [7-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7-L7) ):

```solidity
7: contract SNXV3Connector is BaseConnector, IERC721Receiver {
```

- *SiloConnector.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8-L8) ):

```solidity
8: contract SiloConnector is BaseConnector {
```

- *StargateConnector.sol* ( [19-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L19-L19) ):

```solidity
19: contract StargateConnector is BaseConnector {
```

- *UNIv3Connector.sol* ( [12-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L12-L12) ):

```solidity
12: contract UNIv3Connector is BaseConnector, ERC721Holder {
```

- *Keepers.sol* ( [9-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L9-L9) ):

```solidity
9: contract Keepers is EIP712, Ownable2Step {
```

- *NoyaGovernanceBase.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L6) ):

```solidity
6: contract NoyaGovernanceBase {
```

- *TimeLock.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L6-L6) ):

```solidity
6: contract NoyaTimeLock is TimelockController {
```

- *Watchers.sol* ( [6-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L6-L6) ):

```solidity
6: contract Watchers is Keepers {
```

- *BaseConnector.sol* ( [22-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L22-L22) ):

```solidity
22: contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {
```

- *LZHelperReceiver.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L18-L18) ):

```solidity
18: contract LZHelperReceiver is OAppReceiver {
```

- *LZHelperSender.sol* ( [19-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19-L19) ):

```solidity
19: contract LZHelperSender is OAppSender {
```

- *OmnichainManagerBaseChain.sol* ( [8-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L8-L8) ):

```solidity
8: contract OmnichainManagerBaseChain is OmnichainLogic {
```

- *OmnichainManagerNormalChain.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L10-L10) ):

```solidity
10: contract OmnichainManagerNormalChain is OmnichainLogic {
```

- *GenericSwapAndBridgeHandler.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10-L10) ):

```solidity
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
```

- *LifiImplementation.sol* ( [10-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10-L10) ):

```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {
```

</details>

### [N-71] Avoid the use of sensitive terms

Use [alternative variants](https://www.zdnet.com/article/mysql-drops-master-slave-and-blacklist-whitelist-terminology/), e.g. allowlist/denylist instead of whitelist/blacklist.

<details>
<summary>There are 20 instances (click to show):</summary>

- *PancakeswapConnector.sol* ( [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L5), [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L12), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L14), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L23), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L31), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L33), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L41), [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L42), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L51), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L52) ):

```solidity
5: import "../external/interfaces/Pancakeswap/IMasterChefV3.sol";

12:     IMasterchefV3 public masterchef;

14:     event SendPositionToMasterChef(uint256 tokenId);

23:         masterchef = IMasterchefV3(MC);

31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {

32:         IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId);

33:         emit SendPositionToMasterChef(tokenId);

41:         masterchef.updateLiquidity(tokenId);

42:         _updateTokenInRegistry(masterchef.CAKE());

51:         masterchef.withdraw(tokenId, address(this));

52:         _updateTokenInRegistry(masterchef.CAKE());
```

- *LifiImplementation.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L14), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L22), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L66), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L67), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153) ):

```solidity
14:     mapping(string => bool) public isBridgeWhiteListed;

22:     event AddedBridgeBlacklist(string bridgeName, bool state);

65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {

66:         isBridgeWhiteListed[bridgeName] = state;

67:         emit AddedBridgeBlacklist(bridgeName, state);

153:         if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
```

</details>

### [N-72] Missing checks for uint state variable assignments

Consider whether reasonable bounds checks for variables would be useful.

There are 6 instances:

- *AccountingManager.sol* ( [668-668](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L668-L668), [669-669](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L669-L669), [674-674](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L674-L674), [679-679](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L679-L679) ):

```solidity
668:         depositLimitPerTransaction = _depositLimitPerTransaction;

669:         depositLimitTotalAmount = _depositTotalAmount;

674:         depositWaitingTime = _depositWaitingTime;

679:         withdrawWaitingTime = _withdrawWaitingTime;
```

- *GenericSwapAndBridgeHandler.sol* ( [58-58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L58-L58) ):

```solidity
58:         genericSlippageTolerance = _slippageTolerance;
```

- *UniswapValueOracle.sol* ( [40-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L40-L40) ):

```solidity
40:         period = _period;
```

### [N-73] Use the Modern Upgradeable Contract Paradigm

Modern smart contract development often employs upgradeable contract structures, utilizing proxy patterns like OpenZeppelin’s Upgradeable Contracts. This paradigm separates logic and state, allowing developers to amend and enhance the contract's functionality without altering its state or the deployed contract address. Transitioning to this approach enhances long-term maintainability.
Resolution: Adopt a well-established proxy pattern for upgradeability, ensuring proper initialization and employing transparent proxies to mitigate potential risks. Embrace comprehensive testing and audit practices, particularly when updating contract logic, to ensure state consistency and security are preserved across upgrades. This ensures your contract remains robust and adaptable to future requirements.

<details>
<summary>There are 39 instances (click to show):</summary>

- *AccountingManager.sol* ( [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16) ):

```solidity
16: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
```

- *NoyaFeeReceiver.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7) ):

```solidity
7: contract NoyaFeeReceiver is Ownable {
```

- *Registry.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12) ):

```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

- *AaveConnector.sol* ( [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L11) ):

```solidity
11: contract AaveConnector is BaseConnector {
```

- *AerodromeConnector.sol* ( [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L27) ):

```solidity
27: contract AerodromeConnector is BaseConnector {
```

- *BalancerConnector.sol* ( [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L26) ):

```solidity
26: contract BalancerConnector is BaseConnector {
```

- *BalancerFlashLoan.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L12) ):

```solidity
12: contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {
```

- *CamelotConnector.sol* ( [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L30) ):

```solidity
30: contract CamelotConnector is BaseConnector {
```

- *CompoundConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L7) ):

```solidity
7: contract CompoundConnector is BaseConnector {
```

- *CurveConnector.sol* ( [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L24) ):

```solidity
24: contract CurveConnector is BaseConnector {
```

- *Dolomite.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9) ):

```solidity
9: contract DolomiteConnector is BaseConnector {
```

- *FraxConnector.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L18) ):

```solidity
18: contract FraxConnector is BaseConnector {
```

- *GearBoxV3.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8) ):

```solidity
8: contract Gearboxv3 is BaseConnector {
```

- *LidoConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7) ):

```solidity
7: contract LidoConnector is BaseConnector, ERC721Holder {
```

- *MaverickConnector.sol* ( [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29) ):

```solidity
29: contract MaverickConnector is BaseConnector, IERC721Receiver {
```

- *MorphoBlueConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8) ):

```solidity
8: contract MorphoBlueConnector is BaseConnector {
```

- *PancakeswapConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8) ):

```solidity
8: contract PancakeswapConnector is UNIv3Connector {
```

- *PendleConnector.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12) ):

```solidity
12: contract PendleConnector is BaseConnector {
```

- *PrismaConnector.sol* ( [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L11) ):

```solidity
11: contract PrismaConnector is BaseConnector {
```

- *SNXConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7) ):

```solidity
7: contract SNXV3Connector is BaseConnector, IERC721Receiver {
```

- *SiloConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8) ):

```solidity
8: contract SiloConnector is BaseConnector {
```

- *StargateConnector.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L19) ):

```solidity
19: contract StargateConnector is BaseConnector {
```

- *UNIv3Connector.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L12) ):

```solidity
12: contract UNIv3Connector is BaseConnector, ERC721Holder {
```

- *Keepers.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L9) ):

```solidity
9: contract Keepers is EIP712, Ownable2Step {
```

- *NoyaGovernanceBase.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L6) ):

```solidity
6: contract NoyaGovernanceBase {
```

- *TimeLock.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L6) ):

```solidity
6: contract NoyaTimeLock is TimelockController {
```

- *Watchers.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L6) ):

```solidity
6: contract Watchers is Keepers {
```

- *BaseConnector.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L22) ):

```solidity
22: contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {
```

- *ConnectorMock2.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L14) ):

```solidity
14: contract ConnectorMock2 {
```

- *LZHelperReceiver.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L18) ):

```solidity
18: contract LZHelperReceiver is OAppReceiver {
```

- *LZHelperSender.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19) ):

```solidity
19: contract LZHelperSender is OAppSender {
```

- *OmnichainManagerBaseChain.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L8) ):

```solidity
8: contract OmnichainManagerBaseChain is OmnichainLogic {
```

- *OmnichainManagerNormalChain.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L10) ):

```solidity
10: contract OmnichainManagerNormalChain is OmnichainLogic {
```

- *GenericSwapAndBridgeHandler.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10) ):

```solidity
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
```

- *LifiImplementation.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10) ):

```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {
```

- *NoyaValueOracle.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L10) ):

```solidity
10: contract NoyaValueOracle is INoyaValueOracle {
```

- *ChainlinkOracleConnector.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L10) ):

```solidity
10: contract ChainlinkOracleConnector is INoyaValueOracle {
```

- *UniswapValueOracle.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L12) ):

```solidity
12: contract UniswapValueOracle is INoyaValueOracle {
```

- *WETH_Oracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L4) ):

```solidity
4: contract WETH_Oracle {
```

</details>

### [N-74] Large or complicated code bases should implement invariant tests

This includes: large code bases, or code with lots of inline-assembly, complicated math, or complicated interactions between multiple contracts.
Invariant fuzzers such as Echidna require the test writer to come up with invariants which should not be violated under any circumstances, and the fuzzer tests various inputs and function calls to ensure that the invariants always hold.
Even code with 100% code coverage can still have bugs due to the order of the operations a user performs, and invariant fuzzers may help significantly.

There is 1 instance:

- Global finding

### [N-75] The default value is manually set when it is declared

In instances where a new variable is defined, there is no need to set it to it's default value.

<details>
<summary>There are 60 instances (click to show):</summary>

- *AccountingManager.sol* ( [228-228](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L228-L228), [264-264](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L264-L264), [265-265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L265-L265), [330-330](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L330-L330), [331-331](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L331-L331), [332-332](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L332-L332), [400-400](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L400-L400), [403-403](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L403-L403), [404-404](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L404-L404), [549-549](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L549-L549), [551-551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551-L551), [603-603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), [608-608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608-L608) ):

```solidity
228:         uint64 i = 0;

264:         uint64 i = 0;

265:         uint256 processedBaseTokenAmount = 0;

330:         uint64 i = 0;

331:         uint256 processedShares = 0;

332:         uint256 assetsNeededForWithdraw = 0;

400:         uint64 i = 0;

403:         uint256 withdrawFeeAmount = 0;

404:         uint256 processedBaseTokenAmount = 0;

549:         uint256 amountAskedForWithdraw_temp = 0;

551:         for (uint256 i = 0; i < retrieveData.length; i++) {

603:             for (uint256 i = 0; i < items.length; i++) {

608:             for (uint256 i = 0; i < items.length; i++) {
```

- *Registry.sol* ( [138-138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138-L138), [194-194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194-L194), [214-214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214-L214), [253-253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L253-L253), [274-274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L274-L274) ):

```solidity
138:         for (uint256 i = 0; i < _trustedTokens.length; i++) {

194:         for (uint256 i = 0; i < _connectorAddresses.length; i++) {

214:         for (uint256 i = 0; i < _tokens.length; i++) {

253:             for (uint256 i = 0; i < usingTokens.length; i++) {

274:         for (uint256 i = 0; i < length; i++) {
```

- *BalancerConnector.sol* ( [54-54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54-L54), [77-77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77-L77) ):

```solidity
54:         for (uint256 i = 0; i < rewardsPools.length; i++) {

77:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *BalancerFlashLoan.sol* ( [74-74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79-79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84-84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89-89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L89) ):

```solidity
74:             for (uint256 i = 0; i < tokens.length; i++) {

79:             for (uint256 i = 0; i < destinationConnector.length; i++) {

84:             for (uint256 i = 0; i < tokens.length; i++) {

89:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *CurveConnector.sol* ( [222-222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222-L222), [234-234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234-L234), [248-248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248-L248) ):

```solidity
222:         for (uint256 i = 0; i < gauges.length; i++) {

234:         for (uint256 i = 0; i < pools.length; i++) {

248:         for (uint256 i = 0; i < rewardsPools.length; i++) {
```

- *Dolomite.sol* ( [111-111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L111-L111), [112-112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L112-L112), [113-113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L113-L113) ):

```solidity
111:         uint256 totalDebt = 0;

112:         uint256 totalCollateral = 0;

113:         for (uint256 i = 0; i < markets.length; i++) {
```

- *GearBoxV3.sol* ( [69-69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69-L69) ):

```solidity
69:         for (uint256 i = 0; i < calls.length; i++) {
```

- *MaverickConnector.sol* ( [140-140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L140-L140) ):

```solidity
140:         for (uint256 i = 0; i < earnedInfo.length; i++) {
```

- *PendleConnector.sol* ( [244-244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244), [260-260](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L260-L260) ):

```solidity
244:         for (uint256 i = 0; i < rewardTokens.length; i++) {

260:             uint256 underlyingBalance = 0;
```

- *SiloConnector.sol* ( [114-114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L114-L114), [115-115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L115-L115), [116-116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L116-L116), [132-132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L132-L132) ):

```solidity
114:         uint256 totalDepositAmount = 0;

115:         uint256 totalBAmount = 0;

116:         for (uint256 i = 0; i < assets.length; i++) {

132:         for (uint256 i = 0; i < assetsS.length; i++) {
```

- *UNIv3Connector.sol* ( [102-102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102-L102) ):

```solidity
102:         for (uint256 i = 0; i < tokenIds.length; i++) {
```

- *Keepers.sol* ( [29-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29-L29), [44-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44-L44), [103-103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L103-L103), [104-104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L104-L104) ):

```solidity
29:         for (uint256 i = 0; i < _owners.length; i++) {

44:         for (uint256 i = 0; i < _owners.length; i++) {

103:             address lastAdd = address(0);

104:             for (uint256 i = 0; i < threshold;) {
```

- *BaseConnector.sol* ( [178-178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), [189-189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189), [211-211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211-L211) ):

```solidity
178:         for (uint256 i = 0; i < tokens.length; i++) {

189:         for (uint256 i = 0; i < tokens.length; i++) {

211:         for (uint256 i = 0; i < tokensIn.length; i++) {
```

- *ConnectorMock2.sol* ( [17-17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L17-L17), [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L41-L41), [46-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L46-L46) ):

```solidity
17:     uint256 public vaultId = 0;

41:         for (uint256 i = 0; i < tokens.length; i++) {

46:         for (uint256 i = 0; i < tokens.length; i++) {
```

- *GenericSwapAndBridgeHandler.sol* ( [37-37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), [148-148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L148) ):

```solidity
37:         for (uint256 i = 0; i < usersAddresses.length; i++) {

148:         for (uint256 i = 0; i < _routes.length;) {
```

- *LifiImplementation.sol* ( [85-85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L85-L85), [92-92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L92-L92) ):

```solidity
85:         uint256 balanceOut0 = 0;

92:         uint256 balanceOut1 = 0;
```

- *TVLHelper.sol* ( [18-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L18-L18), [44-44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L44) ):

```solidity
18:         for (uint256 i = 0; i < positions.length; i++) {

44:         for (uint256 i = 0; i < positions.length; i++) {
```

- *NoyaValueOracle.sol* ( [41-41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55-55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88-88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88) ):

```solidity
41:         for (uint256 i = 0; i < baseCurrencies.length; i++) {

55:         for (uint256 i = 0; i < oracle.length; i++) {

88:         for (uint256 i = 0; i < sources.length; i++) {
```

- *ChainlinkOracleConnector.sol* ( [25-25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L25-L25), [74-74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74) ):

```solidity
25:     address public constant ETH = address(0);

74:         for (uint256 i = 0; i < assets.length; i++) {
```

</details>

### [N-76] Contracts should have all `public`/`external` functions exposed by `interface`s

All `external`/`public` functions should extend an `interface`. This is useful to ensure that the whole API is extracted and can be more easily integrated by other projects.

<details>
<summary>There are 37 instances (click to show):</summary>

- *AccountingManager.sol* ( [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16) ):

```solidity
16: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
```

- *NoyaFeeReceiver.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7) ):

```solidity
7: contract NoyaFeeReceiver is Ownable {
```

- *Registry.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12) ):

```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
```

- *AaveConnector.sol* ( [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L11) ):

```solidity
11: contract AaveConnector is BaseConnector {
```

- *AerodromeConnector.sol* ( [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L27) ):

```solidity
27: contract AerodromeConnector is BaseConnector {
```

- *BalancerConnector.sol* ( [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L26) ):

```solidity
26: contract BalancerConnector is BaseConnector {
```

- *BalancerFlashLoan.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L12) ):

```solidity
12: contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {
```

- *CamelotConnector.sol* ( [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L30) ):

```solidity
30: contract CamelotConnector is BaseConnector {
```

- *CompoundConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L7) ):

```solidity
7: contract CompoundConnector is BaseConnector {
```

- *CurveConnector.sol* ( [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L24) ):

```solidity
24: contract CurveConnector is BaseConnector {
```

- *Dolomite.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9) ):

```solidity
9: contract DolomiteConnector is BaseConnector {
```

- *FraxConnector.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L18) ):

```solidity
18: contract FraxConnector is BaseConnector {
```

- *GearBoxV3.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8) ):

```solidity
8: contract Gearboxv3 is BaseConnector {
```

- *LidoConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7) ):

```solidity
7: contract LidoConnector is BaseConnector, ERC721Holder {
```

- *MaverickConnector.sol* ( [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29) ):

```solidity
29: contract MaverickConnector is BaseConnector, IERC721Receiver {
```

- *MorphoBlueConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8) ):

```solidity
8: contract MorphoBlueConnector is BaseConnector {
```

- *PancakeswapConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8) ):

```solidity
8: contract PancakeswapConnector is UNIv3Connector {
```

- *PendleConnector.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12) ):

```solidity
12: contract PendleConnector is BaseConnector {
```

- *PrismaConnector.sol* ( [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L11) ):

```solidity
11: contract PrismaConnector is BaseConnector {
```

- *SNXConnector.sol* ( [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7) ):

```solidity
7: contract SNXV3Connector is BaseConnector, IERC721Receiver {
```

- *SiloConnector.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8) ):

```solidity
8: contract SiloConnector is BaseConnector {
```

- *StargateConnector.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L19) ):

```solidity
19: contract StargateConnector is BaseConnector {
```

- *UNIv3Connector.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L12) ):

```solidity
12: contract UNIv3Connector is BaseConnector, ERC721Holder {
```

- *Keepers.sol* ( [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L9) ):

```solidity
9: contract Keepers is EIP712, Ownable2Step {
```

- *Watchers.sol* ( [6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L6) ):

```solidity
6: contract Watchers is Keepers {
```

- *BaseConnector.sol* ( [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L22) ):

```solidity
22: contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {
```

- *ConnectorMock2.sol* ( [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L14) ):

```solidity
14: contract ConnectorMock2 {
```

- *LZHelperReceiver.sol* ( [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L18) ):

```solidity
18: contract LZHelperReceiver is OAppReceiver {
```

- *LZHelperSender.sol* ( [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19) ):

```solidity
19: contract LZHelperSender is OAppSender {
```

- *OmnichainManagerBaseChain.sol* ( [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L8) ):

```solidity
8: contract OmnichainManagerBaseChain is OmnichainLogic {
```

- *OmnichainManagerNormalChain.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L10) ):

```solidity
10: contract OmnichainManagerNormalChain is OmnichainLogic {
```

- *GenericSwapAndBridgeHandler.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10) ):

```solidity
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
```

- *LifiImplementation.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10) ):

```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {
```

- *NoyaValueOracle.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L10) ):

```solidity
10: contract NoyaValueOracle is INoyaValueOracle {
```

- *ChainlinkOracleConnector.sol* ( [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L10) ):

```solidity
10: contract ChainlinkOracleConnector is INoyaValueOracle {
```

- *UniswapValueOracle.sol* ( [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L12) ):

```solidity
12: contract UniswapValueOracle is INoyaValueOracle {
```

- *WETH_Oracle.sol* ( [4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L4) ):

```solidity
4: contract WETH_Oracle {
```

</details>

### [N-77] Top-level declarations should be separated by at least two lines

-

<details>
<summary>There are 174 instances (click to show):</summary>

- *AccountingManager.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L2-L4), [541-543](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L541-L543), [625-627](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L625-L627), [630-632](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L630-L632), [640-642](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L640-L642), [647-649](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L647-L649), [661-663](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L661-L663), [665-667](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L665-L667), [671-673](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L671-L673), [676-678](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L676-L678), [681-683](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L681-L683), [691-693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L691-L693), [695-697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L695-L697), [699-701](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L699-L701), [703-705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L703-L705) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";

541:     }
542: 
543:     function burnShares(uint256 amount) public {

625:     }
626: 
627:     function TVL() public view returns (uint256) {

630:     }
631: 
632:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {

640:     }
641: 
642:     function _getValue(address token, address base, uint256 amount) internal view returns (uint256) {

647:     }
648: 
649:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {

661:     }
662: 
663:     function unpause() public whenPaused onlyEmergency {

665:     }
666: 
667:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {

671:     }
672: 
673:     function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {

676:     }
677: 
678:     function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {

681:     }
682: 
683:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {

691:     }
692: 
693:     function mint(uint256 shares, address receiver) public override returns (uint256) {

695:     }
696: 
697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

699:     }
700: 
701:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {

703:     }
704: 
705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {
```

- *NoyaFeeReceiver.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L2-L4), [5-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L5-L7), [21-23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L21-L23), [25-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L25-L27) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import { AccountingManager } from "./AccountingManager.sol";

5: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
6: 
7: contract NoyaFeeReceiver is Ownable {

21:     }
22: 
23:     function withdrawShares(uint256 amount) external onlyOwner {

25:     }
26: 
27:     function burnShares(uint256 amount) external onlyOwner {
```

- *Registry.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L2-L4), [37-39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L37-L39), [44-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L44-L46), [51-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L51-L53), [77-79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L77-L79), [82-84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L82-L84) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/access/AccessControl.sol";

37:     }
38: 
39:     modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) {

44:     }
45: 
46:     modifier onlyVaultGoverner(uint256 _vaultId) {

51:     }
52: 
53:     modifier vaultExists(uint256 _vaultId) {

77:     }
78: 
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) {

82:     }
83: 
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {
```

- *AaveConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L2-L4), [86-88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L86-L88), [112-114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L112-L114), [118-120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L118-L120) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

86:     }
87: 
88:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager {

112:     }
113: 
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {

118:     }
119: 
120:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *AerodromeConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L2-L4), [25-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L25-L27), [98-100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L98-L100), [104-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L104-L106), [109-111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L109-L111), [115-117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L115-L117), [123-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L123-L125) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

25: }
26: 
27: contract AerodromeConnector is BaseConnector {

98:     }
99: 
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {

104:     }
105: 
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {

109:     }
110: 
111:     function claim(address pool) public onlyManager nonReentrant {

115:     }
116: 
117:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {

123:     }
124: 
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
```

- *BalancerConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L2-L4), [24-26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L24-L26), [51-53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L51-L53), [107-109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L107-L109), [113-115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L113-L115), [160-162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L160-L162), [173-175](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L173-L175), [182-184](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L182-L184), [187-189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L187-L189) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

24: }
25: 
26: contract BalancerConnector is BaseConnector {

51:     }
52: 
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

107:     }
108: 
109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {

113:     }
114: 
115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {

160:     }
161: 
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

173:     }
174: 
175:     function totalLpBalanceOf(PoolInfo memory pool) public view returns (uint256) {

182:     }
183: 
184:     function totalLpBalanceOf(bytes32 poolId) public view returns (uint256) {

187:     }
188: 
189:     function _getPoolInfo(bytes32 pooId) internal view returns (PoolInfo memory, bytes32) {
```

- *BalancerFlashLoan.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L2-L4), [10-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L10-L12) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import { IBalancerVault, IERC20 } from "../external/interfaces/Balancer/IBalancerVault.sol";

10: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
11: 
12: contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {
```

- *CamelotConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L2-L4), [28-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L28-L30), [41-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L41-L43), [86-88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L86-L88), [97-99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L97-L99) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";

28: }
29: 
30: contract CamelotConnector is BaseConnector {

41:     }
42: 
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {

86:     }
87: 
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

97:     }
98: 
99:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *CompoundConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L2-L4), [5-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L5-L7), [123-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L123-L125), [132-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L132-L134) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

5: import { IComet, IRewards } from "../external/interfaces/Compound/ICompound.sol";
6: 
7: contract CompoundConnector is BaseConnector {

123:     }
124: 
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

132:     }
133: 
134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *CurveConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L2-L4), [22-24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L22-L24) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

22: }
23: 
24: contract CurveConnector is BaseConnector {
```

- *Dolomite.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L2-L4), [7-9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L7-L9), [28-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L28-L30), [41-43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L41-L43), [56-58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L56-L58), [75-77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L75-L77), [96-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L96-L98), [104-106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L104-L106) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

7: import "../external/interfaces/Dolomite/IDolomiteMargin.sol";
8: 
9: contract DolomiteConnector is BaseConnector {

28:     }
29: 
30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

41:     }
42: 
43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

56:     }
57: 
58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)

75:     }
76: 
77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)

96:     }
97: 
98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {

104:     }
105: 
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *FraxConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L2-L4), [16-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L16-L18), [140-142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L140-L142), [148-150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L148-L150) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

16: }
17: 
18: contract FraxConnector is BaseConnector {

140:     }
141: 
142:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {

148:     }
149: 
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *GearBoxV3.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L2-L4), [6-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L6-L8) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

6: import "../external/interfaces/Gearbox/ICreditFacadeV3.sol";
7: 
8: contract Gearboxv3 is BaseConnector {
```

- *LidoConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L2-L4), [5-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L5-L7), [89-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L89-L91) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../external/interfaces/Lido/ILidoWithdrawal.sol";

5: import "../helpers/BaseConnector.sol";
6: 
7: contract LidoConnector is BaseConnector, ERC721Holder {

89:     receive() external payable { }
90: 
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
```

- *MaverickConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L2-L4), [27-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L27-L29), [147-149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L147-L149), [151-153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L151-L153), [159-161](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L159-L161) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";

27: }
28: 
29: contract MaverickConnector is BaseConnector, IERC721Receiver {

147:     }
148: 
149:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {

151:     }
152: 
153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

159:     }
160: 
161:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
```

- *MorphoBlueConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L2-L4), [6-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L6-L8), [116-118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L116-L118), [135-137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L135-L137), [139-141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L139-L141) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

6: import "../external/libraries/Morpho/SharesMathLib.sol";
7: 
8: contract MorphoBlueConnector is BaseConnector {

116:     }
117: 
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

135:     }
136: 
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {

139:     }
140: 
141:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PancakeswapConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L2-L4), [6-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L6-L8) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "./UNIv3Connector.sol";

6: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721.sol";
7: 
8: contract PancakeswapConnector is UNIv3Connector {
```

- *PendleConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L2-L4), [10-12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L10-L12), [309-311](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L309-L311) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

10: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
11: 
12: contract PendleConnector is BaseConnector {

309:     }
310: 
311:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *PrismaConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L2-L4), [9-11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L9-L11) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

9: import "../helpers/BaseConnector.sol";
10: 
11: contract PrismaConnector is BaseConnector {
```

- *SNXConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L2-L4), [5-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L5-L7), [23-25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L23-L25), [28-30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L28-L30), [44-46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L44-L46), [62-64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L62-L64), [66-68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L66-L68), [79-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L79-L81), [92-94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L92-L94), [100-102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L100-L102), [119-121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L119-L121), [126-128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L126-L128) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

5: import "../external/interfaces/SNXV3/IV3CoreProxy.sol";
6: 
7: contract SNXV3Connector is BaseConnector, IERC721Receiver {

23:     }
24: 
25:     function createAccount() public onlyManager {

28:     }
29: 
30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

44:     }
45: 
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

62:     }
63: 
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {

66:     }
67: 
68:     function delegateIntoPreferredPool(

79:     }
80: 
81:     function delegateIntoApprovedPool(

92:     }
93: 
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)

100:     }
101: 
102:     function mintOrBurnSUSD(

119:     }
120: 
121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

126:     }
127: 
128:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
```

- *SiloConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L2-L4), [6-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L6-L8), [69-71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L69-L71), [107-109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L107-L109), [128-130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L128-L130), [141-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L141-L143) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

6: import "../external/libraries/Silo/SolvencyV2.sol";
7: 
8: contract SiloConnector is BaseConnector {

69:     }
70: 
71:     function getData(address siloToken)

107:     }
108: 
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

128:     }
129: 
130:     function isSiloEmpty(ISilo silo) public view returns (bool) {

141:     }
142: 
143:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *StargateConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L2-L4), [17-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L17-L19), [121-123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L121-L123) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../helpers/BaseConnector.sol";

17: }
18: 
19: contract StargateConnector is BaseConnector {

121:     }
122: 
123:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
```

- *UNIv3Connector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L2-L4), [125-127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L125-L127), [150-152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L150-L152) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../external/interfaces/UNIv3/INonfungiblePositionManager.sol";

125:     }
126: 
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

150:     }
151: 
152:     function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
```

- *Keepers.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/utils/cryptography/EIP712.sol";
```

- *NoyaGovernanceBase.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L2-L4), [4-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L4-L6) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import { PositionRegistry, PositionBP } from "../accountingManager/Registry.sol";

4: import { PositionRegistry, PositionBP } from "../accountingManager/Registry.sol";
5: 
6: contract NoyaGovernanceBase {
```

- *TimeLock.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L2-L4), [4-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L4-L6) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/governance/TimelockController.sol";

4: import "@openzeppelin/contracts-5.0/governance/TimelockController.sol";
5: 
6: contract NoyaTimeLock is TimelockController {
```

- *Watchers.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L2-L4), [4-6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L4-L6), [7-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L7-L8) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "./Keepers.sol";

4: import "./Keepers.sol";
5: 
6: contract Watchers is Keepers {

7:     constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
8:     function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
```

- *BaseConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L2-L4), [20-22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L20-L22), [219-221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L219-L221), [251-253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L251-L253), [261-263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L261-L263), [265-267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L265-L267), [269-271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L269-L271), [283-285](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L283-L285) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../interface/IConnector.sol";

20: }
21: 
22: contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {

219:     }
220: 
221:     function _executeSwap(SwapRequest memory swapRequest) internal returns (uint256 amountOut) {

251:     }
252: 
253:     function _getValue(address token, address baseToken, uint256 amount) internal view returns (uint256) {

261:     }
262: 
263:     function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {

265:     }
266: 
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {

269:     }
270: 
271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {

283:     }
284: 
285:     function _revokeApproval(address _token, address _spender) internal virtual {
```

- *ConnectorMock2.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L2-L4), [12-14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L12-L14), [25-27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L25-L27), [38-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L38-L40), [49-51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L49-L51), [63-65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L63-L65), [69-71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L69-L71), [73-75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L73-L75), [77-79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L77-L79), [89-91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L89-L91) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

12: import { PositionRegistry } from "contracts/accountingManager/Registry.sol";
13: 
14: contract ConnectorMock2 {

25:     }
26: 
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)

38:     }
39: 
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {

49:     }
50: 
51:     function updatePositionToRegistryUsingType(bytes32 _positionId, bytes memory data, bool remove) external {

63:     }
64: 
65:     function addPositionToRegistry(bytes memory data) external {

69:     }
70: 
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

73:     }
74: 
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {

77:     }
78: 
79:     function _updateTokenInRegistry(address token, bool remove) internal {

89:     }
90: 
91:     function _updateTokenInRegistry(address token) internal {
```

- *LZHelperReceiver.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L2-L4), [16-18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L16-L18) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

16: }
17: 
18: contract LZHelperReceiver is OAppReceiver {
```

- *LZHelperSender.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L2-L4), [17-19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L17-L19), [38-40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L38-L40) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

17: }
18: 
19: contract LZHelperSender is OAppSender {

38:     }
39: 
40:     function _payNative(uint256 amount) internal override returns (uint256) {
```

- *OmnichainLogic.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../../helpers/SwapHandler/GenericSwapAndBridgeHandler.sol";
```

- *OmnichainManagerBaseChain.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L2-L4), [6-8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L6-L8) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "./OmnichainLogic.sol";

6: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
7: 
8: contract OmnichainManagerBaseChain is OmnichainLogic {
```

- *OmnichainManagerNormalChain.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L2-L4), [8-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L8-L10), [31-33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L31-L33) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";

8: import "../LZHelpers/LZHelperSender.sol";
9: 
10: contract OmnichainManagerNormalChain is OmnichainLogic {

31:     }
32: 
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {
```

- *GenericSwapAndBridgeHandler.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L2-L4), [8-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L8-L10), [27-29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L27-L29) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../../interface/valueOracle/INoyaValueOracle.sol";

8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
9: 
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {

27:     }
28: 
29:     modifier onlyExistingRoute(uint256 _routeId) {
```

- *LifiImplementation.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L2-L4), [8-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L8-L10), [163-165](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L163-L165), [183-185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L183-L185), [187-189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L187-L189), [191-193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L191-L193) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";

8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
9: 
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {

163:     }
164: 
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)

183:     }
184: 
185:     function _setAllowance(IERC20 token, address spender, uint256 amount) internal {

187:     }
188: 
189:     function _isNative(IERC20 token) internal pure returns (bool isNative) {

191:     }
192: 
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {
```

- *TVLHelper.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L2-L4), [5-7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L5-L7) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import { PositionRegistry, HoldingPI } from "../accountingManager/Registry.sol";

5: import { IConnector } from "../interface/IConnector.sol";
6: 
7: library TVLHelper {
```

- *NoyaValueOracle.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L2-L4), [59-61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L59-L61), [79-81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L79-L81), [93-95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L93-L95) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";

59:     }
60: 
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {

79:     }
80: 
81:     function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)

93:     }
94: 
95:     function _getValue(address quotingToken, address baseToken, uint256 amount) internal view returns (uint256) {
```

- *ChainlinkOracleConnector.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L2-L4), [8-10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8-L10), [141-143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L141-L143) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "../../../interface/valueOracle/INoyaValueOracle.sol";

8: import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol";
9: 
10: contract ChainlinkOracleConnector is INoyaValueOracle {

141:     }
142: 
143:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) {
```

- *UniswapValueOracle.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: import "@uniswap/v3-core/contracts/interfaces/IUniswapV3Factory.sol";
```

- *WETH_Oracle.sol* ( [2-4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L2-L4) ):

```solidity
2: pragma solidity 0.8.20;
3: 
4: contract WETH_Oracle {
```

</details>

### [N-78] Consider adding formal verification proofs

Formal verification is the act of proving or disproving the correctness of intended algorithms underlying a system with respect to a certain formal specification/property/invariant, using formal methods of mathematics.

Some tools that are currently available to perform these tests on smart contracts are [SMTChecker](https://docs.soliditylang.org/en/latest/smtchecker.html) and [Certora Prover](https://www.certora.com/).

<details>
<summary>There are 41 instances (click to show):</summary>

- [*AccountingManager.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol)

- [*NoyaFeeReceiver.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol)

- [*Registry.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol)

- [*AaveConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol)

- [*AerodromeConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol)

- [*BalancerConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol)

- [*BalancerFlashLoan.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol)

- [*CamelotConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol)

- [*CompoundConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol)

- [*CurveConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol)

- [*Dolomite.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol)

- [*FraxConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol)

- [*GearBoxV3.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol)

- [*LidoConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol)

- [*MaverickConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol)

- [*MorphoBlueConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol)

- [*PancakeswapConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol)

- [*PendleConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol)

- [*PrismaConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol)

- [*SNXConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol)

- [*SiloConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol)

- [*StargateConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol)

- [*UNIv3Connector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol)

- [*Keepers.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol)

- [*NoyaGovernanceBase.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol)

- [*TimeLock.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol)

- [*Watchers.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol)

- [*BaseConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol)

- [*ConnectorMock2.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol)

- [*LZHelperReceiver.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol)

- [*LZHelperSender.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol)

- [*OmnichainLogic.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol)

- [*OmnichainManagerBaseChain.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol)

- [*OmnichainManagerNormalChain.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol)

- [*GenericSwapAndBridgeHandler.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

- [*LifiImplementation.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)

- [*TVLHelper.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol)

- [*NoyaValueOracle.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol)

- [*ChainlinkOracleConnector.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol)

- [*UniswapValueOracle.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)

- [*WETH_Oracle.sol*](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol)

</details>

### [N-79] Use scopes sparingly

The use of scoped blocks, denoted by `{}` without a preceding control structure like `if`, `for`, etc., allows for the creation of isolated scopes within a function. While this can be useful for managing memory and preventing naming conflicts, it should be used sparingly. Excessive use of these scope blocks can obscure the code's logic flow and make it more difficult to understand, impeding code maintainability. As a best practice, only employ scoped blocks when necessary for memory management or to avoid clear naming conflicts. Otherwise, aim for clarity and simplicity in your code structure for optimal readability and maintainability.

<details>
<summary>There are 7 instances (click to show):</summary>

- *AccountingManager.sol* ( [422-423](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L422-L423) ):

```solidity
422:             {
423:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
```

- *Registry.sol* ( [249-250](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L249-L250) ):

```solidity
249:         {
250:             if (vault.trustedPositionsBP[positionId].isEnabled) revert AlreadyExists();
```

- *BalancerConnector.sol* ( [72-73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L72-L73), [124-125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L124-L125) ):

```solidity
72:         {
73:             (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(poolId);

124:             {
125:                 (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(p.poolId);
```

- *MaverickConnector.sol* ( [97-98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L97-L98) ):

```solidity
97:         {
98:             (tokenId,,,) = IMaverickRouter(maverickRouter).addLiquidityToPool{ value: sendEthAmount }(
```

- *UNIv3Connector.sol* ( [134-135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L134-L135) ):

```solidity
134:         {
135:             IUniswapV3Pool pool = IUniswapV3Pool(factory.getPool(token0, token1, fee));
```

- *Keepers.sol* ( [99-100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L99-L100) ):

```solidity
99:         {
100:             bytes32 txInputHash =
```

</details>
