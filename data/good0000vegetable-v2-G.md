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



## [G-03] Usage of `uints`/`ints` smaller than 32 bytes (256 bits) incurs overhead (**saves ~6 Gas**)
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


## [G-04] Declare `immutable` as `private` to save gas (**saves ~3000 Gas**)

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


## [G-05] Use `unchecked` for Non-Loop Increment/Decrement Operations (**saves ~30 Gas**)

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


## [G-06] Use `revert()` to gain maximum gas savings (**saves ~50 Gas**)

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
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/NoyaGovernanceBase.sol)

```solidity
File: contracts/helpers/BaseConnector.sol

47: revert IConnector_LowHealthFactor(_minimumHealthFactor);
103: if (caller != address(this)) revert IConnector_InvalidAddress(caller);
175: revert IConnector_InvalidAddress(msg.sender);
184: revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol)

```solidity
File: contracts/helpers/LZHelpers/LZHelperSender.sol

76: if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

72: revert IConnector_BridgeTransactionNotApproved(txn);
74: if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();
79: revert IConnector_InvalidDestinationChain();
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol)

```solidity
File: contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

33: if (msg.sender != lzHelper) revert IConnector_InvalidSender();
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol)

```solidity
File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

30: if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();
98: if (_swapRequest.amount == 0) revert InvalidAmount();
100: if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();
135: if (!bridgeImplInfo.isBridge) revert RouteNotAllowedForThisAction();
166: revert RouteNotFound();
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol)

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
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol)


```solidity
File: contracts/helpers/valueOracle/NoyaValueOracle.sol

25: if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
107: revert NoyaOracle_PriceOracleUnavailable(quotingToken, baseToken);
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

42: if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
58: revert NoyaChainlinkOracle_INVALID_INPUT();
96: revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(asset, baseToken, primarySource);
126: revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
129: revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol)

```solidity
File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

25: if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
39: if (_period == 0) revert INoyaValueOracle_InvalidInput();
66: if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
```
[Link to code] (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol)
</details>