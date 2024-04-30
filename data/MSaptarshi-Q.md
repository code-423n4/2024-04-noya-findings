# [L-01] Missing zero address check
The protocol actually checks for address not set to zero in most of the cases, but here i think they missed it to check it
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31
## Recommendation
Add a zero address check
