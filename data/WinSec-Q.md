# Low-01 - Holding positions of the vault will not reach its max  capacity due to off by one error

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


# Low-02 LiFi `Implementation.sol::addBridgeBlacklist` function name should be changed as it can lead to unecessary faults by admin.

[addBridgeBlacklist](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L68) the function name suggests that the bridge is being added to blacklist but the code says otherwise,

```solidity
 function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {
        isBridgeWhiteListed[bridgeName] = state;
        emit AddedBridgeBlacklist(bridgeName, state);
    }
```
In the above function when a `bridgeName` with `state = true` is passed the bridge is added to the list of mappings `isBridgeWhiteListed` where all the bridges with state set to true are whitelisted, while the name of the function says `addBridgeBlacklist` this can confuse the admin and lead to a fault where admin sets the `state = false` thinking he is adding to the list of whitelist and further the function [performBridgeAction](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L139) is calling [verifyBridgeData](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153) which further checks if the bridge is blacklisted or not and reverts the trransaction if the `state = false`.


```solidity
if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
```

Recommendation would be to just change the function name to avoid confusion and setting wrong states.

# Low-03 Many functionality will be broken if external tokens with pausability mechanism ever pause their contract.

As per the contracts readme it is already mentioned that tokens with pausing mechanism are in the scope of this audit.

![pausibility](https://github.com/0xWeb3boy/photo/assets/113019033/b0799d25-1313-47c4-bd15-9bb1b9f95972)

Now there are many tokens like USDT/USDC/FRAX to name a few that have this pausability feature, also if theyt ever decide to pause their contracts there are many functionalities in the protocol that will be bricked since the protocol relies heavily on these tokens.

This should be of medium severity as this particular issue comes under the scope of the audit and the protocol already have mentioned in the readme that external token integration with pausibility mechanism is in the scope of the audit.

Their is no such way to actually mitigate this than just letting the users know before hand about the occurence of this event.

# Low-04  