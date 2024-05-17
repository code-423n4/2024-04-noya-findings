# QA Report

## Low Risk

| Count | Title |
| --- | --- |
| [L-01] | Token in registry is updated before `GearBoxV3` interaction |
| [L-02] | Missing health factor check in `PrismaConnector::openTrove` |
| [L-03] | `SwapAndBridgeHandler` can only add eligible user but never remove it |

| Total Low Risk Issues | 3 |
| --- | --- |

## Non-Critical

| Count | Title |
| --- | --- |
| [NC-01] | Lack of error message in `AccountingManager` |
| [NC-02] | Extract important constant for `positionTypeId` |
| [NC-03] | Unused event in `NoyaFeeReceiver` |
| [NC-04] | `NoyaFeeReceiver`'s baseToken field is unused |
| [NC-05] | File names should be the same as the contracts holding them |
| [NC-06] | Extract a function for building holdingPositionId |
| [NC-07] | Parameter name in repay function is not descriptive |
| [NC-08] | Variable should be constant |
| [NC-09] | Confusing if check in `Balancer::receiveFlashLoan` |
| [NC-10] | Multiple SLOADs can be avoided |
| [NC-11] | Inconsistent formatting |
| [NC-12] | Inconsistent naming of parameters inside some functions of `PrismaConnector` |
| [NC-13] | Lack of error message in `Keepers` |
| [NC-14] | `BaseConnector` should change how some values are declared |
| [NC-15] | Rename recommendation for `_addLiquidity` |
| [NC-16] | Misleading function name in `TVLHelper` |
| [NC-17] | Naming convention for omnichain contracts can be improved |
| [NC-18] | Redundant public function in `BaseConnector` |
| [NC-19] | Function parameter is confusing |
| [NC-20] | Incorrect natspec formatting in `NoyaValueOracle` |
| [NC-21] | Incorrect natspec in `ChainlinkOracleConnector` |
| [NC-22] | Misleading function name in `ChainlinkOracleConnector` |
| [NC-23] | Natspecs for `ConnectorData` and `Vault` are incorrect |
| [NC-24] | Reduntant call to `vm.stopPrank()` |
| [NC-25] | Hardcoded bytes in tests make them hard to understand |
| [NC-26] | Typo in test name |
| [NC-27] | Test files and test contracts don't follow the standard Solidity naming conventions |
| [NC-28] | isCloseTo function can be replaced |
| [NC-29] | `Watchers::verifyRemoveLiquidity()` in not implemented |
| [NC-30] | Additional flag in `PendleConnector::decreasePosition` could lead to having to redeposit in order to close position |

| Total Non-Critical Issues | 30 |
| --- | --- |


## [L-01] Token in registry is updated before GearBoxV3 interaction
All the connectors update token holdings **after** the 3rd party interaction is over. This is due to the fact that updates have to be recorded with the current state and not the state before interacting.

In `GearBoxV3::executeCommands` this pattern is not followed and tokens in registry are updated **before** interacting. This means that a token holding will always exist for `GearBoxV3`, even if all funds are withdrawn. Having empty connections affects gas consumption and could make off-chain accounting harder.

### **Recommendation**: 
Create another loop after `multicall` and place the token updates there.
```diff
    function executeCommands(
        address facade,
        address creditAccount,
        MultiCall[] calldata calls,
        address approvalToken,
        uint256 amount
         for (uint256 i = 0; i < calls.length; i++) {
             if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
-            bytes4 method = bytes4(calls[i].callData[:4]);
-
-            if (method == ICreditFacadeV3Multicall.enableToken.selector) {
-                (address token) = abi.decode(calls[i].callData[4:], (address));
-                _updateTokenInRegistry(token);
-            }
         }
         if (approvalToken != address(0)) {
            _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount);
        }
        ICreditFacadeV3(facade).multicall(creditAccount, calls);
        if (approvalToken != address(0)) {
            _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());
        }
+        for (uint256 i = 0; i < calls.length; i++) {
+            bytes4 method = bytes4(calls[i].callData[:4]);
+            if (method == ICreditFacadeV3Multicall.enableToken.selector) {
+                (address token) = abi.decode(calls[i].callData[4:], (address));
+                _updateTokenInRegistry(token);
+            }
+        }
         emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);
     }
```

## [L-02] Missing health factor check in PrismaConnector::openTrove
The `PrismaConnector` and trove have two separate CRs (health factor) each. The connector requires that a high CR is kept so that trove is far from the danger of being liquidated. This is why the `PrismaConnector::minimumHealthFactor` is higher than the trove's CR for liquidation.

It makes sense to check the CR when calling `adjustTrove`, but it should also be checked when creating a trove via `openTrove`. The reason being is that a trove with health factor `1.4` can be created, which is below `PrismaConnector::minimumHealthFactor`. That's still above Prisma's liquidation threshold, but does not cover the protocols general minimum of `1.5`. So techincally it's allowed to create a trove which does not have NOYA's desired safety margin.

As a result, this poses a risk of price downturns liquidating a trove and causing protocol loss.

### **Recommendation**: 
```diff
function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
        public
        onlyManager
        nonReentrant
    {
        bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
        PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
        address collateral = abi.decode(positionInfo.additionalData, (address));
        address debTtoken = ITroveManager(tm).debtToken();
        _approveOperations(collateral, address(zap), dAmount);
        zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));
+        uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));
+        if (minimumHealthFactor > healthFactor) {
+            revert IConnector_LowHealthFactor(healthFactor);
+        }
        registry.updateHoldingPosition(vaultId, positionId, "", "", false);
        _updateTokenInRegistry(collateral);
        _updateTokenInRegistry(debTtoken);
        emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);
    }
```

## [L-03] SwapAndBridgeHandler can only add eligible user but never remove it
The `SwapAndBridgeHandler::addEligibleUser` function controls which connector is able to execute swaps. The issue is that there is no function that can reverse this action. Thus, once a connector is eligible for swapping it can never be stopped. This can be a security issue in two situations:
- There is a bug in a connector and it's access can't be revoked
- A connector migration is done but the old connector still has access

### **Recommendation**:
To mitigate these vectors, we suggest that you create a `removeEligibleUser` function that revokes access:
```javascript
function removeEligibleUser(address _user) external onlyMaintainerOrEmergency {
    isEligibleToUse[_user] = false;
    emit RemoveEligibleUser(_user);
}
```

## [NC-01] Lack of error message in AccountingManager
It is good practice to have error messages when a require fails.

Examples: 

In `AccountingManager::startCurrentWithdrawGroup()`

```javascript
require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false); // <- no error messsage
```

In `AccountingManager::fulfillCurrentWithdrawGroup()`
```javascript
require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false); // <- no error messsage
```
### **Recommendation**:
```diff
-   require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false); 
+   require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false, "Withdraw group started"); 
```

```diff
-   require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
+   require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false, "Withdraw group NOT yet started");
```

## [NC-02] Extract important constant for positionTypeId
The `positionTypeId` field of `PositionBP` struct is an important one, as it distinguishes connector and `AccountManager` positions. When `positionTypeId` is `0`, only `AccountManager` knows how to calculate the value. For such an important literal, especially when it's used across multiple contracts - `BaseConnector::_updateTokenInRegistry` and `AccountManager::getPositionTVL` it is best practice to have a common way of setting it. Other connectors comply with this pattern, but not `AccountManager` and `BaseConnector`.
### **Recommendation:** 
Make a library which will hold this and other constants. 

## [NC-03] Unused event in NoyaFeeReceiver
`ManagementFeeReceived` event in `NoyaFeeReceiver` is unused and can be omitted.

## [NC-04] NoyaFeeReceiver's baseToken field is unused
The field `baseToken` in `NoyaFeeReceiver` can be omitted, as it's never used.

## [NC-05] File names should be the same as the contracts holding them
The contract `PositionRegistry` is located under `Registry.sol`. Same goes for `SwapAndBridgeHandler`, which is in the file `GenericSwapAndBridgeHandler.sol`. This is confusing for readers. It states in the [solidity docs](https://docs.soliditylang.org/en/latest/style-guide.html#contract-and-library-names):
> Contract and library names should also match their filenames.

## [NC-06] Extract a function for building holdingPositionId
It is best that the creation of `holdingPositionId` is extracted to a pure function as it is used in two places in `PositionRegistry`. This will help code reuse and readibility.

## [NC-07] Parameter name in repay function is not descriptive
`AaveConnector::repay()`'s third parameter is confusingly named `i`, which is usually used for looping. It should be named `rateMode`.

## [NC-08] Variable should be constant
`BalancerConnector::BALANCER_LP_POSITION` should be constant as it will never be changed.

## [NC-09] Confusing if check in Balancer::receiveFlashLoan
The `receiveFlashLoan` function contains the following check:
```javascript
if (!(caller == keeperContract)) {
    revert Unauthorized(caller);
}
```

which can be simplified to:
```javascript
if (caller != keeperContract) {
    revert Unauthorized(caller);
}
```

## [NC-10] Multiple SLOADs can be avoided
`Registry::updateHoldingPosition` can be made a bit more gas efficient if a holding position that is accessed from storage multiple times is first loaded into memory:
```javascript
vault.holdingPositions[positionIndex] = vault.holdingPositions[vault.holdingPositions.length - 1]; 
vault.isPositionUsed[keccak256(
    abi.encode(
        vault.holdingPositions[positionIndex].calculatorConnector,
        vault.holdingPositions[positionIndex].positionId,
        vault.holdingPositions[positionIndex].data
    )
)] = positionIndex;
```

Can be written as:
```javascript
HoldingPI memory holdingPosition = vault.holdingPositions[vault.holdingPositions.length - 1];
vault.isPositionUsed[keccak256(
    abi.encode(
        holdingPosition.calculatorConnector,
        holdingPosition.positionId,
        holdingPosition.data
    )
)] = positionIndex;
vault.holdingPositions[positionIndex] = holdingPosition;
```

The same holds true for `Registry::getGovernanceAddresses`.

## [NC-11] Inconsistent formatting
Above `PendleConnector::supply`'s natspec a header with many `*` symbols can be found. This is not a convention in solidity or anywhere else through out Noya's codebase. We recommend removing the redundant symbols.

## [NC-12] Inconsistent naming of parameters inside some functions of PrismaConnector
`PrismaConnector::openTrove` names the first parameter `zap`. <br>
Other functions in the same contract `addColl` & `adjustTrove` name the first parameter `zapContract`.

Naming convention should be consistent across functions.

## [NC-13] Lack of error message in Keepers
`Keeprs::updateOwners` has the following require statement which lacks error message: <br>
`require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);`

It is considered best practice to have error message when require fails.

## [NC-14] BaseConnector should change how some values are declared
`BaseConnector::MINIMUM_HEALTH_FACTOR` can be constant.

`BaseConnector::DUST_LEVEL` can be immutable in case of every connector having it's own qualification of dust amounts, or constant if dust amounts should be defined across all connectors. Also, consider that it should have a value higher than `1` to be effective. `300 wei` would be a good threshold.

## [NC-15] Rename recommendation for _addLiquidity
The way `BaseConnector::_addLiquidity` function is named looks like it will add liquidity, but it's role in fact is to be a hook called after adding liquidity. Thus, it would be sensible to rename it to `_afterLiquidityAdded`.

## [NC-16] Misleading function name in TVLHelper
The function `TVLHelper::getLatestUpdateTime` does not return the timestamp closest to now, but the oldest. This causes it's callsites to look confusing:
```
uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
```

The function should be renamed to `getOldestUpdateTime`

## [NC-17] Naming convention for omnichain contracts can be improved
Currently the sender of an omnichain message is called `OmnichainManagerNormalChain` and the receiver `OmnichainManagerBaseChain`. One can't distinguish which is which only by looking at the names of the contracts. Having `Normal` in the sender's name is also misleading, because it suggests there's normal and ab-normal chains when no such concept exists. 

Since the former contract can send messages and the latter can only receive it would be more intuitive to rename them as follows:
- `OmnichainManagerNormalChain` -> `OmnichainManagerSender`
- `OmnichainManagerBaseChain`   -> `OmnichainManagerReceiver`

## [NC-18] Redundant public function in BaseConnector
The following code is unnecessarily complicated:
```javascript
function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
    return _getPositionTVL(p, baseToken);
}

function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
    return 0;
}
```

You can make `getPositionTVL` virtual and drop `_getPositionTVL` - all behaviour will be the same. Also, having a public function with an underscore goes against Solidity naming conventions. Here is a [patch](https://gist.github.com/georgiIvanov/098eca8dcc68f8fb2e6e96c9603ff250) for the necessary changes.

## [NC-19] Function parameter is confusing
`NoyaValueOracle::updatePriceRoute` has last parameter called `s`. The name is not descriptive and should be renamed to something more descriptive, like `sources`.

## [NC-20] Incorrect natspec formatting in NoyaValueOracle
[Natspec in NoyaValueOracle](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L71) is not placed properly - there's not space above the natspec and unnecessary space below. Alignment should be fixed so that IDEs and other tools parse the information correctly.

## [NC-21] Incorrect natspec in ChainlinkOracleConnector
The natspec for `ChainlinkOracleConnector::updateChainlinkPriceAgeThreshold` says the lower bound for price threshold should be `1 day`, but in the code is actually `1 hour`. Natspec should be fixed.

## [NC-22] Misleading function name in ChainlinkOracleConnector
`ChainlinkOracleConnector::getTokenDecimals` and the natspec it has say that it returns decimals, but that is not accurate. It returns 10^decimals, which is different. From the `ERC20` standard, it is expected that when `decimals` is called it returns the decimals number - 6, 8, 18, etc. So by association it is expected when a function named `getTokenDecimals` is called to return number of decimals the token uses, not 10 to the power of decimals. 

### **Recommendation**: 
Rename `getTokenDecimals` to `getOneTokenUnit`, so it reflects what the function does. Update natspec as well.

## [NC-23] Natspecs for ConnectorData and Vault are incorrect
In `IPositionRegistry` the natspecs for `ConnectorData` and `Vault` have some inconsistencies that should be fixed. Lets look at the former:
```javascript
/**
 * @Title: ConnectorData
 * @dev This struct is used to store the information of a connector
 * @param connectorAddress The address of the connector
 * @param enabled A boolean indicating if the connector is enabled
 * @param isPositionUsed A mapping of positionIds that the connector is using
 * @param holdingPositions An array of HoldingPI that the connector is holding
 * @param trustedTokens A mapping of additional tokens that the connector is allowed to hold
 */
struct ConnectorData {
    bool enabled;
    mapping(address => bool) trustedTokens;
}
```
- `@param connectorAddress` does not exist as a field
- `@param isPositionUsed` is a mapping belonging to `Vault`, so it should be transferred there
- `@param holdingPositions` is again part of `Vault`

In `Vault`'s natspec:
- `@param vaultManager` - such field does not exist
- `@param trustedTokens` - such field does not exist in `Vault`, but it's part of `ConnectorData`
- `@param strategyManager` - such field does not exist
- some fields lack natspec: `emergency`, `holdingPositions`, `isPositionUsed`, `trustedPositionsBP`

## [NC-24] Reduntant call to vm.stopPrank()
Calling `vm.stopPrank();` at the end of a test does nothing. It just contrubites to code bloat and can be safely omitted.
Example: `BaseConnector.t.sol::testSwap`, `BalancerConnector.t.sol::testVaultDepositFlow`, `CompoundConnector.t.sol::testProcessFlow`, etc.

> Calling `stopPrank` at the end of `setUp` is ok.

## [NC-25] Hardcoded bytes in tests make them hard to understand 
There are a few places in the test suite where hardcoded `bytes memory data` is provided in the test. Some examples: `testLifi.sol::testSwapIntoEth`, `testSwapETH.sol::testSwapEth`, `testSwapHandler` < all tests in this file.

The issue is that it makes tests hard to understand and maintain. Readers don't know what data is provided for swaps. When adding new tests it's prohibiting the introduction of new values and supporting reuse of the same literal over and over.

### **Recommendation**: 
Create a factory function that constructs the data from it's input parameters. In this way it will be easier to understand current tests and write new ones.

## [NC-26] Typo in test name
`testRegistry::testPositinos` should be renamed to `testRegistry::testPositions`

## [NC-27] Test files and test contracts don't follow the standard Solidity naming conventions
`testStarter.sol` should be renamed to `TestStarter.sol` and the contract in it should be named `TestStarter`
The same goes for many other test files: `testOracle.sol`, `testRegistry.sol`, `testAccountingBranches.sol`, `testLifi`, etc.

Also, it is good for files that contain actual tests to have the `.t.sol` extension - this is not the case for many files, one example is `testOracle.sol`. An exception would be `TestStarter.sol` because it's a base class and doesn't contain any tests.

## [NC-28] isCloseTo function can be replaced
Using the `isCloseTo` function in tests requires writing asserts with nested function calls like this `assertTrue(isCloseTo(tvl, _amount, 100));`. Using this function can be dropped since Foundry actually provides an assert that does the same thing `assertApproxEqRel(a, b, percentDelta)`. Thus, asserts call sites will be simplified.

## [NC-29] `Watchers::verifyRemoveLiquidity()` in not implemented
The `Watchers` contract is part of NAYA's governance and it has only one function
```javascript
contract Watchers is Keepers {
    constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
    function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
}
```

It is used only in `BaseConnector::sendTokensToTrustedAddress()`
```javascript
    function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
        external
        returns (uint256)
    {
        emit TransferTokensToTrustedAddress(token, amount, caller, data);
        (address accountingManager,) = registry.getVaultAddresses(vaultId);
        if (msg.sender == accountingManager) {
            (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);

            (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
=>          Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData);

            IERC20(token).safeTransfer(address(accountingManager), newAmount);
            amount = newAmount;
            ...
```

Since it is not implemented, the severity of the issue can not be concluded as the impact is unknown.

## [NC-30] Additional flag in `PendleConnector::decreasePosition` could lead to having to redeposit in order to close position
`PendleConnector::decreasePosition` and `SiloConnector::withdraw` have an extra parameter passed to the functions responsible for lowering position stake called `closePosition`.
In the usual implementation of analogical function in other connectors the position is closed only on the condition that the connector no longer has tokens staked.

For example in `Silo::withdraw`
```javascript
    function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
        external
        onlyManager
        nonReentrant
    {
        ISilo silo = ISilo(siloRepository.getSilo(siloToken));
        silo.withdraw(wToken, amount, oC);
        _updateTokenInRegistry(wToken);
        if (closePosition && isSiloEmpty(silo)) { // <=
            registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true
            );
        }
...
```

The problem arises from the fact that if `silo.withdraw()` is called and all the tokens are withdrawn, but the `closePosition` flag is `false`, the position would be empty and still open in the registry. 
This would cause inconvenience since in order to close it a withdrawal has to be made. However since the connector has 0 tokens if it is tried to withdraw 0 the transaction would revert, since Silo has a check that reverts 0 value withdraws. 

This can be seen in the `BaseSilo` implementation here: https://github.com/silo-finance/silo-core-v1/blob/e5d16f201ab2139829d45ed881532c936249d3a5/contracts/BaseSilo.sol#L378

The situation is analogical for the `PendleConector`

This problem can easily be fixed by depositing minimal value and the calling `withdraw()` with `closePosition` set to `true` in order to close the position.

Since the issue only causes inconvenience it is marked as Informational 