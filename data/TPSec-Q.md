# **NOYA Low Risk and Non-Critical Issues**

- [**NOYA Low Risk and Non-Critical Issues**](#noya-low-risk-and-non-critical-issues)
  - [Low Risk Findings](#low-risk-findings)
    - [\[L-01\] Unhandled chainlink revert would lock all price oracle access](#l-01-unhandled-chainlink-revert-would-lock-all-price-oracle-access)
    - [\[L-02\] `addConnector` is missing input arrays length check, which can lead to disabled connectors](#l-02-addconnector-is-missing-input-arrays-length-check-which-can-lead-to-disabled-connectors)
    - [\[L-03\] On-chain slippage calculation in `SwapAndBridgeHandler::executeSwap` can be manipulated](#l-03-on-chain-slippage-calculation-in-swapandbridgehandlerexecuteswap-can-be-manipulated)
  - [**Informational / Non Critical Findings**](#informational--non-critical-findings)
    - [\[NC-01\] Use named imports](#nc-01-use-named-imports)
    - [\[NC-02\] Consistent usage of require vs custom errors](#nc-02-consistent-usage-of-require-vs-custom-errors)
    - [\[NC-03\] Unnecessary casting](#nc-03-unnecessary-casting)
    - [\[NC-04\] Unused declared variable](#nc-04-unused-declared-variable)
    - [\[NC-05\] CONSTANT\_CASE variable not declared as constant](#nc-05-constant_case-variable-not-declared-as-constant)
    - [\[NC-06\] Missing checks for address(0)](#nc-06-missing-checks-for-address0)

## Low Risk Findings

### [L-01] Unhandled chainlink revert would lock all price oracle access

`ChainlinkOracleConnector` uses Chainlink price feeds to get the asset price. However, when calling `latestRoundData`, it could potentially revert, making it impossible to query any prices.

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

        ...
    }
```

Chainlink’s multisigs can immediately block access to price feeds at will. Therefore, to prevent denial of service scenarios, it is recommended to query Chainlink price feeds using a defensive approach with Solidity’s try/catch structure. In this way, if the call to the price feed fails, the caller contract is still in control and can handle any errors safely and explicitly.

Refer to https://blog.openzeppelin.com/secure-smart-contract-guidelines-the-dangers-of-price-oracles/ for more information regarding potential risks to account for when relying on external price feed providers.

Recommended Mitigation Steps:

Surround the call to `latestRoundData()` with `try/catch` instead of calling it directly. In a scenario where the call reverts, the catch block can be used to call a fallback oracle or handle the error in any other suitable way.

### [L-02] `addConnector` is missing input arrays length check, which can lead to disabled connectors

[Registry::addConnector](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L188) takes in two input arrays that are assumed to have the same length, however this condition is not being checked for inside the body of the function.

```solidity
    function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
        external
        onlyVaultMaintainer(vaultId)
        vaultExists(vaultId)
    {
        Vault storage vault = vaults[vaultId];

        for (uint256 i = 0; i < _connectorAddresses.length; i++) {
            vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
            emit ConnectorAdded(vaultId, _connectorAddresses[i]);
        }
    }
```

Recommended Mitigation Steps:

Add an input array length check, that checks if the length of both input arrays is the same.

```diff
    function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
        external
        onlyVaultMaintainer(vaultId)
        vaultExists(vaultId)
    {
+				if (_connectorAddress.length != _enableds.length) {
+					  revert InputArraysLengthsNotEqual();
+				}

        ...
    }
```

### [L-03] On-chain slippage calculation in `SwapAndBridgeHandler::executeSwap` can be manipulated

[GenericSwapAndBridgeHandler.executeSwap](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90C1-L120C6) takes a `SwapRequest` struct as a parameter. This structure contains the `checkForSlippage` and `minAmount`, which determine whether the function will calculate the slippage on-chain or use a value provided by the user.

```solidity
struct SwapRequest {
    address from;
    uint256 routeId;
    uint256 amount;
    address inputToken;
    address outputToken;
    bytes data;
    bool checkForSlippage;
    uint256 minAmount;
}
```

```solidity
function executeSwap(SwapRequest memory _swapRequest)
    external
    payable
    onlyEligibleUser
    onlyExistingRoute(_swapRequest.routeId)
    nonReentrant
    returns (uint256 _amountOut)
{
    if (_swapRequest.amount == 0) revert InvalidAmount();
    RouteData memory swapImplInfo = routes[_swapRequest.routeId];
    if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();

    if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {
        // set minAmount so that slippage can be checked
        uint256 _slippageTolerance = slippageTolerance[_swapRequest.inputToken][_swapRequest.outputToken];
        if (_slippageTolerance == 0) {
            _slippageTolerance = genericSlippageTolerance;
        }
        INoyaValueOracle _priceOracle = INoyaValueOracle(valueOracle);
        uint256 _outputTokenValue =
            _priceOracle.getValue(_swapRequest.inputToken, _swapRequest.outputToken, _swapRequest.amount);

@>      _swapRequst.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);
    }

    _amountOut = ISwapAndBridgeImplementation(swapImplInfo.route).performSwapAction(msg.sender, _swapRequest);

    emit ExecutionCompleted(
        _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
    );
}

```

However, be aware that the `minAmount` parameter for on-chain slippage calculation can be easily manipulated.

Recommended Mitigation Steps:

Avoid calculating slippage amount on-chain.

## **Informational / Non Critical Findings**

### [NC-01] Use named imports

Use named imports to improve readability of the code and avoid polluting the global namespace.

- Instances
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L4-L13
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L4-L12
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L4-L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L4-L7
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/TimeLock.sol#L4
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Watchers.sol#L4
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L4
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L4-L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L8-L10
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L4-L9
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L4
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L4-L7
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L4-L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L4-L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L4-L7
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L9
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L4-L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L4-L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L4-L6
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L4-L8
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L5
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L4-L6

### [NC-02] Consistent usage of require vs custom errors

To improve code consistency, consider adopting a uniform approach, such as using only custom errors or require statements throughout the codebase.

### [NC-03] Unnecessary casting

There are several instances where variables are unnecessarily converted to addresses, even though they are already defined as such.

- Instances
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L156
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L102
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L58
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L65
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L96
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L99

### [NC-04] Unused declared variable

- Instances
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L331

### [NC-05] CONSTANT_CASE variable not declared as constant

- Instances
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L28
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L31

### [NC-06] Missing checks for address(0)

- Instances
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L66
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L106
  https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L158
