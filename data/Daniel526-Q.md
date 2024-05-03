## A. Lack of Sanity Checks for Receiver Address in Deposit and Withdraw Functions
[AccountingManager.sol#L200-L219](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L200-L219)
[AccountingManager.sol#L304-L316](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L304-L316)
The `deposit` and `withdraw` functions in the provided contract lack explicit sanity checks for the `receiver` address. In both functions, the `receiver` address parameter is accepted without validation, relying solely on external token transfer functions (`baseToken.safeTransferFrom` and `baseToken.safeTransfer`) to handle the transfer process. While these external functions may include checks for address validity, the contract itself does not enforce any validation logic. Here's an excerpt from the relevant functions:

```solidity
function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {
    // Receiver address accepted without explicit validation
    baseToken.safeTransferFrom(msg.sender, address(this), amount);
    // Other deposit logic...
}

function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {
    // Receiver address accepted without explicit validation
    // Withdraw request recorded without validation
    withdrawRequestsByAddress[msg.sender] += share;
    // Other withdrawal logic...
}

```
### Impact:
The lack of explicit validation for the receiver address could potentially lead to unintended behavior or exploitation. If an invalid or malicious receiver address is provided, it could result in tokens being transferred to unintended destinations or lost irretrievably.
### Mitigation:
Implement explicit sanity checks for the receiver address in both the deposit and withdraw functions. This can be achieved by adding simple validations such as ensuring that the receiver address is not the zero address (address(0)) or verifying that it is a valid Ethereum address. 
