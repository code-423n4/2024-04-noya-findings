## Impact
`LZHelperSender::updateTVL()`missing event sending
```js
    function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
        if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();


        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
        bytes memory data = abi.encode(vaultId, tvl, updateTime);
@>        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
    }
```
## Proof of Concept
## Tools Used
Manual Review
## Recommended Mitigation Steps
Add event sending code