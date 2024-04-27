# Gas Optimizations

## Table of Contents

## [G-01] Use `assembly` for efficient event emission (**saves ~380 Gas**)

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



## [G-02] Reduce deployment costs by tweaking contracts' metadata (**saves ~100 Gas**)

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

