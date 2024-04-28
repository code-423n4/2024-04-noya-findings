## Medium Issues


*Total <b>7</b> instances over <b>4</b> issues:*

|ID|Issue|Instances|
|-|:-|:-:|
| [M-1](#M-1) | No way to retrieve ETH from the contract | 4 |
| [M-2](#M-2) | Usage of `slot0` is extremely easy to manipulate | 1 |
| [M-3](#M-3) | No check if L2 sequencer is down | 1 |
| [M-4](#M-4) | latestRoundData() has no check for round completeness | 1 |

## Low Issues


*Total <b>600</b> instances over <b>38</b> issues:*

|ID|Issue|Instances|
|-|:-|:-:|
| [L-1](#L-1) | Missing zero address check in functions with address parameters | 87 |
| [L-2](#L-2) | Array is `push()`ed but not `pop()`ed | 2 |
| [L-3](#L-3) | Consider implementing two-step procedure for updating protocol addresses | 8 |
| [L-4](#L-4) | Constructor / initialization function lacks parameter validation | 15 |
| [L-5](#L-5) | Empty `receive()`/`fallback()` function | 3 |
| [L-6](#L-6) | Code does not follow the best practice of check-effects-interaction | 12 |
| [L-7](#L-7) | External function calls within loops | 26 |
| [L-8](#L-8) | Function may return unassigned variable | 1 |
| [L-9](#L-9) | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 4 |
| [L-10](#L-10) | Governance functions should be controlled by time locks | 6 |
| [L-11](#L-11) | Loss of precision in divisions | 8 |
| [L-12](#L-12) | Missing checks for state variable assignments | 53 |
| [L-13](#L-13) | Missing limits when setting min/max amounts | 5 |
| [L-14](#L-14) | Missing zero address check in constructor | 10 |
| [L-15](#L-15) | Consider some checks for `address(0)` when setting address state variables | 29 |
| [L-16](#L-16) | Owner can renounce ownership | 3 |
| [L-17](#L-17) | `receive()`/`fallback()` function does not authorize requests | 3 |
| [L-18](#L-18) | Solidity version 0.8.20 or above may not work on other chains due to PUSH0 | 41 |
| [L-19](#L-19) | Some tokens may revert when large transfers are made | 20 |
| [L-20](#L-20) | Some tokens may revert when zero value transfers are made | 20 |
| [L-21](#L-21) | Sending tokens in a for loop | 2 |
| [L-22](#L-22) | Tokens may be minted to `address(0)` | 1 |
| [L-23](#L-23) | Unsafe downcast | 6 |
| [L-24](#L-24) | Use Ownable2Step instead of Ownable | 1 |
| [L-25](#L-25) | Consider using `ERC721A` instead of `ERC721` | 2 |
| [L-26](#L-26) | Using zero as a parameter | 10 |
| [L-27](#L-27) | `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()` | 2 |
| [L-28](#L-28) | Centralization Risk for trusted owners | 160 |
| [L-29](#L-29) | `decimals()` is not a part of the ERC-20 standard | 1 |
| [L-30](#L-30) | `onlyOwner` functions not accessible if owner renounces ownership | 6 |
| [L-31](#L-31) | Chainlink answer is not compared against min/max values | 1 |
| [L-32](#L-32) | Prefer skip over revert model in iteration | 3 |
| [L-33](#L-33) | External calls in modifiers should be avoided | 13 |
| [L-34](#L-34) | For loops in public or external functions should be avoided due to high gas costs and possible DOS | 22 |
| [L-35](#L-35) | Function with two (or more) array parameters missing a length check | 9 |
| [L-36](#L-36) | Library has public/external functions | 2 |
| [L-37](#L-37) | No limits when setting price values | 1 |
| [L-38](#L-38) | int/uint passed into abi.encodePacked without casting to a string | 2 |

## Medium Issues

<a name="M-1"></a> 
### [M-1] No way to retrieve ETH from the contract
The following contracts contain at least one `payable` function, yet the function does not utilise forwarded ETH, and the contract is missing functionality to withdraw ETH from the contract. This means that funds may become trapped in the contract indefinitely. Consider adding a withdraw/sweep function to contracts that are capable of receiving ether.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/connectors/LidoConnector.sol

/// @audit Contract can receive Ether but there is lack of functionality to claim the Ethers from the contract
7: contract LidoConnector is BaseConnector, ERC721Holder {

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

/// @audit Contract can receive Ether but there is lack of functionality to claim the Ethers from the contract
29: contract MaverickConnector is BaseConnector, IERC721Receiver {

```
*Github:* [[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L29)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

/// @audit Contract can receive Ether but there is lack of functionality to claim the Ethers from the contract
19: contract LZHelperSender is OAppSender {

```
*Github:* [[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L19)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit Contract can receive Ether but there is lack of functionality to claim the Ethers from the contract
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {

```
*Github:* [[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10)]



<a name="M-2"></a> 
### [M-2] Usage of `slot0` is extremely easy to manipulate

*There is one instance of this issue:*
```solidity
File: ./contracts/connectors/UNIv3Connector.sol

140:             (uint160 sqrtPriceX96,,,,,,) = pool.slot0();

```
*Github:* [[140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L140)]



<a name="M-3"></a> 
### [M-3] No check if L2 sequencer is down
Using Chainlink in L2 chains such as Arbitrum/Optimism/Base/Metis requires to check if the sequencer is down to avoid prices from looking like they are fresh although they are not.

*There is one instance of this issue:*
```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

123:         (, price,, updatedAt,) = source.latestRoundData();

```
*Github:* [[123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L123)]



<a name="M-4"></a> 
### [M-4] latestRoundData() has no check for round completeness
No check for round completeness could lead to stale prices and wrong price return value, or outdated price. The functions rely on accurate price feed might not work as expected, sometimes can lead to fund loss.

*There is one instance of this issue:*
```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

123:         (, price,, updatedAt,) = source.latestRoundData();

```
*Github:* [[123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L123)]




## Low Issues

<a name="L-1"></a> 
### [L-1] Missing zero address check in functions with address parameters
Adding a zero address check for each address type parameter can prevent errors.

<details>
<summary>
There are <b>87</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit missing zero check for `_caller`
150:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
             external
             returns (uint256)
         {

/// @audit missing zero check for `to`
185:     function _update(address from, address to, uint256 amount) internal override {

/// @audit missing zero check for `receiver`
/// @audit missing zero check for `referrer`
200:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {

/// @audit missing zero check for `receiver`
304:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {

/// @audit missing zero check for `base`
632:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {

/// @audit missing zero check for `token`
/// @audit missing zero check for `base`
642:     function _getValue(address token, address base, uint256 amount) internal view returns (uint256) {

/// @audit missing zero check for `receiver`
693:     function mint(uint256 shares, address receiver) public override returns (uint256) {

/// @audit missing zero check for `receiver`
/// @audit missing zero check for `owner`
697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

/// @audit missing zero check for `receiver`
/// @audit missing zero check for `shareOwner`
701:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {

/// @audit missing zero check for `receiver`
705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {

```
*Github:* [[150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L150), [185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L185), [200](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L200), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L304), [632](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L632), [642](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L642), [693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L693), [697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L697), [701](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L701), [705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L705)]


```solidity
File: ./contracts/accountingManager/Registry.sol

/// @audit missing zero check for `_flashLoan`
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

/// @audit missing zero check for `_maintainerWithoutTimelock`
/// @audit missing zero check for `_emergency`
106:     function addVault(
             uint256 vaultId,
             address _accountingManager,
             address _baseToken,
             address _governer,
             address _maintainer,
             address _maintainerWithoutTimelock,
             address _keeperContract,
             address _watcher,
             address _emergency,
             address[] calldata _trustedTokens
         ) external onlyRole(MAINTAINER_ROLE) {

/// @audit missing zero check for `_maintainerWithoutTimelock`
/// @audit missing zero check for `_emergency`
158:     function changeVaultAddresses(
             uint256 vaultId,
             address _governer,
             address _maintainer,
             address _maintainerWithoutTimelock,
             address _keeperContract,
             address _watcher,
             address _emergency
         ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

/// @audit missing zero check for `_connectorAddress`
207:     function updateConnectorTrustedTokens(
             uint256 vaultId,
             address _connectorAddress,
             address[] calldata _tokens,
             bool trusted
         ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {

/// @audit missing zero check for `_connector`
394:     function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
             public
             view
             returns (uint256)
         {

/// @audit missing zero check for `connector`
436:     function isPositionTrustedForConnector(uint256 vaultId, bytes32 _positionId, address connector)
             public
             view
             returns (bool)
         {

/// @audit missing zero check for `token`
/// @audit missing zero check for `connector`
470:     function isTokenTrusted(uint256 vaultId, address token, address connector) public view returns (bool) {

/// @audit missing zero check for `calculatorConnector`
486:     function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)
             public
             pure
             returns (bytes32)
         {

/// @audit missing zero check for `connectorAddress`
499:     function isAnActiveConnector(uint256 vaultId, address connectorAddress) public view returns (bool) {

/// @audit missing zero check for `addr`
525:     function isAddressTrusted(uint256 vaultId, address addr) public view returns (bool) {

```
*Github:* [[84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L84), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L106), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L158), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L207), [394](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L394), [436](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L436), [470](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L470), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L486), [499](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L499), [525](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L525)]


```solidity
File: ./contracts/connectors/AaveConnector.sol

/// @audit missing zero check for `_borrowAsset`
88:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager {

/// @audit missing zero check for `base`
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {

```
*Github:* [[88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L88), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L114)]


```solidity
File: ./contracts/connectors/AerodromeConnector.sol

/// @audit missing zero check for `base`
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

```
*Github:* [[125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L125)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

/// @audit missing zero check for `base`
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

```
*Github:* [[162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L162)]


```solidity
File: ./contracts/connectors/CamelotConnector.sol

/// @audit missing zero check for `base`
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L88)]


```solidity
File: ./contracts/connectors/CompoundConnector.sol

/// @audit missing zero check for `comet`
84:     function getBorrowBalanceInBase(IComet comet) public view returns (uint256 borrowBalanceInVirtualBase) {

/// @audit missing zero check for `comet`
95:     function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) {

/// @audit missing zero check for `base`
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

```
*Github:* [[84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L84), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L95), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L125)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

/// @audit missing zero check for `base`
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

/// @audit missing zero check for `curvePool`
297:     function estimateWithdrawAmount(ICurveSwap curvePool, uint256 amount, uint256 index)
             public
             view
             returns (uint256)
         {

```
*Github:* [[265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L265), [297](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L297)]


```solidity
File: ./contracts/connectors/Dolomite.sol

/// @audit missing zero check for `base`
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L106)]


```solidity
File: ./contracts/connectors/FraxConnector.sol

/// @audit missing zero check for `pool`
104:     function verifyHealthFactor(IFraxPair pool) public view {

/// @audit missing zero check for `_fraxlendPair`
120:     function _getHealthFactor(IFraxPair _fraxlendPair, uint256 _exchangeRate) internal view virtual returns (uint256) {

/// @audit missing zero check for `base`
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L104), [120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L120), [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L150)]


```solidity
File: ./contracts/connectors/GearBoxV3.sol

/// @audit missing zero check for `creditAccount`
62:     function executeCommands(
            address facade,
            address creditAccount,
            MultiCall[] calldata calls,
            address approvalToken,
            uint256 amount
        ) public onlyManager nonReentrant {

/// @audit missing zero check for `base`
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L62), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L93)]


```solidity
File: ./contracts/connectors/LidoConnector.sol

/// @audit missing zero check for `base`
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L91)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

/// @audit missing zero check for ``
/// @audit missing zero check for ``
149:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {

/// @audit missing zero check for `base`
153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L149), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L153)]


```solidity
File: ./contracts/connectors/MorphoBlueConnector.sol

/// @audit missing zero check for `base`
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

/// @audit missing zero check for `collateral`
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {

```
*Github:* [[118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L118), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L137)]


```solidity
File: ./contracts/connectors/PendleConnector.sol

/// @audit missing zero check for `_market`
126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

/// @audit missing zero check for `_market`
137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

/// @audit missing zero check for `base`
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

/// @audit missing zero check for `market`
293:     function getYTValue(address market, uint256 balance) public view returns (uint256) {

```
*Github:* [[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L126), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L137), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L257), [293](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L293)]


```solidity
File: ./contracts/connectors/PrismaConnector.sol

/// @audit missing zero check for `tm`
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {

/// @audit missing zero check for `tm`
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {

/// @audit missing zero check for `troveManager`
129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {

/// @audit missing zero check for `base`
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L33), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L75), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L129), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L145)]


```solidity
File: ./contracts/connectors/SNXConnector.sol

/// @audit missing zero check for ``
/// @audit missing zero check for ``
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {

/// @audit missing zero check for `collateralType`
68:     function delegateIntoPreferredPool(
            uint128 _accountId,
            address collateralType,
            uint256 newCollateralAmountD18,
            uint256 leverage
        ) public onlyManager {

/// @audit missing zero check for `collateralType`
81:     function delegateIntoApprovedPool(
            uint256 poolIndex,
            uint128 _accountId,
            address collateralType,
            uint256 newCollateralAmountD18,
            uint256 leverage
        ) public onlyManager {

/// @audit missing zero check for `distributor`
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
            public
            onlyManager
        {

/// @audit missing zero check for `base`
121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L64), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L81), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L94), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L121)]


```solidity
File: ./contracts/connectors/SiloConnector.sol

/// @audit missing zero check for `base`
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

/// @audit missing zero check for `silo`
130:     function isSiloEmpty(ISilo silo) public view returns (bool) {

```
*Github:* [[109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L109), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L130)]


```solidity
File: ./contracts/connectors/StargateConnector.sol

/// @audit missing zero check for `base`
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L110)]


```solidity
File: ./contracts/connectors/UNIv3Connector.sol

/// @audit missing zero check for `base`
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L127)]


```solidity
File: ./contracts/governance/Keepers.sol

/// @audit missing zero check for `destination`
/// @audit missing zero check for `executor`
84:     function execute(
            address destination,
            bytes calldata data,
            uint256 gasLimit,
            address executor,
            bytes32[] memory sigR,
            bytes32[] memory sigS,
            uint8[] memory sigV,
            uint256 deadline
        ) public {

```
*Github:* [[84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L84)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

/// @audit missing zero check for `baseToken`
249:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

/// @audit missing zero check for `token`
/// @audit missing zero check for `baseToken`
253:     function _getValue(address token, address baseToken, uint256 amount) internal view returns (uint256) {

/// @audit missing zero check for ``
271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {

/// @audit missing zero check for `_spender`
277:     function _approveOperations(address _token, address _spender, uint256 _amount) internal virtual {

/// @audit missing zero check for `_spender`
285:     function _revokeApproval(address _token, address _spender) internal virtual {

```
*Github:* [[249](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L249), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L253), [271](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L271), [277](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L277), [285](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L285)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

/// @audit missing zero check for `caller`
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
            external
            returns (uint256)
        {

/// @audit missing zero check for `baseToken`
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L27), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L71)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

/// @audit missing zero check for ``
65:     function _lzReceive(Origin calldata _origin, bytes32, bytes calldata _message, address, bytes calldata)
            internal
            override
        {

```
*Github:* [[65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L65)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

/// @audit missing zero check for `omniChainManager`
63:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {

```
*Github:* [[63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L63)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

/// @audit missing zero check for ``
51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {

```
*Github:* [[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

/// @audit missing zero check for `base`
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {

```
*Github:* [[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit missing zero check for `_inputToken`
/// @audit missing zero check for `_outputToken`
68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
            external
            onlyMaintainerOrEmergency
        {

/// @audit missing zero check for `addr`
164:     function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) {

```
*Github:* [[68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

/// @audit missing zero check for `_handler`
45:     function addHandler(address _handler, bool state) external onlyOwner {

/// @audit missing zero check for `caller`
77:     function performSwapAction(address caller, SwapRequest calldata _request)
            external
            payable
            override
            onlyHandler
            returns (uint256)
        {

/// @audit missing zero check for `caller`
133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
             external
             payable
             override
             onlyHandler
         {

/// @audit missing zero check for `caller`
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
             internal
             virtual
             nonReentrant
         {

/// @audit missing zero check for `token`
/// @audit missing zero check for `spender`
185:     function _setAllowance(IERC20 token, address spender, uint256 amount) internal {

```
*Github:* [[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133), [165](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165), [185](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L185)]


```solidity
File: ./contracts/helpers/TVLHelper.sol

/// @audit missing zero check for `registry`
/// @audit missing zero check for `baseToken`
14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {

/// @audit missing zero check for `registry`
41:     function getLatestUpdateTime(uint256 vaultId, PositionRegistry registry) public view returns (uint256) {

```
*Github:* [[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L14), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L41)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

/// @audit missing zero check for `asset`
/// @audit missing zero check for `base`
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {

/// @audit missing zero check for `asset`
/// @audit missing zero check for `baseToken`
71:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {

/// @audit missing zero check for `asset`
/// @audit missing zero check for `baseToken`
81:     function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
            internal
            view
            returns (uint256 value)
        {

/// @audit missing zero check for `quotingToken`
/// @audit missing zero check for `baseToken`
95:     function _getValue(address quotingToken, address baseToken, uint256 amount) internal view returns (uint256) {

```
*Github:* [[61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L61), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L71), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L81), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L95)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

/// @audit missing zero check for `asset`
/// @audit missing zero check for `baseToken`
89:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {

/// @audit missing zero check for `asset`
/// @audit missing zero check for `baseToken`
143:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) {

```
*Github:* [[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L89), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L143)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit missing zero check for `tokenIn`
/// @audit missing zero check for `baseToken`
48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {

/// @audit missing zero check for `tokenIn`
/// @audit missing zero check for `baseToken`
60:     function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) {

```
*Github:* [[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60)]


</details>


<a name="L-2"></a> 
### [L-2] Array is `push()`ed but not `pop()`ed
There is no limit specified on the amount of gas used, so the recipient can use up all of the remaining gas (`gasleft()`), causing it to revert. Therefore, when calling an external contract, it is necessary to specify a limited amount of gas to forward.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/Registry.sol

141:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));

```
*Github:* [[141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L141)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

149:             routes.push(_routes[i]);

```
*Github:* [[149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L149)]



<a name="L-3"></a> 
### [L-3] Consider implementing two-step procedure for updating protocol addresses
A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must "accept" the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the "set" functions ensure that the recipient is of the right interface type.

*There are <b>8</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `valueOracle`
124:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {

/// @audit `withdrawFeeReceiver`
/// @audit `performanceFeeReceiver`
/// @audit `managementFeeReceiver`
135:     function setFeeReceivers(
             address _withdrawFeeReceiver,
             address _performanceFeeReceiver,
             address _managementFeeReceiver
         ) public onlyMaintainer {

```
*Github:* [[124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L124), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L135)]


```solidity
File: ./contracts/accountingManager/Registry.sol

/// @audit `flashLoan`
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

```
*Github:* [[84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L84)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

/// @audit `caller`
/// @audit `caller`
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
            external
            nonReentrant
        {

```
*Github:* [[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L37)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

/// @audit `swapHandler`
58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer {

/// @audit `valueOracle`
67:     function updateValueOracle(address _valueOracle) external onlyMaintainer {

```
*Github:* [[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L58), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L67)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

/// @audit `destChainAddress`
46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer {

```
*Github:* [[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit `valueOracle`
48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {

```
*Github:* [[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48)]



<a name="L-4"></a> 
### [L-4] Constructor / initialization function lacks parameter validation
Constructors and initialization functions play a critical role in contracts by setting important initial states when the contract is first deployed before the system starts. The parameters passed to the constructor and initialization functions directly affect the behavior of the contract / protocol. If incorrect parameters are provided, the system may fail to run, behave abnormally, be unstable, or lack security. Therefore, it's crucial to carefully check each parameter in the constructor and initialization functions. If an exception is found, the transaction should be rolled back.

<details>
<summary>
There are <b>15</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `p` not validated
94:     constructor(AccountingManagerConstructorParams memory p)

```
*Github:* [[94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L94)]


```solidity
File: ./contracts/accountingManager/Registry.sol

/// @audit `_flashLoan` not validated
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {

```
*Github:* [[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L66)]


```solidity
File: ./contracts/connectors/PancakeswapConnector.sol

/// @audit `_positionManager` not validated
/// @audit `_factory` not validated
/// @audit `baseConnectorParams` not validated
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)

```
*Github:* [[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19)]


```solidity
File: ./contracts/governance/NoyaGovernanceBase.sol

/// @audit `_vaultId` not validated
21:     constructor(PositionRegistry _registry, uint256 _vaultId) {

```
*Github:* [[21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L21)]


```solidity
File: ./contracts/governance/TimeLock.sol

/// @audit `minDelay` not validated
/// @audit `proposers` not validated
/// @audit `executors` not validated
/// @audit `owner` not validated
7:     constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L7)]


```solidity
File: ./contracts/governance/Watchers.sol

/// @audit `_owners` not validated
/// @audit `_threshold` not validated
7:     constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L7)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

/// @audit `params` not validated
33:     constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {

```
*Github:* [[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L33)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

/// @audit `_vaultId` not validated
22:     constructor(address _registry, uint256 _vaultId) {

```
*Github:* [[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L22)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

/// @audit `_endpoint` not validated
/// @audit `_owner` not validated
31:     constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

/// @audit `_endpoint` not validated
/// @audit `_owner` not validated
29:     constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }

```
*Github:* [[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L29)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

/// @audit `dl` not validated
/// @audit `_lzHelper` not validated
/// @audit `baseConnectorParams` not validated
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)

```
*Github:* [[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

/// @audit `_lzHelper` not validated
/// @audit `baseConnectorParams` not validated
11:     constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)

```
*Github:* [[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L11)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit `_registry` not validated
/// @audit `_vaultId` not validated
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)

```
*Github:* [[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

/// @audit `swapHandler` not validated
/// @audit `_lifi` not validated
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit `_factory` not validated
/// @audit `_registry` not validated
31:     constructor(address _factory, PositionRegistry _registry) {

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31)]


</details>


<a name="L-5"></a> 
### [L-5] Empty `receive()`/`fallback()` function
If the intention is for Ether sent by a caller to be used for an actual purpose (i.e. the function is not just a WETH `withdraw()` handler), the function should call another function (e.g. call `weth.deposit()` and use the token on the caller's behalf) or at least emit an event to track that funds were sent directly to it.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/connectors/LidoConnector.sol

89:     receive() external payable { }

```
*Github:* [[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L89)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

56:     receive() external payable { }

```
*Github:* [[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L56)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

27:     receive() external payable { }

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L27)]



<a name="L-6"></a> 
### [L-6] Code does not follow the best practice of check-effects-interaction
Code should follow the best-practice of [check-effects-interaction](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/), where state variables are updated before any external calls are made. Doing so prevents a large class of reentrancy bugs.

<details>
<summary>
There are <b>12</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `.safeTransferFrom(...)` is called on line 205
217:         depositQueue.last += 1;

/// @audit `.safeTransferFrom(...)` is called on line 205
218:         depositQueue.totalAWFDeposit += amount;

/// @audit `.isAnActiveConnector(...)` is called on line 288
/// @audit `.addLiquidity(...)` is called on line 293
298:         depositQueue.first = firstTemp;

/// @audit `.balanceOf(...)` is called on line 379
381:             currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;

/// @audit `.balanceOf(...)` is called on line 379
383:             currentWithdrawGroup.totalABAmount = availableAssets;

/// @audit `.balanceOf(...)` is called on line 379
385:         currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;

/// @audit `.balanceOf(...)` is called on line 379
386:         currentWithdrawGroup.totalCBAmount = 0;

/// @audit `.safeTransfer(...)` is called on line 428
436:         totalWithdrawnAmount += processedBaseTokenAmount;

/// @audit `.safeTransfer(...)` is called on line 428
/// @audit `.safeTransfer(...)` is called on line 439
441:         withdrawQueue.first = firstTemp;

/// @audit `.isAnActiveConnector(...)` is called on line 552
/// @audit `.balanceOf(...)` is called on line 555
/// @audit `.sendTokensToTrustedAddress(...)` is called on line 556
/// @audit `.balanceOf(...)` is called on line 559
569:         amountAskedForWithdraw += amountAskedForWithdraw_temp;

```
*Github:* [[217](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L217), [218](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L218), [298](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L298), [381](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L381), [383](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L383), [385](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L385), [386](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L386), [436](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L436), [441](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L441), [569](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L569)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

/// @audit `.flashLoan(...)` is called on line 43
44:         caller = address(0);

```
*Github:* [[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L44)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit `.getPool(...)` is called on line 49
51:         assetToBaseToPool[tokenIn][baseToken] = pool;

```
*Github:* [[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L51)]


</details>


<a name="L-7"></a> 
### [L-7] External function calls within loops
Calling external functions within loops can easily result in insufficient gas. This greatly increases the likelihood of transaction failures, DOS attacks, and other unexpected actions. It is recommended to limit the number of loops within loops that call external functions, and to limit the gas line for each external call.

<details>
<summary>
There are <b>26</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `.safeTransfer(...)`
428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);

/// @audit `.isAnActiveConnector(...)`
552:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {

/// @audit `.balanceOf(...)`
555:             uint256 balanceBefore = baseToken.balanceOf(address(this));

/// @audit `.sendTokensToTrustedAddress(...)`
556:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(

/// @audit `.balanceOf(...)`
559:             uint256 balanceAfter = baseToken.balanceOf(address(this));

```
*Github:* [[428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L428), [552](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L552), [555](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L555), [556](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L556), [559](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L559)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

/// @audit `.getReward(...)`
56:             baseRewardPool.getReward();

```
*Github:* [[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L56)]


```solidity
File: ./contracts/connectors/CompoundConnector.sol

/// @audit `.getAssetInfo(...)`
109:                 IComet.AssetInfo memory info = comet.getAssetInfo(i);

/// @audit `.userCollateral(...)`
112:                 (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset);

/// @audit `.getPrice(...)`
115:                 uint256 collateralPriceInVirtualBase = comet.getPrice(info.priceFeed);

```
*Github:* [[109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L109), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L112), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L115)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

/// @audit `.claim_rewards(...)`
223:             IRewardsGauge(gauges[i]).claim_rewards(address(this));

/// @audit `.claimReward(...)`
235:             IDepositToken(pools[i]).claimReward(address(this));

/// @audit `.getReward(...)`
250:             baseRewardPool.getReward(address(this), true);

```
*Github:* [[223](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L223), [235](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L235), [250](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L250)]


```solidity
File: ./contracts/connectors/Dolomite.sol

/// @audit `.getValue(...)`
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value);

```
*Github:* [[114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L114)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

/// @audit `.tokenIndex(...)`
142:                 tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken));

/// @audit `.getReward(...)`
143:                 rewardContract.getReward(address(this), tokenIndex);

```
*Github:* [[142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L142), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L143)]


```solidity
File: ./contracts/connectors/SiloConnector.sol

/// @audit `.balanceOf(...)`
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));

/// @audit `.balanceOf(...)`
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));

/// @audit `.balanceOf(...)`
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));

/// @audit `.balanceOf(...)`
134:                 IERC20(assetsS[i].collateralToken).balanceOf(address(this))

/// @audit `.balanceOf(...)`
135:                     + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0

```
*Github:* [[117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L117), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L118), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L119), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L134), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L135)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

/// @audit `.balanceOf(...)`
180:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));

/// @audit `.sendTokensToTrustedAddress(...)`
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

/// @audit `.balanceOf(...)`
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));

```
*Github:* [[180](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L180), [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L181), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L182)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

/// @audit `.sendTokensToTrustedAddress(...)`
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```
*Github:* [[44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L44)]


```solidity
File: ./contracts/helpers/TVLHelper.sol

/// @audit `.getPositionTVL(...)`
22:             uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);

/// @audit `.isPositionDebt(...)`
23:             bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);

```
*Github:* [[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L22), [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L23)]


</details>


<a name="L-8"></a> 
### [L-8] Function may return unassigned variable
Make sure that functions with a return value always return a valid and assigned value. Even if the default value is as expected, it should be assigned with the default value for code clarity and to reduce confusion.

*There is one instance of this issue:*
```solidity
File: ./contracts/connectors/FraxConnector.sol

/// @audit `tvl` is unassigned
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```
*Github:* [[150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L150)]



<a name="L-9"></a> 
### [L-9] Functions calling contracts/addresses with transfer hooks are missing reentrancy guards
While adherence to the check-effects-interaction pattern is commendable, the absence of a reentrancy guard in functions, especially where transfer hooks might be present, can expose the protocol users to risks of read-only reentrancies. Such reentrancy vulnerabilities can be exploited to execute malicious actions even without altering the contract state. Without a reentrancy guard, the only potential mitigation would be to blocklist the entire protocol - an extreme and disruptive measure. Therefore, incorporating a reentrancy guard into these functions is vital to bolster security, as it helps protect against both traditional reentrancy attacks and read-only reentrancies, ensuring robust and safe protocol operations.

*There are <b>4</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/AccountingManager.sol

150:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
             external
             returns (uint256)
         {
             emit TransferTokensToTrustedAddress(token, amount, _caller, _data);

```
*Github:* [[150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L150)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

279:     function LPToUnder(PoolInfo memory info, uint256 balance) public view returns (uint256, address) {
             if (balance == 0) return (0, info.tokens[info.defaultWithdrawIndex]);
             uint256 underlyingAssetAmount =
                 estimateWithdrawAmount(ICurveSwap(info.pool), balance, info.defaultWithdrawIndex);

```
*Github:* [[279](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L279)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
            external
            returns (uint256)
        {
            emit TransferTokensToTrustedAddress(token, amount, caller, data);

```
*Github:* [[84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L84)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
            for (uint256 i = 0; i < tokens.length; i++) {
                // gather all of the tokens
    
                ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```
*Github:* [[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L40)]



<a name="L-10"></a> 
### [L-10] Governance functions should be controlled by time locks
Governance functions (such as upgrading contracts, setting critical parameters) should be controlled using time locks to introduce a delay between a proposal and its execution. This gives users time to exit before a potentially dangerous or malicious operation is applied.

*There are <b>6</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/Registry.sol

79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) {

84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

```
*Github:* [[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L84)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {

57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {

80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency {

```
*Github:* [[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

38:     function setPeriod(uint32 _period) external onlyMaintainer {

```
*Github:* [[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38)]



<a name="L-11"></a> 
### [L-11] Loss of precision in divisions
Division by large numbers may result in the result being zero, due to solidity not supporting fractions. Consider requiring a minimum amount for the numerator to ensure that it is always larger than the denominator.

*There are <b>8</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/AccountingManager.sol

484:             previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);

```
*Github:* [[484](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L484)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);

```
*Github:* [[172](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L172)]


```solidity
File: ./contracts/connectors/CamelotConnector.sol

96:         return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply;

```
*Github:* [[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L96)]


```solidity
File: ./contracts/connectors/CompoundConnector.sol

89:         borrowBalanceInVirtualBase = (borrowBalanceInBase * basePriceInVirtualBase) / comet.baseScale();

```
*Github:* [[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L89)]


```solidity
File: ./contracts/connectors/FraxConnector.sol

129:             (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;

136:         uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;

```
*Github:* [[129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L129), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L136)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

132:             return (amountIn * sourceTokenUnit) / uintprice;

134:         return (amountIn * uintprice) / (sourceTokenUnit);

```
*Github:* [[132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L132), [134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L134)]



<a name="L-12"></a> 
### [L-12] Missing checks for state variable assignments
There are some missing checks in these functions, and this could lead to unexpected scenarios. Consider always adding a sanity check for state variables.

<details>
<summary>
There are <b>53</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `_valueOracle`
126:         valueOracle = _valueOracle;

/// @audit `_withdrawFeeReceiver`
143:         withdrawFeeReceiver = _withdrawFeeReceiver;

/// @audit `_performanceFeeReceiver`
144:         performanceFeeReceiver = _performanceFeeReceiver;

/// @audit `_managementFeeReceiver`
145:         managementFeeReceiver = _managementFeeReceiver;

/// @audit `_withdrawFee`
177:         withdrawFee = _withdrawFee;

/// @audit `_performanceFee`
178:         performanceFee = _performanceFee;

/// @audit `_managementFee`
179:         managementFee = _managementFee;

/// @audit `_depositLimitPerTransaction`
668:         depositLimitPerTransaction = _depositLimitPerTransaction;

/// @audit `_depositTotalAmount`
669:         depositLimitTotalAmount = _depositTotalAmount;

/// @audit `_depositWaitingTime`
674:         depositWaitingTime = _depositWaitingTime;

/// @audit `_withdrawWaitingTime`
679:         withdrawWaitingTime = _withdrawWaitingTime;

```
*Github:* [[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L126), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L143), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L144), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L145), [177](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L177), [178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L178), [179](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L179), [668](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L668), [669](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L669), [674](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L674), [679](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L679)]


```solidity
File: ./contracts/accountingManager/NoyaFeeReceiver.sol

/// @audit `_accountingManager`
18:         accountingManager = _accountingManager;

/// @audit `_baseToken`
19:         baseToken = _baseToken;

/// @audit `_receiver`
20:         receiver = _receiver;

```
*Github:* [[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L18), [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L19), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L20)]


```solidity
File: ./contracts/accountingManager/Registry.sol

/// @audit `_flashLoan`
76:         flashLoan = _flashLoan;

/// @audit `_maxNumHoldingPositions`
81:         maxNumHoldingPositions = _maxNumHoldingPositions;

/// @audit `_flashLoan`
86:         flashLoan = _flashLoan;

```
*Github:* [[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L76), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L81), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L86)]


```solidity
File: ./contracts/connectors/AaveConnector.sol

/// @audit `_poolBaseToken`
38:         poolBaseToken = _poolBaseToken;

/// @audit `_pool`
39:         pool = _pool;

```
*Github:* [[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L38), [39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L39)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

/// @audit `aura`
48:         AURA = aura;

/// @audit `bal`
49:         BAL = bal;

/// @audit `_balancerVault`
50:         balancerVault = _balancerVault;

```
*Github:* [[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L49), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L50)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

/// @audit `_registry`
28:         registry = _registry;

```
*Github:* [[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L28)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

/// @audit `cvx`
57:         CVX = cvx;

/// @audit `crv`
58:         CRV = crv;

/// @audit `prisma`
59:         PRISMA = prisma;

```
*Github:* [[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L57), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L58), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L59)]


```solidity
File: ./contracts/connectors/LidoConnector.sol

/// @audit `_lido`
27:         lido = _lido;

/// @audit `_lidoW`
28:         lidoWithdrawal = _lidoW;

/// @audit `_steth`
29:         steth = _steth;

/// @audit `w`
30:         weth = w;

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L29), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L30)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

/// @audit `_mav`
50:         mav = _mav;

/// @audit `_veMav`
51:         veMav = _veMav;

/// @audit `mr`
52:         maverickRouter = mr;

```
*Github:* [[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L50), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L51), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L52)]


```solidity
File: ./contracts/governance/Keepers.sol

/// @audit `_threshold`
33:         threshold = _threshold;

/// @audit `_threshold`
65:         threshold = _threshold;

```
*Github:* [[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L33), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L65)]


```solidity
File: ./contracts/governance/NoyaGovernanceBase.sol

/// @audit `_registry`
23:         registry = _registry;

/// @audit `_vaultId`
24:         vaultId = _vaultId;

```
*Github:* [[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L23), [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L24)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

/// @audit `_minimumHealthFactor`
49:         minimumHealthFactor = _minimumHealthFactor;

```
*Github:* [[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L49)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

/// @audit `_vaultId`
24:         vaultId = _vaultId;

```
*Github:* [[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L24)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

/// @audit `_messageSetting`
37:         messageSetting = _messageSetting;

```
*Github:* [[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L37)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

/// @audit `_lzHelper`
36:         lzHelper = _lzHelper;

/// @audit `destinationAddress`
48:         destChainAddress[chainId] = destinationAddress;

```
*Github:* [[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L36), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L48)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

/// @audit `dl`
22:         DUST_LEVEL = dl;

```
*Github:* [[22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L22)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit `_slippageTolerance`
58:         genericSlippageTolerance = _slippageTolerance;

```
*Github:* [[58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L58)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

/// @audit `_lifi`
29:         lifi = _lifi;

/// @audit `state`
46:         isHandler[_handler] = state;

/// @audit `state`
56:         isChainSupported[_chainId] = state;

/// @audit `state`
66:         isBridgeWhiteListed[bridgeName] = state;

```
*Github:* [[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L29), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L46), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L56), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L66)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

/// @audit `_registry`
31:         registry = _registry;

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L31)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

/// @audit `_chainlinkPriceAgeThreshold`
60:         chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold;

```
*Github:* [[60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L60)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit `_factory`
32:         factory = _factory;

/// @audit `_registry`
33:         registry = _registry;

/// @audit `_period`
40:         period = _period;

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L33), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L40)]


</details>


<a name="L-13"></a> 
### [L-13] Missing limits when setting min/max amounts
There are some missing limits in these functions, and this could lead to unexpected scenarios. Consider adding a min/max limit for the following values, when appropriate.

*There are <b>5</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `_depositLimitPerTransaction`
/// @audit `_depositTotalAmount`
667:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {

/// @audit `_depositWaitingTime`
673:     function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {

/// @audit `_withdrawWaitingTime`
678:     function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {

```
*Github:* [[667](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L667), [673](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L673), [678](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L678)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit `_slippageTolerance`
57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {

```
*Github:* [[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit `_period`
38:     function setPeriod(uint32 _period) external onlyMaintainer {

```
*Github:* [[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38)]



<a name="L-14"></a> 
### [L-14] Missing zero address check in constructor
Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

*There are <b>10</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/Registry.sol

/// @audit missing zero check for `_flashLoan`
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {

```
*Github:* [[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L66)]


```solidity
File: ./contracts/connectors/PancakeswapConnector.sol

/// @audit missing zero check for `_positionManager`
/// @audit missing zero check for `_factory`
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
            UNIv3Connector(_positionManager, _factory, baseConnectorParams)
        {

```
*Github:* [[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L19)]


```solidity
File: ./contracts/governance/TimeLock.sol

/// @audit missing zero check for `owner`
7:     constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)
           TimelockController(minDelay, proposers, executors, owner)
       { }

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L7)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

/// @audit missing zero check for `_endpoint`
/// @audit missing zero check for `_owner`
31:     constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

/// @audit missing zero check for `_endpoint`
/// @audit missing zero check for `_owner`
29:     constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }

```
*Github:* [[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L29)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

/// @audit missing zero check for `_lzHelper`
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
            OmnichainLogic(_lzHelper, baseConnectorParams)
        {

```
*Github:* [[19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

/// @audit missing zero check for `_lzHelper`
11:     constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
            OmnichainLogic(_lzHelper, baseConnectorParams)
        { }

```
*Github:* [[11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L11)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

/// @audit missing zero check for `_registry`
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
            NoyaGovernanceBase(_registry, _vaultId)
        {

```
*Github:* [[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

/// @audit missing zero check for `swapHandler`
/// @audit missing zero check for `_lifi`
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit missing zero check for `_factory`
/// @audit missing zero check for `_registry`
31:     constructor(address _factory, PositionRegistry _registry) {

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31)]



<a name="L-15"></a> 
### [L-15] Consider some checks for `address(0)` when setting address state variables
Check for zero-address to avoid the risk of setting `address(0)` for state variables after an update.

<details>
<summary>
There are <b>29</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

/// @audit `_valueOracle`
126:         valueOracle = _valueOracle;

/// @audit `_withdrawFeeReceiver`
143:         withdrawFeeReceiver = _withdrawFeeReceiver;

/// @audit `_performanceFeeReceiver`
144:         performanceFeeReceiver = _performanceFeeReceiver;

/// @audit `_managementFeeReceiver`
145:         managementFeeReceiver = _managementFeeReceiver;

```
*Github:* [[126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L126), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L143), [144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L144), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L145)]


```solidity
File: ./contracts/accountingManager/NoyaFeeReceiver.sol

/// @audit `_accountingManager`
18:         accountingManager = _accountingManager;

/// @audit `_receiver`
20:         receiver = _receiver;

```
*Github:* [[18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L18), [20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L20)]


```solidity
File: ./contracts/accountingManager/Registry.sol

/// @audit `_flashLoan`
76:         flashLoan = _flashLoan;

/// @audit `_flashLoan`
86:         flashLoan = _flashLoan;

```
*Github:* [[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L76), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L86)]


```solidity
File: ./contracts/connectors/AaveConnector.sol

/// @audit `_poolBaseToken`
38:         poolBaseToken = _poolBaseToken;

```
*Github:* [[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L38)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

/// @audit `aura`
48:         AURA = aura;

/// @audit `bal`
49:         BAL = bal;

/// @audit `_balancerVault`
50:         balancerVault = _balancerVault;

```
*Github:* [[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L48), [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L49), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L50)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

/// @audit `_registry`
28:         registry = _registry;

```
*Github:* [[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L28)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

/// @audit `cvx`
57:         CVX = cvx;

/// @audit `crv`
58:         CRV = crv;

/// @audit `prisma`
59:         PRISMA = prisma;

```
*Github:* [[57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L57), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L58), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L59)]


```solidity
File: ./contracts/connectors/LidoConnector.sol

/// @audit `_lido`
27:         lido = _lido;

/// @audit `_lidoW`
28:         lidoWithdrawal = _lidoW;

/// @audit `_steth`
29:         steth = _steth;

/// @audit `w`
30:         weth = w;

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L27), [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L28), [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L29), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L30)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

/// @audit `_mav`
50:         mav = _mav;

/// @audit `_veMav`
51:         veMav = _veMav;

/// @audit `mr`
52:         maverickRouter = mr;

```
*Github:* [[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L50), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L51), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L52)]


```solidity
File: ./contracts/governance/NoyaGovernanceBase.sol

/// @audit `_registry`
23:         registry = _registry;

```
*Github:* [[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L23)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

/// @audit `_lzHelper`
36:         lzHelper = _lzHelper;

```
*Github:* [[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L36)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

/// @audit `_lifi`
29:         lifi = _lifi;

```
*Github:* [[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L29)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

/// @audit `_registry`
31:         registry = _registry;

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L31)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit `_factory`
32:         factory = _factory;

/// @audit `_registry`
33:         registry = _registry;

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L33)]


</details>


<a name="L-16"></a> 
### [L-16] Owner can renounce ownership
Each of the following contracts implements or inherits the `renounceOwnership()` function. This can represent a certain risk if the ownership is renounced for any other reason than by design. Renouncing ownership will leave the contract without an owner, thereby removing any functionality that is only available to the owner.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/NoyaFeeReceiver.sol

7: contract NoyaFeeReceiver is Ownable {

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7)]


```solidity
File: ./contracts/governance/Keepers.sol

9: contract Keepers is EIP712, Ownable2Step {

```
*Github:* [[9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L9)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {

```
*Github:* [[10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10)]



<a name="L-17"></a> 
### [L-17] `receive()`/`fallback()` function does not authorize requests
Having no access control on the function (e.g. `require(msg.sender == address(weth))`) means that someone may send Ether to the contract, and have no way to get anything back out, which is a loss of funds. If the concern is having to spend a small amount of gas to check the sender against an immutable address, the code should at least have a function to rescue mistakenly-sent Ether.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/connectors/LidoConnector.sol

89:     receive() external payable { }

```
*Github:* [[89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L89)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

56:     receive() external payable { }

```
*Github:* [[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L56)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

27:     receive() external payable { }

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L27)]



<a name="L-18"></a> 
### [L-18] Solidity version 0.8.20 or above may not work on other chains due to PUSH0
Solidity version 0.8.20 or above uses the new [Shanghai EVM](https://blog.soliditylang.org/2023/05/10/solidity-0.8.20-release-announcement/#important-note) which introduces the PUSH0 opcode. This op code may not yet be implemented on all evm-chains or Layer2s, so deployment on these chains will fail. Consider using an earlier solidity version.

<details>
<summary>
There are <b>41</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L2)]


```solidity
File: ./contracts/accountingManager/NoyaFeeReceiver.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L2)]


```solidity
File: ./contracts/accountingManager/Registry.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L2)]


```solidity
File: ./contracts/connectors/AaveConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L2)]


```solidity
File: ./contracts/connectors/AerodromeConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L2)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L2)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L2)]


```solidity
File: ./contracts/connectors/CamelotConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L2)]


```solidity
File: ./contracts/connectors/CompoundConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L2)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L2)]


```solidity
File: ./contracts/connectors/Dolomite.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L2)]


```solidity
File: ./contracts/connectors/FraxConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L2)]


```solidity
File: ./contracts/connectors/GearBoxV3.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L2)]


```solidity
File: ./contracts/connectors/LidoConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L2)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L2)]


```solidity
File: ./contracts/connectors/MorphoBlueConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L2)]


```solidity
File: ./contracts/connectors/PancakeswapConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L2)]


```solidity
File: ./contracts/connectors/PendleConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L2)]


```solidity
File: ./contracts/connectors/PrismaConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L2)]


```solidity
File: ./contracts/connectors/SNXConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L2)]


```solidity
File: ./contracts/connectors/SiloConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L2)]


```solidity
File: ./contracts/connectors/StargateConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L2)]


```solidity
File: ./contracts/connectors/UNIv3Connector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L2)]


```solidity
File: ./contracts/governance/Keepers.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L2)]


```solidity
File: ./contracts/governance/NoyaGovernanceBase.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L2)]


```solidity
File: ./contracts/governance/TimeLock.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/TimeLock.sol#L2)]


```solidity
File: ./contracts/governance/Watchers.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Watchers.sol#L2)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L2)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L2)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L2)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L2)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L2)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L2)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L2)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L2)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L2)]


```solidity
File: ./contracts/helpers/TVLHelper.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L2)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L2)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L2)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L2)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

2: pragma solidity 0.8.20;

```
*Github:* [[2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L2)]


</details>


<a name="L-19"></a> 
### [L-19] Some tokens may revert when large transfers are made
Tokens such as COMP or UNI will revert when an address' balance reaches `type(uint96).max`. Ensure that the calls below can be broken up into smaller batches if necessary.

<details>
<summary>
There are <b>20</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

156:             IERC20(token).safeTransfer(address(msg.sender), amount);

205:         baseToken.safeTransferFrom(msg.sender, address(this), amount);

428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);

439:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);

688:             IERC20(token).safeTransfer(msg.sender, amount);

```
*Github:* [[156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L156), [205](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L205), [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L428), [439](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L439), [688](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L688)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

76:                 tokens[i].safeTransfer(receiver, amounts[i]);

91:             tokens[i].safeTransfer(msg.sender, amounts[i]);

```
*Github:* [[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L76), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L91)]


```solidity
File: ./contracts/connectors/PancakeswapConnector.sol

32:         IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L32)]


```solidity
File: ./contracts/connectors/PendleConnector.sol

99:         IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);

114:         IERC20(address(_SY)).safeTransfer(address(market), SYamount);

115:         IERC20(address(_PT)).safeTransfer(address(market), PTamount);

189:         IERC20(address(_PT)).safeTransfer(address(market), exactPTIn);

204:         IERC20(address(market)).safeTransfer(address(market), amount);

221:         IERC20(address(SY)).safeTransfer(address(SY), _amount);

```
*Github:* [[99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L99), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L114), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L115), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L189), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L204), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L221)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);

99:             IERC20(token).safeTransfer(address(msg.sender), amount);

104:             IERC20(token).safeTransfer(msg.sender, amount);

```
*Github:* [[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L96), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L99), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L104)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

32:             IERC20(token).safeTransfer(msg.sender, amount);

36:         IERC20(token).safeTransfer(msg.sender, amountToSend);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L32), [36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L36)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

198:             IERC20(token).safeTransfer(userAddress, amount);

```
*Github:* [[198](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L198)]


</details>


<a name="L-20"></a> 
### [L-20] Some tokens may revert when zero value transfers are made
Despite the fact that [EIP-20 states](https://github.com/ethereum/EIPs/blob/7500ac4fc1bbdfaf684e7ef851f798f6b667b2fe/EIPS/eip-20.md?plain=1#L116) that zero-value transfers must be accepted, some tokens, such as LEND, will revert if this is attempted, which may cause transactions that involve other tokens (such as batch operations) to fully revert. Consider skipping the transfer if the amount is zero, which will also save gas.

<details>
<summary>
There are <b>20</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

156:             IERC20(token).safeTransfer(address(msg.sender), amount);

205:         baseToken.safeTransferFrom(msg.sender, address(this), amount);

428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);

439:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);

688:             IERC20(token).safeTransfer(msg.sender, amount);

```
*Github:* [[156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L156), [205](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L205), [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L428), [439](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L439), [688](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L688)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

76:                 tokens[i].safeTransfer(receiver, amounts[i]);

91:             tokens[i].safeTransfer(msg.sender, amounts[i]);

```
*Github:* [[76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L76), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L91)]


```solidity
File: ./contracts/connectors/PancakeswapConnector.sol

32:         IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L32)]


```solidity
File: ./contracts/connectors/PendleConnector.sol

99:         IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);

114:         IERC20(address(_SY)).safeTransfer(address(market), SYamount);

115:         IERC20(address(_PT)).safeTransfer(address(market), PTamount);

189:         IERC20(address(_PT)).safeTransfer(address(market), exactPTIn);

204:         IERC20(address(market)).safeTransfer(address(market), amount);

221:         IERC20(address(SY)).safeTransfer(address(SY), _amount);

```
*Github:* [[99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L99), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L114), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L115), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L189), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L204), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L221)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);

99:             IERC20(token).safeTransfer(address(msg.sender), amount);

104:             IERC20(token).safeTransfer(msg.sender, amount);

```
*Github:* [[96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L96), [99](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L99), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L104)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

32:             IERC20(token).safeTransfer(msg.sender, amount);

36:         IERC20(token).safeTransfer(msg.sender, amountToSend);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L32), [36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L36)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

198:             IERC20(token).safeTransfer(userAddress, amount);

```
*Github:* [[198](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L198)]


</details>


<a name="L-21"></a> 
### [L-21] Sending tokens in a for loop
Performing token transfers in a loop in a Solidity contract is generally not recommended due to various reasons. One of these reasons is the "Fail-Silently" issue.

In a Solidity loop, if one transfer operation fails, it causes the entire transaction to fail. This issue can be particularly troublesome when you're dealing with multiple transfers in one transaction. For instance, if you're looping through an array of recipients to distribute dividends or rewards, a single failed transfer will prevent all the subsequent recipients from receiving their transfers. This could be due to the recipient contract throwing an exception or due to other issues like a gas limit being exceeded.

Moreover, such a design could also inadvertently lead to a situation where a malicious contract intentionally causes a failure when receiving Ether to prevent other participants from getting their rightful transfers. This could open up avenues for griefing attacks in the system.

Resolution: To mitigate this problem, it's typically recommended to follow the "withdraw pattern" in your contracts instead of pushing payments. In this model, each recipient would be responsible for triggering their own payment. This separates each transfer operation, so a failure in one doesn't impact the others. Additionally, it greatly reduces the chance of malicious interference as the control over fund withdrawal lies with the intended recipient and not with an external loop operation.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/helpers/BaseConnector.sol

/// @audit `sendTokensToTrustedAddress`
178:         for (uint256 i = 0; i < tokens.length; i++) {
                 // gather all of the tokens
                 uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
                 ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```
*Github:* [[178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L178)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

/// @audit `sendTokensToTrustedAddress`
41:         for (uint256 i = 0; i < tokens.length; i++) {
                // gather all of the tokens
    
                ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```
*Github:* [[41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L41)]



<a name="L-22"></a> 
### [L-22] Tokens may be minted to `address(0)`

*There is one instance of this issue:*
```solidity
File: ./contracts/accountingManager/AccountingManager.sol

693:     function mint(uint256 shares, address receiver) public override returns (uint256) {
             revert NoyaAccounting_NOT_ALLOWED();
         }

```
*Github:* [[693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L693)]



<a name="L-23"></a> 
### [L-23] Unsafe downcast
When a type is downcast to a smaller type, the higher order bits are truncated, effectively applying a modulo to the original value. Without any other checks, this wrapping will lead to unexpected behavior and bugs.

*There are <b>6</b> instances of this issue:*
```solidity
File: ./contracts/connectors/CurveConnector.sol

/// @audit uint256 -> uint128
169:         ICurveSwap(poolInfo.pool).remove_liquidity_one_coin(amount, int128(uint128(withdrawIndex)), minAmount);

/// @audit uint256 -> uint128
302:         int128 tokenIndex = int128(uint128(index));

```
*Github:* [[169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L169), [302](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L302)]


```solidity
File: ./contracts/connectors/SNXConnector.sol

/// @audit uint256 -> uint128
90:             _accountId, uint128(poolIds[poolIndex]), collateralType, newCollateralAmountD18, leverage

```
*Github:* [[90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L90)]


```solidity
File: ./contracts/connectors/StargateConnector.sol

/// @audit uint256 -> uint16
84:                 uint16(withdrawRequest.poolId), withdrawRequest.routerAmount, address(this)

```
*Github:* [[84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L84)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit uint256 -> uint128
61:         uint128 amountIn128 = uint128(amount);

/// @audit int56 -> int24
81:         int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));

```
*Github:* [[61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L61), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81)]



<a name="L-24"></a> 
### [L-24] Use Ownable2Step instead of Ownable
`Ownable2Step` and `Ownable2StepUpgradeable` prevent the contract ownership from mistakenly being transferred to an address that cannot handle it (e.g. due to a typo in the address), by requiring that the recipient of the owner permissions actively accept via a contract call of its own.

*There is one instance of this issue:*
```solidity
File: ./contracts/accountingManager/NoyaFeeReceiver.sol

7: contract NoyaFeeReceiver is Ownable {

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L7)]



<a name="L-25"></a> 
### [L-25] Consider using `ERC721A` instead of `ERC721`
[ERC721A](https://www.erc721a.org/) is an implementation of IERC721 with significant gas savings for minting multiple NFTs in a single transaction.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/connectors/LidoConnector.sol

7: contract LidoConnector is BaseConnector, ERC721Holder {

```
*Github:* [[7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L7)]


```solidity
File: ./contracts/connectors/UNIv3Connector.sol

12: contract UNIv3Connector is BaseConnector, ERC721Holder {

```
*Github:* [[12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L12)]



<a name="L-26"></a> 
### [L-26] Using zero as a parameter
Taking `0` as a valid argument in Solidity without checks can lead to severe security issues. A historical example is the infamous `0x0` address bug where numerous tokens were lost. This happens because 0 can be interpreted as an uninitialized `address`, leading to transfers to the 0x0 address, effectively burning tokens. Moreover, `0` as a denominator in division operations would cause a runtime exception. It's also often indicative of a logical error in the caller's code. It's important to always validate input and handle edge cases like `0` appropriately. Use `require()` statements to enforce conditions and provide clear error messages to facilitate debugging and safer code.

*There are <b>10</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/AccountingManager.sol

215:         depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);

313:         withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);

```
*Github:* [[215](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L215), [313](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L313)]


```solidity
File: ./contracts/accountingManager/Registry.sol

141:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));

```
*Github:* [[141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L141)]


```solidity
File: ./contracts/connectors/Dolomite.sol

50:         (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));

```
*Github:* [[50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L50)]


```solidity
File: ./contracts/connectors/SiloConnector.sol

66:             revert IConnector_LowHealthFactor(0);

104:             revert IConnector_LowHealthFactor(0);

```
*Github:* [[66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L66), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L104)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)

```
*Github:* [[213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L213)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here

```
*Github:* [[80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L80)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

59:         emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);

```
*Github:* [[59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

129:             revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));

```
*Github:* [[129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L129)]



<a name="L-27"></a> 
### [L-27] `abi.encodePacked()` should not be used with dynamic types when passing the result to a hash function such as `keccak256()`
Use `abi.encode()` instead which will pad items to 32 bytes, which will [prevent hash collisions](https://docs.soliditylang.org/en/v0.8.13/abi-spec.html#non-standard-packed-mode) (e.g. `abi.encodePacked(0x123,0x456)` => `0x123456` => `abi.encodePacked(0x1,0x23456)`, but `abi.encode(0x123,0x456)` => `0x0...1230...456`). "Unless there is a compelling reason, `abi.encode` should be preferred". If there is only one argument to `abi.encodePacked()` it can often be cast to `bytes()` or `bytes32()` [instead](https://ethereum.stackexchange.com/questions/30912/how-to-compare-strings-in-solidity#answer-82739).
If all arguments are strings and or bytes, `bytes.concat()` should be used instead

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/connectors/UNIv3Connector.sol

136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));

```
*Github:* [[136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L136)]


```solidity
File: ./contracts/governance/Keepers.sol

102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));

```
*Github:* [[102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L102)]



<a name="L-28"></a> 
### [L-28] Centralization Risk for trusted owners
Contracts have owners with privileged rights to perform admin tasks and need to be trusted to not perform malicious updates or drain funds.

<details>
<summary>
There are <b>160</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

124:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {

135:     function setFeeReceivers(
             address _withdrawFeeReceiver,
             address _performanceFeeReceiver,
             address _managementFeeReceiver
         ) public onlyMaintainer {

170:     function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer {

226:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

257:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
             public
             onlyManager

328:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

360:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {

370:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {

396:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

453:     function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager {

475:     function recordProfitForFee() public onlyManager nonReentrant {

505:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {

526:     function collectPerformanceFees() public onlyManager nonReentrant {

548:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {

659:     function emergencyStop() public whenNotPaused onlyEmergency {

663:     function unpause() public whenPaused onlyEmergency {

667:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {

673:     function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {

678:     function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {

683:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {

```
*Github:* [[124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L124), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L135), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L170), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L226), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L257), [328](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L328), [360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L360), [370](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L370), [396](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L396), [453](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L453), [475](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L475), [505](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L505), [526](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L526), [548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L548), [659](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L659), [663](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L663), [667](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L667), [673](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L673), [678](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L678), [683](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L683)]


```solidity
File: ./contracts/accountingManager/NoyaFeeReceiver.sol

23:     function withdrawShares(uint256 amount) external onlyOwner {

27:     function burnShares(uint256 amount) external onlyOwner {

```
*Github:* [[23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L23), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/NoyaFeeReceiver.sol#L27)]


```solidity
File: ./contracts/accountingManager/Registry.sol

79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) {

84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

106:     function addVault(
             uint256 vaultId,
             address _accountingManager,
             address _baseToken,
             address _governer,
             address _maintainer,
             address _maintainerWithoutTimelock,
             address _keeperContract,
             address _watcher,
             address _emergency,
             address[] calldata _trustedTokens
         ) external onlyRole(MAINTAINER_ROLE) {

158:     function changeVaultAddresses(
             uint256 vaultId,
             address _governer,
             address _maintainer,
             address _maintainerWithoutTimelock,
             address _keeperContract,
             address _watcher,
             address _emergency
         ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

188:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
             external
             onlyVaultMaintainer(vaultId)

207:     function updateConnectorTrustedTokens(
             uint256 vaultId,
             address _connectorAddress,
             address[] calldata _tokens,
             bool trusted
         ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {

238:     function addTrustedPosition(
             uint256 vaultId,
             uint256 _positionTypeId,
             address calculatorConnector,
             bool onlyOwner,
             bool _isDebt,
             bytes calldata _data,
             bytes calldata _additionalData
         ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {

266:     function removeTrustedPosition(uint256 vaultId, bytes32 _positionId)
             external
             onlyVaultMaintainer(vaultId)

```
*Github:* [[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L84), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L106), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L158), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L188), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L207), [238](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L238), [266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L266)]


```solidity
File: ./contracts/connectors/AaveConnector.sol

46:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {

62:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
            external
            onlyManager

81:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {

88:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager {

100:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {

```
*Github:* [[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L46), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L62), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L81), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L88), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AaveConnector.sol#L100)]


```solidity
File: ./contracts/connectors/AerodromeConnector.sol

53:     function supply(DepositData memory data) public onlyManager nonReentrant {

79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant {

100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {

106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {

111:     function claim(address pool) public onlyManager nonReentrant {

```
*Github:* [[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L53), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L79), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L100), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L106), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/AerodromeConnector.sol#L111)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

64:     function openPosition(
            bytes32 poolId,
            uint256[] memory amounts,
            uint256[] memory amountsWithoutBPT,
            uint256 minBPT,
            uint256 auraAmount
        ) public onlyManager nonReentrant {

109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {

115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {

```
*Github:* [[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L64), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L109), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L115)]


```solidity
File: ./contracts/connectors/CamelotConnector.sol

43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {

65:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
            external
            onlyManager

```
*Github:* [[43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L43), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CamelotConnector.sol#L65)]


```solidity
File: ./contracts/connectors/CompoundConnector.sol

29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {

48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {

63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {

```
*Github:* [[29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L29), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L48), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CompoundConnector.sol#L63)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {

81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {

103:     function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {

117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
             public
             onlyManager

160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
             public
             onlyManager

182:     function withdrawFromConvexBooster(uint256 pid, uint256 amount) public onlyManager {

192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager {

202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager {

212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager {

221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {

233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {

247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

```
*Github:* [[68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L81), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L103), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L117), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L160), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L182), [192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L192), [202](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L202), [212](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L212), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L221), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L233), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L247)]


```solidity
File: ./contracts/connectors/Dolomite.sol

30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
            public
            onlyManager

77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
            public
            onlyManager

98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {

```
*Github:* [[30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L30), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L43), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L58), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L77), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/Dolomite.sol#L98)]


```solidity
File: ./contracts/connectors/FraxConnector.sol

38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
            external
            onlyManager

68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {

87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {

```
*Github:* [[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L38), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L68), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/FraxConnector.sol#L87)]


```solidity
File: ./contracts/connectors/GearBoxV3.sol

24:     function openAccount(address facade, uint256 ref) public onlyManager {

41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {

62:     function executeCommands(
            address facade,
            address creditAccount,
            MultiCall[] calldata calls,
            address approvalToken,
            uint256 amount
        ) public onlyManager nonReentrant {

```
*Github:* [[24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L24), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L41), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L62)]


```solidity
File: ./contracts/connectors/LidoConnector.sol

37:     function deposit(uint256 amountIn) external onlyManager nonReentrant {

51:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {

69:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {

```
*Github:* [[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L51), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/LidoConnector.sol#L69)]


```solidity
File: ./contracts/connectors/MaverickConnector.sol

64:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant {

78:     function unstake(uint256 lockupId) external onlyManager nonReentrant {

91:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {

115:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
             external
             onlyManager

137:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {

```
*Github:* [[64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L64), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L78), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L91), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L115), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MaverickConnector.sol#L137)]


```solidity
File: ./contracts/connectors/MorphoBlueConnector.sol

35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {

58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {

80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant {

95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant {

```
*Github:* [[35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L35), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L58), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L80), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/MorphoBlueConnector.sol#L95)]


```solidity
File: ./contracts/connectors/PancakeswapConnector.sol

31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {

40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant {

50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant {

```
*Github:* [[31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L31), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L40), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PancakeswapConnector.sol#L50)]


```solidity
File: ./contracts/connectors/PendleConnector.sol

78:     function supply(address market, uint256 amount) external onlyManager nonReentrant {

97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {

112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {

126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
             external
             onlyManager

166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
             public
             onlyManager

183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
             external
             onlyManager

203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {

216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {

241:     function claimRewards(IPMarket market) external onlyManager nonReentrant {

```
*Github:* [[78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L78), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L97), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L112), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L126), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L137), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L149), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L166), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L183), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L203), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L216), [241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PendleConnector.sol#L241)]


```solidity
File: ./contracts/connectors/PrismaConnector.sol

33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {

52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
            public
            onlyManager

75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {

97:     function adjustTrove(
            IStakeNTroveZap zapContract,
            address tm,
            uint256 mFee,
            uint256 wAmount,
            uint256 bAmount,
            bool isBorrowing
        ) public onlyManager nonReentrant {

129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {

```
*Github:* [[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L52), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L75), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L97), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/PrismaConnector.sol#L129)]


```solidity
File: ./contracts/connectors/SNXConnector.sol

25:     function createAccount() public onlyManager {

30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

68:     function delegateIntoPreferredPool(
            uint128 _accountId,
            address collateralType,
            uint256 newCollateralAmountD18,
            uint256 leverage
        ) public onlyManager {

81:     function delegateIntoApprovedPool(
            uint256 poolIndex,
            uint128 _accountId,
            address collateralType,
            uint256 newCollateralAmountD18,
            uint256 leverage
        ) public onlyManager {

94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
            public
            onlyManager

102:     function mintOrBurnSUSD(
             uint256 _amount,
             uint128 _accountId,
             uint128 poolId,
             address collateralType,
             bool mintOrBurn
         ) public onlyManager {

```
*Github:* [[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L25), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L30), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L46), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L81), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L94), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SNXConnector.sol#L102)]


```solidity
File: ./contracts/connectors/SiloConnector.sol

33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {

52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
            external
            onlyManager

85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {

98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {

```
*Github:* [[33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L52), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L85), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/SiloConnector.sol#L98)]


```solidity
File: ./contracts/connectors/StargateConnector.sol

49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {

76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant {

103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {

```
*Github:* [[49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L49), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L76), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/StargateConnector.sol#L103)]


```solidity
File: ./contracts/connectors/UNIv3Connector.sol

40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {

63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {

87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {

101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {

```
*Github:* [[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L40), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L63), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L87), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L101)]


```solidity
File: ./contracts/governance/Keepers.sol

42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {

63:     function setThreshold(uint8 _threshold) public onlyOwner {

```
*Github:* [[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L63)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

45:     function updateMinimumHealthFactor(uint256 _minimumHealthFactor) external onlyMaintainer {

58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer {

67:     function updateValueOracle(address _valueOracle) external onlyMaintainer {

122:     function transferPositionToAnotherConnector(
             address[] memory tokens,
             uint256[] memory amounts,
             bytes memory data,
             address connector
         ) external onlyManager nonReentrant {

153:     function updateTokenInRegistry(address token) public onlyManager {

204:     function swapHoldings(
             address[] memory tokensIn,
             address[] memory tokensOut,
             uint256[] memory amountsIn,
             bytes[] memory swapData,
             uint256[] memory routeIds
         ) external onlyManager nonReentrant {

```
*Github:* [[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L45), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L58), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L67), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L122), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L153), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperReceiver.sol

40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {

52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {

```
*Github:* [[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52)]


```solidity
File: ./contracts/helpers/LZHelpers/LZHelperSender.sol

36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {

51:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {

63:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {

```
*Github:* [[36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L36), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L51), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/LZHelpers/LZHelperSender.sol#L63)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainLogic.sol

46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer {

57:     function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {

68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {

```
*Github:* [[46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68)]


```solidity
File: ./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

28:     function updateTVLInfo() external onlyManager {

```
*Github:* [[28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {

57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {

68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
            external
            onlyMaintainerOrEmergency

80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency {

90:     function executeSwap(SwapRequest memory _swapRequest)
            external
            payable
            onlyEligibleUser

126:     function executeBridge(BridgeRequest calldata _bridgeRequest)
             external
             payable
             onlyEligibleUser

147:     function addRoutes(RouteData[] memory _routes) public onlyMaintainer {

158:     function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {

164:     function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) {

```
*Github:* [[48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L158), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

45:     function addHandler(address _handler, bool state) external onlyOwner {

55:     function addChain(uint256 _chainId, bool state) external onlyOwner {

65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {

77:     function performSwapAction(address caller, SwapRequest calldata _request)
            external
            payable
            override
            onlyHandler

133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
             external
             payable
             override
             onlyHandler

193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {

```
*Github:* [[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
            public
            onlyMaintainer

51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
            external
            onlyMaintainer

61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {

```
*Github:* [[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L51), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L61)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

56:     function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {

70:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
            external
            onlyMaintainer

```
*Github:* [[56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L56), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

38:     function setPeriod(uint32 _period) external onlyMaintainer {

48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {

```
*Github:* [[38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48)]


</details>


<a name="L-29"></a> 
### [L-29] `decimals()` is not a part of the ERC-20 standard
The `decimals()` function is not a part of the ERC-20 standard, and was added later as an optional extension. As such, some valid ERC20 tokens do not support this interface, so it is unsafe to blindly cast all tokens to this interface, and then call this function.

*There is one instance of this issue:*
```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

139:         uint256 decimals = IERC20Metadata(token).decimals();

```
*Github:* [[139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L139)]



<a name="L-30"></a> 
### [L-30] `onlyOwner` functions not accessible if owner renounces ownership
The owner is able to perform certain privileged activities, but it's possible to set the owner to `address(0)`. This can represent a certain risk if the ownership is renounced for any other reason than by design. Renouncing ownership will leave the contract without an owner, therefore limiting any functionality that needs authority.

*There are <b>6</b> instances of this issue:*
```solidity
File: ./contracts/governance/Keepers.sol

42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {

63:     function setThreshold(uint8 _threshold) public onlyOwner {

```
*Github:* [[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L63)]


```solidity
File: ./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

45:     function addHandler(address _handler, bool state) external onlyOwner {

55:     function addChain(uint256 _chainId, bool state) external onlyOwner {

65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {

193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {

```
*Github:* [[45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193)]



<a name="L-31"></a> 
### [L-31] Chainlink answer is not compared against min/max values
Some check like this can be added to avoid returning of the min price or the max price in case of the price crashes:
```solidity
	require(answer < _maxPrice, "Upper price bound breached");
	require(answer > _minPrice, "Lower price bound breached");
```

*There is one instance of this issue:*
```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

123:         (, price,, updatedAt,) = source.latestRoundData();

```
*Github:* [[123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L123)]



<a name="L-32"></a> 
### [L-32] Prefer skip over revert model in iteration
It is preferable to skip operations on an array index when a condition is not met rather than reverting the whole transaction as reverting can introduce the possiblity of malicous actors purposefully introducing array objects which fail conditional checks within for/while loops so group operations fail. As such it is recommended to simply skip such array indices over reverting unless there is a valid security or logic reason behind not doing so.

*There are <b>3</b> instances of this issue:*
```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
                    // execute the transactions
                    (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
                    require(success, "BalancerFlashLoan: Flash loan failed");

89:         for (uint256 i = 0; i < tokens.length; i++) {
                // send the tokens back to the vault
                tokens[i].safeTransfer(msg.sender, amounts[i]);
                require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");

```
*Github:* [[79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L79), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L89)]


```solidity
File: ./contracts/governance/Keepers.sol

104:             for (uint256 i = 0; i < threshold;) {
                     address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
                     require(recovered > lastAdd && isOwner[recovered]);

```
*Github:* [[104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L104)]



<a name="L-33"></a> 
### [L-33] External calls in modifiers should be avoided
External calls within modifiers can introduce unintended reentrancy risks and obscure the flow of a contract's logic. Modifiers are designed to perform checks before executing function logic, and using external calls can make the flow unpredictable due to the potential for state changes or reentrancy by the called contract. Such ambiguity makes code harder to audit and understand. To ensure clarity and security, avoid external calls in modifiers. Instead, place them in the function body, where their execution order and effects are more explicit. This practice enhances contract readability, aids auditors, and minimizes unexpected behaviors.

<details>
<summary>
There are <b>13</b> instances (click to show):
</summary>

```solidity
File: ./contracts/governance/NoyaGovernanceBase.sol

/// @audit `.getGovernanceAddresses(...)`
32:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);

/// @audit `.flashLoan(...)`
33:         if (!(msg.sender == keeperContract || msg.sender == emergencyManager || msg.sender == registry.flashLoan())) {

/// @audit `.getGovernanceAddresses(...)`
44:         (,,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);

/// @audit `.getGovernanceAddresses(...)`
54:         (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);

/// @audit `.getGovernanceAddresses(...)`
66:         (, address maintainer,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);

/// @audit `.getGovernanceAddresses(...)`
76:         (, address maintainer,,,,) = registry.getGovernanceAddresses(vaultId);

/// @audit `.getGovernanceAddresses(...)`
86:         (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);

```
*Github:* [[32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L32), [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L33), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L44), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L54), [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L66), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L76), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/NoyaGovernanceBase.sol#L86)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

/// @audit `.MAINTAINER_ROLE(...)`
25:         if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);

/// @audit `.hasRole(...)`
25:         if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);

```
*Github:* [[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L25), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L25)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

/// @audit `.MAINTAINER_ROLE(...)`
42:         if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);

/// @audit `.hasRole(...)`
42:         if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);

```
*Github:* [[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L42), [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L42)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

/// @audit `.MAINTAINER_ROLE(...)`
25:         if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);

/// @audit `.hasRole(...)`
25:         if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);

```
*Github:* [[25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L25), [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L25)]


</details>


<a name="L-34"></a> 
### [L-34] For loops in public or external functions should be avoided due to high gas costs and possible DOS
In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly.

<details>
<summary>
There are <b>22</b> instances (click to show):
</summary>

```solidity
File: ./contracts/accountingManager/AccountingManager.sol

548:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
             uint256 amountAskedForWithdraw_temp = 0;
             uint256 neededAssets = neededAssetsForWithdraw();
             for (uint256 i = 0; i < retrieveData.length; i++) {

596:     function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
             public
             view
             returns (DepositRequest[] memory depositData, WithdrawRequest[] memory withdrawData)
         {
             if (depositOrWithdraw) {
                 depositData = new DepositRequest[](items.length);
                 for (uint256 i = 0; i < items.length; i++) {

```
*Github:* [[548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L548), [596](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/AccountingManager.sol#L596)]


```solidity
File: ./contracts/accountingManager/Registry.sol

106:     function addVault(
             uint256 vaultId,
             address _accountingManager,
             address _baseToken,
             address _governer,
             address _maintainer,
             address _maintainerWithoutTimelock,
             address _keeperContract,
             address _watcher,
             address _emergency,
             address[] calldata _trustedTokens
         ) external onlyRole(MAINTAINER_ROLE) {
             if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();
             Vault storage vault = vaults[vaultId];
             require(_governer != address(0));
             require(_accountingManager != address(0));
             require(_baseToken != address(0));
             require(_maintainer != address(0));
             require(_keeperContract != address(0));
             require(_watcher != address(0));
     
             vault.accountManager = _accountingManager;
             vault.baseToken = _baseToken;
             vault.governer = _governer;
             vault.maintainer = _maintainer;
             vault.maintainerWithoutTimeLock = _maintainerWithoutTimelock;
             vault.keeperContract = _keeperContract;
             vault.watcherContract = _watcher;
             vault.emergency = _emergency;
             // Enable the accounting manager connector so the vault can use the "getValue" function of the accounting manager for calculating the value of tokens
             vault.connectors[vault.accountManager].enabled = true;
             vault.enabled = true;
             for (uint256 i = 0; i < _trustedTokens.length; i++) {

188:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
             external
             onlyVaultMaintainer(vaultId)
             vaultExists(vaultId)
         {
             Vault storage vault = vaults[vaultId];
             for (uint256 i = 0; i < _connectorAddresses.length; i++) {

207:     function updateConnectorTrustedTokens(
             uint256 vaultId,
             address _connectorAddress,
             address[] calldata _tokens,
             bool trusted
         ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
             Vault storage vault = vaults[vaultId];
             for (uint256 i = 0; i < _tokens.length; i++) {

```
*Github:* [[106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L106), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L188), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L207)]


```solidity
File: ./contracts/connectors/BalancerConnector.sol

53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
            for (uint256 i = 0; i < rewardsPools.length; i++) {

```
*Github:* [[53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerConnector.sol#L53)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

54:     function receiveFlashLoan(
            IERC20[] memory tokens,
            uint256[] memory amounts,
            uint256[] memory feeAmounts,
            bytes memory userData
        ) external override {
            emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
            require(msg.sender == address(vault));
            (
                uint256 vaultId,
                address receiver,
                address[] memory destinationConnector,
                bytes[] memory callingData,
                uint256[] memory gas
            ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
            (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
            if (!(caller == keeperContract)) {
                revert Unauthorized(caller);
            }
            if (registry.isAnActiveConnector(vaultId, receiver)) {
                for (uint256 i = 0; i < tokens.length; i++) {
                    // send the tokens to the receiver
                    tokens[i].safeTransfer(receiver, amounts[i]);
                    amounts[i] = amounts[i] + feeAmounts[i];
                }
                for (uint256 i = 0; i < destinationConnector.length; i++) {
                    // execute the transactions
                    (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
                    require(success, "BalancerFlashLoan: Flash loan failed");
                }
                for (uint256 i = 0; i < tokens.length; i++) {
                    // send the tokens back to this contract
                    BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
                }
            }
            for (uint256 i = 0; i < tokens.length; i++) {

```
*Github:* [[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54)]


```solidity
File: ./contracts/connectors/CurveConnector.sol

221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {
             for (uint256 i = 0; i < gauges.length; i++) {

233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {
             for (uint256 i = 0; i < pools.length; i++) {

247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
             for (uint256 i = 0; i < rewardsPools.length; i++) {

```
*Github:* [[221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L221), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L233), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/CurveConnector.sol#L247)]


```solidity
File: ./contracts/connectors/GearBoxV3.sol

62:     function executeCommands(
            address facade,
            address creditAccount,
            MultiCall[] calldata calls,
            address approvalToken,
            uint256 amount
        ) public onlyManager nonReentrant {
            for (uint256 i = 0; i < calls.length; i++) {

```
*Github:* [[62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/GearBoxV3.sol#L62)]


```solidity
File: ./contracts/connectors/UNIv3Connector.sol

101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
             for (uint256 i = 0; i < tokenIds.length; i++) {

```
*Github:* [[101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L101)]


```solidity
File: ./contracts/governance/Keepers.sol

27:     constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
            require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);
            for (uint256 i = 0; i < _owners.length; i++) {

42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
            uint256 numOwnersTemp = numOwners;
            for (uint256 i = 0; i < _owners.length; i++) {

```
*Github:* [[27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L27), [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
             external
             override
             nonReentrant
         {
             if (!registry.isAddressTrusted(vaultId, msg.sender)) {
                 revert IConnector_InvalidAddress(msg.sender);
             }
     
             for (uint256 i = 0; i < tokens.length; i++) {
                 // gather all of the tokens
                 uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
                 ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
                 uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
                 if (_balanceAfter < amounts[i] + _balance) {
                     revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
                 }
             }
             _addLiquidity(tokens, amounts, data); // call the specific implementation if the connector needs to do something after the liquidity is added
     
             for (uint256 i = 0; i < tokens.length; i++) {

204:     function swapHoldings(
             address[] memory tokensIn,
             address[] memory tokensOut,
             uint256[] memory amountsIn,
             bytes[] memory swapData,
             uint256[] memory routeIds
         ) external onlyManager nonReentrant {
             for (uint256 i = 0; i < tokensIn.length; i++) {

```
*Github:* [[169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L169), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
            for (uint256 i = 0; i < tokens.length; i++) {
                // gather all of the tokens
    
                ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
            }
            for (uint256 i = 0; i < tokens.length; i++) {

```
*Github:* [[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L40)]


```solidity
File: ./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
            NoyaGovernanceBase(_registry, _vaultId)
        {
            for (uint256 i = 0; i < usersAddresses.length; i++) {

147:     function addRoutes(RouteData[] memory _routes) public onlyMaintainer {
             for (uint256 i = 0; i < _routes.length;) {

```
*Github:* [[34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
            public
            onlyMaintainer
        {
            for (uint256 i = 0; i < baseCurrencies.length; i++) {

51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
            external
            onlyMaintainer
        {
            for (uint256 i = 0; i < oracle.length; i++) {

```
*Github:* [[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L51)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

70:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
            external
            onlyMaintainer
        {
            for (uint256 i = 0; i < assets.length; i++) {

```
*Github:* [[70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70)]


</details>


<a name="L-35"></a> 
### [L-35] Function with two (or more) array parameters missing a length check
In Solidity, if two array parameters are used within a function and one of their lengths is used as the for-loop range, it's essential to have a length check. If the arrays are not the same length, you could experience out-of-bounds errors or unintended behavior. This could happen if the function tries to access an index that doesn't exist in the shorter array.

Resolution: Always validate that the lengths of both arrays are the same before entering the loop. Add a require statement at the start of the function to check that both arrays are of equal length. This helps maintain the integrity of the function and prevents potential errors due to differing array lengths. This requirement ensures the function fails early if the arrays don't match, rather than failing unpredictably or silently during execution.

*There are <b>9</b> instances of this issue:*
```solidity
File: ./contracts/accountingManager/Registry.sol

188:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
             external
             onlyVaultMaintainer(vaultId)
             vaultExists(vaultId)
         {
             Vault storage vault = vaults[vaultId];
             for (uint256 i = 0; i < _connectorAddresses.length; i++) {

```
*Github:* [[188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/accountingManager/Registry.sol#L188)]


```solidity
File: ./contracts/connectors/BalancerFlashLoan.sol

54:     function receiveFlashLoan(
            IERC20[] memory tokens,
            uint256[] memory amounts,
            uint256[] memory feeAmounts,
            bytes memory userData
        ) external override {
            emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
            require(msg.sender == address(vault));
            (
                uint256 vaultId,
                address receiver,
                address[] memory destinationConnector,
                bytes[] memory callingData,
                uint256[] memory gas
            ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
            (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
            if (!(caller == keeperContract)) {
                revert Unauthorized(caller);
            }
            if (registry.isAnActiveConnector(vaultId, receiver)) {
                for (uint256 i = 0; i < tokens.length; i++) {

```
*Github:* [[54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/BalancerFlashLoan.sol#L54)]


```solidity
File: ./contracts/governance/Keepers.sol

42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
            uint256 numOwnersTemp = numOwners;
            for (uint256 i = 0; i < _owners.length; i++) {

```
*Github:* [[42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/governance/Keepers.sol#L42)]


```solidity
File: ./contracts/helpers/BaseConnector.sol

169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
             external
             override
             nonReentrant
         {
             if (!registry.isAddressTrusted(vaultId, msg.sender)) {
                 revert IConnector_InvalidAddress(msg.sender);
             }
     
             for (uint256 i = 0; i < tokens.length; i++) {

204:     function swapHoldings(
             address[] memory tokensIn,
             address[] memory tokensOut,
             uint256[] memory amountsIn,
             bytes[] memory swapData,
             uint256[] memory routeIds
         ) external onlyManager nonReentrant {
             for (uint256 i = 0; i < tokensIn.length; i++) {

```
*Github:* [[169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L169), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/BaseConnector.sol#L204)]


```solidity
File: ./contracts/helpers/ConnectorMock2.sol

40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
            for (uint256 i = 0; i < tokens.length; i++) {

```
*Github:* [[40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/ConnectorMock2.sol#L40)]


```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
            public
            onlyMaintainer
        {
            for (uint256 i = 0; i < baseCurrencies.length; i++) {

51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
            external
            onlyMaintainer
        {
            for (uint256 i = 0; i < oracle.length; i++) {

```
*Github:* [[37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L51)]


```solidity
File: ./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

70:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
            external
            onlyMaintainer
        {
            for (uint256 i = 0; i < assets.length; i++) {

```
*Github:* [[70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70)]



<a name="L-36"></a> 
### [L-36] Library has public/external functions
Libraries in Solidity are meant to be static collections of functions. They are deployed once and their code is reused by contracts through DELEGATECALL, which executes the library's code in the context of the calling contract. Public or external functions in libraries can be misleading because libraries are not supposed to maintain state or have external interactions in the way contracts do. Designing libraries with these kinds of functions goes against their intended purpose and can lead to confusion or misuse. For state management or external interactions, using contracts instead of libraries is more appropriate. Libraries should focus on utility functions that can operate on the data passed to them without side effects, enhancing code reuse and gas efficiency.

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/helpers/TVLHelper.sol

14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {

41:     function getLatestUpdateTime(uint256 vaultId, PositionRegistry registry) public view returns (uint256) {

```
*Github:* [[14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L14), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/TVLHelper.sol#L41)]



<a name="L-37"></a> 
### [L-37] No limits when setting price values
When setting price values without defined upper or lower bounds, it can lead to unpredictable behavior or potential vulnerabilities. For instance, overly high or low prices could be set maliciously or accidentally, disrupting platform functionality or enabling manipulative profit schemes. It's crucial to enforce constraints on price values to ensure they remain within a reasonable range. As a solution, implement checks to cap the minimum and maximum permissible price values. Additionally, consider implementing a governance mechanism or multi-signature approval process for significant price adjustments, ensuring an added layer of security and oversight.

*There is one instance of this issue:*
```solidity
File: ./contracts/helpers/valueOracle/NoyaValueOracle.sol

51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
            external
            onlyMaintainer
        {
            for (uint256 i = 0; i < oracle.length; i++) {
                priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
            }
            emit UpdatedAssetPriceSource(asset, baseToken, oracle);

```
*Github:* [[51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/helpers/valueOracle/NoyaValueOracle.sol#L51)]



<a name="L-38"></a> 
### [L-38] int/uint passed into abi.encodePacked without casting to a string
Not casting an integer as a string before passing it into abi.encode can result in unintended behaviour. lets say '1' being encoded as '1' it will be encoded as char(1) which is the 'start of heading' control character or id of 60 would be encoded as '<'. This is may not be intended. To rectify this, simply cast the Id as a string with string(id) or ideally use solmate's libString library (toString)

*There are <b>2</b> instances of this issue:*
```solidity
File: ./contracts/connectors/UNIv3Connector.sol

136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));

136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));

```
*Github:* [[136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L136), [136](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/./contracts/connectors/UNIv3Connector.sol#L136)]



