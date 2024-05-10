Here in [BalancerConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L62)
The comment is `Internal Functions *********************************` but all functions are public execpt [function _getPoolInfo](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L189)

In [PancakeswapConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L11)
The comment is `// ------------ errors -------------- //` but there is no errors

In [SNXConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L47) this comment should be `Withdraw`

In [UNIv3Connector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L121) it has comment for Internal functions but it has more public than internal functions

In [Keepers.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L14)  `nonce` it doesnt set in the constructor
