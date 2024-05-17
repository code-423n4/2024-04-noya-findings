### [L-1] Incorrect event emission in `GenericSwapAndBridgeHandler::setEnableRoute`
The function `setEnableRoute` is designed to update the status of a route by enabling or disabling it. However, the event emitted upon updating the route status incorrectly always sets the event parameter to `false`, regardless of the actual status.
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160
```
- emit RouteUpdate(_routeId, false);
+ emit RouteUpdate(_routeId, enable);
```
### [L-2] `_slippageTolerance` can be set 100% or greater than 100% in `setGeneralSlippageTolerance` and `setSlippageTolerance`
Make a constant MAX_SLIPPAGE_TOLERANCE and use require statement to check 
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L60
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L74
```
require(_slippageTolerance < MAX_SLIPPAGE_TOLERANCE)
```
### [L-3] Missing array length check
BaseConnector::transferPositionToAnotherConnector
BaseConnector::addLiquidity
BaseConnector::swapHoldings
ChainlinkOracleConnector::setAssetSources
NoyaValueOracle::updateAssetPriceSource
PositionRegistry::addConnector
### [L-4] Missing Pool Existence Check in `BalancerConnector::openPosition` and `UNIv3Connector::_getPositionTVL
We can add this line after getPool()
```
require(pool != address(0), "pool doesn't exist");
```

### [N-1] Function state mutability can be restricted to pure
AccountingManager::mint
AccountingManager::withdraw
AccountingManager::redeem
AccountingManager::deposit
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L693-L707
 ConnectorMock2::getPositionTVL
 ConnectorMock2::getUnderlyingTokens

### [N-2] Typo correction
- AccountingManager.sol change "fullfilled" to "fulfilled"
- AccountingManager.sol change "FeeRecepientsChanged" to "FeeRecipientsChanged"
  https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L146
  https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/Accounting/IAccountingManager.sol#L143
- AccountingManager.sol change "desposit" to "deposit" in netspec
  https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L224
-  AccountingManager.sol change "preformanceFeeSharesWaitingForDistribution" to "preformanceFeeSharesWaitingForDistribution"
- AccountingManager.sol change "totalCBAmountFullfilled" to "totalCBAmountFulfilled"
- AccountingManager.sol change "checkIfTVLHasDroped" to "checkIfTVLHasDropped"
  https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L490-L500
- Registry.sol change "updateHoldingPostionWithTime" to "updateHoldingPosition", in netspec spelling is right but for function spelling is wrong
  https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L370
  https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L368
  - LidoConnector.sol change "recieved" to "received"
    https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol#L39
- LidoConnector.sol change "refferal" to "referral"
    https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol#L40
  - CompoundConnector.sol change "getCollBlanace" to "getCollBalanace"
  - ChainlinkOracleConnector.sol change "claculate" to "calculate"
    https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L113C109-L113C118

### [N-3] `caller` should emit in MakeFlashLoan event
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol#L42
```
- emit MakeFlashLoan(tokens, amounts);
+ emit MakeFlashLoan(tokens, amounts, caller);
```
for logging the msg.sender value


### [N-4] Refactor for loop: Combining two loops into one
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/ConnectorMock2.sol#L40-L49
```solidity
    function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
        for (uint256 i = 0; i < tokens.length; i++) {
            // gather all of the tokens

            ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
        }
         for (uint256 i = 0; i < tokens.length; i++) {
            _updateTokenInRegistry(tokens[i]); // update the token in the registry
        }
    }

```
to 
```
function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
        for (uint256 i = 0; i < tokens.length; i++) {
            ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
            _updateTokenInRegistry(tokens[i]); // update the token in the registry
        }
    }

```
### [N-5] Sanity check for `amount`
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L150-L160 -> sendTokensToTrustedAddress()
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L202
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L683 -> rescue()
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L543-L545 -> burnShares()
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L519C9-L519C14
https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L519
```
+ require(amount != 0, "amount must be greater then zero")
```

### [N-6] Zero Address check
Accounting.sol
- deposit for `receiver`
- executeDeposit for `connector`
- withdraw for `receiver`