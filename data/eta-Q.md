# [01]  Notice mistakes and mismatches: [withdrawWaitingTime](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L83C1-L83C109), [_performanceFeeReceiver and managementFeeReceiver](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L133C1-L134C157)
## Notice mistakes
[AccountingManager.sol#L83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L83C1-L83C109)

```solidity
83: -    /// @notice depositWaitingTime is the time that the withdraw should wait for execution after calculation
    +    /// @notice withdrawWaitingTime is the time that the withdraw should wait for execution after calculation
```
## Notice mismatch
No check that _performanceFeeReceiver and _managementFeeReceiver are different addresses as mentioned in [notice](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L133C1-L134C157).
[AccountingManager.sol#L133-134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L133C1-L134C157).

```solidity
133: @--->  /// @param _performanceFeeReceiver is the address that the performance fee is sent to (this should be the NoyaFeeReceiver contract address)
134: @--->  /// @param _managementFeeReceiver is the address that the management fee is sent to(this should be another instance of NoyaFeeReceiver contract address)
135    function setFeeReceivers(
136        address _withdrawFeeReceiver,
137        address _performanceFeeReceiver,
138        address _managementFeeReceiver
139   ) public onlyMaintainer {
140        require(_withdrawFeeReceiver != address(0));
141        require(_performanceFeeReceiver != address(0));
142        require(_managementFeeReceiver != address(0));
+          require(_performanceFeeReceiver != _managementFeeReceiver);
143        withdrawFeeReceiver = _withdrawFeeReceiver;
144        performanceFeeReceiver = _performanceFeeReceiver;
145        managementFeeReceiver = _managementFeeReceiver;
146        emit FeeRecepientsChanged( _withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver );

```