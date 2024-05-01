## Misleading NatSpec and potential gas optimization in `Registry.sol::updateConnectorTrustedTokens`

### Description: 

NatSpec in `Registry.sol::updateConnectorTrustedTokens` states that this function should take an array of token addresses + an array of booleans indicating if these tokens should be trusted by a connector or not. However, the function actually takes a boolean instead of an array of booleans setting ALL of the tokens in the passed array to either trusted or not trusted.

### Impact:
In case a user wants to add some tokens as trusted and change others to non-trusted they need to send at least two transactions instead of a single one, increasing their gas costs.

The NatSpec can be misleading for users and cause failed transactions on their side when passing an array of booleans as indicated in the NatSpec.

### Recommended Mitigation: 
**Preffered**:
Change the `Registry.sol::updateConnectorTrustedTokens` to accept an array of booleans for `trusted` parameter with update logic similar to `_enableds` in `Registry.sol::addConnector` function.

OR

Update the NatSpec to reflect the function taking a single boolean for all tokens.