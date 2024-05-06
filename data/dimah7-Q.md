## Findings Summary

| ID | Issue | Severity |
| - | - | - |
| [L-01] | Some events are triggered with incorrect logs | Low |
| [L-02] | Chainlink oracle connector might provide stale prices to protocol | Low |
| [L-03] | Deployments to L2 networks should check for active sequencer for Chainlink feeds | Low |
| [L-04] | Set a minimum TWAP interval to avoid price volatility | Low |
| [I-01] | Incorrect NatSpec and typo | Info |
| [I-02] | Missing essential check for length equality for array input parameters | Info |

## [L-01] Some events are triggered with incorrect logs

Events are vital for projects as they provide valuable information for protocols state, however some events which are triggered in protocol's deposit flow in `AccountingManager.sol` are emitted with the incorrect logs. This will cause confusion to developers or external systems when relying on event logs. For example As stated in the docs watchers and keepers actions rely on events.

```javascript
event CalculateDeposit(                                      !!!!!!!!!!!!!!  
    uint256 depositId, address receiver, uint256 recordTime, uint256 amount, uint256 shares, uint256 sharePrice
    );

emit CalculateDeposit(                          !!!!!!
    middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
    );

event ExecuteDeposit(                                        !!!!!!!!!!!!!!
    uint256 depositId, address receiver, uint256 recordTime, uint256 amount, uint256 shares, uint256 sharePrice
    );

emit ExecuteDeposit(                            !!!!!!!!!
    firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
    );
``` 

Additionally the custom error in `ChainlinkOracleConnector::getValueFromChainlinkFeed` is implemented with paramaters in incorrect order also

```javascript                                                                        !!!!!!!!!!!!!!
error NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address asset, address baseToken, address source);

if (price <= 0) {                                               !!!!!!!!!!!!!!
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
```

### Recommendation

Implement the parameters in the provided events in correct order.

## [L-02] Chainlink oracle connector might provide stale prices to protocol

In `ChainlinkOracleConnector.sol` contract there is a price age threshold variable which is used to check the price feeds staleness: 

```javascript
uint256 public chainlinkPriceAgeThreshold = 2 hours;

function getValueFromChainlinkFeed(
    ...
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
    ...
```

However although there is an option to change the threshold to different value: 

```javascript
function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {
        if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {
            revert NoyaChainlinkOracle_INVALID_INPUT();
        }
        chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold;
        emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
    }
```

It's not considered that there are price feeds that are with heartbeat of 24 hours. For example the most significant ETH/USD has 24 hour heartbeat on Arbitrum.
Refer here:
https://data.chain.link/feeds/arbitrum/mainnet/eth-usd

And since it's stated in the README that it will be deployed on L2's like Arbitrum also, in this case the function will revert.

### Recommendation

Consider using mapping where the addresses of all sources for price feeds will correspond to different price age threshold for different heartbeats.

## [L-03] Deployments to L2 networks should check for active sequencer for Chainlink feeds

As per protocol's README for the contest, it's stated that the project will be deployed on these chains: Ethereum,Arbitrum,Base,BSC,Optimism,Polygon,zkSync,Other,Avaxpolygon zkevm. As of right now when fetching data from the Chainlink oracle, the protocol doesn't consider whether the sequencer is down for deployments on L2 blockchains. It's important to ensure that the prices provided are not falsely perceived as fresh, even when the sequencer is down. This should be always considered when consuming data from Chainlink.

There is no check if the sequencer is down: 

```javascript
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

### Recommendation

Implement functionality to check the sequencer uptime with Chainlink oracles for deploying to L2s.

Reference here: https://docs.chain.link/data-feeds/l2-sequencer-feeds#example-code

## [L-04] Set a minimum TWAP interval to avoid price volatility

The formula for how TWAP oracle works for UniswapV3 is: 

$$tickCumulative(pool,time_{A},time_{B}) = \sum_{i=time_{A}}^{time_{B}} Price_{i}(pool)$$

$$TWAP(pool,time_{A},time_{B}) = \frac{tickCumulative(pool,time_{A},time_{B})}{time_{B} - time_{A}}$$

1. TickCumulative calculates the tick cumulative within a specified time range (from time_A to time_B) for a given Uniswap V3 pool. The tick cumulative is the sum of prices observed over this time period.
2. TWAP calculates the Time-Weighted Average Price (TWAP) for the specified time range (from time_A to time_B) using the tick cumulative. It divides the tick cumulative by the duration of the time range (time_B - time_A) to obtain the average price

So if $time_{B} - time_{A}$ is too low it would be relatively easy to manipulate TWAP output. For example a malicious actor might execute trades within a very short time frame to influence the price. And since $time_{B} - time_{A}$ is represented as: 

`UniswapValueOracle.sol`:

```javascript
// Period for the oracle
    uint32 public period = 1800;

function setPeriod(uint32 _period) external onlyMaintainer {
        if (_period == 0) revert INoyaValueOracle_InvalidInput();
        period = _period;
        emit NewPeriod(_period);
    }
```

### Recommendation:

Add a min period check to add another layer of security, taking in consideration that Ethereum block rate is ~12 seconds.

## [I-01] Incorrect NatSpec and typo 

Incorrect NatSpec for: 

```javascript
/// @notice depositWaitingTime is the time that the withdraw should wait for execution after calculation
    uint256 public withdrawWaitingTime = 6 hours;
```

Typo in: 

`AccountingManager.sol`:
```javascript
/// @notice preformanceFeeSharesWaitingForDistribution is the total amount of shares that are waiting for distribution of the performance fee
    /// @dev we use this variable to prevent the strategy manager to get the performance fee before the lock period is passed
    uint256 public preformanceFeeSharesWaitingForDistribution;
```

`CompoundConnector.sol`:
```javascript
/**
     * @notice Returns the collateral balance in base token for the given comet.
     */

    function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) {
```

## [I-02] Missing essential check for length equality for array input parameters

It's good practice to ensure that the length of the array parameters are equal, so it doesn't lead to false logic

```javascript
function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
        external
        onlyMaintainer
    {

function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
        public
        onlyMaintainer
    {

function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
        external
        onlyMaintainer
    {
```