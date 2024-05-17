### Low-01 Strategy manager might get the performance fee even though profit dropped. 
**Instances(1)**
In AccountingManager.sol, performance fee is only intended to be awarded when there's a profit increase. Current mechanism is whenever there is a profit increase `getProfit()` >= totalProfitCalculated, the manager role would call `recordProfitForFee()` and the performance fee is recorded in `performanceFeeSharesWaitingForDistribution`. 
```solidity
    function recordProfitForFee() public onlyManager nonReentrant {
        storedProfitForFee = getProfit();
        profitStoredTime = block.timestamp;

        if (storedProfitForFee < totalProfitCalculated) {
            return;
        }

|>      preformanceFeeSharesWaitingForDistribution =
            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);
        emit RecordProfit(
            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
        );
    }
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L483)

And whenever there is a profit drop, someone /any can call `checkIfTVLHasDroped()`, such that `performanceFeeSharesWaitingForDistribution` will be cleared to 0. 
```solidity
    function checkIfTVLHasDroped() public nonReentrant {
        uint256 currentProfit = getProfit();
        if (currentProfit < storedProfitForFee) {
            emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
|>          preformanceFeeSharesWaitingForDistribution = 0;
            profitStoredTime = 0;
        }
    }
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L497)

The problem is there is no ensuring that `checkIfTVLHasDroped()` will be called in time or at all by anyone to clear recorded performance fee. The impact is that performance fee can be awarded even though there is a profit drop, which unfairly deflates users' share value.

Recommendations:
Considering make `checkIfTVLHasDroped()` as a hook everytime [TVL()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L628) is called, so that performance fee can be updated automatically in various flows.

### Low-02 In the multisig Keepers.sol, any tx that has more than required number of signatures will revert due to vulnerable signature threshold checks.
**Instances(1)**
In Keepers::execute, the signature threshold check is vulnerable and will revert execution if more than the required number of signatures are passed.
```solidity
//contracts/governance/Keepers.sol
    function execute(
    ...
|>       require(sigR.length == threshold, "Not enough signatures");
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L96)

Recommendations:
Change the check `sigR.length >= threshold`.

### Low-03 Keepers cannot execute any external calls that require `msg.value`.
**Instances(1)**
In Keepers::execute, if signature threshold is met, any external call can be executed through a low-level call. However, current implementation will prevent any msg.value to be sent over the call, disabling the ability for keeprs to call a payable external method.
```solidity
//contracts/governance/Keepers.sol
    function execute(
        address destination,
        bytes calldata data,
        uint256 gasLimit,
        address executor,
        bytes32[] memory sigR,
        bytes32[] memory sigS,
        uint8[] memory sigV,
        uint256 deadline
    ) public {
...
|>      (bool success,) = destination.call{ gas: gasLimit }(data);
        require(success, "Transaction execution reverted.");
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L116)

Recommendations:
In destination.call, add msg.value options to enable calling a payable method with native ETH.
 
