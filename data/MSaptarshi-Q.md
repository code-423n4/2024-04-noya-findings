# [L-01] A malicious deployer can set themselves as the fee reciever
In the keeper contract a malicious deployer can set themsleves as fee reciever
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

# [L-03] Curve admin fees
Curve has a feature for when adding liquidity into their pool they have a fees kept for admin. The protocol calculates the minAmount offchain to mitiagte for slippage, but for end users who interact with NOYA for them it can  be unknown
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L131
## Recommendation 
Make sure it is well known in the docs


# [L-04] Uniswapv3 Price manipulation.
The oracle uses the TWAP price from Uniswap V3 to determine the price of each asset.
If a pair is not listed on Uniswap V3, the oracle will not work.
This will be a relatively common occurrence that doesn't require obscure tokens. Many combinations of tokens on Uniswap are able to be traded because they don't have a pool directly, but they share a poolmate. A quick review of [Uniswap Pairs](https://info.uniswap.org/pairs#/), can show this.

An attacker Create a Uniswap V3 pool with the required token and the token in question
Seed it with an incredibly low amount of liquidity at a ratio that values that token in question at ~0
They would just Maintain the price for the length of the TWAP, which shouldn't be hard with a new, unused pool and low liquidity(arbitrages shouldn't touch it). Or they can overinflate the price so that when the price of that token is fetched from that pool, it returns the manipulated price


https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60
## Recommendation
UniV3Oracle should require the pool being used as an oracle to meet certain liquidity thresholds or have existed for a predefined period of time before returning the price to the Swapper.