
# QA Report : Noya Contest | 26th Apr 2024 - 17th May 2024

---

## Findings Description

| **ID**              | **Title**                                                                                                | **Severity**       |
| --------------- | ---------------------------------------------------------------------------------------------------- | -------------- |
| [L - 01](#l-01-setperiod-doesnt-validate-the-_period-value-to-a-minimum-value-of-900-seconds-15mins) |  `setPeriod()` doesn't validate the `_period` value to a minimum value of 900 seconds (15 mins)                              | _Low_          |
| [L - 02](#l-02-contract-must-check-whether-the-l2-sequencer-is-down-to-avoid-stale-pricing) | Contract must check whether the L2 sequencer is down to avoid stale pricing                | _Low_          |
| [L - 03](#l-03-wrong-order-of-arguments-passed-for-event-emission) | Wrong order of arguments passed for event emission                | _Low_          |
| [L - 04](#l-04-addvault-can-allow-maintainer-to-add-vault-with-emergency-as-addr0) |`addVault()` can allow maintainer to add Vault with `emergency` as addr(0)    | _Low_          |
| [L - 05](#l-05-no-input-sanitization-for-bytes-data-when-sending-it-via-an-external-call) | No input sanitization for `bytes data` when sending it via an external call           | _Low_          |
| [NC-01](#nc-01-no-event-is-emitted-here-but-it-should-be-as-being-intended-by-the-todo-statement) | No event is emitted here, but it should be, as being intended by the `TODO` statement                  | _Non Critical_ |
| [NC-02](#nc-02-assignment-should-be-done-after-the-require-check) | Assignment should be done after the `require` check                                                     | _Non Critical_ |

---
---
## [L-01] `setPeriod()` doesn't validate the `_period` value to a minimum value of 900 seconds (15mins) 
#### Description:
In the provided function `setPeriod()`, the `_period` is set by the maintainer, which checks only for non-zero values, disallowing 0 to be assigned to it. But a malicious maintainer can exploit the intended use of TWAP in the `UniswapValueOracle.sol` contract by setting it to least non-zero seconds possible, which allows the TWAP returned value to be heavily influenced by flashloans.

#### [Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L42)

#### Recommendation:
Validate the _period supplied to have a value of more than or equals to 900 (15 mins) which is chosen as an ideal value in various TWAP implementations. 
```diff
- if(_period == 0)
+ if(_period < 900 )
```
##
## [L-02] Contract must check whether the L2 sequencer is down to avoid stale pricing

#### Description: 
When using Chainlink with L2 chains like Arbitrum and others, the smart contracts must check whether the L2 Sequencer is down to avoid stale pricing data that appears fresh. 

#### [Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L115-L135) 

#### Recommendation: 
Chainlink’s official documentation provides an example implementation. Refer the below documentation, to implement ChainLinkOracle for all the other L2's where the deployment is intended.

[Link to Chainlink docs](https://docs.chain.link/data-feeds/l2-sequencer-feeds#example-code)

```solidity
/* Network: Optimism mainnet
     * Data Feed: BTC/USD
     * Data Feed address: 0xD702DD976Fb76Fffc2D3963D037dfDae5b04E593
     * Uptime Feed address: 0x371EAD81c9102C9BF4874A9075FFFf170F2Ee389
     * For a list of available Sequencer Uptime Feed proxy addresses, see:
     * https://docs.chain.link/docs/data-feeds/l2-sequencer-feeds
     */
    constructor() {
        dataFeed = AggregatorV2V3Interface(
            0xD702DD976Fb76Fffc2D3963D037dfDae5b04E593
        );
        sequencerUptimeFeed = AggregatorV2V3Interface(
            0x371EAD81c9102C9BF4874A9075FFFf170F2Ee389
        );
    }

    // Check the sequencer status and return the latest data
    function getChainlinkDataFeedLatestAnswer() public view returns (int) {
        (
            /*uint80 roundID*/,
            int256 answer,
            uint256 startedAt,
            /*uint256 updatedAt*/,
            /*uint80 answeredInRound*/
        ) = sequencerUptimeFeed.latestRoundData();

        // Answer == 0: Sequencer is up
        // Answer == 1: Sequencer is down
        bool isSequencerUp = answer == 0;
        if (!isSequencerUp) {
            revert SequencerDown();
        }

        // Make sure the grace period has passed after the
        // sequencer is back up.
        uint256 timeSinceUp = block.timestamp - startedAt;
        if (timeSinceUp <= GRACE_PERIOD_TIME) {
            revert GracePeriodNotOver();
        }

```

##
## [L-03] Wrong order of arguments passed for event emission 
#### Description: 
In AccountingManager.sol contract, for the function `calculateDepositShares()` we emit an event `CalculateDeposit` which is defined in the contract's interface as: 

```solidity
event CalculateDeposit(
        uint256 depositId, address receiver, uint256 recordTime, uint256 amount, uint256 shares, uint256 sharePrice
    );
```
But in this function we emit it as follows: 
```solidity
emit CalculateDeposit(
                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
            );
```
As you can notice that the `amount` which should `data.amount` and `shares` should be correspondingly be `shares` in emit, but the ordering here has been interchanges for amount and shares. 

#### Code Snippets:  
[Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L242)

#### Recommendation: 
Correct the ordering of both the arguments as mentioned above, using the below code:  
```solidity
emit CalculateDeposit(
                middleTemp, data.receiver, block.timestamp, data.amount, shares, shares * 1e18 / data.amount
            );
```

##
## [L-04] `addVault()` can allow maintainer to add Vault with `emergency` as addr(0) 
#### Description: 
In the `addVault()` while initializing state variables of vault struct, it has checks for all members of Vault except `emergency`and `maintainerWithoutTimelock`.

#### [Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L106-L134)

#### Recommendation: 
```solidity
require(_emergency != address(0));
require(_maintainerWithoutTimelock!= address(0));

vault.maintainerWithoutTimeLock = _maintainerWithoutTimelock;
vault.emergency = _emergency;
```
##

## [L-05] No input sanitization for `bytes data` when sending it via an external call

#### Description: 
The `execute()` in Keepers.sol contract executes a transaction if it has been approved by the required number of owners, it Validates the signatures against the transaction details. Though this function is dealt only by owners, but it is better to avoid sending the `data` without sanitizing or making any checks, as it can make internal call to extract funds/ harm the protocol. 


#### Code Snippets: 
[Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L116)

**Code**:
```solidity		

        (bool success,) = destination.call{ gas: gasLimit }(data);

```
##

***

##
## [NC-01] No event is emitted here, but it should be, as being intended by the `TODO` statement
#### Description: 
Developers have intended to send an event whenever the omniChain manager updates the TVL via `updateTVL()` function.


#### [Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L80) :
**Code:**
```solidity		
        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here

```

#### Recommendation: 
You might consider adding the event to ensure that any off-chain acknowledgement that requires to know the update of TVL is met accordingly.

```solidity
        event TVLUpdated(uint256 vaulId, address omnichainManager);
    //..//
        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
        emit TVLUpdated(vaultId, msg.sender);
```
##
## [NC-02] Assignment should be done after the `require` check 
#### Description: 
The constructor of OmnichainLogic.sol contract performs the check for 0 address `_lzHelper` after assigning the value to the state variable.
Though it may revert the assignment to the state variable when 0 address is passed as _lzHelper. 

#### [Code](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33-L38)

#### Recommendation:
Typically, when a transaction reverts due to a require statement or an explicit revert() call, any remaining gas after the point of failure is returned to the sender. The refunded gas includes the gas consumed up to the point of failure (excluding gas consumed by the require statement or revert() call itself) and any gas stipend remaining in the transaction.

```solidity
constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
        BaseConnector(baseConnectorParams)
    {
        require(_lzHelper != address(0));
        lzHelper = _lzHelper;
    }
```
Similarly, one more [instance](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L40-L41)

***
---