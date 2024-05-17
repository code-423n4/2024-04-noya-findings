## 1. Redundant check in `rescue` function for `ETH`

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691

### Impact
Rescue function holds a check for address(0) token, i.e ETH. But the contract holds no payable or receive function and has no way to receive ETH, making the check redundant.

```solidity
    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { //only emergency manager
        if (token == address(0)) {
            (bool success,) = payable(msg.sender).call{ value: amount }(""); 
            require(success, "Transfer failed.");
        } else {
            IERC20(token).safeTransfer(msg.sender, amount); 
        }
        emit Rescue(msg.sender, token, amount);
    }
```

### Recommended Mitigation Steps
Consider removing the check, or introducing receive() payable function

***

## 2. Introduce a check that token being withdrawn is not `baseToken`

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691

### Impact

The rescue function prevent the withdrawer from withdrawing the baseToken, which can be used maliciously to drain the contract. Should introduce balance checks incase the basetoken is one with multiple addresses.


```solidity
    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { 
        if (token == address(0)) {
            (bool success,) = payable(msg.sender).call{ value: amount }(""); 
            require(success, "Transfer failed.");
        } else {
            IERC20(token).safeTransfer(msg.sender, amount); 
        }
        emit Rescue(msg.sender, token, amount);
    }
```