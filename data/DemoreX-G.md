# [GAS-01] Unnecessary if statements and function calls at fulFillCurrentWithdraw() function 

Function: [fulFillCurrentWithdraw()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L370C1-L390C6)

## Description

```available_Assets``` information is already acknowledged after ```neededAssetsForWithdraw()``` function but it calculates that again in order to use in the function later. Also ```availableAssets >= currentWithdrawGroup.totalCBAmount``` information is already acknowledged. In revised version, execution flow is exactly same with less costly process.

### Revised Version: 

```solidity
function fulfillCurrentWithdrawGroupV2() public onlyManager nonReentrant whenNotPaused {
        require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
        uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
        if ( availableAssets >= currentWithdrawGroup.totalCBAmount ) {
            currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;
        } else{
            if (amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount){
                revert NoyaAccounting_NOT_READY_TO_FULFILL();
            }
            currentWithdrawGroup.totalABAmount = availableAssets;
        }
        currentWithdrawGroup.isFullfilled = true;
        amountAskedForWithdraw = 0;
        currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;
        currentWithdrawGroup.totalCBAmount = 0;
        emit WithdrawGroupFulfilled(
            currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount
        );
}
```

### Original Version:

```
function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
        require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
        uint256 neededAssets = neededAssetsForWithdraw();

        if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {
            revert NoyaAccounting_NOT_READY_TO_FULFILL();
        }
        currentWithdrawGroup.isFullfilled = true;
        amountAskedForWithdraw = 0;
        uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
        if (availableAssets >= currentWithdrawGroup.totalCBAmount) {
            currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;
        } else {
            currentWithdrawGroup.totalABAmount = availableAssets;
        }
        currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;
        currentWithdrawGroup.totalCBAmount = 0;
        emit WithdrawGroupFulfilled(
            currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount
        );
}
```

## Gas Report

```terminal
| Function Name                                                                | min             | avg    | median | max    | calls
| fulfillCurrentWithdrawGroup                                                  | 118497          | 118497 | 118497 | 118497 | 1       |
| fulfillCurrentWithdrawGroupV2                                                | 115923          | 115923 | 115923 | 115923 | 1       |
```

## 2574 Gas saved



