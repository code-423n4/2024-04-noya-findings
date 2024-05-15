# Gas Optimizations

## Table of Contents
| Number | Optimization Details                                                     | Instances |
| :----: | :----------------------------------------------------------------------- | :-------: |
| [G‑01] | Use `revert()` to gain maximum gas savings                               |    98     |
| [G‑02] | Use nested if and avoid multiple check combinations                      |    19     |
| [G-03] | Declare `immutable` as `private` to save gas                             |     3     |
| [G‑04] | Use assembly to write address storage values                             |    16     |
| [G‑05] | Use `unchecked` for Non-Loop Increment/Decrement Operations              |     3     |
| [G‑06] | Using Storage Instead of Memory for structs/arrays Saves Gas             |    44     |
| [G‑07] | Setting the constructor to payable                                       |    39     |
| [G-08] | Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead |    60     |
| [G-09] | Use `assembly` for efficient event emission                              |    139    |
| [G‑10] | Optimize names to save gas                                               | All files |
| [G-11] | Reduce deployment costs by tweaking contracts' metadata                  | All files |
| [G‑12] | Optimize names to save gas                                               |    13     |

## [G-01] Use `revert()` to gain maximum gas savings 

If you dont need Error messages, or you want gain maximum gas savings - `revert()` is a cheapest way to revert transaction in terms of gas.
```solidity
    revert(); // 117 gas 
    require(false); // 132 gas
    revert CustomError(); // 157 gas
    assert(false); // 164 gas
    revert("Custom Error"); // 406 gas
    require(false, "Custom Error"); // 421 gas
```


<details>
<summary><i>98 issue instances in 24 files:</i></summary>

```solidity
File: contracts/accountingManager/AccountingManager.sol

116: revert NoyaAccounting_INVALID_FEE();
175: revert NoyaAccounting_INVALID_FEE();
187: revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
202: revert NoyaAccounting_INVALID_AMOUNT();
208: revert NoyaAccounting_DepositLimitPerTransactionExceeded();
212: revert NoyaAccounting_TotalDepositLimitExceeded();
295: revert NoyaAccounting_INVALID_CONNECTOR();
306: revert NoyaAccounting_INSUFFICIENT_FUNDS(
336: revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
375: revert NoyaAccounting_NOT_READY_TO_FULFILL();
398: revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
458: revert NoyaAccounting_INVALID_AMOUNT();
465: revert NoyaAccounting_INVALID_AMOUNT();
560: if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
571: revert NoyaAccounting_INVALID_AMOUNT();
694: revert NoyaAccounting_NOT_ALLOWED();
698: revert NoyaAccounting_NOT_ALLOWED();
702: revert NoyaAccounting_NOT_ALLOWED();
706: revert NoyaAccounting_NOT_ALLOWED();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)

```solidity
File: contracts/accountingManager/Registry.sol

34: revert UnauthorizedAccess();
41: revert UnauthorizedAccess();
48: revert UnauthorizedAccess();
54: if (vaults[_vaultId].accountManager == address(0)) revert NotExist();
118: if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();
250: if (vault.trustedPositionsBP[positionId].isEnabled) revert AlreadyExists();
251: if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();
255: revert TokenNotTrusted(usingTokens[i]);
272: if (!vault.trustedPositionsBP[_positionId].isEnabled) revert NotExist();
276: revert CannotRemovePosition(vaultId, _positionId);
306: revert InvalidPosition(_positionId);
309: revert TooManyPositions();
343: if (!vault.connectors[msg.sender].enabled) revert UnauthorizedAccess();
344: if (!vault.trustedPositionsBP[_positionId].isEnabled) revert InvalidPosition(_positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)

```solidity
File: contracts/connectors/AaveConnector.sol

68: revert IConnector_UntrustedToken(_borrowAsset);
73: if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
104: if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol)

```solidity
File: contracts/connectors/BalancerFlashLoan.sol

71: revert Unauthorized(caller);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol)

```solidity
File: contracts/connectors/CompoundConnector.sol

31: if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
50: if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
52: if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)

```solidity
File: contracts/connectors/Dolomite.sol

66: revert IConnector_UntrustedToken(token);
85: revert IConnector_UntrustedToken(token);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/Dolomite.sol)

```solidity
File: contracts/connectors/FraxConnector.sol

92: revert IConnector_InvalidInput();
110: revert IConnector_LowHealthFactor(healthFactor);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/FraxConnector.sol)

```solidity
File: contracts/connectors/GearBoxV3.sol

70: if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol)

```solidity
File: contracts/connectors/MorphoBlueConnector.sol

84: revert IConnector_LowHealthFactor(getHealthFactor(id, morphoBlue.market(id)));
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol)

```solidity
File: contracts/connectors/PendleConnector.sol

192: revert InsufficientSyOut(netSyOut, minSY);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol)

```solidity
File: contracts/connectors/PrismaConnector.sol

38: revert IConnector_InvalidPosition(positionId);
80: revert IConnector_InvalidPosition(positionId);
108: revert IConnector_InvalidPosition(positionId);
119: revert IConnector_LowHealthFactor(healthFactor);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PrismaConnector.sol)

```solidity
File: contracts/connectors/SiloConnector.sol

66: revert IConnector_LowHealthFactor(0);
104: revert IConnector_LowHealthFactor(0);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SiloConnector.sol)

```solidity
File: contracts/connectors/UNIv3Connector.sol

66: revert IConnector_InvalidAmount();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol)

```solidity
File: contracts/governance/Keepers.sol

117: require(success, "Transaction execution reverted.");
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol)


```solidity
File: contracts/governance/NoyaGovernanceBase.sol

34: revert NoyaGovernance_Unauthorized(msg.sender);
45: if (msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);
56: revert NoyaGovernance_Unauthorized(msg.sender);
67: if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);
77: if (msg.sender != maintainer) revert NoyaGovernance_Unauthorized(msg.sender);
87: if (msg.sender != governer) revert NoyaGovernance_Unauthorized(msg.sender);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/NoyaGovernanceBase.sol)

```solidity
File: contracts/helpers/BaseConnector.sol

47: revert IConnector_LowHealthFactor(_minimumHealthFactor);
103: if (caller != address(this)) revert IConnector_InvalidAddress(caller);
175: revert IConnector_InvalidAddress(msg.sender);
184: revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperSender.sol

76: if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

72: revert IConnector_BridgeTransactionNotApproved(txn);
74: if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();
79: revert IConnector_InvalidDestinationChain();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

33: if (msg.sender != lzHelper) revert IConnector_InvalidSender();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol)

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30: if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();
98: if (_swapRequest.amount == 0) revert InvalidAmount();
100: if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();
135: if (!bridgeImplInfo.isBridge) revert RouteNotAllowedForThisAction();
166: revert RouteNotFound();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol


113: revert InvalidSelector();
118: if (from != _request.from) revert InvalidReceiver(from, _request.from);
119: if (receivingAmount < _request.minAmount) revert InvalidMinAmount();
120: if (sendingAssetId != _request.inputToken) revert InvalidInputToken();
121: if (receivingAssetId != _request.outputToken) revert InvalidOutputToken();
122: if (amount != _request.amount) revert InvalidAmount();
153: if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
154: if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId();
155: if (bridgeData.sendingAssetId != _request.inputToken) revert InvalidFromToken();
157: revert InvalidReceiver(bridgeData.receiver, _request.receiverAddress);
159: if (bridgeData.minAmount > _request.amount) revert InvalidMinAmount();
160: if (bridgeData.destinationChainId != _request.destChainId) revert InvalidToChainId();
179: revert FailedToForward(err);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)


```solidity
File: contracts/helpers/valueOracle/NoyaValueOracle.sol

25: if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
107: revert NoyaOracle_PriceOracleUnavailable(quotingToken, baseToken);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

42: if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
58: revert NoyaChainlinkOracle_INVALID_INPUT();
96: revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(asset, baseToken, primarySource);
126: revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
129: revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

25: if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
39: if (_period == 0) revert INoyaValueOracle_InvalidInput();
66: if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)
</details>


## [G-02] Use nested if and avoid multiple check combinations 
Using nested is cheaper than using && multiple check combinations. There are more advantages, such as easier to read code and better coverage reports.

example:

```solidity
File: contracts/accountingManager/AccountingManager.sol:

185      function _update(address from, address to, uint256 amount) internal override {
186:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {
187              revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
```

**Recomendation Code:**
```diff
File: contracts/accountingManager/AccountingManager.sol:

  185      function _update(address from, address to, uint256 amount) internal override {
- 186:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {
+ 186:         if (!(from == address(0))){
+ 187:             if(balanceOf(from) < amount + withdrawRequestsByAddress[from]){
  188                  revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
+ 189:             }
+ 190:         }
        
```

<details>
<summary><i> 19 issue instances in 10 files:</i></summary>


```solidity
File: contracts/accountingManager/AccountingManager.sol

186: if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {
288: if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
335: if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {
374: if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol) 

```solidity
File: contracts/accountingManager/Registry.sol

40: if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
47: if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
347: if (positionIndex == 0 && removePosition) return type(uint256).max;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol) 

```solidity
File: contracts/connectors/MorphoBlueConnector.sol

66: if (p.collateral == 0 && p.supplyShares == 0) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol) 

```solidity
File: contracts/connectors/PendleConnector.sol

223: if (closePosition && isMarketEmpty(market)) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol) 

```solidity
File: contracts/connectors/PrismaConnector.sol

111: if (bAmount > 0 && !isBorrowing) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PrismaConnector.sol) 

```solidity
File: contracts/connectors/SiloConnector.sol

60: if (closePosition && isSiloEmpty(silo)) {
120: if (depositAmount == 0 && borrowAmount == 0) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SiloConnector.sol) 

```solidity
File: contracts/governance/Keepers.sol

45: if (addOrRemove[i] && !isOwner[_owners[i]]) {
48: } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol) 

```solidity
File: contracts/governance/NoyaGovernanceBase.sol

55: if (msg.sender != emergencyManager && msg.sender != watcherContract) {
67: if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/NoyaGovernanceBase.sol) 

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30: if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();
102: if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol) 

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

82: if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol) 

</details>

## [G-03] Declare `immutable` as `private` to save gas 

Using `private` instead of `public` for immutables saves gas.

The compiler doesn't need to create non-payable getter functions for deployment calldata, store the bytes of the value outside of where it's used, or add another entry to the method ID table, saving 3406-3606 gas in deployment.

<details>
<summary><i>3 issue instances in 2 files:</i></summary>


```solidity
File: contracts/connectors/MorphoBlueConnector.sol

13: IMorpho public immutable morphoBlue;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol#L13)

```solidity
File: contracts/connectors/UNIv3Connector.sol
16: INonfungiblePositionManager public immutable positionManager;
17: IUniswapV3Factory public immutable factory;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol#L16-L17)

</details>


## [G-04] Use assembly to write address storage values 
example:

```solidity
File: contracts/accountingManager/AccountingManager.sol:

102:       withdrawFeeReceiver = p._withdrawFeeReceiver;
```

**Recomendation Code:**
```diff
File: contracts/accountingManager/AccountingManager.sol:

-102:       withdrawFeeReceiver = p._withdrawFeeReceiver;
+102:       assembly {
+103:           sstore(withdrawFeeReceiver.slot, p._withdrawFeeReceiver);
+104:       }     
```

<details>
<summary><i> 16 issue instances in 7 files:</i></summary>



```solidity
File: contracts/accountingManager/AccountingManager.sol

102: withdrawFeeReceiver = p._withdrawFeeReceiver;
103: performanceFeeReceiver = p._performanceFeeReceiver;
104: managementFeeReceiver = p._managementFeeReceiver;
143: withdrawFeeReceiver = _withdrawFeeReceiver;
144: performanceFeeReceiver = _performanceFeeReceiver;
145: managementFeeReceiver = _managementFeeReceiver;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)

```solidity
File: contracts/accountingManager/NoyaFeeReceiver.sol

18: accountingManager = _accountingManager;
19: baseToken = _baseToken;
20: receiver = _receiver;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol)

```solidity
File: contracts/accountingManager/Registry.sol

76: flashLoan = _flashLoan;
86: flashLoan = _flashLoan;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)

```solidity
File: contracts/connectors/BalancerConnector.sol

48: AURA = aura;
49: BAL = bal;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol)

```solidity
File: contracts/connectors/CurveConnector.sol

57: CVX = cvx;
58: CRV = crv;
59: PRISMA = prisma;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol)

```solidity
File: contracts/connectors/LidoConnector.sol

27: lido = _lido;
28: lidoWithdrawal = _lidoW;
29: steth = _steth;
30: weth = w;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

29: lifi = _lifi;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

32: factory = _factory;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)


</details>



## [G-05] Use `unchecked` for Non-Loop Increment/Decrement Operations 

*Disclaimer: `You should be sure that underflow is not possible `
Using `unchecked` increments can save gas by bypassing the built-in overflow checks.
This can save 30-40 gas per iteration.
It is recommended to use unchecked increments when overflow is not possible.

<details>
<summary><i>3 issue instances in 3 files:</i></summary>


```solidity
File: contracts/governance/Keepers.sol

113: nonce++;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L113)

```solidity
File: contracts/governance/Keepers.sol

50: numOwnersTemp--;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L50)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

83: timeWeightedAverageTick--;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L83)
</details>

## [G-06] Using Storage Instead of Memory for structs/arrays Saves Gas 
### Note 
I reported issue that was overlooked by the bot.

When fetching data from a storage location, assigning the data to a memory variable causes all fields of the struct / array to be read from storage. This incurs a Gcoldsload (2100 gas) for each field of the struct / array. If the fields are read from the new memory variable, they incur an additional MLOAD, which is more expensive than a simple stack read.

Instead of declaring the variable with the memory keyword, a more cost-effective approach is to declare the variable with the storage keyword. In this case, you can cache any fields that need to be re-read in stack variables. This approach significantly reduces gas costs, as you only incur the Gcoldsload for the fields actually read.

The only scenario where it makes sense to read the whole struct / array into a memory variable is if the full struct / array is being returned by the function or passed to a function that requires memory. Additionally, if the array / struct is being read from another memory array / struct, using a memory variable may be appropriate.

By carefully considering the storage and memory usage in your contract, you can optimize gas costs and improve the efficiency of your smart contract operations.

<details>
<summary><i> 44 issue instances in 17 files:</i></summary>


```solidity
File: contracts/accountingManager/AccountingManager.sol

412: WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
633: PositionBP memory p = registry.getPositionBP(vaultId, position.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)

```solidity
File: contracts/accountingManager/Registry.sol

441: PositionBP memory position = vaults[vaultId].trustedPositionsBP[_positionId];
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L441)

```solidity
File: contracts/connectors/AerodromeConnector.sol

126: PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AerodromeConnector.sol#L126)

```solidity
File: contracts/connectors/BalancerConnector.sol

100: (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);
110: (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);
117: (PoolInfo memory _poolInfo, bytes32 positionId) = _getPoolInfo(p.poolId);
163: PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
164: PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
191: PositionBP memory p = registry.getPositionBP(vaultId, positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol)

```solidity
File: contracts/connectors/CompoundConnector.sol

96: IComet.UserBasic memory userBasic = comet.userBasic(address(this));
109: IComet.AssetInfo memory info = comet.getAssetInfo(i);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)


```solidity
File: contracts/connectors/CompoundConnector.sol

69: PoolInfo memory poolInfo = _getPoolInfo(pool);
82: PoolInfo memory poolInfo = _getPoolInfo(pool);
104: PoolInfo memory poolInfo = _getPoolInfo(pool);
123: PositionBP memory p = registry.getPositionBP(vaultId, positionId);
124: PoolInfo memory poolInfo = abi.decode(p.additionalData, (PoolInfo));
260: PositionBP memory p = registry.getPositionBP(vaultId, positionId);
266: PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)

```solidity
File: contracts/connectors/GearBoxV3.sol

95: PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
97: CollateralDebtData memory d = ICreditManagerV3(facade.creditManager()).calcDebtAndCollateral(
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol)

```solidity
File: contracts/connectors/MaverickConnector.sol

154: PositionBP memory position = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol#L154)

```solidity
File: contracts/connectors/MorphoBlueConnector.sol

36: MarketParams memory params = morphoBlue.idToMarketParams(id);
59: MarketParams memory params = morphoBlue.idToMarketParams(id);
65: Position memory p = morphoBlue.position(id, address(this));
81: MarketParams memory market = morphoBlue.idToMarketParams(id);
96: MarketParams memory params = morphoBlue.idToMarketParams(id);
109: MarketParams memory market = morphoBlue.idToMarketParams(_id);
110: Position memory p = morphoBlue.position(_id, address(this));
119: PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
122: MarketParams memory params = morphoBlue.idToMarketParams(id);
124: Position memory pos = morphoBlue.position(id, address(this));
143: MarketParams memory params = morphoBlue.idToMarketParams(id);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol)

```solidity
File: contracts/connectors/PendleConnector.sol

258: PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol#L258)

```solidity
File: contracts/connectors/PrismaConnector.sol

58: PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
78: PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
146: PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PrismaConnector.sol)

```solidity
File: contracts/connectors/SiloConnector.sol

110: PositionBP memory bp = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SiloConnector.sol#L110)

```solidity
File: contracts/connectors/StargateConnector.sol

111: PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/StargateConnector.sol#L111)

```solidity
File: contracts/connectors/UNIv3Connector.sol

128: PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol#L128)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

34: PositionBP memory bp = registry.getPositionBP(vaultId, position.positionId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L34)

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

99: RouteData memory swapImplInfo = routes[_swapRequest.routeId];
133: RouteData memory bridgeImplInfo = routes[_bridgeRequest.routeId];
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

151: ILiFi.BridgeData memory bridgeData = ILiFi(lifi).extractBridgeData(_request.data);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L151)


## [G-07] Setting the constructor to payable
You can cut out 10 opcodes in the creation-time EVM bytecode if you declare a constructor payable. Making the constructor payable eliminates the need for an initial check of msg.value == 0 and saves 13 gas on deployment with no security risks.

Furthermore, Solidity's division operation also includes a division-by-0 prevention which is bypassed using shifting.


<details>
<summary><i>39 issue instances in 39 files:</i></summary>

```solidity
File: contracts/accountingManager/AccountingManager.sol:

94: constructor(AccountingManagerConstructorParams memory p)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)

```solidity
File: contracts/accountingManager/NoyaFeeReceiver.sol:

14: constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol)

```solidity
File: contracts/accountingManager/Registry.sol:

66: constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)

```solidity
File: contracts/connectors/AaveConnector.sol:

33: constructor(address _pool, address _poolBaseToken, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol)

```solidity
File: contracts/connectors/AerodromeConnector.sol:

40: constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AerodromeConnector.sol)

```solidity
File: contracts/connectors/BalancerConnector.sol:

42: constructor(address _balancerVault, address bal, address aura, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol)

```solidity
File: contracts/connectors/BalancerFlashLoan.sol:

24: constructor(address _balancerVault, PositionRegistry _registry) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol)

```solidity
File: contracts/connectors/CamelotConnector.sol:

36: constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CamelotConnector.sol)

```solidity
File: contracts/connectors/CompoundConnector.sol:

17: constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)

```solidity
File: contracts/connectors/CurveConnector.sol:

45: constructor(
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol)

```solidity
File: contracts/connectors/Dolomite.sol:

18: constructor(
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/Dolomite.sol)

```solidity
File: contracts/connectors/FraxConnector.sol:

29: constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/FraxConnector.sol)

```solidity
File: contracts/connectors/GearBoxV3.sol:

17: constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol)

```solidity
File: contracts/connectors/LidoConnector.sol:

20: constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol)

```solidity
File: contracts/connectors/MaverickConnector.sol:

43: constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol)

```solidity
File: contracts/connectors/MorphoBlueConnector.sol:

23: constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol)

```solidity
File: contracts/connectors/PancakeswapConnector.sol:

19: constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PancakeswapConnector.sol)

```solidity
File: contracts/connectors/PendleConnector.sol:

57: constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol)

```solidity
File: contracts/connectors/PrismaConnector.sol:

25: constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PrismaConnector.sol)

```solidity
File: contracts/connectors/SiloConnector.sol:

17: constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SiloConnector.sol)

```solidity
File: contracts/connectors/SNXConnector.sol:

20: constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol)

```solidity
File: contracts/connectors/StargateConnector.sol:

33: constructor(address lpStacking, address _stargateRouter, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/StargateConnector.sol)

```solidity
File: contracts/connectors/UNIv3Connector.sol:

27: constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol)

```solidity
File: contracts/governance/Keepers.sol:

27: constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol)

```solidity
File: contracts/governance/NoyaGovernanceBase.sol:

21: constructor(PositionRegistry _registry, uint256 _vaultId) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/NoyaGovernanceBase.sol)

```solidity
File: contracts/governance/TimeLock.sol:

7: constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/TimeLock.sol)

```solidity
File: contracts/governance/Watchers.sol:

7: constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Watchers.sol)

```solidity
File: contracts/helpers/BaseConnector.sol:

33: constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol)

```solidity
File: contracts/helpers/ConnectorMock2.sol:

22: constructor(address _registry, uint256 _vaultId) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/ConnectorMock2.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperReceiver.sol:

31: constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperSender.sol:

29: constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol:

33: constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol:

19: constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol:

11: constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol)

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol:

34: constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol:

27: constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)

```solidity
File: contracts/helpers/valueOracle/NoyaValueOracle.sol:

29: constructor(PositionRegistry _registry) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol:

46: constructor(address _reg) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol:

31: constructor(address _factory, PositionRegistry _registry) {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)

</details>


## [G-08] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead 
> When using elements that are smaller than 32 bytes, your contract’s gas usage may be higher. This is because the EVM operates on 32 bytes at a time. Therefore, if the element is smaller than that, the EVM must use more operations in order to reduce the size of the element from 32 bytes to the desired size.

https://docs.soliditylang.org/en/v0.8.11/internals/layout_in_storage.html

Use a larger size then downcast where needed


<details>
<summary><i>60 issue instances in 14 files:</i></summary>


```solidity
File: contracts/accountingManager/AccountingManager.sol

228: uint64 i = 0;
264: uint64 i = 0;
330: uint64 i = 0;
400: uint64 i = 0;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)

```solidity
File: contracts/connectors/CompoundConnector.sol

97: uint16 assetsIn = userBasic.assetsIn;
101: uint256 principalInBase = uint256(uint104(userBasic.principal));
104: uint8 numberOfAssets = comet.numAssets();
107: for (uint8 i; i < numberOfAssets; ++i) {

141: function isInAsset(uint16 assetsIn, uint8 assetOffset) public pure returns (bool) {
142: return (assetsIn & (uint16(1) << assetOffset) != 0);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)

```solidity
File: contracts/connectors/CurveConnector.sol

169: ICurveSwap(poolInfo.pool).remove_liquidity_one_coin(amount, int128(uint128(withdrawIndex)), minAmount);
302: int128 tokenIndex = int128(uint128(index));
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol)

```solidity
File: contracts/connectors/MaverickConnector.sol

139: uint8 tokenIndex;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol)

```solidity
File: contracts/connectors/SNXConnector.sol

30: function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
46: function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
69: uint128 _accountId;
76: uint128 poolId = SNXCoreProxy.getPreferredPool();
83: uint128 _accountId;
90: _accountId, uint128(poolIds[poolIndex]), collateralType, newCollateralAmountD18, leverage
94: function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
104: uint128 _accountId,
105: uint128 poolId,
122: (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address));
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol)

```solidity
File: contracts/connectors/StargateConnector.sol

84: uint16(withdrawRequest.poolId), withdrawRequest.routerAmount, address(this)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/StargateConnector.sol)

```solidity
File: contracts/connectors/UNIv3Connector.sol

64: (uint128 currentLiquidity, address token0, address token1) = getCurrentLiquidity(p.tokenId);
116: function getCurrentLiquidity(uint256 tokenId) public view returns (uint128, address, address) {
117: (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);
123: CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max);
133: (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));
138: (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);
140: (uint160 sqrtPriceX96,,,,,,) = pool.slot0();
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol)

```solidity
File: contracts/governance/Keepers.sol

15: uint8 public threshold;
20: event UpdateThreshold(uint8 threshold);
27: constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
63: function setThreshold(uint8 _threshold) public onlyOwner {
91: uint8[] memory sigV,
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol)

```solidity
File: contracts/governance/Watchers.sol

7: constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Watchers.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperReceiver.sol

19: mapping(uint32 => ChainInfo) public chainInfo; // chainId => ChainInfo
24: uint32 constant TVL_UPDATE = 1;
40: function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperSender.sol

10: uint32 lzChainId;
51: function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
78: uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

19: uint32 public period = 1800;
21: event NewPeriod(uint32 period);
38: function setPeriod(uint32 _period) external onlyMaintainer {
48: function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {
61: uint128 amountIn128 = uint128(amount);
69: uint32[] memory secondsAgos = new uint32[](2);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

8: returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/WETH_Oracle.sol)

</details>


## [G-09] Use `assembly` for efficient event emission 

To efficiently emit events, consider utilizing assembly by making use of scratch space and the free memory pointer. This approach can potentially avoid the costs associated with memory expansion.

However, it's crucial to cache and restore the free memory pointer for safe optimization. Good examples of such practices can be found in well-optimized Solady's codebases. Please review your code and consider the potential gas savings of this approach.


<details>
<summary><i>139 issue instances in 27 files:</i></summary>


```solidity
File: contracts/accountingManager/AccountingManager.sol

127: emit ValueOracleUpdated(address(_valueOracle));
146: emit FeeRecepientsChanged(_withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver);
154: emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
180: emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee);
216: emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);
242: emit CalculateDeposit(
274: emit ExecuteDeposit(
314: emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);
349: emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);
364: emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);
387: emit WithdrawGroupFulfilled(
429: emit ExecuteWithdraw(
455: emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw);
462: emit ResetMiddle(newMiddle, withdrawQueue.middle, depositOrWithdraw);
485: emit RecordProfit(
496: emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
520: emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares);
538: emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);
562: emit RetrieveTokensForWithdraw(
670: emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount);
675: emit SetDepositWaitingTime(_depositWaitingTime);
680: emit SetWithdrawWaitingTime(_withdrawWaitingTime);
690: emit Rescue(msg.sender, token, amount);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)


```solidity
File: contracts/accountingManager/Registry.sol

85: emit updateFlashloanAddress(_flashLoan, flashLoan);
142: emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens);
143: emit VaultAddressesChanged(
178: emit VaultAddressesChanged(
196: emit ConnectorAdded(vaultId, _connectorAddresses[i]);
217: emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted);
262: emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data);
279: emit TrustedPositionRemoved(vaultId, _positionId);
302: emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index);
361: emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)

```solidity
File: contracts/connectors/AaveConnector.sol
53: emit Supply(supplyToken, amount);
75: emit Borrow(_borrowAsset, _amount);
85: emit Repay(asset, amount, i);
90: emit RepayWithCollateral(_borrowAsset, _amount, i);
111: emit WithdrawCollateral(_collateral, _collateralAmount);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol)

```solidity
File: contracts/connectors/AerodromeConnector.sol
72: emit Supply(data.pool, data.amount0, data.amount1);
97: emit Withdraw(data.pool, data.amountLiquidity);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AerodromeConnector.sol)

```solidity
File: contracts/connectors/BalancerConnector.sol
106: emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount);
159: emit DecreasePosition(p);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol)

```solidity
File: contracts/connectors/BalancerFlashLoan.sol
42: emit MakeFlashLoan(tokens, amounts);
60: emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol)

```solidity
File: contracts/connectors/CompoundConnector.sol
37: emit Supply(market, asset, amount);
59: emit WithdrawOrBorrow(_market, asset, amount);
67: emit ClaimRewards(rewardContract, market);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)

```solidity
File: contracts/connectors/CurveConnector.sol
149: emit OpenCurvePosition(pool, depositIndex, amount, minAmount);
174: emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount);
184: emit WithdrawFromConvexBooster(pid, amount);
194: emit WithdrawFromConvexRewardPool(pool, amount);
204: emit WithdrawFromGauge(pool, amount);
214: emit WithdrawFromPrisma(depostiToken, amount);
226: emit HarvestRewards(gauges);
240: emit HarvestPrismaRewards(pools);
254: emit HarvestConvexRewards(rewardsPools);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol)

```solidity
File: contracts/connectors/FraxConnector.sol
60: emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount);
79: emit Withdraw(address(pool), withdrawAmount);
97: emit Repay(address(pool), sharesToRepay);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/FraxConnector.sol)

```solidity
File: contracts/connectors/GearBoxV3.sol
33: emit OpenAccount(facade, ref);
51: emit CloseAccount(facade, creditAccount);
85: emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol)

```solidity
File: contracts/connectors/LidoConnector.sol
44: emit Deposit(amountIn);
62: emit RequestWithdrawals(amount);
86: emit ClaimWithdrawal(requestId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol)

```solidity
File: contracts/connectors/MaverickConnector.sol
71: emit Stake(amount, duration, doDelegation);
83: emit Unstake(lockupId);
107: emit AddLiquidityInMaverickPool(p);
130: emit RemoveLiquidityFromMaverickPool(p);
146: emit ClaimBoostedPositionRewards(rewardContract);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol)

```solidity
File: contracts/connectors/MorphoBlueConnector.sol
49: emit Supply(amount, id, sOrC);
72: emit Withdraw(amount, id, sOrC);
87: emit Borrow(amount, id);
100: emit Repay(amount, id);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol)

```solidity
File: contracts/connectors/PancakeswapConnector.sol
33: emit SendPositionToMasterChef(tokenId);
43: emit UpdatePosition(tokenId);
53: emit Withdraw(tokenId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PancakeswapConnector.sol)

```solidity
File: contracts/connectors/PendleConnector.sol
89: emit Supply(market, syMinted);
101: emit MintPTAndYT(market, syAmount);
118: emit DepositIntoMarket(address(market), SYamount, PTamount);
129: emit DepositIntoPenpie(_market, _amount);
139: emit WithdrawFromPenpie(_market, _amount);
156: emit SwapYTForPT(market, exactYTIn, min, guess);
173: emit SwapYTForSY(market, exactYTIn, min, orderData);
195: emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY);
207: emit BurnLP(address(market), amount);
232: emit DecreasePosition(address(market), _amount, closePosition);
247: emit ClaimRewards(address(market));
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol)

```solidity
File: contracts/connectors/PrismaConnector.sol
66: emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);
85: emit AddColl(address(zapContract), tm, amountIn);
121: emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);
135: emit CloseTrove(address(zapContract), troveManager);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PrismaConnector.sol)


```solidity
File: contracts/connectors/SiloConnector.sol

41: emit Deposit(siloToken, dToken, amount, oC);
68: emit Withdraw(siloToken, wToken, amount, oC, closePosition);
89: emit Borrow(siloToken, bToken, amount);
106: emit Repay(siloToken, rToken, amount);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SiloConnector.sol)

```solidity
File: contracts/connectors/StargateConnector.sol

69: emit DepositIntoStargatePool(depositRequest);
96: emit WithdrawFromStargatePool(withdrawRequest);
106: emit ClaimStargateRewards(poolId);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/StargateConnector.sol)

```solidity
File: contracts/connectors/UNIv3Connector.sol

56: emit OpenPosition(p, tokenId);
80: emit DecreasePosition(p);
95: emit IncreasePosition(p);
107: emit CollectFees(tokenIds[i]);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol)

```solidity
File: contracts/governance/Keepers.sol

55: emit UpdateOwners(_owners, addOrRemove);
66: emit UpdateThreshold(_threshold);
115: emit Execute(destination, data, gasLimit, executor, deadline);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

49: emit UpdateChainInfo(chainId, destinationAddress);
60: emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp);
70: emit StartBridgeTransaction(bridgeRequest, txn);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

47: emit AddedHandler(_handler, state);
57: emit AddedChain(_chainId, state);
67: emit AddedBridgeBlacklist(bridgeName, state);
99: emit Swapped(balanceOut0, balanceOut1, _request.outputToken);
141: emit Bridged(_request.from, _request.inputToken, _request.amount, _request.data);
182: emit Forwarded(lifi, address(token), amount, data);
200: emit Rescued(token, userAddress, amount);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

50: emit SetValueOracle(_valueOracle);
59: emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);
73: emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance);
82: emit AddEligibleUser(_user);
117: emit ExecutionCompleted(
139: emit BridgeExecutionCompleted(_bridgeRequest);
150: emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);
160: emit RouteUpdate(_routeId, false);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

61: emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
76: emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

41: emit NewPeriod(_period);
52: emit PoolsForAsset(tokenIn, baseToken, pool);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/NoyaValueOracle.sol

44: emit UpdatedDefaultPriceSource(baseCurrencies, oracles);
58: emit UpdatedAssetPriceSource(asset, baseToken, oracle);
63: emit UpdatedPriceRoute(asset, base, s);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol)

```solidity
File: contracts/helpers/BaseConnector.sol

50: emit MinimumHealthFactorUpdated(_minimumHealthFactor);
60: emit SwapHandlerUpdated(_swapHandler);
69: emit ValueOracleUpdated(_valueOracle);
88: emit TransferTokensToTrustedAddress(token, amount, caller, data);
128: emit TransferPositionToConnector(tokens, amounts, connector, data);
143: emit UpdateTokenInRegistry(token, remove);
192: emit AddLiquidity(tokens, amounts, data);
217: emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol)

</details>


## [G-10] Optimize names to save gas
Contracts most called functions could simply save gas by function ordering via ```Method ID```. Calling a function at runtime will be cheaper if the function is positioned earlier in the order (has a relatively lower Method ID) because ```22 gas``` are added to the cost of a function for every position that came before it. The caller can save on gas if you prioritize most called functions. 

**Recommendation:** 
Find a lower ```method ID``` name for the most called functions for example Call() vs. Call1() is cheaper by ```22 gas```

**Proof of Consept:**
https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92

<summary><i>issue instances in all files:</i></summary>

## [G-11] Reduce deployment costs by tweaking contracts' metadata 

The Solidity compiler appends 53 bytes of metadata to the smart contract code which translates to an extra 10,600 gas (200 per bytecode) + the calldata cost (16 gas per non-zero bytes, 4 gas per zero-byte).
This translates to up to 848 additional gas in calldata cost.
One way to reduce this cost is by optimizing the IPFS hash that gets appended to the smart contract code.

Why is this important?
- The metadata adds an extra 53 bytes, resulting in an additional 10,600 gas cost for deployment.
- It also incurs up to 848 additional gas in calldata cost.

Options to Reduce Gas:
1. Use the `--no-cbor-metadata` compiler option to exclude metadata, but this might affect contract verification.
2. Mine for code comments that lead to an IPFS hash with more zeros, reducing calldata costs.

<details>
<summary><i>41 issue instances in 41 files:</i></summary>


```solidity
File: contracts/accountingManager/AccountingManager.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol)

```solidity
File: contracts/accountingManager/NoyaFeeReceiver.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol)

```solidity
File: contracts/accountingManager/Registry.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)

```solidity
File: contracts/connectors/AaveConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol)

```solidity
File: contracts/connectors/AerodromeConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AerodromeConnector.sol)

```solidity
File: contracts/connectors/BalancerConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol)

```solidity
File: contracts/connectors/BalancerFlashLoan.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol)

```solidity
File: contracts/connectors/CamelotConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CamelotConnector.sol)

```solidity
File: contracts/connectors/CompoundConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CompoundConnector.sol)

```solidity
File: contracts/connectors/CurveConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol)


```solidity
File: contracts/connectors/Dolomite.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/Dolomite.sol)

```solidity
File: contracts/connectors/FraxConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/FraxConnector.sol)

```solidity
File: contracts/connectors/GearBoxV3.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol)

```solidity
File: contracts/connectors/LidoConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol)

```solidity
File: contracts/connectors/MaverickConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol)

```solidity
File: contracts/connectors/MorphoBlueConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol)

```solidity
File: contracts/connectors/PancakeswapConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PancakeswapConnector.sol)

```solidity
File: contracts/connectors/PendleConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol)

```solidity
File: contracts/connectors/PrismaConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PrismaConnector.sol)

```solidity
File: contracts/connectors/SNXConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol)

```solidity
File: contracts/connectors/SiloConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SiloConnector.sol)

```solidity
File: contracts/connectors/StargateConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/StargateConnector.sol)

```solidity
File: contracts/connectors/UNIv3Connector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol)

```solidity
File: contracts/governance/Keepers.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol)

```solidity
File: contracts/governance/NoyaGovernanceBase.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/NoyaGovernanceBase.sol)

```solidity
File: contracts/governance/TimeLock.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/TimeLock.sol)

```solidity
File: contracts/governance/Watchers.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Watchers.sol)

```solidity
File: contracts/helpers/BaseConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol)

```solidity
File: contracts/helpers/ConnectorMock2.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/ConnectorMock2.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperReceiver.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperSender.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol)


```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol)

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)

```solidity
File: contracts/helpers/TVLHelper.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/TVLHelper.sol)

```solidity
File: contracts/helpers/valueOracle/NoyaValueOracle.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

1: Consider optimizing the IPFS hash during deployment.
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/WETH_Oracle.sol)

</details>


## [G-12] Functions guaranteed to revert when called by normal users can be marked payable
If a function modifier or require such as onlyOwner/onlyX is used, the function will revert if a normal user tries to pay the function. Marking the function as payable will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are CALLVALUE(2), DUP1(3), ISZERO(3), PUSH2(3), JUMPI(10), PUSH1(3), DUP1(3), REVERT(0), JUMPDEST(1), POP(2) which costs an average of about 21 gas per call to the function, in addition to the extra deployment cost. 

The recommended mitigation steps is that functions guaranteed to revert when called by normal users can be marked payable.

<details>
<summary><i> 13 issue instances in 5 files:</i></summary>

```solidity
File: contracts/accountingManager/NoyaFeeReceiver.sol:

23: function withdrawShares(uint256 amount) external onlyOwner {
27: function burnShares(uint256 amount) external onlyOwner {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol)

```solidity
File: contracts/governance/Keepers.sol:

42: function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
63: function setThreshold(uint8 _threshold) public onlyOwner {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperReceiver.sol:

40: function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
52: function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperSender.sol:

36: function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
51: function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
63: function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol)

```solidity
File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol:

45: function addHandler(address _handler, bool state) external onlyOwner {
55: function addChain(uint256 _chainId, bool state) external onlyOwner {
65: function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {
193: function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {
```
[Link to code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)

</details>