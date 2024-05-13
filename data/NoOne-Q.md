Here in [BalancerConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L62)
The comment is `Internal Functions *********************************` but all functions are public execpt [function _getPoolInfo](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L189)

In [PancakeswapConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L11)
The comment is `// ------------ errors -------------- //` but there is no errors

In [SNXConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L47) this comment should be `Withdraw`

In [UNIv3Connector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L121) it has comment for Internal functions but it has more public than internal functions

In [Keepers.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L14)  `nonce` it doesnt set in the constructor

In [MaverickConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L161) the function parameter `uint256 id` is unused

In [ConnectorMock2.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L27) the function parameter is unused `address caller`

In [AerodromeConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L117) the function parameter is unused `uint256 p`

In [BalancerFlashLoan.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L69) local variable is unused `address emergencyManager`

In `PendleConnector.sol` in [swapYTForPT](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L149) , [swapYTForSY](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L166C14-L166C25) has an unused local variables `IPStandardizedYield _SY, IPPrincipalToken _PT` and in [swapExactPTForSY](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L183) has an unused local variable `IPStandardizedYield _SY`
 
In `NoyaGovernanceBase.sol` has unused modifiers 
[modifier onlyEmergencyOrWatcher](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L53)
[modifier onlyGovernance](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L85)


//------------Unused imports----------//

[MaverickConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L4)
[BaseConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L8)
[BaseConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L12)
[LZHelperReceiver.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L4)
[LZHelperSender.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L4)
[LZHelperSender.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L6)
[NoyaValueOracle.so](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L4)
[ChainlinkOracleConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L7)
[UniswapValueOracle.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L6)


//-----------------------------------//

