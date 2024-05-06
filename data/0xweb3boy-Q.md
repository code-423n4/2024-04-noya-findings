Low-01 - Holding positions of the vault will not reach its max  capacity due to off by one error

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L308-L309

`Registry.sol`  -  `updateHoldingPosition()` is used to update all the positions held by the connectors after checking if these positions are a duplicate positions or if they are a trusted position and the adds  them to the `HoldingPositions` array of the vault, however due to invalid comarison in the if block these positions will never reach its max capacity which is 20 in this case.

```java
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
```

However while doing so it checks one if condition 

```java
if (vault.holdingPositions.length >= maxNumHoldingPositions) {
                revert TooManyPositions();
            }
```

Where it checks if the vault is holding max no of tokens or not by comparing it to `maxNumHoldingPositions` which is 20 in this case, but even if the vault is holding `20` tokens the whole update will just revert due to the wrong comparison

It should have been only `>` rather than `>=`
```java
if (vault.holdingPositions.length > maxNumHoldingPositions) {
                revert TooManyPositions();
            }
```

Off by ones are mostly QA's but due to `updateHoldingPosition()` being one of the most important functions in the whole protocol and it is mostly used in every connectors to update the holding positions, And limiting holding positions to 19 would not be an ideal situation protocol would want to be in, so I think this could be a Medium severity at least.

## Recommended Mitigation Steps

```diff
- if (vault.holdingPositions.length >= maxNumHoldingPositions) {
-                revert TooManyPositions();
-            }

+ if (vault.holdingPositions.length > maxNumHoldingPositions) {
+                revert TooManyPositions();
+            }
```
