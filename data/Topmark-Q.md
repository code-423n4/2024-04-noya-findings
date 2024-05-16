### Report 1:
#### DoS When Emergency Role Address wants to remove Trusted Position
Denial of Service When Emergency Role Address wants to remove Trusted Position at [L268](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L268) that it initially added at [L246](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L246) due to strict validation of onlyVaultMaintainer modifier which requires that emergency role must also be vault maintainer unlike the addTrustedPosition(...) function that can be called by only the Emegency role as can be noted in the onlyVaultMaintainerWithoutTimeLock modifier below.
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L33
```solidity
  modifier onlyVaultMaintainer(uint256 _vaultId) {
>>>        if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {
            revert UnauthorizedAccess();
        }
        _;
    }
    modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) {
        if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
            revert UnauthorizedAccess();
        }
        _;
    }
```

