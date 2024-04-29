## [L-01] `block.timestamp` manipulation

### Description

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L528

The vulnerability arises from the reliance on `block.timestamp` for time-based checks within the `collectPerformanceFees() ` function. Specifically, the function contains conditional statements that check the time difference between the current block's timestamp and a stored timestamp (profitStoredTime). These checks are intended to enforce specific time constraints for the execution of the fee collection process.
However, the vulnerability lies in the fact that miners can potentially manipulate the `block.timestamp` value to bypass these time-based checks. By artificially adjusting the timestamp of the block they are mining, miners can influence the outcome of the conditional statements and potentially trigger the execution of the fee collection process at an unintended time.

### Code Snippet
```solidity
function collectPerformanceFees() public onlyManager nonReentrant {
        if (
            preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours
                || block.timestamp - profitStoredTime > 48 hours // @audit Miners can exploit block.timestamp check
        ) {
            return;
        }

        _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);

        totalProfitCalculated = storedProfitForFee;

        emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);

        preformanceFeeSharesWaitingForDistribution = 0;
    }
```

### Remediation

To mitigate the vulnerability and enhance the robustness of the fee collection mechanism, the following recommendations are proposed:
- **Avoid Reliance Solely** on `block.timestamp`: Instead of relying solely on `block.timestamp` for time-based checks, consider implementing additional mechanisms for time verification, such as block confirmations or external time oracles.
- **Use Relative Time Intervals**: Rather than comparing absolute timestamp values, consider using relative time intervals (e.g., block durations) to determine the eligibility for fee collection. This approach can reduce the susceptibility to timestamp manipulation.
- **Implement Auditable Time Verification**: Introduce mechanisms for auditing and verifying the timing of fee collection actions to detect and mitigate any instances of manipulation or irregularities.






