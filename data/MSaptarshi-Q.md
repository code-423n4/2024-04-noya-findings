# [L-01] A malicious owner can set themselves as the fee reciever
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L20
## Recommendation
Add proper explicit check for owners if trying to do malicious things

# [L-02] Lido MIN/MAX withdrawal
Lido has a [MIN](https://github.com/lidofinance/lido-dao/blob/5fcedc6e9a9f3ec154e69cff47c2b9e25503a78a/contracts/0.8.9/WithdrawalQueue.sol#L52) and a [MAX](https://github.com/lidofinance/lido-dao/blob/5fcedc6e9a9f3ec154e69cff47c2b9e25503a78a/contracts/0.8.9/WithdrawalQueue.sol#L57) withdrawal limit check present for limit minimal and huge withdrawl
But Noya doesn't set those checks or any warnings in the comments
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L51
So some users who might be withdrawing <100 , might see their transaction get reverted, and since there is a approve present which is itself prone to frontrunning might be a bit problematic for users
## Recommendation
Either warn users through docs or implement the checks 