# Low-01 - Holding positions of the vault will not reach its max  capacity due to off by one error

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L308-L309

`Registry.sol`  -  `updateHoldingPosition()` is used to update all the positions held by the connectors after checking if these positions are duplicate positions or if they are trusted positions and then adds them to the `HoldingPositions` array of the vault, however, due to invalid comparison in the if block these positions will never reach the max capacity which is 20 in this case.

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

However, while doing so it checks one condition:

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

Off-by ones are mostly QA's but due to `updateHoldingPosition()` being one of the most important functions in the whole protocol and it is mostly used in every connector to update the holding positions, limiting holding positions to 19 would not be ideal situation protocol would want to be in, so I think this could be a Medium severity at least.

## Recommended Mitigation Steps

```diff
- if (vault.holdingPositions.length >= maxNumHoldingPositions) {
-                revert TooManyPositions();
-            }

+ if (vault.holdingPositions.length > maxNumHoldingPositions) {
+                revert TooManyPositions();
+            }
```


# Low-02 - LiFi `Implementation.sol::addBridgeBlacklist` function name should be changed as it can lead to unnecessary faults by admin.

[addBridgeBlacklist](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L68) the function name suggests that the bridge is being added to blacklist but the code says otherwise,

```solidity
 function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {
        isBridgeWhiteListed[bridgeName] = state;
        emit AddedBridgeBlacklist(bridgeName, state);
    }
```
In the above function when a `bridgeName` with `state = true` is passed the bridge is added to the list of mappings `isBridgeWhiteListed` where all the bridges with state set to true are whitelisted, while the name of the function says `addBridgeBlacklist` this can confuse the admin and lead to a fault where admin sets the `state = false` thinking he is adding to the list of whitelist and further the function [performBridgeAction](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L139) is calling [verifyBridgeData](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153) which further checks if the bridge is blacklisted or not and reverts the transaction if the `state = false`.


```solidity
if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
```

The recommendation would be to just change the function name to avoid confusion and setting wrong states.

# Low-03 - Many functionalities will be broken if external tokens with a pausability mechanism ever pause their contract.

As per the contracts readme it is already mentioned that tokens with pausing mechanism are in the scope of this audit.

![pausibility](https://github.com/0xWeb3boy/photo/assets/113019033/b0799d25-1313-47c4-bd15-9bb1b9f95972)

Now there are many tokens like USDT/USDC/FRAX to name a few that have this pausability feature, also if they ever decide to pause their contracts there are many functionalities in the protocol that will be bricked since the protocol relies heavily on these tokens.

This should be of medium severity as this particular issue comes under the scope of the audit and the protocol already mentioned in the readme that external token integration with a pausing mechanism is in the scope of the audit.

There is no such way to actually mitigate this than just letting the users know beforehand about the occurrence of this event.

# Low-04 - In `FraxConnector.sol` there are a few inconsistencies which could lead to accounting issues

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/FraxConnector.sol#L87-L98

when a call to the `withdraw()` function is made, the holding position is updated there, but while repaying the holding position is not updated.

```solidity
 function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
        uint256 repayTokenAmount = pool.toBorrowAmount(sharesToRepay, true);
        uint256 sharesOwed = pool.userBorrowShares(address(this));
        address asset = pool.asset();
        if (sharesToRepay > sharesOwed) {
            revert IConnector_InvalidInput();
        }
        _approveOperations(asset, address(pool), repayTokenAmount); 
        IFraxPair(pool).repayAsset(sharesToRepay, address(this));
        _updateTokenInRegistry(asset);
        emit Repay(address(pool), sharesToRepay);
    }
``` 
The above function in `FraxConnector` is to repay the borrowed assets but there is no call to registry.updateHoldingPosition in this function
While in every other connector, while repaying they are calling this updateHoldingPosition, this could lead to inconsistency in the accounting.

Although it can be done manually via calling `registry.updateHoldingPosition` function it should be automatic just like it has been done in other connectors.

# Low-05 - Protocol assumes 6 decimals for USDC

depositLimitTotalAmount is defined in AccountManager as -

`uint256 public depositLimitTotalAmount = 1e6 * 200_000;`

This shows that the protocol is assuming 6 decimals for USDC, which is not the case with the BSC chain, as USDC on BSC has 18 decimals.

Due to this the deposit limits for each transaction and for the total is set to a very small amount, thus preventing the user from depositing the amount they want.

To mitigate this, before deploying the contract, use 18 decimals for BSC. These checks should be made on a case-by-case basis for each chain.