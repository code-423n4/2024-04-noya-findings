## [L-01] Fee changes should only be applied to the next batch of transactions rather than the current

The current implementation of setting fee and fee deduction would allow the admin to enforce fee changes instantly in the current transaction batch e.g for transactions in the withdraw queue. Since these withdrawal transactions were initiated before the fee change, they should stick to the same fee deduction as it was before the new fee was set.

[AccountingManager.sol#L170-L181](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L170-L181)
[AccountingManager.sol#L422-L426](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L422-L426)

```solidity
function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer {
        if (
            _withdrawFee > WITHDRAWAL_MAX_FEE || _performanceFee > PERFORMANCE_MAX_FEE
                || _managementFee > MANAGEMENT_MAX_FEE
        ) {
            revert NoyaAccounting_INVALID_FEE();
        }
        /*
            @audit if the fees increase or decrease, it should only be applied to the next withdrawal batch and not a batch currently waiting to be executed
        */
        withdrawFee = _withdrawFee;
        performanceFee = _performanceFee;
        managementFee = _managementFee;
        emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee);
    }
```

Snippet from `executeWithdraw()`:

```solidity
 {
    uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION; // @audit new fee rates should be applied next batch
    withdrawFeeAmount += feeAmount;
    baseTokenAmount = baseTokenAmount - feeAmount;
}
```

## [L-02] Anyone can spam emit token transfers from accounting manager to the connector

`sendTokensToTrustedAddress()` allows a connected connector to call the function and take the deposit asset, e.g USDC then emit a transfer event for the action. Since the call only does the transfer if the msg.sender is an active connector within the NOYA system, it makes sense to not emit fake events as any user can still emit the fake transfer event regardless

[AccountingManager.sol#L150-L160](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L150-L160)

```solidity
function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
        external
        returns (uint256)
    {
        emit TransferTokensToTrustedAddress(token, amount, _caller, _data); // @audit spam events QA
        if (registry.isAnActiveConnector(vaultId, msg.sender)) {
            IERC20(token).safeTransfer(address(msg.sender), amount);
            return amount;
        }
        return 0;
    }
```

```diff
- emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
if (registry.isAnActiveConnector(vaultId, msg.sender)) {
+ emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
    IERC20(token).safeTransfer(address(msg.sender), amount);
    return amount;
}
```

## [L-03] Minting user shares to the zero address by mistake is not prevented

During execution of deposits, minting shares can be done to the zero address assuming the user copied it into the request data by error. Since, they cannot cancel withdrawals, they weigh their hopes on the protocol calling `resetMiddle()` which would nullify the current deposit batch

[AccountingManager.sol#L278](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L278)

```solidity
function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
        public
        onlyManager
        whenNotPaused
        nonReentrant
    {
        uint256 firstTemp = depositQueue.first;
        uint64 i = 0;
        uint256 processedBaseTokenAmount = 0;

        while (
            depositQueue.middle > firstTemp
                && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
        ) {
            i += 1;
            DepositRequest memory data = depositQueue.queue[firstTemp];

            emit ExecuteDeposit(
                firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
            );
            // minting shares for receiver address
            _mint(data.receiver, data.shares); // @audit no sanitation for receiver?

            processedBaseTokenAmount += data.amount;
            delete depositQueue.queue[firstTemp];
            firstTemp += 1;
        }
        ...
    }
```

```diff
+ require(data.receiver != address(0), "NoyaAccounting_INVALID_RECEIVER");
_mint(data.receiver, data.shares);
```

## [L-04] Liquidity will be removed irrespective of whether or not the Watcher verifies it

The Watcher's `verifyRemoveLiquidity` function is unfinished and will always assume that the liquidity removal call from the accounting manager call to a connector  is verified

[Watchers.sol#L8](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Watchers.sol#L8)
[BaseConnector.sol#L94](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol#L94)

```solidity
function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
        external
        returns (uint256)
    {
        emit TransferTokensToTrustedAddress(token, amount, caller, data);
        (address accountingManager,) = registry.getVaultAddresses(vaultId);
        if (msg.sender == accountingManager) {
            (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);

            (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
@>            Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData); // @audit verified irrespective

            IERC20(token).safeTransfer(address(accountingManager), newAmount);
            amount = newAmount;
        } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {
            IERC20(token).safeTransfer(address(msg.sender), amount);
        } else {
            uint256 routeId = abi.decode(data, (uint256));
            swapHandler.verifyRoute(routeId, msg.sender);
            if (caller != address(this)) revert IConnector_InvalidAddress(caller);
            IERC20(token).safeTransfer(msg.sender, amount);
        }
        _updateTokenInRegistry(token);
        return amount;
    }
```

```solidity
contract Watchers is Keepers {
    constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }

    // @audit unfinished function
    function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
}
```

## [L-05] No zero address checks in the constructor function of UniswapValueOracle

[UniswapValueOracle.sol#L31-L34](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L34)

```solidity
constructor(address _factory, PositionRegistry _registry) {
        factory = _factory;
        registry = _registry;
    }
```

```diff
+   require(_factory != address(0));
+   require(_registry != address(0));
    factory = _factory;
    registry = _registry;
```

## [L-06] `transferPositionToAnotherConnector`, `updateAssetPriceSource` & `updateDefaultPriceSource` lack array lengths match checks

[BaseConnector.sol#L122-L132](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol#L122-L132)
[NoyaValueOracle.sol#L51-L59](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L59)
[NoyaValueOracle.sol#L37-L45](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L45)

```solidity
function transferPositionToAnotherConnector(
        address[] memory tokens,
        uint256[] memory amounts,
        bytes memory data,
        address connector
    ) external onlyManager nonReentrant {
        emit TransferPositionToConnector(tokens, amounts, connector, data);
        // @audit QA unchecked array lengths of tokens == amounts
        if (registry.isAnActiveConnector(vaultId, connector)) {
            IConnector(connector).addLiquidity(tokens, amounts, data);
        }
    }

function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
        public
        onlyMaintainer
    {
        // @audit QA check for array length mismatch to avoid entering zero address oracle sources
        for (uint256 i = 0; i < baseCurrencies.length; i++) {
            defaultPriceSource[baseCurrencies[i]] = oracles[i];
        }
        emit UpdatedDefaultPriceSource(baseCurrencies, oracles);
    }
```

```diff
emit TransferPositionToConnector(tokens, amounts, connector, data);
+   require(tokens.length == amounts.length); 
    if (registry.isAnActiveConnector(vaultId, connector)) {
        IConnector(connector).addLiquidity(tokens, amounts, data);
}
```

```diff
+ require(baseCurrencies.length == oracles.length);
for (uint256 i = 0; i < baseCurrencies.length; i++) {
    defaultPriceSource[baseCurrencies[i]] = oracles[i];
}
```

```diff
+ require(asset.length == baseToken.length);
+ require(baseToken.length == oracle.length);
 for (uint256 i = 0; i < oracle.length; i++) {
    priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
}
```

## [L-07] No zero address checks in the `setAssetSources` function of ChainlinkOracleConnector

[ChainlinkOracleConnector.sol#L70-L78](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L78)

```solidity
function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
        external
        onlyMaintainer
    {
        for (uint256 i = 0; i < assets.length; i++) {
            assetsSources[assets[i]][baseTokens[i]] = sources[i];
            emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);
        }
    }
```

## [L-08] Chainlink price retrievals on Arbitrum lack the sequencer downtime check

Asset value query on Arbitrum One lack checks for ensuring the sequencer is not down before making the call for the price data which is then utilized. In the function below for example, the call to one of Chainlink' price feed happens irrespective of the sequencer status

[ChainlinkOracleConnector.sol#L115-L135](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L115-L135)

```solidity
function getValueFromChainlinkFeed(
        AggregatorV3Interface source,
        uint256 amountIn,
        uint256 sourceTokenUnit,
        bool isInverse
    ) public view returns (uint256) {
        int256 price;
        uint256 updatedAt;
        (, price,, updatedAt,) = source.latestRoundData();
        uint256 uintprice = uint256(price);
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
        }
        if (price <= 0) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
        if (isInverse) {
            return (amountIn * sourceTokenUnit) / uintprice;
        }
        return (amountIn * uintprice) / (sourceTokenUnit);
    }
```

## [NC-01] `getUnderlyingTokens` should be external

The function is not being used anywhere in the Accounting Manager contract and can be marked external

[AccountingManager.sol#L649-L656](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L649-L656)

```diff
- function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
+ function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) external view returns (address[] memory) {
    if (positionTypeId == 0) {
        address[] memory tokens = new address[](1);
        tokens[0] = abi.decode(data, (address));
        return tokens;
    }
    return new address[](0);
}
```

## [NC-02] NoyaFeeReceiver `baseToken` should be removed as it is never used

The `baseToken` address variable of the NoyaFeeReceiver is not being used for anything within the contract and can be removed

[NoyaFeeReceiver.sol#L10](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol#L10)

```diff
- address public baseToken;

event ManagementFeeReceived(address indexed token, uint256 amount);

- constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
+ constructor(address _accountingManager, address _receiver) Ownable(msg.sender) {
    require(_accountingManager != address(0));
-   require(_baseToken != address(0));
    require(_receiver != address(0));
    accountingManager = _accountingManager;
-   baseToken = _baseToken;
    receiver = _receiver;
}
```

## [NC-03] NoyaFeeReceiver `ManagementFeeReceived` should be removed as it is never used

The `ManagementFeeReceived` event is supposed to be emitted whenever the fee receiver receives fee shares but since the event is not being used in the contract, it can be removed

[NoyaFeeReceiver.sol#L12](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol#L12)

```diff
- event ManagementFeeReceived(address indexed token, uint256 amount);
```

## [NC-04] NoyaFeeReceiver `receiver` should be immutable as it is never changed

[NoyaFeeReceiver.sol#L8](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/NoyaFeeReceiver.sol#L8)

```diff
- address public receiver;
+ address public immutable receiver;
```

## [NC-05] `getPositionTVL` should be external

The function is not being used anywhere in the Accounting Manager contract and can be marked external

[AccountingManager.sol#L632-L640](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L632-L640)

```diff
- function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {
+ function getPositionTVL(HoldingPI memory position, address base) external view returns (uint256) {
        PositionBP memory p = registry.getPositionBP(vaultId, position.positionId);
        if (p.positionTypeId == 0) {
            address token = abi.decode(p.data, (address));
            uint256 amount = IERC20(token).balanceOf(abi.decode(position.data, (address)));
            return _getValue(token, base, amount);
        }
        return 0;
    }
```