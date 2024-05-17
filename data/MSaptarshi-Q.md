# [L-01] A malicious deployer can set themselves as the fee reciever
In the NoyafeeReciever contract a malicious deployer can set themsleves as fee reciever
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L20
## Recommendation
Add proper explicit check for deployers/owners for such specific risks

# [L-02] Lido MIN/MAX withdrawal
Lido has a [MIN](https://github.com/lidofinance/lido-dao/blob/5fcedc6e9a9f3ec154e69cff47c2b9e25503a78a/contracts/0.8.9/WithdrawalQueue.sol#L52) and a [MAX](https://github.com/lidofinance/lido-dao/blob/5fcedc6e9a9f3ec154e69cff47c2b9e25503a78a/contracts/0.8.9/WithdrawalQueue.sol#L57) withdrawal limit check present for limit minimal and huge withdrawl
But Noya doesn't set those checks or any warnings in the comments
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L51
So some users who might be withdrawing <100 , might see their transaction get reverted, and since there is a approve present which is itself prone to frontrunning might be a bit problematic for users
## Recommendation
Either warn users through docs or implement the checks 


# [L-03] Uniswapv3 Price manipulation.
The oracle uses the TWAP price from Uniswap V3 to determine the price of each asset.
If a pair is not listed on Uniswap V3, the oracle will not work.
This will be a relatively common occurrence that doesn't require obscure tokens. Many combinations of tokens on Uniswap are able to be traded because they don't have a pool directly, but they share a poolmate. A quick review of [Uniswap Pairs](https://info.uniswap.org/pairs#/), can show this.

An attacker Create a Uniswap V3 pool with the required token and the token in question
Seed it with an incredibly low amount of liquidity at a ratio that values that token in question at ~0
They would just Maintain the price for the length of the TWAP, which shouldn't be hard with a new, unused pool and low liquidity(arbitrages shouldn't touch it). Or they can overinflate the price so that when the price of that token is fetched from that pool, it returns the manipulated price

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60
## Recommendation
UniV3Oracle should require the pool being used as an oracle to meet certain liquidity thresholds or have existed for a predefined period of time before returning the price to the Swapper.

# [L-04] Admin setter functions missing events
Events are often used to monitor the protocol status. Without emission of events, users might be affected due to ignorance of the changes.

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L36
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L52
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L51
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L63

## Recommended 
Add events for the mentioned codelines, & check for other parts where event emission might be needed 

# [L-05] Access-controlled functions cannot be called when L2 sequencers are down
L2 rollups like Optimism and Arbitrum have forced transaction inclusion, it is important that the aliased sender address is also checked within access control modifiers when verifying the sender holds a permissioned role to allow the functions to which they are applied to be called even in the event of sequencer downtime. 
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L31
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L43
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L53
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L65
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L659
# Recommendation 
Validate the sender address against permissioned pauser/keeper/manager roles .

# [L-06] The contract will revert when trying to initialize with tokens, that do not support name/symbol in string type variable
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L96
The accounting manager initializes the contracts with those tokens, when deploying the contract through `ERC20(p._name, p._symbol)` where p is the `AccountingManagerConstructorParams` struct where name/symbol are present as struct

```diff
struct AccountingManagerConstructorParams {
    string _name;
    string _symbol;
   ,
   ....
    ,
}
```
Tokens such as makerdao has name/symbol encoded as bytes instead of string

## Recommendation
Add different logic if these tokens are expected to be supported

# [L-07] Tvl might not get updated on hardfork
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L20
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L9
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L78
The protocol uses mapping to store the `chainId` of that particular chain, If the chain were to through a hardfork the `chainId` will change. This might lead to token balance updating in the chain inaccessible due to a difference between the actual TVL & stored TVL
## Recommendation
Add an admin operated function, to migrate the updating of TVL from old to new `chainID`

# [L-08] All harvest/claim doesn't yield same amount of reward
A keeper is supposed to call and withdraw the rewards which user's generated at their respective positions in the connector.
But all harvest doesn't produce same yield as reward which can be unprofitable for keeper in terms of gas costs
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L221
## Recommendation
Make sure the keeper calls it with appropriate gas costs.

# [L-09] A malicious keeper/watcher can attack on harvest reward
Keepers/watcher are highly trusted entities that are intended to be multisigs/smart contracts with trust assumptions similar to governance addresses. However if they are compromised they can decrease other user's positions by making a large deposit, triggering a harvest or withdrawing a position from a certain connector
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L221
# Recommendation 
Make sure keeper’s/watcher's access well-secured to avoid misuse of the trust.

# [L-10] Multiple Token Address (Weird ERC20)
A owner is set to send funds `rescuefunds` to user's address if anyhow some assets let remain in the contract `LifiImplementation.sol`. 
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193
But some proxied tokens have multiple addresses. Any protocol would assume single address per token and so allowing the owner to steal all the funds in the bridge.
More importantly there are no further checks which user's address the assets are being sent to, making an owner to send those assets to any random user's address
## Recommendation
Make sure the owner is well trusted and have a gateway for the tokens supported

# [L-11] Failed transfer with low level call won't revert
Noya uses low level call to transfer assets. According to [Solidity Docs](https://docs.soliditylang.org/en/develop/control-structures.html#error-handling-assert-require-revert-and-exceptions)the call may return true even if it was a failure. This may result in user funds lost because funds were transferred into this contract in preparation for the swap. The swap fails but doesn't revert.
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176
## Recommendation
Check for contract existance, in places where low level calls are used

# [L-12] Decmials should be returned as uint8
Some tokens are vulnerable when returning tokens decimal as uint256 instead of uint8
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L138
## Recommendation
  ```
- function getTokenDecimals(address token) public view returns (uint256) {
+    function getTokenDecimals(address token) public view returns (uint8) {
```

Also wrap it in try/catch if the metadata of the token is not supported


