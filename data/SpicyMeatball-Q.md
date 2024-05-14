### Adding a pool with different fee tier will overwrite previous pool data

Currently, in the `UniswapValueOracle` contract, adding a pool for the same token pair but with a different fee tier will overwrite the previous pool data

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48
```solidity
    function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {
        address pool = IUniswapV3Factory(factory).getPool(tokenIn, baseToken, fee);
        require(pool != address(0), "pool doesn't exist");
>>      assetToBaseToPool[tokenIn][baseToken] = pool;
        emit PoolsForAsset(tokenIn, baseToken, pool);
    }
```

To address this issue, the fee tier can be added as a third parameter to the `assetToBaseToPool` mapping.

### `getValue` will revert if `baseToken` and `tokenIn` are the same tokens.

The `getValue` function in the `UniswapValueOracle` contract will revert if `baseToken` and `tokenIn` are the same tokens. This is due to the non-existence of a pool for such a token pair. 

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60
```solidity
    function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) {
        uint128 amountIn128 = uint128(amount);
>>      address pool = assetToBaseToPool[tokenIn][baseToken];
        if (pool == address(0)) {
            pool = assetToBaseToPool[baseToken][tokenIn];
        }
        if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
```

Return `amount` value, similar to how it is done in the Noya oracle contract.

```solidity
    function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
        if (asset == baseToken || amount == 0) {
            return amount;
        }
```

### Uncollected fees are not included in the TVL of Uniswap connector

The `_getPositionTVL` function of the Uniswap connector does not include fees that have been accrued by the position.

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol#L127-L150
```solidity
    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
        uint256 tokenId = abi.decode(p.data, (uint256));
        (address token0, address token1) = abi.decode(positionInfo.data, (address, address));
        uint256 amount0;
        uint256 amount1;
        (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));
        {
            IUniswapV3Pool pool = IUniswapV3Pool(factory.getPool(token0, token1, fee));
            bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));

>>          (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);

            (uint160 sqrtPriceX96,,,,,,) = pool.slot0();
            (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
                sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity
            );
            amount0 += tokensOwed0;
            amount1 += tokensOwed1;
        }

        tvl += valueOracle.getValue(token0, base, amount0);
        tvl += valueOracle.getValue(token1, base, amount1);
    }
```

As observed in the `_getPositionTVL` function of the Uniswap connector, only the liquidity and tokens that have been removed from the position are currently counted. However, there are also pending fees in the form of `feeGrowthGlobalX128` and `feeGrowthOutsideX128` that are not included in the TVL calculation. Since the TVL is used to calculate the vault's profit for performance fees and depositor's rewards, including uncollected fees will help to accurately reflect the actual profit of the vault.

### CAKE rewards are not included in the TVL of the Pancakeswap connector

The Pancakeswap connector allows LP tokens to be staked in the MasterChef contract to receive CAKE rewards. However, the `_getPositionTVL` function of the Pancakeswap connector does not include these rewards in the TVL calculation, making it incomplete. Updating the function to include the CAKE rewards will provide a more accurate TVL calculation for the Pancakeswap connector.
