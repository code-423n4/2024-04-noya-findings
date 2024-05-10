https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L348

 function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
        uint256 middleTemp = withdrawQueue.middle;
        uint64 i = 0;
        uint256 processedShares = 0;
        uint256 assetsNeededForWithdraw = 0;
        uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);

        if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {
            revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
        }
        while (
            withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
                && i < maxIterations
        ) {
            i += 1;
            WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
            uint256 assets = previewRedeem(data.shares);
            data.amount = assets;
            data.calculationTime = block.timestamp;
            assetsNeededForWithdraw += assets;
            processedShares += data.shares;
            emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);

            middleTemp += 1;
        }
        currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
        withdrawQueue.middle = middleTemp;
    }

"processedShares" is calculated, but never been used.