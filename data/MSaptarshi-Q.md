# [L-01] A malicious deployer can set themselves as the fee reciever
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

# [L-04] Curve withdraws `weth` when removing liquidity from Curve V2 pools
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L169
Curve V2 pool will always wrap to WETH unless the use_eth is explicitly set to True. `remove_liquidity_one_coin` function is executed without explicitly setting the use_eth parameter to True. Thus, WETH instead of Native ETH will be returned during remove liquidity. As a result, these weth if not accounted for in the vault may cause loss of assets.
https://etherscan.io/address/0x0f3159811670c117c372428d4e69ac32325e4d0f#code
```
[def remove_liquidity_one_coin(token_amount: uint256, i: uint256, min_amount: uint256,
                              use_eth: bool = False, receiver: address = msg.sender) -> uint256:]
```
## Recommendation 
Make sure user's/keepers are made aware of this issue

