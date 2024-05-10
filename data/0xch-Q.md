The event `ManagementFeeReceived` in `NoyaFeeReceiver` with parameters (address token, uint256 amount) is declared within the smart contract but is not currently utilized in any of the contract's functions. It is advisable to remove or implement this event to align with the contract's intended functionality and to maintain code cleanliness.
``` solidity
    event ManagementFeeReceived(address indexed token, uint256 amount);
```

The `updateHoldingPosition` in `Registry.sol:` function in the contract emits an event before updating the state, which goes against the recommended checks-effects-interactions pattern. This pattern suggests that events should be emitted after all state changes have occurred to ensure that the event log accurately reflects the completed action, and to prevent reentrancy attacks or other state inconsistencies.

```
 function updateHoldingPosition(
        Vault storage vault,
        uint256 vaultId,
        bytes32 _positionId,
        bytes calldata d,
        bytes calldata AD,
        uint256 index,
        bytes32 holdingPositionId
    ) internal returns (uint256) {
        emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index);

        if (index == 0) {
            if (!isPositionTrustedForConnector(vaultId, _positionId, msg.sender)) {
                revert InvalidPosition(_positionId);
            }
            if (vault.holdingPositions.length >= maxNumHoldingPositions) {
                revert TooManyPositions();
            }
            vault.isPositionUsed[holdingPositionId] = vault.holdingPositions.length;
            vault.holdingPositions.push(
                HoldingPI(
                    vaults[vaultId].trustedPositionsBP[_positionId].calculatorConnector,
                    msg.sender,
                    _positionId,
                    d,
                    AD,
                    type(uint256).max
                )
            );
            return vault.holdingPositions.length - 1;
        }
        vault.holdingPositions[index].additionalData = AD;
        return index;```



https://vscode.dev/github/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L302