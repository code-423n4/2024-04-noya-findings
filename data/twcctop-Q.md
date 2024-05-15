## L1  `burnSahres`  cna replace with tansfer 0 address

https://github.com/code-423n4/2024-04-noya/blob/cc3854f634a72bd4a8b597021887088ca2d6d29f/contracts/accountingManager/AccountingManager.sol#L607

 we have  `burnShares` function that  allow user to burn shares ,  it can be replaced with `transfer` to 0 address.
since the transfer function is public, think delete this function.

```solidity
   function burnShares(uint256 amount) public {
@>        _burn(msg.sender, amount);
    }


```




## L2  `getQueueItems` possible revert if items length too long

https://github.com/code-423n4/2024-04-noya/blob/cc3854f634a72bd4a8b597021887088ca2d6d29f/contracts/accountingManager/AccountingManager.sol#L604


once items.length > deposit queue length, `getQueueItems` is possible revert

```solidity 
        function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
        public
        view
        returns (DepositRequest[] memory depositData, WithdrawRequest[] memory withdrawData)
    {
        if (depositOrWithdraw) {
            depositData = new DepositRequest[](items.length);
            for (uint256 i = 0; i < items.length; i++) {
@>                depositData[i] = depositQueue.queue[items[i]];
            }

```
