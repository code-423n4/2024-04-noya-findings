## Remove the `onlyOwner` modifier

## vulnerability Details

* In the `NoyaFeeReceiver.sol` contract, the functions `withdrawShares() and burnShares()` do not require access modifier controls. This is because these functions merely call the corresponding public functions `withdraw() and burnShares()` in another contract, `AccountingManager.sol`.

* Since these functions in `AccountingManager.sol` are public and can be accessed by anyone, adding access modifiers to the `withdraw() and burnShares()` functions in `NoyaFeeReceiver.sol` is unnecessary


```
# NoyaFeeReceiver.sol


 - function withdrawShares(uint256 amount) external onlyOwner {
 + function withdrawShares(uint256 amount) external {
      AccountingManager(accountingManager).withdraw(amount, receiver);
    }




 -   function burnShares(uint256 amount) external onlyOwner {
 +   function burnShares(uint256 amount) external {
      AccountingManager(accountingManager).burnShares(amount);
    }

```

```

# AccountingManager.sol


function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {
...
}


function burnShares(uint256 amount) public {
...
}

```


https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L543C1-L544C1

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L304
