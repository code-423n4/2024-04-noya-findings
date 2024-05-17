
# LOWS

## [1] Any connector can transfer an arbitrary amount of tokens at any time from another connector by calling `sendTokensToTrustedAddress` from that connector.

## [2] Allowing the management to completely lose fees whenever the tvl drops drastically can accumulate loss of funds for protocol in long term

## [3] Any connector can transfer any amount of token at any time out of `AccountingManager` which can lead to problems with other processes in the syste
m
## [4] Use of `safeTransferFrom` in `AccountingManager::deposit` may fail if deployed on arbitrum and WETH is set as the basetoken

## [5] `Manager` cannot remove malicious deposits or rearrange the depositQueue

## [6] `Manager` cannot remove malicious withdraw requests or rearrange the withdraw group

## [7]  Execution of the withdraw group in a loop can become very expensive and cause other problems with execution

## [8] There is no time limit between when deposits are created and when they're calculated by the manager, creating a scenario where users cannot reliable predict how long their deposits would take

## [9] There is no time limit between when withdraw are created and when they're executed by the manager, causing users to wait longer than the `WithdrawWaitingTime` for their withdrawn assets

## [10] Not allowing the manager to manually end a `currentWithdrawGroup` and start a new one unless it is completely executed leads to numerous problems and can cause withdraw by legit users to be griefed

## [11] uniswapV3 slot0 price is used to getPositionTvl in `UNIv3Connector` which is prone to manipulation.

## [12] Execution of deposits in a loop can become very expensive and cause other problems with execution

## [13] `BaseConnector::executeSwap` would revert if any of the amounts for any token is 0.

## [14] `BaseConnector` should implement the erc165 interface in the BaseConnector to ensure any connector which inherits from it is completely compatible with it.

## [15] Eligible users in `GenericSwapAndBridgeHandler` can be added but cannot be removed by the maintainer or emergency.

## [16] Routes in `GenericSwapAndBridgeHandler` should be removeable by the maintainer or emergency

## [17] Looping over all current positions when getting the position tvl can be expensive and gas-intensive. Depending on number of positions this can be DOSsed

## [18] `WETH_Oracle` does not implement `INoyaValueOracle` interface.

## [19] Encoding the WETH_Oracle answer as 1e18 can cause problems when calculating value.

## [20] The `AccountingManager` for a vault can never be changed.

## [21] `Vault` struct does not implement all parameters in documentation

## [22] The placeholder of ETH being `address(0)` in `ChainlinkOracleConnector` can cause problems with other aspects of the protocol.

## NC/INFO

## [19] Missing 0 address checks in critical aspects of the system

## [20] Wrong parameter documentation in various parts of the system

## [21] `Governer` should be corrrected to `Governor` in `Registry`

## [23] Difference in filename and contract name in `Registry.sol`

## [24] `vaults[vaultId]` should be cached once in `Registry::changeVaultAddresses` to save gas

## [25] Discrepancy in access control mechanism in `PositionRegistry`

## [26] Use of same function name in the same contract can be confusing for users and other devs

## [27] When 2 arrays are accepted in a function, it is recommended to first check if both array lengths match before carrying out execution with them

## [28] Routes can be added multiple times in `GenericSwapAndBridgeHandler`

## [29] Wrong event emission in multiple parts of the system

## [30] Allowing the price threshold of chainlink to be set up to 10 days can create arbitrage opportunities

## [31] Chainlink's library should be used directly in `AggregatorV3Interface`

