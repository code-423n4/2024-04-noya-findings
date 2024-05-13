### Prevent re-setting a state variable with the same value
Not only is wasteful in terms of gas, but this is especially problematic when an event is emitted and the old and new values set are the same, as listeners might not expect this kind of scenario.

```solidity
Path: ./contracts/accountingManager/Registry.sol

86:        flashLoan = _flashLoan;	// @audit-issue

174:        vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock;	// @audit-issue

177:        vaults[vaultId].emergency = _emergency;	// @audit-issue

380:            vaults[vaultId].holdingPositions[positionIndex].positionTimestamp = positionTimestamp;	// @audit-issue
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L86-L86), [174](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L174-L174), [177](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L177-L177), [380](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L380-L380), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

126:        valueOracle = _valueOracle;	// @audit-issue

215:        depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);	// @audit-issue

313:        withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);	// @audit-issue

668:        depositLimitPerTransaction = _depositLimitPerTransaction;	// @audit-issue

669:        depositLimitTotalAmount = _depositTotalAmount;	// @audit-issue

674:        depositWaitingTime = _depositWaitingTime;	// @audit-issue

679:        withdrawWaitingTime = _withdrawWaitingTime;	// @audit-issue
```
[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L126-L126), [215](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L215-L215), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L313-L313), [668](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L668-L668), [669](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L669-L669), [674](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L674-L674), [679](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L679-L679), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

59:        swapHandler = SwapAndBridgeHandler(_swapHandler);	// @audit-issue

68:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue
```
[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L59-L59), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L68-L68), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

49:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue

58:        genericSlippageTolerance = _slippageTolerance;	// @audit-issue

72:        slippageTolerance[_inputToken][_outputToken] = _slippageTolerance;	// @audit-issue

159:        routes[_routeId].isEnabled = enable;	// @audit-issue
```
[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L49-L49), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L58-L58), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L72-L72), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L159-L159), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

46:        isHandler[_handler] = state;	// @audit-issue

56:        isChainSupported[_chainId] = state;	// @audit-issue

66:        isBridgeWhiteListed[bridgeName] = state;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L46-L46), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L56-L56), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L66-L66), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

42:            defaultPriceSource[baseCurrencies[i]] = oracles[i];	// @audit-issue

56:            priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);	// @audit-issue

62:        priceRoutes[asset][base] = s;	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L42-L42), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L62-L62), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

75:            assetsSources[assets[i]][baseTokens[i]] = sources[i];	// @audit-issue
```
[75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

42:        chainInfo[lzChainId] = ChainInfo(chainId, lzHelperAddress);	// @audit-issue

54:        vaultIdToVaultInfo[vaultId] = VaultInfo(baseChainId, omniChainManager);	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L42-L42), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L54-L54), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

37:        messageSetting = _messageSetting;	// @audit-issue

53:        chainInfo[chainId] = ChainInfo(lzChainId, lzHelperAddress);	// @audit-issue

64:        vaultIdToVaultInfo[vaultId] = VaultInfo(baseChainId, omniChainManager);	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L37-L37), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L64-L64), 


#### Recommendation

Implement checks in your Solidity contracts to avoid re-setting state variables to their existing values. Prior to updating a state variable, compare the new value with the current value and proceed with the assignment only if they differ. Additionally, ensure that events related to state variable updates are emitted only when actual changes occur. This approach not only saves gas but also prevents confusion and unnecessary triggers in event listeners. Regularly reviewing and optimizing your contract for such redundancies can significantly enhance efficiency and clarity in contract operations.

### Cache Local Variable Array Length In For Loop
If not cached, the solidity compiler will always read the length of the array during each iteration. If it is a memory array, this is an extra mload operation (3 additional gas for each iteration except for the first).

```solidity
Path: ./contracts/accountingManager/Registry.sol

138:        for (uint256 i = 0; i < _trustedTokens.length; i++) {	// @audit-issue

194:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {	// @audit-issue

214:        for (uint256 i = 0; i < _tokens.length; i++) {	// @audit-issue

253:            for (uint256 i = 0; i < usingTokens.length; i++) {	// @audit-issue
```
[138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138-L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214-L214), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L253-L253), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

551:        for (uint256 i = 0; i < retrieveData.length; i++) {	// @audit-issue

603:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue

608:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue
```
[551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551-L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608-L608), 


```solidity
Path: ./contracts/governance/Keepers.sol

29:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29-L29), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

18:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L18-L18), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

178:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

189:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

211:        for (uint256 i = 0; i < tokensIn.length; i++) {	// @audit-issue
```
[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211-L211), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

37:        for (uint256 i = 0; i < usersAddresses.length; i++) {	// @audit-issue

148:        for (uint256 i = 0; i < _routes.length;) {	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), [148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L148), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

41:        for (uint256 i = 0; i < baseCurrencies.length; i++) {	// @audit-issue

55:        for (uint256 i = 0; i < oracle.length; i++) {	// @audit-issue

88:        for (uint256 i = 0; i < sources.length; i++) {	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

74:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

140:        for (uint256 i = 0; i < earnedInfo.length; i++) {	// @audit-issue
```
[140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

69:        for (uint256 i = 0; i < calls.length; i++) {	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

116:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue

132:        for (uint256 i = 0; i < assetsS.length; i++) {	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L116-L116), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

102:        for (uint256 i = 0; i < tokenIds.length; i++) {	// @audit-issue
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

54:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue

77:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54-L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

74:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

79:            for (uint256 i = 0; i < destinationConnector.length; i++) {	// @audit-issue

84:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

89:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

244:        for (uint256 i = 0; i < rewardTokens.length; i++) {	// @audit-issue
```
[244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

113:        for (uint256 i = 0; i < markets.length; i++) {	// @audit-issue
```
[113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L113-L113), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

222:        for (uint256 i = 0; i < gauges.length; i++) {	// @audit-issue

234:        for (uint256 i = 0; i < pools.length; i++) {	// @audit-issue

248:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue
```
[222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222-L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234-L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248-L248), 


#### Recommendation

To optimize gas consumption, cache the length of memory arrays before for loop iterations in Solidity. This reduces redundant mload operations, saving 3 gas per iteration after the first and improving overall contract efficiency.

### State Variable Access Within a Loop
State variable reads and writes are more expensive than local variable reads and writes. Therefore, it is recommended to replace state variable reads and writes within loops with a local variable. Gas savings should be multiplied by the average loop length.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

233:            depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime	// @audit-issue: `depositQueue` used in loop.

237:            DepositRequest storage data = depositQueue.queue[middleTemp];	// @audit-issue: `depositQueue` used in loop.

268:            depositQueue.middle > firstTemp	// @audit-issue: `depositQueue` used in loop.

269:                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI	// @audit-issue: `depositQueue` used in loop.

269:                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI	// @audit-issue: `depositWaitingTime` used in loop.

272:            DepositRequest memory data = depositQueue.queue[firstTemp];	// @audit-issue: `depositQueue` used in loop.

281:            delete depositQueue.queue[firstTemp];	// @audit-issue: `depositQueue` used in loop.

339:            withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime	// @audit-issue: `withdrawQueue` used in loop.

343:            WithdrawRequest storage data = withdrawQueue.queue[middleTemp];	// @audit-issue: `withdrawQueue` used in loop.

407:            currentWithdrawGroup.lastId > firstTemp	// @audit-issue: `currentWithdrawGroup` used in loop.

408:                && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp	// @audit-issue: `withdrawQueue` used in loop.

408:                && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp	// @audit-issue: `withdrawWaitingTime` used in loop.

412:            WithdrawRequest memory data = withdrawQueue.queue[firstTemp];	// @audit-issue: `withdrawQueue` used in loop.

416:                data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;	// @audit-issue: `currentWithdrawGroup` used in loop.

418:            withdrawRequestsByAddress[data.owner] -= shares;	// @audit-issue: `withdrawRequestsByAddress` used in loop.

423:                uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;	// @audit-issue: `withdrawFee` used in loop.

428:            baseToken.safeTransfer(data.receiver, baseTokenAmount);	// @audit-issue: `baseToken` used in loop.

432:            delete withdrawQueue.queue[firstTemp];	// @audit-issue: `withdrawQueue` used in loop.

552:            if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {	// @audit-issue: `registry` used in loop.

552:            if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {	// @audit-issue: `vaultId` used in loop.

555:            uint256 balanceBefore = baseToken.balanceOf(address(this));	// @audit-issue: `baseToken` used in loop.

557:                address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data	// @audit-issue: `baseToken` used in loop.

559:            uint256 balanceAfter = baseToken.balanceOf(address(this));	// @audit-issue: `baseToken` used in loop.

566:                amountAskedForWithdraw + amountAskedForWithdraw_temp	// @audit-issue: `amountAskedForWithdraw` used in loop.

604:                depositData[i] = depositQueue.queue[items[i]];	// @audit-issue: `depositQueue` used in loop.

609:                withdrawData[i] = withdrawQueue.queue[items[i]];	// @audit-issue: `withdrawQueue` used in loop.
```
[233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L233-L233), [237](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L237-L237), [268](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L268-L268), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L269-L269), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L269-L269), [272](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L272-L272), [281](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L281-L281), [339](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L339-L339), [343](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L343-L343), [407](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L407-L407), [408](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L408-L408), [408](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L408-L408), [412](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L412-L412), [416](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L416-L416), [418](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L418-L418), [423](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L423-L423), [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L428-L428), [432](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L432-L432), [552](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L552-L552), [552](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L552-L552), [555](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L555-L555), [557](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L557-L557), [559](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L559-L559), [566](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L566-L566), [604](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L604-L604), [609](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L609-L609), 


```solidity
Path: ./contracts/governance/Keepers.sol

30:            isOwner[_owners[i]] = true;	// @audit-issue: `isOwner` used in loop.

45:            if (addOrRemove[i] && !isOwner[_owners[i]]) {	// @audit-issue: `isOwner` used in loop.

46:                isOwner[_owners[i]] = true;	// @audit-issue: `isOwner` used in loop.

48:            } else if (!addOrRemove[i] && isOwner[_owners[i]]) {	// @audit-issue: `isOwner` used in loop.

49:                isOwner[_owners[i]] = false;	// @audit-issue: `isOwner` used in loop.

106:                require(recovered > lastAdd && isOwner[recovered]);	// @audit-issue: `isOwner` used in loop.

104:            for (uint256 i = 0; i < threshold;) {	// @audit-issue: `threshold` used in loop.
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L30-L30), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L45-L45), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L46-L46), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L48-L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L49-L49), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L106-L106), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L104-L104), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

38:            isEligibleToUse[usersAddresses[i]] = true;	// @audit-issue: `isEligibleToUse` used in loop.

149:            routes.push(_routes[i]);	// @audit-issue: `routes` used in loop.
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L38-L38), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L149-L149), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

42:            defaultPriceSource[baseCurrencies[i]] = oracles[i];	// @audit-issue: `defaultPriceSource` used in loop.

56:            priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);	// @audit-issue: `priceSource` used in loop.
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L42-L42), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

75:            assetsSources[assets[i]][baseTokens[i]] = sources[i];	// @audit-issue: `assetsSources` used in loop.
```
[75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

78:            if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);	// @audit-issue: `balancerVault` used in loop.
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L78-L78), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

114:            uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value);	// @audit-issue: `valueOracle` used in loop.
```
[114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L114-L114), 


#### Recommendation

Optimize gas usage in Solidity by replacing state variable reads and writes within loops with local variable operations. This reduces gas costs significantly, especially when multiplied by the average loop length.

### Function Visibility Can Be `view`
In Solidity, a `view` function indicates that it will not modify the blockchain state. It's only allowed to read from the blockchain, not write to it. Ensuring a function is marked as `view` when possible helps with gas optimization, as calls to such functions do not consume any gas when called externally. This also provides better clarity and security, as it guarantees that calling the function won't result in any state changes. If a function only reads state variables but is not marked as `view`, it's recommended to update its visibility to reflect this and potentially reduce gas costs for clients interfacing with the contract.

```solidity
Path: ./contracts/helpers/BaseConnector.sol

267:    function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {	// @audit-issue
```
[267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267), 


#### Recommendation

Ensure functions that only read from the blockchain state are marked as 'view' in Solidity. This improves gas efficiency for external calls and provides clarity on the function's non-state-modifying behavior, enhancing security and contract integrity.

### Function Visibility Can Be `pure`
In Solidity, a `pure` function is one that neither reads from nor writes to the blockchain state; it only works with the input values provided and computes the output. Marking a function as `pure` is used for functions like mathematical calculations and ensures that no gas is spent on reading or altering stored data when it's called.

```solidity
Path: ./contracts/governance/Watchers.sol

8:    function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

267:    function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {	// @audit-issue

271:    function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {	// @audit-issue
```
[267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267), [271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271-L271), 


#### Recommendation

Mark functions in Solidity as 'pure' when they neither read from nor write to the blockchain state. This practice optimizes gas usage by signaling that the function only performs computations with its input values.

### Unnecessary Variable Initialization
In programming, it's a common practice to declare and initialize variables that will be used later in the code. However, if after declaration, the variable is not used anywhere else in the code, this leads to unnecessary variable initialization. In the context of Solidity and smart contracts, where gas efficiency is paramount, such redundant initializations not only consume extra gas but also clutter the codebase, making it less readable and harder to maintain.

Variables that are declared but never used represent dead code. They take up space in the bytecode, result in wasted gas when the contract is deployed, and can be confusing for anyone reading or auditing the code.


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

331:        uint256 processedShares = 0;	// @audit-issue
```
[331](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L331-L331), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

96:        uint256 tokenId;	// @audit-issue
```
[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L96-L96), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

129:        uint256 tokenId = abi.decode(p.data, (uint256));	// @audit-issue
```
[129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L129-L129), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

69:        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

123:        (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =	// @audit-issue
```
[123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L123-L123), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

190:        (uint256 netSyOut, uint256 netSyFee) = market.swapExactPtForSy(address(this), exactPTIn, swapData);	// @audit-issue
```
[190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L190-L190), 


#### Recommendation

To avoid unnecessary variable initialization in Solidity code, regularly review and remove unused variables, use meaningful variable names, and avoid overly defensive coding. Prioritize gas efficiency and rigorous testing to maintain clean and efficient code.

### Unnecessary casting as variable is already of the same type
In Solidity, explicitly casting a variable to a type that it already represents is redundant and can lead to confusion and clutter in the code. This unnecessary casting doesn't typically consume additional gas since Solidity's optimizer often removes such redundant conversions during compilation. However, it does affect code readability and may obscure the actual intent of the code, making it harder for developers to understand and maintain. Ensuring that casting is used only when necessary helps maintain clean, clear, and efficient code.

```solidity
Path: ./contracts/helpers/BaseConnector.sol

96:            IERC20(token).safeTransfer(address(accountingManager), newAmount);	// @audit-issue: Variable `accountingManager` is converted to `address` from type `address`.
```
[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L96-L96), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

102:        IERC20(pool).forceApprove(address(gauge), liquidity);	// @audit-issue: Variable `gauge` is converted to `address` from type `address`.
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

65:        IRewards(rewardContract).claim(address(market), address(this), true);	// @audit-issue: Variable `market` is converted to `address` from type `address`.
```
[65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L65-L65), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

58:        _updateTokenInRegistry(address(AURA));	// @audit-issue: Variable `AURA` is converted to `address` from type `address`.
```
[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L58-L58), 


#### Recommendation

Review your Solidity code for instances of unnecessary casting where variables are cast to their own type. Remove these redundant casts to enhance code clarity and maintainability. When writing new code, ensure that casting is only applied when changing a variable's type is genuinely needed. This practice helps in keeping the codebase straightforward and understandable, reducing potential confusion and errors associated with misinterpreting the variable types.

### Shortcircuit rules can be be used to optimize some gas usage
Some conditions may be reordered to save an SLOAD (2100 gas), as we avoid reading state variables when the first part of the condition fails (with `&&`), or succeeds (with `||`).

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

233:            depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime	// @audit-issue: Control with `depositQueue` can be done after all non state variable/function call controls.

269:                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI	// @audit-issue: Control with `depositWaitingTime` can be done after all non state variable/function call controls.

288:        if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {	// @audit-issue: Control with `vaultId` can be done after all non state variable/function call controls.

339:            withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime	// @audit-issue: Control with `withdrawQueue` can be done after all non state variable/function call controls.

408:                && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp	// @audit-issue: Control with `withdrawWaitingTime` can be done after all non state variable/function call controls.
```
[233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L233-L233), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L269-L269), [288](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L288-L288), [339](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L339-L339), [408](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L408-L408), 


```solidity
Path: ./contracts/governance/Keepers.sol

64:        require(_threshold <= numOwners && _threshold > 1);	// @audit-issue: Control with `numOwners` can be done after all non state variable/function call controls.
```
[64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L64-L64), 


#### Recommendation

Review your Solidity contracts for conditional statements that use `&&` and `||` operators. Prioritize conditions that are less gas-intensive or have a higher likelihood of determining the outcome of the entire expression. For instance, if a condition involves an `SLOAD` operation and another is a simple variable comparison, evaluate the simpler condition first:
Before optimization:
```solidity
if (contractStateVariable > value && isEligible(msg.sender)) {
    // Execution logic
}

After optimization:
```solidity
if (isEligible(msg.sender) && contractStateVariable > value) {
    // Execution logic
}

This rearrangement ensures that if `isEligible(msg.sender)` returns false, the contract avoids the gas cost associated with reading `contractStateVariable` from storage. Apply this principle across your contract's logic where applicable, especially in functions called frequently or in gas-sensitive contexts. Testing remains crucial; ensure that the reordering of conditions does not alter the intended logic or outcomes of your contract.

### Same cast is done multiple times
It's cheaper to do it once, and store the result to a variable.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

125:        require(address(_valueOracle) != address(0));	// @audit-issue: Same casting also done in line(s): `[127]`.
```
[125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L125-L125), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

94:            balanceOut1 = address(_request.from).balance;	// @audit-issue: Same casting also done in line(s): `[87]`.

171:            ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId));	// @audit-issue: Same casting also done in line(s): `[182]`.
```
[94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L94-L94), [171](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L171-L171), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

97:        if (address(oracle) == address(0)) {	// @audit-issue: Same casting also done in line(s): `[106, 100, 103]`.
```
[97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L97-L97), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

81:        int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));	// @audit-issue: Same casting also done in line(s): `[82]`.
```
[81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81-L81), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

42:            _approveOperations(params.collateralToken, address(morphoBlue), amount);	// @audit-issue: Same casting also done in line(s): `[38]`.
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L42-L42), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

56:        _approveOperations(IPool(data.pool).token1(), address(aerodromeRouter), data.amount1);	// @audit-issue: Same casting also done in line(s): `[55]`.
```
[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L56-L56), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

56:            _updateTokenInRegistry(address(token));	// @audit-issue: Same casting also done in line(s): `[47]`.

60:        emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount);	// @audit-issue: Same casting also done in line(s): `[47]`.

97:        emit Repay(address(pool), sharesToRepay);	// @audit-issue: Same casting also done in line(s): `[94]`.
```
[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L56-L56), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L60-L60), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L97-L97), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

44:        _approveOperations(p.tokenA, address(router), p.amountA);	// @audit-issue: Same casting also done in line(s): `[45]`.
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L44-L44), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

45:        _approveOperations(p.token0, address(positionManager), p.amount0Desired);	// @audit-issue: Same casting also done in line(s): `[46]`.

90:        _approveOperations(token0, address(positionManager), p.amount0Desired);	// @audit-issue: Same casting also done in line(s): `[91]`.
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L45-L45), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L90-L90), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

66:        emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);	// @audit-issue: Same casting also done in line(s): `[61]`.

83:        _approveOperations(collateral, address(zapContract), amountIn);	// @audit-issue: Same casting also done in line(s): `[85]`.
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L66-L66), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L83-L83), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

114:        IERC20(address(_SY)).safeTransfer(address(market), SYamount);	// @audit-issue: Same casting also done in line(s): `[115, 118]`.

195:        emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY);	// @audit-issue: Same casting also done in line(s): `[189]`.

204:        IERC20(address(market)).safeTransfer(address(market), amount);	// @audit-issue: Same casting also done in line(s): `[205, 207]`.

221:        IERC20(address(SY)).safeTransfer(address(SY), _amount);	// @audit-issue: Same casting also done in line(s): `[222]`.
```
[114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L114-L114), [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L195-L195), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L204-L204), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L221-L221), 


#### Recommendation

Identify instances in your Solidity contracts where the same value is cast to another type multiple times. Refactor these operations by performing the cast once and storing the result in a local variable. Use this variable for all subsequent operations requiring the cast value.

### Conditions Can Be Optimized
The way conditional statements are written can significantly impact the contract's gas efficiency, readability, and overall maintainability. Complex or poorly structured conditions can lead to increased execution costs and potential security vulnerabilities. There is often an opportunity to simplify and streamline these statements. By optimizing conditional logic, developers can create smarter contracts that are not only more cost-effective in terms of gas usage but also more secure and easier to understand and maintain. This optimization plays a crucial role in enhancing the performance and reliability of smart contracts on the Ethereum blockchain.

`require(bool_var)` is better than `require(bool_var == True)`.


```solidity
Path: ./contracts/accountingManager/Registry.sol

33:        if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

40:        if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

47:        if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

251:            if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L33-L33), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L40-L40), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L47-L47), [251](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L251-L251), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

335:        if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {	// @audit-issue

361:        require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

371:        require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

397:        if (currentWithdrawGroup.isFullfilled == false) {	// @audit-issue

619:            currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true	// @audit-issue
```
[335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L335-L335), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361-L361), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371-L371), [397](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L397-L397), [619](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L619-L619), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

35:        require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER");	// @audit-issue

153:        if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();	// @audit-issue

154:        if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId();	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35-L35), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153-L153), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L154-L154), 


#### Recommendation

Optimize conditional statements in Solidity for better gas efficiency, readability, and maintainability. Simplify logic where possible and consider the cost implications of each condition to create more effective and secure smart contracts.

### `address(this)` should be cached
Cacheing saves gas when compared to repeating the calculation at each point it is used in the contract.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

557:                address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data	// @audit-issue: `adress(this)` also used on line(s): [559, 555]
```
[557](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L557-L557), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

144:            registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);	// @audit-issue: `adress(this)` also used on line(s): [141]

182:            uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue: `adress(this)` also used on line(s): [180]
```
[144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L144-L144), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L182-L182), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

126:            vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true	// @audit-issue: `adress(this)` also used on line(s): [123]

138:        IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));	// @audit-issue: `adress(this)` also used on line(s): [143]
```
[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L126-L126), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L138-L138), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

47:            vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false	// @audit-issue: `adress(this)` also used on line(s): [43, 39]

63:            morphoBlue.withdrawCollateral(params, amount, address(this), address(this));	// @audit-issue: `adress(this)` also used on line(s): [68, 65, 61]
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L47-L47), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L63-L63), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

60:                stakingAmount = IERC20(lpAddress).balanceOf(address(this));	// @audit-issue: `adress(this)` also used on line(s): [67, 54]

84:                uint16(withdrawRequest.poolId), withdrawRequest.routerAmount, address(this)	// @audit-issue: `adress(this)` also used on line(s): [88, 91, 89]
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L60-L60), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L84-L84), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

25:        address c = ICreditFacadeV3(facade).openCreditAccount(address(this), new MultiCall[](0), ref);	// @audit-issue: `adress(this)` also used on line(s): [28]
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L25-L25), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

62:                vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true	// @audit-issue: `adress(this)` also used on line(s): [65]

118:            depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));	// @audit-issue: `adress(this)` also used on line(s): [119, 117]

135:                    + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0	// @audit-issue: `adress(this)` also used on line(s): [134]
```
[62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L62-L62), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L118-L118), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L135-L135), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

54:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue: `adress(this)` also used on line(s): [65]

89:            address(this),	// @audit-issue: `adress(this)` also used on line(s): [92, 80]
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L54-L54), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

34:            vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false	// @audit-issue: `adress(this)` also used on line(s): [31]

50:        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);	// @audit-issue: `adress(this)` also used on line(s): [55]

112:                (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset);	// @audit-issue: `adress(this)` also used on line(s): [96]
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L34-L34), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L50-L50), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L112-L112), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

44:            registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));	// @audit-issue: `adress(this)` also used on line(s): [50, 53]

76:        pool.removeCollateral(withdrawAmount, address(this));	// @audit-issue: `adress(this)` also used on line(s): [72, 69]

95:        IFraxPair(pool).repayAsset(sharesToRepay, address(this));	// @audit-issue: `adress(this)` also used on line(s): [89]

125:        uint256 _collateralAmount = _fraxlendPair.userCollateralBalance(address(this));	// @audit-issue: `adress(this)` also used on line(s): [122]

153:        uint256 collateralAmount = pool.userCollateralBalance(address(this));	// @audit-issue: `adress(this)` also used on line(s): [154]
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L44-L44), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L76-L76), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L95-L95), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L125-L125), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L153-L153), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

47:            p.tokenA, p.tokenB, p.amountA, p.amountB, p.minAmountA, p.minAmountB, address(this), p.deadline	// @audit-issue: `adress(this)` also used on line(s): [53]

73:            p.tokenA, p.tokenB, p.amountLiquidty, p.minAmountA, p.minAmountB, address(this), p.deadline	// @audit-issue: `adress(this)` also used on line(s): [77, 80]
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L47-L47), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L73-L73), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

42:            registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));	// @audit-issue: `adress(this)` also used on line(s): [43]
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L42-L42), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

83:            address(this), // sender	// @audit-issue: `adress(this)` also used on line(s): [96, 104, 102, 84]

149:                    registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(p.poolId)),	// @audit-issue: `adress(this)` also used on line(s): [133, 132]

181:        return IERC20(pool.pool).balanceOf(address(this)) + auraShares;	// @audit-issue: `adress(this)` also used on line(s): [178]
```
[83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L83-L83), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L149-L149), [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L181-L181), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

86:                BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");	// @audit-issue: `adress(this)` also used on line(s): [92]
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L86-L86), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

48:        IPool(pool).supply(supplyToken, amount, address(this), 0);	// @audit-issue: `adress(this)` also used on line(s): [50]

67:        if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {	// @audit-issue: `adress(this)` also used on line(s): [72, 70]

101:        IPool(pool).withdraw(_collateral, _collateralAmount, address(this));	// @audit-issue: `adress(this)` also used on line(s): [108, 103]
```
[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L48-L48), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L67-L67), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L101-L101), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

58:        bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, "");	// @audit-issue: `adress(this)` also used on line(s): [57]

73:        uint256 beforeClaimBalance = address(this).balance;	// @audit-issue: `adress(this)` also used on line(s): [77, 80]
```
[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L58-L58), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L73-L73), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

37:            if (!registry.isPositionTrustedForConnector(vaultId, positionId, address(this))) {	// @audit-issue: `adress(this)` also used on line(s): [35]

62:        zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));	// @audit-issue: `adress(this)` also used on line(s): [57]

79:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue: `adress(this)` also used on line(s): [77, 84]

114:        borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this));	// @audit-issue: `adress(this)` also used on line(s): [106, 107, 117]

133:        borrowerOperations.closeTrove(troveManager, address(this));	// @audit-issue: `adress(this)` also used on line(s): [131]
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L37-L37), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L62-L62), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L79-L79), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L114-L114), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L133-L133), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

85:        uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);	// @audit-issue: `adress(this)` also used on line(s): [87]

222:        IPStandardizedYield(address(SY)).redeem(address(this), _amount, _underlyingToken, 1, true);	// @audit-issue: `adress(this)` also used on line(s): [226]

274:            uint256 PTAmount = _PT.balanceOf(address(this));	// @audit-issue: `adress(this)` also used on line(s): [277, 269, 265]

307:                && market.balanceOf(address(this)) == 0	// @audit-issue: `adress(this)` also used on line(s): [306]
```
[85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L85-L85), [222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L222-L222), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L274-L274), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L307-L307), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

50:        (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));	// @audit-issue: `adress(this)` also used on line(s): [53]

73:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true	// @audit-issue: `adress(this)` also used on line(s): [65]
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L50-L50), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L73-L73), 


#### Recommendation

To enhance gas efficiency, cache the contract's address by storing `address(this)` in a state variable at the point of contract deployment or initialization. Use this cached address throughout the contract instead of repeatedly calling `address(this)`. This practice reduces the gas cost associated with multiple computations of the contract's address, leading to more efficient contract execution, especially in scenarios with frequent usage of the contract's address.

### Superfluous event fields
`block.number` and `block.timestamp` are added to the event information by default, so adding them manually will waste additional gas.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

216:        emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);	// @audit-issue

242:            emit CalculateDeposit(
243:                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount	// @audit-issue
244:            );

274:            emit ExecuteDeposit(
275:                firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount	// @audit-issue
276:            );

314:        emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);	// @audit-issue

349:            emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);	// @audit-issue

429:            emit ExecuteWithdraw(
430:                firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp	// @audit-issue
431:            );

485:        emit RecordProfit(
486:            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp	// @audit-issue
487:        );

496:            emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);	// @audit-issue
```
[216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L216-L216), [243](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L242-L244), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L274-L276), [314](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L314-L314), [349](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L349-L349), [430](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L429-L431), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L485-L487), [496](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L496-L496), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

60:        emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp);	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L60-L60), 


#### Recommendation

Review your smart contracts to identify and remove `block.number` and `block.timestamp` from the parameters of emitted events. Instead of manually adding these fields, rely on the Ethereum blockchain's inherent inclusion of this information within the block context. Simplify your event definitions to include only the essential data specific to the event's purpose, excluding universally available block metadata.

### It is a waste of GAS to emit variable literals
Emitting variable literals (true, false, address(0), 1 etc...) in events is inefficient, as it consumes extra gas without providing added value. These literals are fixed values that can be accessed or hardcoded elsewhere in the smart contract or application, making their inclusion in events redundant and an unnecessary drain on resources during transaction execution.

```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

59:        emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);	// @audit-issue
```
[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59-L59), 


#### Recommendation

Refrain from including fixed variable literals as parameters in your Solidity contract events. Evaluate your event emissions and remove literals that do not provide dynamic information about contract state or actions. For instance, instead of emitting an event with a `true` literal to indicate success, consider naming the event in a way that inherently indicates success or failure, such as `ActionSuccessful()`:
```solidity
// Before optimization
event ActionTaken(bool success);

// After optimization
event ActionSuccessful();
event ActionFailed();
```


### `event` Declared But Not Emitted
An event within the contract is declared but not utilized in any of the contract's functions or operations. Having unused event declarations can consume unnecessary space and may lead to misunderstandings for developers or users expecting this event as part of the contract's functionality.


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

12:    event ManagementFeeReceived(address indexed token, uint256 amount);	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L12-L12), 


#### Recommendation


Consider removing the unused event declaration to optimize the contract and enhance clarity. If there is an intent for this event to be part of certain operations, ensure it is emitted appropriately. Otherwise, for the sake of clean and efficient code, it is advisable to remove any unused declarations.


### Revert String Size Optimization
Shortening the revert strings to fit within 32 bytes will decrease deployment time and decrease runtime Gas when the revert condition is met.

Revert strings that are longer than 32 bytes require at least one additional `mstore`, along with additional overhead to calculate memory offset, etc.



```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

25:        require(isEligibleToUse[msg.sender], "NoyaSwapHandler: Not eligible to use");	// @audit-issue: String length is `36`
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L25-L25), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

35:        require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER");	// @audit-issue: String length is `34`

84:        require(verifySwapData(_request), "LifiImplementation: INVALID_SWAP_DATA");	// @audit-issue: String length is `37`
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35-L35), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L84-L84), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

82:                require(success, "BalancerFlashLoan: Flash loan failed");	// @audit-issue: String length is `36`

92:            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");	// @audit-issue: String length is `42`
```
[82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L82-L82), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92), 


#### Recommendation


To optimize Gas usage in your Solidity contract, it is recommended to keep revert strings as short as possible and to ensure that they fit within 32 bytes. It is possible to use abbreviations or simplified error messages to keep the string length short. Doing so can reduce the amount of Gas used during deployment and runtime when the revert condition is met.


### Custom Errors in Solidity for Gas Efficiency
Starting from Solidity version 0.8.4, the language introduced a feature known as "custom errors". These custom errors provide a way for developers to define more descriptive and semantically meaningful error conditions without relying on string messages. Prior to this version, developers often used the `require` statement with string error messages to handle specific conditions or validations. However, every unique string used as a revert reason consumes gas, making transactions more expensive.

Custom errors, on the other hand, are identified by their name and the types of their parameters only, and they do not have the overhead of string storage. This means that, when using custom errors instead of `require` statements with string messages, the gas consumption can be significantly reduced, leading to more gas-efficient contracts.

```solidity
Path: ./contracts/accountingManager/Registry.sol

67:        require(_governer != address(0));	// @audit-issue

68:        require(_maintainer != address(0));	// @audit-issue

69:        require(_emergency != address(0));	// @audit-issue

80:        require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);	// @audit-issue

120:        require(_governer != address(0));	// @audit-issue

121:        require(_accountingManager != address(0));	// @audit-issue

122:        require(_baseToken != address(0));	// @audit-issue

123:        require(_maintainer != address(0));	// @audit-issue

124:        require(_keeperContract != address(0));	// @audit-issue

125:        require(_watcher != address(0));	// @audit-issue

167:        require(_governer != address(0));	// @audit-issue

168:        require(_maintainer != address(0));	// @audit-issue

169:        require(_keeperContract != address(0));	// @audit-issue

170:        require(_watcher != address(0));	// @audit-issue
```
[67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L67-L67), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L68-L68), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L69-L69), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L80-L80), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L120-L120), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L121-L121), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L122-L122), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L123-L123), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L124-L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L125-L125), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L167-L167), [168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L168-L168), [169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L169-L169), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L170-L170), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

15:        require(_accountingManager != address(0));	// @audit-issue

16:        require(_baseToken != address(0));	// @audit-issue

17:        require(_receiver != address(0));	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L17-L17), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

106:        require(p._baseTokenAddress != address(0));	// @audit-issue

107:        require(p._valueOracle != address(0));	// @audit-issue

108:        require(p._withdrawFeeReceiver != address(0));	// @audit-issue

109:        require(p._performanceFeeReceiver != address(0));	// @audit-issue

110:        require(p._managementFeeReceiver != address(0));	// @audit-issue

125:        require(address(_valueOracle) != address(0));	// @audit-issue

140:        require(_withdrawFeeReceiver != address(0));	// @audit-issue

141:        require(_performanceFeeReceiver != address(0));	// @audit-issue

142:        require(_managementFeeReceiver != address(0));	// @audit-issue

361:        require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

371:        require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

686:            require(success, "Transfer failed.");
```
[106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L106-L106), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L107-L107), [108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L108-L108), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L109-L109), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L110-L110), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L125-L125), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L140-L140), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L141-L141), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L142-L142), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361-L361), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371-L371), [684](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L686-L686), 


```solidity
Path: ./contracts/governance/Keepers.sol

28:        require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);	// @audit-issue

53:        require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);	// @audit-issue

64:        require(_threshold <= numOwners && _threshold > 1);	// @audit-issue

94:        require(isOwner[msg.sender], "Not an owner");	// @audit-issue

95:        require(sigR.length == threshold, "Not enough signatures");	// @audit-issue

96:        require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");	// @audit-issue

97:        require(executor == msg.sender, "Invalid executor");	// @audit-issue

98:        require(block.timestamp <= deadline, "Transaction expired");	// @audit-issue

106:                require(recovered > lastAdd && isOwner[recovered]);

117:        require(success, "Transaction execution reverted.");	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L28-L28), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L64-L64), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L94-L94), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L95-L95), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L96-L96), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L97-L97), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L98-L98), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L106-L106), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L117-L117), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

22:        require(address(_registry) != address(0));	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L22-L22), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

25:        require(isEligibleToUse[msg.sender], "NoyaSwapHandler: Not eligible to use");	// @audit-issue

41:        require(_valueOracle != address(0));	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L25-L25), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L41-L41), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

35:        require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER");	// @audit-issue

84:        require(verifySwapData(_request), "LifiImplementation: INVALID_SWAP_DATA");	// @audit-issue

196:            require(success, "Transfer failed.");
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35-L35), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L84-L84), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L196-L196), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

30:        require(address(_registry) != address(0));	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L30-L30), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

50:        require(pool != address(0), "pool doesn't exist");	// @audit-issue
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L50-L50), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

47:        require(_reg != address(0));	// @audit-issue
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L47-L47), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

41:        require(lzHelperAddress != address(0));	// @audit-issue

53:        require(omniChainManager != address(0));	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L41-L41), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L53-L53), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

52:        require(lzHelperAddress != address(0));	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L52-L52), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

37:        require(_lzHelper != address(0));	// @audit-issue

47:        require(destinationAddress != address(0));	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L37-L37), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L47-L47), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

46:        require(_mav != address(0));	// @audit-issue

47:        require(_veMav != address(0));	// @audit-issue

48:        require(mr != address(0));	// @audit-issue

49:        require(pi != address(0));	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L46-L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L47-L47), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L48-L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L49-L49), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

24:        require(MB != address(0));	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

22:        require(MC != address(0));	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

36:        require(lpStacking != address(0));	// @audit-issue

37:        require(_stargateRouter != address(0));	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L36-L36), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

18:        require(SR != address(0));	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

43:        require(_router != address(0));	// @audit-issue
```
[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L43-L43), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

37:        require(_router != address(0));	// @audit-issue

38:        require(_factory != address(0));	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L37-L37), [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L38-L38), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

45:        require(_balancerVault != address(0));	// @audit-issue

46:        require(bal != address(0));	// @audit-issue

47:        require(aura != address(0));	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L45-L45), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L46-L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L47-L47), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

25:        require(_balancerVault != address(0));	// @audit-issue

26:        require(address(_registry) != address(0));	// @audit-issue

61:        require(msg.sender == address(vault));	// @audit-issue

82:                require(success, "BalancerFlashLoan: Flash loan failed");

92:            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L26-L26), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L61-L61), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L82-L82), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

21:        require(_SNXCoreProxy != address(0));	// @audit-issue
```
[21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L21-L21), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

36:        require(_pool != address(0));	// @audit-issue

37:        require(_poolBaseToken != address(0));	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L36-L36), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

23:        require(_lido != address(0));	// @audit-issue

24:        require(_lidoW != address(0));	// @audit-issue

25:        require(_steth != address(0));	// @audit-issue

26:        require(w != address(0));	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L23-L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L24-L24), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L26-L26), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

60:        require(_pendleMarketDepositHelper != address(0));	// @audit-issue

61:        require(_pendleRouter != address(0));	// @audit-issue

62:        require(SR != address(0));	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L60-L60), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L61-L61), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L62-L62), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

24:        require(_depositWithdrawalProxy != address(0));	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

52:        require(_convexBooster != address(0));	// @audit-issue

53:        require(cvx != address(0));	// @audit-issue

54:        require(crv != address(0));	// @audit-issue

55:        require(prisma != address(0));	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L52-L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L53-L53), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L54-L54), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L55-L55), 


#### Recommendation


It is recommended to use custom errors instead of revert strings to reduce gas costs, especially during contract deployment. Custom errors can be defined using the error keyword and can include dynamic information.

### Avoid repeating computations
In Solidity development, repeating the same computations within a contract can lead to unnecessary gas consumption and reduce the contract's efficiency. This is particularly relevant in functions that are called frequently or involve complex calculations. Repeating computations not only wastes computational resources but also increases the cost of executing transactions. By identifying and eliminating redundant calculations, developers can optimize contract performance, reduce gas costs, and improve overall execution speed.

```solidity
Path: ./contracts/accountingManager/Registry.sol

349:            if (positionIndex < vault.holdingPositions.length - 1) {	// @audit-issue: Same binary operation statement in line(s) between: ['350:350']
```
[349](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L349-L349), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

528:            preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours	// @audit-issue: Same binary operation statement in line(s) between: ['529:529']

584:        if (tvl + totalWithdrawnAmount > totalDepositedAmount) {	// @audit-issue: Same binary operation statement in line(s) between: ['585:585']

603:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue: Same binary operation statement in line(s) between: ['608:608']
```
[528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528-L528), [584](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L584-L584), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

178:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue: Same binary operation statement in line(s) between: ['189:189']
```
[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

86:        if (_request.outputToken == address(0)) {	// @audit-issue: Same binary operation statement in line(s) between: ['93:93']
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L86-L86), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

97:        if (address(oracle) == address(0)) {	// @audit-issue: Same binary operation statement in line(s) between: ['100:100', '103:103', '106:106']
```
[97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L97-L97), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

78:        if (approvalToken != address(0)) {	// @audit-issue: Same binary operation statement in line(s) between: ['82:82']
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L78-L78), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

46:        if (collateralAmount > 0) {	// @audit-issue: Same binary operation statement in line(s) between: ['52:52', '55:55']
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L46-L46), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

74:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue: Same binary operation statement in line(s) between: ['84:84', '89:89']
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), 


#### Recommendation

Review your Solidity contracts to identify any computations that are performed multiple times with the same inputs. Cache the results of these computations in local variables and reuse them within the function or across function calls if the state remains unchanged.

### Unused State Variables
There are state variables which are declared but not used in any function. This might increase the contract's gas usage unnecessarily.

```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

24:    uint32 constant TVL_UPDATE = 1;	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

17:    uint256 public constant SNX_POOL_POSITION_ID = 2;	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L17-L17), 


#### Recommendation

To optimize your contract's gas usage, remove any state variables that are declared but not used in any function. Unnecessary state variables can increase gas costs and should be eliminated during code review.

### Unused `struct`s
Note that there may be cases where a struct superficially appears to be used, but this is only because there are multiple definitions of the struct in different files. In such cases, the struct definition should be moved into a separate file. The instances below are the unused definitions.

```solidity
Path: ./contracts/connectors/FraxConnector.sol

7:struct FraxPoolInfo {	// @audit-issue
8:    address collateralContract;
9:    address assetContract;
10:    bool isActive;
11:}

13:struct FraxBorrowRequest {	// @audit-issue
14:    address poolAddress;
15:    uint256 amount;
16:}
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L7-L11), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L13-L16), 


#### Recommendation

Identify and remove any unused `struct` definitions from your Solidity contracts. If a `struct` is defined multiple times across different files, centralize its definition in a single file and import it wherever required. This approach reduces code redundancy, ensures consistency in data structures, and helps maintain a clean and efficient codebase. Regularly auditing your contracts for unused or duplicated code elements like `structs` is a good practice for optimal contract maintenance and development.

### Unused Modifier
Modifier is declared in the project, but never used.

```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

53:    modifier onlyEmergencyOrWatcher() {	// @audit-issue

85:    modifier onlyGovernance() {	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L53-L53), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L85-L85), 


#### Recommendation

Remove redundant code..

### Unused `error` definition
Note that there may be cases where an error superficially appears to be used, but this is only because there are multiple definitions of the error in different files. In such cases, the error definition should be moved into a separate file. The instances below are the unused definitions.


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

22:    error InvalidPayload();	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L22-L22), 


#### Recommendation

Unused `error` definitions should be removed from the contract, and if needed, consolidated into a separate file to avoid duplication.

### Using Prefix Operators Costs Less Gas Than Postfix Operators in Loops
Conditions can be optimized issues in Solidity refer to situations where smart contract developers write conditional statements that can be simplified or optimized for better gas efficiency, readability, and maintainability. Optimizing conditions can lead to more cost-effective and secure smart contracts.

```solidity
Path: ./contracts/accountingManager/Registry.sol

138:        for (uint256 i = 0; i < _trustedTokens.length; i++) {	// @audit-issue

194:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {	// @audit-issue

214:        for (uint256 i = 0; i < _tokens.length; i++) {	// @audit-issue

253:            for (uint256 i = 0; i < usingTokens.length; i++) {	// @audit-issue

274:        for (uint256 i = 0; i < length; i++) {	// @audit-issue
```
[138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138-L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214-L214), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L253-L253), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L274-L274), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

551:        for (uint256 i = 0; i < retrieveData.length; i++) {	// @audit-issue

603:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue

608:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue
```
[551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551-L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608-L608), 


```solidity
Path: ./contracts/governance/Keepers.sol

29:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

47:                numOwnersTemp++;	// @audit-issue

50:                numOwnersTemp--;	// @audit-issue

44:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

113:            nonce++;	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29-L29), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L47-L47), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L50-L50), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44-L44), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L113-L113), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

18:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L18-L18), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

178:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

189:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

211:        for (uint256 i = 0; i < tokensIn.length; i++) {	// @audit-issue
```
[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211-L211), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

37:        for (uint256 i = 0; i < usersAddresses.length; i++) {	// @audit-issue

152:                i++;	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), [152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L152-L152), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

41:        for (uint256 i = 0; i < baseCurrencies.length; i++) {	// @audit-issue

55:        for (uint256 i = 0; i < oracle.length; i++) {	// @audit-issue

88:        for (uint256 i = 0; i < sources.length; i++) {	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

83:            timeWeightedAverageTick--;	// @audit-issue
```
[83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L83-L83), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

74:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

140:        for (uint256 i = 0; i < earnedInfo.length; i++) {	// @audit-issue
```
[140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

69:        for (uint256 i = 0; i < calls.length; i++) {	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

116:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue

132:        for (uint256 i = 0; i < assetsS.length; i++) {	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L116-L116), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

102:        for (uint256 i = 0; i < tokenIds.length; i++) {	// @audit-issue
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

54:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue

77:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54-L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

74:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

79:            for (uint256 i = 0; i < destinationConnector.length; i++) {	// @audit-issue

84:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

89:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

244:        for (uint256 i = 0; i < rewardTokens.length; i++) {	// @audit-issue
```
[244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

113:        for (uint256 i = 0; i < markets.length; i++) {	// @audit-issue
```
[113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L113-L113), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

222:        for (uint256 i = 0; i < gauges.length; i++) {	// @audit-issue

234:        for (uint256 i = 0; i < pools.length; i++) {	// @audit-issue

248:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue
```
[222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222-L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234-L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248-L248), 


#### Recommendation

To improve gas efficiency in your Solidity code, prefer using prefix operators (e.g., `++i` or `--i`) instead of postfix operators (e.g., `i++` or `i--`) within loops. Prefix operators typically result in lower gas costs and can contribute to more efficient contract execution.

### Optimization of Loop Control for Early Termination
The identified issue is a common inefficiency in programming related to loop control during search operations. In the current implementation, loops are designed to traverse through the entire dataset (like arrays or lists) even after the required condition has been met or the target element has been found. This lack of early termination results in unnecessary processing and can lead to increased execution times, particularly in large datasets. The issue is not about the correctness of the function but its efficiency, as continuing the loop after meeting the required condition is redundant and wastes computational resources.

```solidity
Path: ./contracts/helpers/TVLHelper.sol

44:        for (uint256 i = 0; i < positions.length; i++) {
45:            if (latestUpdateTime == 0 || positions[i].positionTimestamp < latestUpdateTime) {
46:                latestUpdateTime = positions[i].positionTimestamp;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L46), 


#### Recommendation

To optimize such functions, it is recommended to incorporate an early exit mechanism within the loop. This can be achieved by introducing a `break` statement (or an equivalent control structure) immediately after the condition is satisfied or the target element is located. This approach ensures that the loop terminates as soon as its objective is achieved, preventing further unnecessary iterations. Implementing this optimization will enhance the performance, especially in scenarios involving large data sets or resource-intensive operations, by minimizing the time and resources expended on redundant processing. This optimization strategy is applicable and beneficial across various programming languages and scenarios where loop-based search or check operations are utilized.

### Multiple accesses of a mapping/array should use a local variable cache
The instances below point to the second+ access of a value inside a mapping/array, within a function. Caching a mapping's value in a local `storage` or `calldata` variable when the value is accessed [multiple times](https://gist.github.com/IllIllI000/ec23a57daa30a8f8ca8b9681c8ccefb0), saves **~42 gas per access** due to not having to recalculate the key's keccak256 hash (Gkeccak256 - **30 gas**) and that calculation's associated stack operations. Caching an array's struct avoids recalculating the array offsets into memory/calldata

```solidity
Path: ./contracts/accountingManager/Registry.sol

118:        if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();	// @audit-issue: Same index access of variable `vaults` is used also on line(s): ['119'].

196:            emit ConnectorAdded(vaultId, _connectorAddresses[i]);	// @audit-issue: Same index access of variable `_connectorAddresses` is used also on line(s): ['195'].

460:            vaults[vaultId].emergency	// @audit-issue: Same index access of variable `vaults` is used also on line(s): ['458', '456', '459', '457', '455'].

472:            vaults[vaultId].connectors[vaults[vaultId].accountManager].trustedTokens[token]	// @audit-issue: Same index access of variable `vaults` is used also on line(s): ['472', '473'].

517:        return (vaults[vaultId].accountManager, vaults[vaultId].baseToken);	// @audit-issue: Same index access of variable `vaults` is used also on line(s): ['517'].
```
[118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L118-L118), [196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L196-L196), [460](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L460-L460), [472](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L472-L472), [517](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L517-L517), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

186:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {	// @audit-issue: Same index access of variable `withdrawRequestsByAddress` is used also on line(s): ['187'].

237:            DepositRequest storage data = depositQueue.queue[middleTemp];	// @audit-issue: Same index access of variable `depositQueue` is used also on line(s): ['233'].

269:                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI	// @audit-issue: Same index access of variable `depositQueue` is used also on line(s): ['272'].

307:                balanceOf(msg.sender), share, withdrawRequestsByAddress[msg.sender]	// @audit-issue: Same index access of variable `withdrawRequestsByAddress` is used also on line(s): ['305'].

343:            WithdrawRequest storage data = withdrawQueue.queue[middleTemp];	// @audit-issue: Same index access of variable `withdrawQueue` is used also on line(s): ['339'].

412:            WithdrawRequest memory data = withdrawQueue.queue[firstTemp];	// @audit-issue: Same index access of variable `withdrawQueue` is used also on line(s): ['408'].

552:            if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {	// @audit-issue: Same index access of variable `retrieveData` is used also on line(s): ['557', '557', '561', '563', '564', '556'].
```
[186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186-L186), [237](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L237-L237), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L269-L269), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L307-L307), [343](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L343-L343), [412](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L412-L412), [552](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L552-L552), 


```solidity
Path: ./contracts/governance/Keepers.sol

45:            if (addOrRemove[i] && !isOwner[_owners[i]]) {	// @audit-issue: Same index access of variable `isOwner` is used also on line(s): ['48'].
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L45-L45), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30:        if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();	// @audit-issue: Same index access of variable `routes` is used also on line(s): ['30'].
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30-L30), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

75:            assetsSources[assets[i]][baseTokens[i]] = sources[i];	// @audit-issue: Same index access of variable `assets` is used also on line(s): ['76'].

75:            assetsSources[assets[i]][baseTokens[i]] = sources[i];	// @audit-issue: Same index access of variable `baseTokens` is used also on line(s): ['76'].

76:            emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);	// @audit-issue: Same index access of variable `sources` is used also on line(s): ['75'].

145:            return (assetsSources[asset][baseToken], false);	// @audit-issue: Same index access of variable `assetsSources` is used also on line(s): ['144'].

146:        } else if (assetsSources[baseToken][asset] != address(0)) {	// @audit-issue: Same index access of variable `assetsSources` is used also on line(s): ['147'].
```
[75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L76-L76), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L145-L145), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L146-L146), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

78:        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;	// @audit-issue: Same index access of variable `vaultIdToVaultInfo` is used also on line(s): ['76'].
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L78-L78), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

71:        if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {	// @audit-issue: Same index access of variable `approvedBridgeTXN` is used also on line(s): ['71'].

76:            destChainAddress[bridgeRequest.destChainId] == address(0)	// @audit-issue: Same index access of variable `destChainAddress` is used also on line(s): ['77'].
```
[71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71-L71), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L76-L76), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

74:                (address token) = abi.decode(calls[i].callData[4:], (address));	// @audit-issue: Same index access of variable `calls` is used also on line(s): ['71', '70', '70'].
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L74-L74), 


#### Recommendation

When a mapping or array value is accessed multiple times within a function, cache it in a local `storage` or `calldata` variable. This approach minimizes the gas cost by reducing the number of hash computations for mappings and offset calculations for arrays. Carefully review your functions to identify opportunities for such optimizations, especially in functions with frequent or repeated accesses to the same mapping or array element, to enhance gas efficiency in your contracts.

### State Variables That Are Used Multiple Times In a Function Should Be Cached In Stack Variables
When performing multiple operations on a state variable in a function, it is recommended to cache it first. Either multiple reads or multiple writes to a state variable can save gas by caching it on the stack. Caching of a state variable replaces each Gwarmaccess (100 gas) with a much cheaper stack read. Other less obvious fixes/optimizations include having local memory caches of state variable structs, or having local caches of state variable contracts/addresses. Saves 100 gas per instance.


```solidity
Path: ./contracts/accountingManager/Registry.sol

118:        if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();	// @audit-issue: State variable `vaults` is used also on line(s): ['119'].

136:        vault.connectors[vault.accountManager].enabled = true;	// @audit-issue: State variable `vault` is used also on line(s): ['139'].

275:            if (vault.holdingPositions[i].positionId == _positionId) {	// @audit-issue: State variable `vault` is used also on line(s): ['273'].

349:            if (positionIndex < vault.holdingPositions.length - 1) {	// @audit-issue: State variable `vault` is used also on line(s): ['350'].

353:                        vault.holdingPositions[positionIndex].calculatorConnector,	// @audit-issue: State variable `vault` is used also on line(s): ['354', '350', '349', '350', '355'].

354:                        vault.holdingPositions[positionIndex].positionId,	// @audit-issue: State variable `vault` is used also on line(s): ['353', '355'].

460:            vaults[vaultId].emergency	// @audit-issue: State variable `vaults` is used also on line(s): ['458', '456', '459', '457', '455'].

472:            vaults[vaultId].connectors[vaults[vaultId].accountManager].trustedTokens[token]	// @audit-issue: State variable `vaults` is used also on line(s): ['473'].

472:            vaults[vaultId].connectors[vaults[vaultId].accountManager].trustedTokens[token]	// @audit-issue: State variable `vaults` is used also on line(s): ['472', '473'].

517:        return (vaults[vaultId].accountManager, vaults[vaultId].baseToken);	// @audit-issue: State variable `vaults` is used also on line(s): ['517'].
```
[118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L118-L118), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L136-L136), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L275-L275), [349](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L349-L349), [353](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L353-L353), [354](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L354-L354), [460](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L460-L460), [472](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L472-L472), [472](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L472-L472), [517](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L517-L517), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

186:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {	// @audit-issue: State variable `withdrawRequestsByAddress` is used also on line(s): ['187'].

216:        emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);	// @audit-issue: State variable `depositQueue` is used also on line(s): ['215'].

237:            DepositRequest storage data = depositQueue.queue[middleTemp];	// @audit-issue: State variable `depositQueue` is used also on line(s): ['233'].

239:            uint256 shares = previewDeposit(data.amount);	// @audit-issue: State variable `data` is used also on line(s): ['243', '243'].

269:                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI	// @audit-issue: State variable `depositQueue` is used also on line(s): ['272'].

307:                balanceOf(msg.sender), share, withdrawRequestsByAddress[msg.sender]	// @audit-issue: State variable `withdrawRequestsByAddress` is used also on line(s): ['305'].

313:        withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);	// @audit-issue: State variable `withdrawQueue` is used also on line(s): ['314'].

343:            WithdrawRequest storage data = withdrawQueue.queue[middleTemp];	// @audit-issue: State variable `withdrawQueue` is used also on line(s): ['339'].

344:            uint256 assets = previewRedeem(data.shares);	// @audit-issue: State variable `data` is used also on line(s): ['348', '349'].

381:            currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;	// @audit-issue: State variable `currentWithdrawGroup` is used also on line(s): ['374', '388', '380', '385'].

407:            currentWithdrawGroup.lastId > firstTemp	// @audit-issue: State variable `currentWithdrawGroup` is used also on line(s): ['443'].

412:            WithdrawRequest memory data = withdrawQueue.queue[firstTemp];	// @audit-issue: State variable `withdrawQueue` is used also on line(s): ['408'].

457:            if (newMiddle > depositQueue.middle || newMiddle < depositQueue.first) {	// @audit-issue: State variable `depositQueue` is used also on line(s): ['455'].

464:            if (newMiddle > withdrawQueue.middle || newMiddle < withdrawQueue.first || currentWithdrawGroup.isStarted) {	// @audit-issue: State variable `withdrawQueue` is used also on line(s): ['462'].

486:            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp	// @audit-issue: State variable `storedProfitForFee` is used also on line(s): ['484', '479'].

484:            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);	// @audit-issue: State variable `totalProfitCalculated` is used also on line(s): ['486', '479'].

495:        if (currentProfit < storedProfitForFee) {	// @audit-issue: State variable `storedProfitForFee` is used also on line(s): ['496'].

509:        uint256 timePassed = block.timestamp - lastFeeDistributionTime;	// @audit-issue: State variable `lastFeeDistributionTime` is used also on line(s): ['506'].

514:        uint256 currentFeeShares = balanceOf(managementFeeReceiver) + balanceOf(performanceFeeReceiver)	// @audit-issue: State variable `managementFeeReceiver` is used also on line(s): ['519'].

534:        _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);	// @audit-issue: State variable `preformanceFeeSharesWaitingForDistribution` is used also on line(s): ['538', '528'].

528:            preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours	// @audit-issue: State variable `profitStoredTime` is used also on line(s): ['529'].

584:        if (tvl + totalWithdrawnAmount > totalDepositedAmount) {	// @audit-issue: State variable `totalWithdrawnAmount` is used also on line(s): ['585'].

584:        if (tvl + totalWithdrawnAmount > totalDepositedAmount) {	// @audit-issue: State variable `totalDepositedAmount` is used also on line(s): ['585'].

624:        return currentWithdrawGroup.totalCBAmount - availableAssets;	// @audit-issue: State variable `currentWithdrawGroup` is used also on line(s): ['620'].
```
[186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186-L186), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L216-L216), [237](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L237-L237), [239](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L239-L239), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L269-L269), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L307-L307), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L313-L313), [343](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L343-L343), [344](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L344-L344), [381](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L381-L381), [407](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L407-L407), [412](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L412-L412), [457](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L457-L457), [464](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L464-L464), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L486-L486), [484](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L484-L484), [495](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L495-L495), [509](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L509-L509), [514](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L514-L514), [534](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L534-L534), [528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528-L528), [584](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L584-L584), [584](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L584-L584), [624](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L624-L624), 


```solidity
Path: ./contracts/governance/Keepers.sol

53:        require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);	// @audit-issue: State variable `threshold` is used also on line(s): ['53'].

45:            if (addOrRemove[i] && !isOwner[_owners[i]]) {	// @audit-issue: State variable `isOwner` is used also on line(s): ['48'].

95:        require(sigR.length == threshold, "Not enough signatures");	// @audit-issue: State variable `threshold` is used also on line(s): ['104'].
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L53-L53), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L45-L45), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L95-L95), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

91:            (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: State variable `vaultId` is used also on line(s): ['98', '89'].

141:            registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));	// @audit-issue: State variable `vaultId` is used also on line(s): ['136', '144'].
```
[91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L91-L91), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L141-L141), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30:        if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();	// @audit-issue: State variable `routes` is used also on line(s): ['30'].
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30-L30), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

70:        secondsAgos[0] = period;	// @audit-issue: State variable `period` is used also on line(s): ['81', '82'].
```
[70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L70-L70), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

145:            return (assetsSources[asset][baseToken], false);	// @audit-issue: State variable `assetsSources` is used also on line(s): ['144'].

146:        } else if (assetsSources[baseToken][asset] != address(0)) {	// @audit-issue: State variable `assetsSources` is used also on line(s): ['147'].
```
[145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L145-L145), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L146-L146), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

78:        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;	// @audit-issue: State variable `vaultIdToVaultInfo` is used also on line(s): ['76'].
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L78-L78), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

71:        if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {	// @audit-issue: State variable `approvedBridgeTXN` is used also on line(s): ['71'].

76:            destChainAddress[bridgeRequest.destChainId] == address(0)	// @audit-issue: State variable `destChainAddress` is used also on line(s): ['77'].
```
[71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71-L71), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L76-L76), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

21:        return TVLHelper.getTVL(vaultId, registry, baseToken);	// @audit-issue: State variable `vaultId` is used also on line(s): ['20'].
```
[21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L21-L21), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

69:        _updateTokenInRegistry(mav);	// @audit-issue: State variable `mav` is used also on line(s): ['66'].

68:        IveMAV(veMav).stake(amount, duration, doDelegation);	// @audit-issue: State variable `veMav` is used also on line(s): ['70', '66'].

82:        _updateTokenInRegistry(veMav);	// @audit-issue: State variable `veMav` is used also on line(s): ['80'].

93:        _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); // TODO: check token A is eth	// @audit-issue: State variable `maverickRouter` is used also on line(s): ['94', '98'].

122:        IMaverickRouter(maverickRouter).removeLiquidity(	// @audit-issue: State variable `maverickRouter` is used also on line(s): ['120', '121'].
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L69-L69), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L68-L68), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L82-L82), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L93-L93), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L122-L122), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

34:            vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false	// @audit-issue: State variable `vaultId` is used also on line(s): ['31'].

50:        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);	// @audit-issue: State variable `vaultId` is used also on line(s): ['55'].
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L34-L34), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L50-L50), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

75:        address pool = IBalancerVault(balancerVault).getPool(poolId);	// @audit-issue: State variable `balancerVault` is used also on line(s): ['78', '73', '81'].

130:            IBalancerVault(balancerVault).exitPool(	// @audit-issue: State variable `balancerVault` is used also on line(s): ['125'].
```
[75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L75-L75), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L130-L130), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

71:            revert Unauthorized(caller);	// @audit-issue: State variable `caller` is used also on line(s): ['70'].
```
[71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L71-L71), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

38:        IWETH(weth).withdraw(amountIn);	// @audit-issue: State variable `weth` is used also on line(s): ['43'].

52:        _approveOperations(steth, lidoWithdrawal, amount);	// @audit-issue: State variable `steth` is used also on line(s): ['61'].

52:        _approveOperations(steth, lidoWithdrawal, amount);	// @audit-issue: State variable `lidoWithdrawal` is used also on line(s): ['57'].

71:        ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);	// @audit-issue: State variable `lidoWithdrawal` is used also on line(s): ['71', '75'].

85:        _updateTokenInRegistry(weth);	// @audit-issue: State variable `weth` is used also on line(s): ['77'].
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L38-L38), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L52-L52), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L52-L52), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L71-L71), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L85-L85), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

63:        registry.updateHoldingPosition(vaultId, positionId, "", "", false);	// @audit-issue: State variable `vaultId` is used also on line(s): ['58'].

78:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);	// @audit-issue: State variable `vaultId` is used also on line(s): ['79'].
```
[63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L63-L63), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L78-L78), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

65:        if (!registry.isTokenTrusted(vaultId, token, address(this))) {	// @audit-issue: State variable `vaultId` is used also on line(s): ['73'].
```
[65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L65-L65), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

150:        registry.updateHoldingPosition(vaultId, positionId, "", "", false);	// @audit-issue: State variable `vaultId` is used also on line(s): ['123'].
```
[150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L150-L150), 


#### Recommendation

Cache state variables in stack or local memory variables within functions when they are used multiple times. This approach replaces costlier Gwarmaccess operations with cheaper stack reads, saving approximately 100 gas per instance and optimizing overall contract performance.

### Missing Constant Modifier For State Variables
State variables that are never re-assigned after their initial assignment should typically be declared with the `constant` modifier. This ensures that these variables remain unmodified and communicates their unchanging nature. Using the `constant` modifier also offers potential gas savings, as accessing these variables does not require any storage operations.

```solidity
Path: ./contracts/connectors/MaverickConnector.sol

35:    uint256 public MAVERICK_LP = 10;	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L35-L35), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

8:    uint256 public COMPOUND_LP = 2;	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L8-L8), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

22:    uint256 public COLLATERAL_AND_DEBT_POSITION_TYPE = 1;	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

32:    uint256 public BALANCER_LP_POSITION = 1;	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L32-L32), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

13:    uint256 public LIDO_WITHDRAWAL_REQUEST_ID = 10;	// @audit-issue
```
[13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L13-L13), 


#### Recommendation

Declare state variables that are not reassigned after initialization with the 'constant' modifier in Solidity. This clarifies their unchanging nature, improves code readability, and saves gas by avoiding storage operations when accessing these variables.

### State Variables Only Set in The Constructor Should Be Declared `immutable`
Avoids a Gsset(** 20000 gas**) in the constructor, and replaces the first access in each transaction(Gcoldsload - ** 2100 gas **) and each access thereafter(Gwarmacces - ** 100 gas **) with a`PUSH32`(** 3 gas **).

While`string`s are not value types, and therefore cannot be`immutable` / `constant` if not hard - coded outside of the constructor, the same behavior can be achieved by making the current contract `abstract` with `virtual` functions for the`string` accessors, and having a child contract override the functions with the hard - coded implementation - specific values.

```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

8:    address public receiver;	// @audit-issue

9:    address public accountingManager;	// @audit-issue

10:    address public baseToken;	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L8-L8), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L9-L9), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L10-L10), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

60:    IERC20 public baseToken;	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L60-L60), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

7:    PositionRegistry public registry;	// @audit-issue

8:    uint256 public vaultId;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

28:    uint256 public MINIMUM_HEALTH_FACTOR = 15e17;	// @audit-issue

31:    uint256 public DUST_LEVEL = 1;	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L28-L28), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L31-L31), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

16:    address public lifi;	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L16-L16), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

11:    PositionRegistry public registry;	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L11-L11), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

16:    address public factory;	// @audit-issue

17:    PositionRegistry public registry;	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L17-L17), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

11:    PositionRegistry public registry;	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L11-L11), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

17:    address payable public lzHelper;	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L17-L17), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

30:    address mav;	// @audit-issue

31:    address veMav;	// @audit-issue

32:    address maverickRouter;	// @audit-issue

33:    IPositionInspector positionInspector;	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L30-L30), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L31-L31), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L32-L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L33-L33), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

12:    IMasterchefV3 public masterchef;	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L12-L12), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

22:    IStargateLPStaking LPStaking;	// @audit-issue

23:    IStargateRouter stargateRouter;	// @audit-issue

24:    address rewardToken;	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L22-L22), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L23-L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

9:    ISiloRepository public siloRepository;	// @audit-issue
```
[9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L9-L9), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

33:    IRouter aerodromeRouter;	// @audit-issue

34:    IVoter voter;	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L33-L33), [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L34-L34), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

31:    ICamelotRouter public router;	// @audit-issue

32:    ICamelotFactory public factory;	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L31-L31), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L32-L32), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

27:    address internal balancerVault;	// @audit-issue

29:    address public BAL;	// @audit-issue

30:    address public AURA;	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L27-L27), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L29-L29), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L30-L30), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

15:    IBalancerVault internal vault;	// @audit-issue

16:    PositionRegistry public registry;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L16-L16), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

14:    IV3CoreProxy public SNXCoreProxy;	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L14-L14), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

8:    address public lido;	// @audit-issue

9:    address public lidoWithdrawal;	// @audit-issue

10:    address public steth;	// @audit-issue

11:    address public weth;	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L8-L8), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L9-L9), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L10-L10), [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L11-L11), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

22:    IPendleMarketDepositHelper public pendleMarketDepositHelper;	// @audit-issue

23:    IPAllActionV3 public pendleRouter;	// @audit-issue

24:    IPendleStaticRouter public staticRouter;	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L22-L22), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L23-L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

12:    IDepositWithdrawalProxy public depositWithdrawalProxy;	// @audit-issue

13:    IDolomiteMargin public dolomiteMargin;	// @audit-issue

14:    IBorrowPositionProxyV1 public borrowPositionProxy;	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L12-L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L14-L14), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

26:    IBooster public convexBooster;	// @audit-issue

27:    address public CVX;	// @audit-issue

28:    address public CRV;	// @audit-issue

29:    address public PRISMA;	// @audit-issue
```
[26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L26-L26), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L27-L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L29-L29), 


#### Recommendation

Consider marking state variables as an immutable that never changes on the contract.

### Increments can be `unchecked` in for-loops
Newer versions of the Solidity compiler will check for integer overflows and underflows automatically. This provides safety but increases gas costs.
When an unsigned integer is guaranteed to never overflow, the unchecked feature of Solidity can be used to save gas costs.A common case for this is for-loops using a strictly-less-than comparision in their conditional statement.

```solidity
Path: ./contracts/accountingManager/Registry.sol

138:        for (uint256 i = 0; i < _trustedTokens.length; i++) {	// @audit-issue

194:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {	// @audit-issue

214:        for (uint256 i = 0; i < _tokens.length; i++) {	// @audit-issue

253:            for (uint256 i = 0; i < usingTokens.length; i++) {	// @audit-issue

274:        for (uint256 i = 0; i < length; i++) {	// @audit-issue
```
[138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138-L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214-L214), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L253-L253), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L274-L274), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

551:        for (uint256 i = 0; i < retrieveData.length; i++) {	// @audit-issue

603:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue

608:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue
```
[551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551-L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608-L608), 


```solidity
Path: ./contracts/governance/Keepers.sol

29:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29-L29), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

18:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L18-L18), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

178:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

189:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

211:        for (uint256 i = 0; i < tokensIn.length; i++) {	// @audit-issue
```
[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211-L211), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

37:        for (uint256 i = 0; i < usersAddresses.length; i++) {	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

41:        for (uint256 i = 0; i < baseCurrencies.length; i++) {	// @audit-issue

55:        for (uint256 i = 0; i < oracle.length; i++) {	// @audit-issue

88:        for (uint256 i = 0; i < sources.length; i++) {	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

74:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

140:        for (uint256 i = 0; i < earnedInfo.length; i++) {	// @audit-issue
```
[140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

69:        for (uint256 i = 0; i < calls.length; i++) {	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

116:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue

132:        for (uint256 i = 0; i < assetsS.length; i++) {	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L116-L116), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

107:        for (uint8 i; i < numberOfAssets; ++i) {	// @audit-issue
```
[107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L107-L107), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

102:        for (uint256 i = 0; i < tokenIds.length; i++) {	// @audit-issue
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

54:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue

77:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54-L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

74:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

79:            for (uint256 i = 0; i < destinationConnector.length; i++) {	// @audit-issue

84:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

89:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

244:        for (uint256 i = 0; i < rewardTokens.length; i++) {	// @audit-issue
```
[244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

113:        for (uint256 i = 0; i < markets.length; i++) {	// @audit-issue
```
[113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L113-L113), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

222:        for (uint256 i = 0; i < gauges.length; i++) {	// @audit-issue

234:        for (uint256 i = 0; i < pools.length; i++) {	// @audit-issue

248:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue
```
[222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222-L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234-L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248-L248), 


#### Recommendation

Use unchecked math to block overflow / underflow check to save Gas.

### Divisions can be unchecked to save gas
The expression type(int).min/(-1) is the only case where division causes an overflow. Therefore, uncheck can be used to save gas in scenarios where it is certain that such an overflow will not occur.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

243:                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount	// @audit-issue

275:                firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount	// @audit-issue

416:                data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;	// @audit-issue

423:                uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;	// @audit-issue

484:            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);	// @audit-issue

518:            (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;	// @audit-issue
```
[243](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L243-L243), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L275-L275), [416](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L416-L416), [423](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L423-L423), [484](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L484-L484), [518](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L518-L518), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

112:            _swapRequest.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);	// @audit-issue
```
[112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L112-L112), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

81:        int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));	// @audit-issue
```
[81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81-L81), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

132:            return (amountIn * sourceTokenUnit) / uintprice;	// @audit-issue

134:        return (amountIn * uintprice) / (sourceTokenUnit);	// @audit-issue
```
[132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L132-L132), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L134-L134), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

115:        return market.lltv * convertCToL(p.collateral, market.oracle, market.collateralToken) / borrowAmount;	// @audit-issue

138:        return amount * IOracle(marketOracle).price() / ORACLE_PRICE_SCALE;	// @audit-issue
```
[115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L115-L115), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L138-L138), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

124:            totalDepositAmount += depositAmount * price / 1e18;	// @audit-issue

125:            totalBAmount += borrowAmount * price / 1e18;	// @audit-issue
```
[124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L124-L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L125-L125), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

131:        uint256 amount0 = balance * reserve0 / totalSupply;	// @audit-issue

132:        uint256 amount1 = balance * reserve1 / totalSupply;	// @audit-issue
```
[131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L131-L131), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

78:        return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase;	// @audit-issue

89:        borrowBalanceInVirtualBase = (borrowBalanceInBase * basePriceInVirtualBase) / comet.baseScale();	// @audit-issue

118:                    collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice;	// @audit-issue

119:                if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;	// @audit-issue
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L78-L78), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L89-L89), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L118-L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L119-L119), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

129:            (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;	// @audit-issue

136:        uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;	// @audit-issue
```
[129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L129-L129), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L136-L136), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

96:        return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply;	// @audit-issue
```
[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L96-L96), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

172:        return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);	// @audit-issue
```
[172](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L172-L172), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

271:                SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;	// @audit-issue

275:            if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;	// @audit-issue

280:            if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;	// @audit-issue
```
[271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L271-L271), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L275-L275), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L280-L280), 


#### Recommendation

Utilize 'unchecked' blocks in Solidity for divisions where overflow is impossible, such as when 'type(int).min/(-1)' is not a concern. This can save gas by bypassing overflow checks in these specific cases.

### Add `unchecked {}` for subtractions where the operands cannot underflow because of a previous `require()` or `if`-statement
Unchecked keyword can be added to such scenerios: 
`require(a <= b); x = b - a` => `require(a <= b); unchecked { x = b - a }`

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

484:            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);	// @audit-issue

624:        return currentWithdrawGroup.totalCBAmount - availableAssets;	// @audit-issue
```
[484](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L484-L484), [624](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L624-L624), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

33:        return (totalTVL - totalDebt);	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L33-L33), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

103:        return _getValue(address(840), base, (d.totalValueUSD - d.totalDebtUSD));	// @audit-issue
```
[103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L103-L103), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

160:            return collateralValue - borrowValue;	// @audit-issue
```
[160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L160-L160), 


#### Recommendation

In scenarios where subtraction cannot result in underflow due to prior `require()` or `if`-statements, wrap these operations in an `unchecked` block to save gas. This optimization should only be applied when the safety of the operation is assured. Carefully analyze each case to confirm that underflow is impossible before implementing `unchecked` blocks, as incorrect usage can lead to vulnerabilities in the contract.

### Stack variable is only used once
If the variable is only accessed once, it's cheaper to use the assigned value directly that one time, and save the 3 gas the extra stack assignment would spend

```solidity
Path: ./contracts/accountingManager/Registry.sol

399:        bytes32 holdingPositionId = keccak256(abi.encode(_connector, _positionId, data));	// @audit-issue: holdingPositionId used only on line: 400
```
[399](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L399-L399), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

372:        uint256 neededAssets = neededAssetsForWithdraw();	// @audit-issue: neededAssets used only on line: 374

550:        uint256 neededAssets = neededAssetsForWithdraw();	// @audit-issue: neededAssets used only on line: 570

636:            uint256 amount = IERC20(token).balanceOf(abi.decode(position.data, (address)));	// @audit-issue: amount used only on line: 637

685:            (bool success,) = payable(msg.sender).call{ value: amount }("");	// @audit-issue: success used only on line: 686
```
[372](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L372-L372), [550](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L550-L550), [636](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L636-L636), [685](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L685-L685), 


```solidity
Path: ./contracts/governance/Keepers.sol

100:            bytes32 txInputHash =	// @audit-issue: txInputHash used only on line: 102
101:                keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));

116:        (bool success,) = destination.call{ gas: gasLimit }(data);	// @audit-issue: success used only on line: 117
```
[100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L100-L101), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L116-L116), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

32:        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: keeperContract used only on line: 33

32:        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: emergencyManager used only on line: 33

44:        (,,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: emergencyManager used only on line: 45

54:        (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: watcherContract used only on line: 55

54:        (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: emergencyManager used only on line: 55

66:        (, address maintainer,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: maintainer used only on line: 67

66:        (, address maintainer,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: emergencyManager used only on line: 67

76:        (, address maintainer,,,,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: maintainer used only on line: 77

86:        (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: governer used only on line: 87
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L32-L32), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L32-L32), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L44-L44), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L54-L54), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L54-L54), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L66-L66), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L66-L66), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L76-L76), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L86-L86), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

91:            (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: watcherContract used only on line: 94

93:            (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));	// @audit-issue: newData used only on line: 94

101:            uint256 routeId = abi.decode(data, (uint256));	// @audit-issue: routeId used only on line: 102

136:        (address accountingManager,) = registry.getVaultAddresses(vaultId);	// @audit-issue: accountingManager used only on line: 138

278:        uint256 currentAllowance = IERC20(_token).allowance(address(this), _spender);	// @audit-issue: currentAllowance used only on line: 279
```
[91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L91-L91), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L93-L93), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L101-L101), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L136-L136), [278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L278-L278), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

108:            INoyaValueOracle _priceOracle = INoyaValueOracle(valueOracle);	// @audit-issue: _priceOracle used only on line: 110

109:            uint256 _outputTokenValue =	// @audit-issue: _outputTokenValue used only on line: 112
110:                _priceOracle.getValue(_swapRequest.inputToken, _swapRequest.outputToken, _swapRequest.amount);
```
[108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L108-L108), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L109-L110), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

111:        bytes4 selector = bytes4(_request.data[:4]);	// @audit-issue: selector used only on line: 112

115:        (address sendingAssetId, uint256 amount, address from, address receivingAssetId, uint256 receivingAmount) =	// @audit-issue: sendingAssetId used only on line: 120
116:            ILiFi(lifi).extractGenericSwapParameters(_request.data);

115:        (address sendingAssetId, uint256 amount, address from, address receivingAssetId, uint256 receivingAmount) =	// @audit-issue: amount used only on line: 122
116:            ILiFi(lifi).extractGenericSwapParameters(_request.data);

115:        (address sendingAssetId, uint256 amount, address from, address receivingAssetId, uint256 receivingAmount) =	// @audit-issue: receivingAssetId used only on line: 121
116:            ILiFi(lifi).extractGenericSwapParameters(_request.data);

115:        (address sendingAssetId, uint256 amount, address from, address receivingAssetId, uint256 receivingAmount) =	// @audit-issue: receivingAmount used only on line: 119
116:            ILiFi(lifi).extractGenericSwapParameters(_request.data);

176:        (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);	// @audit-issue: success used only on line: 178

176:        (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);	// @audit-issue: err used only on line: 179

195:            (bool success,) = payable(userAddress).call{ value: amount }("");	// @audit-issue: success used only on line: 196
```
[111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L111-L111), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L115-L116), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L115-L116), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L115-L116), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L115-L116), [176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176), [176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176), [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

76:        address[] memory sources = priceRoutes[asset][baseToken];	// @audit-issue: sources used only on line: 78
```
[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L76-L76), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

61:        uint128 amountIn128 = uint128(amount);	// @audit-issue: amountIn128 used only on line: 85
```
[61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L61-L61), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

139:        uint256 decimals = IERC20Metadata(token).decimals();	// @audit-issue: decimals used only on line: 140
```
[139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L139-L139), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

69:        (uint256 vaultId, uint256 tvl, uint256 updateTime) = abi.decode(_message, (uint256, uint256, uint256));	// @audit-issue: vaultId used only on line: 71

69:        (uint256 vaultId, uint256 tvl, uint256 updateTime) = abi.decode(_message, (uint256, uint256, uint256));	// @audit-issue: tvl used only on line: 71

69:        (uint256 vaultId, uint256 tvl, uint256 updateTime) = abi.decode(_message, (uint256, uint256, uint256));	// @audit-issue: updateTime used only on line: 71

70:        uint256 _srcChainId = chainInfo[_origin.srcEid].chainId;	// @audit-issue: _srcChainId used only on line: 71
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L69-L69), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L69-L69), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L69-L69), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L70-L70), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

78:        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;	// @audit-issue: lzChainId used only on line: 80

79:        bytes memory data = abi.encode(vaultId, tvl, updateTime);	// @audit-issue: data used only on line: 80
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L78-L78), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L79-L79), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

52:        uint256 positionTypeId = registry.getPositionBP(vaultId, position.positionId).positionTypeId;	// @audit-issue: positionTypeId used only on line: 53
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L52-L52), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

20:        (, address baseToken) = registry.getVaultAddresses(vaultId);	// @audit-issue: baseToken used only on line: 21

29:        uint256 tvl = getTVL();	// @audit-issue: tvl used only on line: 30

37:            uint256 amount = IERC20(token).balanceOf(address(this));	// @audit-issue: amount used only on line: 38
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L20-L20), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L29-L29), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

92:        uint256 sendEthAmount = p.ethPoolIncluded ? p.tokenARequiredAllowance : 0;	// @audit-issue: sendEthAmount used only on line: 98

96:        uint256 tokenId;	// @audit-issue: tokenId used only on line: 98

120:        IMaverickPosition position = IMaverickRouter(maverickRouter).position();	// @audit-issue: position used only on line: 121

154:        PositionBP memory position = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: position used only on line: 155

157:        (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool);	// @audit-issue: a used only on line: 158

157:        (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool);	// @audit-issue: b used only on line: 158
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L92-L92), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L96-L96), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L120-L120), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L154-L154), [157](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L157-L157), [157](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L157-L157), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

125:            uint256 borrowAmount =	// @audit-issue: borrowAmount used only on line: 132
126:                uint256(pos.borrowShares).toAssetsUp(market.totalBorrowAssets, market.totalBorrowShares);

127:            uint256 supplyAmount =	// @audit-issue: supplyAmount used only on line: 132
128:                uint256(pos.supplyShares).toAssetsUp(market.totalSupplyAssets, market.totalSupplyShares);

142:        Id id = abi.decode(data, (Id));	// @audit-issue: id used only on line: 143
```
[125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L125-L126), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L127-L128), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L142-L142), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

66:        bytes32 positionId =	// @audit-issue: positionId used only on line: 68
67:            registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));

78:        address underlyingToken = IStargatePool(lpAddress).token();	// @audit-issue: underlyingToken used only on line: 86

88:        uint256 LPAmount = LPStaking.userInfo(withdrawRequest.poolId, address(this)).amount;	// @audit-issue: LPAmount used only on line: 89

90:            bytes32 positionId = registry.calculatePositionId(	// @audit-issue: positionId used only on line: 93
91:                address(this), STARGATE_LP_POSITION_TYPE, abi.encode(withdrawRequest.poolId)
92:            );

111:        PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: pBP used only on line: 112

118:        address underlyingToken = IStargatePool(lpAddress).token();	// @audit-issue: underlyingToken used only on line: 120

119:        uint256 underlyingAmount = IStargatePool(lpAddress).amountLPtoLD(lpAmount);	// @audit-issue: underlyingAmount used only on line: 120

124:        uint256 poolId = abi.decode(data, (uint256));	// @audit-issue: poolId used only on line: 125

125:        address lpAddress = LPStaking.poolInfo(poolId).lpToken;	// @audit-issue: lpAddress used only on line: 127
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L66-L67), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L78-L78), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L88-L88), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L90-L92), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L111-L111), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L118-L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L119-L119), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L124-L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L125-L125), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

25:        address c = ICreditFacadeV3(facade).openCreditAccount(address(this), new MultiCall[](0), ref);	// @audit-issue: c used only on line: 29

94:        address creditAccount = abi.decode(p.data, (address));	// @audit-issue: creditAccount used only on line: 98

95:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: positionInfo used only on line: 96

96:        ICreditFacadeV3 facade = ICreditFacadeV3(abi.decode(positionInfo.data, (address)));	// @audit-issue: facade used only on line: 97
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L25-L25), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L94-L94), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L95-L95), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L96-L96), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

86:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue: silo used only on line: 87

110:        PositionBP memory bp = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: bp used only on line: 111

111:        (address siloToken) = abi.decode(bp.data, (address));	// @audit-issue: siloToken used only on line: 112

112:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue: silo used only on line: 113

144:        (address siloToken) = abi.decode(data, (address));	// @audit-issue: siloToken used only on line: 145

145:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue: silo used only on line: 146

146:        (address[] memory assets,) = silo.getAssetsWithState();	// @audit-issue: assets used only on line: 147
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L86-L86), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L110-L110), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L111-L111), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L112-L112), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L144-L144), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L145-L145), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L146-L146), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

54:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue: positionId used only on line: 68

80:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue: positionId used only on line: 93

107:        address gauge = voter.gauges(pool);	// @audit-issue: gauge used only on line: 108

126:        PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: pBP used only on line: 127

130:        (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();	// @audit-issue: reserve0 used only on line: 131

130:        (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();	// @audit-issue: reserve1 used only on line: 132

131:        uint256 amount0 = balance * reserve0 / totalSupply;	// @audit-issue: amount0 used only on line: 133

132:        uint256 amount1 = balance * reserve1 / totalSupply;	// @audit-issue: amount1 used only on line: 133
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L54-L54), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L80-L80), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L107-L107), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L126-L126), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L130-L130), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L130-L130), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L131-L131), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

64:        address rewardToken = IRewards(rewardContract).rewardConfig(market).token;	// @audit-issue: rewardToken used only on line: 66

87:        address basePriceFeed = comet.baseTokenPriceFeed();	// @audit-issue: basePriceFeed used only on line: 88

88:        uint256 basePriceInVirtualBase = comet.getPrice(basePriceFeed);	// @audit-issue: basePriceInVirtualBase used only on line: 89

101:            uint256 principalInBase = uint256(uint104(userBasic.principal));	// @audit-issue: principalInBase used only on line: 102

128:        uint256 positiveBalance = getCollBlanace(IComet(market), false);	// @audit-issue: positiveBalance used only on line: 130

129:        uint256 negativeBalance = getBorrowBalanceInBase(IComet(market));	// @audit-issue: negativeBalance used only on line: 130

130:        uint256 balance = positiveBalance - negativeBalance;	// @audit-issue: balance used only on line: 131
```
[64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L64-L64), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L87-L87), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L88-L88), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L101-L101), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L128-L128), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L129-L129), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L130-L130), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

43:        bytes32 positionId =	// @audit-issue: positionId used only on line: 58
44:            registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));

69:        uint256 currentCollateral = pool.userCollateralBalance(address(this));	// @audit-issue: currentCollateral used only on line: 70

71:            bytes32 positionId =	// @audit-issue: positionId used only on line: 74
72:                registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));

88:        uint256 repayTokenAmount = pool.toBorrowAmount(sharesToRepay, true);	// @audit-issue: repayTokenAmount used only on line: 94

89:        uint256 sharesOwed = pool.userBorrowShares(address(this));	// @audit-issue: sharesOwed used only on line: 91

106:        uint256 exchangeRate = pool.exchangeRateInfo().exchangeRate;	// @audit-issue: exchangeRate used only on line: 108

122:        uint256 borrowerShares = _fraxlendPair.userBorrowShares(address(this));	// @audit-issue: borrowerShares used only on line: 123

127:        (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();	// @audit-issue: LTV_PRECISION used only on line: 129

127:        (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();	// @audit-issue: EXCHANGE_PRECISION used only on line: 129

132:        uint256 fraxlendPairMaxLTV = _fraxlendPair.maxLTV();	// @audit-issue: fraxlendPairMaxLTV used only on line: 136

136:        uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;	// @audit-issue: currentHF used only on line: 139

151:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: positionInfo used only on line: 152

153:        uint256 collateralAmount = pool.userCollateralBalance(address(this));	// @audit-issue: collateralAmount used only on line: 158

154:        uint256 borrowerShares = pool.userBorrowShares(address(this));	// @audit-issue: borrowerShares used only on line: 155

155:        uint256 _borrowerAmount = pool.toBorrowAmount(borrowerShares, true);	// @audit-issue: _borrowerAmount used only on line: 157
```
[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L43-L44), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L69-L69), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L71-L72), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L88-L88), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L89-L89), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L106-L106), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L122-L122), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L127-L127), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L127-L127), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L132-L132), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L136-L136), [151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L151-L151), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L153-L153), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L154-L154), [155](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L155-L155), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

92:        uint256 totalSupply = IERC20(pool).totalSupply();	// @audit-issue: totalSupply used only on line: 96

93:        (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();	// @audit-issue: reserves0 used only on line: 96

93:        (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();	// @audit-issue: reserves1 used only on line: 96

95:        uint256 balanceThis = IERC20(pool).balanceOf(address(this));	// @audit-issue: balanceThis used only on line: 96

100:        (address tokenA, address tokenB) = abi.decode(data, (address, address));	// @audit-issue: tokenA used only on line: 102

100:        (address tokenA, address tokenB) = abi.decode(data, (address, address));	// @audit-issue: tokenB used only on line: 103
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L92-L92), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L93-L93), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L93-L93), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L95-L95), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L100-L100), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L100-L100), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

41:        bytes32 positionId =	// @audit-issue: positionId used only on line: 52
42:            registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));

50:        bytes memory positionData = abi.encode(tokenId);	// @audit-issue: positionData used only on line: 52

75:            bytes32 positionId =	// @audit-issue: positionId used only on line: 78
76:                registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(token0, token1));

77:            bytes memory positionData = abi.encode(p.tokenId);	// @audit-issue: positionData used only on line: 78

117:        (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);	// @audit-issue: token0 used only on line: 118

117:        (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);	// @audit-issue: token1 used only on line: 118

117:        (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);	// @audit-issue: liquidity used only on line: 118

123:        CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max);	// @audit-issue: params used only on line: 124

128:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: positionInfo used only on line: 130

133:        (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));	// @audit-issue: fee used only on line: 135

136:            bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));	// @audit-issue: key used only on line: 138

138:            (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);	// @audit-issue: liquidity used only on line: 142

138:            (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);	// @audit-issue: tokensOwed0 used only on line: 144

138:            (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);	// @audit-issue: tokensOwed1 used only on line: 145

140:            (uint160 sqrtPriceX96,,,,,,) = pool.slot0();	// @audit-issue: sqrtPriceX96 used only on line: 142
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L41-L42), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L50-L50), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L75-L76), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L77-L77), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L117-L117), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L117-L117), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L117-L117), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L123-L123), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L128-L128), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L133-L133), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L136-L136), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L138-L138), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L138-L138), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L138-L138), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

96:        bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(poolId));	// @audit-issue: positionId used only on line: 97

102:            uint256 amount = IERC20(pool).balanceOf(address(this));	// @audit-issue: amount used only on line: 103

117:            (PoolInfo memory _poolInfo, bytes32 positionId) = _getPoolInfo(p.poolId);	// @audit-issue: _poolInfo used only on line: 119

163:        PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: PTI used only on line: 164

165:        uint256 lpBalance = totalLpBalanceOf(pool);	// @audit-issue: lpBalance used only on line: 172

166:        (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);	// @audit-issue: _tokenBalances used only on line: 171

167:        uint256 _totalSupply = IERC20(pool.pool).totalSupply();	// @audit-issue: _totalSupply used only on line: 172

169:        uint256 _weight = pool.weights[pool.tokenIndex];	// @audit-issue: _weight used only on line: 172

171:        uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]);	// @audit-issue: token1bal used only on line: 172

185:        (PoolInfo memory pool,) = _getPoolInfo(poolId);	// @audit-issue: pool used only on line: 186

191:        PositionBP memory p = registry.getPositionBP(vaultId, positionId);	// @audit-issue: p used only on line: 192
```
[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L96-L96), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L102-L102), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L117-L117), [163](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L163-L163), [165](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L165-L165), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L166-L166), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L167-L167), [169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L169-L169), [171](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L171-L171), [185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L185-L185), [191](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L191-L191), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

69:        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue: keeperContract used only on line: 70
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

50:        (uint256 c,,) = SNXCoreProxy.getAccountCollateral(_accountId, _token);	// @audit-issue: c used only on line: 51

76:        uint128 poolId = SNXCoreProxy.getPreferredPool();	// @audit-issue: poolId used only on line: 78

88:        uint256[] memory poolIds = SNXCoreProxy.getApprovedPools();	// @audit-issue: poolIds used only on line: 90

122:        (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address));	// @audit-issue: accountId used only on line: 124

123:        (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =	// @audit-issue: totalDeposited used only on line: 125
124:            SNXCoreProxy.getAccountCollateral(accountId, collateralType);

123:        (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =	// @audit-issue: totalAssigned used only on line: 125
124:            SNXCoreProxy.getAccountCollateral(accountId, collateralType);
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L50-L50), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L76-L76), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L88-L88), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L122-L122), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L123-L124), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L123-L124), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

103:        (uint256 totalCollateralBase,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));	// @audit-issue: totalCollateralBase used only on line: 106

115:        (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this));	// @audit-issue: totalCollateralBase used only on line: 116

115:        (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this));	// @audit-issue: totalDebtBase used only on line: 116

116:        uint256 poolBaseAmount = totalCollateralBase - totalDebtBase;	// @audit-issue: poolBaseAmount used only on line: 117
```
[103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L103-L103), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L115-L115), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L115-L115), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L116-L116), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

57:        uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this));	// @audit-issue: requestIds used only on line: 59

58:        bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, "");	// @audit-issue: positionId used only on line: 59

73:        uint256 beforeClaimBalance = address(this).balance;	// @audit-issue: beforeClaimBalance used only on line: 77

92:        (uint256 amount) = abi.decode(p.additionalData, (uint256));	// @audit-issue: amount used only on line: 93
```
[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L57-L57), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L58-L58), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L73-L73), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

58:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);	// @audit-issue: positionInfo used only on line: 59

60:        address debTtoken = ITroveManager(tm).debtToken();	// @audit-issue: debTtoken used only on line: 65

78:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);	// @audit-issue: positionInfo used only on line: 82

82:        address collateral = abi.decode(positionInfo.additionalData, (address));	// @audit-issue: collateral used only on line: 83

130:        bytes32 positionId =	// @audit-issue: positionId used only on line: 134
131:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, troveManager));

132:        IBorrowerOperations borrowerOperations = zapContract.borrowerOps();	// @audit-issue: borrowerOperations used only on line: 133

148:            (address zap, address troveManager) = abi.decode(positionInfo.data, (address, address));	// @audit-issue: zap used only on line: 149

149:            IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();	// @audit-issue: borrowerOperations used only on line: 150

150:            address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;	// @audit-issue: collateral used only on line: 154

151:            address debTtoken = ITroveManager(troveManager).debtToken();	// @audit-issue: debTtoken used only on line: 154

152:            (uint256 collateralBalance, uint256 debtBalance) =	// @audit-issue: collateralBalance used only on line: 154
153:                ITroveManager(troveManager).getTroveCollAndDebt(address(this));

152:            (uint256 collateralBalance, uint256 debtBalance) =	// @audit-issue: debtBalance used only on line: 154
153:                ITroveManager(troveManager).getTroveCollAndDebt(address(this));

165:        (address zap, address troveManager) = abi.decode(data, (address, address));	// @audit-issue: zap used only on line: 166

166:        IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();	// @audit-issue: borrowerOperations used only on line: 167

167:        address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;	// @audit-issue: collateral used only on line: 170

168:        address debTtoken = ITroveManager(troveManager).debtToken();	// @audit-issue: debTtoken used only on line: 171
```
[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L58-L58), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L60-L60), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L78-L78), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L82-L82), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L130-L131), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L132-L132), [148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L148-L148), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L149-L149), [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L150-L150), [151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L151-L151), [152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L152-L153), [152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L152-L153), [165](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L165-L165), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L166-L166), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L167-L167), [168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L168-L168), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

85:        uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);	// @audit-issue: syMinted used only on line: 89

87:        bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));	// @audit-issue: positionId used only on line: 88

98:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _SY used only on line: 99

113:        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();	// @audit-issue: _SY used only on line: 114

113:        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();	// @audit-issue: _PT used only on line: 115

153:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _YT used only on line: 154

170:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _YT used only on line: 171

188:        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();	// @audit-issue: _PT used only on line: 189

218:        (, address _underlyingToken,) = SY.assetInfo();	// @audit-issue: _underlyingToken used only on line: 222

262:            (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _PT used only on line: 274

262:            (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _YT used only on line: 277

263:            (, address _underlyingToken,) = _SY.assetInfo();	// @audit-issue: _underlyingToken used only on line: 282

294:        (uint256 netSyOut,,,,,,) = staticRouter.swapExactYtForSyStatic(market, balance);	// @audit-issue: netSyOut used only on line: 295

304:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _SY used only on line: 306

304:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _PT used only on line: 306

304:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue: _YT used only on line: 306

312:        address market = abi.decode(data, (address));	// @audit-issue: market used only on line: 313

313:        (IPStandardizedYield SY,,) = IPMarket(market).readTokens();	// @audit-issue: SY used only on line: 315
```
[85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L85-L85), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L87-L87), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L98-L98), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L113-L113), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L113-L113), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153-L153), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170-L170), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L188-L188), [218](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L218-L218), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L262-L262), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L262-L262), [263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L263-L263), [294](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L294-L294), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304-L304), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304-L304), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304-L304), [312](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L312-L312), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L313-L313), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

44:        address token = dolomiteMargin.getMarketTokenAddress(marketId);	// @audit-issue: token used only on line: 49

50:        (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));	// @audit-issue: markets used only on line: 51

107:        uint256 accountId = abi.decode(p.data, (uint256));	// @audit-issue: accountId used only on line: 110
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L44-L44), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L50-L50), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L107-L107), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

85:        address lpToken = poolInfo.lpToken;	// @audit-issue: lpToken used only on line: 90

104:        PoolInfo memory poolInfo = _getPoolInfo(pool);	// @audit-issue: poolInfo used only on line: 106

123:        PositionBP memory p = registry.getPositionBP(vaultId, positionId);	// @audit-issue: p used only on line: 124

125:        address token = poolInfo.tokens[depositIndex];	// @audit-issue: token used only on line: 127

166:        address token = poolInfo.tokens[withdrawIndex];	// @audit-issue: token used only on line: 170

167:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue: positionId used only on line: 172

259:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue: positionId used only on line: 260

260:        PositionBP memory p = registry.getPositionBP(vaultId, positionId);	// @audit-issue: p used only on line: 261

266:        PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue: PTI used only on line: 267

268:        uint256 lpBalance = totalLpBalanceOf(poolInfo);	// @audit-issue: lpBalance used only on line: 269

269:        (uint256 amount, address token) = LPToUnder(poolInfo, lpBalance);	// @audit-issue: amount used only on line: 270

269:        (uint256 amount, address token) = LPToUnder(poolInfo, lpBalance);	// @audit-issue: token used only on line: 270

302:        int128 tokenIndex = int128(uint128(index));	// @audit-issue: tokenIndex used only on line: 303

312:        uint256 lpBalance = balanceOfLPToken(info);	// @audit-issue: lpBalance used only on line: 317

313:        uint256 rewardBalance = balanceOfRewardPool(info);	// @audit-issue: rewardBalance used only on line: 317

314:        uint256 convexRewardBalance = balanceOfConvexRewardPool(info);	// @audit-issue: convexRewardBalance used only on line: 317

315:        uint256 prismaBalance = balanceOfPrisma(info.prismaCurvePool);	// @audit-issue: prismaBalance used only on line: 317

316:        uint256 prismaConvexBalance = balanceOfPrisma(info.prismaConvexPool);	// @audit-issue: prismaConvexBalance used only on line: 317
```
[85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L85-L85), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L104-L104), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L123-L123), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L125-L125), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L166-L166), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L167-L167), [259](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L259-L259), [260](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L260-L260), [266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L266-L266), [268](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L268-L268), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L269-L269), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L269-L269), [302](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L302-L302), [312](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L312-L312), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L313-L313), [314](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L314-L314), [315](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L315-L315), [316](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L316-L316), 


#### Recommendation

Eliminate single-use stack variables in Solidity to optimize gas consumption. Directly use the assigned value in the place of the variable. This approach saves the 3 gas typically used for the extra stack assignment, streamlining the function's execution and enhancing overall gas efficiency.

### Avoid Using State Variables Directly in `emit` for Gas Efficiency
In Solidity, emitting events is a common way to log contract activity and changes, especially for off-chain monitoring and interfacing. However, using state variables directly in `emit` statements can lead to increased gas costs. Each access to a state variable incurs gas due to storage reading operations. When these variables are used directly in `emit` statements, especially within functions that perform multiple operations, the cumulative gas cost can become significant. Instead, caching state variables in memory and using these local copies in `emit` statements can optimize gas usage.


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

216:        emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);	// @audit-issue: `depositQueue` is a state variable and used on line(s): ['215']

314:        emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);	// @audit-issue: `withdrawQueue` is a state variable and used on line(s): ['313']

364:        emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);	// @audit-issue: `currentWithdrawGroup` is a state variable and used on line(s): ['361', '361']

387:        emit WithdrawGroupFulfilled(
388:            currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount	// @audit-issue: `currentWithdrawGroup` is a state variable and used on line(s): ['381', '374', '371', '380', '371', '385']
389:        );

455:            emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw);	// @audit-issue: `depositQueue` is a state variable and used on line(s): ['457', '457']

462:            emit ResetMiddle(newMiddle, withdrawQueue.middle, depositOrWithdraw);	// @audit-issue: `withdrawQueue` is a state variable and used on line(s): ['464', '464']

485:        emit RecordProfit(
486:            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp	// @audit-issue: `storedProfitForFee` is a state variable and used on line(s): ['484', '479']
487:        );

485:        emit RecordProfit(
486:            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp	// @audit-issue: `totalProfitCalculated` is a state variable and used on line(s): ['484', '479']
487:        );

496:            emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);	// @audit-issue: `storedProfitForFee` is a state variable and used on line(s): ['495']

538:        emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);	// @audit-issue: `preformanceFeeSharesWaitingForDistribution` is a state variable and used on line(s): ['534', '528']
```
[216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L216-L216), [314](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L314-L314), [364](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L364-L364), [388](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L387-L389), [455](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L455-L455), [462](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L462-L462), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L485-L487), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L485-L487), [496](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L496-L496), [538](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L538-L538), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

182:        emit Forwarded(lifi, address(token), amount, data);	// @audit-issue: `lifi` is a state variable and used on line(s): ['176', '173']
```
[182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L182-L182), 


#### Recommendation


To optimize gas efficiency, cache state variables in memory when they are used multiple times within a function, including in `emit` statements.

### Don't emit events inside a loop
Emitting an event has an overhead of 375 gas, which will be incurred on every iteration of the loop. It is cheaper to emit only once after the loop has finished.

```solidity
Path: ./contracts/accountingManager/Registry.sol

196:            emit ConnectorAdded(vaultId, _connectorAddresses[i]);	// @audit-issue
```
[196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L196-L196), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

242:            emit CalculateDeposit(	// @audit-issue

274:            emit ExecuteDeposit(	// @audit-issue

349:            emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);	// @audit-issue

429:            emit ExecuteWithdraw(	// @audit-issue

562:            emit RetrieveTokensForWithdraw(	// @audit-issue
```
[242](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L242-L242), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L274-L274), [349](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L349-L349), [429](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L429-L429), [562](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L562-L562), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

217:            emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);	// @audit-issue
```
[217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L217-L217), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

150:            emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);	// @audit-issue
```
[150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L150-L150), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

76:            emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);	// @audit-issue
```
[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L76-L76), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

107:            emit CollectFees(tokenIds[i]);	// @audit-issue
```
[107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L107-L107), 


#### Recommendation

To optimize gas usage, avoid emitting events inside loops in Solidity. Instead, emit a single event after the loop completes, thereby saving the 375 gas overhead incurred on each iteration.

### `Internal` functions only called once can be inlined to save gas
If an internal function is only used once, there is no need to modularize it, unless the function calling it would otherwise be too long and complex. Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

```solidity
Path: ./contracts/accountingManager/Registry.sol

293:    function updateHoldingPosition(	// @audit-issue
```
[293](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L293-L293), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

642:    function _getValue(address token, address base, uint256 amount) internal view returns (uint256) {	// @audit-issue
```
[642](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L642-L642), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

221:    function _executeSwap(SwapRequest memory swapRequest) internal returns (uint256 amountOut) {	// @audit-issue

267:    function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {	// @audit-issue

285:    function _revokeApproval(address _token, address _spender) internal virtual {	// @audit-issue
```
[221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L221-L221), [267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267), [285](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L285-L285), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

185:    function _setAllowance(IERC20 token, address spender, uint256 amount) internal {	// @audit-issue

189:    function _isNative(IERC20 token) internal pure returns (bool isNative) {	// @audit-issue
```
[185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L185-L185), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L189-L189), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

81:    function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)	// @audit-issue
```
[81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L81), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

120:    function _getHealthFactor(IFraxPair _fraxlendPair, uint256 _exchangeRate) internal view virtual returns (uint256) {	// @audit-issue
```
[120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L120-L120), 


#### Recommendation

Inline 'internal' functions in Solidity that are called only once to save gas. This avoids the additional gas cost of 20 to 40 units associated with extra JUMP instructions and stack operations required for separate function calls, unless the calling function becomes too complex.

### Inline modifiers used only once
In Solidity, modifiers provide a way to add reusable conditions or logic to functions. However, if a modifier is used only once, the modularization may not be beneficial in terms of gas efficiency. The overhead associated with a modifier – including two extra JUMP instructions and additional stack operations for the function call – results in an extra cost of about 20 to 40 gas. In cases where a modifier is unique to a single function and the function’s complexity does not necessitate breaking out logic, inlining the modifier's code directly within the function can be more gas-efficient. This approach avoids the overhead of a separate modifier call while maintaining code clarity.

```solidity
Path: ./contracts/accountingManager/Registry.sol

39:    modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) {	// @audit-issue

46:    modifier onlyVaultGoverner(uint256 _vaultId) {	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L39-L39), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L46-L46), 


#### Recommendation

Evaluate the use of modifiers in your Solidity contracts, particularly those applied to only one function. If a modifier is unique to a single function, consider inlining its logic within the function itself to save gas. This is especially advantageous for simpler functions where the additional clarity provided by a separate modifier does not outweigh the gas cost of its use. Ensure that the function remains clear and maintainable after inlining the modifier's logic, and document the rationale for inlining to maintain code readability and facilitate future maintenance.

### Use `private` Rather than `public` for Constants 
In Solidity, constants represent immutable values that cannot be changed after they are set at compile-time. By default, constants have internal visibility, meaning they can be accessed within the contract they are declared in and in derived contracts. If a constant is explicitly declared as `public`, Solidity automatically generates a getter function for it. While this might seem harmless, it actually incurs a gas overhead, especially when the contract is deployed, as the EVM needs to generate bytecode for that getter. Conversely, declaring constants as `private` ensures that no additional getter is generated, optimizing gas usage.

```solidity
Path: ./contracts/accountingManager/Registry.sol

15:    bytes32 public constant MAINTAINER_ROLE = keccak256("MAINTAINER_ROLE");	// @audit-issue

17:    bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE");	// @audit-issue

19:    bytes32 public constant EMERGENCY_ROLE = keccak256("EMERGENCY_ROLE");	// @audit-issue

21:    uint256 public constant MAX_NUM_HOLDING_POSITIONS = 40;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L15-L15), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L19-L19), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L21-L21), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

52:    uint256 public constant FEE_PRECISION = 1e6;	// @audit-issue

53:    uint256 public constant WITHDRAWAL_MAX_FEE = 5e4;	// @audit-issue

54:    uint256 public constant MANAGEMENT_MAX_FEE = 5e5;	// @audit-issue

55:    uint256 public constant PERFORMANCE_MAX_FEE = 1e5;	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L52-L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L53-L53), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L54-L54), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L55-L55), 


```solidity
Path: ./contracts/governance/Keepers.sol

11:    bytes32 public constant TXTYPE_HASH = keccak256(	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L11-L11), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

18:    bytes4 public constant LI_FI_GENERIC_SWAP_SELECTOR = 0x4630a0d8;	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L18-L18), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

25:    address public constant ETH = address(0);	// @audit-issue

26:    address public constant USD = address(840);	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L26-L26), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

11:    uint256 public constant OMNICHAIN_POSITION_ID = 13;	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L11-L11), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

19:    uint256 public constant BRIDGE_TXN_WAITING_TIME = 30 minutes;	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L19-L19), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

15:    uint256 public constant MORPHO_POSITION_ID = 1;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L15-L15), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

26:    uint256 public constant STARGATE_LP_POSITION_TYPE = 1;	// @audit-issue
```
[26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L26-L26), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

9:    uint256 public constant GEARBOX_POSITION_ID = 3;	// @audit-issue
```
[9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L9-L9), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

10:    uint256 public constant SILO_LP_ID = 11;	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

31:    uint256 public constant AERODROME_POSITION_TYPE = 1;	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L31-L31), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

34:    uint256 public constant CAMELOT_POSITION_ID = 1;	// @audit-issue
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L34-L34), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

19:    uint256 public constant UNI_LP_POSITION_TYPE = 5;	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L19-L19), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

16:    uint256 public constant SNX_POSITION_ID = 1;	// @audit-issue

17:    uint256 public constant SNX_POOL_POSITION_ID = 2;	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L17-L17), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

24:    uint256 public constant AAVE_POSITION_ID = 1;	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

14:    uint256 public constant PRISMA_POSITION_ID = 10;	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L14-L14), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

26:    uint256 public constant PENDLE_POSITION_ID = 11;	// @audit-issue
```
[26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L26-L26), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

16:    uint256 public constant DOL_POSITION_ID = 1;	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L16-L16), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

31:    uint256 public constant CURVE_LP_POSITION = 4;	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L31-L31), 


#### Recommendation

To optimize gas usage in your Solidity contracts, declare constants with `private` visibility rather than `public` when possible. Using `private` prevents the automatic generation of a getter function, reducing gas overhead, especially during contract deployment.

### Using `this` to access functions results in an external call, wasting gas
External calls have an overhead of **100 gas**, which can be avoided by not referencing the function using `this`. Contracts [are allowed](https://docs.soliditylang.org/en/latest/contracts.html#function-overriding) to override their parents' functions and change the visibility from `external` to `public`, so make this change if it's required in order to call the function internally.

```solidity
Path: ./contracts/connectors/MaverickConnector.sol

150:        return this.onERC721Received.selector;	// @audit-issue
```
[150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L150-L150), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

65:        return this.onERC721Received.selector;	// @audit-issue
```
[65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L65-L65), 


#### Recommendation

Adopt a consistent timekeeping mechanism across L1 and L2 solutions when using `block.number` or similar timing mechanisms in your Solidity contracts. Consider using a standard clock or timestamp-based system, especially for functionalities like governance that require consistent timing across chains. For contracts on specific L2 solutions, ensure you're using the correct method to obtain block numbers consistent with the intended behavior. Keep abreast of standards and best practices, such as those suggested by OpenZeppelin, and implement appropriate solutions like EIP-6372 to provide a consistent and reliable timing mechanism across different blockchain environments.

### Consider pre-calculating the address of `address(this)` to save gas
Use `foundry`'s [`script.sol`](https://book.getfoundry.sh/reference/forge-std/compute-create-address) or `solady`'s [`LibRlp.sol`](https://github.com/Vectorized/solady/blob/main/src/utils/LibRLP.sol) to save the value in a constant, which will avoid having to spend gas to push the value on the stack every time it's used.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

205:        baseToken.safeTransferFrom(msg.sender, address(this), amount);	// @audit-issue

379:        uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;	// @audit-issue

555:            uint256 balanceBefore = baseToken.balanceOf(address(this));	// @audit-issue

557:                address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data	// @audit-issue

559:            uint256 balanceAfter = baseToken.balanceOf(address(this));	// @audit-issue

617:        uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;	// @audit-issue

628:        return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this))	// @audit-issue
```
[205](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L205-L205), [379](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L379-L379), [555](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L555-L555), [557](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L557-L557), [559](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L559-L559), [617](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L617-L617), [628](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L628-L628), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

103:            if (caller != address(this)) revert IConnector_InvalidAddress(caller);	// @audit-issue

141:            registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));	// @audit-issue

144:            registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);	// @audit-issue

159:        _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0);	// @audit-issue

180:            uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue

182:            uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue

213:                SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)	// @audit-issue

278:        uint256 currentAllowance = IERC20(_token).allowance(address(this), _spender);	// @audit-issue
```
[103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L103-L103), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L141-L141), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L144-L144), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L159-L159), [180](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L180-L180), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L182-L182), [213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L213-L213), [278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L278-L278), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

80:        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here	// @audit-issue
```
[80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L80-L80), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

37:            registry.calculatePositionId(address(this), OMNICHAIN_POSITION_ID, abi.encode(chainId)),	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L37-L37), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

74:        if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L74-L74), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

37:            uint256 amount = IERC20(token).balanceOf(address(this));	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

103:            vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false	// @audit-issue

123:            p.pool, address(this), p.tokenId, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline	// @audit-issue

126:            vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true	// @audit-issue

138:        IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));	// @audit-issue

143:                rewardContract.getReward(address(this), tokenIndex);	// @audit-issue

157:        (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool);	// @audit-issue
```
[103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L103-L103), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L123-L123), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L126-L126), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L138-L138), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L143-L143), [157](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L157-L157), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

39:            morphoBlue.supply(params, amount, 0, address(this), "");	// @audit-issue

43:            morphoBlue.supplyCollateral(params, amount, address(this), "");	// @audit-issue

47:            vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false	// @audit-issue

61:            morphoBlue.withdraw(params, amount, 0, address(this), address(this));	// @audit-issue

63:            morphoBlue.withdrawCollateral(params, amount, address(this), address(this));	// @audit-issue

65:        Position memory p = morphoBlue.position(id, address(this));	// @audit-issue

68:                vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true	// @audit-issue

82:        morphoBlue.borrow(market, amount, 0, address(this), address(this));	// @audit-issue

98:        morphoBlue.repay(params, amount, 0, address(this), "");	// @audit-issue

110:        Position memory p = morphoBlue.position(_id, address(this));	// @audit-issue

124:            Position memory pos = morphoBlue.position(id, address(this));	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L39-L39), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L43-L43), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L47-L47), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L61-L61), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L63-L63), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L65-L65), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L68-L68), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L82-L82), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L98-L98), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L110-L110), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L124-L124), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

32:        IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId);	// @audit-issue

51:        masterchef.withdraw(tokenId, address(this));	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L32-L32), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L51-L51), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

54:            stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this));	// @audit-issue

60:                stakingAmount = IERC20(lpAddress).balanceOf(address(this));	// @audit-issue

67:            registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));	// @audit-issue

84:                uint16(withdrawRequest.poolId), withdrawRequest.routerAmount, address(this)	// @audit-issue

88:        uint256 LPAmount = LPStaking.userInfo(withdrawRequest.poolId, address(this)).amount;	// @audit-issue

89:        if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) {	// @audit-issue

91:                address(this), STARGATE_LP_POSITION_TYPE, abi.encode(withdrawRequest.poolId)	// @audit-issue

114:        uint256 lpAmount = LPStaking.userInfo(poolId, address(this)).amount + IERC20(lpAddress).balanceOf(address(this));	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L54-L54), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L60-L60), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L67-L67), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L84-L84), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L88-L88), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L89-L89), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L91-L91), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L114-L114), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

25:        address c = ICreditFacadeV3(facade).openCreditAccount(address(this), new MultiCall[](0), ref);	// @audit-issue

28:            registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),	// @audit-issue

46:            registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L25-L25), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L28-L28), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L46-L46), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

39:            vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", false	// @audit-issue

62:                vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true	// @audit-issue

65:        if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) {	// @audit-issue

76:        return SolvencyV2.getData(ISilo(siloRepository.getSilo(siloToken)), address(this), minimumHealthFactor);	// @audit-issue

103:        if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) {	// @audit-issue

117:            uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));	// @audit-issue

118:            depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));	// @audit-issue

119:            uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));	// @audit-issue

134:                IERC20(assetsS[i].collateralToken).balanceOf(address(this))	// @audit-issue

135:                    + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L39-L39), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L62-L62), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L65-L65), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L76-L76), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L103-L103), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L117-L117), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L118-L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L119-L119), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L134-L134), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L135-L135), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

54:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue

65:            address(this),	// @audit-issue

80:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue

89:            address(this),	// @audit-issue

92:        if (IERC20(data.pool).balanceOf(address(this)) == 0) {	// @audit-issue

103:        IGauge(gauge).deposit(liquidity, address(this));	// @audit-issue

113:        IGauge(gauge).getReward(address(this));	// @audit-issue

128:        uint256 balance = IERC20(pool).balanceOf(address(this));	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L54-L54), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L65-L65), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L80-L80), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L89-L89), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L92-L92), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L103-L103), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L113-L113), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L128-L128), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

31:        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);	// @audit-issue

34:            vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false	// @audit-issue

50:        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);	// @audit-issue

55:                vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true	// @audit-issue

65:        IRewards(rewardContract).claim(address(market), address(this), true);	// @audit-issue

85:        uint256 borrowBalanceInBase = comet.borrowBalanceOf(address(this));	// @audit-issue

96:        IComet.UserBasic memory userBasic = comet.userBasic(address(this));	// @audit-issue

112:                (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset);	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L31-L31), [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L34-L34), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L50-L50), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L55-L55), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L65-L65), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L85-L85), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L96-L96), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L112-L112), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

44:            registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));	// @audit-issue

50:            pool.borrowAsset(borrowAmount, collateralAmount, address(this));	// @audit-issue

53:            pool.addCollateral(collateralAmount, address(this));	// @audit-issue

69:        uint256 currentCollateral = pool.userCollateralBalance(address(this));	// @audit-issue

72:                registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));	// @audit-issue

76:        pool.removeCollateral(withdrawAmount, address(this));	// @audit-issue

89:        uint256 sharesOwed = pool.userBorrowShares(address(this));	// @audit-issue

95:        IFraxPair(pool).repayAsset(sharesToRepay, address(this));	// @audit-issue

122:        uint256 borrowerShares = _fraxlendPair.userBorrowShares(address(this));	// @audit-issue

125:        uint256 _collateralAmount = _fraxlendPair.userCollateralBalance(address(this));	// @audit-issue

153:        uint256 collateralAmount = pool.userCollateralBalance(address(this));	// @audit-issue

154:        uint256 borrowerShares = pool.userBorrowShares(address(this));	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L44-L44), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L50-L50), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L53-L53), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L69-L69), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L72-L72), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L76-L76), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L89-L89), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L95-L95), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L122-L122), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L125-L125), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L153-L153), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L154-L154), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

47:            p.tokenA, p.tokenB, p.amountA, p.amountB, p.minAmountA, p.minAmountB, address(this), p.deadline	// @audit-issue

53:            registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),	// @audit-issue

73:            p.tokenA, p.tokenB, p.amountLiquidty, p.minAmountA, p.minAmountB, address(this), p.deadline	// @audit-issue

77:        if (IERC20(pool).balanceOf(address(this)) == 0) {	// @audit-issue

80:                registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),	// @audit-issue

95:        uint256 balanceThis = IERC20(pool).balanceOf(address(this));	// @audit-issue
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L47-L47), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L53-L53), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L73-L73), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L77-L77), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L80-L80), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L95-L95), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

42:            registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));	// @audit-issue

43:        p.recipient = address(this);	// @audit-issue

76:                registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(token0, token1));	// @audit-issue

123:        CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max);	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L42-L42), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L43-L43), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L76-L76), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L123-L123), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

83:            address(this), // sender	// @audit-issue

84:            address(this), // recipient	// @audit-issue

96:        bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(poolId));	// @audit-issue

102:            uint256 amount = IERC20(pool).balanceOf(address(this));	// @audit-issue

104:            IRewardPool(_poolInfo.auraPoolAddress).deposit(auraAmount, address(this));	// @audit-issue

112:        IRewardPool(_poolInfo.auraPoolAddress).deposit(_amount, address(this));	// @audit-issue

132:                address(this), // sender	// @audit-issue

133:                payable(address(this)), // recipient	// @audit-issue

149:                    registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(p.poolId)),	// @audit-issue

178:            auraShares = IERC20(pool.auraPoolAddress).balanceOf(address(this));	// @audit-issue

181:        return IERC20(pool.pool).balanceOf(address(this)) + auraShares;	// @audit-issue

190:        bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(pooId));	// @audit-issue
```
[83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L83-L83), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L84-L84), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L96-L96), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L102-L102), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L104-L104), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L112-L112), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L132-L132), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L133-L133), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L149-L149), [178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L178-L178), [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L181-L181), [190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L190-L190), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

86:                BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");	// @audit-issue

92:            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");	// @audit-issue
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L86-L86), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

37:            registry.calculatePositionId(address(this), SNX_POSITION_ID, ""),	// @audit-issue

54:                registry.calculatePositionId(address(this), SNX_POSITION_ID, ""),	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L37-L37), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L54-L54), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

48:        IPool(pool).supply(supplyToken, amount, address(this), 0);	// @audit-issue

50:            vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", false	// @audit-issue

67:        if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {	// @audit-issue

70:        IPool(pool).borrow(_borrowAsset, _amount, _interestRateMode, 0, address(this));	// @audit-issue

72:        (,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));	// @audit-issue

83:        IPool(pool).repay(asset, amount, i, address(this));	// @audit-issue

101:        IPool(pool).withdraw(_collateral, _collateralAmount, address(this));	// @audit-issue

103:        (uint256 totalCollateralBase,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));	// @audit-issue

108:                vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", true	// @audit-issue

115:        (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this));	// @audit-issue
```
[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L48-L48), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L50-L50), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L67-L67), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L70-L70), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L72-L72), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L83-L83), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L101-L101), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L103-L103), [108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L108-L108), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L115-L115), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

57:        uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this));	// @audit-issue

58:        bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, "");	// @audit-issue

73:        uint256 beforeClaimBalance = address(this).balance;	// @audit-issue

77:        IWETH(weth).deposit{ value: address(this).balance - beforeClaimBalance }();	// @audit-issue

80:            registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, ""),	// @audit-issue
```
[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L57-L57), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L58-L58), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L73-L73), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L77-L77), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L80-L80), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

35:            bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));	// @audit-issue

37:            if (!registry.isPositionTrustedForConnector(vaultId, positionId, address(this))) {	// @audit-issue

57:        bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));	// @audit-issue

62:        zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));	// @audit-issue

77:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));	// @audit-issue

79:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue

84:        zapContract.addColl(tm, amountIn, address(this), address(this));	// @audit-issue

106:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));	// @audit-issue

107:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue

114:        borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this));	// @audit-issue

117:        uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));	// @audit-issue

131:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, troveManager));	// @audit-issue

133:        borrowerOperations.closeTrove(troveManager, address(this));	// @audit-issue

153:                ITroveManager(troveManager).getTroveCollAndDebt(address(this));	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L35-L35), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L37-L37), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L57-L57), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L62-L62), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L77-L77), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L84-L84), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L106-L106), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L107-L107), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L114-L114), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L117-L117), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L131-L131), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L133-L133), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L153-L153), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

85:        uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);	// @audit-issue

87:        bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));	// @audit-issue

100:        _YT.mintPY(address(this), address(this));	// @audit-issue

116:        market.mint(address(this), SYamount, PTamount);	// @audit-issue

155:        pendleRouter.swapExactYtForPt(address(this), market, exactYTIn, min, guess);	// @audit-issue

172:        pendleRouter.swapExactYtForSy(address(this), market, exactYTIn, min, orderData);	// @audit-issue

190:        (uint256 netSyOut, uint256 netSyFee) = market.swapExactPtForSy(address(this), exactPTIn, swapData);	// @audit-issue

205:        market.burn(address(this), address(market), amount);	// @audit-issue

222:        IPStandardizedYield(address(SY)).redeem(address(this), _amount, _underlyingToken, 1, true);	// @audit-issue

226:                registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)),	// @audit-issue

242:        market.redeemRewards(address(this));	// @audit-issue

265:            uint256 SYAmount = _SY.balanceOf(address(this));	// @audit-issue

269:                IERC20(market).balanceOf(address(this)) + pendleMarketDepositHelper.balance(market, address(this));	// @audit-issue

274:            uint256 PTAmount = _PT.balanceOf(address(this));	// @audit-issue

277:            uint256 YTBalance = _YT.balanceOf(address(this));	// @audit-issue

306:            _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0	// @audit-issue

307:                && market.balanceOf(address(this)) == 0	// @audit-issue
```
[85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L85-L85), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L87-L87), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L100-L100), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L116-L116), [155](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L155-L155), [172](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L172-L172), [190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L190-L190), [205](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L205-L205), [222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L222-L222), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L226-L226), [242](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L242-L242), [265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L265-L265), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L269-L269), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L274-L274), [277](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L277-L277), [306](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L306-L306), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L307-L307), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

39:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", false	// @audit-issue

50:        (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));	// @audit-issue

53:                vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true	// @audit-issue

65:        if (!registry.isTokenTrusted(vaultId, token, address(this))) {	// @audit-issue

73:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true	// @audit-issue

84:        if (!registry.isTokenTrusted(vaultId, token, address(this))) {	// @audit-issue

102:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true	// @audit-issue

110:            dolomiteMargin.getAccountBalances(Info(address(this), accountId));	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L39-L39), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L50-L50), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L53-L53), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L65-L65), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L73-L73), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L84-L84), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L102-L102), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L110-L110), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

93:        IDepositToken(depostiToken).deposit(address(this), amount);	// @audit-issue

122:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue

167:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue

213:        IDepositToken(depostiToken).withdraw(address(this), amount);	// @audit-issue

223:            IRewardsGauge(gauges[i]).claim_rewards(address(this));	// @audit-issue

235:            IDepositToken(pools[i]).claimReward(address(this));	// @audit-issue

250:            baseRewardPool.getReward(address(this), true);	// @audit-issue

259:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue

327:        return IConvexBasicRewards(info.convexRewardPool).balanceOf(address(this));	// @audit-issue

336:        return IERC20(info.lpToken).balanceOf(address(this));	// @audit-issue

346:        return IRewardsGauge(info.gauge).balanceOf(address(this));	// @audit-issue

356:        return IDepositToken(prismaPool).balanceOf(address(this));	// @audit-issue
```
[93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L93-L93), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L122-L122), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L167-L167), [213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L213-L213), [223](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L223-L223), [235](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L235-L235), [250](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L250-L250), [259](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L259-L259), [327](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L327-L327), [336](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L336-L336), [346](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L346-L346), [356](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L356-L356), 


#### Recommendation

To enhance gas efficiency, cache the contract's address by storing `address(this)` in a state variable at the point of contract deployment or initialization. Use this cached address throughout the contract instead of repeatedly calling `address(this)`. This practice reduces the gas cost associated with multiple computations of the contract's address, leading to more efficient contract execution, especially in scenarios with frequent usage of the contract's address.

### All variables can be packed into fewer storage slots by truncating timestamp bytes
By using a `uint32` rather than a larger type for variables that track timestamps, one can save gas by using fewer storage slots per struct, at the expense of the protocol breaking after the year 2106 (when `uint32` wraps). If this is an acceptable tradeoff, if variables occupying the same slot are both written the same function or by the constructor, avoids a separate Gsset (**20000 gas**). Reads of the variables can also be cheaper

```solidity
Path: ./contracts/governance/Keepers.sol

92:        uint256 deadline	// @audit-issue
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L92-L92), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

8:        returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

122:        uint256 updatedAt;	// @audit-issue
```
[122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L122-L122), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

17:    uint256 deadline;	// @audit-issue

26:    uint256 deadline;	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L17-L17), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L26-L26), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

16:    uint256 deadline;	// @audit-issue

24:    uint256 deadline;	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L16-L16), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

18:    uint256 deadline;	// @audit-issue

27:    uint256 deadline;	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L18-L18), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L27-L27), 


#### Recommendation

Evaluate the use of `uint32` for timestamp variables in your Solidity contracts, especially within structs that are frequently written to or read from storage. Ensure that the reduced size will not impact the functionality of your contract, particularly considering the 2106 overflow limitation. When implementing this optimization, aim to group such variables together in the same storage slot to maximize gas savings. This strategy is most effective when these variables are updated together, as in a constructor or specific functions, allowing for a single storage operation (`Gsset`) instead of multiple. Always balance the benefits of gas savings against the longevity and future-proofing of your contract.

### Counting down in for statements is more gas efficient
Looping downwards in Solidity is more gas efficient due to how the EVM compares variables. In a 'for' loop that counts down, the end condition is usually to compare with zero, which is cheaper than comparing with another number. As such, restructure your loops to count downwards where possible.

```solidity
Path: ./contracts/accountingManager/Registry.sol

138:        for (uint256 i = 0; i < _trustedTokens.length; i++) {	// @audit-issue

194:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {	// @audit-issue

214:        for (uint256 i = 0; i < _tokens.length; i++) {	// @audit-issue

253:            for (uint256 i = 0; i < usingTokens.length; i++) {	// @audit-issue

274:        for (uint256 i = 0; i < length; i++) {	// @audit-issue
```
[138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138-L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214-L214), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L253-L253), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L274-L274), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

551:        for (uint256 i = 0; i < retrieveData.length; i++) {	// @audit-issue

603:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue

608:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue
```
[551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551-L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608-L608), 


```solidity
Path: ./contracts/governance/Keepers.sol

29:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

109:                    ++i;	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29-L29), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44-L44), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L109-L109), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

18:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L18-L18), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

178:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

189:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

211:        for (uint256 i = 0; i < tokensIn.length; i++) {	// @audit-issue
```
[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211-L211), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

37:        for (uint256 i = 0; i < usersAddresses.length; i++) {	// @audit-issue

152:                i++;	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), [152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L152-L152), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

41:        for (uint256 i = 0; i < baseCurrencies.length; i++) {	// @audit-issue

55:        for (uint256 i = 0; i < oracle.length; i++) {	// @audit-issue

88:        for (uint256 i = 0; i < sources.length; i++) {	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

74:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

140:        for (uint256 i = 0; i < earnedInfo.length; i++) {	// @audit-issue
```
[140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

69:        for (uint256 i = 0; i < calls.length; i++) {	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

116:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue

132:        for (uint256 i = 0; i < assetsS.length; i++) {	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L116-L116), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

107:        for (uint8 i; i < numberOfAssets; ++i) {	// @audit-issue
```
[107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L107-L107), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

102:        for (uint256 i = 0; i < tokenIds.length; i++) {	// @audit-issue
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

54:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue

77:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54-L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

74:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

79:            for (uint256 i = 0; i < destinationConnector.length; i++) {	// @audit-issue

84:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

89:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

244:        for (uint256 i = 0; i < rewardTokens.length; i++) {	// @audit-issue
```
[244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

113:        for (uint256 i = 0; i < markets.length; i++) {	// @audit-issue
```
[113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L113-L113), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

222:        for (uint256 i = 0; i < gauges.length; i++) {	// @audit-issue

234:        for (uint256 i = 0; i < pools.length; i++) {	// @audit-issue

248:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue
```
[222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222-L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234-L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248-L248), 


#### Recommendation

Where feasible, refactor `for` loops in your Solidity contracts to count downwards. Adjust the loop initialization, condition, and iteration statements to decrement the loop variable and terminate the loop when it reaches zero. This approach can lead to gas savings, making your contract more efficient in terms of execution costs. Ensure that this refactoring aligns with the logic and requirements of your contract, and thoroughly test to confirm that the revised loop behavior matches the intended functionality.

### Use solady library where possible to save gas
The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible

```solidity
Path: ./contracts/accountingManager/Registry.sol

4:import "@openzeppelin/contracts-5.0/access/AccessControl.sol";	// @audit-issue

5:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L4-L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L5-L5), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

5:import "@openzeppelin/contracts-5.0/access/Ownable.sol";	// @audit-issue
```
[5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L5-L5), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

4:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue

5:import { ERC4626, ERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/extensions/ERC4626.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L4-L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L5-L5), 


```solidity
Path: ./contracts/governance/Keepers.sol

5:import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";	// @audit-issue
```
[5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L5-L5), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

7:import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue

8:import "@openzeppelin/contracts-5.0/token/ERC721/utils/ERC721Holder.sol";	// @audit-issue

12:import "@openzeppelin/contracts-5.0/token/ERC721/IERC721Receiver.sol";	// @audit-issue

13:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L8-L8), [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L12-L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L13-L13), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

7:import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue

8:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

4:import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";	// @audit-issue

5:import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue

8:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L4-L4), [5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L5-L5), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

4:import "@openzeppelin/contracts-5.0/access/Ownable.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L4-L4), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

6:import "@openzeppelin/contracts-5.0/access/Ownable.sol";	// @audit-issue
```
[6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L6-L6), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

7:import "@openzeppelin/contracts-5.0/access/Ownable.sol";	// @audit-issue

8:import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol";	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

4:import "@openzeppelin/contracts-5.0/access/Ownable.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L4-L4), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

4:import "@openzeppelin/contracts-5.0/access/Ownable.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L4-L4), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

6:import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L6-L6), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

4:import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L4-L4), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

4:import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L4-L4), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

6:import "@openzeppelin/contracts-5.0/token/ERC721/IERC721.sol";	// @audit-issue
```
[6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L6-L6), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

4:import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L4-L4), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

8:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue

10:import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L8-L8), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

4:import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L4-L4), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

10:import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L10-L10), 


#### Recommendation

Evaluate and, where appropriate, integrate Solady modules in your Solidity contracts as alternatives to similar OpenZeppelin imports. Focus on areas where gas efficiency can be significantly improved. Ensure that any replacement with Solady's modules does not compromise the security or functionality of your contracts. Conduct thorough testing and code reviews when making such substitutions to confirm compatibility and maintain the integrity of your application. Stay informed about updates and community feedback on both libraries to make informed decisions about their use in your projects.

### Consider using solady's 'FixedPointMathLib'
Using Solady's "FixedPointMathLib" for multiplication or division operations in Solidity can lead to significant gas savings. This library is designed to optimize fixed-point arithmetic operations, which are common in financial calculations involving tokens or currencies. By implementing more efficient algorithms and assembly optimizations, "FixedPointMathLib" minimizes the computational resources required for these operations. For contracts that frequently perform such calculations, integrating this library can reduce transaction costs, thereby enhancing overall performance and cost-effectiveness. However, developers must ensure compatibility with their existing codebase and thoroughly test for accuracy and expected behavior to avoid any unintended consequences.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

243:                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount	// @audit-issue

275:                firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount	// @audit-issue

416:                data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;	// @audit-issue

423:                uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;	// @audit-issue

484:            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);	// @audit-issue

518:            (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;	// @audit-issue
```
[243](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L243-L243), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L275-L275), [416](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L416-L416), [423](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L423-L423), [484](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L484-L484), [518](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L518-L518), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

112:            _swapRequest.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);	// @audit-issue
```
[112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L112-L112), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

81:        int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));	// @audit-issue
```
[81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81-L81), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

132:            return (amountIn * sourceTokenUnit) / uintprice;	// @audit-issue

134:        return (amountIn * uintprice) / (sourceTokenUnit);	// @audit-issue
```
[132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L132-L132), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L134-L134), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

115:        return market.lltv * convertCToL(p.collateral, market.oracle, market.collateralToken) / borrowAmount;	// @audit-issue

138:        return amount * IOracle(marketOracle).price() / ORACLE_PRICE_SCALE;	// @audit-issue
```
[115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L115-L115), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L138-L138), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

124:            totalDepositAmount += depositAmount * price / 1e18;	// @audit-issue

125:            totalBAmount += borrowAmount * price / 1e18;	// @audit-issue
```
[124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L124-L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L125-L125), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

131:        uint256 amount0 = balance * reserve0 / totalSupply;	// @audit-issue

132:        uint256 amount1 = balance * reserve1 / totalSupply;	// @audit-issue
```
[131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L131-L131), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

78:        return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase;	// @audit-issue

89:        borrowBalanceInVirtualBase = (borrowBalanceInBase * basePriceInVirtualBase) / comet.baseScale();	// @audit-issue

118:                    collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice;	// @audit-issue

119:                if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;	// @audit-issue
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L78-L78), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L89-L89), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L118-L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L119-L119), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

129:            (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;	// @audit-issue

136:        uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;	// @audit-issue
```
[129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L129-L129), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L136-L136), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

96:        return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply;	// @audit-issue
```
[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L96-L96), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

172:        return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);	// @audit-issue
```
[172](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L172-L172), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

106:        if (totalCollateralBase <= DUST_LEVEL * 1e7) {	// @audit-issue
```
[106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L106-L106), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

271:                SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;	// @audit-issue

275:            if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;	// @audit-issue

280:            if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;	// @audit-issue
```
[271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L271-L271), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L275-L275), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L280-L280), 


#### Recommendation

Consider integrating Solady's 'FixedPointMathLib' into your Solidity contracts for optimized fixed-point arithmetic operations. This library can provide substantial gas savings and enhance the performance of your contract. Before integration, evaluate how 'FixedPointMathLib' aligns with your contract’s requirements. Ensure thorough testing for accuracy and compatibility with your existing contract logic. Carefully document any changes and keep track of how these optimizations affect your contract's operations to maintain transparency and reliability in your application. Adopting 'FixedPointMathLib' should be a considered decision, balancing the benefits of gas efficiency with the need for maintaining code clarity and functionality.

### Consider using OZ EnumerateSet in place of nested mappings
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios.


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

15:    mapping(address => mapping(address => uint256)) public slippageTolerance;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L15-L15), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

14:    mapping(address => mapping(address => address[])) public priceRoutes;	// @audit-issue

16:    mapping(address => mapping(address => INoyaValueOracle)) public priceSource;	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L14-L14), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L16-L16), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

14:    mapping(address => mapping(address => address)) public assetToBaseToPool;	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L14-L14), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

20:    mapping(address => mapping(address => address)) private assetsSources;	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L20-L20), 


#### Recommendation

Consider using OpenZeppelin's EnumerableSet library as a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays, especially when managing unique elements. This library simplifies the handling of unique data sets and allows for the enumeration of elements, a feature not natively supported in Solidity. When refactoring your contract, replace nested mappings or arrays with EnumerableSet where appropriate, ensuring both gas efficiency and enhanced functionality. Be sure to understand the use cases and limitations of EnumerableSet to apply it effectively in your contract's design and implementation.

### Constant Keccak Variables Are Treated As Expressions, Not Constants
In Solidity, state variables or local variables declared with the `constant` keyword are expected to represent constant values that are determined at compile time. These constants typically do not incur any gas costs when accessed since their values are hard-coded into the contract bytecode.

However, this expected behavior deviates when using the `keccak256()` function. When a variable is initialized with a `keccak256()` hash computation, even if declared as `constant`, it isn't truly treated as a constant in the resulting bytecode. Instead, every time this "constant" is referenced, the EVM recalculates the hash. This behavior contrasts with other true constants, which are embedded directly into the bytecode and accessed without additional computations.


```solidity
Path: ./contracts/accountingManager/Registry.sol

15:    bytes32 public constant MAINTAINER_ROLE = keccak256("MAINTAINER_ROLE");	// @audit-issue

17:    bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE");	// @audit-issue

19:    bytes32 public constant EMERGENCY_ROLE = keccak256("EMERGENCY_ROLE");	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L15-L15), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L19-L19), 


```solidity
Path: ./contracts/governance/Keepers.sol

11:    bytes32 public constant TXTYPE_HASH = keccak256(	// @audit-issue
12:        "Execute(uint256 nonce,address destination,bytes data,uint256 gasLimit,address executor, uint256 deadline)"
13:    );
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L11-L13), 


#### Recommendation

Avoid using 'keccak256()' to initialize 'constant' variables in Solidity. Instead, precompute the hash value outside of the contract and assign this precomputed value to the constant. This ensures the variable is a true constant, eliminating redundant hash computations and saving gas.

### Use bitmap to save gas
Bitmaps in Solidity are essentially a way of representing a set of boolean values within an integer type variable such as `uint256`. Each bit in the integer represents a true or false value (1 or 0), thus allowing efficient storage of multiple boolean values.

Bitmaps can save gas in the Ethereum network because they condense a lot of information into a small amount of storage. In Ethereum, storage is one of the most significant costs in terms of gas usage. By reducing the amount of storage space needed, you can potentially save on gas fees.

Here's a quick comparison:

If you were to represent 256 different boolean values in the traditional way, you would have to declare 256 different `bool` variables. Given that each `bool` occupies a storage slot and each storage slot costs 20,000 gas to initialize, you would end up paying a considerable amount of gas.

On the other hand, if you were to use a bitmap, you could store these 256 boolean values within a single `uint256` variable. In other words, you'd only pay for a single storage slot, resulting in significant gas savings.

However, it's important to note that while bitmaps can provide gas efficiencies, they do add complexity to the code, making it harder to read and maintain. Also, using bitmaps is efficient only when dealing with a large number of boolean variables that are frequently changed or accessed together. 

In contrast, the straightforward counterpart to bitmaps would be using arrays or mappings to store boolean values, with each `bool` value occupying its own storage slot. This approach is simpler and more readable but could potentially be more expensive in terms of gas usage.

```solidity
Path: ./contracts/accountingManager/Registry.sol

136:        vault.connectors[vault.accountManager].enabled = true;	// @audit-issue

137:        vault.enabled = true;	// @audit-issue

139:            vault.connectors[vault.accountManager].trustedTokens[_trustedTokens[i]] = true;	// @audit-issue
```
[136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L136-L136), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L137-L137), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L139-L139), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

362:        currentWithdrawGroup.isStarted = true;	// @audit-issue

377:        currentWithdrawGroup.isFullfilled = true;	// @audit-issue
```
[362](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L362-L362), [377](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L377-L377), 


```solidity
Path: ./contracts/governance/Keepers.sol

30:            isOwner[_owners[i]] = true;	// @audit-issue

46:                isOwner[_owners[i]] = true;	// @audit-issue

49:                isOwner[_owners[i]] = false;	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L30-L30), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L46-L46), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L49-L49), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

38:            isEligibleToUse[usersAddresses[i]] = true;	// @audit-issue

81:        isEligibleToUse[_user] = true;	// @audit-issue
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L38-L38), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L81-L81), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

28:        isHandler[swapHandler] = true;	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L28-L28), 


#### Recommendation

Consider using bitmaps in your Solidity contracts when you need to store and manipulate a large set of boolean values. This approach is particularly advantageous in terms of gas efficiency for scenarios involving frequent changes or accesses to these values. However, balance this efficiency with code readability and maintainability. Ensure that the use of bitmaps is well-documented, and consider the complexity it introduces into the code. Employ bitmaps judiciously, especially when their use results in significant gas savings, and the logic they represent is a core aspect of the contract's functionality.

### Using `bool`s for storage incurs overhead
[Booleans are more expensive than uint256](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/58f635312aa21f947cae5f8578638a85aa2519f5/contracts/security/ReentrancyGuard.sol#L23-L27) or any type that takes up a full word because each write operation emits an extra SLOAD to first read the slot's contents, replace the bits taken up by the boolean, and then write back. This is the compiler's defense against contract upgrades and pointer aliasing, and it cannot be disabled.
Use `uint256(0)` and `uint256(1)` for true/false to avoid a Gwarmaccess (**[100 gas](https://gist.github.com/IllIllI000/1b70014db712f8572a72378321250058)**) for the extra SLOAD.


```solidity
Path: ./contracts/governance/Keepers.sol

10:    mapping(address => bool) public isOwner;	// @audit-issue

19:    event UpdateOwners(address[] owners, bool[] addOrRemove);	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L10-L10), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L19-L19), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

13:    mapping(address => bool) public isEligibleToUse;	// @audit-issue
```
[13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L13-L13), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

13:    mapping(address => bool) public isHandler;	// @audit-issue

14:    mapping(string => bool) public isBridgeWhiteListed;	// @audit-issue

15:    mapping(uint256 => bool) public isChainSupported;	// @audit-issue

20:    event AddedHandler(address _handler, bool state);	// @audit-issue

21:    event AddedChain(uint256 _chainId, bool state);	// @audit-issue

22:    event AddedBridgeBlacklist(string bridgeName, bool state);	// @audit-issue
```
[13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L14-L14), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L15-L15), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L20-L20), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L21-L21), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

10:    bool ethPoolIncluded;	// @audit-issue

37:    event Stake(uint256 amount, uint256 duration, bool doDelegation);	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L10-L10), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

17:    event Supply(uint256 amount, Id id, bool sOrC);	// @audit-issue

18:    event Withdraw(uint256 amount, Id id, bool sOrC);	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L17-L17), [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

12:    event Deposit(address siloToken, address dToken, uint256 amount, bool oC);	// @audit-issue

13:    event Withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition);	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L12-L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L13-L13), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

10:    bool isActive;	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

18:    event AdjustTrove(address zap, address tm, uint256 mFee, uint256 wAmount, uint256 bAmount, bool isBorrowing);	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

44:    event DecreasePosition(address market, uint256 amount, bool closePosition);	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L44-L44), 


#### Recommendation

To minimize gas overhead in your Solidity contracts, consider using `uint256(1)` and `uint256(2)` to represent `true` and `false`, respectively, instead of `bool` types for storage. This approach avoids additional `SLOAD` and `SSTORE` operations, resulting in more gas-efficient code.

### Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead
When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.
https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.html Each operation involving a `uint8` costs an extra [22-28](https://gist.github.com/IllIllI000/9388d20c70f9a4632eb3ca7836f54977) gas (depending on whether the other operand is also a variable of type `uint8`) as compared to ones involving `uint256`, due to the compiler having to clear the higher bits of the memory word before operating on the `uint8`, as well as the associated stack operations of doing so. Use a larger size then downcast where needed


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

228:        uint64 i = 0;	// @audit-issue

264:        uint64 i = 0;	// @audit-issue

330:        uint64 i = 0;	// @audit-issue

400:        uint64 i = 0;	// @audit-issue
```
[228](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L228-L228), [264](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L264-L264), [330](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L330-L330), [400](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L400-L400), 


```solidity
Path: ./contracts/governance/Keepers.sol

15:    uint8 public threshold;	// @audit-issue

27:    constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {	// @audit-issue

63:    function setThreshold(uint8 _threshold) public onlyOwner {	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L15-L15), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L27-L27), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L63-L63), 


```solidity
Path: ./contracts/governance/Watchers.sol

7:    constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L7-L7), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

8:        returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

19:    uint32 public period = 1800;	// @audit-issue

38:    function setPeriod(uint32 _period) external onlyMaintainer {	// @audit-issue

48:    function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {	// @audit-issue

61:        uint128 amountIn128 = uint128(amount);	// @audit-issue

77:        int56 tickCumulativesDelta = tickCumulatives[1] - tickCumulatives[0];	// @audit-issue

81:        int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L19-L19), [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L38), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L61-L61), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L77-L77), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81-L81), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

24:    uint32 constant TVL_UPDATE = 1;	// @audit-issue

19:    mapping(uint32 => ChainInfo) public chainInfo; // chainId => ChainInfo	// @audit-issue

40:    function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L19-L19), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

51:    function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {	// @audit-issue

78:        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;	// @audit-issue

10:    uint32 lzChainId;	// @audit-issue
```
[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L51-L51), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L78-L78), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

139:        uint8 tokenIndex;	// @audit-issue
```
[139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L139-L139), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

97:        uint16 assetsIn = userBasic.assetsIn;	// @audit-issue

104:        uint8 numberOfAssets = comet.numAssets();	// @audit-issue

107:        for (uint8 i; i < numberOfAssets; ++i) {	// @audit-issue

141:    function isInAsset(uint16 assetsIn, uint8 assetOffset) public pure returns (bool) {	// @audit-issue
```
[97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L97-L97), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L104-L104), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L107-L107), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L141-L141), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

64:        (uint128 currentLiquidity, address token0, address token1) = getCurrentLiquidity(p.tokenId);	// @audit-issue

116:    function getCurrentLiquidity(uint256 tokenId) public view returns (uint128, address, address) {	// @audit-issue

117:        (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);	// @audit-issue

133:        (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));	// @audit-issue

138:            (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);	// @audit-issue

140:            (uint160 sqrtPriceX96,,,,,,) = pool.slot0();	// @audit-issue
```
[64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L64-L64), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L116-L116), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L117-L117), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L133-L133), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L138-L138), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

30:    function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {	// @audit-issue

46:    function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {	// @audit-issue

69:        uint128 _accountId,	// @audit-issue

76:        uint128 poolId = SNXCoreProxy.getPreferredPool();	// @audit-issue

83:        uint128 _accountId,	// @audit-issue

94:    function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)	// @audit-issue

104:        uint128 _accountId,	// @audit-issue

105:        uint128 poolId,	// @audit-issue

122:        (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address));	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L30-L30), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L46-L46), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L69-L69), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L76-L76), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L83-L83), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L94-L94), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L104-L104), [105](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L105-L105), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L122-L122), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

302:        int128 tokenIndex = int128(uint128(index));	// @audit-issue
```
[302](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L302-L302), 


#### Recommendation

Minimize gas overhead by using 'uint256' or 'int256' instead of smaller integer types in Solidity contracts. The EVM operates more efficiently with 32-byte sizes. Downcast to smaller types only when necessary, as operations with smaller types like 'uint8' incur extra gas due to additional EVM operations for size adjustment.

### Use more recent OpenZeppelin version for gas boost
OpenZeppelin version 4.9.0+ provides many small gas optimizations, see [here](https://github.com/OpenZeppelin/openzeppelin-contracts/releases/tag/v4.9.0) for more info. Your project is using version: 4.8.1
```solidity
/// @audit Global finding.
```
[1](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L1), 


#### Recommendation

Consider using OpenZeppelin version 4.9.0+.

### Refactor modifiers to call a local function
Modifiers code is copied in all instances where it's used, increasing bytecode size. If deployment gas costs are a concern for this contract, refactoring modifiers into functions can reduce bytecode size significantly at the cost of one JUMP.

```solidity
Path: ./contracts/accountingManager/Registry.sol

32:    modifier onlyVaultMaintainer(uint256 _vaultId) {	// @audit-issue

39:    modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) {	// @audit-issue

46:    modifier onlyVaultGoverner(uint256 _vaultId) {	// @audit-issue

53:    modifier vaultExists(uint256 _vaultId) {	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L32-L32), [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L39-L39), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L46-L46), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L53-L53), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

31:    modifier onlyManager() {	// @audit-issue

43:    modifier onlyEmergency() {	// @audit-issue

53:    modifier onlyEmergencyOrWatcher() {	// @audit-issue

65:    modifier onlyMaintainerOrEmergency() {	// @audit-issue

75:    modifier onlyMaintainer() {	// @audit-issue

85:    modifier onlyGovernance() {	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L31-L31), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L43-L43), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L53-L53), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L65-L65), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L75-L75), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L85-L85), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

24:    modifier onlyEligibleUser() {	// @audit-issue

29:    modifier onlyExistingRoute(uint256 _routeId) {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L24-L24), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L29-L29), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

34:    modifier onlyHandler() {	// @audit-issue
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L34-L34), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

24:    modifier onlyMaintainer() {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L24-L24), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

24:    modifier onlyMaintainer() {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L24-L24), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

41:    modifier onlyMaintainer() {	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L41-L41), 


#### Recommendation

Evaluate your contract's use of modifiers, particularly those applied across multiple functions, to identify candidates for refactoring into functions. Convert these modifiers into external or public functions that perform the same checks or actions. Then, replace the modifier usage in function declarations with calls to these functions at the start of your functions

### Avoid Unnecessary Public Variables
Public state variables in Solidity automatically generate getter functions, increasing contract size and potentially leading to higher deployment and interaction costs. To optimize gas usage and contract efficiency, minimize the use of public variables unless external access is necessary. Instead, use internal or private visibility combined with explicit getter functions when required. This practice not only reduces contract size but also provides better control over data access and manipulation, enhancing security and readability. Prioritize lean, efficient contracts to ensure cost-effectiveness and better performance on the blockchain.

```solidity
Path: ./contracts/accountingManager/Registry.sol

15:    bytes32 public constant MAINTAINER_ROLE = keccak256("MAINTAINER_ROLE");	// @audit-issue

17:    bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE");	// @audit-issue

19:    bytes32 public constant EMERGENCY_ROLE = keccak256("EMERGENCY_ROLE");	// @audit-issue

21:    uint256 public constant MAX_NUM_HOLDING_POSITIONS = 40;	// @audit-issue

23:    uint256 public maxNumHoldingPositions = 20;	// @audit-issue

26:    mapping(uint256 => Vault) public vaults;	// @audit-issue

28:    address public flashLoan;	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L15-L15), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L19-L19), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L21-L21), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L23-L23), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L28-L28), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

8:    address public receiver;	// @audit-issue

9:    address public accountingManager;	// @audit-issue

10:    address public baseToken;	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L8-L8), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L9-L9), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L10-L10), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

7:import { NoyaGovernanceBase, PositionBP } from "../governance/NoyaGovernanceBase.sol";	// @audit-issue

8:import "../helpers/TVLHelper.sol";	// @audit-issue

21:    DepositQueue public depositQueue;	// @audit-issue

23:    WithdrawQueue public withdrawQueue;	// @audit-issue

27:    mapping(address => uint256) public withdrawRequestsByAddress;	// @audit-issue

30:    uint256 public amountAskedForWithdraw;	// @audit-issue

34:    uint256 public totalDepositedAmount;	// @audit-issue

37:    uint256 public totalWithdrawnAmount;	// @audit-issue

41:    uint256 public storedProfitForFee;	// @audit-issue

43:    uint256 public profitStoredTime;	// @audit-issue

45:    uint256 public lastFeeDistributionTime;	// @audit-issue

47:    uint256 public totalProfitCalculated;	// @audit-issue

50:    uint256 public preformanceFeeSharesWaitingForDistribution;	// @audit-issue

52:    uint256 public constant FEE_PRECISION = 1e6;	// @audit-issue

53:    uint256 public constant WITHDRAWAL_MAX_FEE = 5e4;	// @audit-issue

54:    uint256 public constant MANAGEMENT_MAX_FEE = 5e5;	// @audit-issue

55:    uint256 public constant PERFORMANCE_MAX_FEE = 1e5;	// @audit-issue

60:    IERC20 public baseToken;	// @audit-issue

63:    uint256 public withdrawFee; // 0.0001% = 1	// @audit-issue

65:    uint256 public performanceFee;	// @audit-issue

67:    uint256 public managementFee;	// @audit-issue

69:    address public withdrawFeeReceiver;	// @audit-issue

71:    address public performanceFeeReceiver;	// @audit-issue

73:    address public managementFeeReceiver;	// @audit-issue

79:    WithdrawGroup public currentWithdrawGroup;	// @audit-issue

82:    uint256 public depositWaitingTime = 30 minutes;	// @audit-issue

84:    uint256 public withdrawWaitingTime = 6 hours;	// @audit-issue

87:    uint256 public depositLimitTotalAmount = 1e6 * 200_000;	// @audit-issue

89:    uint256 public depositLimitPerTransaction = 1e6 * 2000;	// @audit-issue

92:    INoyaValueOracle public valueOracle;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L8-L8), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L21-L21), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L23-L23), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L27-L27), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L30-L30), [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L34-L34), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L37-L37), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L41-L41), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L43-L43), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L45-L45), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L47-L47), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L50-L50), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L52-L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L53-L53), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L54-L54), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L55-L55), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L60-L60), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L63-L63), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L65-L65), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L67-L67), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L69-L69), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L71-L71), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L73-L73), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L79-L79), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L82-L82), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L84-L84), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L87-L87), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L89-L89), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L92-L92), 


```solidity
Path: ./contracts/governance/Keepers.sol

10:    mapping(address => bool) public isOwner;	// @audit-issue

11:    bytes32 public constant TXTYPE_HASH = keccak256(	// @audit-issue

14:    uint256 public nonce;	// @audit-issue

15:    uint8 public threshold;	// @audit-issue

16:    uint256 public numOwners;	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L10-L10), [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L11-L11), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L14-L14), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L16-L16), 


```solidity
Path: ./contracts/governance/Watchers.sol





```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L10-L10), [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L11-L11), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L14-L14), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L16-L16), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

7:    PositionRegistry public registry;	// @audit-issue

8:    uint256 public vaultId;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

7:import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue

8:import "@openzeppelin/contracts-5.0/token/ERC721/utils/ERC721Holder.sol";	// @audit-issue

25:    SwapAndBridgeHandler public swapHandler;	// @audit-issue

26:    INoyaValueOracle public valueOracle;	// @audit-issue

28:    uint256 public MINIMUM_HEALTH_FACTOR = 15e17;	// @audit-issue

29:    uint256 public minimumHealthFactor;	// @audit-issue

31:    uint256 public DUST_LEVEL = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L31-L31), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

7:import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";	// @audit-issue

8:import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";	// @audit-issue

13:    mapping(address => bool) public isEligibleToUse;	// @audit-issue

14:    INoyaValueOracle public valueOracle;	// @audit-issue

15:    mapping(address => mapping(address => uint256)) public slippageTolerance;	// @audit-issue

16:    uint256 public genericSlippageTolerance = 50_000; // 5% slippage tolerance	// @audit-issue

17:    RouteData[] public routes;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L8-L8), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L14-L14), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L17-L17), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

13:    mapping(address => bool) public isHandler;	// @audit-issue

14:    mapping(string => bool) public isBridgeWhiteListed;	// @audit-issue

15:    mapping(uint256 => bool) public isChainSupported;	// @audit-issue

16:    address public lifi;	// @audit-issue

18:    bytes4 public constant LI_FI_GENERIC_SWAP_SELECTOR = 0x4630a0d8;	// @audit-issue
```
[13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L14-L14), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L16-L16), [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L18-L18), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

11:    PositionRegistry public registry;	// @audit-issue

13:    mapping(address => INoyaValueOracle) public defaultPriceSource;	// @audit-issue

14:    mapping(address => mapping(address => address[])) public priceRoutes;	// @audit-issue

16:    mapping(address => mapping(address => INoyaValueOracle)) public priceSource;	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L11-L11), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L14-L14), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L16-L16), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

14:    mapping(address => mapping(address => address)) public assetToBaseToPool;	// @audit-issue

16:    address public factory;	// @audit-issue

17:    PositionRegistry public registry;	// @audit-issue

19:    uint32 public period = 1800;	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L14-L14), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L19-L19), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

11:    PositionRegistry public registry;	// @audit-issue

14:    uint256 public chainlinkPriceAgeThreshold = 2 hours;	// @audit-issue

25:    address public constant ETH = address(0);	// @audit-issue

26:    address public constant USD = address(840);	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L11-L11), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L14-L14), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L26-L26), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

19:    mapping(uint32 => ChainInfo) public chainInfo; // chainId => ChainInfo	// @audit-issue

20:    mapping(uint256 => VaultInfo) public vaultIdToVaultInfo; // vaultId => VaultInfo	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L19-L19), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L20-L20), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

20:    mapping(uint256 => ChainInfo) public chainInfo; // chainId => ChainInfo	// @audit-issue

21:    mapping(uint256 => VaultInfo) public vaultIdToVaultInfo; // vaultId => VaultInfo	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L20-L20), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L21-L21), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

7:	// @audit-issue

8:contract OmnichainManagerBaseChain is OmnichainLogic {	// @audit-issue

25:    /**	// @audit-issue

26:     * @notice Updates the TVL for a specific chain ID based on cross-chain data received and adds it to the position.	// @audit-issue

28:     * @param chainId The ID of the chain where the TVL update originated.	// @audit-issue

29:     * @param tvl The new TVL figure to be recorded.	// @audit-issue

31:     */	// @audit-issue

17:     */	// @audit-issue

19:    constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

21:    {	// @audit-issue

22:        DUST_LEVEL = dl;	// @audit-issue

11:    uint256 public constant OMNICHAIN_POSITION_ID = 13;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L31-L31), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L19), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L21-L21), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L22-L22), [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L11-L11), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

7:/**	// @audit-issue

8: * @notice OmnichainLogic is a base contract for OmnichainManagerBaseChain and OmnichainManagerNormalChain, which are used to manage cross-chain communication and transactions.	// @audit-issue

25:    event UpdateBridgeTransactionApproval(bytes32 transactionHash, uint256 timestamp);	// @audit-issue

26:    event StartBridgeTransaction(BridgeRequest bridgeRequest, bytes32 transactionHash);	// @audit-issue

28:    /**	// @audit-issue

29:     * @notice Initializes the OmnichainLogic contract with the address of the LayerZero helper contract and base connector parameters	// @audit-issue

31:     * @param baseConnectorParams Parameters for initializing the base connector functionalities	// @audit-issue

17:    address payable public lzHelper;	// @audit-issue

19:    uint256 public constant BRIDGE_TXN_WAITING_TIME = 30 minutes;	// @audit-issue

21:    mapping(uint256 => address) public destChainAddress;	// @audit-issue

22:    mapping(bytes32 => uint256) public approvedBridgeTXN;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L31-L31), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L19-L19), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L21-L21), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L22-L22), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

7:import "../TVLHelper.sol";	// @audit-issue

8:import "../LZHelpers/LZHelperSender.sol";	// @audit-issue

25:     * This function is restricted to be called by managers only, ensuring that TVL updates are controlled and authorized.	// @audit-issue

26:     */	// @audit-issue

28:    function updateTVLInfo() external onlyManager {	// @audit-issue

29:        uint256 tvl = getTVL();	// @audit-issue

31:    }	// @audit-issue

17:     */	// @audit-issue

19:    function getTVL() public view returns (uint256) {	// @audit-issue

21:        return TVLHelper.getTVL(vaultId, registry, baseToken);	// @audit-issue

22:    }	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L31-L31), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L19-L19), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L21-L21), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

7:import "../helpers/BaseConnector.sol";	// @audit-issue

8:	// @audit-issue

25:    uint256 minTokenBAmount;	// @audit-issue

26:    uint256 deadline;	// @audit-issue

28:	// @audit-issue

29:contract MaverickConnector is BaseConnector, IERC721Receiver {	// @audit-issue

31:    address veMav;	// @audit-issue

35:    uint256 public MAVERICK_LP = 10;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L31-L31), [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L35-L35), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

7:	// @audit-issue

8:contract MorphoBlueConnector is BaseConnector {	// @audit-issue

25:        morphoBlue = IMorpho(MB);	// @audit-issue

26:    }	// @audit-issue

28:    // ------------ Connector functions -------------- //	// @audit-issue

29:    /**	// @audit-issue

31:     * @param amount - amount of tokens to supply	// @audit-issue

13:    IMorpho public immutable morphoBlue;	// @audit-issue

15:    uint256 public constant MORPHO_POSITION_ID = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L31-L31), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L13-L13), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L15-L15), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

7:	// @audit-issue

8:contract PancakeswapConnector is UNIv3Connector {	// @audit-issue

25:    // ------------ Connector functions -------------- //	// @audit-issue

26:    /**	// @audit-issue

28:     * @param tokenId - tokenId of the position	// @audit-issue

29:     */	// @audit-issue

31:    function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {	// @audit-issue

16:    event Withdraw(uint256 tokenId);	// @audit-issue

17:    // ------------ Constructor -------------- //	// @audit-issue

19:    constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

12:    IMasterchefV3 public masterchef;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L31-L31), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19-L19), [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L12-L12), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

7:/**	// @audit-issue

8: * @notice Deposit request	// @audit-issue

25:	// @audit-issue

26:    uint256 public constant STARGATE_LP_POSITION_TYPE = 1;	// @audit-issue

28:    event DepositIntoStargatePool(StargateRequest depositRequest);	// @audit-issue

29:    event WithdrawFromStargatePool(StargateRequest withdrawRequest);	// @audit-issue

31:	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L31-L31), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

7:	// @audit-issue

8:contract Gearboxv3 is BaseConnector {	// @audit-issue

25:        address c = ICreditFacadeV3(facade).openCreditAccount(address(this), new MultiCall[](0), ref);	// @audit-issue

26:        registry.updateHoldingPosition(	// @audit-issue

28:            registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),	// @audit-issue

29:            abi.encode(c),	// @audit-issue

31:            false	// @audit-issue

9:    uint256 public constant GEARBOX_POSITION_ID = 3;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L31-L31), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L9-L9), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

7:	// @audit-issue

8:contract SiloConnector is BaseConnector {	// @audit-issue

25:    /**	// @audit-issue

26:     * @notice Deposit tokens to Silo	// @audit-issue

28:     * @param dToken - token to deposit	// @audit-issue

29:     * @param amount - amount to deposit	// @audit-issue

31:     */	// @audit-issue

9:    ISiloRepository public siloRepository;	// @audit-issue

10:    uint256 public constant SILO_LP_ID = 11;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L31-L31), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L9-L9), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

7:import "../external/interfaces/Aerodrome/IVoter.sol";	// @audit-issue

8:import "../external/interfaces/Aerodrome/IGauge.sol";	// @audit-issue

25:}	// @audit-issue

26:	// @audit-issue

28:    using SafeERC20 for IERC20;	// @audit-issue

29:	// @audit-issue

31:    uint256 public constant AERODROME_POSITION_TYPE = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L31-L31), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

7:contract CompoundConnector is BaseConnector {	// @audit-issue

8:    uint256 public COMPOUND_LP = 2;	// @audit-issue

25:     * @param market - Compound market address	// @audit-issue

26:     * @param asset - asset to supply	// @audit-issue

28:     */	// @audit-issue

29:    function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

31:        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L31-L31), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

7:struct FraxPoolInfo {	// @audit-issue

8:    address collateralContract;	// @audit-issue

25:    event Withdraw(address pool, uint256 withdrawAmount);	// @audit-issue

26:    event Repay(address pool, uint256 sharesToRepay);	// @audit-issue

28:	// @audit-issue

29:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue

31:    // ------------ Connector functions -------------- //	// @audit-issue

22:    uint256 public COLLATERAL_AND_DEBT_POSITION_TYPE = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L31-L31), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

7:import "../external/interfaces/Camelot/ICamelotRouter.sol";	// @audit-issue

8:import "../external/interfaces/Camelot/ICamelotFactory.sol";	// @audit-issue

25:    uint256 minAmountA;	// @audit-issue

26:    uint256 minAmountB;	// @audit-issue

28:}	// @audit-issue

29:	// @audit-issue

31:    ICamelotRouter public router;	// @audit-issue

32:    ICamelotFactory public factory;	// @audit-issue

34:    uint256 public constant CAMELOT_POSITION_ID = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L31-L31), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L32-L32), [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L34-L34), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

7:	// @audit-issue

8:/**	// @audit-issue

25:    // ------------ Constructor -------------- //	// @audit-issue

26:	// @audit-issue

28:        BaseConnector(baseConnectorParams)	// @audit-issue

29:    {	// @audit-issue

31:        factory = IUniswapV3Factory(_factory);	// @audit-issue

16:    INonfungiblePositionManager public immutable positionManager;	// @audit-issue

17:    IUniswapV3Factory public immutable factory;	// @audit-issue

19:    uint256 public constant UNI_LP_POSITION_TYPE = 5;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L31-L31), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L17-L17), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L19-L19), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

7:struct PoolInfo {	// @audit-issue

8:    address pool;	// @audit-issue

25:	// @audit-issue

26:contract BalancerConnector is BaseConnector {	// @audit-issue

28:	// @audit-issue

29:    address public BAL;	// @audit-issue

31:	// @audit-issue

30:    address public AURA;	// @audit-issue

32:    uint256 public BALANCER_LP_POSITION = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L31-L31), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L30-L30), [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L32-L32), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

16:    PositionRegistry public registry;	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L16-L16), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

7:contract SNXV3Connector is BaseConnector, IERC721Receiver {	// @audit-issue

8:    using SafeERC20 for IERC20;	// @audit-issue

25:    function createAccount() public onlyManager {	// @audit-issue

26:        // Create account	// @audit-issue

28:    }	// @audit-issue

29:	// @audit-issue

31:        // Deposit	// @audit-issue

14:    IV3CoreProxy public SNXCoreProxy;	// @audit-issue

16:    uint256 public constant SNX_POSITION_ID = 1;	// @audit-issue

17:    uint256 public constant SNX_POOL_POSITION_ID = 2;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L31-L31), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L14-L14), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L17-L17), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

7:/*	// @audit-issue

8:    * @title AaveConnector	// @audit-issue

25:	// @audit-issue

26:    event Supply(address supplyToken, uint256 amount);	// @audit-issue

28:    event Repay(address repayToken, uint256 amount, uint256 i);	// @audit-issue

29:    event RepayWithCollateral(address repayToken, uint256 amount, uint256 i);	// @audit-issue

31:	// @audit-issue

24:    uint256 public constant AAVE_POSITION_ID = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L31-L31), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

7:contract LidoConnector is BaseConnector, ERC721Holder {	// @audit-issue

8:    address public lido;	// @audit-issue

25:        require(_steth != address(0));	// @audit-issue

26:        require(w != address(0));	// @audit-issue

28:        lidoWithdrawal = _lidoW;	// @audit-issue

29:        steth = _steth;	// @audit-issue

31:    }	// @audit-issue

9:    address public lidoWithdrawal;	// @audit-issue

10:    address public steth;	// @audit-issue

11:    address public weth;	// @audit-issue

13:    uint256 public LIDO_WITHDRAWAL_REQUEST_ID = 10;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L31-L31), [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L9-L9), [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L10-L10), [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L11-L11), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L13-L13), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

7:import { ITroveManager } from "../external/interfaces/Prisma/TroveManager/ITroveManager.sol";	// @audit-issue

8:import { IStakeNTroveZap } from "../external/interfaces/Prisma/IStakeNTroveZap.sol";	// @audit-issue

25:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue

26:    /**	// @audit-issue

28:     * @param zap The address of the StakeNTroveZap contract	// @audit-issue

29:     * @param tm The address of the TroveManager contract	// @audit-issue

31:     */	// @audit-issue

14:    uint256 public constant PRISMA_POSITION_ID = 10;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L31-L31), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L14-L14), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

7:import { IPendleMarketDepositHelper } from "../external/interfaces/Pendle/IPendleMarketDepositHelper.sol";	// @audit-issue

8:import "../external/interfaces/Pendle/IPendleRouter.sol";	// @audit-issue

25:	// @audit-issue

26:    uint256 public constant PENDLE_POSITION_ID = 11;	// @audit-issue

28:    /**	// @audit-issue

29:     * @notice throws when the output of a swap operation is insufficient	// @audit-issue

31:     * @param minSY The minimum acceptable amount of SY tokens specified for the swap	// @audit-issue

22:    IPendleMarketDepositHelper public pendleMarketDepositHelper;	// @audit-issue

23:    IPAllActionV3 public pendleRouter;	// @audit-issue

24:    IPendleStaticRouter public staticRouter;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L31-L31), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L22-L22), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L23-L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

7:import "../external/interfaces/Dolomite/IDolomiteMargin.sol";	// @audit-issue

8:	// @audit-issue

25:        depositWithdrawalProxy = IDepositWithdrawalProxy(_depositWithdrawalProxy);	// @audit-issue

26:        dolomiteMargin = IDolomiteMargin(_dolomiteMargin);	// @audit-issue

28:    }	// @audit-issue

29:	// @audit-issue

31:        // get market token	// @audit-issue

12:    IDepositWithdrawalProxy public depositWithdrawalProxy;	// @audit-issue

13:    IDolomiteMargin public dolomiteMargin;	// @audit-issue

14:    IBorrowPositionProxyV1 public borrowPositionProxy;	// @audit-issue

16:    uint256 public constant DOL_POSITION_ID = 1;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L31-L31), [12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L12-L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L14-L14), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L16-L16), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

7:import { IDepositToken } from "../external/interfaces/Prisma/IDepositToken.sol";	// @audit-issue

8:	// @audit-issue

25:    // ------------ state variables -------------- //	// @audit-issue

26:    IBooster public convexBooster;	// @audit-issue

28:    address public CRV;	// @audit-issue

29:    address public PRISMA;	// @audit-issue

31:    uint256 public constant CURVE_LP_POSITION = 4;	// @audit-issue

27:    address public CVX;	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L8-L8), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L26-L26), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L29-L29), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L31-L31), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L27-L27), 


#### Recommendation

Avoid creating explicit getter functions for 'public' state variables in Solidity. The compiler automatically generates getters for such variables, making additional functions redundant. This practice helps reduce contract size, lowers deployment costs, and simplifies maintenance and understanding of the contract.

### Use `do while` loops intead of for loops
A `do while` loop will cost less gas since the condition is not being checked for the first iteration.
```solidity
uint256 i = 1;
do {                   
    param2 += i;
    i++;
}
while (i < 50);
``` 
is better than
```solidity
for(uint256 i = 1; i< 50; i++){
    param1 += i;
}
```


```solidity
Path: ./contracts/accountingManager/Registry.sol

138:        for (uint256 i = 0; i < _trustedTokens.length; i++) {	// @audit-issue

194:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {	// @audit-issue

214:        for (uint256 i = 0; i < _tokens.length; i++) {	// @audit-issue

253:            for (uint256 i = 0; i < usingTokens.length; i++) {	// @audit-issue

274:        for (uint256 i = 0; i < length; i++) {	// @audit-issue
```
[138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L138-L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L214-L214), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L253-L253), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L274-L274), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

551:        for (uint256 i = 0; i < retrieveData.length; i++) {	// @audit-issue

603:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue

608:            for (uint256 i = 0; i < items.length; i++) {	// @audit-issue
```
[551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L551-L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L603-L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L608-L608), 


```solidity
Path: ./contracts/governance/Keepers.sol

29:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < _owners.length; i++) {	// @audit-issue

104:            for (uint256 i = 0; i < threshold;) {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L29-L29), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L44-L44), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L104-L104), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

18:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue

44:        for (uint256 i = 0; i < positions.length; i++) {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L18-L18), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L44-L44), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

178:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

189:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

211:        for (uint256 i = 0; i < tokensIn.length; i++) {	// @audit-issue
```
[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178-L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L189-L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L211-L211), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

37:        for (uint256 i = 0; i < usersAddresses.length; i++) {	// @audit-issue

148:        for (uint256 i = 0; i < _routes.length;) {	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), [148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L148), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

41:        for (uint256 i = 0; i < baseCurrencies.length; i++) {	// @audit-issue

55:        for (uint256 i = 0; i < oracle.length; i++) {	// @audit-issue

88:        for (uint256 i = 0; i < sources.length; i++) {	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

74:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

140:        for (uint256 i = 0; i < earnedInfo.length; i++) {	// @audit-issue
```
[140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L140-L140), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

69:        for (uint256 i = 0; i < calls.length; i++) {	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

116:        for (uint256 i = 0; i < assets.length; i++) {	// @audit-issue

132:        for (uint256 i = 0; i < assetsS.length; i++) {	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L116-L116), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L132-L132), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

107:        for (uint8 i; i < numberOfAssets; ++i) {	// @audit-issue
```
[107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L107-L107), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

102:        for (uint256 i = 0; i < tokenIds.length; i++) {	// @audit-issue
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

54:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue

77:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L54-L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

74:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

79:            for (uint256 i = 0; i < destinationConnector.length; i++) {	// @audit-issue

84:            for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue

89:        for (uint256 i = 0; i < tokens.length; i++) {	// @audit-issue
```
[74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

244:        for (uint256 i = 0; i < rewardTokens.length; i++) {	// @audit-issue
```
[244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L244-L244), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

113:        for (uint256 i = 0; i < markets.length; i++) {	// @audit-issue
```
[113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L113-L113), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

222:        for (uint256 i = 0; i < gauges.length; i++) {	// @audit-issue

234:        for (uint256 i = 0; i < pools.length; i++) {	// @audit-issue

248:        for (uint256 i = 0; i < rewardsPools.length; i++) {	// @audit-issue
```
[222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L222-L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L234-L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L248-L248), 


#### Recommendation

Where appropriate, consider using a `do while` loop instead of a `for` loop in your Solidity contracts. This is especially beneficial when the first iteration of the loop does not require a condition check. Refactor your loop logic to fit the `do while` structure for more gas-efficient execution. However, ensure that the loop's logic and termination conditions are correctly implemented to avoid infinite loops or other logical errors. Always balance gas efficiency with code readability and the specific requirements of your contract's logic.

### Using XOR (^) and AND (&) bitwise equivalents for gas optimizations
Given 4 variables a, b, c and d represented as such:
```
0 0 0 0 0 1 1 0 <- a
0 1 1 0 0 1 1 0 <- b
0 0 0 0 0 0 0 0 <- c
1 1 1 1 1 1 1 1 <- d
```
To have a == b means that every 0 and 1 match on both variables. Meaning that a XOR (operator ^) would evaluate to 0 ((a ^ b) == 0), as it excludes by definition any equalities.Now, if a != b, this means that there’s at least somewhere a 1 and a 0 not matching between a and b, making (a ^ b) != 0.Both formulas are logically equivalent and using the XOR bitwise operator costs actually the same amount of gas.However, it is much cheaper to use the bitwise OR operator (|) than comparing the truthy or falsy values.These are logically equivalent too, as the OR bitwise operator (|) would result in a 1 somewhere if any value is not 0 between the XOR (^) statements, meaning if any XOR (^) statement verifies that its arguments are different.


```solidity
Path: ./contracts/accountingManager/Registry.sol

33:        if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

40:        if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

47:        if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

54:        if (vaults[_vaultId].accountManager == address(0)) revert NotExist();	// @audit-issue

251:            if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();	// @audit-issue

275:            if (vault.holdingPositions[i].positionId == _positionId) {	// @audit-issue

304:        if (index == 0) {	// @audit-issue

347:        if (positionIndex == 0 && removePosition) return type(uint256).max;	// @audit-issue

442:        return position.isEnabled && (!position.onlyOwner || position.calculatorConnector == connector);	// @audit-issue

526:        if (addr == vaults[vaultId].accountManager) return true;	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L33-L33), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L40-L40), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L47-L47), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L54-L54), [251](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L251-L251), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L275-L275), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L304-L304), [347](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L347-L347), [442](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L442-L442), [526](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L526-L526), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

186:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {	// @audit-issue

201:        if (amount == 0) {	// @audit-issue

335:        if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {	// @audit-issue

361:        require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

371:        require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

397:        if (currentWithdrawGroup.isFullfilled == false) {	// @audit-issue

443:        if (currentWithdrawGroup.lastId == firstTemp) {	// @audit-issue

528:            preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours	// @audit-issue

619:            currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true	// @audit-issue

634:        if (p.positionTypeId == 0) {	// @audit-issue

643:        if (token == base) {	// @audit-issue

650:        if (positionTypeId == 0) {	// @audit-issue

684:        if (token == address(0)) {	// @audit-issue
```
[186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186-L186), [201](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L201-L201), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L335-L335), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361-L361), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371-L371), [397](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L397-L397), [443](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L443-L443), [528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528-L528), [619](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L619-L619), [634](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L634-L634), [643](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L643-L643), [650](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L650-L650), [684](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L684-L684), 


```solidity
Path: ./contracts/governance/Keepers.sol

95:        require(sigR.length == threshold, "Not enough signatures");	// @audit-issue

96:        require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");	// @audit-issue

97:        require(executor == msg.sender, "Invalid executor");	// @audit-issue
```
[95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L95-L95), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L96-L96), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L97-L97), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

33:        if (!(msg.sender == keeperContract || msg.sender == emergencyManager || msg.sender == registry.flashLoan())) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L33-L33), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

19:            if (positions[i].calculatorConnector == address(0)) {	// @audit-issue

45:            if (latestUpdateTime == 0 || positions[i].positionTimestamp < latestUpdateTime) {	// @audit-issue

49:        if (latestUpdateTime == 0) {	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L19-L19), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L45-L45), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L49-L49), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

90:        if (msg.sender == accountingManager) {	// @audit-issue

98:        } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {	// @audit-issue

142:        if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {	// @audit-issue

159:        _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0);	// @audit-issue

233:        if (positionTypeId == 0) {	// @audit-issue

254:        if (token == baseToken) {	// @audit-issue

257:        if (amount == 0) {	// @audit-issue
```
[90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L90-L90), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L98-L98), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L142-L142), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L159-L159), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L233-L233), [254](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L254-L254), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L257-L257), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30:        if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();	// @audit-issue

98:        if (_swapRequest.amount == 0) revert InvalidAmount();	// @audit-issue

102:        if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {	// @audit-issue

105:            if (_slippageTolerance == 0) {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30-L30), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L98-L98), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L102-L102), [105](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L105-L105), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

35:        require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER");	// @audit-issue

86:        if (_request.outputToken == address(0)) {	// @audit-issue

93:        if (_request.outputToken == address(0)) {	// @audit-issue

153:        if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();	// @audit-issue

154:        if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId();	// @audit-issue

190:        return address(token) == address(0);	// @audit-issue

194:        if (token == address(0)) {	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35-L35), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L86-L86), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L93-L93), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153-L153), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L154-L154), [190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L190-L190), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L194-L194), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

72:        if (asset == baseToken || amount == 0) {	// @audit-issue

97:        if (address(oracle) == address(0)) {	// @audit-issue

100:        if (address(oracle) == address(0)) {	// @audit-issue

103:        if (address(oracle) == address(0)) {	// @audit-issue

106:        if (address(oracle) == address(0)) {	// @audit-issue
```
[72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L72-L72), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L97-L97), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L100-L100), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L103-L103), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L106-L106), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

39:        if (_period == 0) revert INoyaValueOracle_InvalidInput();	// @audit-issue

63:        if (pool == address(0)) {	// @audit-issue

66:        if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L39-L39), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L63-L63), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L66-L66), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

90:        if (asset == baseToken) {	// @audit-issue

95:        if (primarySource == address(0)) {	// @audit-issue

99:        decimalsSource = decimalsSource == ETH || decimalsSource == USD ? primarySource : decimalsSource;	// @audit-issue
```
[90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L90-L90), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L95-L95), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L99-L99), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

53:        if (positionTypeId == OMNICHAIN_POSITION_ID) {	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L53-L53), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

71:        if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {	// @audit-issue

76:            destChainAddress[bridgeRequest.destChainId] == address(0)	// @audit-issue
```
[71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71-L71), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L76-L76), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

35:        if (bp.positionTypeId == 0) {	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L35-L35), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

66:        if (p.collateral == 0 && p.supplyShares == 0) {	// @audit-issue

112:        if (borrowAmount == 0) return type(uint256).max;	// @audit-issue

120:        if (positionInfo.positionTypeId == MORPHO_POSITION_ID) {	// @audit-issue
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L66-L66), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L112-L112), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L120-L120), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

59:            if (depositRequest.LPStakingAmount == type(uint256).max) {	// @audit-issue

89:        if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) {	// @audit-issue

115:        if (lpAmount == 0) {	// @audit-issue
```
[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L59-L59), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L89-L89), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L115-L115), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

73:            if (method == ICreditFacadeV3Multicall.enableToken.selector) {	// @audit-issue
```
[73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L73-L73), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

120:            if (depositAmount == 0 && borrowAmount == 0) {	// @audit-issue
```
[120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L120-L120), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

92:        if (IERC20(data.pool).balanceOf(address(this)) == 0) {	// @audit-issue
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

53:        if (getCollBlanace(IComet(_market), false) == 0) {	// @audit-issue

77:        if (borrowBalanceInBase == 0) return type(uint256).max;	// @audit-issue

86:        if (borrowBalanceInBase == 0) return 0;	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L53-L53), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L77-L77), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L86-L86), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

70:        if (withdrawAmount == currentCollateral) {	// @audit-issue

124:        if (_borrowerAmount == 0) return type(uint256).max;	// @audit-issue

126:        if (_collateralAmount == 0) return 0;	// @audit-issue

133:        if (currentPositionLTV == 0) return type(uint256).max; // loan is small	// @audit-issue
```
[70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L70-L70), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L124-L124), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L126-L126), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L133-L133), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

77:        if (IERC20(pool).balanceOf(address(this)) == 0) {	// @audit-issue
```
[77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

73:        if (currentLiquidity == p.liquidity) {	// @audit-issue
```
[73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L73-L73), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

146:            if (totalLpBalanceOf(p.poolId) == 0) {	// @audit-issue
```
[146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L146-L146), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

61:        require(msg.sender == address(vault));	// @audit-issue

70:        if (!(caller == keeperContract)) {	// @audit-issue

92:            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");	// @audit-issue
```
[61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L61-L61), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L70-L70), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

51:        if (c == 0) {	// @audit-issue
```
[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L51-L51), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

79:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue

107:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue

147:        if (positionInfo.positionTypeId == PRISMA_POSITION_ID) {	// @audit-issue
```
[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L79-L79), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L107-L107), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L147-L147), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

259:        if (positionInfo.positionTypeId == PENDLE_POSITION_ID) {	// @audit-issue

306:            _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0	// @audit-issue

307:                && market.balanceOf(address(this)) == 0	// @audit-issue
```
[259](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L259-L259), [306](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L306-L306), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L307-L307), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

51:        if (markets.length == 0) {	// @audit-issue
```
[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L51-L51), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

128:        if (poolInfo.tokens.length == 2) {	// @audit-issue

132:        } else if (poolInfo.tokens.length == 3) {	// @audit-issue

136:        } else if (poolInfo.tokens.length == 4) {	// @audit-issue

140:        } else if (poolInfo.tokens.length == 5) {	// @audit-issue

144:        } else if (poolInfo.tokens.length == 6) {	// @audit-issue

171:        if (totalLpBalanceOf(poolInfo) == 0) {	// @audit-issue

280:        if (balance == 0) return (0, info.tokens[info.defaultWithdrawIndex]);	// @audit-issue

326:        if (info.convexRewardPool == address(0)) return 0;	// @audit-issue

345:        if (info.gauge == address(0)) return 0;	// @audit-issue

355:        if (prismaPool == address(0)) return 0;	// @audit-issue
```
[128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L128-L128), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L132-L132), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L136-L136), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L140-L140), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L144-L144), [171](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L171-L171), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L280-L280), [326](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L326-L326), [345](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L345-L345), [355](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L355-L355), 


#### Recommendation

Review your Solidity contracts to identify any computations that are performed multiple times with the same inputs. Cache the results of these computations in local variables and reuse them within the function or across function calls if the state remains unchanged.

### Consider using `bytes32` rather than a `string`
Using the bytes types for fixed-length strings is more efficient than having the EVM have to incur the overhead of string processing. Consider whether the value needs to be a string. A good reason to keep it as a string would be if the variable is defined in an interface that this project does not own.


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

14:    mapping(string => bool) public isBridgeWhiteListed;	// @audit-issue

22:    event AddedBridgeBlacklist(string bridgeName, bool state);	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L14-L14), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L22-L22), 


#### Recommendation

For fixed-length strings, prefer using 'bytes32' over 'string' to leverage EVM efficiency and reduce overhead. Evaluate the necessity of using a string, especially if the variable isn't part of an externally defined interface.

### The result of a function call should be cached rather than re-calling the function
The function calls in solidity are expensive. If the same result of the same function calls are to be used several times, the result should be cached to reduce the gas consumption of repeated calls.        

```solidity
Path: ./contracts/accountingManager/Registry.sol

347:        if (positionIndex == 0 && removePosition) return type(uint256).max;	// @audit-issue: Function call is called multiple times at line(s) [362].
```
[347](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L347-L347), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

186:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {	// @audit-issue: Function call `balanceOf` is called multiple times at lines [187].

305:        if (balanceOf(msg.sender) < share + withdrawRequestsByAddress[msg.sender]) {	// @audit-issue: Function call `balanceOf` is called multiple times at lines [307].

458:                revert NoyaAccounting_INVALID_AMOUNT();	// @audit-issue: Function call `NoyaAccounting_INVALID_AMOUNT` is called multiple times at lines [465].

559:            uint256 balanceAfter = baseToken.balanceOf(address(this));	// @audit-issue: Function call `balanceOf` is called multiple times at lines [555].
```
[186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186-L186), [305](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L305-L305), [458](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L458-L458), [559](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L559-L559), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

104:            IERC20(token).safeTransfer(msg.sender, amount);	// @audit-issue: Function call `IERC20` is called multiple times at lines [96, 99].

144:            registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);	// @audit-issue: Function call `encode` is called multiple times at lines [141].

182:            uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue: Function call `balanceOf` is called multiple times at lines [180].

182:            uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue: Function call `IERC20` is called multiple times at lines [180].

278:        uint256 currentAllowance = IERC20(_token).allowance(address(this), _spender);	// @audit-issue: Function call `IERC20` is called multiple times at lines [282].
```
[104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L104-L104), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L144-L144), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L182-L182), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L182-L182), [278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L278-L278), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

96:            balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);	// @audit-issue: Function call `balanceOf` is called multiple times at lines [89].

89:            balanceOut0 = IERC20(_request.outputToken).balanceOf(_request.from);	// @audit-issue: Function call `IERC20` is called multiple times at lines [96].
```
[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L96-L96), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L89-L89), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

93:        _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); // TODO: check token A is eth	// @audit-issue: Function call `tokenA` is called multiple times at lines [105].

94:        _approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);	// @audit-issue: Function call `tokenB` is called multiple times at lines [106].

120:        IMaverickPosition position = IMaverickRouter(maverickRouter).position();	// @audit-issue: Function call `IMaverickRouter` is called multiple times at lines [122].

165:        tokens[1] = IMaverickPool(pool).tokenB();	// @audit-issue: Function call `IMaverickPool` is called multiple times at lines [164].
```
[93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L93-L93), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L94-L94), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L120-L120), [165](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L165-L165), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

83:        if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {	// @audit-issue: Function call `getHealthFactor` is called multiple times at lines [84].

83:        if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {	// @audit-issue: Function call `market` is called multiple times at lines [84].
```
[83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L83-L83), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L83-L83), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

118:        address underlyingToken = IStargatePool(lpAddress).token();	// @audit-issue: Function call `IStargatePool` is called multiple times at lines [119].
```
[118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L118-L118), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

83:            _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());	// @audit-issue: Function call `creditManager` is called multiple times at lines [79].

81:        ICreditFacadeV3(facade).multicall(creditAccount, calls);	// @audit-issue: Function call `ICreditFacadeV3` is called multiple times at lines [83, 79].
```
[83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L83-L83), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L81-L81), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

58:            IPool(data.pool).token0(),	// @audit-issue: Function call `token0` is called multiple times at lines [55, 69].

60:            IPool(data.pool).stable(),	// @audit-issue: Function call `IPool` is called multiple times at lines [70, 58, 59, 55, 69, 56].

70:        _updateTokenInRegistry(IPool(data.pool).token1());	// @audit-issue: Function call `token1` is called multiple times at lines [56, 59].

95:        _updateTokenInRegistry(IPool(data.pool).token0());	// @audit-issue: Function call `token0` is called multiple times at lines [83].

85:            IPool(data.pool).stable(),	// @audit-issue: Function call `IPool` is called multiple times at lines [95, 83, 96, 84].

96:        _updateTokenInRegistry(IPool(data.pool).token1());	// @audit-issue: Function call `token1` is called multiple times at lines [84].

113:        IGauge(gauge).getReward(address(this));	// @audit-issue: Function call `IGauge` is called multiple times at lines [114].

121:        tokens[1] = IPool(pool).token1();	// @audit-issue: Function call `IPool` is called multiple times at lines [120].

128:        uint256 balance = IERC20(pool).balanceOf(address(this));	// @audit-issue: Function call `IERC20` is called multiple times at lines [129].

130:        (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();	// @audit-issue: Function call `IPool` is called multiple times at lines [133, 133].
```
[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L58-L58), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L60-L60), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L70-L70), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L95-L95), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L85-L85), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L96-L96), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L113-L113), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L121-L121), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L128-L128), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L130-L130), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

53:        if (getCollBlanace(IComet(_market), false) == 0) {	// @audit-issue: Function call `IComet` is called multiple times at lines [49, 51].

65:        IRewards(rewardContract).claim(address(market), address(this), true);	// @audit-issue: Function call `IRewards` is called multiple times at lines [64].

131:        return (valueOracle.getValue(IComet(market).baseToken(), base, balance));	// @audit-issue: Function call `IComet` is called multiple times at lines [129, 128].
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L53-L53), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L65-L65), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L131-L131), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

133:        if (currentPositionLTV == 0) return type(uint256).max; // loan is small	// @audit-issue: Function call is called multiple times at line(s) [124].

146:        tokens[1] = IFraxPair(pool).asset();	// @audit-issue: Function call `IFraxPair` is called multiple times at lines [145].
```
[133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L133-L133), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L146-L146), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

92:        uint256 totalSupply = IERC20(pool).totalSupply();	// @audit-issue: Function call `IERC20` is called multiple times at lines [95].
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

123:        CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max);	// @audit-issue: Function call is called multiple times at line(s) [123].
```
[123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L123-L123), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

75:        address pool = IBalancerVault(balancerVault).getPool(poolId);	// @audit-issue: Function call `IBalancerVault` is called multiple times at lines [81, 73].

130:            IBalancerVault(balancerVault).exitPool(	// @audit-issue: Function call `IBalancerVault` is called multiple times at lines [125].
```
[75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L75-L75), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L130-L130), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

70:        IPool(pool).borrow(_borrowAsset, _amount, _interestRateMode, 0, address(this));	// @audit-issue: Function call `IPool` is called multiple times at lines [72].

101:        IPool(pool).withdraw(_collateral, _collateralAmount, address(this));	// @audit-issue: Function call `IPool` is called multiple times at lines [103].
```
[70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L70-L70), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L101-L101), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

71:        ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);	// @audit-issue: Function call `ILidoWithdrawal` is called multiple times at lines [75].
```
[71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L71-L71), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

115:        _updateTokenInRegistry(ITroveManager(tm).debtToken());	// @audit-issue: Function call `debtToken` is called multiple times at lines [112].

112:            _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount);	// @audit-issue: Function call `ITroveManager` is called multiple times at lines [115, 117].

153:                ITroveManager(troveManager).getTroveCollAndDebt(address(this));	// @audit-issue: Function call `ITroveManager` is called multiple times at lines [151].
```
[115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L115-L115), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L112-L112), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L153-L153), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

271:                SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;	// @audit-issue: Function call `IPMarket` is called multiple times at lines [275, 262].
```
[271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L271-L271), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

147:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue: Function call `add_liquidity` is called multiple times at lines [139, 143, 131, 135].

135:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue: Function call `ICurveSwap` is called multiple times at lines [131, 147, 139, 143].
```
[147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L147-L147), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L135-L135), 


#### Recommendation

Cache the result of function calls in Solidity instead of making repeated calls to the same function. This practice significantly reduces gas consumption by minimizing costly function call operations.

### Avoid updating storage when the value hasn't changed
Manipulating storage in solidity is gas-intensive. It can be optimized by avoiding unnecessary storage updates when the new value equals the existing value. If the old value is equal to the new value, not re-storing the value will avoid a Gsreset (2900 gas), potentially at the expense of a Gcoldsload (2100 gas) or a Gwarmaccess (100 gas).

```solidity
Path: ./contracts/accountingManager/Registry.sol

86:        flashLoan = _flashLoan;	// @audit-issue

174:        vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock;	// @audit-issue

177:        vaults[vaultId].emergency = _emergency;	// @audit-issue

380:            vaults[vaultId].holdingPositions[positionIndex].positionTimestamp = positionTimestamp;	// @audit-issue
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L86-L86), [174](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L174-L174), [177](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L177-L177), [380](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L380-L380), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

126:        valueOracle = _valueOracle;	// @audit-issue

215:        depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);	// @audit-issue

313:        withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);	// @audit-issue

668:        depositLimitPerTransaction = _depositLimitPerTransaction;	// @audit-issue

669:        depositLimitTotalAmount = _depositTotalAmount;	// @audit-issue

674:        depositWaitingTime = _depositWaitingTime;	// @audit-issue

679:        withdrawWaitingTime = _withdrawWaitingTime;	// @audit-issue
```
[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L126-L126), [215](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L215-L215), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L313-L313), [668](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L668-L668), [669](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L669-L669), [674](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L674-L674), [679](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L679-L679), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

59:        swapHandler = SwapAndBridgeHandler(_swapHandler);	// @audit-issue

68:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue
```
[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L59-L59), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L68-L68), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

49:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue

58:        genericSlippageTolerance = _slippageTolerance;	// @audit-issue

72:        slippageTolerance[_inputToken][_outputToken] = _slippageTolerance;	// @audit-issue

159:        routes[_routeId].isEnabled = enable;	// @audit-issue
```
[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L49-L49), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L58-L58), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L72-L72), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L159-L159), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

46:        isHandler[_handler] = state;	// @audit-issue

56:        isChainSupported[_chainId] = state;	// @audit-issue

66:        isBridgeWhiteListed[bridgeName] = state;	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L46-L46), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L56-L56), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L66-L66), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

42:            defaultPriceSource[baseCurrencies[i]] = oracles[i];	// @audit-issue

56:            priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);	// @audit-issue

62:        priceRoutes[asset][base] = s;	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L42-L42), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L62-L62), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

75:            assetsSources[assets[i]][baseTokens[i]] = sources[i];	// @audit-issue
```
[75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

42:        chainInfo[lzChainId] = ChainInfo(chainId, lzHelperAddress);	// @audit-issue

54:        vaultIdToVaultInfo[vaultId] = VaultInfo(baseChainId, omniChainManager);	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L42-L42), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L54-L54), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

37:        messageSetting = _messageSetting;	// @audit-issue

53:        chainInfo[chainId] = ChainInfo(lzChainId, lzHelperAddress);	// @audit-issue

64:        vaultIdToVaultInfo[vaultId] = VaultInfo(baseChainId, omniChainManager);	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L37-L37), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L64-L64), 


#### Recommendation

Optimize gas usage by avoiding storage updates in Solidity when the new value is the same as the existing one. This prevents unnecessary gas expenditure from storage resets, balancing the cost against cold or warm storage access as needed.

### Avoid zero transfers calls
In Solidity, unnecessary operations can waste gas. For example, a transfer function without a zero amount check uses gas even if called with a zero amount, since the contract state remains unchanged. Implementing a zero amount check avoids these unnecessary function calls, saving gas and improving efficiency.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

156:            IERC20(token).safeTransfer(address(msg.sender), amount);	// @audit-issue

688:            IERC20(token).safeTransfer(msg.sender, amount);	// @audit-issue
```
[156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L156-L156), [688](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L688-L688), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

99:            IERC20(token).safeTransfer(address(msg.sender), amount);	// @audit-issue

104:            IERC20(token).safeTransfer(msg.sender, amount);	// @audit-issue
```
[99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L99-L99), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L104-L104), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

198:            IERC20(token).safeTransfer(userAddress, amount);	// @audit-issue
```
[198](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L198-L198), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

99:        IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);	// @audit-issue

114:        IERC20(address(_SY)).safeTransfer(address(market), SYamount);	// @audit-issue

115:        IERC20(address(_PT)).safeTransfer(address(market), PTamount);	// @audit-issue

189:        IERC20(address(_PT)).safeTransfer(address(market), exactPTIn);	// @audit-issue

204:        IERC20(address(market)).safeTransfer(address(market), amount);	// @audit-issue

221:        IERC20(address(SY)).safeTransfer(address(SY), _amount);	// @audit-issue
```
[99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L99-L99), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L114-L114), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L115-L115), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L189-L189), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L204-L204), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L221-L221), 


#### Recommendation

Include a condition in your transfer functions to check for and prevent zero-value transfers. Implement a `require(amount > 0, "Transfer amount must be greater than zero");` statement at the beginning of the function. This preemptive check ensures that the function only proceeds with non-zero transfer amounts, avoiding wasteful operations and saving gas. Apply this optimization across all functions involving token transfers or similar operations to improve your contract's gas efficiency and operational effectiveness.

### Empty Blocks Should Be Removed Or Emit Something
The code should be refactored such that empty blocks no longer exist, or the block should do something useful, such as emitting an event or reverting. Empty blocks can introduce confusion and potential errors when the code is modified in the future.


```solidity
Path: ./contracts/governance/Watchers.sol

8:    function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L8-L8), 


#### Recommendation

Remove empty blocks in Solidity code to avoid confusion and potential errors. If a block is necessary, ensure it performs a useful action, like emitting an event or reverting, to justify its presence and clarify its purpose.

### Functions guaranteed to `revert` when called by normal users can be marked `payable`
If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided.

```solidity
Path: ./contracts/accountingManager/Registry.sol

79:    function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) {	// @audit-issue

84:    function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {	// @audit-issue

106:    function addVault(	// @audit-issue

158:    function changeVaultAddresses(	// @audit-issue

188:    function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)	// @audit-issue

207:    function updateConnectorTrustedTokens(	// @audit-issue

238:    function addTrustedPosition(	// @audit-issue

266:    function removeTrustedPosition(uint256 vaultId, bytes32 _positionId)	// @audit-issue
```
[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L84-L84), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L106-L106), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L158-L158), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L188-L188), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L207-L207), [238](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L238-L238), [266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L266-L266), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

23:    function withdrawShares(uint256 amount) external onlyOwner {	// @audit-issue

27:    function burnShares(uint256 amount) external onlyOwner {	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L23-L23), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L27-L27), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

124:    function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {	// @audit-issue

135:    function setFeeReceivers(	// @audit-issue

170:    function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer {	// @audit-issue

226:    function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {	// @audit-issue

257:    function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)	// @audit-issue

328:    function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {	// @audit-issue

360:    function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {	// @audit-issue

370:    function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {	// @audit-issue

396:    function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {	// @audit-issue

453:    function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager {	// @audit-issue

475:    function recordProfitForFee() public onlyManager nonReentrant {	// @audit-issue

505:    function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {	// @audit-issue

526:    function collectPerformanceFees() public onlyManager nonReentrant {	// @audit-issue

548:    function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {	// @audit-issue

659:    function emergencyStop() public whenNotPaused onlyEmergency {	// @audit-issue

663:    function unpause() public whenPaused onlyEmergency {	// @audit-issue

667:    function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {	// @audit-issue

673:    function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {	// @audit-issue

678:    function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {	// @audit-issue

683:    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {	// @audit-issue
```
[124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L124-L124), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L135-L135), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L170-L170), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L226-L226), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L257-L257), [328](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L328-L328), [360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L360-L360), [370](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L370-L370), [396](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L396-L396), [453](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L453-L453), [475](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L475-L475), [505](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L505-L505), [526](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L526-L526), [548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L548-L548), [659](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L659-L659), [663](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L663-L663), [667](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L667-L667), [673](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L673-L673), [678](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L678-L678), [683](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L683-L683), 


```solidity
Path: ./contracts/governance/Keepers.sol

42:    function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {	// @audit-issue

63:    function setThreshold(uint8 _threshold) public onlyOwner {	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42-L42), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L63-L63), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

45:    function updateMinimumHealthFactor(uint256 _minimumHealthFactor) external onlyMaintainer {	// @audit-issue

58:    function updateSwapHandler(address payable _swapHandler) external onlyMaintainer {	// @audit-issue

67:    function updateValueOracle(address _valueOracle) external onlyMaintainer {	// @audit-issue

122:    function transferPositionToAnotherConnector(	// @audit-issue

153:    function updateTokenInRegistry(address token) public onlyManager {	// @audit-issue

204:    function swapHoldings(	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L45-L45), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L58-L58), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L67-L67), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122-L122), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L153-L153), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L204), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

48:    function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {	// @audit-issue

57:    function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {	// @audit-issue

68:    function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)	// @audit-issue

80:    function addEligibleUser(address _user) external onlyMaintainerOrEmergency {	// @audit-issue

147:    function addRoutes(RouteData[] memory _routes) public onlyMaintainer {	// @audit-issue

158:    function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {	// @audit-issue

164:    function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) {	// @audit-issue
```
[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L48), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L57), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L68), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147-L147), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L158-L158), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164-L164), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

45:    function addHandler(address _handler, bool state) external onlyOwner {	// @audit-issue

55:    function addChain(uint256 _chainId, bool state) external onlyOwner {	// @audit-issue

65:    function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {	// @audit-issue

193:    function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55-L55), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L65), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L193), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

37:    function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)	// @audit-issue

51:    function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)	// @audit-issue

61:    function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L51), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

38:    function setPeriod(uint32 _period) external onlyMaintainer {	// @audit-issue

48:    function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {	// @audit-issue
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L38), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

56:    function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {	// @audit-issue

70:    function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)	// @audit-issue
```
[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L56-L56), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L70), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

40:    function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {	// @audit-issue

52:    function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {	// @audit-issue
```
[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

36:    function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {	// @audit-issue

51:    function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {	// @audit-issue

63:    function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L51-L51), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L63-L63), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

46:    function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer {	// @audit-issue

57:    function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {	// @audit-issue

68:    function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46-L46), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57-L57), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

28:    function updateTVLInfo() external onlyManager {	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

64:    function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant {	// @audit-issue

78:    function unstake(uint256 lockupId) external onlyManager nonReentrant {	// @audit-issue

91:    function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {	// @audit-issue

115:    function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)	// @audit-issue

137:    function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {	// @audit-issue
```
[64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L64-L64), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L78-L78), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L91-L91), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L115-L115), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L137-L137), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

35:    function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {	// @audit-issue

58:    function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {	// @audit-issue

80:    function borrow(uint256 amount, Id id) external onlyManager nonReentrant {	// @audit-issue

95:    function repay(uint256 amount, Id id) public onlyManager nonReentrant {	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L35-L35), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L58-L58), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L80-L80), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L95-L95), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

31:    function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {	// @audit-issue

40:    function updatePosition(uint256 tokenId) public onlyManager nonReentrant {	// @audit-issue

50:    function withdraw(uint256 tokenId) public onlyManager nonReentrant {	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L31-L31), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L40-L40), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L50-L50), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

49:    function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {	// @audit-issue

76:    function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant {	// @audit-issue

103:    function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {	// @audit-issue
```
[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L49-L49), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L76-L76), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L103-L103), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

24:    function openAccount(address facade, uint256 ref) public onlyManager {	// @audit-issue

41:    function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {	// @audit-issue

62:    function executeCommands(	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L24-L24), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L41-L41), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L62-L62), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

33:    function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {	// @audit-issue

52:    function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)	// @audit-issue

85:    function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

98:    function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L33-L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L52-L52), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L85-L85), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L98-L98), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

53:    function supply(DepositData memory data) public onlyManager nonReentrant {	// @audit-issue

79:    function withdraw(WithdrawData memory data) public onlyManager nonReentrant {	// @audit-issue

100:    function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {	// @audit-issue

106:    function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {	// @audit-issue

111:    function claim(address pool) public onlyManager nonReentrant {	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L53-L53), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L79-L79), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L100-L100), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L106-L106), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L111-L111), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

29:    function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

48:    function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

63:    function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L29-L29), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L48-L48), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L63-L63), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

38:    function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)	// @audit-issue

68:    function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {	// @audit-issue

87:    function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {	// @audit-issue
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L38-L38), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L68-L68), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L87-L87), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

43:    function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {	// @audit-issue

65:    function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)	// @audit-issue
```
[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L43-L43), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L65-L65), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

40:    function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {	// @audit-issue

63:    function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {	// @audit-issue

87:    function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {	// @audit-issue

101:    function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {	// @audit-issue
```
[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L40-L40), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L63-L63), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L87-L87), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L101-L101), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

53:    function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {	// @audit-issue

64:    function openPosition(	// @audit-issue

109:    function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {	// @audit-issue

115:    function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64-L64), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L109-L109), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L115-L115), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

25:    function createAccount() public onlyManager {	// @audit-issue

30:    function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {	// @audit-issue

46:    function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {	// @audit-issue

68:    function delegateIntoPreferredPool(	// @audit-issue

81:    function delegateIntoApprovedPool(	// @audit-issue

94:    function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)	// @audit-issue

102:    function mintOrBurnSUSD(	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L25-L25), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L30-L30), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L46-L46), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L68-L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L81-L81), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L94-L94), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

46:    function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

62:    function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)	// @audit-issue

81:    function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {	// @audit-issue

88:    function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager {	// @audit-issue

100:    function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L46-L46), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L62-L62), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L81-L81), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L88-L88), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L100-L100), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

37:    function deposit(uint256 amountIn) external onlyManager nonReentrant {	// @audit-issue

51:    function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {	// @audit-issue

69:    function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L37-L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L51-L51), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

33:    function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {	// @audit-issue

52:    function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)	// @audit-issue

75:    function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {	// @audit-issue

97:    function adjustTrove(	// @audit-issue

129:    function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L33-L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L52-L52), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L75-L75), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L97-L97), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L129-L129), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

78:    function supply(address market, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

97:    function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {	// @audit-issue

112:    function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {	// @audit-issue

126:    function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {	// @audit-issue

137:    function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {	// @audit-issue

149:    function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)	// @audit-issue

166:    function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)	// @audit-issue

183:    function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)	// @audit-issue

203:    function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {	// @audit-issue

216:    function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {	// @audit-issue

241:    function claimRewards(IPMarket market) external onlyManager nonReentrant {	// @audit-issue
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L78-L78), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L97-L97), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L112-L112), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L126-L126), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L137-L137), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L149-L149), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L166-L166), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L183-L183), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L203-L203), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L216-L216), [241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L241-L241), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

30:    function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {	// @audit-issue

43:    function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {	// @audit-issue

58:    function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)	// @audit-issue

77:    function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)	// @audit-issue

98:    function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L30-L30), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L43-L43), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L58-L58), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L77-L77), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L98-L98), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

68:    function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {	// @audit-issue

81:    function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {	// @audit-issue

103:    function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {	// @audit-issue

117:    function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)	// @audit-issue

160:    function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)	// @audit-issue

182:    function withdrawFromConvexBooster(uint256 pid, uint256 amount) public onlyManager {	// @audit-issue

192:    function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager {	// @audit-issue

202:    function withdrawFromGauge(address pool, uint256 amount) public onlyManager {	// @audit-issue

212:    function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager {	// @audit-issue

221:    function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {	// @audit-issue

233:    function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {	// @audit-issue

247:    function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {	// @audit-issue
```
[68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L68-L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L81-L81), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L103-L103), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L117-L117), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L160-L160), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L182-L182), [192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L192-L192), [202](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L202-L202), [212](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L212-L212), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L221-L221), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L233-L233), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L247-L247), 


#### Recommendation

Mark functions with access restrictions like 'onlyOwner' as 'payable' in Solidity. This reduces gas costs for legitimate callers by removing the compiler's checks for incoming payments, as the function will revert for unauthorized users anyway.

### `abi.encode()` is less efficient than `abi.encodePacked()`
When working with Solidity, it is important to pay attention to gas efficiency in order to optimize smart contracts. In this blog post, we will compare the gas costs of `abi.encode()` and `abi.encodepacked()` and explore why the latter is more efficient.Source: [reference](https://github.com/ConnorBlockchain/Solidity-Encode-Gas-Comparison)


```solidity
Path: ./contracts/accountingManager/Registry.sol

345:        bytes32 holdingPositionId = keccak256(abi.encode(msg.sender, _positionId, _data));	// @audit-issue

352:                    abi.encode(	// @audit-issue
353:                        vault.holdingPositions[positionIndex].calculatorConnector,
354:                        vault.holdingPositions[positionIndex].positionId,
355:                        vault.holdingPositions[positionIndex].data
356:                    )

399:        bytes32 holdingPositionId = keccak256(abi.encode(_connector, _positionId, data));	// @audit-issue

491:        return keccak256(abi.encode(calculatorConnector, positionTypeId, data));	// @audit-issue
```
[345](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L345-L345), [352](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L352-L356), [399](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L399-L399), [491](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L491-L491), 


```solidity
Path: ./contracts/governance/Keepers.sol

101:                keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));	// @audit-issue
```
[101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L101-L101), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

138:        bytes32 positionId = registry.calculatePositionId(accountingManager, 0, abi.encode(token));	// @audit-issue

141:            registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));	// @audit-issue

144:            registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);	// @audit-issue
```
[138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L138-L138), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L141-L141), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L144-L144), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

171:            ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId));	// @audit-issue
```
[171](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L171-L171), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

79:        bytes memory data = abi.encode(vaultId, tvl, updateTime);	// @audit-issue
```
[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L79-L79), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

37:            registry.calculatePositionId(address(this), OMNICHAIN_POSITION_ID, abi.encode(chainId)),	// @audit-issue

39:            abi.encode(tvl),	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L37-L37), [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L39-L39), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

69:        bytes32 txn = keccak256(abi.encode(bridgeRequest));	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

103:            vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false	// @audit-issue

126:            vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true	// @audit-issue
```
[103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L103-L103), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L126-L126), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

47:            vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false	// @audit-issue

68:                vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true	// @audit-issue
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L47-L47), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L68-L68), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

67:            registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));	// @audit-issue

91:                address(this), STARGATE_LP_POSITION_TYPE, abi.encode(withdrawRequest.poolId)	// @audit-issue
```
[67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L67-L67), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L91-L91), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

28:            registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),	// @audit-issue

29:            abi.encode(c),	// @audit-issue

46:            registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),	// @audit-issue

47:            abi.encode(creditAccount),	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L29-L29), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L46-L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L47-L47), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

39:            vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", false	// @audit-issue

62:                vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L39-L39), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L62-L62), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

54:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue

80:        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));	// @audit-issue
```
[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L54-L54), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L80-L80), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

34:            vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false	// @audit-issue

55:                vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true	// @audit-issue
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L34-L34), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L55-L55), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

44:            registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));	// @audit-issue

72:                registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L44-L44), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L72-L72), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

53:            registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),	// @audit-issue

80:                registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L53-L53), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L80-L80), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

42:            registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));	// @audit-issue

50:        bytes memory positionData = abi.encode(tokenId);	// @audit-issue

52:            vaultId, positionId, positionData, abi.encode(p.tickLower, p.tickUpper, p.fee), false	// @audit-issue

76:                registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(token0, token1));	// @audit-issue

77:            bytes memory positionData = abi.encode(p.tokenId);	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L42-L42), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L50-L50), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L52-L52), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L76-L76), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

88:                abi.encode(	// @audit-issue
89:                    IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                    amountsWithoutBPT, //_noBptAmounts,
91:                    minBPT // minimumBPT
92:                ),

96:        bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(poolId));	// @audit-issue

137:                    abi.encode(	// @audit-issue
138:                        IBalancerVault.ExitKind.EXACT_BPT_IN_FOR_ONE_TOKEN_OUT,
139:                        p._lpAmount,
140:                        p.withdrawIndex // enterTokenIndex
141:                    ),

149:                    registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(p.poolId)),	// @audit-issue

190:        bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(pooId));	// @audit-issue
```
[88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L88-L92), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L96-L96), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L137-L141), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L149-L149), [190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L190-L190), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

38:            abi.encode(_accountId, _token),	// @audit-issue

55:                abi.encode(_accountId, _token),	// @audit-issue
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L38-L38), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L55-L55), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

59:        registry.updateHoldingPosition(vaultId, positionId, abi.encode(requestIds[0]), abi.encode(amount), false);	// @audit-issue

81:            abi.encode(requestId),	// @audit-issue
```
[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L59-L59), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L81-L81), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

35:            bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));	// @audit-issue

57:        bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));	// @audit-issue

77:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));	// @audit-issue

106:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));	// @audit-issue

131:            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, troveManager));	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L35-L35), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L57-L57), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L77-L77), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L106-L106), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L131-L131), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

87:        bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));	// @audit-issue

226:                registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)),	// @audit-issue
```
[87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L87-L87), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L226-L226), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

39:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", false	// @audit-issue

53:                vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true	// @audit-issue

73:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true	// @audit-issue

102:            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L39-L39), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L53-L53), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L73-L73), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L102-L102), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

122:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue

167:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue

259:        bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));	// @audit-issue
```
[122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L122-L122), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L167-L167), [259](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L259-L259), 


#### Recommendation

Optimize gas usage by preferring 'abi.encodePacked()' over 'abi.encode()' where appropriate, as 'abi.encodePacked()' is generally more gas-efficient. However, ensure its suitability based on the data type and structure requirements, as 'abi.encodePacked()' can lead to ambiguity in certain cases.

### `x += y` costs more gas than `x = x + y` for stack variables
Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

236:            i += 1;	// @audit-issue

246:            middleTemp += 1;	// @audit-issue

271:            i += 1;	// @audit-issue

280:            processedBaseTokenAmount += data.amount;	// @audit-issue

282:            firstTemp += 1;	// @audit-issue

342:            i += 1;	// @audit-issue

347:            assetsNeededForWithdraw += assets;	// @audit-issue

348:            processedShares += data.shares;	// @audit-issue

351:            middleTemp += 1;	// @audit-issue

411:            i += 1;	// @audit-issue

421:            processedBaseTokenAmount += data.amount;	// @audit-issue

424:                withdrawFeeAmount += feeAmount;	// @audit-issue

434:            firstTemp += 1;	// @audit-issue

561:            amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;	// @audit-issue
```
[236](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L236-L236), [246](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L246-L246), [271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L271-L271), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L280-L280), [282](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L282-L282), [342](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L342-L342), [347](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L347-L347), [348](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L348-L348), [351](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L351-L351), [411](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L411-L411), [421](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L421-L421), [424](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L424-L424), [434](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L434-L434), [561](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L561-L561), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

118:            depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));	// @audit-issue

124:            totalDepositAmount += depositAmount * price / 1e18;	// @audit-issue

125:            totalBAmount += borrowAmount * price / 1e18;	// @audit-issue
```
[118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L118-L118), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L124-L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L125-L125), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

102:            CollValue += principalInBase;	// @audit-issue

119:                if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;	// @audit-issue

120:                else CollValue += collateralValueInVirtualBase;	// @audit-issue
```
[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L102-L102), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L119-L119), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L120-L120), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

144:            amount0 += tokensOwed0;	// @audit-issue

145:            amount1 += tokensOwed1;	// @audit-issue

148:        tvl += valueOracle.getValue(token0, base, amount0);	// @audit-issue

149:        tvl += valueOracle.getValue(token1, base, amount1);	// @audit-issue
```
[144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L144-L144), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L145-L145), [148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L148-L148), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L149-L149), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

271:                SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;	// @audit-issue

275:            if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;	// @audit-issue

278:            if (YTBalance > 0) SYAmount += getYTValue(market, YTBalance);	// @audit-issue

280:            if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;	// @audit-issue
```
[271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L271-L271), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L275-L275), [278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L278-L278), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L280-L280), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

116:                totalCollateral += value;	// @audit-issue

118:                totalDebt += value;	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L116-L116), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L118-L118), 


#### Recommendation

Prefer using 'x = x + y' over 'x += y' for state variable assignments in Solidity to save gas. The latter incurs extra costs due to additional JUMP instructions and stack operations associated with non-inlined function calls.

### Use `s.x = s.x + y` instead of `s.x += y` for memory structs
Using the `s.x = s.x + y` instead of `s.x += y` for memory structs can save **100 gas**. The same applies to `-=`, `*=`, etc.

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

217:        depositQueue.last += 1;	// @audit-issue

218:        depositQueue.totalAWFDeposit += amount;	// @audit-issue

284:        depositQueue.totalAWFDeposit -= processedBaseTokenAmount;	// @audit-issue

315:        withdrawQueue.last += 1;	// @audit-issue

353:        currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;	// @audit-issue
```
[217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L217-L217), [218](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L218-L218), [284](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L284-L284), [315](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L315-L315), [353](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L353-L353), 


#### Recommendation

Use explicit arithmetic assignment operations like `s.x = s.x + y` instead of compound assignments `s.x += y` for memory structs in Solidity. This approach saves around 100 gas per operation, making it preferable in scenarios involving frequent memory struct manipulations. Apply the same optimization for other arithmetic operations such as `-=` and `*=`, to enhance overall gas efficiency in your contracts.

### Use calldata instead of memory for function arguments that do not get mutated
Mark data types as `calldata` instead of `memory` where possible. This makes it so that the data is not automatically loaded into memory. If the data passed into the function does not need to be changed (like updating values in an array), it can be passed in as `calldata`. The one exception to this is if the argument must later be passed into another function that takes an argument that specifies `memory` storage.

```solidity
Path: ./contracts/accountingManager/Registry.sol

394:    function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)	// @audit-issue

486:    function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)	// @audit-issue
```
[394](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L394-L394), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L486-L486), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

94:    constructor(AccountingManagerConstructorParams memory p)	// @audit-issue

257:    function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)	// @audit-issue

596:    function getQueueItems(bool depositOrWithdraw, uint256[] memory items)	// @audit-issue

632:    function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {	// @audit-issue

649:    function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {	// @audit-issue
```
[94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L94-L94), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L257-L257), [596](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L596-L596), [632](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L632-L632), [649](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L649-L649), 


```solidity
Path: ./contracts/governance/Keepers.sol

27:    constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {	// @audit-issue

42:    function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {	// @audit-issue

84:    function execute(
85:        address destination,
86:        bytes calldata data,
87:        uint256 gasLimit,
88:        address executor,
89:        bytes32[] memory sigR,	// @audit-issue
90:        bytes32[] memory sigS,
91:        uint8[] memory sigV,
92:        uint256 deadline
93:    ) public {

84:    function execute(
85:        address destination,
86:        bytes calldata data,
87:        uint256 gasLimit,
88:        address executor,
89:        bytes32[] memory sigR,
90:        bytes32[] memory sigS,	// @audit-issue
91:        uint8[] memory sigV,
92:        uint256 deadline
93:    ) public {

84:    function execute(
85:        address destination,
86:        bytes calldata data,
87:        uint256 gasLimit,
88:        address executor,
89:        bytes32[] memory sigR,
90:        bytes32[] memory sigS,
91:        uint8[] memory sigV,	// @audit-issue
92:        uint256 deadline
93:    ) public {
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L27-L27), [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42-L42), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L84-L93), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L84-L93), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L84-L93), 


```solidity
Path: ./contracts/governance/Watchers.sol

7:    constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }	// @audit-issue

8:    function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L7-L7), [8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L8-L8), 


```solidity
Path: ./contracts/governance/TimeLock.sol

7:    constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L7-L7), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

33:    constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {	// @audit-issue

84:    function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)	// @audit-issue

122:    function transferPositionToAnotherConnector(
123:        address[] memory tokens,	// @audit-issue
124:        uint256[] memory amounts,
125:        bytes memory data,
126:        address connector
127:    ) external onlyManager nonReentrant {

122:    function transferPositionToAnotherConnector(
123:        address[] memory tokens,
124:        uint256[] memory amounts,	// @audit-issue
125:        bytes memory data,
126:        address connector
127:    ) external onlyManager nonReentrant {

122:    function transferPositionToAnotherConnector(
123:        address[] memory tokens,
124:        uint256[] memory amounts,
125:        bytes memory data,	// @audit-issue
126:        address connector
127:    ) external onlyManager nonReentrant {

169:    function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)	// @audit-issue

204:    function swapHoldings(
205:        address[] memory tokensIn,	// @audit-issue
206:        address[] memory tokensOut,
207:        uint256[] memory amountsIn,
208:        bytes[] memory swapData,
209:        uint256[] memory routeIds
210:    ) external onlyManager nonReentrant {

204:    function swapHoldings(
205:        address[] memory tokensIn,
206:        address[] memory tokensOut,	// @audit-issue
207:        uint256[] memory amountsIn,
208:        bytes[] memory swapData,
209:        uint256[] memory routeIds
210:    ) external onlyManager nonReentrant {

204:    function swapHoldings(
205:        address[] memory tokensIn,
206:        address[] memory tokensOut,
207:        uint256[] memory amountsIn,	// @audit-issue
208:        bytes[] memory swapData,
209:        uint256[] memory routeIds
210:    ) external onlyManager nonReentrant {

204:    function swapHoldings(
205:        address[] memory tokensIn,
206:        address[] memory tokensOut,
207:        uint256[] memory amountsIn,
208:        bytes[] memory swapData,	// @audit-issue
209:        uint256[] memory routeIds
210:    ) external onlyManager nonReentrant {

204:    function swapHoldings(
205:        address[] memory tokensIn,
206:        address[] memory tokensOut,
207:        uint256[] memory amountsIn,
208:        bytes[] memory swapData,
209:        uint256[] memory routeIds	// @audit-issue
210:    ) external onlyManager nonReentrant {

221:    function _executeSwap(SwapRequest memory swapRequest) internal returns (uint256 amountOut) {	// @audit-issue

232:    function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {	// @audit-issue

249:    function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {	// @audit-issue

263:    function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {	// @audit-issue

267:    function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {	// @audit-issue

271:    function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L33-L33), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L84-L84), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122-L127), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122-L127), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122-L127), [169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L169-L169), [205](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L210), [206](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L210), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L210), [208](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L210), [209](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204-L210), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L221-L221), [232](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L232-L232), [249](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L249-L249), [263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L263-L263), [267](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L267-L267), [271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271-L271), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

34:    constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)	// @audit-issue

90:    function executeSwap(SwapRequest memory _swapRequest)	// @audit-issue

147:    function addRoutes(RouteData[] memory _routes) public onlyMaintainer {	// @audit-issue
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L34), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L90), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147-L147), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

65:    function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {	// @audit-issue
```
[65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L65), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

81:    function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)	// @audit-issue
```
[81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L81), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

36:    function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

19:    constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

51:    function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L19), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51-L51), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

33:    constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

68:    function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33-L33), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

11:    constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

33:    function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L11-L11), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33-L33), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

43:    constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)	// @audit-issue

149:    function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {	// @audit-issue

153:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

161:    function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L43-L43), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L149-L149), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L153-L153), [161](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L161-L161), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

23:    constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {	// @audit-issue

108:    function getHealthFactor(Id _id, Market memory _market) public view returns (uint256) {	// @audit-issue

118:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

141:    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L23-L23), [108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L108-L108), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L118-L118), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L141-L141), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

19:    constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19-L19), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

33:    constructor(address lpStacking, address _stargateRouter, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

110:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

123:    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L33-L33), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L110-L110), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L123-L123), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

17:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue

93:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L17-L17), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L93-L93), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

17:    constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {	// @audit-issue

109:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

143:    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L17-L17), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L109-L109), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L143-L143), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

40:    constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

53:    function supply(DepositData memory data) public onlyManager nonReentrant {	// @audit-issue

79:    function withdraw(WithdrawData memory data) public onlyManager nonReentrant {	// @audit-issue

117:    function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {	// @audit-issue

125:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {	// @audit-issue
```
[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L40-L40), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L53-L53), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L79-L79), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L117-L117), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L125-L125), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

17:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue

125:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {	// @audit-issue

134:    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L17-L17), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L125-L125), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L134-L134), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

29:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue

142:    function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {	// @audit-issue

150:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L29-L29), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L142-L142), [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L150-L150), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

36:    constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {	// @audit-issue

88:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

99:    function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L36-L36), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L88-L88), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L99-L99), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

27:    constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

40:    function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {	// @audit-issue

63:    function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {	// @audit-issue

87:    function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {	// @audit-issue

101:    function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {	// @audit-issue

127:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

152:    function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L27-L27), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L40-L40), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L63-L63), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L87-L87), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L101-L101), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L127-L127), [152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L152-L152), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

42:    constructor(address _balancerVault, address bal, address aura, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

64:    function openPosition(
65:        bytes32 poolId,
66:        uint256[] memory amounts,	// @audit-issue
67:        uint256[] memory amountsWithoutBPT,
68:        uint256 minBPT,
69:        uint256 auraAmount
70:    ) public onlyManager nonReentrant {

64:    function openPosition(
65:        bytes32 poolId,
66:        uint256[] memory amounts,
67:        uint256[] memory amountsWithoutBPT,	// @audit-issue
68:        uint256 minBPT,
69:        uint256 auraAmount
70:    ) public onlyManager nonReentrant {

115:    function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {	// @audit-issue

162:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {	// @audit-issue

175:    function totalLpBalanceOf(PoolInfo memory pool) public view returns (uint256) {	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L42-L42), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64-L70), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64-L70), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L115-L115), [162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L162-L162), [175](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L175-L175), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

37:    function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)	// @audit-issue

54:    function receiveFlashLoan(
55:        IERC20[] memory tokens,	// @audit-issue
56:        uint256[] memory amounts,
57:        uint256[] memory feeAmounts,
58:        bytes memory userData
59:    ) external override {

54:    function receiveFlashLoan(
55:        IERC20[] memory tokens,
56:        uint256[] memory amounts,	// @audit-issue
57:        uint256[] memory feeAmounts,
58:        bytes memory userData
59:    ) external override {

54:    function receiveFlashLoan(
55:        IERC20[] memory tokens,
56:        uint256[] memory amounts,
57:        uint256[] memory feeAmounts,	// @audit-issue
58:        bytes memory userData
59:    ) external override {

54:    function receiveFlashLoan(
55:        IERC20[] memory tokens,
56:        uint256[] memory amounts,
57:        uint256[] memory feeAmounts,
58:        bytes memory userData	// @audit-issue
59:    ) external override {
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L37-L37), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54-L59), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54-L59), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54-L59), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54-L59), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

20:    constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {	// @audit-issue

64:    function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {	// @audit-issue

121:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

128:    function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L20-L20), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L64-L64), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L121-L121), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L128-L128), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

33:    constructor(address _pool, address _poolBaseToken, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

114:    function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {	// @audit-issue

120:    function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L33-L33), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114-L114), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L120-L120), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

20:    constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)	// @audit-issue

91:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L20-L20), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L91-L91), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

25:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue

145:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

164:    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L25-L25), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L145-L145), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L164-L164), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

57:    constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)	// @audit-issue

149:    function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)	// @audit-issue

166:    function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)	// @audit-issue

257:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

311:    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {	// @audit-issue
```
[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L57-L57), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L149-L149), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L166-L166), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L257-L257), [311](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L311-L311), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

18:    constructor(
19:        address _depositWithdrawalProxy,
20:        address _dolomiteMargin,
21:        address _borrowPositionProxy,
22:        BaseConnectorCP memory baseConnectorParams	// @audit-issue
23:    ) BaseConnector(baseConnectorParams) {

98:    function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {	// @audit-issue

106:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L18-L23), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L98-L98), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L106-L106), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

45:    constructor(
46:        address _convexBooster,
47:        address cvx,
48:        address crv,
49:        address prisma,
50:        BaseConnectorCP memory baseConnectorParams	// @audit-issue
51:    ) BaseConnector(baseConnectorParams) {

265:    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {	// @audit-issue

279:    function LPToUnder(PoolInfo memory info, uint256 balance) public view returns (uint256, address) {	// @audit-issue

311:    function totalLpBalanceOf(PoolInfo memory info) public view returns (uint256) {	// @audit-issue

325:    function balanceOfConvexRewardPool(PoolInfo memory info) public view returns (uint256) {	// @audit-issue

335:    function balanceOfLPToken(PoolInfo memory info) public view returns (uint256) {	// @audit-issue

344:    function balanceOfRewardPool(PoolInfo memory info) public view returns (uint256) {	// @audit-issue
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L45-L51), [265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L265-L265), [279](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L279-L279), [311](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L311-L311), [325](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L325-L325), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L335-L335), [344](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L344-L344), 


#### Recommendation

To optimize gas usage in your Solidity functions, mark data types as `calldata` instead of `memory` wherever applicable. This prevents unnecessary data loading into memory. Use `calldata` for function arguments that do not require changes within the function, except when passing them into another function that explicitly requires `memory` storage.

### Splitting `require()` statements that use `&&` saves gas
Instead of using the `&&` operator in a single require statement to check multiple conditions,using multiple require statements with 1 condition per require statement will save 3 GAS per `&&`:

```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

361:        require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);	// @audit-issue

371:        require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);	// @audit-issue
```
[361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L361-L361), [371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L371-L371), 


```solidity
Path: ./contracts/governance/Keepers.sol

28:        require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);	// @audit-issue

53:        require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);	// @audit-issue

64:        require(_threshold <= numOwners && _threshold > 1);	// @audit-issue

96:        require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");	// @audit-issue

106:                require(recovered > lastAdd && isOwner[recovered]);	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L28-L28), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L64-L64), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L96-L96), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L106-L106), 


#### Recommendation

Split 'require()' statements in Solidity that use '&&' into multiple 'require()' statements, each with a single condition. This approach saves 3 gas per '&&', optimizing overall gas usage in the contract.

### Nesting `if` statements that uses `&&` saves gas
In Solidity, the way conditional checks are structured can impact the gas consumption of a transaction. When conditions are combined using `&&` within an `if` statement, Solidity short-circuits the evaluation, meaning that if the first condition is `false`, the subsequent conditions won't be evaluated. This behavior can lead to gas savings compared to using separate nested `if` statements because not all conditions might need to be checked every time. By efficiently structuring these conditional checks, contracts can optimize the gas required for execution, leading to reduced costs for users.


```solidity
Path: ./contracts/accountingManager/Registry.sol

40:        if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

47:        if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

347:        if (positionIndex == 0 && removePosition) return type(uint256).max;	// @audit-issue
```
[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L40-L40), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L47-L47), [347](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L347-L347), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

186:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {	// @audit-issue

288:        if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {	// @audit-issue

335:        if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {	// @audit-issue

374:        if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {	// @audit-issue
```
[186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186-L186), [288](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L288-L288), [335](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L335-L335), [374](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L374-L374), 


```solidity
Path: ./contracts/governance/Keepers.sol

45:            if (addOrRemove[i] && !isOwner[_owners[i]]) {	// @audit-issue

48:            } else if (!addOrRemove[i] && isOwner[_owners[i]]) {	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L45-L45), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L48-L48), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

55:        if (msg.sender != emergencyManager && msg.sender != watcherContract) {	// @audit-issue

67:        if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);	// @audit-issue
```
[55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L55-L55), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L67-L67), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

142:        if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {	// @audit-issue
```
[142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L142-L142), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30:        if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();	// @audit-issue

102:        if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30-L30), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L102-L102), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

82:        if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {	// @audit-issue
```
[82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L82-L82), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

66:        if (p.collateral == 0 && p.supplyShares == 0) {	// @audit-issue
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L66-L66), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

60:        if (closePosition && isSiloEmpty(silo)) {	// @audit-issue

120:            if (depositAmount == 0 && borrowAmount == 0) {	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L60-L60), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L120-L120), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

111:        if (bAmount > 0 && !isBorrowing) {	// @audit-issue
```
[111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L111-L111), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

223:        if (closePosition && isMarketEmpty(market)) {	// @audit-issue
```
[223](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L223-L223), 


#### Recommendation


When multiple conditions need to be checked successively, try to combine them in a single `if` statement using `&&` instead of nesting separate `if` statements. This will leverage short-circuit evaluation for potential gas savings.


### Use `!= 0` Instead of `> 0` for Unsigned Integer Comparison
In Solidity, unsigned integers (e.g., `uint256`, `uint8`, etc.) represent non-negative whole numbers, ranging from 0 to a maximum value determined by their bit size. When performing comparisons on these numbers, especially to check if they are non-zero, developers have options. A common practice is to compare against zero using the `>` operator, as in `value > 0`. However, given the nature of unsigned integers, a more straightforward and slightly gas-efficient comparison is to use the `!=` operator, as in `value != 0`.

The primary rationale is that the `!=` comparison directly checks for non-equality, whereas the `>` comparison checks if one value is strictly greater than another. For unsigned integers, where negative values don't exist, the `!= 0` check is both semantically clearer and potentially more efficient at the EVM bytecode level.


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

288:        if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {	// @audit-issue

438:        if (withdrawFeeAmount > 0) {	// @audit-issue
```
[288](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L288-L288), [438](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L438-L438), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

142:        if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {	// @audit-issue
```
[142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L142-L142), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

52:        if (depositRequest.routerAmount > 0) {	// @audit-issue

79:        if (withdrawRequest.LPStakingAmount > 0) {	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L52-L52), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L79-L79), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

134:                IERC20(assetsS[i].collateralToken).balanceOf(address(this))	// @audit-issue
```
[134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L134-L134), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

100:        if (userBasic.principal > 0) {	// @audit-issue
```
[100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L100-L100), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

46:        if (collateralAmount > 0) {	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L46-L46), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

78:            if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);	// @audit-issue

116:        if (p._auraAmount > 0) {	// @audit-issue
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L78-L78), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L116-L116), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

111:        if (bAmount > 0 && !isBorrowing) {	// @audit-issue
```
[111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L111-L111), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

270:            if (lpBalance > 0) {	// @audit-issue
```
[270](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L270-L270), 


#### Recommendation

Use '!= 0' instead of '> 0' for comparing unsigned integers in Solidity. This is semantically clearer and slightly more gas-efficient, as it directly checks for non-zero values without considering unnecessary relational comparisons.

### Operator `>=`/`<=` costs less gas than operator `>`/`<`
The compiler uses opcodes `GT` and `ISZERO` for code that uses `>`, but only requires `LT` for `>=`. A similar behaviour applies for `>`, which uses opcodes `LT` and `ISZERO`, but only requires `GT` for `<=`.


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

506:        if (block.timestamp - lastFeeDistributionTime < 1 days) {	// @audit-issue

510:        if (timePassed > 10 days) {	// @audit-issue

528:            preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours	// @audit-issue

529:                || block.timestamp - profitStoredTime > 48 hours	// @audit-issue
```
[506](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L506-L506), [510](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L510-L510), [528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528-L528), [529](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L529-L529), 


```solidity
Path: ./contracts/governance/Keepers.sol

28:        require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);	// @audit-issue

53:        require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);	// @audit-issue

64:        require(_threshold <= numOwners && _threshold > 1);	// @audit-issue
```
[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L28-L28), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L64-L64), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

126:        address poolAddress = (poolInfo.tokens.length > 2 && poolInfo.zap != address(0)) ? poolInfo.zap : pool;	// @audit-issue
```
[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L126-L126), 


#### Recommendation

Opt for '>=', '<=' operators over '>' and '<' in Solidity where logically appropriate, as they consume less gas. This is because '>=' and '<=' require only one opcode ('LT' or 'GT'), compared to the two opcodes ('GT'/'LT' and 'ISZERO') needed for '>' and '<'.

### Constructor Can Be Marked As Payable
`payable` functions cost less gas to execute, since the compiler does not have to add extra checks to ensure that a payment wasn't provided.

A `constructor` can safely be marked as `payable`, since only the deployer would be able to pass funds, and the project itself would not pass any funds.



```solidity
Path: ./contracts/accountingManager/Registry.sol

66:    constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {	// @audit-issue
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L66-L66), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

14:    constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L14-L14), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

94:    constructor(AccountingManagerConstructorParams memory p)	// @audit-issue
```
[94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L94-L94), 


```solidity
Path: ./contracts/governance/Keepers.sol

27:    constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L27-L27), 


```solidity
Path: ./contracts/governance/Watchers.sol

7:    constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L7-L7), 


```solidity
Path: ./contracts/governance/TimeLock.sol

7:    constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L7-L7), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

21:    constructor(PositionRegistry _registry, uint256 _vaultId) {	// @audit-issue
```
[21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L21-L21), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

33:    constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L33-L33), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

34:    constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)	// @audit-issue
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L34), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

27:    constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L27), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

29:    constructor(PositionRegistry _registry) {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L29-L29), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

31:    constructor(address _factory, PositionRegistry _registry) {	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L31), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

46:    constructor(address _reg) {	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L46-L46), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

31:    constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31-L31), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

29:    constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L29-L29), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

19:    constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L19), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

33:    constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33-L33), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

11:    constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L11-L11), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

43:    constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)	// @audit-issue
```
[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L43-L43), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

23:    constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L23-L23), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

19:    constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19-L19), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

33:    constructor(address lpStacking, address _stargateRouter, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L33-L33), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

17:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L17-L17), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

17:    constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L17-L17), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

40:    constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L40-L40), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

17:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L17-L17), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

29:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L29-L29), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

36:    constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L36-L36), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

27:    constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L27-L27), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

42:    constructor(address _balancerVault, address bal, address aura, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L42-L42), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

24:    constructor(address _balancerVault, PositionRegistry _registry) {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

20:    constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L20-L20), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

33:    constructor(address _pool, address _poolBaseToken, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L33-L33), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

20:    constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L20-L20), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

25:    constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L25-L25), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

57:    constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)	// @audit-issue
```
[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L57-L57), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

18:    constructor(	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

45:    constructor(	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L45-L45), 


#### Recommendation

Mark constructors as 'payable' in Solidity contracts to reduce gas costs, as this eliminates the need for the compiler to add checks against incoming payments. This is safe because only the deployer can send funds during contract creation, and typically no funds are sent at this stage.

### Use `selfbalance()` instead of `address(this).balance`
In Solidity, contracts often need to query their own Ether balance. While `address(this).balance` has been a widely used approach to retrieve the current contract's balance, it is not the most gas-efficient method, especially with the introduction of the `SELFBALANCE` opcode in more recent EVM versions.

The `SELFBALANCE` opcode provides a more gas-efficient way to obtain the balance of the current contract. In Solidity, this can be invoked using the `selfbalance()` function. Compared to the `BALANCE` opcode used by `address(this).balance`, `SELFBALANCE` offers significant gas savings:

- `BALANCE`: The static gas cost is 0. If the accessed address is warm, the dynamic gas cost is 100. If the address is cold, the dynamic cost is 2,600.
  
- `SELFBALANCE`: Semantically equivalent to the `BALANCE` opcode when called on the contract's own address, but with a dramatically reduced minimum gas cost of 5.

Switching to `selfbalance()` can lead to significant gas savings, especially in operations or functions that frequently check the contract's balance.


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

80:        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here	// @audit-issue
```
[80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L80-L80), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

73:        uint256 beforeClaimBalance = address(this).balance;	// @audit-issue

77:        IWETH(weth).deposit{ value: address(this).balance - beforeClaimBalance }();	// @audit-issue
```
[73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L73-L73), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L77-L77), 


#### Recommendation

To optimize gas usage when querying a contract's own Ether balance in Solidity, it's recommended to use the `selfbalance()` function, which utilizes the more gas-efficient `SELFBALANCE` opcode. This can result in significant gas savings compared to `address(this).balance`.

### Optimize names to save gas
`public`/`external` function names and `public` member variable names can be optimized to save gas. Below are the interfaces/abstract contracts that can be optimized so that the most frequently-called functions use the least amount of gas possible during method lookup. Method IDs that have two leading zero bytes can save 128 gas each during deployment, and renaming functions to have lower method IDs will save 22 gas per call, [per sorted position shifted](https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92).


```solidity
Path: ./contracts/accountingManager/Registry.sol

12:contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L12-L12), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

7:contract NoyaFeeReceiver is Ownable {	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7-L7), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

16:contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {	// @audit-issue
```
[16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L16-L16), 


```solidity
Path: ./contracts/governance/Keepers.sol

9:contract Keepers is EIP712, Ownable2Step {	// @audit-issue
```
[9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L9-L9), 


```solidity
Path: ./contracts/governance/Watchers.sol

6:contract Watchers is Keepers {	// @audit-issue
```
[6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L6-L6), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

6:contract NoyaGovernanceBase {	// @audit-issue
```
[6](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L6-L6), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

7:library TVLHelper {	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L7-L7), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

22:contract BaseConnector is NoyaGovernanceBase, IConnector, ReentrancyGuard {	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L22-L22), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

10:contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10-L10), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

10:contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10-L10), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

10:contract NoyaValueOracle is INoyaValueOracle {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L10-L10), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

4:contract WETH_Oracle {	// @audit-issue
```
[4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L4-L4), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

12:contract UniswapValueOracle is INoyaValueOracle {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L12-L12), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

10:contract ChainlinkOracleConnector is INoyaValueOracle {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L10-L10), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

18:contract LZHelperReceiver is OAppReceiver {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L18-L18), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

19:contract LZHelperSender is OAppSender {	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19-L19), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

8:contract OmnichainManagerBaseChain is OmnichainLogic {	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L8-L8), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

14:abstract contract OmnichainLogic is BaseConnector {	// @audit-issue
```
[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L14-L14), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

10:contract OmnichainManagerNormalChain is OmnichainLogic {	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

29:contract MaverickConnector is BaseConnector, IERC721Receiver {	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29-L29), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

8:contract MorphoBlueConnector is BaseConnector {	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L8-L8), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

8:contract PancakeswapConnector is UNIv3Connector {	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L8-L8), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

19:contract StargateConnector is BaseConnector {	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L19-L19), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

8:contract Gearboxv3 is BaseConnector {	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L8-L8), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

8:contract SiloConnector is BaseConnector {	// @audit-issue
```
[8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L8-L8), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

27:contract AerodromeConnector is BaseConnector {	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L27-L27), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

7:contract CompoundConnector is BaseConnector {	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L7-L7), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

18:contract FraxConnector is BaseConnector {	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

30:contract CamelotConnector is BaseConnector {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L30-L30), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

12:contract UNIv3Connector is BaseConnector, ERC721Holder {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L12-L12), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

26:contract BalancerConnector is BaseConnector {	// @audit-issue
```
[26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L26-L26), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

12:contract BalancerFlashLoan is IFlashLoanRecipient, ReentrancyGuard {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L12-L12), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

7:contract SNXV3Connector is BaseConnector, IERC721Receiver {	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L7-L7), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

11:contract AaveConnector is BaseConnector {	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L11-L11), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

7:contract LidoConnector is BaseConnector, ERC721Holder {	// @audit-issue
```
[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7-L7), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

11:contract PrismaConnector is BaseConnector {	// @audit-issue
```
[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L11-L11), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

12:contract PendleConnector is BaseConnector {	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L12-L12), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

9:contract DolomiteConnector is BaseConnector {	// @audit-issue
```
[9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L9-L9), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

24:contract CurveConnector is BaseConnector {	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L24-L24), 


#### Recommendation

Optimize gas usage by renaming 'public'/'external' functions and 'public' member variables in Solidity. Aim for shorter and more efficient names, especially for frequently called functions. This can save gas during deployment and reduce gas costs per call due to lower method ID sorting positions.

### Use `uint256(1)`/`uint256(2)` instead of `true`/`false` to save gas for changes
Avoids a Gsset (**20000 gas**) when changing from `false` to `true`, after having been `true` in the past. Since most of the bools aren't changed twice in one transaction, I've counted the amount of gas as half of the full amount, for each variable. Note that public state variables can be re-written to be `private` and use `uint256`, but have public getters returning `bool`s.

```solidity
Path: ./contracts/governance/Keepers.sol

10:    mapping(address => bool) public isOwner;	// @audit-issue

19:    event UpdateOwners(address[] owners, bool[] addOrRemove);	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L10-L10), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L19-L19), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

13:    mapping(address => bool) public isEligibleToUse;	// @audit-issue
```
[13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L13-L13), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

13:    mapping(address => bool) public isHandler;	// @audit-issue

14:    mapping(string => bool) public isBridgeWhiteListed;	// @audit-issue

15:    mapping(uint256 => bool) public isChainSupported;	// @audit-issue

20:    event AddedHandler(address _handler, bool state);	// @audit-issue

21:    event AddedChain(uint256 _chainId, bool state);	// @audit-issue

22:    event AddedBridgeBlacklist(string bridgeName, bool state);	// @audit-issue
```
[13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L13-L13), [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L14-L14), [15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L15-L15), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L20-L20), [21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L21-L21), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

10:    bool ethPoolIncluded;	// @audit-issue

37:    event Stake(uint256 amount, uint256 duration, bool doDelegation);	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L10-L10), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

17:    event Supply(uint256 amount, Id id, bool sOrC);	// @audit-issue

18:    event Withdraw(uint256 amount, Id id, bool sOrC);	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L17-L17), [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

12:    event Deposit(address siloToken, address dToken, uint256 amount, bool oC);	// @audit-issue

13:    event Withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition);	// @audit-issue
```
[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L12-L12), [13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L13-L13), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

10:    bool isActive;	// @audit-issue
```
[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L10-L10), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

18:    event AdjustTrove(address zap, address tm, uint256 mFee, uint256 wAmount, uint256 bAmount, bool isBorrowing);	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

44:    event DecreasePosition(address market, uint256 amount, bool closePosition);	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L44-L44), 


#### Recommendation

To minimize gas overhead in your Solidity contracts, consider using `uint256(1)` and `uint256(2)` to represent `true` and `false`, respectively, instead of `bool` types for storage. This approach avoids additional `SLOAD` and `SSTORE` operations, resulting in more gas-efficient code.

### Consider activating `via-ir` for deploying
The IR-based code generator was developed to make code generation more performant by enabling optimization passes that can be applied across functions.

It is possible to activate the IR-based code generator through the command line by using the flag `--via-ir`or by including the option `{"viaIR": true}`.

Keep in mind that compiling with this option may take longer. However, you can simply test it before deploying your code. If you find that it provides better performance, you can add the `--via-ir` flag to your deploy command.
```solidity
/// @audit Global finding.
```
[1](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L1), 


#### Recommendation

Consider activating `via-ir`.

### Optimize Deployment Size by Fine-tuning IPFS Hash
The Solidity compiler appends 53 bytes of metadata to the smart contract code, incurring an extra cost of 10,600 gas. This additional expense arises from 200 gas per bytecode, plus calldata cost, which amounts to 16 gas for non-zero bytes and 4 gas for zero bytes. This results in a maximum of 848 extra gas in calldata cost.

Reducing this cost is crucial for the following reasons:

The metadata's 53-byte addition leads to a deployment cost increase of 10,600 gas. It can also result in an additional calldata cost of up to 848 gas. Ways to Minimize Gas Consumption:

Employ the `--no-cbor-metadata` compiler option to exclude metadata. Be cautious as this might impact contract verification. Search for code comments that yield an IPFS hash with more zeros, thereby reducing calldata costs.

```solidity
/// @audit Global finding.
```
[1](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L1), 


#### Recommendation

To optimize deployment size and reduce associated costs, consider the following strategies:
1. **Exclude Metadata with Compiler Option**: Use the `solc` compiler’s `--metadata-hash none` or `--no-cbor-metadata` option to prevent the inclusion of metadata in the compiled bytecode. This action reduces the bytecode size, thus lowering deployment gas costs. However, exercise caution with this approach, as it might affect the ability to verify the contract on platforms like Etherscan.

2. **Optimize IPFS Hash for More Zeros**: If excluding metadata is not desirable, another approach involves optimizing code comments or elements that influence the metadata hash generation to achieve an IPFS hash with a higher proportion of zeros. Since calldata costs are lower for zero bytes, a metadata hash with more zeros can reduce the calldata costs associated with contract interactions.

Example for excluding metadata:
```bash
solc --metadata-hash none YourContract.sol
```


### Low level `call` can be optimized with assembly
`returnData` is copied to memory even if the variable is not utilized: the proper way to handle this is through a low level assembly call.
```solidity
// before
(bool success,) = payable(receiver).call{gas: gas, value: value}("");

//after
bool success;
assembly {
    success := call(gas, receiver, value, 0, 0, 0, 0)
}
```


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

685:            (bool success,) = payable(msg.sender).call{ value: amount }("");	// @audit-issue
```
[685](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L685-L685), 


```solidity
Path: ./contracts/governance/Keepers.sol

116:        (bool success,) = destination.call{ gas: gasLimit }(data);	// @audit-issue
```
[116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L116-L116), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

176:        (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);	// @audit-issue

195:            (bool success,) = payable(userAddress).call{ value: amount }("");	// @audit-issue
```
[176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176), [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

81:                (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);	// @audit-issue
```
[81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L81-L81), 


#### Recommendation

Optimize low-level 'call' operations in Solidity using assembly, especially when 'returnData' is not needed. This avoids unnecessary copying to memory and can lead to gas savings. For example, replace '(bool success,) = payable(receiver).call{gas: gas, value: value}("");' with an assembly block: 'assembly { success := call(gas, receiver, value, 0, 0, 0, 0) }'. This ensures a more efficient execution.

### Assembly: Use scratch space for building calldata
If an external call's calldata can fit into two or fewer words, use the scratch space to build the calldata, rather than allowing Solidity to do a memory expansion.

```solidity
Path: ./contracts/accountingManager/Registry.sol

141:        vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));	// @audit-issue

252:            address[] memory usingTokens = IConnector(calculatorConnector).getUnderlyingTokens(_positionTypeId, _data);	// @audit-issue

312:            vault.holdingPositions.push(	// @audit-issue

359:            vault.holdingPositions.pop();	// @audit-issue
```
[141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L141-L141), [252](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L252-L252), [312](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L312-L312), [359](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L359-L359), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

24:        AccountingManager(accountingManager).withdraw(amount, receiver);	// @audit-issue

28:        AccountingManager(accountingManager).burnShares(amount);	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L24-L24), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L28-L28), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

155:        if (registry.isAnActiveConnector(vaultId, msg.sender)) {	// @audit-issue

156:            IERC20(token).safeTransfer(address(msg.sender), amount);	// @audit-issue

230:        uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);	// @audit-issue

288:        if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {	// @audit-issue

333:        uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);	// @audit-issue

379:        uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;	// @audit-issue

428:            baseToken.safeTransfer(data.receiver, baseTokenAmount);	// @audit-issue

439:            baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);	// @audit-issue

552:            if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {	// @audit-issue

555:            uint256 balanceBefore = baseToken.balanceOf(address(this));	// @audit-issue

559:            uint256 balanceAfter = baseToken.balanceOf(address(this));	// @audit-issue

617:        uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;	// @audit-issue

628:        return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this))	// @audit-issue

633:        PositionBP memory p = registry.getPositionBP(vaultId, position.positionId);	// @audit-issue

636:            uint256 amount = IERC20(token).balanceOf(abi.decode(position.data, (address)));	// @audit-issue

688:            IERC20(token).safeTransfer(msg.sender, amount);	// @audit-issue
```
[155](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L155-L155), [156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L156-L156), [230](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L230-L230), [288](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L288-L288), [333](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L333-L333), [379](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L379-L379), [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L428-L428), [439](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L439-L439), [552](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L552-L552), [555](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L555-L555), [559](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L559-L559), [617](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L617-L617), [628](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L628-L628), [633](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L633-L633), [636](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L636-L636), [688](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L688-L688), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

32:        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

33:        if (!(msg.sender == keeperContract || msg.sender == emergencyManager || msg.sender == registry.flashLoan())) {	// @audit-issue

44:        (,,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

54:        (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

66:        (, address maintainer,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

76:        (, address maintainer,,,,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

86:        (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L32-L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L33-L33), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L44-L44), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L54-L54), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L66-L66), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L76-L76), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L86-L86), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

17:        HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);	// @audit-issue

22:            uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);	// @audit-issue

23:            bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);	// @audit-issue

43:        HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);	// @audit-issue
```
[17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L17-L17), [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L22-L22), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L23-L23), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L43-L43), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

89:        (address accountingManager,) = registry.getVaultAddresses(vaultId);	// @audit-issue

91:            (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

96:            IERC20(token).safeTransfer(address(accountingManager), newAmount);	// @audit-issue

98:        } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {	// @audit-issue

99:            IERC20(token).safeTransfer(address(msg.sender), amount);	// @audit-issue

102:            swapHandler.verifyRoute(routeId, msg.sender);	// @audit-issue

104:            IERC20(token).safeTransfer(msg.sender, amount);	// @audit-issue

129:        if (registry.isAnActiveConnector(vaultId, connector)) {	// @audit-issue

136:        (address accountingManager,) = registry.getVaultAddresses(vaultId);	// @audit-issue

159:        _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0);	// @audit-issue

174:        if (!registry.isAddressTrusted(vaultId, msg.sender)) {	// @audit-issue

180:            uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue

182:            uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));	// @audit-issue

222:        amountOut = swapHandler.executeSwap(swapRequest);	// @audit-issue

278:        uint256 currentAllowance = IERC20(_token).allowance(address(this), _spender);	// @audit-issue

282:        IERC20(_token).forceApprove(_spender, _amount);	// @audit-issue

286:        IERC20(_token).forceApprove(_spender, 0);	// @audit-issue
```
[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L89-L89), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L91-L91), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L96-L96), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L98-L98), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L99-L99), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L102-L102), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L104-L104), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L129-L129), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L136-L136), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L159-L159), [174](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L174-L174), [180](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L180-L180), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L182-L182), [222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L222-L222), [278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L278-L278), [282](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L282-L282), [286](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L286-L286), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

115:        _amountOut = ISwapAndBridgeImplementation(swapImplInfo.route).performSwapAction(msg.sender, _swapRequest);	// @audit-issue

137:        ISwapAndBridgeImplementation(bridgeImplInfo.route).performBridgeAction(msg.sender, _bridgeRequest);	// @audit-issue

149:            routes.push(_routes[i]);	// @audit-issue
```
[115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L115-L115), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L137-L137), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L149-L149), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

89:            balanceOut0 = IERC20(_request.outputToken).balanceOf(_request.from);	// @audit-issue

96:            balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);	// @audit-issue

116:            ILiFi(lifi).extractGenericSwapParameters(_request.data);	// @audit-issue

151:        ILiFi.BridgeData memory bridgeData = ILiFi(lifi).extractBridgeData(_request.data);	// @audit-issue

186:        token.forceApprove(spender, amount);	// @audit-issue

198:            IERC20(token).safeTransfer(userAddress, amount);	// @audit-issue
```
[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L89-L89), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L96-L96), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L116-L116), [151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L151-L151), [186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L186-L186), [198](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L198-L198), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

25:        if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L25-L25), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

25:        if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);	// @audit-issue

74:        (int56[] memory tickCumulatives,) = IUniswapV3Pool(pool).observe(secondsAgos);	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L25-L25), [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L74-L74), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

42:        if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);	// @audit-issue

123:        (, price,, updatedAt,) = source.latestRoundData();	// @audit-issue

139:        uint256 decimals = IERC20Metadata(token).decimals();	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L42-L42), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L123-L123), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L139-L139), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

52:        uint256 positionTypeId = registry.getPositionBP(vaultId, position.positionId).positionTypeId;	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L52-L52), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

82:        swapHandler.executeBridge(bridgeRequest);	// @audit-issue
```
[82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L82-L82), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

20:        (, address baseToken) = registry.getVaultAddresses(vaultId);	// @audit-issue

34:        PositionBP memory bp = registry.getPositionBP(vaultId, position.positionId);	// @audit-issue

37:            uint256 amount = IERC20(token).balanceOf(address(this));	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L20-L20), [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L34-L34), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

80:        IveMAV(veMav).unstake(lockupId);	// @audit-issue

93:        _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); // TODO: check token A is eth	// @audit-issue

94:        _approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);	// @audit-issue

105:        _updateTokenInRegistry(p.pool.tokenA());	// @audit-issue

106:        _updateTokenInRegistry(p.pool.tokenB());	// @audit-issue

120:        IMaverickPosition position = IMaverickRouter(maverickRouter).position();	// @audit-issue

121:        position.approve(maverickRouter, p.tokenId);	// @audit-issue

128:        _updateTokenInRegistry(p.pool.tokenA());	// @audit-issue

129:        _updateTokenInRegistry(p.pool.tokenB());	// @audit-issue

138:        IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));	// @audit-issue

142:                tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken));	// @audit-issue

143:                rewardContract.getReward(address(this), tokenIndex);	// @audit-issue

154:        PositionBP memory position = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

157:        (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool);	// @audit-issue

158:        return _getValue(pool.tokenA(), base, a) + _getValue(pool.tokenB(), base, b);	// @audit-issue

164:        tokens[0] = IMaverickPool(pool).tokenA();	// @audit-issue

165:        tokens[1] = IMaverickPool(pool).tokenB();	// @audit-issue
```
[80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L80-L80), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L93-L93), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L94-L94), [105](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L105-L105), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L106-L106), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L120-L120), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L121-L121), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L128-L128), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L129-L129), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L138-L138), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L142-L142), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L143-L143), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L154-L154), [157](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L157-L157), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L158-L158), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L164-L164), [165](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L165-L165), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

36:        MarketParams memory params = morphoBlue.idToMarketParams(id);	// @audit-issue

59:        MarketParams memory params = morphoBlue.idToMarketParams(id);	// @audit-issue

65:        Position memory p = morphoBlue.position(id, address(this));	// @audit-issue

81:        MarketParams memory market = morphoBlue.idToMarketParams(id);	// @audit-issue

83:        if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {	// @audit-issue

84:            revert IConnector_LowHealthFactor(getHealthFactor(id, morphoBlue.market(id)));	// @audit-issue

96:        MarketParams memory params = morphoBlue.idToMarketParams(id);	// @audit-issue

109:        MarketParams memory market = morphoBlue.idToMarketParams(_id);	// @audit-issue

110:        Position memory p = morphoBlue.position(_id, address(this));	// @audit-issue

111:        uint256 borrowAmount = uint256(p.borrowShares).toAssetsUp(_market.totalBorrowAssets, _market.totalBorrowShares);	// @audit-issue

119:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

122:            MarketParams memory params = morphoBlue.idToMarketParams(id);	// @audit-issue

123:            Market memory market = morphoBlue.market(id);	// @audit-issue

124:            Position memory pos = morphoBlue.position(id, address(this));	// @audit-issue

126:                uint256(pos.borrowShares).toAssetsUp(market.totalBorrowAssets, market.totalBorrowShares);	// @audit-issue

128:                uint256(pos.supplyShares).toAssetsUp(market.totalSupplyAssets, market.totalSupplyShares);	// @audit-issue

138:        return amount * IOracle(marketOracle).price() / ORACLE_PRICE_SCALE;	// @audit-issue

143:        MarketParams memory params = morphoBlue.idToMarketParams(id);	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L36-L36), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L59-L59), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L65-L65), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L81-L81), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L83-L83), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L84-L84), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L96-L96), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L109-L109), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L110-L110), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L111-L111), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L119-L119), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L122-L122), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L123-L123), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L124-L124), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L126-L126), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L128-L128), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L138-L138), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L143-L143), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

41:        masterchef.updateLiquidity(tokenId);	// @audit-issue

42:        _updateTokenInRegistry(masterchef.CAKE());	// @audit-issue

51:        masterchef.withdraw(tokenId, address(this));	// @audit-issue

52:        _updateTokenInRegistry(masterchef.CAKE());	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L41-L41), [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L42-L42), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L51-L51), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L52-L52), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

41:        rewardToken = LPStaking.stargate();	// @audit-issue

50:        address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;	// @audit-issue

51:        address underlyingToken = IStargatePool(lpAddress).token();	// @audit-issue

60:                stakingAmount = IERC20(lpAddress).balanceOf(address(this));	// @audit-issue

63:            LPStaking.deposit(depositRequest.poolId, stakingAmount);	// @audit-issue

77:        address lpAddress = LPStaking.poolInfo(withdrawRequest.poolId).lpToken;	// @audit-issue

78:        address underlyingToken = IStargatePool(lpAddress).token();	// @audit-issue

80:            IStargateLPStaking(LPStaking).withdraw(withdrawRequest.poolId, withdrawRequest.LPStakingAmount);	// @audit-issue

88:        uint256 LPAmount = LPStaking.userInfo(withdrawRequest.poolId, address(this)).amount;	// @audit-issue

89:        if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) {	// @audit-issue

104:        LPStaking.deposit(poolId, 0);	// @audit-issue

111:        PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

113:        address lpAddress = LPStaking.poolInfo(poolId).lpToken;	// @audit-issue

114:        uint256 lpAmount = LPStaking.userInfo(poolId, address(this)).amount + IERC20(lpAddress).balanceOf(address(this));	// @audit-issue

118:        address underlyingToken = IStargatePool(lpAddress).token();	// @audit-issue

119:        uint256 underlyingAmount = IStargatePool(lpAddress).amountLPtoLD(lpAmount);	// @audit-issue

125:        address lpAddress = LPStaking.poolInfo(poolId).lpToken;	// @audit-issue

127:        tokens[0] = IStargatePool(lpAddress).token();	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L41-L41), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L50-L50), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L51-L51), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L60-L60), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L63-L63), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L77-L77), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L78-L78), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L80-L80), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L88-L88), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L89-L89), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L104-L104), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L111-L111), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L113-L113), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L114-L114), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L118-L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L119-L119), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L125-L125), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L127-L127), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

42:        ICreditFacadeV3(facade).closeCreditAccount(creditAccount, new MultiCall[](0));	// @audit-issue

79:            _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount);	// @audit-issue

81:        ICreditFacadeV3(facade).multicall(creditAccount, calls);	// @audit-issue

83:            _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());	// @audit-issue

95:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

97:        CollateralDebtData memory d = ICreditManagerV3(facade.creditManager()).calcDebtAndCollateral(	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L42-L42), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L79-L79), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L81-L81), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L83-L83), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L95-L95), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L97-L97), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

34:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue

57:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue

76:        return SolvencyV2.getData(ISilo(siloRepository.getSilo(siloToken)), address(this), minimumHealthFactor);	// @audit-issue

86:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue

87:        silo.borrow(bToken, amount);	// @audit-issue

99:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue

101:        silo.repay(rToken, amount);	// @audit-issue

110:        PositionBP memory bp = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

112:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue

113:        (address[] memory assets, IBaseSilo.AssetStorage[] memory assetsS) = silo.getAssetsWithState();	// @audit-issue

117:            uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));	// @audit-issue

118:            depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));	// @audit-issue

119:            uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));	// @audit-issue

131:        (, IBaseSilo.AssetStorage[] memory assetsS) = silo.getAssetsWithState();	// @audit-issue

134:                IERC20(assetsS[i].collateralToken).balanceOf(address(this))	// @audit-issue

135:                    + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0	// @audit-issue

145:        ISilo silo = ISilo(siloRepository.getSilo(siloToken));	// @audit-issue

146:        (address[] memory assets,) = silo.getAssetsWithState();	// @audit-issue
```
[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L34-L34), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L57-L57), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L76-L76), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L86-L86), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L87-L87), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L99-L99), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L101-L101), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L110-L110), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L112-L112), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L113-L113), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L117-L117), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L118-L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L119-L119), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L131-L131), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L134-L134), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L135-L135), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L145-L145), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L146-L146), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

55:        _approveOperations(IPool(data.pool).token0(), address(aerodromeRouter), data.amount0);	// @audit-issue

56:        _approveOperations(IPool(data.pool).token1(), address(aerodromeRouter), data.amount1);	// @audit-issue

58:            IPool(data.pool).token0(),	// @audit-issue

59:            IPool(data.pool).token1(),	// @audit-issue

60:            IPool(data.pool).stable(),	// @audit-issue

69:        _updateTokenInRegistry(IPool(data.pool).token0());	// @audit-issue

70:        _updateTokenInRegistry(IPool(data.pool).token1());	// @audit-issue

83:            IPool(data.pool).token0(),	// @audit-issue

84:            IPool(data.pool).token1(),	// @audit-issue

85:            IPool(data.pool).stable(),	// @audit-issue

92:        if (IERC20(data.pool).balanceOf(address(this)) == 0) {	// @audit-issue

95:        _updateTokenInRegistry(IPool(data.pool).token0());	// @audit-issue

96:        _updateTokenInRegistry(IPool(data.pool).token1());	// @audit-issue

101:        address gauge = voter.gauges(pool);	// @audit-issue

102:        IERC20(pool).forceApprove(address(gauge), liquidity);	// @audit-issue

103:        IGauge(gauge).deposit(liquidity, address(this));	// @audit-issue

107:        address gauge = voter.gauges(pool);	// @audit-issue

108:        IGauge(gauge).withdraw(liquidity);	// @audit-issue

112:        address gauge = voter.gauges(pool);	// @audit-issue

113:        IGauge(gauge).getReward(address(this));	// @audit-issue

114:        _updateTokenInRegistry(IGauge(gauge).rewardToken());	// @audit-issue

120:        tokens[0] = IPool(pool).token0();	// @audit-issue

121:        tokens[1] = IPool(pool).token1();	// @audit-issue

126:        PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

128:        uint256 balance = IERC20(pool).balanceOf(address(this));	// @audit-issue

129:        uint256 totalSupply = IERC20(pool).totalSupply();	// @audit-issue

130:        (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();	// @audit-issue

133:        return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1);	// @audit-issue
```
[55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L55-L55), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L56-L56), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L58-L58), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L59-L59), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L60-L60), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L69-L69), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L70-L70), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L83-L83), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L84-L84), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L85-L85), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L92-L92), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L95-L95), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L96-L96), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L101-L101), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L102-L102), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L103-L103), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L107-L107), [108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L108-L108), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L112-L112), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L113-L113), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L114-L114), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L120-L120), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L121-L121), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L126-L126), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L128-L128), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L129-L129), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L130-L130), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L133-L133), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

32:        IComet(market).supply(asset, amount);	// @audit-issue

49:        IComet(_market).withdraw(asset, amount);	// @audit-issue

64:        address rewardToken = IRewards(rewardContract).rewardConfig(market).token;	// @audit-issue

85:        uint256 borrowBalanceInBase = comet.borrowBalanceOf(address(this));	// @audit-issue

87:        address basePriceFeed = comet.baseTokenPriceFeed();	// @audit-issue

88:        uint256 basePriceInVirtualBase = comet.getPrice(basePriceFeed);	// @audit-issue

89:        borrowBalanceInVirtualBase = (borrowBalanceInBase * basePriceInVirtualBase) / comet.baseScale();	// @audit-issue

96:        IComet.UserBasic memory userBasic = comet.userBasic(address(this));	// @audit-issue

98:        uint256 basePrice = comet.getPrice(comet.baseTokenPriceFeed());	// @audit-issue

99:        uint256 baseScale = comet.baseScale();	// @audit-issue

104:        uint8 numberOfAssets = comet.numAssets();	// @audit-issue

109:                IComet.AssetInfo memory info = comet.getAssetInfo(i);	// @audit-issue

112:                (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset);	// @audit-issue

115:                uint256 collateralPriceInVirtualBase = comet.getPrice(info.priceFeed);	// @audit-issue

126:        address market = abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address));	// @audit-issue

131:        return (valueOracle.getValue(IComet(market).baseToken(), base, balance));	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L32-L32), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L49-L49), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L64-L64), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L85-L85), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L87-L87), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L88-L88), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L89-L89), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L96-L96), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L98-L98), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L99-L99), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L104-L104), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L109-L109), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L112-L112), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L115-L115), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L126-L126), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L131-L131), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

45:        IERC20 token = IERC20(pool.collateralContract());	// @audit-issue

51:            _updateTokenInRegistry(pool.asset());	// @audit-issue

53:            pool.addCollateral(collateralAmount, address(this));	// @audit-issue

69:        uint256 currentCollateral = pool.userCollateralBalance(address(this));	// @audit-issue

76:        pool.removeCollateral(withdrawAmount, address(this));	// @audit-issue

77:        _updateTokenInRegistry(pool.collateralContract());	// @audit-issue

88:        uint256 repayTokenAmount = pool.toBorrowAmount(sharesToRepay, true);	// @audit-issue

89:        uint256 sharesOwed = pool.userBorrowShares(address(this));	// @audit-issue

90:        address asset = pool.asset();	// @audit-issue

95:        IFraxPair(pool).repayAsset(sharesToRepay, address(this));	// @audit-issue

106:        uint256 exchangeRate = pool.exchangeRateInfo().exchangeRate;	// @audit-issue

122:        uint256 borrowerShares = _fraxlendPair.userBorrowShares(address(this));	// @audit-issue

123:        uint256 _borrowerAmount = _fraxlendPair.toBorrowAmount(borrowerShares, true);	// @audit-issue

125:        uint256 _collateralAmount = _fraxlendPair.userCollateralBalance(address(this));	// @audit-issue

127:        (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();	// @audit-issue

132:        uint256 fraxlendPairMaxLTV = _fraxlendPair.maxLTV();	// @audit-issue

145:        tokens[0] = IFraxPair(pool).collateralContract();	// @audit-issue

146:        tokens[1] = IFraxPair(pool).asset();	// @audit-issue

151:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

153:        uint256 collateralAmount = pool.userCollateralBalance(address(this));	// @audit-issue

154:        uint256 borrowerShares = pool.userBorrowShares(address(this));	// @audit-issue

155:        uint256 _borrowerAmount = pool.toBorrowAmount(borrowerShares, true);	// @audit-issue

157:        uint256 borrowValue = _getValue(pool.asset(), base, _borrowerAmount);	// @audit-issue

158:        uint256 collateralValue = _getValue(pool.collateralContract(), base, collateralAmount);	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L45-L45), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L51-L51), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L53-L53), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L69-L69), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L76-L76), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L77-L77), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L88-L88), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L89-L89), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L90-L90), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L95-L95), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L106-L106), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L122-L122), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L123-L123), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L125-L125), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L127-L127), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L132-L132), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L145-L145), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L146-L146), [151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L151-L151), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L153-L153), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L154-L154), [155](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L155-L155), [157](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L157-L157), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L158-L158), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

70:        address pool = factory.getPair(p.tokenA, p.tokenB);	// @audit-issue

77:        if (IERC20(pool).balanceOf(address(this)) == 0) {	// @audit-issue

90:            abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address, address));	// @audit-issue

91:        address pool = factory.getPair(tokenA, tokenB);	// @audit-issue

92:        uint256 totalSupply = IERC20(pool).totalSupply();	// @audit-issue

93:        (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();	// @audit-issue

95:        uint256 balanceThis = IERC20(pool).balanceOf(address(this));	// @audit-issue
```
[70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L70-L70), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L77-L77), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L90-L90), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L91-L91), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L92-L92), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L93-L93), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L95-L95), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

49:        (tokenId,,,) = positionManager.mint(p);	// @audit-issue

68:        positionManager.decreaseLiquidity(p);	// @audit-issue

74:            positionManager.burn(p.tokenId);	// @audit-issue

92:        positionManager.increaseLiquidity(p);	// @audit-issue

117:        (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);	// @audit-issue

124:        (amount0, amount1) = positionManager.collect(params);	// @audit-issue

128:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

138:            (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);	// @audit-issue

140:            (uint160 sqrtPriceX96,,,,,,) = pool.slot0();	// @audit-issue

142:                sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity	// @audit-issue
```
[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L49-L49), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L68-L68), [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L74-L74), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L92-L92), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L117-L117), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L124-L124), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L128-L128), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L138-L138), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L140-L140), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L142-L142), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

56:            baseRewardPool.getReward();	// @audit-issue

73:            (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(poolId);	// @audit-issue

75:        address pool = IBalancerVault(balancerVault).getPool(poolId);	// @audit-issue

102:            uint256 amount = IERC20(pool).balanceOf(address(this));	// @audit-issue

104:            IRewardPool(_poolInfo.auraPoolAddress).deposit(auraAmount, address(this));	// @audit-issue

112:        IRewardPool(_poolInfo.auraPoolAddress).deposit(_amount, address(this));	// @audit-issue

119:            IRewardPool(_poolInfo.auraPoolAddress).withdrawAndUnwrap(p._auraAmount, true);	// @audit-issue

125:                (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(p.poolId);	// @audit-issue

163:        PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

166:        (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);	// @audit-issue

167:        uint256 _totalSupply = IERC20(pool.pool).totalSupply();	// @audit-issue

178:            auraShares = IERC20(pool.auraPoolAddress).balanceOf(address(this));	// @audit-issue

179:            auraShares = IRewardPool(pool.auraPoolAddress).convertToAssets(auraShares);	// @audit-issue

181:        return IERC20(pool.pool).balanceOf(address(this)) + auraShares;	// @audit-issue

191:        PositionBP memory p = registry.getPositionBP(vaultId, positionId);	// @audit-issue
```
[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L56-L56), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L73-L73), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L75-L75), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L102-L102), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L104-L104), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L112-L112), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L119-L119), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L125-L125), [163](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L163-L163), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L166-L166), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L167-L167), [178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L178-L178), [179](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L179-L179), [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L181-L181), [191](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L191-L191), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

69:        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);	// @audit-issue

73:        if (registry.isAnActiveConnector(vaultId, receiver)) {	// @audit-issue

76:                tokens[i].safeTransfer(receiver, amounts[i]);	// @audit-issue

91:            tokens[i].safeTransfer(msg.sender, amounts[i]);	// @audit-issue

92:            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L69-L69), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L73-L73), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L76-L76), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L91-L91), [92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

27:        SNXCoreProxy.createAccount();	// @audit-issue

50:        (uint256 c,,) = SNXCoreProxy.getAccountCollateral(_accountId, _token);	// @audit-issue

76:        uint128 poolId = SNXCoreProxy.getPreferredPool();	// @audit-issue

88:        uint256[] memory poolIds = SNXCoreProxy.getApprovedPools();	// @audit-issue

110:        address usdToken = SNXCoreProxy.getUsdToken();	// @audit-issue

124:            SNXCoreProxy.getAccountCollateral(accountId, collateralType);	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L27-L27), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L50-L50), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L76-L76), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L88-L88), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L110-L110), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L124-L124), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

72:        (,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));	// @audit-issue

103:        (uint256 totalCollateralBase,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));	// @audit-issue

115:        (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this));	// @audit-issue
```
[72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L72-L72), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L103-L103), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L115-L115), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

38:        IWETH(weth).withdraw(amountIn);	// @audit-issue

57:        uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this));	// @audit-issue

71:        ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);	// @audit-issue

75:        ILidoWithdrawal(lidoWithdrawal).claimWithdrawal(requestId);	// @audit-issue
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L38-L38), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L57-L57), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L71-L71), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L75-L75), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

41:        IBorrowerOperations(zap.borrowerOps()).setDelegateApproval(address(zap), approve);	// @audit-issue

58:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);	// @audit-issue

60:        address debTtoken = ITroveManager(tm).debtToken();	// @audit-issue

78:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);	// @audit-issue

110:        IBorrowerOperations borrowerOps = zapContract.borrowerOps();	// @audit-issue

112:            _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount);	// @audit-issue

115:        _updateTokenInRegistry(ITroveManager(tm).debtToken());	// @audit-issue

117:        uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));	// @audit-issue

132:        IBorrowerOperations borrowerOperations = zapContract.borrowerOps();	// @audit-issue

133:        borrowerOperations.closeTrove(troveManager, address(this));	// @audit-issue

146:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

149:            IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();	// @audit-issue

150:            address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;	// @audit-issue

151:            address debTtoken = ITroveManager(troveManager).debtToken();	// @audit-issue

153:                ITroveManager(troveManager).getTroveCollAndDebt(address(this));	// @audit-issue

166:        IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();	// @audit-issue

167:        address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;	// @audit-issue

168:        address debTtoken = ITroveManager(troveManager).debtToken();	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L41-L41), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L58-L58), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L60-L60), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L78-L78), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L110-L110), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L112-L112), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L115-L115), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L117-L117), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L132-L132), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L133-L133), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L146-L146), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L149-L149), [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L150-L150), [151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L151-L151), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L153-L153), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L166-L166), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L167-L167), [168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L168-L168), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

79:        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();	// @audit-issue

81:        (, address _underlyingToken,) = _SY.assetInfo();	// @audit-issue

98:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue

99:        IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);	// @audit-issue

100:        _YT.mintPY(address(this), address(this));	// @audit-issue

113:        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();	// @audit-issue

114:        IERC20(address(_SY)).safeTransfer(address(market), SYamount);	// @audit-issue

115:        IERC20(address(_PT)).safeTransfer(address(market), PTamount);	// @audit-issue

117:        market.skim();	// @audit-issue

127:        _approveOperations(_market, pendleMarketDepositHelper.pendleStaking(), _amount);	// @audit-issue

128:        pendleMarketDepositHelper.depositMarket(_market, _amount);	// @audit-issue

153:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue

170:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue

188:        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();	// @audit-issue

189:        IERC20(address(_PT)).safeTransfer(address(market), exactPTIn);	// @audit-issue

194:        market.skim();	// @audit-issue

204:        IERC20(address(market)).safeTransfer(address(market), amount);	// @audit-issue

206:        market.skim();	// @audit-issue

217:        (IPStandardizedYield SY,,) = market.readTokens();	// @audit-issue

218:        (, address _underlyingToken,) = SY.assetInfo();	// @audit-issue

221:        IERC20(address(SY)).safeTransfer(address(SY), _amount);	// @audit-issue

242:        market.redeemRewards(address(this));	// @audit-issue

243:        address[] memory rewardTokens = market.getRewardTokens();	// @audit-issue

258:        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

262:            (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue

263:            (, address _underlyingToken,) = _SY.assetInfo();	// @audit-issue

265:            uint256 SYAmount = _SY.balanceOf(address(this));	// @audit-issue

269:                IERC20(market).balanceOf(address(this)) + pendleMarketDepositHelper.balance(market, address(this));	// @audit-issue

271:                SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;	// @audit-issue

274:            uint256 PTAmount = _PT.balanceOf(address(this));	// @audit-issue

275:            if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;	// @audit-issue

277:            uint256 YTBalance = _YT.balanceOf(address(this));	// @audit-issue

280:            if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;	// @audit-issue

294:        (uint256 netSyOut,,,,,,) = staticRouter.swapExactYtForSyStatic(market, balance);	// @audit-issue

304:        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();	// @audit-issue

306:            _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0	// @audit-issue

307:                && market.balanceOf(address(this)) == 0	// @audit-issue

313:        (IPStandardizedYield SY,,) = IPMarket(market).readTokens();	// @audit-issue

315:        (, tokens[0],) = SY.assetInfo();	// @audit-issue
```
[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L79-L79), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L81-L81), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L98-L98), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L99-L99), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L100-L100), [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L113-L113), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L114-L114), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L115-L115), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L117-L117), [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L127-L127), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L128-L128), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L153-L153), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L170-L170), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L188-L188), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L189-L189), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L194-L194), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L204-L204), [206](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L206-L206), [217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L217-L217), [218](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L218-L218), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L221-L221), [242](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L242-L242), [243](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L243-L243), [258](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L258-L258), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L262-L262), [263](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L263-L263), [265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L265-L265), [269](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L269-L269), [271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L271-L271), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L274-L274), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L275-L275), [277](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L277-L277), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L280-L280), [294](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L294-L294), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L304-L304), [306](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L306-L306), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L307-L307), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L313-L313), [315](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L315-L315), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

32:        address token = dolomiteMargin.getMarketTokenAddress(marketId);	// @audit-issue

35:        depositWithdrawalProxy.depositWeiIntoDefaultAccount(marketId, _amount);	// @audit-issue

44:        address token = dolomiteMargin.getMarketTokenAddress(marketId);	// @audit-issue

50:        (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));	// @audit-issue

63:        address token = dolomiteMargin.getMarketTokenAddress(marketId);	// @audit-issue

82:        address token = dolomiteMargin.getMarketTokenAddress(marketId);	// @audit-issue

110:            dolomiteMargin.getAccountBalances(Info(address(this), accountId));	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L32-L32), [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L35-L35), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L44-L44), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L50-L50), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L63-L63), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L82-L82), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L110-L110), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

72:        IRewardsGauge(poolInfo.gauge).deposit(amount);	// @audit-issue

93:        IDepositToken(depostiToken).deposit(address(this), amount);	// @audit-issue

123:        PositionBP memory p = registry.getPositionBP(vaultId, positionId);	// @audit-issue

131:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue

135:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue

139:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue

143:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue

147:            ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);	// @audit-issue

183:        convexBooster.withdraw(pid, amount);	// @audit-issue

193:        IConvexBasicRewards(pool).withdraw(amount, true);	// @audit-issue

203:        IRewardsGauge(pool).withdraw(amount);	// @audit-issue

213:        IDepositToken(depostiToken).withdraw(address(this), amount);	// @audit-issue

223:            IRewardsGauge(gauges[i]).claim_rewards(address(this));	// @audit-issue

235:            IDepositToken(pools[i]).claimReward(address(this));	// @audit-issue

250:            baseRewardPool.getReward(address(this), true);	// @audit-issue

260:        PositionBP memory p = registry.getPositionBP(vaultId, positionId);	// @audit-issue

266:        PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);	// @audit-issue

303:        return curvePool.calc_withdraw_one_coin(amount, tokenIndex);	// @audit-issue

327:        return IConvexBasicRewards(info.convexRewardPool).balanceOf(address(this));	// @audit-issue

336:        return IERC20(info.lpToken).balanceOf(address(this));	// @audit-issue

346:        return IRewardsGauge(info.gauge).balanceOf(address(this));	// @audit-issue

356:        return IDepositToken(prismaPool).balanceOf(address(this));	// @audit-issue
```
[72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L72-L72), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L93-L93), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L123-L123), [131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L131-L131), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L135-L135), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L139-L139), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L143-L143), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L147-L147), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L183-L183), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L193-L193), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L203-L203), [213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L213-L213), [223](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L223-L223), [235](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L235-L235), [250](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L250-L250), [260](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L260-L260), [266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L266-L266), [303](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L303-L303), [327](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L327-L327), [336](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L336-L336), [346](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L346-L346), [356](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L356-L356), 


#### Recommendation

Review your smart contracts to identify and remove `block.number` and `block.timestamp` from the parameters of emitted events. Instead of manually adding these fields, rely on the Ethereum blockchain's inherent inclusion of this information within the block context. Simplify your event definitions to include only the essential data specific to the event's purpose, excluding universally available block metadata.

### Use assembly to check for `address(0)`
In Solidity, it's a common practice to check whether an Ethereum address variable is set to the zero address (`address(0)`) to handle various scenarios, such as token transfers or contract interactions. Typically, this check is performed using a conditional statement like `if (addressVariable == address(0))`.

However, using this approach in high-frequency or gas-sensitive operations can lead to unnecessary gas costs. A more gas-efficient alternative is to use inline assembly to perform the zero address check, which can significantly reduce gas consumption, especially in loops or complex contract logic.

By utilizing inline assembly for this specific check, you can optimize gas usage and make your Solidity code more efficient.

```solidity
Path: ./contracts/accountingManager/Registry.sol

67:        require(_governer != address(0));	// @audit-issue

68:        require(_maintainer != address(0));	// @audit-issue

69:        require(_emergency != address(0));	// @audit-issue

118:        if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();	// @audit-issue

120:        require(_governer != address(0));	// @audit-issue

121:        require(_accountingManager != address(0));	// @audit-issue

122:        require(_baseToken != address(0));	// @audit-issue

123:        require(_maintainer != address(0));	// @audit-issue

124:        require(_keeperContract != address(0));	// @audit-issue

125:        require(_watcher != address(0));	// @audit-issue

141:        vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));	// @audit-issue

167:        require(_governer != address(0));	// @audit-issue

168:        require(_maintainer != address(0));	// @audit-issue

169:        require(_keeperContract != address(0));	// @audit-issue

170:        require(_watcher != address(0));	// @audit-issue
```
[67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L67-L67), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L68-L68), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L69-L69), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L118-L118), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L120-L120), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L121-L121), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L122-L122), [123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L123-L123), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L124-L124), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L125-L125), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L141-L141), [167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L167-L167), [168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L168-L168), [169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L169-L169), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L170-L170), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

15:        require(_accountingManager != address(0));	// @audit-issue

16:        require(_baseToken != address(0));	// @audit-issue

17:        require(_receiver != address(0));	// @audit-issue
```
[15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L15-L15), [16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L16-L16), [17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L17-L17), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

106:        require(p._baseTokenAddress != address(0));	// @audit-issue

107:        require(p._valueOracle != address(0));	// @audit-issue

108:        require(p._withdrawFeeReceiver != address(0));	// @audit-issue

109:        require(p._performanceFeeReceiver != address(0));	// @audit-issue

110:        require(p._managementFeeReceiver != address(0));	// @audit-issue

125:        require(address(_valueOracle) != address(0));	// @audit-issue

140:        require(_withdrawFeeReceiver != address(0));	// @audit-issue

141:        require(_performanceFeeReceiver != address(0));	// @audit-issue

142:        require(_managementFeeReceiver != address(0));	// @audit-issue

186:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {	// @audit-issue

684:        if (token == address(0)) {	// @audit-issue
```
[106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L106-L106), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L107-L107), [108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L108-L108), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L109-L109), [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L110-L110), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L125-L125), [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L140-L140), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L141-L141), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L142-L142), [186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L186-L186), [684](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L684-L684), 


```solidity
Path: ./contracts/governance/Keepers.sol

103:            address lastAdd = address(0);	// @audit-issue
```
[103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L103-L103), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

22:        require(address(_registry) != address(0));	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L22-L22), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

19:            if (positions[i].calculatorConnector == address(0)) {	// @audit-issue
```
[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L19-L19), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

41:        require(_valueOracle != address(0));	// @audit-issue

59:        emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L41-L41), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59-L59), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

86:        if (_request.outputToken == address(0)) {	// @audit-issue

93:        if (_request.outputToken == address(0)) {	// @audit-issue

190:        return address(token) == address(0);	// @audit-issue

194:        if (token == address(0)) {	// @audit-issue
```
[86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L86-L86), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L93-L93), [190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L190-L190), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L194-L194), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

30:        require(address(_registry) != address(0));	// @audit-issue

97:        if (address(oracle) == address(0)) {	// @audit-issue

100:        if (address(oracle) == address(0)) {	// @audit-issue

103:        if (address(oracle) == address(0)) {	// @audit-issue

106:        if (address(oracle) == address(0)) {	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L30-L30), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L97-L97), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L100-L100), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L103-L103), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L106-L106), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

50:        require(pool != address(0), "pool doesn't exist");	// @audit-issue

63:        if (pool == address(0)) {	// @audit-issue

66:        if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);	// @audit-issue
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L50-L50), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L63-L63), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L66-L66), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

47:        require(_reg != address(0));	// @audit-issue

95:        if (primarySource == address(0)) {	// @audit-issue

129:            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));	// @audit-issue

144:        if (assetsSources[asset][baseToken] != address(0)) {	// @audit-issue

146:        } else if (assetsSources[baseToken][asset] != address(0)) {	// @audit-issue

149:        return (address(0), false);	// @audit-issue
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L47-L47), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L95-L95), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L129-L129), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L144-L144), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L146-L146), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L149-L149), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

41:        require(lzHelperAddress != address(0));	// @audit-issue

53:        require(omniChainManager != address(0));	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L41-L41), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L53-L53), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

52:        require(lzHelperAddress != address(0));	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L52-L52), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

37:        require(_lzHelper != address(0));	// @audit-issue

47:        require(destinationAddress != address(0));	// @audit-issue

76:            destChainAddress[bridgeRequest.destChainId] == address(0)	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L37-L37), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L47-L47), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L76-L76), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

46:        require(_mav != address(0));	// @audit-issue

47:        require(_veMav != address(0));	// @audit-issue

48:        require(mr != address(0));	// @audit-issue

49:        require(pi != address(0));	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L46-L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L47-L47), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L48-L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L49-L49), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

24:        require(MB != address(0));	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

22:        require(MC != address(0));	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

36:        require(lpStacking != address(0));	// @audit-issue

37:        require(_stargateRouter != address(0));	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L36-L36), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

78:        if (approvalToken != address(0)) {	// @audit-issue

82:        if (approvalToken != address(0)) {	// @audit-issue
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L78-L78), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L82-L82), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

18:        require(SR != address(0));	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L18-L18), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

43:        require(_router != address(0));	// @audit-issue
```
[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L43-L43), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

37:        require(_router != address(0));	// @audit-issue

38:        require(_factory != address(0));	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L37-L37), [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L38-L38), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

45:        require(_balancerVault != address(0));	// @audit-issue

46:        require(bal != address(0));	// @audit-issue

47:        require(aura != address(0));	// @audit-issue

177:        if (pool.auraPoolAddress != address(0)) {	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L45-L45), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L46-L46), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L47-L47), [177](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L177-L177), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

25:        require(_balancerVault != address(0));	// @audit-issue

26:        require(address(_registry) != address(0));	// @audit-issue

44:        caller = address(0);	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L26-L26), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L44-L44), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

21:        require(_SNXCoreProxy != address(0));	// @audit-issue
```
[21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L21-L21), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

36:        require(_pool != address(0));	// @audit-issue

37:        require(_poolBaseToken != address(0));	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L36-L36), [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L37-L37), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

23:        require(_lido != address(0));	// @audit-issue

24:        require(_lidoW != address(0));	// @audit-issue

25:        require(_steth != address(0));	// @audit-issue

26:        require(w != address(0));	// @audit-issue

41:        ILido(lido).submit{ value: amountIn }(address(0));	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L23-L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L24-L24), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L26-L26), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L41-L41), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

60:        require(_pendleMarketDepositHelper != address(0));	// @audit-issue

61:        require(_pendleRouter != address(0));	// @audit-issue

62:        require(SR != address(0));	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L60-L60), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L61-L61), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L62-L62), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

24:        require(_depositWithdrawalProxy != address(0));	// @audit-issue
```
[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L24-L24), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

52:        require(_convexBooster != address(0));	// @audit-issue

53:        require(cvx != address(0));	// @audit-issue

54:        require(crv != address(0));	// @audit-issue

55:        require(prisma != address(0));	// @audit-issue

126:        address poolAddress = (poolInfo.tokens.length > 2 && poolInfo.zap != address(0)) ? poolInfo.zap : pool;	// @audit-issue

283:        if (info.poolAddressIfDefaultWithdrawTokenIsAnotherPosition != address(0)) {	// @audit-issue

326:        if (info.convexRewardPool == address(0)) return 0;	// @audit-issue

345:        if (info.gauge == address(0)) return 0;	// @audit-issue

355:        if (prismaPool == address(0)) return 0;	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L52-L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L53-L53), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L54-L54), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L55-L55), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L126-L126), [283](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L283-L283), [326](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L326-L326), [345](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L345-L345), [355](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L355-L355), 


#### Recommendation

To optimize gas usage in your Solidity code, consider using inline assembly for checking `address(0)`. This approach can significantly reduce gas costs, especially in high-frequency or gas-sensitive operations, leading to more efficient contract execution.

### Use assembly to check for `0`
Using assembly to check for zero can save gas by allowing more direct access to the evm and reducing some of the overhead associated with high-level operations in solidity.

```solidity
Path: ./contracts/accountingManager/Registry.sol

304:        if (index == 0) {	// @audit-issue

347:        if (positionIndex == 0 && removePosition) return type(uint256).max;	// @audit-issue
```
[304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L304-L304), [347](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L347-L347), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

201:        if (amount == 0) {	// @audit-issue

288:        if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {	// @audit-issue

374:        if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {	// @audit-issue

438:        if (withdrawFeeAmount > 0) {	// @audit-issue

528:            preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours	// @audit-issue

634:        if (p.positionTypeId == 0) {	// @audit-issue

650:        if (positionTypeId == 0) {	// @audit-issue
```
[201](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L201-L201), [288](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L288-L288), [374](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L374-L374), [438](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L438-L438), [528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L528-L528), [634](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L634-L634), [650](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L650-L650), 


```solidity
Path: ./contracts/helpers/TVLHelper.sol

45:            if (latestUpdateTime == 0 || positions[i].positionTimestamp < latestUpdateTime) {	// @audit-issue

49:        if (latestUpdateTime == 0) {	// @audit-issue
```
[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L45-L45), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L49-L49), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

142:        if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {	// @audit-issue

159:        _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0);	// @audit-issue

233:        if (positionTypeId == 0) {	// @audit-issue

257:        if (amount == 0) {	// @audit-issue
```
[142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L142-L142), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L159-L159), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L233-L233), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L257-L257), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

98:        if (_swapRequest.amount == 0) revert InvalidAmount();	// @audit-issue

102:        if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {	// @audit-issue

105:            if (_slippageTolerance == 0) {	// @audit-issue
```
[98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L98-L98), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L102-L102), [105](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L105-L105), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

72:        if (asset == baseToken || amount == 0) {	// @audit-issue
```
[72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L72-L72), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

39:        if (_period == 0) revert INoyaValueOracle_InvalidInput();	// @audit-issue

82:        if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L39-L39), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L82-L82), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

128:        if (price <= 0) {	// @audit-issue
```
[128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L128-L128), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

58:        if (approvedBridgeTXN[transactionHash] != 0) delete approvedBridgeTXN[transactionHash];	// @audit-issue

71:        if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {	// @audit-issue
```
[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L58-L58), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71-L71), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

35:        if (bp.positionTypeId == 0) {	// @audit-issue
```
[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L35-L35), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

141:            if (earnedInfo[i].earned != 0) {	// @audit-issue
```
[141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L141-L141), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

66:        if (p.collateral == 0 && p.supplyShares == 0) {	// @audit-issue

112:        if (borrowAmount == 0) return type(uint256).max;	// @audit-issue
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L66-L66), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L112-L112), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

52:        if (depositRequest.routerAmount > 0) {	// @audit-issue

57:        if (depositRequest.LPStakingAmount > 0) {	// @audit-issue

79:        if (withdrawRequest.LPStakingAmount > 0) {	// @audit-issue

82:        if (withdrawRequest.routerAmount > 0) {	// @audit-issue

89:        if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) {	// @audit-issue

115:        if (lpAmount == 0) {	// @audit-issue
```
[52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L52-L52), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L57-L57), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L79-L79), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L82-L82), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L89-L89), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L115-L115), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

120:            if (depositAmount == 0 && borrowAmount == 0) {	// @audit-issue

134:                IERC20(assetsS[i].collateralToken).balanceOf(address(this))	// @audit-issue
```
[120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L120-L120), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L134-L134), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

92:        if (IERC20(data.pool).balanceOf(address(this)) == 0) {	// @audit-issue
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

53:        if (getCollBlanace(IComet(_market), false) == 0) {	// @audit-issue

77:        if (borrowBalanceInBase == 0) return type(uint256).max;	// @audit-issue

86:        if (borrowBalanceInBase == 0) return 0;	// @audit-issue

100:        if (userBasic.principal > 0) {	// @audit-issue

142:        return (assetsIn & (uint16(1) << assetOffset) != 0);	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L53-L53), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L77-L77), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L86-L86), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L100-L100), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L142-L142), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

46:        if (collateralAmount > 0) {	// @audit-issue

49:        if (borrowAmount > 0) {	// @audit-issue

52:        } else if (collateralAmount > 0) {	// @audit-issue

55:        if (collateralAmount > 0) {	// @audit-issue

124:        if (_borrowerAmount == 0) return type(uint256).max;	// @audit-issue

126:        if (_collateralAmount == 0) return 0;	// @audit-issue

133:        if (currentPositionLTV == 0) return type(uint256).max; // loan is small	// @audit-issue
```
[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L46-L46), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L49-L49), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L52-L52), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L55-L55), [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L124-L124), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L126-L126), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L133-L133), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

77:        if (IERC20(pool).balanceOf(address(this)) == 0) {	// @audit-issue
```
[77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L77-L77), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

78:            if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);	// @audit-issue

99:        if (auraAmount > 0) {	// @audit-issue

116:        if (p._auraAmount > 0) {	// @audit-issue

122:        if (p._lpAmount > 0) {	// @audit-issue

146:            if (totalLpBalanceOf(p.poolId) == 0) {	// @audit-issue
```
[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L78-L78), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L99-L99), [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L116-L116), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L122-L122), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L146-L146), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

92:            require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");	// @audit-issue
```
[92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L92-L92), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

51:        if (c == 0) {	// @audit-issue
```
[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L51-L51), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

79:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue

107:        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {	// @audit-issue

111:        if (bAmount > 0 && !isBorrowing) {	// @audit-issue
```
[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L79-L79), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L107-L107), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L111-L111), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

270:            if (lpBalance > 0) {	// @audit-issue

275:            if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;	// @audit-issue

278:            if (YTBalance > 0) SYAmount += getYTValue(market, YTBalance);	// @audit-issue

280:            if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;	// @audit-issue

306:            _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0	// @audit-issue

307:                && market.balanceOf(address(this)) == 0	// @audit-issue
```
[270](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L270-L270), [275](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L275-L275), [278](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L278-L278), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L280-L280), [306](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L306-L306), [307](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L307-L307), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

51:        if (markets.length == 0) {	// @audit-issue
```
[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L51-L51), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

171:        if (totalLpBalanceOf(poolInfo) == 0) {	// @audit-issue

280:        if (balance == 0) return (0, info.tokens[info.defaultWithdrawIndex]);	// @audit-issue
```
[171](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L171-L171), [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L280-L280), 


#### Recommendation

To optimize gas usage in your Solidity code, consider using inline assembly for checking `0`. This approach can significantly reduce gas costs, especially in high-frequency or gas-sensitive operations, leading to more efficient contract execution.

### Use assembly to write `address` storage values
Using assembly `{ sstore(state.slot, addr)}` instead of `state = addr` can save gas.


```solidity
Path: ./contracts/accountingManager/Registry.sol

76:        flashLoan = _flashLoan;	// @audit-issue

86:        flashLoan = _flashLoan;	// @audit-issue

172:        vaults[vaultId].governer = _governer;	// @audit-issue

173:        vaults[vaultId].maintainer = _maintainer;	// @audit-issue

174:        vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock;	// @audit-issue

175:        vaults[vaultId].keeperContract = _keeperContract;	// @audit-issue

176:        vaults[vaultId].watcherContract = _watcher;	// @audit-issue

177:        vaults[vaultId].emergency = _emergency;	// @audit-issue
```
[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L76-L76), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L86-L86), [172](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L172-L172), [173](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L173-L173), [174](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L174-L174), [175](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L175-L175), [176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L176-L176), [177](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L177-L177), 


```solidity
Path: ./contracts/accountingManager/NoyaFeeReceiver.sol

18:        accountingManager = _accountingManager;	// @audit-issue

19:        baseToken = _baseToken;	// @audit-issue

20:        receiver = _receiver;	// @audit-issue
```
[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L18-L18), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L19-L19), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L20-L20), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

126:        valueOracle = _valueOracle;	// @audit-issue

143:        withdrawFeeReceiver = _withdrawFeeReceiver;	// @audit-issue

144:        performanceFeeReceiver = _performanceFeeReceiver;	// @audit-issue

145:        managementFeeReceiver = _managementFeeReceiver;	// @audit-issue
```
[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L126-L126), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L143-L143), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L144-L144), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L145-L145), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

23:        registry = _registry;	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L23-L23), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

59:        swapHandler = SwapAndBridgeHandler(_swapHandler);	// @audit-issue

68:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue
```
[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L59-L59), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L68-L68), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

40:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue

49:        valueOracle = INoyaValueOracle(_valueOracle);	// @audit-issue
```
[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L40-L40), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L49-L49), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

29:        lifi = _lifi;	// @audit-issue
```
[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L29-L29), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

31:        registry = _registry;	// @audit-issue
```
[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L31-L31), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

32:        factory = _factory;	// @audit-issue

33:        registry = _registry;	// @audit-issue
```
[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L32-L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L33-L33), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

48:        registry = PositionRegistry(_reg);	// @audit-issue
```
[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L48-L48), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

36:        lzHelper = _lzHelper;	// @audit-issue

48:        destChainAddress[chainId] = destinationAddress;	// @audit-issue
```
[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L36-L36), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L48-L48), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

50:        mav = _mav;	// @audit-issue

51:        veMav = _veMav;	// @audit-issue

52:        maverickRouter = mr;	// @audit-issue

53:        positionInspector = IPositionInspector(pi);	// @audit-issue
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L50-L50), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L51-L51), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L52-L52), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L53-L53), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

25:        morphoBlue = IMorpho(MB);	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L25-L25), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

23:        masterchef = IMasterchefV3(MC);	// @audit-issue
```
[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L23-L23), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

39:        LPStaking = IStargateLPStaking(lpStacking);	// @audit-issue

40:        stargateRouter = IStargateRouter(_stargateRouter);	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L39-L39), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L40-L40), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

20:        siloRepository = ISiloRepository(SR);	// @audit-issue
```
[20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L20-L20), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

44:        aerodromeRouter = IRouter(_router);	// @audit-issue

45:        voter = IVoter(_voter);	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L44-L44), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L45-L45), 


```solidity
Path: ./contracts/connectors/CamelotConnector.sol

39:        router = ICamelotRouter(_router);	// @audit-issue

40:        factory = ICamelotFactory(_factory);	// @audit-issue
```
[39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L39-L39), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L40-L40), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

30:        positionManager = INonfungiblePositionManager(_positionManager);	// @audit-issue

31:        factory = IUniswapV3Factory(_factory);	// @audit-issue
```
[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L30-L30), [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L31-L31), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

48:        AURA = aura;	// @audit-issue

49:        BAL = bal;	// @audit-issue

50:        balancerVault = _balancerVault;	// @audit-issue
```
[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L48-L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L49-L49), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L50-L50), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

27:        vault = IBalancerVault(_balancerVault);	// @audit-issue

28:        registry = _registry;	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L27-L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L28-L28), 


```solidity
Path: ./contracts/connectors/SNXConnector.sol

22:        SNXCoreProxy = IV3CoreProxy(_SNXCoreProxy);	// @audit-issue
```
[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L22-L22), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

38:        poolBaseToken = _poolBaseToken;	// @audit-issue

39:        pool = _pool;	// @audit-issue
```
[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L38-L38), [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L39-L39), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

27:        lido = _lido;	// @audit-issue

28:        lidoWithdrawal = _lidoW;	// @audit-issue

29:        steth = _steth;	// @audit-issue

30:        weth = w;	// @audit-issue
```
[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L27-L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L28-L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L29-L29), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L30-L30), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

63:        pendleMarketDepositHelper = IPendleMarketDepositHelper(_pendleMarketDepositHelper);	// @audit-issue

64:        pendleRouter = IPAllActionV3(_pendleRouter);	// @audit-issue

65:        staticRouter = IPendleStaticRouter(SR);	// @audit-issue
```
[63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L63-L63), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L64-L64), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L65-L65), 


```solidity
Path: ./contracts/connectors/Dolomite.sol

25:        depositWithdrawalProxy = IDepositWithdrawalProxy(_depositWithdrawalProxy);	// @audit-issue

26:        dolomiteMargin = IDolomiteMargin(_dolomiteMargin);	// @audit-issue

27:        borrowPositionProxy = IBorrowPositionProxyV1(_borrowPositionProxy);	// @audit-issue
```
[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L25-L25), [26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L26-L26), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L27-L27), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

56:        convexBooster = IBooster(_convexBooster);	// @audit-issue

57:        CVX = cvx;	// @audit-issue

58:        CRV = crv;	// @audit-issue

59:        PRISMA = prisma;	// @audit-issue
```
[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L56-L56), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L57-L57), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L58-L58), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L59-L59), 


#### Recommendation

To reduce gas costs in your Solidity code, consider using assembly with `{ sstore(state.slot, addr) }` for writing `address` storage values instead of `state = addr`. This approach can result in significant gas savings.

### Use assembly to emit an `event`
To efficiently emit events, it's possible to utilize assembly by making use of scratch space and the free memory pointer. This approach has the advantage of potentially avoiding the costs associated with memory expansion.

However, it's important to note that in order to safely optimize this process, it is preferable to cache and restore the free memory pointer.

A good example of such practice can be seen in [Solady's](https://github.com/Vectorized/solady/blob/main/src/tokens/ERC1155.sol#L167) codebase.


```solidity
Path: ./contracts/accountingManager/Registry.sol

85:        emit updateFlashloanAddress(_flashLoan, flashLoan);	// @audit-issue

142:        emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens);	// @audit-issue

143:        emit VaultAddressesChanged(	// @audit-issue

178:        emit VaultAddressesChanged(	// @audit-issue

196:            emit ConnectorAdded(vaultId, _connectorAddresses[i]);	// @audit-issue

217:        emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted);	// @audit-issue

262:        emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data);	// @audit-issue

279:        emit TrustedPositionRemoved(vaultId, _positionId);	// @audit-issue

302:        emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index);	// @audit-issue

361:            emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);	// @audit-issue
```
[85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L85-L85), [142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L142-L142), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L143-L143), [178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L178-L178), [196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L196-L196), [217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L217-L217), [262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L262-L262), [279](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L279-L279), [302](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L302-L302), [361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L361-L361), 


```solidity
Path: ./contracts/accountingManager/AccountingManager.sol

127:        emit ValueOracleUpdated(address(_valueOracle));	// @audit-issue

146:        emit FeeRecepientsChanged(_withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver);	// @audit-issue

154:        emit TransferTokensToTrustedAddress(token, amount, _caller, _data);	// @audit-issue

180:        emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee);	// @audit-issue

216:        emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);	// @audit-issue

242:            emit CalculateDeposit(	// @audit-issue

274:            emit ExecuteDeposit(	// @audit-issue

314:        emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);	// @audit-issue

349:            emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);	// @audit-issue

364:        emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);	// @audit-issue

387:        emit WithdrawGroupFulfilled(	// @audit-issue

429:            emit ExecuteWithdraw(	// @audit-issue

455:            emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw);	// @audit-issue

462:            emit ResetMiddle(newMiddle, withdrawQueue.middle, depositOrWithdraw);	// @audit-issue

485:        emit RecordProfit(	// @audit-issue

496:            emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);	// @audit-issue

520:        emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares);	// @audit-issue

538:        emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);	// @audit-issue

562:            emit RetrieveTokensForWithdraw(	// @audit-issue

670:        emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount);	// @audit-issue

675:        emit SetDepositWaitingTime(_depositWaitingTime);	// @audit-issue

680:        emit SetWithdrawWaitingTime(_withdrawWaitingTime);	// @audit-issue

690:        emit Rescue(msg.sender, token, amount);	// @audit-issue
```
[127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L127-L127), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L146-L146), [154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L154-L154), [180](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L180-L180), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L216-L216), [242](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L242-L242), [274](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L274-L274), [314](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L314-L314), [349](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L349-L349), [364](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L364-L364), [387](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L387-L387), [429](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L429-L429), [455](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L455-L455), [462](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L462-L462), [485](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L485-L485), [496](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L496-L496), [520](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L520-L520), [538](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L538-L538), [562](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L562-L562), [670](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L670-L670), [675](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L675-L675), [680](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L680-L680), [690](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L690-L690), 


```solidity
Path: ./contracts/governance/Keepers.sol

55:        emit UpdateOwners(_owners, addOrRemove);	// @audit-issue

66:        emit UpdateThreshold(_threshold);	// @audit-issue

115:        emit Execute(destination, data, gasLimit, executor, deadline);	// @audit-issue
```
[55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L55-L55), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L66-L66), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L115-L115), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

50:        emit MinimumHealthFactorUpdated(_minimumHealthFactor);	// @audit-issue

60:        emit SwapHandlerUpdated(_swapHandler);	// @audit-issue

69:        emit ValueOracleUpdated(_valueOracle);	// @audit-issue

88:        emit TransferTokensToTrustedAddress(token, amount, caller, data);	// @audit-issue

128:        emit TransferPositionToConnector(tokens, amounts, connector, data);	// @audit-issue

143:            emit UpdateTokenInRegistry(token, remove);	// @audit-issue

192:        emit AddLiquidity(tokens, amounts, data);	// @audit-issue

217:            emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);	// @audit-issue
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L50-L50), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L60-L60), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L69-L69), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L88-L88), [128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L128-L128), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L143-L143), [192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L192-L192), [217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L217-L217), 


```solidity
Path: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

50:        emit SetValueOracle(_valueOracle);	// @audit-issue

59:        emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);	// @audit-issue

73:        emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance);	// @audit-issue

82:        emit AddEligibleUser(_user);	// @audit-issue

117:        emit ExecutionCompleted(	// @audit-issue

139:        emit BridgeExecutionCompleted(_bridgeRequest);	// @audit-issue

150:            emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);	// @audit-issue

160:        emit RouteUpdate(_routeId, false);	// @audit-issue
```
[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L50-L50), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59-L59), [73](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L73-L73), [82](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L82-L82), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L117-L117), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L139-L139), [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L150-L150), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160-L160), 


```solidity
Path: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

47:        emit AddedHandler(_handler, state);	// @audit-issue

57:        emit AddedChain(_chainId, state);	// @audit-issue

67:        emit AddedBridgeBlacklist(bridgeName, state);	// @audit-issue

99:        emit Swapped(balanceOut0, balanceOut1, _request.outputToken);	// @audit-issue

141:        emit Bridged(_request.from, _request.inputToken, _request.amount, _request.data);	// @audit-issue

182:        emit Forwarded(lifi, address(token), amount, data);	// @audit-issue

200:        emit Rescued(token, userAddress, amount);	// @audit-issue
```
[47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L47-L47), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L57-L57), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L67-L67), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L99-L99), [141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L141-L141), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L182-L182), [200](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L200-L200), 


```solidity
Path: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

44:        emit UpdatedDefaultPriceSource(baseCurrencies, oracles);	// @audit-issue

58:        emit UpdatedAssetPriceSource(asset, baseToken, oracle);	// @audit-issue

63:        emit UpdatedPriceRoute(asset, base, s);	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L44-L44), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L58-L58), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L63-L63), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

41:        emit NewPeriod(_period);	// @audit-issue

52:        emit PoolsForAsset(tokenIn, baseToken, pool);	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L41-L41), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L52-L52), 


```solidity
Path: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

61:        emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);	// @audit-issue

76:            emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);	// @audit-issue
```
[61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L61-L61), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L76-L76), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

49:        emit UpdateChainInfo(chainId, destinationAddress);	// @audit-issue

60:        emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp);	// @audit-issue

70:        emit StartBridgeTransaction(bridgeRequest, txn);	// @audit-issue
```
[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L49-L49), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L60-L60), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L70-L70), 


```solidity
Path: ./contracts/connectors/MaverickConnector.sol

71:        emit Stake(amount, duration, doDelegation);	// @audit-issue

83:        emit Unstake(lockupId);	// @audit-issue

107:        emit AddLiquidityInMaverickPool(p);	// @audit-issue

130:        emit RemoveLiquidityFromMaverickPool(p);	// @audit-issue

146:        emit ClaimBoostedPositionRewards(rewardContract);	// @audit-issue
```
[71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L71-L71), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L83-L83), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L107-L107), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L130-L130), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L146-L146), 


```solidity
Path: ./contracts/connectors/MorphoBlueConnector.sol

49:        emit Supply(amount, id, sOrC);	// @audit-issue

72:        emit Withdraw(amount, id, sOrC);	// @audit-issue

87:        emit Borrow(amount, id);	// @audit-issue

100:        emit Repay(amount, id);	// @audit-issue
```
[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L49-L49), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L72-L72), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L87-L87), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L100-L100), 


```solidity
Path: ./contracts/connectors/PancakeswapConnector.sol

33:        emit SendPositionToMasterChef(tokenId);	// @audit-issue

43:        emit UpdatePosition(tokenId);	// @audit-issue

53:        emit Withdraw(tokenId);	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L33-L33), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L43-L43), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L53-L53), 


```solidity
Path: ./contracts/connectors/StargateConnector.sol

69:        emit DepositIntoStargatePool(depositRequest);	// @audit-issue

96:        emit WithdrawFromStargatePool(withdrawRequest);	// @audit-issue

106:        emit ClaimStargateRewards(poolId);	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L69-L69), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L96-L96), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L106-L106), 


```solidity
Path: ./contracts/connectors/GearBoxV3.sol

33:        emit OpenAccount(facade, ref);	// @audit-issue

51:        emit CloseAccount(facade, creditAccount);	// @audit-issue

85:        emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L33-L33), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L51-L51), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L85-L85), 


```solidity
Path: ./contracts/connectors/SiloConnector.sol

41:        emit Deposit(siloToken, dToken, amount, oC);	// @audit-issue

68:        emit Withdraw(siloToken, wToken, amount, oC, closePosition);	// @audit-issue

89:        emit Borrow(siloToken, bToken, amount);	// @audit-issue

106:        emit Repay(siloToken, rToken, amount);	// @audit-issue
```
[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L41-L41), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L68-L68), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L89-L89), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L106-L106), 


```solidity
Path: ./contracts/connectors/AerodromeConnector.sol

72:        emit Supply(data.pool, data.amount0, data.amount1);	// @audit-issue

97:        emit Withdraw(data.pool, data.amountLiquidity);	// @audit-issue
```
[72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L72-L72), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L97-L97), 


```solidity
Path: ./contracts/connectors/CompoundConnector.sol

37:        emit Supply(market, asset, amount);	// @audit-issue

59:        emit WithdrawOrBorrow(_market, asset, amount);	// @audit-issue

67:        emit ClaimRewards(rewardContract, market);	// @audit-issue
```
[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L37-L37), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L59-L59), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L67-L67), 


```solidity
Path: ./contracts/connectors/FraxConnector.sol

60:        emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount);	// @audit-issue

79:        emit Withdraw(address(pool), withdrawAmount);	// @audit-issue

97:        emit Repay(address(pool), sharesToRepay);	// @audit-issue
```
[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L60-L60), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L79-L79), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L97-L97), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

56:        emit OpenPosition(p, tokenId);	// @audit-issue

80:        emit DecreasePosition(p);	// @audit-issue

95:        emit IncreasePosition(p);	// @audit-issue

107:            emit CollectFees(tokenIds[i]);	// @audit-issue
```
[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L56-L56), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L80-L80), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L95-L95), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L107-L107), 


```solidity
Path: ./contracts/connectors/BalancerConnector.sol

106:        emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount);	// @audit-issue

159:        emit DecreasePosition(p);	// @audit-issue
```
[106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L106-L106), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L159-L159), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

42:        emit MakeFlashLoan(tokens, amounts);	// @audit-issue

60:        emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);	// @audit-issue
```
[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L42-L42), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L60-L60), 


```solidity
Path: ./contracts/connectors/AaveConnector.sol

53:        emit Supply(supplyToken, amount);	// @audit-issue

75:        emit Borrow(_borrowAsset, _amount);	// @audit-issue

85:        emit Repay(asset, amount, i);	// @audit-issue

90:        emit RepayWithCollateral(_borrowAsset, _amount, i);	// @audit-issue

111:        emit WithdrawCollateral(_collateral, _collateralAmount);	// @audit-issue
```
[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L53-L53), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L75-L75), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L85-L85), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L90-L90), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L111-L111), 


```solidity
Path: ./contracts/connectors/LidoConnector.sol

44:        emit Deposit(amountIn);	// @audit-issue

62:        emit RequestWithdrawals(amount);	// @audit-issue

86:        emit ClaimWithdrawal(requestId);	// @audit-issue
```
[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L44-L44), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L62-L62), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L86-L86), 


```solidity
Path: ./contracts/connectors/PrismaConnector.sol

66:        emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);	// @audit-issue

85:        emit AddColl(address(zapContract), tm, amountIn);	// @audit-issue

121:        emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);	// @audit-issue

135:        emit CloseTrove(address(zapContract), troveManager);	// @audit-issue
```
[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L66-L66), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L85-L85), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L121-L121), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L135-L135), 


```solidity
Path: ./contracts/connectors/PendleConnector.sol

89:        emit Supply(market, syMinted);	// @audit-issue

101:        emit MintPTAndYT(market, syAmount);	// @audit-issue

118:        emit DepositIntoMarket(address(market), SYamount, PTamount);	// @audit-issue

129:        emit DepositIntoPenpie(_market, _amount);	// @audit-issue

139:        emit WithdrawFromPenpie(_market, _amount);	// @audit-issue

156:        emit SwapYTForPT(market, exactYTIn, min, guess);	// @audit-issue

173:        emit SwapYTForSY(market, exactYTIn, min, orderData);	// @audit-issue

195:        emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY);	// @audit-issue

207:        emit BurnLP(address(market), amount);	// @audit-issue

232:        emit DecreasePosition(address(market), _amount, closePosition);	// @audit-issue

247:        emit ClaimRewards(address(market));	// @audit-issue
```
[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L89-L89), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L101-L101), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L118-L118), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L129-L129), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L139-L139), [156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L156-L156), [173](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L173-L173), [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L195-L195), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L207-L207), [232](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L232-L232), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L247-L247), 


```solidity
Path: ./contracts/connectors/CurveConnector.sol

149:        emit OpenCurvePosition(pool, depositIndex, amount, minAmount);	// @audit-issue

174:        emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount);	// @audit-issue

184:        emit WithdrawFromConvexBooster(pid, amount);	// @audit-issue

194:        emit WithdrawFromConvexRewardPool(pool, amount);	// @audit-issue

204:        emit WithdrawFromGauge(pool, amount);	// @audit-issue

214:        emit WithdrawFromPrisma(depostiToken, amount);	// @audit-issue

226:        emit HarvestRewards(gauges);	// @audit-issue

240:        emit HarvestPrismaRewards(pools);	// @audit-issue

254:        emit HarvestConvexRewards(rewardsPools);	// @audit-issue
```
[149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L149-L149), [174](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L174-L174), [184](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L184-L184), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L194-L194), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L204-L204), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L214-L214), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L226-L226), [240](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L240-L240), [254](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L254-L254), 


#### Recommendation

To optimize event emission in your Solidity code, consider using assembly with scratch space and the free memory pointer. This approach can help reduce gas costs by avoiding memory expansion expenses. However, it's crucial to ensure safe optimization by caching and restoring the free memory pointer, as demonstrated in examples like Solady's codebase.

### Use assembly to validate `msg.sender`
We can use assembly to efficiently validate `msg.sender` with the least amount of opcodes necessary. For more details check the following report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender)


```solidity
Path: ./contracts/accountingManager/Registry.sol

33:        if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

40:        if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue

47:        if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L33-L33), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L40-L40), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L47-L47), 


```solidity
Path: ./contracts/governance/Keepers.sol

97:        require(executor == msg.sender, "Invalid executor");	// @audit-issue
```
[97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L97-L97), 


```solidity
Path: ./contracts/governance/NoyaGovernanceBase.sol

33:        if (!(msg.sender == keeperContract || msg.sender == emergencyManager || msg.sender == registry.flashLoan())) {	// @audit-issue

45:        if (msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);	// @audit-issue

55:        if (msg.sender != emergencyManager && msg.sender != watcherContract) {	// @audit-issue

67:        if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);	// @audit-issue

77:        if (msg.sender != maintainer) revert NoyaGovernance_Unauthorized(msg.sender);	// @audit-issue

87:        if (msg.sender != governer) revert NoyaGovernance_Unauthorized(msg.sender);	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L33-L33), [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L45-L45), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L55-L55), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L67-L67), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L77-L77), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L87-L87), 


```solidity
Path: ./contracts/helpers/BaseConnector.sol

90:        if (msg.sender == accountingManager) {	// @audit-issue

98:        } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {	// @audit-issue
```
[90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L90-L90), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L98-L98), 


```solidity
Path: ./contracts/helpers/LZHelpers/LZHelperSender.sol

76:        if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();	// @audit-issue
```
[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L76-L76), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

33:        if (msg.sender != lzHelper) revert IConnector_InvalidSender();	// @audit-issue
```
[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L33-L33), 


```solidity
Path: ./contracts/connectors/BalancerFlashLoan.sol

61:        require(msg.sender == address(vault));	// @audit-issue
```
[61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L61-L61), 


#### Recommendation

To optimize the validation of `msg.sender` in your Solidity code, consider using assembly to achieve this with the minimum number of opcodes required. You can refer to the detailed report [Here](https://code4rena.com/reports/2023-05-juicebox#g-06-use-assembly-to-validate-msgsender) for more insights and examples on efficient implementation.

### Use assembly to write hashes
Considering using [assembly](https://medium.com/@kalexotsu/understanding-solidity-assembly-hashing-a-string-from-calldata-fbd2ece82263) to write hashes, as it's possible to save a considerable amount of gas.


```solidity
Path: ./contracts/accountingManager/Registry.sol

345:        bytes32 holdingPositionId = keccak256(abi.encode(msg.sender, _positionId, _data));	// @audit-issue

351:                vault.isPositionUsed[keccak256(	// @audit-issue

399:        bytes32 holdingPositionId = keccak256(abi.encode(_connector, _positionId, data));	// @audit-issue

491:        return keccak256(abi.encode(calculatorConnector, positionTypeId, data));	// @audit-issue
```
[345](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L345-L345), [351](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L351-L351), [399](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L399-L399), [491](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L491-L491), 


```solidity
Path: ./contracts/governance/Keepers.sol

101:                keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));	// @audit-issue

102:            bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));	// @audit-issue
```
[101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L101-L101), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L102-L102), 


```solidity
Path: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

69:        bytes32 txn = keccak256(abi.encode(bridgeRequest));	// @audit-issue
```
[69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L69-L69), 


```solidity
Path: ./contracts/connectors/UNIv3Connector.sol

136:            bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));	// @audit-issue
```
[136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L136-L136), 


#### Recommendation

To achieve gas savings in your Solidity code when writing hashes, consider using assembly, as it can significantly reduce gas consumption. You can refer to this [article](https://medium.com/@kalexotsu/understanding-solidity-assembly-hashing-a-string-from-calldata-fbd2ece82263) for insights on how to efficiently implement hash operations.