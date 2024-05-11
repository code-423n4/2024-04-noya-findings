## Low Findings

|        | Issue                                                                            |
| ------ | -------------------------------------------------------------------------------- |
| [L-01] | Unsafe ERC20 Operations should not be used                                       |
| [L-02] | Solidity pragma should be specific, not wide                                     |
| [L-03] | `public` functions not used internally could be marked `external`                |
| [L-04] | Missing checks for `address(0)` when assigning values to address state variables |
| [L-05] | The `nonReentrant` `modifier` should occur before all other modifiers            |
| [L-06] | Modifiers invoked only once can be shoe-horned into the function                 |
| [L-07] | Consider checking that transfer to `address(this)` is disabled                   |
| [L-08] | Unchecked Return Values of the `approve()` Function                              |
| [L-09] | Missing Contract-Existence Checks Before Low-Level Calls                         |
| [L-10] | Consider implementing two-step procedure for updating protocol addresses         |
| [L-11] | Empty `require()` / `revert()` statements                                        |
| [L-12] | Incorrect Order of Division and Multiplication                                   |

Total: 12 issues

## NonCritical Findings

|        | Issue                                                                                      |
| ------ | ------------------------------------------------------------------------------------------ |
| [N-01] | Event is missing `indexed` fields                                                          |
| [N-02] | Empty Block                                                                                |
| [N-03] | Contract still has TODOs                                                                   |
| [N-04] | Loop contains `require`/`revert` statements                                                |
| [N-05] | Define and use `constant` variables instead of using literals                              |
| [N-06] | Large literal values multiples of 10000 can be replaced with scientific notation           |
| [N-07] | Internal functions called only once can be inlined                                         |
| [N-08] | Dead code                                                                                  |
| [N-09] | Unused State Variable                                                                      |
| [N-10] | Style guide: Contract does not follow the Solidity style guide's suggested layout ordering |
| [N-12] | Unused state variables                                                                     |
| [N-13] | Consider using a struct rather than having many function input parameters                  |
| [N-14] | Consider using descriptive constants when passing zero as a function argument              |
| [N-15] | Custom error has no error details                                                          |
| [N-16] | Consider using OpenZeppelin's SafeCast for any casting                                     |
| [N-17] | Consider emitting an event at the end of the constructor                                   |
| [N-18] | Consider using named returns                                                               |
| [N-19] | Events are missing sender information                                                      |
| [N-20] | Leverage Recent Solidity Features with 0.8.23                                              |
| [N-21] | Outdated Solidity Version                                                                  |
| [N-22] | Non-uppercase/Constant-case Naming for immutable Variables                                 |
| [N-23] | Consider defining system-wide constants in a single file                                   |
| [N-24] | Style guide: Control structures do not follow the Solidity Style Guide                     |
| [N-25] | Consider using named mappings                                                              |
| [N-26] | Contracts should have full test coverage                                                   |
| [N-27] | Large or complicated code bases should implement invariant tests                           |

Total: 27 issues

## Low Findings Details

### [L-01] Unsafe ERC20 Operations should not be used

ERC20 functions may not behave as expected. For example: return values are not always meaningful. It is recommended to use OpenZeppelin's SafeERC20 library.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/LidoConnector.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/LidoConnector.sol#L71)

  ```solidity
          ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MaverickConnector.sol#L121)

  ```solidity
          position.approve(maverickRouter, p.tokenId);
  ```

</details>

### [L-02] Solidity pragma should be specific, not wide

Consider using a specific version of Solidity in your contracts instead of a wide version. For example, instead of `pragma solidity ^0.8.0;`, use `pragma solidity 0.8.0;`

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/interfaces/Aerodrome/IRouter.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Aerodrome/IRouter.sol#L2)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in contracts/external/interfaces/Aerodrome/IVoter.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Aerodrome/IVoter.sol#L2)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in contracts/external/interfaces/Balancer/IFlashLoanRecipient.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Balancer/IFlashLoanRecipient.sol#L15)

  ```solidity
  pragma solidity >=0.7.0 <0.9.0;
  ```

- Found in contracts/external/interfaces/Camelot/ICamelotFactory.sol [Line: 1](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Camelot/ICamelotFactory.sol#L1)

  ```solidity
  pragma solidity >=0.8.0;
  ```

- Found in contracts/external/interfaces/Camelot/ICamelotPair.sol [Line: 3](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Camelot/ICamelotPair.sol#L3)

  ```solidity
  pragma solidity >=0.8.20;
  ```

- Found in contracts/external/interfaces/Camelot/ICamelotRouter.sol [Line: 1](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Camelot/ICamelotRouter.sol#L1)

  ```solidity
  pragma solidity >=0.8.20;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 1](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L1)

  ```solidity
  pragma solidity >=0.6.0;
  ```

- Found in contracts/external/interfaces/Curve/IRewardsGauge.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/IRewardsGauge.sol#L4)

  ```solidity
  pragma solidity >=0.6.0 <0.9.0;
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L4)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol#L4)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3Multicall.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Gearbox/ICreditFacadeV3Multicall.sol#L4)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditManagerV3.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Gearbox/ICreditManagerV3.sol#L4)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in contracts/external/interfaces/Morpho/IIrm.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Morpho/IIrm.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/Morpho/IMorpho.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Morpho/IMorpho.sol#L4)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/Morpho/IOracle.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Morpho/IOracle.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/MorphoBlue/IIrm.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/MorphoBlue/IIrm.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/MorphoBlue/IMorpho.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/MorphoBlue/IMorpho.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/MorphoBlue/IOracle.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/MorphoBlue/IOracle.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/Pendle/IPActionSwapPTV3.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Pendle/IPActionSwapPTV3.sol#L2)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in contracts/external/interfaces/Pendle/IPActionSwapYTV3.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Pendle/IPActionSwapYTV3.sol#L2)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in contracts/external/interfaces/Pendle/IPAllActionTypeV3.sol [Line: 3](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Pendle/IPAllActionTypeV3.sol#L3)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in contracts/external/interfaces/Pendle/IPLimitRouter.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Pendle/IPLimitRouter.sol#L2)

  ```solidity
  pragma solidity ^0.8.0;
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 3](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L3)

  ```solidity
  pragma solidity ^0.8.4;
  ```

- Found in contracts/external/interfaces/Silo/IPriceProvider.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Silo/IPriceProvider.sol#L2)

  ```solidity
  pragma solidity >=0.7.6 <0.9.0;
  ```

- Found in contracts/external/interfaces/Silo/IPriceProvidersRepository.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Silo/IPriceProvidersRepository.sol#L2)

  ```solidity
  pragma solidity >=0.7.6 <0.9.0;
  ```

- Found in contracts/external/interfaces/UNIv3/IUniswapV3Factory.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/UNIv3/IUniswapV3Factory.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/interfaces/UNIv3/IUniswapV3Pool.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/UNIv3/IUniswapV3Pool.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/libraries/GearBox/BalancesLogic.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/GearBox/BalancesLogic.sol#L4)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in contracts/external/libraries/GearBox/BitMask.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/GearBox/BitMask.sol#L4)

  ```solidity
  pragma solidity ^0.8.17;
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/Math.sol#L15)

  ```solidity
  pragma solidity ^0.8.20;
  ```

- Found in contracts/external/libraries/uniswap/FixedPoint96.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/FixedPoint96.sol#L2)

  ```solidity
  pragma solidity >=0.4.0;
  ```

- Found in contracts/external/libraries/uniswap/FullMath.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/FullMath.sol#L2)

  ```solidity
  pragma solidity >=0.4.0;
  ```

- Found in contracts/external/libraries/uniswap/LiquidityAmounts.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/LiquidityAmounts.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L2)

  ```solidity
  pragma solidity >=0.5.0 <=0.8.20;
  ```

- Found in contracts/external/libraries/uniswap/PoolAddress.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/PoolAddress.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L2)

  ```solidity
  pragma solidity >=0.5.0;
  ```

</details>

### [L-03] `public` functions not used internally could be marked `external`

Instead of marking a function as `public`, consider marking it as `external` if it is not used internally.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/AccountingManager.sol [Line: 124](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L124)

```solidity
    function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {
```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 135](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L135)

  ```solidity
      function setFeeReceivers(
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 171](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L171)

  ```solidity
      function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 201](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L201)

  ```solidity
      function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 227](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L227)

  ```solidity
      function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 258](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L258)

  ```solidity
      function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 305](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L305)

  ```solidity
      function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 329](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L329)

  ```solidity
      function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 361](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L361)

  ```solidity
      function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 371](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L371)

  ```solidity
      function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 397](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L397)

  ```solidity
      function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 454](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L454)

  ```solidity
      function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 476](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L476)

  ```solidity
      function recordProfitForFee() public onlyManager nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 494](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L494)

  ```solidity
      function checkIfTVLHasDroped() public nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 507](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L507)

  ```solidity
      function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 528](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L528)

  ```solidity
      function collectPerformanceFees() public onlyManager nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 545](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L545)

  ```solidity
      function burnShares(uint256 amount) public {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 550](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L550)

  ```solidity
      function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 593](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L593)

  ```solidity
      function totalAssets() public view override returns (uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 598](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L598)

  ```solidity
      function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 636](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L636)

  ```solidity
      function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 653](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L653)

  ```solidity
      function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 663](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L663)

  ```solidity
      function emergencyStop() public whenNotPaused onlyEmergency {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 667](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L667)

  ```solidity
      function unpause() public whenPaused onlyEmergency {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 671](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L671)

  ```solidity
      function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 677](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L677)

  ```solidity
      function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 682](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L682)

  ```solidity
      function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 687](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L687)

  ```solidity
      function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 697](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L697)

  ```solidity
      function mint(uint256 shares, address receiver) public override returns (uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 701](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L701)

  ```solidity
      function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 705](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L705)

  ```solidity
      function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 709](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L709)

  ```solidity
      function deposit(uint256 assets, address receiver) public override returns (uint256) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 224](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L224)

  ```solidity
      function getPositionBP(uint256 vaultId, bytes32 _positionId) public view returns (PositionBP memory) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 394](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L394)

  ```solidity
      function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 408](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L408)

  ```solidity
      function getHoldingPosition(uint256 vaultId, uint256 i) public view returns (HoldingPI memory) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 416](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L416)

  ```solidity
      function getHoldingPositions(uint256 vaultId) public view returns (HoldingPI[] memory) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 426](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L426)

  ```solidity
      function isPositionTrusted(uint256 vaultId, bytes32 _positionId) public view returns (bool) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 449](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L449)

  ```solidity
      function getGovernanceAddresses(uint256 vaultId)
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 508](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L508)

  ```solidity
      function isPositionDebt(uint256 vaultId, bytes32 _positionId) public view returns (bool) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 516](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L516)

  ```solidity
      function getVaultAddresses(uint256 vaultId) public view returns (address, address) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 525](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L525)

  ```solidity
      function isAddressTrusted(uint256 vaultId, address addr) public view returns (bool) {
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 114](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AaveConnector.sol#L114)

  ```solidity
      function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 120](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AaveConnector.sol#L120)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L53)

  ```solidity
      function supply(DepositData memory data) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 79](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L79)

  ```solidity
      function withdraw(WithdrawData memory data) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 100](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L100)

  ```solidity
      function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 106](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L106)

  ```solidity
      function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 111](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L111)

  ```solidity
      function claim(address pool) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 117](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L117)

  ```solidity
      function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L125)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/BalancerConnector.sol#L53)

  ```solidity
      function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 64](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/BalancerConnector.sol#L64)

  ```solidity
      function openPosition(
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 109](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/BalancerConnector.sol#L109)

  ```solidity
      function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 115](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/BalancerConnector.sol#L115)

  ```solidity
      function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 162](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/BalancerConnector.sol#L162)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
  ```

- Found in contracts/connectors/CamelotConnector.sol [Line: 88](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CamelotConnector.sol#L88)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/CamelotConnector.sol [Line: 99](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CamelotConnector.sol#L99)

  ```solidity
      function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CompoundConnector.sol#L125)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 134](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CompoundConnector.sol#L134)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L68)

  ```solidity
      function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L81)

  ```solidity
      function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 103](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L103)

  ```solidity
      function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 117](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L117)

  ```solidity
      function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 160](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L160)

  ```solidity
      function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 182](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L182)

  ```solidity
      function withdrawFromConvexBooster(uint256 pid, uint256 amount) public onlyManager {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 192](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L192)

  ```solidity
      function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 202](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L202)

  ```solidity
      function withdrawFromGauge(address pool, uint256 amount) public onlyManager {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 212](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L212)

  ```solidity
      function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 221](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L221)

  ```solidity
      function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 233](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L233)

  ```solidity
      function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 247](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L247)

  ```solidity
      function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 265](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L265)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L30)

  ```solidity
      function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 43](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L43)

  ```solidity
      function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L58)

  ```solidity
      function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 77](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L77)

  ```solidity
      function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 98](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L98)

  ```solidity
      function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 106](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L106)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/FraxConnector.sol#L68)

  ```solidity
      function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 87](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/FraxConnector.sol#L87)

  ```solidity
      function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 142](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/FraxConnector.sol#L142)

  ```solidity
      function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 150](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/FraxConnector.sol#L150)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L24)

  ```solidity
      function openAccount(address facade, uint256 ref) public onlyManager {
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L41)

  ```solidity
      function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 62](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L62)

  ```solidity
      function executeCommands(
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 93](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L93)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 51](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/LidoConnector.sol#L51)

  ```solidity
      function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 69](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/LidoConnector.sol#L69)

  ```solidity
      function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 91](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/LidoConnector.sol#L91)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { public func
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 149](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MaverickConnector.sol#L149)

  ```solidity
      function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 153](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MaverickConnector.sol#L153)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 161](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MaverickConnector.sol#L161)

  ```solidity
      function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {

  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 95](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MorphoBlueConnector.sol#L95)

  ```solidity
      function repay(uint256 amount, Id id) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 118](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MorphoBlueConnector.sol#L118)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 141](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MorphoBlueConnector.sol#L141)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PancakeswapConnector.sol#L40)

  ```solidity
      function updatePosition(uint256 tokenId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 50](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PancakeswapConnector.sol#L50)

  ```solidity
      function withdraw(uint256 tokenId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 126](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L126)

  ```solidity
      function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 137](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L137)

  ```solidity
      function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 166](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L166)

  ```solidity
      function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 257](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L257)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 311](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L311)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L33)

  ```solidity
      function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 52](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L52)

  ```solidity
      function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 75](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L75)

  ```solidity
      function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 97](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L97)

  ```solidity
      function adjustTrove(
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 129](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L129)

  ```solidity
      function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 145](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L145)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 164](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L164)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L25)

  ```solidity
      function createAccount() public onlyManager {
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L30)

  ```solidity
      function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L46)

  ```solidity
      function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L68)

  ```solidity
      function delegateIntoPreferredPool(
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L81)

  ```solidity
      function delegateIntoApprovedPool(
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 94](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L94)

  ```solidity
      function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 102](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L102)

  ```solidity
      function mintOrBurnSUSD(
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L121)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 128](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L128)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L71)

  ```solidity
      function getData(address siloToken)
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 109](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L109)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 143](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L143)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 110](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/StargateConnector.sol#L110)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 123](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/StargateConnector.sol#L123)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 101](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/UNIv3Connector.sol#L101)

  ```solidity
      function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 127](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/UNIv3Connector.sol#L127)

  ```solidity
      function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 152](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/UNIv3Connector.sol#L152)

  ```solidity
      function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 47](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Silo/SolvencyV2.sol#L47)

  ```solidity
      function isSolvent(ISilo pool, address _user, uint256 liquidationThresholdMultilpier) public view returns (bool) {
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Silo/SolvencyV2.sol#L58)

  ```solidity
      function getData(ISilo pool, address _user, uint256 liquidationThresholdMultilpier)
  ```

- Found in contracts/governance/Keepers.sol [Line: 42](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L42)

  ```solidity
      function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
  ```

- Found in contracts/governance/Keepers.sol [Line: 63](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L63)

  ```solidity
      function setThreshold(uint8 _threshold) public onlyOwner {
  ```

- Found in contracts/governance/Keepers.sol [Line: 84](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L84)

  ```solidity
      function execute(
  ```

- Found in contracts/governance/Keepers.sol [Line: 124](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L124)

  ```solidity
      function domainSeparatorV4() public view returns (bytes32) {
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 154](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L154)

  ```solidity
      function updateTokenInRegistry(address token) public onlyManager {
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 233](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L233)

  ```solidity
      function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 250](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L250)

  ```solidity
      function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
  ```

- Found in contracts/helpers/ConnectorMock2.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/ConnectorMock2.sol#L71)

  ```solidity
      function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
  ```

- Found in contracts/helpers/ConnectorMock2.sol [Line: 75](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/ConnectorMock2.sol#L75)

  ```solidity
      function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40)

  ```solidity
      function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 52](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52)

  ```solidity
      function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L36)

  ```solidity
      function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 52](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L52)

  ```solidity
      function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 64](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L64)

  ```solidity
      function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 76](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L76)

  ```solidity
      function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 57](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57)

  ```solidity
      function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68)

  ```solidity
      function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol [Line: 52](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L52)

  ```solidity
      function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33)

  ```solidity
      function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 147](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147)

  ```solidity
      function addRoutes(RouteData[] memory _routes) public onlyMaintainer {
  ```

- Found in contracts/helpers/TVLHelper.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/TVLHelper.sol#L14)

  ```solidity
      function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
  ```

- Found in contracts/helpers/TVLHelper.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/TVLHelper.sol#L41)

  ```solidity
      function getLatestUpdateTime(uint256 vaultId, PositionRegistry registry) public view returns (uint256) {
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L37)

  ```solidity
      function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71)

  ```solidity
      function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
  ```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 89](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L89)

  ```solidity
      function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
  ```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 60](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60)

  ```solidity
      function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) {
  ```

  </details>

### [L-04] Missing checks for `address(0)` when assigning values to address state variables

State variables that are of type address should always be checked to ensure that they are not being assigned the null address (address(0x0)). A null address often implies an error or omission in the code. Without proper checks, such a scenario can lead to unexpected behavior and potential vulnerabilities in the smart contract.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/AccountingManager.sol [Line: 311](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L311)

  ```solidity
          withdrawRequestsByAddress[msg.sender] += share;
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 76](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L76)

  ```solidity
          flashLoan = _flashLoan;
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 86](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L86)

  ```solidity
          flashLoan = _flashLoan;
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 45](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/AerodromeConnector.sol#L45)

  ```solidity
          voter = IVoter(_voter);
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L26)

  ```solidity
          dolomiteMargin = IDolomiteMargin(_dolomiteMargin);
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/Dolomite.sol#L27)

  ```solidity
          borrowPositionProxy = IBorrowPositionProxyV1(_borrowPositionProxy);
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 34](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L34)

  ```solidity
          swapHandler = params.swapHandler;
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L35)

  ```solidity
          valueOracle = params.valueOracle;
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 59](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L59)

  ```solidity
          swapHandler = SwapAndBridgeHandler(_swapHandler);
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L68)

  ```solidity
          valueOracle = INoyaValueOracle(_valueOracle);
  ```

- Found in contracts/helpers/ConnectorMock2.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/ConnectorMock2.sol#L23)

  ```solidity
          registry = PositionRegistry(_registry);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 49](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L49)

  ```solidity
          valueOracle = INoyaValueOracle(_valueOracle);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 72](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L72)

  ```solidity
          slippageTolerance[_inputToken][_outputToken] = _slippageTolerance;
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L29)

  ```solidity
          lifi = _lifi;
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L46)

  ```solidity
          isHandler[_handler] = state;
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 42](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L42)

  ```solidity
              defaultPriceSource[baseCurrencies[i]] = oracles[i];
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 56](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L56)

  ```solidity
              priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 62](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L62)

  ```solidity
          priceRoutes[asset][base] = s;
  ```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 75](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75)

  ```solidity
              assetsSources[assets[i]][baseTokens[i]] = sources[i];
  ```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 32](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L32)

  ```solidity
          factory = _factory;
  ```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L33)

  ```solidity
          registry = _registry;
  ```

</details>

### [L-05] The `nonReentrant` `modifier` should occur before all other modifiers

This is recommended way to protect against reentrancy in other modifiers.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/AccountingManager.sol [Line: 227](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L227)

  ```solidity
      function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 262](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L262)

  ```solidity
          nonReentrant
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 329](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L329)

  ```solidity
      function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 361](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L361)

  ```solidity
      function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 371](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L371)

  ```solidity
      function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 397](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L397)

  ```solidity
      function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 476](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L476)

  ```solidity
      function recordProfitForFee() public onlyManager nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 507](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L507)

  ```solidity
      function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 528](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L528)

  ```solidity
      function collectPerformanceFees() public onlyManager nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 550](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L550)

  ```solidity
      function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 687](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L687)

  ```solidity
      function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 246](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L246)

  ```solidity
      ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L46)

  ```solidity
      function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L65)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L81)

  ```solidity
      function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L100)

  ```solidity
      function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L53)

  ```solidity
      function supply(DepositData memory data) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L79)

  ```solidity
      function withdraw(WithdrawData memory data) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L100)

  ```solidity
      function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L106)

  ```solidity
      function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L111)

  ```solidity
      function claim(address pool) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L53)

  ```solidity
      function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L70)

  ```solidity
      ) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L109)

  ```solidity
      function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L115)

  ```solidity
      function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CamelotConnector.sol [Line: 43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L43)

  ```solidity
      function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CamelotConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L68)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L29)

  ```solidity
      function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L48)

  ```solidity
      function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L63)

  ```solidity
      function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L68)

  ```solidity
      function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L81)

  ```solidity
      function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L120)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 163](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L163)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L221)

  ```solidity
      function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L233)

  ```solidity
      function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L247)

  ```solidity
      function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L30)

  ```solidity
      function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L43)

  ```solidity
      function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L61)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L80)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L98)

  ```solidity
      function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L41)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L68)

  ```solidity
      function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L87)

  ```solidity
      function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L41)

  ```solidity
      function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L68)

  ```solidity
      ) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L37)

  ```solidity
      function deposit(uint256 amountIn) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L51)

  ```solidity
      function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L69)

  ```solidity
      function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L64)

  ```solidity
      function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L78)

  ```solidity
      function unstake(uint256 lockupId) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L91)

  ```solidity
      function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L118)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L137)

  ```solidity
      function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L35)

  ```solidity
      function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L58)

  ```solidity
      function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L80)

  ```solidity
      function borrow(uint256 amount, Id id) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L95)

  ```solidity
      function repay(uint256 amount, Id id) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L31)

  ```solidity
      function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L40)

  ```solidity
      function updatePosition(uint256 tokenId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L50)

  ```solidity
      function withdraw(uint256 tokenId) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L78)

  ```solidity
      function supply(address market, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L97)

  ```solidity
      function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L112)

  ```solidity
      function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L126)

  ```solidity
      function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L137)

  ```solidity
      function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 186](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L186)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L203)

  ```solidity
      function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L216)

  ```solidity
      function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L241)

  ```solidity
      function claimRewards(IPMarket market) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L33)

  ```solidity
      function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L55)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L75)

  ```solidity
      function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L104)

  ```solidity
      ) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L129)

  ```solidity
      function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L33)

  ```solidity
      function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L55)

  ```solidity
          nonReentrant
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L85)

  ```solidity
      function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L98)

  ```solidity
      function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L49)

  ```solidity
      function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L76)

  ```solidity
      function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L103)

  ```solidity
      function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L40)

  ```solidity
      function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L63)

  ```solidity
      function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L87)

  ```solidity
      function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L101)

  ```solidity
      function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 128](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L128)

  ```solidity
      ) external onlyManager nonReentrant {
  ```

- Found in contracts/helpers/BaseConnector.sol [Line: 211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L211)

  ```solidity
      ) external onlyManager nonReentrant {
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68)

  ```solidity
      function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L95)

  ```solidity
          nonReentrant
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 131](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L131)

  ```solidity
          nonReentrant
  ```

  </details>

### [L-06] Modifiers invoked only once can be shoe-horned into the function

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/Registry.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L39)

  ```solidity
      modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) {
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L46)

  ```solidity
      modifier onlyVaultGoverner(uint256 _vaultId) {
  ```

</details>

### [L-07] Consider checking that transfer to `address(this)` is disabled

Functions allowing users to specify the receiving address should check whether the referenced address is not `address(this)`. This would prevent tokens to remain lock inside the contract due to an incorrect transfer or mint.

### [L-08] Unchecked Return Values of the `approve()` function

The unchecked return value of the `approve()` method can potentially cause transaction failures to go unnoticed in your contract.

Some IERC20 token implementations utilize boolean return values to indicate transaction failures, instead of relying on the `revert()` function. If the return value of the `approve()` method isn't appropriately verified, transactions may seemingly proceed even when the necessary token approvals have not been appropriately executed.

As a safeguard, it is crucial to consistently verify the return values of these methods. This helps to ensure the correct execution of token approvals, maintaining the integrity of transaction operations and reducing the risk of unnoticed transaction failures.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/MaverickConnector.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol#L121)

```solidity
position.approve(maverickRouter, p.tokenId);
```

- Found in contracts/connectors/LidoConnector.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/LidoConnector.sol#L71)

```solidity
ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);
```

</details>

### [L-09] Missing Contract-Existence Checks Before Low-Level Calls

When making low-level calls, it's crucial to ensure the existence of the contract at the specified address. If the contract doesn't exist at the given address, low-level calls will still return success, potentially causing errors in the code execution. Therefore, alongside zero-address checks, adding an additional check to verify that

.code.length > 0 before making low-level calls would be recommended.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol#L81)

```solidity
(bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
```

- Found in contracts/connectors/GearBoxV3.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol#L71)

```solidity
bytes4 method = bytes4(calls[i].callData[:4]);
```

- Found in contracts/connectors/GearBoxV3.sol [Line: 74](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol#L74)

```solidity
(address token) = abi.decode(calls[i].callData[4:], (address));
```

- Found in contracts/governance/Keepers.sol [Line: 116](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L116)

```solidity
(bool success,) = destination.call{ gas: gasLimit }(data);
```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 689](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L689)

```solidity
(bool success,) = payable(msg.sender).call{ value: amount }("");
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 176](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176)

```solidity
(bool success, bytes memory err) = lifi.call{ value: msg.value }(data);
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 195](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195)

```solidity
(bool success,) = payable(userAddress).call{ value: amount }("");
```

</details>

### [L-10] Consider implementing two-step procedure for updating protocol addresses

Direct state address changes in a function can be risky, as they don't allow for a verification step before the change is made. It's safer to implement a two-step process where the new address is first proposed, then later confirmed, allowing for more control and the chance to catch errors or malicious activity.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/PrismaConnector.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L41)

</details>

### [L-11] Empty `require()` / `revert()` statements

Use descriptive reason strings or custom errors for revert paths.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/AccountingManager.sol [Line: 106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L106)

  ```solidity
          require(p._baseTokenAddress != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L107)

  ```solidity
          require(p._valueOracle != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 108](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L108)

  ```solidity
          require(p._withdrawFeeReceiver != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L110)

  ```solidity
          require(p._managementFeeReceiver != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L125)

  ```solidity
          require(address(_valueOracle) != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L140)

  ```solidity
          require(_withdrawFeeReceiver != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 141](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L141)

  ```solidity
          require(_performanceFeeReceiver != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 142](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L142)

  ```solidity
          require(_managementFeeReceiver != address(0));
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 362](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L362)

  ```solidity
          require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 372](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L372)

  ```solidity
          require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
  ```

- Found in contracts/accountingManager/NoyaFeeReceiver.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L15)

  ```solidity
          require(_accountingManager != address(0));
  ```

- Found in contracts/accountingManager/NoyaFeeReceiver.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L16)

  ```solidity
          require(_baseToken != address(0));
  ```

- Found in contracts/accountingManager/NoyaFeeReceiver.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L17)

  ```solidity
          require(_receiver != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L67)

  ```solidity
          require(_governer != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L68)

  ```solidity
          require(_maintainer != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L69)

  ```solidity
          require(_emergency != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L80)

  ```solidity
          require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L121)

  ```solidity
          require(_accountingManager != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L122)

  ```solidity
          require(_baseToken != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 123](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L123)

  ```solidity
          require(_maintainer != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L124)

  ```solidity
          require(_keeperContract != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L125)

  ```solidity
          require(_watcher != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L159)

  ```solidity
          uint256 vaultId,
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 167](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L167)

  ```solidity
          require(_governer != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 168](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L168)

  ```solidity
          require(_maintainer != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L169)

  ```solidity
          require(_keeperContract != address(0));
  ```

- Found in contracts/accountingManager/Registry.sol [Line: 170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L170)

  ```solidity
          require(_watcher != address(0));
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L36)

  ```solidity
          require(_pool != address(0));
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L37)

  ```solidity
          require(_poolBaseToken != address(0));
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L43)

  ```solidity
          require(_router != address(0));
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L45)

  ```solidity
          require(_balancerVault != address(0));
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L46)

  ```solidity
          require(bal != address(0));
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L47)

  ```solidity
          require(aura != address(0));
  ```

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L25)

  ```solidity
          require(_balancerVault != address(0));
  ```

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L26)

  ```solidity
          require(address(_registry) != address(0));
  ```

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L61)

  ```solidity
          require(msg.sender == address(vault));
  ```

- Found in contracts/connectors/CamelotConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L37)

  ```solidity
          require(_router != address(0));
  ```

- Found in contracts/connectors/CamelotConnector.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L38)

  ```solidity
          require(_factory != address(0));
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L52)

  ```solidity
          require(_convexBooster != address(0));
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L53)

  ```solidity
          require(cvx != address(0));
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L54)

  ```solidity
          require(crv != address(0));
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L55)

  ```solidity
          require(prisma != address(0));
  ```

- Found in contracts/connectors/Dolomite.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L24)

  ```solidity
          require(_depositWithdrawalProxy != address(0));
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L23)

  ```solidity
          require(_lido != address(0));
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L24)

  ```solidity
          require(_lidoW != address(0));
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L25)

  ```solidity
          require(_steth != address(0));
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L26)

  ```solidity
          require(w != address(0));
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L46)

  ```solidity
          require(_mav != address(0));
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L47)

  ```solidity
          require(_veMav != address(0));
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L48)

  ```solidity
          require(mr != address(0));
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L49)

  ```solidity
          require(pi != address(0));
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L24)

  ```solidity
          require(MB != address(0));
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L22)

  ```solidity
          require(MC != address(0));
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L60)

  ```solidity
          require(_pendleMarketDepositHelper != address(0));
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L61)

  ```solidity
          require(_pendleRouter != address(0));
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L62)

  ```solidity
          require(SR != address(0));
  ```

- Found in contracts/connectors/SNXConnector.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L21)

  ```solidity
          require(_SNXCoreProxy != address(0));
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L18)

  ```solidity
          require(SR != address(0));
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L36)

  ```solidity
          require(lpStacking != address(0));
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L37)

  ```solidity
          require(_stargateRouter != address(0));
  ```

- Found in contracts/external/libraries/GearBox/BitMask.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/GearBox/BitMask.sol#L18)

  ```solidity
          if (mask == 0) revert(); // U:[BM-1]
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L117)

  ```solidity
          require(x <= uint256(type(int256).max));
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L122)

  ```solidity
          require(type(int128).min <= x && x <= type(int128).max);
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L135)

  ```solidity
          require(x >= 0);
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L140)

  ```solidity
          require(x <= type(uint32).max);
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L145)

  ```solidity
          require(x <= type(uint112).max);
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L150)

  ```solidity
          require(x <= type(uint96).max);
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 155](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/Math.sol#L155)

  ```solidity
          require(x <= type(uint128).max);
  ```

- Found in contracts/external/libraries/uniswap/FullMath.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/FullMath.sol#L30)

  ```solidity
              require(denominator > 0);
  ```

- Found in contracts/external/libraries/uniswap/FullMath.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/FullMath.sol#L39)

  ```solidity
          require(denominator > prod1);
  ```

- Found in contracts/external/libraries/uniswap/FullMath.sol [Line: 112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/FullMath.sol#L112)

  ```solidity
              require(result < type(uint256).max);
  ```

- Found in contracts/external/libraries/uniswap/LiquidityAmounts.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/LiquidityAmounts.sol#L14)

  ```solidity
          require((y = uint128(x)) == x);
  ```

- Found in contracts/external/libraries/uniswap/PoolAddress.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/PoolAddress.sol#L30)

  ```solidity
          require(key.token0 < key.token1);
  ```

- Found in contracts/governance/Keepers.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L28)

  ```solidity
          require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);
  ```

- Found in contracts/governance/Keepers.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L53)

  ```solidity
          require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
  ```

- Found in contracts/governance/Keepers.sol [Line: 64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L64)

  ```solidity
          require(_threshold <= numOwners && _threshold > 1);
  ```

- Found in contracts/governance/Keepers.sol [Line: 106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L106)

  ```solidity
                  require(recovered > lastAdd && isOwner[recovered]);
  ```

- Found in contracts/governance/NoyaGovernanceBase.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L22)

  ```solidity
          require(address(_registry) != address(0));
  ```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L41)

  ```solidity
          require(lzHelperAddress != address(0));
  ```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L53)

  ```solidity
          require(omniChainManager != address(0));
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L53)

  ```solidity
          require(lzHelperAddress != address(0));
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L37)

  ```solidity
          require(_lzHelper != address(0));
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L47)

  ```solidity
          require(destinationAddress != address(0));
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L41)

  ```solidity
          require(_valueOracle != address(0));
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L30)

  ```solidity
          require(address(_registry) != address(0));
  ```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L47)

  ```solidity
          require(_reg != address(0));
  ```

</details>

### [L-12] Incorrect Order of Division and Multiplication

Division operations followed directly by multiplication operations can lead to precision loss due to the way integer arithmetic is handled in Solidity.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 317](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Silo/SolvencyV2.sol#L317)

```solidity
            + _assetTotalBorrows * _rcomp / _PRECISION_DECIMALS * depositorsShare / _PRECISION_DECIMALS;
```

</details>

## Non-Critical Findings Details

### [N-01] Event is missing `indexed` fields

Index event fields make the field more quickly accessible to off-chain tools that parse events. However, note that each index field costs extra gas during emission, so it's not necessarily to index the maximum allowed per event (three fields). Each event should use three indexed fields if there are three or more fields, and gas usage is not particularly of concern for the events in question. If there are fewer than three fields, all of the fields should be indexed.

<details>
<summary><i>Instances</i></summary>
- Found in contracts/accountingManager/NoyaFeeReceiver.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L12)

```solidity
    event ManagementFeeReceived(address indexed token, uint256 amount);
```

- Found in contracts/connectors/AaveConnector.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L26)

  ```solidity
      event Supply(address supplyToken, uint256 amount);
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L27)

  ```solidity
      event Borrow(address borrowToken, uint256 amount);
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L28)

  ```solidity
      event Repay(address repayToken, uint256 amount, uint256 i);
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L29)

  ```solidity
      event RepayWithCollateral(address repayToken, uint256 amount, uint256 i);
  ```

- Found in contracts/connectors/AaveConnector.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L30)

  ```solidity
      event WithdrawCollateral(address collateral, uint256 amount);
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L36)

  ```solidity
      event Supply(address pool, uint256 amount0, uint256 amount1);
  ```

- Found in contracts/connectors/AerodromeConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L37)

  ```solidity
      event Withdraw(address pool, uint256 amountLiquidity);
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L34)

  ```solidity
      event OpenPosition(
  ```

- Found in contracts/connectors/BalancerConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L37)

  ```solidity
      event DecreasePosition(DecreasePositionParams p);
  ```

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L21)

  ```solidity
      event MakeFlashLoan(IERC20[] tokens, uint256[] amounts);
  ```

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L22)

  ```solidity
      event ReceiveFlashLoan(IERC20[] tokens, uint256[] amounts, uint256[] feeAmounts, bytes userData);
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L10)

  ```solidity
      event Supply(address market, address asset, uint256 amount);
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L11)

  ```solidity
      event WithdrawOrBorrow(address market, address asset, uint256 amount);
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L12)

  ```solidity
      event ClaimRewards(address rewardContract, address market);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L33)

  ```solidity
      event OpenCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L34)

  ```solidity
      event DecreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L35)

  ```solidity
      event WithdrawFromConvexBooster(uint256 pid, uint256 amount);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L36)

  ```solidity
      event WithdrawFromConvexRewardPool(address pool, uint256 amount);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L37)

  ```solidity
      event WithdrawFromGauge(address pool, uint256 amount);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L38)

  ```solidity
      event WithdrawFromPrisma(address depostiToken, uint256 amount);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L39)

  ```solidity
      event HarvestRewards(address[] gauges);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L40)

  ```solidity
      event HarvestPrismaRewards(address[] pools);
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L41)

  ```solidity
      event HarvestConvexRewards(address[] rewardsPools);
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L24)

  ```solidity
      event BorrowAndSupply(address pool, uint256 borrowAmount, uint256 collateralAmount);
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L25)

  ```solidity
      event Withdraw(address pool, uint256 withdrawAmount);
  ```

- Found in contracts/connectors/FraxConnector.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L26)

  ```solidity
      event Repay(address pool, uint256 sharesToRepay);
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L11)

  ```solidity
      event OpenAccount(address facade, uint256 ref);
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L12)

  ```solidity
      event CloseAccount(address facade, address creditAccount);
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L13)

  ```solidity
      event ExecuteCommands(
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L15)

  ```solidity
      event Deposit(uint256 amountIn);
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L16)

  ```solidity
      event RequestWithdrawals(uint256 amount);
  ```

- Found in contracts/connectors/LidoConnector.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L17)

  ```solidity
      event ClaimWithdrawal(uint256 requestId);
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L37)

  ```solidity
      event Stake(uint256 amount, uint256 duration, bool doDelegation);
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L38)

  ```solidity
      event Unstake(uint256 lockupId);
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L39)

  ```solidity
      event AddLiquidityInMaverickPool(MavericAddLiquidityParams p);
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L40)

  ```solidity
      event RemoveLiquidityFromMaverickPool(MavericRemoveLiquidityParams p);
  ```

- Found in contracts/connectors/MaverickConnector.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L41)

  ```solidity
      event ClaimBoostedPositionRewards(IMaverickReward rewardContract);
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L17)

  ```solidity
      event Supply(uint256 amount, Id id, bool sOrC);
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L18)

  ```solidity
      event Withdraw(uint256 amount, Id id, bool sOrC);
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L19)

  ```solidity
      event Borrow(uint256 amount, Id id);
  ```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L20)

  ```solidity
      event Repay(uint256 amount, Id id);
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L14)

  ```solidity
      event SendPositionToMasterChef(uint256 tokenId);
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L15)

  ```solidity
      event UpdatePosition(uint256 tokenId);
  ```

- Found in contracts/connectors/PancakeswapConnector.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L16)

  ```solidity
      event Withdraw(uint256 tokenId);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L35)

  ```solidity
      event Supply(address market, uint256 amount);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L36)

  ```solidity
      event MintPTAndYT(address market, uint256 syAmount);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L37)

  ```solidity
      event DepositIntoMarket(address market, uint256 SYamount, uint256 PTamount);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L38)

  ```solidity
      event DepositIntoPenpie(address market, uint256 amount);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L39)

  ```solidity
      event WithdrawFromPenpie(address market, uint256 amount);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L40)

  ```solidity
      event SwapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams guess);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L41)

  ```solidity
      event SwapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData orderData);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L42)

  ```solidity
      event SwapExactPTForSY(address market, uint256 exactPTIn, bytes swapData, uint256 minSY);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L43)

  ```solidity
      event BurnLP(address market, uint256 amount);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L44)

  ```solidity
      event DecreasePosition(address market, uint256 amount, bool closePosition);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L45)

  ```solidity
      event ClaimRewards(address market);
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L16)

  ```solidity
      event OpenTrove(address zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount);
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L17)

  ```solidity
      event AddColl(address zap, address tm, uint256 amountIn);
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L18)

  ```solidity
      event AdjustTrove(address zap, address tm, uint256 mFee, uint256 wAmount, uint256 bAmount, bool isBorrowing);
  ```

- Found in contracts/connectors/PrismaConnector.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L19)

  ```solidity
      event CloseTrove(address zap, address troveManager);
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L12)

  ```solidity
      event Deposit(address siloToken, address dToken, uint256 amount, bool oC);
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L13)

  ```solidity
      event Withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition);
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L14)

  ```solidity
      event Borrow(address siloToken, address bToken, uint256 amount);
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L15)

  ```solidity
      event Repay(address siloToken, address rToken, uint256 amount);
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L28)

  ```solidity
      event DepositIntoStargatePool(StargateRequest depositRequest);
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L29)

  ```solidity
      event WithdrawFromStargatePool(StargateRequest withdrawRequest);
  ```

- Found in contracts/connectors/StargateConnector.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L30)

  ```solidity
      event ClaimStargateRewards(uint256 poolId);
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L21)

  ```solidity
      event OpenPosition(MintParams p, uint256 tokenId);
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L22)

  ```solidity
      event DecreasePosition(DecreaseLiquidityParams p);
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L23)

  ```solidity
      event IncreasePosition(IncreaseLiquidityParams p);
  ```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L24)

  ```solidity
      event CollectFees(uint256 tokenId);
  ```

- Found in contracts/external/interfaces/Aerodrome/IGauge.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IGauge.sol#L12)

  ```solidity
      event Deposit(address indexed from, address indexed to, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IGauge.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IGauge.sol#L13)

  ```solidity
      event Withdraw(address indexed from, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IGauge.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IGauge.sol#L14)

  ```solidity
      event NotifyReward(address indexed from, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IGauge.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IGauge.sol#L15)

  ```solidity
      event ClaimFees(address indexed from, uint256 claimed0, uint256 claimed1);
  ```

- Found in contracts/external/interfaces/Aerodrome/IGauge.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IGauge.sol#L16)

  ```solidity
      event ClaimRewards(address indexed from, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IVoter.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IVoter.sol#L58)

  ```solidity
      event NotifyReward(address indexed sender, address indexed reward, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IVoter.sol [Line: 59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Aerodrome/IVoter.sol#L59)

  ```solidity
      event DistributeReward(address indexed sender, address indexed gauge, uint256 amount);
  ```

- Found in contracts/external/interfaces/Camelot/ICamelotFactory.sol [Line: 4](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Camelot/ICamelotFactory.sol#L4)

  ```solidity
      event PairCreated(address indexed token0, address indexed token1, address pair, uint256);
  ```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L36)

  ```solidity
      event Approval(address indexed owner, address indexed spender, uint256 value);
  ```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L38)

  ```solidity
      event Transfer(address indexed from, address indexed to, uint256 value);
  ```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L40)

  ```solidity
      event Mint(address indexed sender, uint256 amount0Wei, uint256 amount1Wei);
  ```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L42)

  ```solidity
      event Burn(address indexed sender, uint256 amount0Wei, uint256 amount1Wei, address indexed to);
  ```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L44)

  ```solidity
      event Swap(
  ```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L53)

  ```solidity
      event Sync(uint112 reserve0, uint112 reserve1);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L46)

  ```solidity
      event SetTokenLiquidationThreshold(address indexed token, uint16 liquidationThreshold);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L49)

  ```solidity
      event ScheduleTokenLiquidationThresholdRamp(
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L81)

  ```solidity
      event SetMaxEnabledTokens(uint8 maxEnabledTokens);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L84)

  ```solidity
      event UpdateFees(
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L113)

  ```solidity
      event SetBorrowingLimits(uint256 minDebt, uint256 maxDebt);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L116)

  ```solidity
      event SetMaxDebtPerBlockMultiplier(uint8 maxDebtPerBlockMultiplier);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L119)

  ```solidity
      event SetMaxCumulativeLoss(uint128 maxCumulativeLoss);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditConfiguratorV3.sol#L125)

  ```solidity
      event SetExpirationDate(uint40 expirationDate);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol#L53)

  ```solidity
      event LiquidateCreditAccount(
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol#L58)

  ```solidity
      event IncreaseDebt(address indexed creditAccount, uint256 amount);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol#L61)

  ```solidity
      event DecreaseDebt(address indexed creditAccount, uint256 amount);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol [Line: 64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol#L64)

  ```solidity
      event AddCollateral(address indexed creditAccount, address indexed token, uint256 amount);
  ```

- Found in contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol [Line: 67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Gearbox/ICreditFacadeV3.sol#L67)

  ```solidity
      event WithdrawCollateral(address indexed creditAccount, address indexed token, uint256 amount, address to);
  ```

- Found in contracts/external/interfaces/Pendle/IPMarket.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPMarket.sol#L13)

  ```solidity
      event Mint(address indexed receiver, uint256 netLpMinted, uint256 netSyUsed, uint256 netPtUsed);
  ```

- Found in contracts/external/interfaces/Pendle/IPMarket.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPMarket.sol#L15)

  ```solidity
      event Burn(
  ```

- Found in contracts/external/interfaces/Pendle/IPMarket.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPMarket.sol#L19)

  ```solidity
      event Swap(
  ```

- Found in contracts/external/interfaces/Pendle/IPMarket.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPMarket.sol#L28)

  ```solidity
      event UpdateImpliedRate(uint256 indexed timestamp, uint256 lnLastImpliedRate);
  ```

- Found in contracts/external/interfaces/Pendle/IPMarket.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPMarket.sol#L30)

  ```solidity
      event IncreaseObservationCardinalityNext(
  ```

- Found in contracts/external/interfaces/Pendle/IPPtOracle.sol [Line: 5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPPtOracle.sol#L5)

  ```solidity
      event SetBlockCycleNumerator(uint16 newBlockCycleNumerator);
  ```

- Found in contracts/external/interfaces/Pendle/IPStandardizedYield.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPStandardizedYield.sol#L33)

  ```solidity
      event ClaimRewards(address indexed user, address[] rewardTokens, uint256[] rewardAmounts);
  ```

- Found in contracts/external/interfaces/Pendle/IPYieldToken.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Pendle/IPYieldToken.sol#L21)

  ```solidity
      event Burn(address indexed caller, address indexed receiver, uint256 amountPYToRedeem, uint256 amountSyOut);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L13)

  ```solidity
      event OwnerChanged(address oldOwner, address newOwner);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L14)

  ```solidity
      event OwnerNominated(address newOwner);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L15)

  ```solidity
      event Upgraded(address indexed self, address implementation);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L35)

  ```solidity
      event FeatureFlagAllowAllSet(bytes32 indexed feature, bool allowAll);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L36)

  ```solidity
      event FeatureFlagAllowlistAdded(bytes32 indexed feature, address account);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L37)

  ```solidity
      event FeatureFlagAllowlistRemoved(bytes32 indexed feature, address account);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L38)

  ```solidity
      event FeatureFlagDeniersReset(bytes32 indexed feature, address[] deniers);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L39)

  ```solidity
      event FeatureFlagDenyAllSet(bytes32 indexed feature, bool denyAll);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L150)

  ```solidity
      event AssociatedSystemSet(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L190)

  ```solidity
      event CollateralLockCreated(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 196](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L196)

  ```solidity
      event CollateralLockExpired(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 250](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L250)

  ```solidity
      event CollateralConfigured(address indexed collateralType, CollateralConfiguration.Data config);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L266)

  ```solidity
      event IssuanceFeePaid(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 319](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L319)

  ```solidity
      event VaultLiquidation(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 415](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L415)

  ```solidity
      event MarketSystemFeePaid(uint128 indexed marketId, uint256 feeAmount);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L428)

  ```solidity
      event SetMarketMinLiquidityRatio(uint128 indexed marketId, uint256 minLiquidityRatio);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 429](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L429)

  ```solidity
      event SetMinDelegateTime(uint128 indexed marketId, uint32 minDelegateTime);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 480](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L480)

  ```solidity
      event PoolApprovedAdded(uint256 poolId);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 481](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L481)

  ```solidity
      event PoolApprovedRemoved(uint256 poolId);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 482](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L482)

  ```solidity
      event PreferredPoolSet(uint256 poolId);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 497](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L497)

  ```solidity
      event PoolConfigurationSet(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 503](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L503)

  ```solidity
      event PoolNameUpdated(uint128 indexed poolId, string name, address indexed sender);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 512](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L512)

  ```solidity
      event SetMinLiquidityRatio(uint256 minLiquidityRatio);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 557](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L557)

  ```solidity
      event RewardsDistributed(
  ```

- Found in contracts/external/interfaces/Silo/IBaseSilo.sol [Line: 75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/IBaseSilo.sol#L75)

  ```solidity
      event Deposit(address indexed asset, address indexed depositor, uint256 amount, bool collateralOnly);
  ```

- Found in contracts/external/interfaces/Silo/IBaseSilo.sol [Line: 91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/IBaseSilo.sol#L91)

  ```solidity
      event Borrow(address indexed asset, address indexed user, uint256 amount);
  ```

- Found in contracts/external/interfaces/Silo/IBaseSilo.sol [Line: 97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/IBaseSilo.sol#L97)

  ```solidity
      event Repay(address indexed asset, address indexed user, uint256 amount);
  ```

- Found in contracts/external/interfaces/Silo/IBaseSilo.sol [Line: 105](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/IBaseSilo.sol#L105)

  ```solidity
      event Liquidate(address indexed asset, address indexed user, uint256 shareAmountRepaid, uint256 seizedCollateral);
  ```

- Found in contracts/external/interfaces/Silo/IShareToken.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/IShareToken.sol#L12)

  ```solidity
      event NotificationSent(INotificationReceiver indexed notificationReceiver, bool success);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L45)

  ```solidity
      event NewDefaultMaximumLTV(uint64 defaultMaximumLTV);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L47)

  ```solidity
      event NewDefaultLiquidationThreshold(uint64 defaultLiquidationThreshold);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L53)

  ```solidity
      event NewSilo(address indexed silo, address indexed asset, uint128 siloVersion);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 92](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L92)

  ```solidity
      event RegisterSiloVersion(address indexed factory, uint128 siloLatestVersion, uint128 siloDefaultVersion);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L97)

  ```solidity
      event UnregisterSiloVersion(address indexed factory, uint128 siloVersion);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L101)

  ```solidity
      event SiloDefaultVersion(uint128 newDefaultVersion);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L107)

  ```solidity
      event FeeUpdate(uint64 newEntryFee, uint64 newProtocolShareFee, uint64 newProtocolLiquidationFee);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L113)

  ```solidity
      event AssetConfigUpdate(address indexed silo, address indexed asset, AssetConfig assetConfig);
  ```

- Found in contracts/external/interfaces/Silo/ISiloRepository.sol [Line: 118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Silo/ISiloRepository.sol#L118)

  ```solidity
      event VersionForAsset(address indexed asset, uint128 version);
  ```

- Found in contracts/external/libraries/Pendle/IPMarket.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPMarket.sol#L13)

  ```solidity
      event Mint(address indexed receiver, uint256 netLpMinted, uint256 netSyUsed, uint256 netPtUsed);
  ```

- Found in contracts/external/libraries/Pendle/IPMarket.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPMarket.sol#L15)

  ```solidity
      event Burn(
  ```

- Found in contracts/external/libraries/Pendle/IPMarket.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPMarket.sol#L19)

  ```solidity
      event Swap(
  ```

- Found in contracts/external/libraries/Pendle/IPMarket.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPMarket.sol#L28)

  ```solidity
      event UpdateImpliedRate(uint256 indexed timestamp, uint256 lnLastImpliedRate);
  ```

- Found in contracts/external/libraries/Pendle/IPMarket.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPMarket.sol#L30)

  ```solidity
      event IncreaseObservationCardinalityNext(
  ```

- Found in contracts/external/libraries/Pendle/IPPtOracle.sol [Line: 5](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPPtOracle.sol#L5)

  ```solidity
      event SetBlockCycleNumerator(uint16 newBlockCycleNumerator);
  ```

- Found in contracts/external/libraries/Pendle/IPStandardizedYield.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPStandardizedYield.sol#L33)

  ```solidity
      event ClaimRewards(address indexed user, address[] rewardTokens, uint256[] rewardAmounts);
  ```

- Found in contracts/external/libraries/Pendle/IPYieldToken.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/Pendle/IPYieldToken.sol#L21)

  ```solidity
      event Burn(address indexed caller, address indexed receiver, uint256 amountPYToRedeem, uint256 amountSyOut);
  ```

- Found in contracts/governance/Keepers.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L18)

  ```solidity
      event Execute(address indexed destination, bytes data, uint256 gasLimit, address executor, uint256 deadline);
  ```

- Found in contracts/governance/Keepers.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L19)

  ```solidity
      event UpdateOwners(address[] owners, bool[] addOrRemove);
  ```

- Found in contracts/governance/Keepers.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L20)

  ```solidity
      event UpdateThreshold(uint8 threshold);
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L24)

  ```solidity
      event UpdateChainInfo(uint256 chainId, address destinationAddress);
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L25)

  ```solidity
      event UpdateBridgeTransactionApproval(bytes32 transactionHash, uint256 timestamp);
  ```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L26)

  ```solidity
      event StartBridgeTransaction(BridgeRequest bridgeRequest, bytes32 transactionHash);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L19)

  ```solidity
      event SetValueOracle(address _valueOracle);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L20)

  ```solidity
      event SetSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L21)

  ```solidity
      event AddEligibleUser(address _user);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L22)

  ```solidity
      event BridgeExecutionCompleted(BridgeRequest _bridgeRequest);
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L20)

  ```solidity
      event AddedHandler(address _handler, bool state);
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L21)

  ```solidity
      event AddedChain(uint256 _chainId, bool state);
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L22)

  ```solidity
      event AddedBridgeBlacklist(string bridgeName, bool state);
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L23)

  ```solidity
      event Bridged(address bridge, address token, uint256 amount, bytes data);
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L24)

  ```solidity
      event Rescued(address token, address userAddress, uint256 amount);
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L20)

  ```solidity
      event UpdatedDefaultPriceSource(address[] baseCurrencies, INoyaValueOracle[] oracles);
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L21)

  ```solidity
      event UpdatedAssetPriceSource(address[] asset, address[] baseToken, address[] oracle);
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L22)

  ```solidity
      event UpdatedPriceRoute(address asset, address baseToken, address[] s);
  ```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L32)

  ```solidity
      event ChainlinkPriceAgeThresholdUpdated(uint256 newThreshold);
  ```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L21)

  ```solidity
      event NewPeriod(uint32 period);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L116)

  ```solidity
      event RecordDeposit(uint256 depositId, address receiver, uint256 recordTime, uint256 amount, address referrer);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L117)

  ```solidity
      event CalculateDeposit(
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 120](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L120)

  ```solidity
      event MoveTheMiddle(uint256 newMiddle, bool depositOrWithdraw);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L121)

  ```solidity
      event ExecuteDeposit(
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L125)

  ```solidity
      event RecordWithdraw(uint256 withdrawId, address owner, address receiver, uint256 shares, uint256 recordTime);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L126)

  ```solidity
      event CalculateWithdraw(
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L134)

  ```solidity
      event ExecuteWithdraw(
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L143)

  ```solidity
      event FeeRecepientsChanged(address, address, address);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 144](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L144)

  ```solidity
      event FeeRatesChanged(uint256, uint256, uint256);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L145)

  ```solidity
      event WithdrawGroupStarted(uint256 lastId, uint256 totalCBAmount);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L146)

  ```solidity
      event WithdrawGroupFulfilled(uint256 lastId, uint256 totalCBAmount, uint256 totalABAmount);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L147)

  ```solidity
      event ValueOracleUpdated(address valueOracle);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L148)

  ```solidity
      event TransferTokensToTrustedAddress(address token, uint256 amount, address caller, bytes data);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L149)

  ```solidity
      event ResetMiddle(uint256 newMiddle, uint256 oldMiddle, bool depositOrWithdraw);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L150)

  ```solidity
      event RecordProfit(uint256 storedProfitAmount, uint256 currentProfit, uint256 feeAmount, uint256 recordTime);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 151](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L151)

  ```solidity
      event ResetFee(uint256 storedProfitAmount, uint256 currentProfit, uint256 recordTime);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 152](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L152)

  ```solidity
      event CollectManagementFee(uint256 feeAmount, uint256 timeDuration, uint256 totalShares, uint256 currentFeeShares);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L153)

  ```solidity
      event CollectPerformanceFee(uint256 feeAmount);
  ```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 154](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L154)

  ```solidity
      event RetrieveTokensForWithdraw(
  ```

</details>

### [N-02] Empty Block

Consider removing empty blocks.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/governance/Watchers.sol [Line: 8](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Watchers.sol#L8)

        ```solidity
            function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
        ```

</details>

### [N-03] Contract still has TODOs

Contract contains comments with TODOS

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/MaverickConnector.sol [Line: 93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L93)

  ```solidity
  contract MaverickConnector is BaseConnector, IERC721Receiver {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L80)

  ```solidity
  contract LZHelperSender is OAppSender {
  ```

</details>

### [N-04] Loop contains `require`/`revert` statements

Avoid `require` / `revert` statements in a loop because a single bad item can cause the whole transaction to fail. It's recommended to forgive on fail and return failed elements post processing of the loop

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L79)

  ```solidity
              for (uint256 i = 0; i < destinationConnector.length; i++) {
  ```

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L89)

  ```solidity
          for (uint256 i = 0; i < tokens.length; i++) {
  ```

- Found in contracts/governance/Keepers.sol [Line: 104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L104)

  ```solidity
              for (uint256 i = 0; i < threshold;) {
  ```

  </details>

### [N-05] Define and use `constant` variables instead of using literals

Magic numbers are hardcoded numerical values used directly in the code, making it harder to read and maintain. Consider using constants instead of magic numbers.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/AccountingManager.sol [Line: 244](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L244)

  ```solidity
                  middleTemp, data.receiver, block.timestamp, shares, data.amount, (shares * 1e18) / data.amount
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 276](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L276)

  ```solidity
                  firstTemp, data.receiver, block.timestamp, data.shares, data.amount, (data.shares * 1e18) / data.amount
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 512](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L512)

  ```solidity
          if (timePassed > 10 days) {
  ```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 513](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/AccountingManager.sol#L513)

  ```solidity
              timePassed = 10 days;
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 78](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CompoundConnector.sol#L78)

  ```solidity
          return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase;
  ```

- Found in contracts/connectors/CompoundConnector.sol [Line: 119](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CompoundConnector.sol#L119)

  ```solidity
                  if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 132](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L132)

  ```solidity
          } else if (poolInfo.tokens.length == 3) {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 133](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L133)

  ```solidity
              uint256[3] memory amounts;
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 136](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L136)

  ```solidity
          } else if (poolInfo.tokens.length == 4) {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 137](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L137)

  ```solidity
              uint256[4] memory amounts;
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 140](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L140)

  ```solidity
          } else if (poolInfo.tokens.length == 5) {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 141](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L141)

  ```solidity
              uint256[5] memory amounts;
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 144](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L144)

  ```solidity
          } else if (poolInfo.tokens.length == 6) {
  ```

- Found in contracts/connectors/CurveConnector.sol [Line: 145](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CurveConnector.sol#L145)

  ```solidity
              uint256[6] memory amounts;
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L71)

  ```solidity
              bytes4 method = bytes4(calls[i].callData[:4]);
  ```

- Found in contracts/connectors/GearBoxV3.sol [Line: 74](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L74)

  ```solidity
                  (address token) = abi.decode(calls[i].callData[4:], (address));
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 271](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L271)

  ```solidity
                  SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 275](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L275)

  ```solidity
              if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 280](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PendleConnector.sol#L280)

  ```solidity
              if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 123](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L123)

  ```solidity
              uint256 price = _getValue(assets[i], base, 1e18);
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 124](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L124)

  ```solidity
              totalDepositAmount += depositAmount * price / 1e18;
  ```

- Found in contracts/connectors/SiloConnector.sol [Line: 125](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L125)

  ```solidity
              totalBAmount += borrowAmount * price / 1e18;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L12)

  ```solidity
      function add_liquidity(uint256[3] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L13)

  ```solidity
      function add_liquidity(uint256[3] memory amounts, uint256 min_mint_amount, bool _use_underlying) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L14)

  ```solidity
      function add_liquidity(address _pool, uint256[3] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L16)

  ```solidity
      function add_liquidity(uint256[4] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L17)

  ```solidity
      function add_liquidity(address _pool, uint256[4] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L19)

  ```solidity
      function add_liquidity(uint256[5] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L20)

  ```solidity
      function add_liquidity(address _pool, uint256[5] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L22)

  ```solidity
      function add_liquidity(uint256[6] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/interfaces/Curve/ICurveSwap.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/interfaces/Curve/ICurveSwap.sol#L23)

  ```solidity
      function add_liquidity(address _pool, uint256[6] memory amounts, uint256 min_mint_amount) external payable;
  ```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L26)

  ```solidity
          return uint256(morpho.extSloads(slot)[0] >> 128);
  ```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L36)

  ```solidity
          return uint256(morpho.extSloads(slot)[0] >> 128);
  ```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L46)

  ```solidity
          return uint256(morpho.extSloads(slot)[0] >> 128);
  ```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 56](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L56)

  ```solidity
          return uint256(morpho.extSloads(slot)[0] >> 128);
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 132](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L132)

  ```solidity
              x *= 100;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 189](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L189)

  ```solidity
              term = ((term * x) / ONE_20) / 3;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 195](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L195)

  ```solidity
              term = ((term * x) / ONE_20) / 5;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 201](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L201)

  ```solidity
              term = ((term * x) / ONE_20) / 7;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 207](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L207)

  ```solidity
              term = ((term * x) / ONE_20) / 9;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 213](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L213)

  ```solidity
              term = ((term * x) / ONE_20) / 11;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 226](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L226)

  ```solidity
              return (((product * seriesSum) / ONE_20) * firstAN) / 100;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 338](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L338)

  ```solidity
              sum *= 100;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 339](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L339)

  ```solidity
              a *= 100;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 411](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L411)

  ```solidity
              seriesSum += num / 3;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 414](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L414)

  ```solidity
              seriesSum += num / 5;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 417](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L417)

  ```solidity
              seriesSum += num / 7;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 420](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L420)

  ```solidity
              seriesSum += num / 9;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 423](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L423)

  ```solidity
              seriesSum += num / 11;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 434](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L434)

  ```solidity
              return (sum + seriesSum) / 100;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 468](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L468)

  ```solidity
              seriesSum += num / 3;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 471](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L471)

  ```solidity
              seriesSum += num / 5;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 474](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L474)

  ```solidity
              seriesSum += num / 7;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 477](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L477)

  ```solidity
              seriesSum += num / 9;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 480](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/Pendle/LogExpMath.sol#L480)

  ```solidity
              seriesSum += num / 11;
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L40)

  ```solidity
          harmonicMeanLiquidity = uint128(secondsAgoX160 / (uint192(secondsPerLiquidityCumulativesDelta) << 32));
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 60](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L60)

  ```solidity
                  ? FullMath.mulDiv(ratioX192, baseAmount, 1 << 192)
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L61)

  ```solidity
                  : FullMath.mulDiv(1 << 192, baseAmount, ratioX192);
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 65](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L65)

  ```solidity
                  ? FullMath.mulDiv(ratioX128, baseAmount, 1 << 128)
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 66](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L66)

  ```solidity
                  : FullMath.mulDiv(1 << 128, baseAmount, ratioX128);
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L121)

  ```solidity
                  / (uint192(secondsPerLiquidityCumulativeX128 - prevSecondsPerLiquidityCumulativeX128) << 32)
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L28)

  ```solidity
          if (absTick & 0x2 != 0) ratio = (ratio * 0xfff97272373d413259a46990580e213a) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L29)

  ```solidity
          if (absTick & 0x4 != 0) ratio = (ratio * 0xfff2e50f5f656932ef12357cf3c7fdcc) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L30)

  ```solidity
          if (absTick & 0x8 != 0) ratio = (ratio * 0xffe5caca7e10e4e61c3624eaa0941cd0) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L31)

  ```solidity
          if (absTick & 0x10 != 0) ratio = (ratio * 0xffcb9843d60f6159c9db58835c926644) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 32](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L32)

  ```solidity
          if (absTick & 0x20 != 0) ratio = (ratio * 0xff973b41fa98c081472e6896dfb254c0) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L33)

  ```solidity
          if (absTick & 0x40 != 0) ratio = (ratio * 0xff2ea16466c96a3843ec78b326b52861) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 34](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L34)

  ```solidity
          if (absTick & 0x80 != 0) ratio = (ratio * 0xfe5dee046a99a2a811c461f1969c3053) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L35)

  ```solidity
          if (absTick & 0x100 != 0) ratio = (ratio * 0xfcbe86c7900a88aedcffc83b479aa3a4) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L36)

  ```solidity
          if (absTick & 0x200 != 0) ratio = (ratio * 0xf987a7253ac413176f2b074cf7815e54) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L37)

  ```solidity
          if (absTick & 0x400 != 0) ratio = (ratio * 0xf3392b0822b70005940c7a398e4b70f3) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L38)

  ```solidity
          if (absTick & 0x800 != 0) ratio = (ratio * 0xe7159475a2c29b7443b29c7fa6e889d9) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L39)

  ```solidity
          if (absTick & 0x1000 != 0) ratio = (ratio * 0xd097f3bdfd2022b8845ad8f792aa5825) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 40](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L40)

  ```solidity
          if (absTick & 0x2000 != 0) ratio = (ratio * 0xa9f746462d870fdf8a65dc1f90e061e5) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L41)

  ```solidity
          if (absTick & 0x4000 != 0) ratio = (ratio * 0x70d869a156d2a1b890bb3df62baf32f7) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 42](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L42)

  ```solidity
          if (absTick & 0x8000 != 0) ratio = (ratio * 0x31be135f97d08fd981231505542fcfa6) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 43](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L43)

  ```solidity
          if (absTick & 0x10000 != 0) ratio = (ratio * 0x9aa508b5b7a84e1c677de54f3e99bc9) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 44](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L44)

  ```solidity
          if (absTick & 0x20000 != 0) ratio = (ratio * 0x5d6af8dedb81196699c329225ee604) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 45](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L45)

  ```solidity
          if (absTick & 0x40000 != 0) ratio = (ratio * 0x2216e584f5fa1ea926041bedfe98) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L46)

  ```solidity
          if (absTick & 0x80000 != 0) ratio = (ratio * 0x48a170391f7dc42444e8fa2) >> 128;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L53)

  ```solidity
          sqrtPriceX96 = uint160((ratio >> 32) + (ratio % (1 << 32) == 0 ? 0 : 1));
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 64](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L64)

  ```solidity
          uint256 ratio = uint256(sqrtPriceX96) << 32;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 109](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L109)

  ```solidity
          if (msb >= 128) r = ratio >> (msb - 127);
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 110](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L110)

  ```solidity
          else r = ratio << (127 - msb);
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 112](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L112)

  ```solidity
          int256 log_2 = (int256(msb) - 128) << 64;
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 200](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L200)

  ```solidity
          int24 tickLow = int24((log_sqrt10001 - 3_402_992_956_809_132_418_596_140_100_660_247_210) >> 128);
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 201](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/external/libraries/uniswap/TickMath.sol#L201)

  ```solidity
          int24 tickHi = int24((log_sqrt10001 + 291_339_464_771_989_622_907_027_621_153_398_088_495) >> 128);
  ```

- Found in contracts/governance/Keepers.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L28)

  ```solidity
          require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);
  ```

- Found in contracts/governance/Keepers.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L53)

  ```solidity
          require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 112](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L112)

  ```solidity
              _swapRequest.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);
  ```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 57](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L57)

  ```solidity
          if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {
  ```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 141](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L141)

  ```solidity
          return 10 ** decimals;
  ```

</details>

### [N-06] Large literal values multiples of 10000 can be replaced with scientific notation

Use `e` notation, for example: `1e18`, instead of its full numeric value.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/AccountingManager.sol [Line: 87](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L87)

  ```solidity
      uint256 public depositLimitTotalAmount = 1e6 * 200_000;
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 59](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L59)

  ```solidity
      int256 constant x0 = 128_000_000_000_000_000_000; // 2ˆ7
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 60](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L60)

  ```solidity
      int256 constant a0 = 38_877_084_059_945_950_922_200_000_000_000_000_000_000_000_000_000_000_000; // eˆ(x0) (no decimals)
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L61)

  ```solidity
      int256 constant x1 = 64_000_000_000_000_000_000; // 2ˆ6
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 62](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L62)

  ```solidity
      int256 constant a1 = 6_235_149_080_811_616_882_910_000_000; // eˆ(x1) (no decimals)
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 65](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L65)

  ```solidity
      int256 constant x2 = 3_200_000_000_000_000_000_000; // 2ˆ5
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 66](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L66)

  ```solidity
      int256 constant a2 = 7_896_296_018_268_069_516_100_000_000_000_000; // eˆ(x2)
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 67](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L67)

  ```solidity
      int256 constant x3 = 1_600_000_000_000_000_000_000; // 2ˆ4
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L68)

  ```solidity
      int256 constant a3 = 888_611_052_050_787_263_676_000_000; // eˆ(x3)
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 69](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L69)

  ```solidity
      int256 constant x4 = 800_000_000_000_000_000_000; // 2ˆ3
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L71)

  ```solidity
      int256 constant x5 = 400_000_000_000_000_000_000; // 2ˆ2
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 73](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L73)

  ```solidity
      int256 constant x6 = 200_000_000_000_000_000_000; // 2ˆ1
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 75](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L75)

  ```solidity
      int256 constant x7 = 100_000_000_000_000_000_000; // 2ˆ0
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 77](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L77)

  ```solidity
      int256 constant x8 = 50_000_000_000_000_000_000; // 2ˆ-1
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 79](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L79)

  ```solidity
      int256 constant x9 = 25_000_000_000_000_000_000; // 2ˆ-2
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 81](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L81)

  ```solidity
      int256 constant x10 = 12_500_000_000_000_000_000; // 2ˆ-3
  ```

- Found in contracts/external/libraries/Pendle/LogExpMath.sol [Line: 83](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/LogExpMath.sol#L83)

  ```solidity
      int256 constant x11 = 6_250_000_000_000_000_000; // 2ˆ-4
  ```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L16)

  ```solidity
      uint256 public genericSlippageTolerance = 50_000; // 5% slippage tolerance
  ```

</details>

### [N-07] Internal functions called only once can be inlined

Instead of separating the logic into a separate function, consider inlining the logic into the calling function. This can reduce the number of function calls and improve readability.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/Registry.sol [Line: 293](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L293)

  ```solidity
      function updateHoldingPosition(
  ```

- Found in contracts/external/libraries/Morpho/MathLib.sol [Line: 32](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/MathLib.sol#L32)

  ```solidity
      function mulDivUp(uint256 x, uint256 y, uint256 d) internal pure returns (uint256) {
  ```

- Found in contracts/external/libraries/Pendle/MarketApproxPtInLib.sol [Line: 130](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketApproxPtInLib.sol#L130)

  ```solidity
      function calcNumerators(
  ```

- Found in contracts/external/libraries/Pendle/MarketApproxPtInLib.sol [Line: 246](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketApproxPtInLib.sol#L246)

  ```solidity
      function calcSlope(MarketPreCompute memory comp, int256 totalPt, int256 ptToMarket)
  ```

- Found in contracts/external/libraries/Pendle/MarketMathCore.sol [Line: 110](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketMathCore.sol#L110)

  ```solidity
      function addLiquidityCore(MarketState memory market, int256 syDesired, int256 ptDesired, uint256 blockTime)
  ```

- Found in contracts/external/libraries/Pendle/MarketMathCore.sol [Line: 153](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketMathCore.sol#L153)

  ```solidity
      function removeLiquidityCore(MarketState memory market, int256 lpToRemove)
  ```

- Found in contracts/external/libraries/Pendle/MarketMathCore.sol [Line: 205](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketMathCore.sol#L205)

  ```solidity
      function getMarketPreCompute(MarketState memory market, PYIndex index, uint256 blockTime)
  ```

- Found in contracts/external/libraries/Pendle/MarketMathCore.sol [Line: 226](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketMathCore.sol#L226)

  ```solidity
      function calcTrade(MarketState memory market, MarketPreCompute memory comp, PYIndex index, int256 netPtToAccount)
  ```

- Found in contracts/external/libraries/Pendle/Math.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/Math.sol#L121)

  ```solidity
      function Int128(int256 x) internal pure returns (int128) {
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 188](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L188)

  ```solidity
      function getCollateralAmounts(SolvencyParams memory _params)
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 221](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L221)

  ```solidity
      function getBorrowAmounts(SolvencyParams memory _params)
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 245](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L245)

  ```solidity
      function getUserCollateralAmount(
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 275](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L275)

  ```solidity
      function getUserBorrowAmount(ISilo.AssetStorage memory _assetStates, address _user, uint256 _rcomp)
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 308](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L308)

  ```solidity
      function totalDepositsWithInterest(
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 324](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L324)

  ```solidity
      function totalBorrowAmountWithInterest(uint256 _totalBorrowAmount, uint256 _rcomp)
  ```

- Found in contracts/external/libraries/uniswap/FullMath.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/uniswap/FullMath.sol#L14)

  ```solidity
      function mulDiv(uint256 a, uint256 b, uint256 denominator) internal pure returns (uint256 result) {
  ```

- Found in contracts/external/libraries/uniswap/TickMath.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/uniswap/TickMath.sol#L23)

  ```solidity
      function getSqrtRatioAtTick(int24 tick) internal pure returns (uint160 sqrtPriceX96) {
  ```

## L-14: Contract still has TODOs

Contract contains comments with TODOS

- Found in contracts/connectors/MaverickConnector.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MaverickConnector.sol#L29)

  ```solidity
  contract MaverickConnector is BaseConnector, IERC721Receiver {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L19)

  ```solidity
  contract LZHelperSender is OAppSender {
  ```

</details>
 
### [N-08] Dead code
Protocol teams should consider removing dead code from contracts. Doing so not only increases readability but also has the potential to decrease contract size, leading to reduced gas usage

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/libraries/Pendle/IPYieldToken.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/IPYieldToken.sol#L33)

```solidity
// function redeemPYMulti(
```

- Found in contracts/external/libraries/Pendle/IPYieldToken.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/IPYieldToken.sol#L38)

```solidity
// function redeemDueInterestAndRewards(
```

- Found in contracts/external/libraries/Pendle/MarketApproxPtInLib.sol [Line: 436](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketApproxPtInLib.sol#L436)

```solidity
// function approxSwapExactYtForPt(
```

- Found in contracts/external/interfaces/Pendle/IPYieldToken.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPYieldToken.sol#L33)

```solidity
// function redeemPYMulti(
```

- Found in contracts/external/interfaces/Pendle/IPYieldToken.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPYieldToken.sol#L38)

```solidity
// function redeemDueInterestAndRewards(
```

- Found in contracts/external/interfaces/Convex/IBooster.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Convex/IBooster.sol#L14)

```solidity
// function poolInfo(uint256) external view returns (PoolInfo memory); // tuple(address,address,address,address,address,bool) returned
```

- Found in contracts/external/interfaces/Dolomite/AccountBalanceHelper.sol [Line: 56](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/AccountBalanceHelper.sol#L56)

```solidity
// function verifyBalanceIsNonNegative(
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L26)

```solidity
// function feeTo() external view returns (address);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L27)

```solidity
// function feeToSetter() external view returns (address);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 28](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L28)

```solidity
// function dolomiteMargin() external view returns (address);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L31)

```solidity
// function allPairs(uint) external view returns (address pair);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 32](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L32)

```solidity
// function allPairsLength() external view returns (uint);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L33)

```solidity
// function getPairInitCode() external pure returns (bytes memory);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 34](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L34)

```solidity
// function getPairInitCodeHash() external pure returns (bytes32);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L36)

```solidity
// function createPair(address tokenA, address tokenB) external returns (address pair);
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L38)

```solidity
// function setFeeTo(address) external;
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAmmFactory.sol#L39)

```solidity
// function setFeeToSetter(address) external;
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 72](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L72)

```solidity
// function getTradeCost(
```

- Found in contracts/helpers/ConnectorMock2.sol [Line: 55](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/ConnectorMock2.sol#L55)

```solidity
// function addPositionToRegistryUsingType(bytes32 _positionId, bytes memory data) external {
```

</details>

### [N-09] Unused State Variable

Consider removing unused state variables. Doing so not only increases readability but also has the potential to decrease contract size, leading to reduced gas usage

<details>
<summary><i>Instances</i></summary>

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol)
</details>

### [N-10] Style guide: Contract does not follow the Solidity style guide's suggested layout ordering

Adhering to a recommended order in Solidity contracts increases code readability and maintenance.
[More information in Documentation](https://docs.soliditylang.org/en/latest/style-guide.html#order-of-layout)
It's recommended to use the following order:

1. Type declarations
2. State variables
3. Events
4. Errors
5. Modifiers
6. Functions

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/BalancerFlashLoan.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerFlashLoan.sol#L21)

  ```solidity
      event MakeFlashLoan(IERC20[] tokens, uint256[] amounts);
  ```

- Found in contracts/connectors/PendleConnector.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol#L35)

  ```solidity
      event Supply(address market, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IGauge.sol [Line: 12](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Aerodrome/IGauge.sol#L12)

  ```solidity
      event Deposit(address indexed from, address indexed to, uint256 amount);
  ```

- Found in contracts/external/interfaces/Aerodrome/IRouter.sol [Line: 54](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Aerodrome/IRouter.sol#L54)

  ```solidity
      struct Zap {
  ```

- Found in contracts/external/interfaces/Aerodrome/IVoter.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Aerodrome/IVoter.sol#L30)

  ```solidity
      event GaugeCreated(
  ```

- Found in contracts/external/interfaces/Balancer/IBalancerVault.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Balancer/IBalancerVault.sol#L31)

  ```solidity
      struct JoinPoolRequest {
  ```

- Found in contracts/external/interfaces/Compound/ICompound.sol [Line: 142](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Compound/ICompound.sol#L142)

  ```solidity
      error Absurd();
  ```

- Found in contracts/external/interfaces/Pendle/IPLimitRouter.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPLimitRouter.sol#L13)

  ```solidity
      struct StaticOrder {
  ```

- Found in contracts/external/interfaces/Pendle/IPLimitRouter.sol [Line: 104](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPLimitRouter.sol#L104)

  ```solidity
      event OrderFilled(
  ```

- Found in contracts/external/interfaces/Pendle/IPStandardizedYield.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPStandardizedYield.sol#L33)

  ```solidity
      event ClaimRewards(address indexed user, address[] rewardTokens, uint256[] rewardAmounts);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L13)

  ```solidity
      event OwnerChanged(address oldOwner, address newOwner);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L33)

  ```solidity
      error ValueAlreadyInSet();
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L35)

  ```solidity
      event FeatureFlagAllowAllSet(bytes32 indexed feature, bool allowAll);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 61](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L61)

  ```solidity
      error FeatureUnavailable(bytes32 which);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 68](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L68)

  ```solidity
      event AccountCreated(uint128 indexed accountId, address indexed owner);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 116](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L116)

  ```solidity
      error AccountNotFound(uint128 accountId);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 131](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L131)

  ```solidity
      event DebtAssociated(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 148](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L148)

  ```solidity
      error MismatchAssociatedSystemKind(bytes32 expected, bytes32 actual);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 150](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L150)

  ```solidity
      event AssociatedSystemSet(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 177](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L177)

  ```solidity
      error AccountActivityTimeoutPending(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 190](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L190)

  ```solidity
      event CollateralLockCreated(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 250](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L250)

  ```solidity
      event CollateralConfigured(address indexed collateralType, CollateralConfiguration.Data config);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 264](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L264)

  ```solidity
      error InsufficientDebt(int256 currentDebt);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 266](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L266)

  ```solidity
      event IssuanceFeePaid(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 301](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L301)

  ```solidity
      error CannotScaleEmptyMapping();
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 311](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L311)

  ```solidity
      event Liquidation(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 349](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L349)

  ```solidity
      error InsufficientMarketCollateralDepositable(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 359](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L359)

  ```solidity
      event MarketCollateralDeposited(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 408](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L408)

  ```solidity
      error IncorrectMarketInterface(address market);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 410](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L410)

  ```solidity
      event MarketRegistered(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 480](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L480)

  ```solidity
      event PoolApprovedAdded(uint256 poolId);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 494](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L494)

  ```solidity
      error CapacityLocked(uint256 marketId);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 497](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L497)

  ```solidity
      event PoolConfigurationSet(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 545](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L545)

  ```solidity
      error OverflowUint256ToUint32();
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 550](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L550)

  ```solidity
      event RewardsClaimed(
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 623](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L623)

  ```solidity
      error InsufficientDelegation(uint256 minDelegation);
  ```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 626](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L626)

  ```solidity
      event DelegationUpdated(
  ```

- Found in contracts/external/interfaces/Silo/IBaseSilo.sol [Line: 15](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Silo/IBaseSilo.sol#L15)

  ```solidity
      struct AssetStorage {
  ```

- Found in contracts/external/libraries/Pendle/IPStandardizedYield.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/IPStandardizedYield.sol#L33)

  ```solidity
      event ClaimRewards(address indexed user, address[] rewardTokens, uint256[] rewardAmounts);
  ```

- Found in contracts/external/libraries/Pendle/MarketApproxPtInLib.sol [Line: 155](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketApproxPtInLib.sol#L155)

  ```solidity
      struct Args7 {
  ```

- Found in contracts/external/libraries/Pendle/MarketApproxPtInLib.sol [Line: 353](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/MarketApproxPtInLib.sol#L353)

  ```solidity
      struct Args6 {
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L25)

  ```solidity
      error DifferentArrayLength();
  ```

- Found in contracts/external/libraries/Silo/SolvencyV2.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Silo/SolvencyV2.sol#L30)

  ```solidity
      struct SolvencyParams {
  ```

- Found in contracts/external/libraries/dolomite/Decimal.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/dolomite/Decimal.sol#L35)

  ```solidity
      struct D256 {
  ```

- Found in contracts/external/libraries/dolomite/Types.sol [Line: 160](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/dolomite/Types.sol#L160)

  ```solidity
      struct AssetAmount {
  ```

- Found in contracts/external/libraries/uniswap/OracleLibrary.sol [Line: 127](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/uniswap/OracleLibrary.sol#L127)

  ```solidity
      struct WeightedTickData {
  ```

- Found in contracts/external/libraries/uniswap/PoolAddress.sol [Line: 9](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/uniswap/PoolAddress.sol#L9)

  ```solidity
      struct PoolKey {
  ```

- Found in contracts/governance/NoyaGovernanceBase.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/NoyaGovernanceBase.sol#L31)

  ```solidity
      modifier onlyManager() {
  ```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 24](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24)

  ```solidity
      uint32 constant TVL_UPDATE = 1;
  ```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 34](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L34)

  ```solidity
      modifier onlyHandler() {
  ```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L20)

  ```solidity
      event UpdatedDefaultPriceSource(address[] baseCurrencies, INoyaValueOracle[] oracles);
  ```

</details>

### [N-13] Consider using a struct rather than having many function input parameters

Functions with many parameters can become difficult to read and maintain. Using a struct to encapsulate these parameters can increase code readability, increase reusability, and reduce the likelihood of errors. Consider refactoring functions that take more than three parameters to use a struct instead.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/interfaces/MorphoBlue/IMorpho.sol [Line: 208](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/MorphoBlue/IMorpho.sol#L208):

```solidity
function supplyCollateral(MarketParams memory marketParams, uint256 assets, address onBehalf, bytes memory data)
```

- Found in contracts/external/interfaces/MorphoBlue/IMorpho.sol [Line: 104](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/MorphoBlue/IMorpho.sol#L104):

```solidity
function withdrawCollateral(MarketParams memory marketParams, uint256 assets, address onBehalf, address receiver)
```

- Found in contracts/external/interfaces/MorphoBlue/IMorpho.sol [Line: 105](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/MorphoBlue/IMorpho.sol#L105):

```solidity
function liquidate(
        MarketParams memory marketParams,
        address borrower,
        uint256 seizedAssets,
        uint256 repaidShares,
        bytes memory data
    )
```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 149](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L149):

```solidity
function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
```

- Found in contracts/accountingManager/Registry.sol [Line: 106](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L106):

```solidity
function addVault(
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
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 158](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L158):

```solidity
function changeVaultAddresses(
        uint256 vaultId,
        address _governer,
        address _maintainer,
        address _maintainerWithoutTimelock,
        address _keeperContract,
        address _watcher,
        address _emergency
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 207](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L207):

```solidity
function updateConnectorTrustedTokens(
        uint256 vaultId,
        address _connectorAddress,
        address[] calldata _tokens,
        bool trusted
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 238](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L238):

```solidity
function addTrustedPosition(
        uint256 vaultId,
        uint256 _positionTypeId,
        address calculatorConnector,
        bool onlyOwner,
        bool _isDebt,
        bytes calldata _data,
        bytes calldata _additionalData
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 293](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L293):

```solidity
function updateHoldingPosition(
        Vault storage vault,
        uint256 vaultId,
        bytes32 _positionId,
        bytes calldata d,
        bytes calldata AD,
        uint256 index,
        bytes32 holdingPositionId
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 293](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L293):

```solidity
function updateHoldingPosition(
        uint256 vaultId,
        bytes32 _positionId,
        bytes calldata _data,
        bytes calldata additionalData,
        bool removePosition
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 370](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L370):

```solidity
function updateHoldingPostionWithTime(
        uint256 vaultId,
        bytes32 _positionId,
        bytes calldata _data,
        bytes calldata additionalData,
        bool removePosition,
        uint256 positionTimestamp
    )
```

- Found in contracts/accountingManager/Registry.sol [Line: 394](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L394):

```solidity
function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
```

- Found in contracts/helpers/ConnectorMock2.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/ConnectorMock2.sol#L27):

```solidity
function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
```

- Found in contracts/helpers/BaseConnector.sol [Line: 85](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol#L85):

```solidity
function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
```

- Found in contracts/helpers/BaseConnector.sol [Line: 123](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol#L123):

```solidity
function transferPositionToAnotherConnector(
        address[] memory tokens,
        uint256[] memory amounts,
        bytes memory data,
        address connector
    )
```

- Found in contracts/helpers/BaseConnector.sol [Line: 205](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/BaseConnector.sol#L205):

```solidity
function swapHoldings(
        address[] memory tokensIn,
        address[] memory tokensOut,
        uint256[] memory amountsIn,
        bytes[] memory swapData,
        uint256[] memory routeIds
    )
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 91](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L91):

```solidity
function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L58):

```solidity
function _lzReceive(Origin calldata _origin, bytes32, bytes calldata _message, address, bytes calldata)
```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 78](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L78):

```solidity
function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 100](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L100):

```solidity
function getValueFromChainlinkFeed(
        AggregatorV3Interface source,
        uint256 amountIn,
        uint256 sourceTokenUnit,
        bool isInverse
```

</details>

### [N-14] Consider using descriptive constants when passing zero as a function argument

In instances where utilizing a zero parameter is essential, it is recommended to employ descriptive constants or an enum instead of directly integrating zero within function calls. This strategy aids in clearly articulating the caller's intention and minimizes the risk of errors. Emitting zero also not recomended, as it is not clear what the intention is.

<details>
<summary><i>Instances</i></summary>

Found in contracts/connectors/Dolomite.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L39)

```solidity
registry.updateHoldingPosition(
            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", false
        );
```

Found in contracts/connectors/Dolomite.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L53)

```solidity
 registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true
            );
```

</details>

### [N-15] Custom error has no error details

Take advantage of custom error's return value property.

An important feature of Custom Error is that values such as address, tokenID, msg.value can be written inside the () sign, providing a serious advantage in debugging and examining the revert details .

<details>
<summary><i>Instances</i></summary>

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L22):

```solidity
error InvalidPayload();
```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L25):

```solidity
error InvalidSender();
```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L18):

```solidity
error NoyaOracle_PriceOracleUnavailable(address asset, address baseToken);
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 37](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L37):

```solidity
error NoyaChainlinkOracle_DATA_OUT_OF_DATE();
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 38](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L38):

```solidity
error NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address asset, address baseToken, address source);
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L39):

```solidity
error NoyaChainlinkOracle_INVALID_INPUT();

</details>
```

### [N-16] Consider using OpenZeppelin's SafeCast for any casting

OpenZeppelin's has SafeCast library that provides functions to safely cast. Recommended to use it instead of casting directly in any case.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 67](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L67)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, MARKET_SLOT))) + TOTAL_BORROW_ASSETS_AND_SHARES_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 71](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L71)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, MARKET_SLOT))) + LAST_UPDATE_AND_FEE_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 91](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L91)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, ID_TO_MARKET_PARAMS_SLOT))) + LOAN_TOKEN_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 95](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L95)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, ID_TO_MARKET_PARAMS_SLOT))) + COLLATERAL_TOKEN_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 99](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L99)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, ID_TO_MARKET_PARAMS_SLOT))) + ORACLE_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 103](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L103)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, ID_TO_MARKET_PARAMS_SLOT))) + IRM_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol [Line: 107](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoStorageLib.sol#L107)

```solidity
        return bytes32(uint256(keccak256(abi.encode(id, ID_TO_MARKET_PARAMS_SLOT))) + LLTV_OFFSET);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L16)

```solidity
        return uint256(morpho.extSloads(slot)[0]);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L21)

```solidity
        return uint128(uint256(morpho.extSloads(slot)[0]));
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L26)

```solidity
        return uint256(morpho.extSloads(slot)[0] >> 128);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L31)

```solidity
        return uint128(uint256(morpho.extSloads(slot)[0]));
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L36)

```solidity
        return uint256(morpho.extSloads(slot)[0] >> 128);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 41](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L41)

```solidity
        return uint128(uint256(morpho.extSloads(slot)[0]));
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L46)

```solidity
        return uint256(morpho.extSloads(slot)[0] >> 128);
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 51](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L51)

```solidity
        return uint128(uint256(morpho.extSloads(slot)[0]));
```

- Found in contracts/external/libraries/Morpho/periphery/MorphoLib.sol [Line: 56](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Morpho/periphery/MorphoLib.sol#L56)

```solidity
        return uint256(morpho.extSloads(slot)[0] >> 128);
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 124](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L124)

```solidity
        uint256 uintprice = uint256(price);
```

</details>

### [N-17] Consider emitting an event at the end of the constructor

This will allow users to easily exactly pinpoint when and by whom a contract was constructed.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/CamelotConnector.sol [Line: 36](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/CamelotConnector.sol#L36)

```solidity
constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```

- Found in contracts/connectors/SiloConnector.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SiloConnector.sol#L17)

```solidity
constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 23](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/MorphoBlueConnector.sol#L23)

```solidity
constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
```

- Found in contracts/connectors/GearBoxV3.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/GearBoxV3.sol#L17)

```solidity
constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```

- Found in contracts/connectors/PrismaConnector.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/PrismaConnector.sol#L25)

```solidity
constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```

- Found in contracts/connectors/SNXConnector.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/connectors/SNXConnector.sol#L20)

```solidity
constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
```

- Found in contracts/governance/NoyaGovernanceBase.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/NoyaGovernanceBase.sol#L21)

```solidity
constructor(PositionRegistry _registry, uint256 _vaultId) {
```

- Found in contracts/governance/Keepers.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Keepers.sol#L27)

```solidity
constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
```

- Found in contracts/governance/Watchers.sol [Line: 7](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/governance/Watchers.sol#L7)

```solidity
constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
```

- Found in contracts/accountingManager/Registry.sol [Line: 66](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/Registry.sol#L66)

```solidity
constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
```

- Found in contracts/accountingManager/NoyaFeeReceiver.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/accountingManager/NoyaFeeReceiver.sol#L14)

```solidity
constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
```

- Found in contracts/helpers/ConnectorMock2.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/ConnectorMock2.sol#L22)

```solidity
constructor(address _registry, uint256 _vaultId) {
```

- Found in contracts/helpers/BaseConnector.sol [Line: 33](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/BaseConnector.sol#L33)

```solidity
constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27)

```solidity
constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31)

```solidity
constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }
```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L29)

```solidity
constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 29](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L29)

```solidity
constructor(PositionRegistry _registry) {
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 46](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L46)

```solidity
constructor(address _reg) {
```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 31](https://github.com/code-423n4/2024-04-noya/tree/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31)

```solidity
constructor(address _factory, PositionRegistry _registry) {
```

</details>

### [N-18] Consider using named returns

Using named returns makes the code more self-documenting, makes it easier to fill out NatSpec, and in some cases can save gas. The cases below are where there currently is at most one return statement, which is optimal for named returns.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/accountingManager/Registry.sol (https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)

```solidity

    function getPositionBP(uint256 vaultId, bytes32 _positionId) public view returns (PositionBP memory) {

     function updateHoldingPosition(
        uint256 vaultId,
        bytes32 _positionId,
        bytes calldata _data,
        bytes calldata additionalData,
        bool removePosition
    ) public vaultExists(vaultId) returns (uint256)
```

</details>

### [N-19] Events are missing sender information

Events should include the sender information when emitted in public or external functions for easier traceability.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/interfaces/Pendle/IPMarket.sol [Line: 30](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPMarket.sol#L30)

```solidity
event IncreaseObservationCardinalityNext(
        uint16 observationCardinalityNextOld, uint16 observationCardinalityNextNew
    );
```

- Found in contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol [Line: 53](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Dolomite/IDolomiteAMMPair.sol#L53)

```solidity
event Sync(uint112 reserve0, uint112 reserve1);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L35)

```solidity
event FeatureFlagAllowAllSet(bytes32 indexed feature, bool allowAll);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L39)

```solidity
event FeatureFlagDenyAllSet(bytes32 indexed feature, bool denyAll);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 415](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L415)

```solidity
event MarketSystemFeePaid(uint128 indexed marketId, uint256 feeAmount);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 428](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L428)

```solidity
event SetMarketMinLiquidityRatio(uint128 indexed marketId, uint256 minLiquidityRatio);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 429](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L429)

```solidity
event SetMinDelegateTime(uint128 indexed marketId, uint32 minDelegateTime);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 480](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L480)

```solidity
event PoolApprovedAdded(uint256 poolId);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 481](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L481)

```solidity
event PoolApprovedRemoved(uint256 poolId);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 482](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L482)

```solidity
event PreferredPoolSet(uint256 poolId);
```

- Found in contracts/external/interfaces/SNXV3/IV3CoreProxy.sol [Line: 512](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/SNXV3/IV3CoreProxy.sol#L512)

```solidity
event SetMinLiquidityRatio(uint256 minLiquidityRatio);
```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L25)

```solidity
event UpdateBridgeTransactionApproval(bytes32 transactionHash, uint256 timestamp);
```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L26)

```solidity
event StartBridgeTransaction(BridgeRequest bridgeRequest, bytes32 transactionHash);
```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L22)

```solidity
event BridgeExecutionCompleted(BridgeRequest _bridgeRequest);
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L21)

```solidity
event AddedChain(uint256 _chainId, bool state);
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L22)

```solidity
event AddedBridgeBlacklist(string bridgeName, bool state);
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 32](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L32)

```solidity
event ChainlinkPriceAgeThresholdUpdated(uint256 newThreshold);
```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L21)

```solidity
event NewPeriod(uint32 period);
```

</details>

### [N-20] Leverage Recent Solidity Features with 0.8.23

The recent updates in Solidity provide several features and optimizations that, when leveraged appropriately, can significantly elevate your contract's code clarity and maintainability. Key things include the use of push0 for placing 0 on the stack for EVM versions starting from "Shanghai", making your code simpler and more straightforward. Moreover, Solidity has extended NatSpec documentation support to enum and struct definitions, facilitating more comprehensive and insightful code documentation.

Additionally, the re-implementation of the UnusedAssignEliminator and UnusedStoreEliminator in the Solidity optimizer provides the ability to remove unused assignments in deeply nested loops. This results in a cleaner, more efficient contract code, reducing clutter and potential points of confusion during code review or debugging. It's recommended to make full use of these features and optimizations to increase the robustness and readability of your smart contracts.

### [N-21] Outdated Solidity Version

The current Solidity version used in the contract is outdated. Consider using a more recent version for advanced features and security.

0.8.4: bytes.concat() instead of abi.encodePacked(,)

0.8.12: string.concat() instead of abi.encodePacked(,)

0.8.13: Ability to use using for with a list of free functions

0.8.14: ABI Encoder: When ABI-encoding values from calldata that contain nested arrays, correctly validate the nested array length against calldatasize() in all cases. Override Checker: Allow changing data location for parameters only when overriding external functions.

0.8.15: Code Generation: Avoid writing dirty bytes to storage when copying bytes arrays. Yul Optimizer: Keep all memory side-effects of inline assembly blocks.

0.8.16: Code Generation: Fix data corruption that affected ABI-encoding of calldata values represented by tuples: structs at any nesting level; argument lists of external functions, events and errors; return value lists of external functions. The 32 leading bytes of the first dynamically-encoded value in the tuple would get zeroed when the last component contained a statically-encoded array.

0.8.17: Yul Optimizer: Prevent the incorrect removal of storage writes before calls to Yul functions that conditionally terminate the external EVM call.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/external/interfaces/Pendle/IPAllActionTypeV3.sol [Line: 3](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPAllActionTypeV3.sol#L3)

```solidity
pragma solidity ^0.8.0;
```

- Found in contracts/external/interfaces/Pendle/IPActionSwapYTV3.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPActionSwapYTV3.sol#L2)

```solidity
pragma solidity ^0.8.0;
```

- Found in contracts/external/interfaces/Pendle/IPActionSwapPTV3.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPActionSwapPTV3.sol#L2)

```solidity
pragma solidity ^0.8.0;
```

- Found in contracts/external/interfaces/Pendle/IPLimitRouter.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Pendle/IPLimitRouter.sol#L2)

```solidity
pragma solidity ^0.8.0;
```

- Found in contracts/external/interfaces/Aerodrome/IRouter.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Aerodrome/IRouter.sol#L2)

```solidity
pragma solidity ^0.8.0;
```

- Found in contracts/external/interfaces/Aerodrome/IVoter.sol [Line: 2](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/interfaces/Aerodrome/IVoter.sol#L2)

```solidity
pragma solidity ^0.8.0;
```

</details>

### [N-22] Non-uppercase/Constant-case Naming for immutable Variables

<details>
<summary><i>Instances</i></summary>

- Found in contracts/connectors/UNIv3Connector.sol [Line: 16](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol#L16)

```solidity
immutable positionManager
```

- Found in contracts/connectors/UNIv3Connector.sol [Line: 17](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol#L17)

```solidity
immutable factory
```

- Found in contracts/connectors/MorphoBlueConnector.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol#L13)

```solidity
immutable morphoBlue
```

- Found in contracts/connectors/AaveConnector.sol [Line: 18](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol#L18)

```solidity
immutable pool
```

- Found in contracts/connectors/AaveConnector.sol [Line: 22](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol#L22)

```solidity
immutable poolBaseToken
```

</details>

### [N-23] Consider defining system-wide constants in a single file

System-wide constants should be declared in a single file for easier maintainability and readability. This contract seems to contain constants which could potentially be system-wide and could be easier managed if they were centralized in a single location.

<details>
<summary><i>Instances</i></summary>

System-wide used constant 'ONE':

- Found in contracts/external/libraries/Pendle/SYUtils.sol [Line: 5](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/SYUtils.sol#L5)
- Found in contracts/external/libraries/Pendle/Math.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/external/libraries/Pendle/Math.sol#L20)
</details>

### [N-24] Style guide: Control structures do not follow the Solidity Style Guide

Following recommended practices for control structures in solidity code is vital for readability and maintainability. The control structures in contracts, libraries, functions, and structs should adhere to the following standards:

- Braces denoting the body should open on the same line as the declaration and close on their own line at the same indentation level as the beginning of the declaration.
- A single space should precede the opening brace.
- Control structures such as 'if', 'else', 'while', and 'for' should also follow these spacing and brace placement recommendations.

It is advised to revisit the [control structures](https://docs.soliditylang.org/en/latest/style-guide.html#control-structures) sections in documentation to ensure conformity with these recommended practices, fostering cleaner and more maintainable code.

<details>
<summary><i>Instances</i></summary>

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 119](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L119)

```solidity
if (receivingAmount < _request.minAmount)
  revert InvalidMinAmount();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 120](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L120)

```solidity
if (sendingAssetId != _request.inputToken)
  revert InvalidInputToken();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 121](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L121)

```solidity
if (receivingAssetId != _request.outputToken)
  revert InvalidOutputToken();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 122](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L122)

```solidity
if (amount != _request.amount)
  revert InvalidAmount();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 153](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153)

```solidity
if (isBridgeWhiteListed[bridgeData.bridge] == false)
  revert BridgeBlacklisted();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 154](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L154)

```solidity
if (isChainSupported[bridgeData.destinationChainId] == false)
  revert InvalidChainId();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 155](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L155)

```solidity
if (bridgeData.sendingAssetId != _request.inputToken) revert InvalidFromToken();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 159](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L159)

```solidity
if (bridgeData.minAmount > _request.amount) revert InvalidMinAmount();
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 160](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L160)

```solidity
if (bridgeData.destinationChainId != _request.destChainId) revert InvalidToChainId();
```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 78](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L78)

```solidity
if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L25)

```solidity
if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 42](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L42)

```solidity
if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 25](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L25)

```solidity
if (!registry.hasRole(registry.MAINTAINER_ROLE(), msg.sender)) revert INoyaValueOracle_Unauthorized(msg.sender);
```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 39](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L39)

```solidity
if (_period == 0) revert INoyaValueOracle_InvalidInput();
```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 66](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L66)

```solidity
if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
```

</details>

### [N-25] Consider using named mappings

As of Solidity version 0.8.18, it is possible to use named mappings to clarify the purpose of each mapping in the code.
It is recommended to use this feature for code readability and maintainability.

More information: [Solidity 0.8.18 Release Announcement](https://blog.soliditylang.org/2023/02/01/solidity-0.8.18-release-announcement/)

<details>
<summary><i>Instances</i></summary>

- Found in contracts/interface/IPositionRegistry.sol [Line: 35](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/IPositionRegistry.sol#L35)

```solidity
mapping(address => bool) trustedTokens;
```

- Found in contracts/interface/IPositionRegistry.sol [Line: 57](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/IPositionRegistry.sol#L57)

```solidity
mapping(address => ConnectorData) connectors;
```

- Found in contracts/interface/IPositionRegistry.sol [Line: 58](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/IPositionRegistry.sol#L58)

```solidity
mapping(bytes32 => PositionBP) trustedPositionsBP;
```

- Found in contracts/interface/IPositionRegistry.sol [Line: 59](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/IPositionRegistry.sol#L59)

```solidity
mapping(bytes32 => uint256) isPositionUsed;
```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 57](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/Accounting/IAccountingManager.sol#L57)

```solidity
mapping(uint256 => DepositRequest) queue;
```

- Found in contracts/interface/Accounting/IAccountingManager.sol [Line: 73](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/interface/Accounting/IAccountingManager.sol#L73)

```solidity
mapping(uint256 => WithdrawRequest) queue;
```

- Found in contracts/governance/Keepers.sol [Line: 10](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L10)

```solidity
mapping(address => bool) public isOwner;
```

- Found in contracts/accountingManager/AccountingManager.sol [Line: 27](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L27)

```solidity
mapping(address => uint256) public withdrawRequestsByAddress;
```

- Found in contracts/accountingManager/Registry.sol [Line: 26](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol#L26)

```solidity
mapping(uint256 => Vault) public vaults;
```

- Found in contracts/helpers/OmniChainHandler/OmnichainLogic.sol [Line: 21](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L21)

```solidity
mapping(uint256 => address) public destChainAddress;
    mapping(bytes32 => uint256) public approvedBridgeTXN;
```

- Found in contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol [Line: 13](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L13)

```solidity
mapping(address => bool) public isEligibleToUse;
    mapping(address => mapping(address => uint256)) public slippageTolerance;
```

- Found in contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol [Line: 13-14](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L13-L14)

```solidity
mapping(address => bool) public isHandler;
    mapping(string => bool) public isBridgeWhiteListed;
    mapping(uint256 => bool) public isChainSupported;
```

- Found in contracts/helpers/LZHelpers/LZHelperReceiver.sol [Line: 19](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L19)

```solidity
mapping(uint32 => ChainInfo) public chainInfo; // chainId => ChainInfo
    mapping(uint256 => VaultInfo) public vaultIdToVaultInfo; // vaultId => VaultInfo
```

- Found in contracts/helpers/LZHelpers/LZHelperSender.sol [Line: 20-21](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/LZHelpers/LZHelperSender.sol#L20-L21)

```solidity
    mapping(uint256 => ChainInfo) public chainInfo; // chainId => ChainInfo
    mapping(uint256 => VaultInfo) public vaultIdToVaultInfo; // vaultId => VaultInfo
```

- Found in contracts/helpers/valueOracle/NoyaValueOracle.sol [Line: 13-14](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L13-L14)

```solidity
mapping(address => INoyaValueOracle) public defaultPriceSource;
    mapping(address => mapping(address => address[])) public priceRoutes;
    mapping(address => mapping(address => INoyaValueOracle)) public priceSource;
```

- Found in contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol [Line: 20](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L20)

```solidity
mapping(address => mapping(address => address)) private assetsSources;
```

- Found in contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol [Line: 14](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L14)

```solidity
mapping(address => mapping(address => address)) public assetToBaseToPool;
```

</details>

### [N-26] Contracts should have full test coverage

It's recommended to have full test coverage for all contracts. While 100% code coverage does not guarantee absence of bugs, it can catch simple bugs and reduce regressions during code modifications. Moreover, to achieve full coverage, authors often have to refactor their code into more modular components, each testable separately. This leads to lower interdependencies, and results in code that is easier to understand and audit.

### [N-27] Large or complicated code bases should implement invariant tests

Large or complex code bases should include invariant fuzzing tests, such as those provided by Echidna. These tests require the identification of invariants that should not be violated under any circumstances, with the fuzzer testing various inputs and function calls to ensure these invariants always hold. This is especially important for code with a lot of inline-assembly, complicated math, or complex interactions between contracts. Despite having 100% code coverage, bugs can still occur due to the order of operations a user performs. Extensive invariant tests can significantly reduce this testing gap.