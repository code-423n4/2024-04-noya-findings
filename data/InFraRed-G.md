Gas Optimization in loop for function 'calculateDepositShares'.

Consider optimizing the loop to reduce gas consumption. 

**Suggested Code**

```
function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
    uint256 middleTemp = depositQueue.middle;
    uint64 i = 0;

    uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
    uint256 last = depositQueue.last;

    while (middleTemp < last && i < maxIterations) {
        DepositRequest storage data = depositQueue.queue[middleTemp];
        if (data.recordTime <= oldestUpdateTime) {
            uint256 shares = previewDeposit(data.amount);
            data.shares = shares;
            data.calculationTime = block.timestamp;
            emit CalculateDeposit(
                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
            );
        }
        middleTemp++;
        i++;
    }

    depositQueue.middle = middleTemp;
}
```
Here, I tried to minimize the number of iterations and avoid unnecessary calculations within the loop.