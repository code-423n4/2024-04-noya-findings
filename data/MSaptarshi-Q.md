# [L-01] Missing zero address check
The protocol actually checks for address not set to zero in most of the cases, but here i think they missed it to check it
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31
## Recommendation
Add a zero address check

# [L-02] Missing check for zero fee
The protocol should check for zero fee initialization 
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L112
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L170
## Recommendation
Add a zero fee check

# [L-03] A malicious owner can set themselves as the fee reciever
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L20
## Recommendation
Add proper explicit check for owners if trying to do malicious things