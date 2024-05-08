## Misleading NatSpec and potential gas optimization in `Registry.sol::updateConnectorTrustedTokens`

### Description: 

NatSpec in `Registry.sol::updateConnectorTrustedTokens` states that this function should take an array of token addresses + an array of booleans indicating if these tokens should be trusted by a connector or not. However, the function actually takes a boolean instead of an array of booleans setting ALL of the tokens in the passed array to either trusted or not trusted.

### Impact:
In case a user wants to add some tokens as trusted and change others to non-trusted they need to send at least two transactions instead of a single one, increasing their gas costs.

The NatSpec can be misleading for users and cause failed transactions on their side when passing an array of booleans as indicated in the NatSpec.

### Recommended Mitigation: 
**Preffered**:
Change the `Registry.sol::updateConnectorTrustedTokens` to accept an array of booleans for `trusted` parameter with update logic similar to `_enableds` in `Registry.sol::addConnector` function.

```diff
function updateConnectorTrustedTokens(
    uint256 vaultId,
    address _connectorAddress,
    address[] calldata _tokens,
-   bool trusted
+   bool[] calldata _trusteds
) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
    Vault storage vault = vaults[vaultId];
    for (uint256 i = 0; i < _tokens.length; i++) {
-       vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = trusted;
+       vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = _trusteds[i];
    }
    emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, _trusteds);
}
```

OR

Update the NatSpec to reflect the function taking a single boolean for all tokens.

```diff
/*
* @dev This function is used to add or remove new trusted tokens to an specific connector
* @param vaultId The id of the vault
* @param _connectorAddress The address of the connector
* @param _tokens An array of token addresses
- * @param _trusteds An array of booleans indicating if the token is trusted or not
+ * @param _trusteds A boolean indicating if all tokens in _tokens parameter should be trusted
*/
function updateConnectorTrustedTokens(...snippet...) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
    ...snippet...
}
}
```