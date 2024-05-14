
# L. When calling updateHoldingPosition in the closeBorrowPosition, `removePosition` should be false.
[closeBorrowPosition](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/Dolomite.sol#L102)
```solidity
function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
        // repay
        borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds);
        registry.updateHoldingPosition(
            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true // @audit false?
        );
    }
```