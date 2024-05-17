**Proof of Concept:**

**Tool used**

- Manual review

**Recommended Mitigation:**

Refactor `checkIfTVLHasDroped` event emission code block as follows:

```diff
-   emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
+   emit ResetFee(storedProfitForFee, currentProfit, block.timestamp);
```

## [QA] Informational Findings on AavConnector.sol

### [QA-1]: Lack of Maximum Supply Amount Check

**Description:**
The `AaveConnector::supply` function does not include a check for the maximum amount to be supplied. This could lead to potential issues if excessively large amounts are supplied, potentially causing overflow or other unintended consequences.

**Impact:**
Without a maximum amount check, the contract could be exposed to risks such as excessive gas consumption or other limitations of the underlying protocols.

**Recommended Mitigation:**
Introduce a maximum supply amount check to ensure that the supplied amount does not exceed a predefined limit.

```solidity
function supply(
    address supplyToken,
    uint256 amount
) external onlyManager nonReentrant {
    require(amount <= MAX_SUPPLY_AMOUNT, "Supply amount exceeds maximum limit");
    _approveOperations(supplyToken, pool, amount);
    IPool(pool).supply(supplyToken, amount, address(this), 0);
    _updateTokenInRegistry(supplyToken);
    emit Supply(supplyToken, amount);
}
```

### [QA-2]: Adherence to the Checks-Effects-Interactions (CEI) Pattern

**Description:**
This report analyzes the `AaveConnector::supply`, `AaveConnector::borrow`, and `AaveConnector::repay` functions for adherence to the Checks-Effects-Interactions (CEI) pattern. The functions initially violate this pattern by performing state updates after external calls. This report details the necessary corrections, ensuring all state changes occur before any external interactions, thereby enhancing the contract's security and robustness.

**Impact:**
Although the functions use a non-reentrancy guard, which mitigates the risk of reentrancy attacks, strictly following the CEI pattern is still important for coding best practices and security standards. Adhering to the CEI pattern ensures a clear and structured approach to function execution, enhancing readability, maintainability, and robustness against potential vulnerabilities.

**Proof of Concept:**

<details>
<summary>Code</summary>

```solidity
function supply(
    address supplyToken,
    uint256 amount
) external onlyManager nonReentrant {
    _approveOperations(supplyToken, pool, amount);
    IPool(pool).supply(supplyToken, amount, address(this), 0);
    registry.updateHoldingPosition(
        vaultId,
        registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""),
        "",
        "",
        false
    );
    _updateTokenInRegistry(supplyToken);
    emit Supply(supplyToken, amount);
}

function borrow(
    uint256 _amount,
    uint256 _interestRateMode,
    address _borrowAsset
) external onlyManager nonReentrant {
    if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {
        revert IConnector_UntrustedToken(_borrowAsset);
    }
    IPool(pool).borrow(
        _borrowAsset,
        _amount,
        _interestRateMode,
        0,
        address(this)
    );
    (, , , , , uint256 healthFactor) = IPool(pool).getUserAccountData(
        address(this)
    );
    if (healthFactor < minimumHealthFactor)
        revert IConnector_LowHealthFactor(healthFactor);
    _updateTokenInRegistry(_borrowAsset);
    emit Borrow(_borrowAsset, _amount);
}

function repay(
    address asset,
    uint256 amount,
    uint256 i
) external onlyManager nonReentrant {
    _approveOperations(asset, pool, amount);
    IPool(pool).repay(asset, amount, i, address(this));
    _updateTokenInRegistry(asset);
    emit Repay(asset, amount, i);
}
```
</details>

**Recommended Mitigation:**

Refactor the functions to ensure state changes are made before any external calls, adhering to the CEI pattern:

#### Corrected `supply` Function

```diff
function supply(
    address supplyToken,
    uint256 amount
) external onlyManager nonReentrant {
    require(amount <= MAX_SUPPLY_AMOUNT, "Supply amount exceeds maximum limit");
    _approveOperations(supplyToken, pool, amount);
+   _updateTokenInRegistry(supplyToken);
    IPool(pool).supply(supplyToken, amount, address(this), 0);
    registry.updateHoldingPosition(
        vaultId,
        registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""),
        "",
        "",
        false
    );
-   _updateTokenInRegistry(supplyToken);
    emit Supply(supplyToken, amount);
}
```

#### Corrected `borrow` Function

```diff
function borrow(
    uint256 _amount,
    uint256 _interestRateMode,
    address _borrowAsset
) external onlyManager nonReentrant {
    if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {
        revert IConnector_UntrustedToken(_borrowAsset);
    }
+   _updateTokenInRegistry(_borrowAsset);
    IPool(pool).borrow(
        _borrowAsset,
        _amount,
        _interestRateMode,
        0,
        address(this)
    );
    (, , , , , uint256 healthFactor) = IPool(pool).getUserAccountData(
        address(this)
    );
    if (healthFactor < minimumHealthFactor)
        revert IConnector_LowHealthFactor(healthFactor);
-   _updateTokenInRegistry(_borrowAsset);
    emit Borrow(_borrowAsset, _amount);
}
```

#### Corrected `repay` Function

```diff
function repay(
    address asset,
    uint256 amount,
    uint256 i
) external onlyManager nonReentrant {
    _approveOperations(asset, pool, amount);
+   _updateTokenInRegistry(asset);
    IPool(pool).repay(asset, amount, i, address(this));
-   _updateTokenInRegistry(asset);
    emit Repay(asset, amount, i);
}
```
## [QA] Informational Findings on StargateConnector.sol
### 1. `SNXConnector::withdraw`

**Description:**
The withdraw function allows the manager to withdraw a specified amount of a token from the SNXCoreProxy under a given account ID. The function lacks proper input validations and a reentrancy guard, making it vulnerable to potential attacks.

**Recommended Mitigation:**
Add input validations at the beginning, move state updates before external calls, and add a reentrancy guard.

```solidity
function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager nonReentrant {
    // Checks
    require(_amount > 0, "Amount must be greater than zero");
    require(_token != address(0), "Invalid token address");

    // Effects
    _approveOperations(_token, address(SNXCoreProxy), _amount);
    _updateTokenInRegistry(_token);

    // Interactions
    SNXCoreProxy.withdraw(_accountId, _token, _amount);
    (uint256 c,,) = SNXCoreProxy.getAccountCollateral(_accountId, _token);
    if (c == 0) {
        registry.updateHoldingPosition(
            vaultId,
            registry.calculatePositionId(address(this), SNX_POSITION_ID, ""),
            abi.encode(_accountId, _token),
            "",
            true
        );
    }
}
```

### 2. `SNXConnector::claimRewards`

**Description:**
The claimRewards function allows the manager to claim rewards from the SNXCoreProxy for a given account ID and pool ID, using a specified collateral type and distributor. The function lacks explicit checks for preconditions or input validations and a reentrancy guard.

**Recommended Mitigation:**
Add input validations and checks at the beginning, ensure state updates occur before external calls, and include a non-reentrancy guard.

```solidity
function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
    public
    onlyManager
    nonReentrant
{
    // Checks
    require(collateralType != address(0), "Invalid collateral type");
    require(distributor != address(0), "Invalid distributor address");

    // Effects
    _updateTokenInRegistry(collateralType);

    // Interactions
    SNXCoreProxy.claimRewards(accountId, poolId, collateralType, distributor);
}
```

### Summary

By incorporating these changes:

- **Withdraw Function:**
  - Added input validation checks.
  - Moved state updates before external calls.
  - Included a non-reentrancy guard.

- **ClaimRewards Function:**
  - Added input validation checks.
  - Moved state updates before external calls.
  - Included a non-reentrancy guard.

These modifications ensure adherence to the CEI pattern, enhancing the security and robustness of the smart contract functions


## [QA] Informational Findings on StargateConnector.sol

### [QA-1] TITLE: Adherence to the Checks-Effects-Interactions (CEI) Pattern

**Description:**
This report analyzes the `StargateConnector::claimStargateRewards` function for adherence to the Checks-Effects-Interactions pattern. Initially, the function updated the state after an external call, violating the CEI pattern. This report details the necessary corrections to ensure all state changes occur before any external interactions, enhancing the contract's security and robustness.

**Impact:**
Although the `StargateConnector::claimStargateRewards` function uses a non-reentrancy guard to mitigate the risk of reentrancy attacks, strictly following the CEI pattern is essential for coding best practices and ethical standards. Adhering to the CEI pattern ensures a clear and structured approach to function execution, enhancing readability, maintainability, and security. It also reinforces the function's robustness against potential vulnerabilities. Therefore, even with the non-reentrancy guard in place, following the CEI pattern is a prudent practice that upholds high standards of smart contract development.

**Proof of Concept:**

<details>
<summary>Code</summary>

```javascript
function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {
    // Effects
    _updateTokenInRegistry(rewardToken);

    // Interactions
    LPStaking.deposit(poolId, 0);

    // Emit event
    emit ClaimStargateRewards(poolId);
}
```
</details>

**Recommended Mitigation:**
The call to `LPStaking.deposit()` happens before the internal call to `_updateTokenInRegistry`, which is a state change. To strictly follow the CEI pattern, all state changes should be made before calling external contracts. Let’s correct the function to adhere to the CEI pattern:

```solidity
function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {
    // Effects
    _updateTokenInRegistry(rewardToken);

    // Interactions
    LPStaking.deposit(poolId, 0);

    // Emit event
    emit ClaimStargateRewards(poolId);
}
```

By moving the state update `_updateTokenInRegistry(rewardToken)` before the external interaction with `LPStaking.deposit`, we ensure that all state changes occur before any external calls, adhering strictly to the CEI pattern. This enhances the security and robustness of the `claimStargateRewards` function.


```markdown
## [QA-2] TITLE: Absence of NatSpec Documentation for addLiquidityInCamelotPool Function in CamelotConnector Contract

**Description:**
The CamelotConnector contract facilitates liquidity operations within the Camelot protocol, specifically through functions such as `addLiquidityInCamelotPool`. NatSpec (Ethereum Natural Language Specification Format) is a documentation standard used in Solidity to describe the functionality of code in a way that is easy for both developers and end-users to understand. The current implementation of the addLiquidityInCamelotPool function lacks NatSpec comments, which are crucial for providing clear, concise documentation directly within the code.

**Impact:**
The absence of NatSpec documentation in the `addLiquidityInCamelotPool` function has several notable impacts:

- **Reduced Code Understandability:** Developers and auditors may find it challenging to quickly grasp the purpose and mechanics of the function without detailed comments.
- **Increased Onboarding Time:** New team members or contributors may require additional time and resources to understand the codebase, slowing down development and collaboration.
- **Poor User Documentation:** End-users and integrators may lack essential information needed to interact with the contract effectively, potentially leading to misuse or errors.
- **Difficulty in Maintenance:** Lack of documentation can lead to maintenance challenges, as future modifications may be made without a full understanding of the original intent and functionality.

**Recommended Mitigation:**
To mitigate these issues, it is recommended to add comprehensive NatSpec documentation to the `addLiquidityInCamelotPool` function. This documentation should include descriptions of the function’s purpose, parameters, and any relevant details about its behavior and requirements.

**Example Mitigation:**

```solidity
/**
 * @notice Adds liquidity to a Camelot pool using the specified parameters.
 * @dev This function approves the token transfers and interacts with the Camelot router to add liquidity.
 * @param p The parameters for adding liquidity, encapsulated in a CamelotAddLiquidityParams struct.
 * - tokenA: The address of the first token.
 * - tokenB: The address of the second token.
 * - amountA: The amount of tokenA to add.
 * - amountB: The amount of tokenB to add.
 * - minAmountA: The minimum amount of tokenA expected to add.
 * - minAmountB: The minimum amount of tokenB expected to add.
 * - deadline: The timestamp by which the transaction must be completed.
 * Emits a {LiquidityAdded} event.
 */
function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {
    _approveOperations(p.tokenA, address(router), p.amountA);
    _approveOperations(p.tokenB, address(router), p.amountB);
    router.addLiquidity(
        p.tokenA, p.tokenB, p.amountA, p.amountB, p.minAmountA, p.minAmountB, address(this), p.deadline
    );
    _updateTokenInRegistry(p.tokenA);
    _updateTokenInRegistry(p.tokenB);
    registry.updateHoldingPosition(
        vaultId,
        registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),
        "",
        "",
        false
    );
    emit LiquidityAdded(msg.sender, p.tokenA, p.tokenB, p.amountA, p.amountB, p.minAmountA, p.minAmountB, p.deadline);
}
```

Adding NatSpec documentation to the `addLiquidityInCamelotPool` function will significantly enhance the readability, maintainability, and usability of the CamelotConnector contract. This improvement ensures that developers, auditors, and end-users can easily understand and interact with the function, fostering better development practices and reducing potential for errors or misunderstandings.

By implementing the recommended NatSpec comments, the contract will align with best practices for Solidity development, providing clear and helpful documentation directly within the code.
```
## [QA] Informational Findings on LZHelperSender.sol

## [QA-1] : Use Ownable2Step instead of Ownable; https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L4
## [QA-2] : Change lzChainId to normalchainId; https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L10C12-L10C21
# INFORMATIONAL REPORT

## [QA]: Informational Findings on NoyaFeeReceiver.sol

### Description:
The NoyaFeeReceiver contract currently uses the OpenZeppelin Ownable contract for managing ownership. However, it is recommended to use the Ownable2Step contract instead of Ownable.

### Impact:
This issue is not a security vulnerability, but it is an important improvement for the following reasons:

- **Risk of Ownership Loss:** The OpenZeppelin Ownable contract can lead to the loss of contract ownership if ownership is transferred to a non-existent or incorrect address. This could happen due to a typo or other mistake when specifying the new owner's address.
- **Ownership Confirmation:** The Ownable2Step contract requires the new owner to confirm ownership, providing an additional layer of security. This ensures that ownership is not accidentally transferred to a mistyped address.

### Recommended Mitigation:
Replace the use of Ownable with Ownable2Step to enhance the security and robustness of the ownership transfer process. This change ensures that the new owner must explicitly accept the ownership transfer, reducing the risk of accidental loss of ownership.

### Example Mitigation:

1. **Update Import Statement:**
   Update the import statement to use Ownable2Step instead of Ownable.

```solidity
import "@openzeppelin/contracts/access/Ownable2Step.sol";
```

2. **Replace Ownable with Ownable2Step:**
   Replace the inheritance of Ownable with Ownable2Step in the NoyaFeeReceiver contract.

```solidity
// Current code
contract NoyaFeeReceiver is Ownable {
    // contract code...
}

// Updated code
contract NoyaFeeReceiver is Ownable2Step {
    // contract code...
}
```

By implementing Ownable2Step, the NoyaFeeReceiver contract will benefit from enhanced security in the ownership transfer process, reducing the risk of accidentally losing ownership of the contract.

This small but significant improvement aligns the contract with best practices for Solidity development, providing better safeguards for ownership management.