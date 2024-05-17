## [L-1] Some connectors don't have `getUnderlyingTokens`
### Summary 
according to the natspec
```js
@>     * @dev each connector should implement this function to return the underlying tokens for the position type and data
     */
function
    function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
```
5 connectors don't implement this function to return the underlying tokens for the position type and data
The connectors are: `BalancerConnector`, `CurveConnector`, `DolomiteConnector`, `Gearboxv3` and `LidoConnector`


## [L-2] Wrong emission in some events
### Summary 
Some event parameters aren't implemented correctly. here is the list with the corrected parameters:
1. in the `AccountingManager::calculateDepositShares` :
`            emit CalculateDeposit(
                middleTemp, data.receiver, block.timestamp, data.amount, shares, data.amount / shares
            );`

2. in the `AccountingManager::executeDeposit` :
`            emit ExecuteDeposit(
                firstTemp, data.receiver, block.timestamp, data.amount, data.shares, data.amount / shares
            );`

3. in the `AccountingManager::checkIfTVLHasDroped` :
`            emit ResetFee(storedProfitForFee, currentProfit, block.timestamp);`



## [L-3] multiple emissions in the `AccountingManager::sendTokensToTrustedAddress`
### Summary 
this function can be called by anyone and anyone could spam the logs with incorrect and arbitrary parameters in the event
```js
    /// @notice sendTokensToTrustedAddress is used to transfer tokens from the accounting manager to other contracts
    function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
        external
        returns (uint256)
    {
        // @audit-low: this could be easily manipulated and emitable for infinite when `connector` is not active or not active
        emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
        if (registry.isAnActiveConnector(vaultId, msg.sender)) {
            IERC20(token).safeTransfer(address(msg.sender), amount);
            return amount;
        }
        return 0;
    }
```

### mitigation
include the emission inside the if statement


## [L-1] The withdraw function doesn't handle the 0 value as shares
### Summary 
anyone can call the withdraw function in the accounting manager contract with shares having 0 value. this will lead to infinite emission and increase the `withdraQueue.last` which leads to unexpected behavior and if when the manager calls the `executeWithdraw` and `calculateWithdrawShares`, this will create a lot of unnecessary and meaningless emission of events during the loops which all comes from unhandling the shares as 0 value

### mitigation
in the withdraw function let the function revert if `shares == 0`


## [L-1] No emission for collecting a fee in `UNIv3Connector::decreasePosition`
### Summary 
the `decreasePosition` function calls the _collectFees function but doesn't emit an event for it. as we can see in the `collectAllFees` function which will emit an event for collecting fee so the `decreasePosition` function should do it too

### mitigation 
add this line at the end of the `decreasePosition` function
```git
+      emit CollectFees(p.tokenId);
```


## [L-1] No equality check between owners and addOrRemove array leads to unexpected behavior
### Summary 
in the `Keepers::updateOwners` function there is no equality check between owners and addOrRemove array which might lead to unexpected behavior

### mitigation
add this at the first line of the function
```git
+ require(_owners.length == addOrRemove.length, "Arrays length mismatch");
```