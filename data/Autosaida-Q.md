## Table of Contents

| Issue ID                                                                   | Description                                                |
| -------------------------------------------------------------------------- | ---------------------------------------------------------- |
| [QA-01](#qa-01-Logic-Error-in-onlyVaultMaintainer-Modifier-in-PositionRegistry-Contract)        | Logic Error in onlyVaultMaintainer Modifier in PositionRegistry Contract      |
| [QA-02](#qa-02-insufficient-governance-functionality-in-watcher-contract) | Insufficient Governance Functionality in Watcher Contract |
| [QA-03](#qa-03-misleading-function-name-in-addBridgeBlacklist-function-in-lifiImplementation-contract)     | Misleading Function Name in addBridgeBlacklist Function in LifiImplementation Contract                   |
| [QA-04](#qa-04-inconsistent-implementation-and-comment-in-updateChainlinkPriceAgeThreshold-Function-in-chainlinkOracleConnector-contract)               | Inconsistent Implementation and Comment in updateChainlinkPriceAgeThreshold Function in ChainlinkOracleConnector contract        |


## QA-01 Logic Error in onlyVaultMaintainer Modifier in PositionRegistry Contract

### Description

The `PositionRegistry` contract has a logic error in the `onlyVaultMaintainer` modifier. The current logic requires the `maintainer` of all vaults to also possess the `EMERGENCY_ROLE` set during the registry's initialization. This issue is caused by the use of a logical OR (`||`) instead of a logical AND (`&&`) operator in the modifier, which incorrectly restricts access.

```solidity
modifier onlyVaultMaintainer(uint256 _vaultId) {
    if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {
        revert UnauthorizedAccess();
    }
    _;
}
```

The current logic restricts the functionality of the protocol by preventing the execution of functions protected by the `onlyVaultMaintainer` modifier, such as `addConnector` and `updateConnectorTrustedTokens`. This issue can lead to governance confusion and renders certain protocol functions unusable unless all vault maintainers also have the emergency role, which is not a practical or secure requirement.

### Recommended Mitigation Steps

Modify the `onlyVaultMaintainer` modifier to use a logical AND (`&&`) operator instead of a logical OR (`||`). This change ensures that either the vault maintainer or a user with the `EMERGENCY_ROLE` can access the protected functions, without requiring both roles to be held simultaneously.

``` solidity
modifier onlyVaultMaintainer(uint256 _vaultId) {
    if (msg.sender != vaults[_vaultId].maintainer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
        revert UnauthorizedAccess();
    }
    _;
}
```

## QA-02 Insufficient Governance Functionality in Watcher Contract

### Description

The `Watcher` contract fails to fulfill its intended governance role as specified in the documentation. According to the documentation, "The watcher is responsible to make sure the execution of Noya is going on correctly. If there is any misbehaving (like price manipulation or any suspicious actions from the keepers) the watchers should undo the action." However, the current implementation of the `Watcher` contract merely inherits from the `Keeper` contract without adding any additional functionality.

Furthermore, the `onlyEmergencyOrWatcher` modifier defined in the NoyaGovernanceBase contract is not utilized anywhere in the code, indicating that the watcher role is essentially meaningless in its current form. There is no capability for watchers to undo actions or monitor the system effectively, rendering the contract inadequate for its intended purpose.

### Recommended Mitigation Steps

1. **Redesign the `Watcher` contract**: Implement the necessary functions and logic to allow watchers to effectively monitor the system and undo any suspicious actions. This might include functions to revert transactions, halt operations, or flag suspicious activities.

2. **Utilize the `onlyEmergencyOrWatcher` modifier**: Ensure that this modifier is applied to relevant functions to grant watchers the necessary permissions to perform their governance duties.


## QA-03 Misleading Function Name in addBridgeBlacklist Function in LifiImplementation Contract

### Description

The `addBridgeBlacklist` function in the `LifiImplementation` contract has a naming confusion that can lead to misuse. 

```solidity
/**
    * @notice adding or removing a bridge name (string) to the list of supported bridges
    * @param bridgeName string chain id
    * @param state bool state of the bridge
    */
function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {
    isBridgeWhiteListed[bridgeName] = state;
    emit AddedBridgeBlacklist(bridgeName, state);
}
```

From the function implementation, the function is intended to add or remove a bridge name from the list of supported bridges based on the `state` parameter. If `state` is `true`, the bridge is added to the whitelist, making it valid. This logic is also applied in the `verifyBridgeData` function below.

```solidity
function verifyBridgeData(BridgeRequest calldata _request) public view override returns (bool) {
    ILiFi.BridgeData memory bridgeData = ILiFi(lifi).extractBridgeData(_request.data);

    if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
    ...
}
```

However, the function name suggests that it is adding the bridge to a blacklist, which implies that setting `state` to `true` would make the bridge invalid. This conflicts with the implemented logic, causing a semantic inconsistency and potential misuse.

### Recommended Mitigation Steps

Rename the `addBridgeBlacklist` function to `addBridgeWhitelist` to accurately reflect its functionality and avoid semantic confusion.

## QA-04 Inconsistent Implementation and Comment in updateChainlinkPriceAgeThreshold Function in ChainlinkOracleConnector contract

### Description

The `updateChainlinkPriceAgeThreshold` function in the `ChainlinkOracleConnector` contract has an inconsistency between its implementation and the accompanying comment. 

``` solidity
/*
* @notice Updates the threshold for the age of the price data
* @param _chainlinkPriceAgeThreshold The new threshold
* @dev The threshold should be between 1 day and 10 days
*/
function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {
    if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {
        revert NoyaChainlinkOracle_INVALID_INPUT();
    }
    chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold;
    emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
}
```

The comment states that the threshold for the age of the price data should be between 1 day and 10 days. However, the actual implementation checks if the threshold is between 1 hour and 10 days. This inconsistency can lead to confusion and potential misconfiguration of the threshold for the age of price data. 

rve that the function reverts despite the comment indicating the threshold should be between 1 day and 10 days.

### Recommended Mitigation Steps

Align the implementation with the comment by updating the threshold check to be between 1 day and 10 days as stated in the comment. 