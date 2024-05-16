## Summary

| |Issue|Instances| 
|-|:-|:-:|
| [[L-01](#l-01)] | Consider adding validation of user inputs | 145| 
| [[L-02](#l-02)] | Array is `push()`ed but not `pop()`ed | 1| 
| [[L-03](#l-03)] | Execution at deadlines should be allowed | 1|
| [[L-04](#l-04)] | Consider bounding input array length | 37|
| [[L-05](#l-05)] | Burning is missing access control | 1| 
| [[L-06](#l-06)] | Privileged functions can create points of failure(Not captured by 4nalyzer) | 144| 
| [[L-07](#l-07)] | Deleting mapping in struct will not delete the mapping | 3|
| [[L-08](#l-08)] | Consider disabling `renounceOwnership()` | 3| 
| [[L-09](#l-09)] | Possible reentrancy with callback on transfer tokens | 3| 
| [[L-10](#l-10)] | Events may be emitted out of order due to reentrancy | 81| 
| [[L-11](#l-11)] | External calls in an unbounded loop can result in a DoS(Not captured by 4nalyzer) | 17| 
| [[L-12](#l-12)] | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 12| 
| [[L-13](#l-13)] | Gas griefing/theft is possible on an unsafe external call | 2| 
| [[L-14](#l-14)] | Input array lengths may differ | 13| 
| [[L-15](#l-15)] | Mapping arrays can grow in size without a way to shrink them | 1|
| [[L-16](#l-16)] | Missing zero address check in constructor | 16|
| [[L-17](#l-17)] | Missing contract-existence checks before low-level calls | 5|
| [[L-18](#l-18)] | Named return variable used before assignment | 1|
| [[L-19](#l-19)] | The `nonReentrant` modifier should be placed first in a function declaration | 92|
| [[L-20](#l-20)] | Contracts are designed to receive ETH but do not implement function for withdrawal | 2|
| [[L-21](#l-21)] | `onlyOwner` functions not accessible if owner renounces ownership | 10|
| [[L-22](#l-22)] | Sending tokens in a loop | 3|
| [[L-23](#l-23)] | Solidity version `0.8.20` may not work on other chains due to `PUSH0`(Not captured by 4nalyzer) | 1|
| [[L-24](#l-24)] | State variables not capped at reasonable values | 8|
| [[L-25](#l-25)] | Consider implementing two-step procedure for updating protocol addresses | 10|
| [[L-26](#l-26)] | Using zero as a parameter | 3|

### Low Risk Issues

### [L-01]<a name="l-01"></a> Consider adding validation of user inputs

There are no validations done on the arguments below. Consider that the Solidity [documentation](https://docs.soliditylang.org/en/latest/control-structures.html#panic-via-assert-and-error-via-require) states that `Properly functioning code should never create a Panic, not even on invalid external input. If this happens, then there is a bug in your contract which you should fix`. This means that there should be explicit checks for expected ranges of inputs. Underflows/overflows result in panics should not be used as range checks, and allowing funds to be sent to `0x0`, which is the default value of address variables and has many gotchas, should be avoided.

*There are 145 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

// @audit missing checks for -->  token, _caller
150:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
151:         external
152:         returns (uint256)
153:     {

// @audit missing checks for -->  receiver, referrer
200:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {

// @audit missing checks for -->  connector
257:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
258:         public
259:         onlyManager
260:         whenNotPaused
261:         nonReentrant
262:     {

// @audit missing checks for -->  receiver
304:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {

// @audit missing checks for -->  retrieveData
548:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {

// @audit missing checks for -->  base
632:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {

// @audit missing checks for -->  receiver
693:     function mint(uint256 shares, address receiver) public override returns (uint256) {

// @audit missing checks for -->  receiver, owner
697:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {

// @audit missing checks for -->  receiver, shareOwner
701:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {

// @audit missing checks for -->  receiver
705:     function deposit(uint256 assets, address receiver) public override returns (uint256) {

```


*GitHub* : [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L150-L153), [200](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L200-L200), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L257-L262), [304](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L304-L304), [548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L548-L548), [632](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L632-L632), [693](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L693-L693), [697](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L697-L697), [701](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L701-L701), [705](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L705-L705)

```solidity
📁 File: contracts/accountingManager/Registry.sol

// @audit missing checks for -->  _flashLoan
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

// @audit missing checks for -->  _maintainerWithoutTimelock, _emergency, _trustedTokens
106:     function addVault(
107:         uint256 vaultId,
108:         address _accountingManager,
109:         address _baseToken,
110:         address _governer,
111:         address _maintainer,
112:         address _maintainerWithoutTimelock,
113:         address _keeperContract,
114:         address _watcher,
115:         address _emergency,
116:         address[] calldata _trustedTokens
117:     ) external onlyRole(MAINTAINER_ROLE) {

// @audit missing checks for -->  _maintainerWithoutTimelock, _emergency
158:     function changeVaultAddresses(
159:         uint256 vaultId,
160:         address _governer,
161:         address _maintainer,
162:         address _maintainerWithoutTimelock,
163:         address _keeperContract,
164:         address _watcher,
165:         address _emergency
166:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

// @audit missing checks for -->  _connectorAddresses
188:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
189:         external
190:         onlyVaultMaintainer(vaultId)
191:         vaultExists(vaultId)
192:     {

// @audit missing checks for -->  _connectorAddress, _tokens
207:     function updateConnectorTrustedTokens(
208:         uint256 vaultId,
209:         address _connectorAddress,
210:         address[] calldata _tokens,
211:         bool trusted
212:     ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {

// @audit missing checks for -->  calculatorConnector
238:     function addTrustedPosition(
239:         uint256 vaultId,
240:         uint256 _positionTypeId,
241:         address calculatorConnector,
242:         bool onlyOwner,
243:         bool _isDebt,
244:         bytes calldata _data,
245:         bytes calldata _additionalData
246:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {

// @audit missing checks for -->  _connector
394:     function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
395:         public
396:         view
397:         returns (uint256)
398:     {

// @audit missing checks for -->  connector
436:     function isPositionTrustedForConnector(uint256 vaultId, bytes32 _positionId, address connector)
437:         public
438:         view
439:         returns (bool)
440:     {

// @audit missing checks for -->  token, connector
470:     function isTokenTrusted(uint256 vaultId, address token, address connector) public view returns (bool) {

// @audit missing checks for -->  calculatorConnector
486:     function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)
487:         public
488:         pure
489:         returns (bytes32)
490:     {

// @audit missing checks for -->  connectorAddress
499:     function isAnActiveConnector(uint256 vaultId, address connectorAddress) public view returns (bool) {

// @audit missing checks for -->  addr
525:     function isAddressTrusted(uint256 vaultId, address addr) public view returns (bool) {

```


*GitHub* : [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L84-L84), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L106-L117), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L158-L166), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L188-L192), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L207-L212), [238](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L238-L246), [394](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L394-L398), [436](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L436-L440), [470](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L470-L470), [486](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L486-L490), [499](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L499-L499), [525](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L525-L525)

```solidity
📁 File: contracts/connectors/AaveConnector.sol

// @audit missing checks for -->  supplyToken
46:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  _borrowAsset
62:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
63:         external
64:         onlyManager
65:         nonReentrant
66:     {

// @audit missing checks for -->  asset
81:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {

// @audit missing checks for -->  _borrowAsset
88:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager {

// @audit missing checks for -->  _collateral
100:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {

// @audit missing checks for -->  base
114:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L46-L46), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L62-L66), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L81-L81), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L88-L88), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L100-L100), [114](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L114-L114)

```solidity
📁 File: contracts/connectors/AerodromeConnector.sol

// @audit missing checks for -->  pool
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {

// @audit missing checks for -->  pool
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {

// @audit missing checks for -->  pool
111:     function claim(address pool) public onlyManager nonReentrant {

// @audit missing checks for -->  base
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

```


*GitHub* : [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L100-L100), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L106-L106), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L111-L111), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L125-L125)

```solidity
📁 File: contracts/connectors/BalancerConnector.sol

// @audit missing checks for -->  rewardsPools
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

// @audit missing checks for -->  base
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

```


*GitHub* : [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L53-L53), [162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L162-L162)

```solidity
📁 File: contracts/connectors/BalancerFlashLoan.sol

// @audit missing checks for -->  tokens
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
38:         external
39:         nonReentrant
40:     {

// @audit missing checks for -->  tokens
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L37-L40), [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L54-L59)

```solidity
📁 File: contracts/connectors/CamelotConnector.sol

// @audit missing checks for -->  base
88:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L88-L88)

```solidity
📁 File: contracts/connectors/CompoundConnector.sol

// @audit missing checks for -->  market, asset
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  _market, asset
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  rewardContract, market
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {

// @audit missing checks for -->  comet
74:     function getAccountHealthFactor(IComet comet) public view returns (uint256) {

// @audit missing checks for -->  comet
84:     function getBorrowBalanceInBase(IComet comet) public view returns (uint256 borrowBalanceInVirtualBase) {

// @audit missing checks for -->  comet
95:     function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) {

// @audit missing checks for -->  base
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {

```


*GitHub* : [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L29-L29), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L48-L48), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L63-L63), [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L74-L74), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L84-L84), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L95-L95), [125](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L125-L125)

```solidity
📁 File: contracts/connectors/CurveConnector.sol

// @audit missing checks for -->  pool
68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {

// @audit missing checks for -->  pool
81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {

// @audit missing checks for -->  pool
103:     function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {

// @audit missing checks for -->  pool
117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant
121:     {

// @audit missing checks for -->  pool
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     {

// @audit missing checks for -->  pool
192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager {

// @audit missing checks for -->  pool
202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager {

// @audit missing checks for -->  depostiToken
212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager {

// @audit missing checks for -->  gauges
221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {

// @audit missing checks for -->  pools
233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {

// @audit missing checks for -->  rewardsPools
247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

// @audit missing checks for -->  base
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

// @audit missing checks for -->  curvePool
297:     function estimateWithdrawAmount(ICurveSwap curvePool, uint256 amount, uint256 index)
298:         public
299:         view
300:         returns (uint256)
301:     {

```


*GitHub* : [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L68-L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L81-L81), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L103-L103), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L117-L121), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L160-L164), [192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L192-L192), [202](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L202-L202), [212](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L212-L212), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L221-L221), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L233-L233), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L247-L247), [265](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L265-L265), [297](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L297-L301)

```solidity
📁 File: contracts/connectors/Dolomite.sol

// @audit missing checks for -->  base
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L106-L106)

```solidity
📁 File: contracts/connectors/FraxConnector.sol

// @audit missing checks for -->  pool
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant
42:     {

// @audit missing checks for -->  pool
68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {

// @audit missing checks for -->  pool
87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {

// @audit missing checks for -->  pool
104:     function verifyHealthFactor(IFraxPair pool) public view {

// @audit missing checks for -->  base
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L38-L42), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L68-L68), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L87-L87), [104](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L104-L104), [150](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L150-L150)

```solidity
📁 File: contracts/connectors/GearBoxV3.sol

// @audit missing checks for -->  facade
24:     function openAccount(address facade, uint256 ref) public onlyManager {

// @audit missing checks for -->  facade, creditAccount
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {

// @audit missing checks for -->  facade, creditAccount, calls
62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {

// @audit missing checks for -->  base
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L24-L24), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L41-L41), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L62-L68), [93](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L93-L93)

```solidity
📁 File: contracts/connectors/LidoConnector.sol

// @audit missing checks for -->  base
91:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L91-L91)

```solidity
📁 File: contracts/connectors/MaverickConnector.sol

// @audit missing checks for -->  rewardContract
137:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {

// @audit missing checks for -->  base
153:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L137-L137), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L153-L153)

```solidity
📁 File: contracts/connectors/MorphoBlueConnector.sol

// @audit missing checks for -->  base
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

// @audit missing checks for -->  marketOracle, collateral
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {

```


*GitHub* : [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L118-L118), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L137-L137)

```solidity
📁 File: contracts/connectors/PendleConnector.sol

// @audit missing checks for -->  market
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  market
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {

// @audit missing checks for -->  market
112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {

// @audit missing checks for -->  _market
126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

// @audit missing checks for -->  _market
137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

// @audit missing checks for -->  market
149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
150:         external
151:         onlyManager
152:     {

// @audit missing checks for -->  market
166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
167:         public
168:         onlyManager
169:     {

// @audit missing checks for -->  market
183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant
187:     {

// @audit missing checks for -->  market
203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  market
216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {

// @audit missing checks for -->  market
241:     function claimRewards(IPMarket market) external onlyManager nonReentrant {

// @audit missing checks for -->  base
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

// @audit missing checks for -->  market
293:     function getYTValue(address market, uint256 balance) public view returns (uint256) {

// @audit missing checks for -->  market
303:     function isMarketEmpty(IPMarket market) public view returns (bool) {

```


*GitHub* : [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L78-L78), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L97-L97), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L112-L112), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L126-L126), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L137-L137), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L149-L152), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L166-L169), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L183-L187), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L203-L203), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L216-L216), [241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L241-L241), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L257-L257), [293](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L293-L293), [303](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L303-L303)

```solidity
📁 File: contracts/connectors/PrismaConnector.sol

// @audit missing checks for -->  zap, tm
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {

// @audit missing checks for -->  zap, tm
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {

// @audit missing checks for -->  zapContract, tm
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {

// @audit missing checks for -->  zapContract, tm
97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant {

// @audit missing checks for -->  zapContract, troveManager
129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {

// @audit missing checks for -->  base
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L33-L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L52-L56), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L75-L75), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L97-L104), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L129-L129), [145](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L145-L145)

```solidity
📁 File: contracts/connectors/SNXConnector.sol

// @audit missing checks for -->  _token
30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

// @audit missing checks for -->  _token
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

// @audit missing checks for -->  collateralType
68:     function delegateIntoPreferredPool(
69:         uint128 _accountId,
70:         address collateralType,
71:         uint256 newCollateralAmountD18,
72:         uint256 leverage
73:     ) public onlyManager {

// @audit missing checks for -->  collateralType
81:     function delegateIntoApprovedPool(
82:         uint256 poolIndex,
83:         uint128 _accountId,
84:         address collateralType,
85:         uint256 newCollateralAmountD18,
86:         uint256 leverage
87:     ) public onlyManager {

// @audit missing checks for -->  collateralType, distributor
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
95:         public
96:         onlyManager
97:     {

// @audit missing checks for -->  collateralType
102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager {

// @audit missing checks for -->  base
121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L30-L30), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L46-L46), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L68-L73), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L81-L87), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L94-L97), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L102-L108), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L121-L121)

```solidity
📁 File: contracts/connectors/SiloConnector.sol

// @audit missing checks for -->  siloToken, dToken
33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {

// @audit missing checks for -->  siloToken, wToken
52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant
56:     {

// @audit missing checks for -->  siloToken
71:     function getData(address siloToken)
72:         public
73:         view
74:         returns (uint256 userLTV, uint256 LiquidationThreshold, bool isSolvent)
75:     {

// @audit missing checks for -->  siloToken, bToken
85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  siloToken, rToken
98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {

// @audit missing checks for -->  base
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

// @audit missing checks for -->  silo
130:     function isSiloEmpty(ISilo silo) public view returns (bool) {

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L33-L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L52-L56), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L71-L75), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L85-L85), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L98-L98), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L109-L109), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L130-L130)

```solidity
📁 File: contracts/connectors/StargateConnector.sol

// @audit missing checks for -->  base
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [110](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L110-L110)

```solidity
📁 File: contracts/connectors/UNIv3Connector.sol

// @audit missing checks for -->  base
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {

```


*GitHub* : [127](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L127-L127)

```solidity
📁 File: contracts/governance/Keepers.sol

// @audit missing checks for -->  _owners
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {

// @audit missing checks for -->  destination, executor
84:     function execute(
85:         address destination,
86:         bytes calldata data,
87:         uint256 gasLimit,
88:         address executor,
89:         bytes32[] memory sigR,
90:         bytes32[] memory sigS,
91:         uint8[] memory sigV,
92:         uint256 deadline
93:     ) public {

```


*GitHub* : [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L42-L42), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L84-L93)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

// @audit missing checks for -->  _swapHandler
58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer {

// @audit missing checks for -->  _valueOracle
67:     function updateValueOracle(address _valueOracle) external onlyMaintainer {

// @audit missing checks for -->  token, caller
84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
85:         external
86:         returns (uint256)
87:     {

// @audit missing checks for -->  tokens, connector
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant {

// @audit missing checks for -->  token
153:     function updateTokenInRegistry(address token) public onlyManager {

// @audit missing checks for -->  tokens
169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
170:         external
171:         override
172:         nonReentrant
173:     {

// @audit missing checks for -->  tokensIn, tokensOut
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {

// @audit missing checks for -->  baseToken
249:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

```


*GitHub* : [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L58-L58), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L67-L67), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L84-L87), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L122-L127), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L153-L153), [169](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L169-L173), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L204-L210), [249](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L249-L249)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

// @audit missing checks for -->  token, caller
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     {

// @audit missing checks for -->  tokens
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {

// @audit missing checks for -->  baseToken
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {

```


*GitHub* : [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L27-L30), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L40-L40), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L71-L71)

```solidity
📁 File: contracts/helpers/LZHelpers/LZHelperSender.sol

// @audit missing checks for -->  omniChainManager
63:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner {

```


*GitHub* : [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L63-L63)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

// @audit missing checks for -->  base
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33-L33)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

// @audit missing checks for -->  _valueOracle
48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {

// @audit missing checks for -->  _inputToken, _outputToken
68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     {

// @audit missing checks for -->  _user
80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency {

// @audit missing checks for -->  _routes
147:     function addRoutes(RouteData[] memory _routes) public onlyMaintainer {

// @audit missing checks for -->  addr
164:     function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) {

```


*GitHub* : [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L48), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L71), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147-L147), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164-L164)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

// @audit missing checks for -->  _handler
45:     function addHandler(address _handler, bool state) external onlyOwner {

// @audit missing checks for -->  caller
77:     function performSwapAction(address caller, SwapRequest calldata _request)
78:         external
79:         payable
80:         override
81:         onlyHandler
82:         returns (uint256)
83:     {

// @audit missing checks for -->  caller
133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
134:         external
135:         payable
136:         override
137:         onlyHandler
138:     {

// @audit missing checks for -->  userAddress
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {

```


*GitHub* : [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L83), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133-L138), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L193)

```solidity
📁 File: contracts/helpers/TVLHelper.sol

// @audit missing checks for -->  registry, baseToken
14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {

// @audit missing checks for -->  registry
41:     function getLatestUpdateTime(uint256 vaultId, PositionRegistry registry) public view returns (uint256) {

```


*GitHub* : [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L14-L14), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L41-L41)

```solidity
📁 File: contracts/helpers/valueOracle/NoyaValueOracle.sol

// @audit missing checks for -->  baseCurrencies, oracles
37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
38:         public
39:         onlyMaintainer
40:     {

// @audit missing checks for -->  asset, baseToken, oracle
51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
52:         external
53:         onlyMaintainer
54:     {

// @audit missing checks for -->  asset, base, s
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {

// @audit missing checks for -->  asset, baseToken
71:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L40), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L54), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61), [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L71)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

// @audit missing checks for -->  assets, baseTokens, sources
70:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
71:         external
72:         onlyMaintainer
73:     {

// @audit missing checks for -->  asset, baseToken
89:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {

// @audit missing checks for -->  source
115:     function getValueFromChainlinkFeed(
116:         AggregatorV3Interface source,
117:         uint256 amountIn,
118:         uint256 sourceTokenUnit,
119:         bool isInverse
120:     ) public view returns (uint256) {

// @audit missing checks for -->  token
138:     function getTokenDecimals(address token) public view returns (uint256) {

// @audit missing checks for -->  asset, baseToken
143:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) {

```


*GitHub* : [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L73), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L89-L89), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L115-L120), [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L138-L138), [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L143-L143)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

// @audit missing checks for -->  tokenIn, baseToken
48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {

// @audit missing checks for -->  tokenIn, baseToken
60:     function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) {

```


*GitHub* : [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48), [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60-L60)

### [L-02]<a name="l-02"></a> Array is `push()`ed but not `pop()`ed

Array entries are added but are never removed. Consider whether this should be the case, or whether there should be a maximum, or whether old entries should be removed. Cases where there are specific potential problems will be flagged separately under a different issue.

*There are 1 instance(s) of this issue:*

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

149:             routes.push(_routes[i]);

```


*GitHub* : [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L149-L149)

### [L-03]<a name="l-03"></a> Execution at deadlines should be allowed

The condition may be wrong in these cases, as when block.timestamp is equal to the compared `>` or `<` variable these blocks will not be executed.

*There are 1 instance(s) of this issue:*

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

71:         if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {

```


*GitHub* : [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71-L71)

### [L-04]<a name="l-04"></a> Consider bounding input array length

Unbounded array inputs in functions can lead to unintentional excessive gas consumption, potentially causing a transaction to revert after expending substantial gas. To enhance user experience and prevent such scenarios, consider implementing a `require()` statement that limits the array length to a defined maximum. This constraint ensures that transactions won't proceed if they're likely to hit gas limits due to array size, saving users from unnecessary gas costs and offering a more predictable interaction with the contract.

*There are 37 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

//@audit retrieveData.length not bounded 
551:         for (uint256 i = 0; i < retrieveData.length; i++) {

//@audit items.length not bounded 
603:             for (uint256 i = 0; i < items.length; i++) {

//@audit items.length not bounded 
608:             for (uint256 i = 0; i < items.length; i++) {

```


*GitHub* : [551](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L551-L551), [603](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L603-L603), [608](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L608-L608)

```solidity
📁 File: contracts/accountingManager/Registry.sol

//@audit _trustedTokens.length not bounded 
138:         for (uint256 i = 0; i < _trustedTokens.length; i++) {

//@audit _connectorAddresses.length not bounded 
194:         for (uint256 i = 0; i < _connectorAddresses.length; i++) {

//@audit _tokens.length not bounded 
214:         for (uint256 i = 0; i < _tokens.length; i++) {

//@audit usingTokens.length not bounded 
253:             for (uint256 i = 0; i < usingTokens.length; i++) {

```


*GitHub* : [138](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L138-L138), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L194-L194), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L214-L214), [253](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L253-L253)

```solidity
📁 File: contracts/connectors/BalancerConnector.sol

//@audit rewardsPools.length not bounded 
54:         for (uint256 i = 0; i < rewardsPools.length; i++) {

//@audit tokens.length not bounded 
77:         for (uint256 i = 0; i < tokens.length; i++) {

```


*GitHub* : [54](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L54-L54), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L77-L77)

```solidity
📁 File: contracts/connectors/BalancerFlashLoan.sol

//@audit tokens.length not bounded 
74:             for (uint256 i = 0; i < tokens.length; i++) {

//@audit destinationConnector.length not bounded 
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {

//@audit tokens.length not bounded 
84:             for (uint256 i = 0; i < tokens.length; i++) {

//@audit tokens.length not bounded 
89:         for (uint256 i = 0; i < tokens.length; i++) {

```


*GitHub* : [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L74-L74), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L79-L79), [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L84-L84), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L89-L89)

```solidity
📁 File: contracts/connectors/CurveConnector.sol

//@audit gauges.length not bounded 
222:         for (uint256 i = 0; i < gauges.length; i++) {

//@audit pools.length not bounded 
234:         for (uint256 i = 0; i < pools.length; i++) {

//@audit rewardsPools.length not bounded 
248:         for (uint256 i = 0; i < rewardsPools.length; i++) {

```


*GitHub* : [222](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L222-L222), [234](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L234-L234), [248](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L248-L248)

```solidity
📁 File: contracts/connectors/Dolomite.sol

//@audit markets.length not bounded 
113:         for (uint256 i = 0; i < markets.length; i++) {

```


*GitHub* : [113](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L113-L113)

```solidity
📁 File: contracts/connectors/GearBoxV3.sol

//@audit calls.length not bounded 
69:         for (uint256 i = 0; i < calls.length; i++) {

```


*GitHub* : [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L69-L69)

```solidity
📁 File: contracts/connectors/MaverickConnector.sol

//@audit earnedInfo.length not bounded 
140:         for (uint256 i = 0; i < earnedInfo.length; i++) {

```


*GitHub* : [140](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L140-L140)

```solidity
📁 File: contracts/connectors/PendleConnector.sol

//@audit rewardTokens.length not bounded 
244:         for (uint256 i = 0; i < rewardTokens.length; i++) {

```


*GitHub* : [244](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L244-L244)

```solidity
📁 File: contracts/connectors/SiloConnector.sol

//@audit assets.length not bounded 
116:         for (uint256 i = 0; i < assets.length; i++) {

//@audit assetsS.length not bounded 
132:         for (uint256 i = 0; i < assetsS.length; i++) {

```


*GitHub* : [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L116-L116), [132](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L132-L132)

```solidity
📁 File: contracts/connectors/UNIv3Connector.sol

//@audit tokenIds.length not bounded 
102:         for (uint256 i = 0; i < tokenIds.length; i++) {

```


*GitHub* : [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L102-L102)

```solidity
📁 File: contracts/governance/Keepers.sol

//@audit _owners.length not bounded 
44:         for (uint256 i = 0; i < _owners.length; i++) {

```


*GitHub* : [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L44-L44)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

//@audit tokens.length not bounded 
178:         for (uint256 i = 0; i < tokens.length; i++) {

//@audit tokens.length not bounded 
189:         for (uint256 i = 0; i < tokens.length; i++) {

//@audit tokensIn.length not bounded 
211:         for (uint256 i = 0; i < tokensIn.length; i++) {

```


*GitHub* : [178](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L178-L178), [189](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L189-L189), [211](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L211-L211)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

//@audit tokens.length not bounded 
41:         for (uint256 i = 0; i < tokens.length; i++) {

//@audit tokens.length not bounded 
46:         for (uint256 i = 0; i < tokens.length; i++) {

```


*GitHub* : [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L41-L41), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L46-L46)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

//@audit usersAddresses.length not bounded 
37:         for (uint256 i = 0; i < usersAddresses.length; i++) {

//@audit _routes.length not bounded 
148:         for (uint256 i = 0; i < _routes.length;) {

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L37-L37), [148](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L148)

```solidity
📁 File: contracts/helpers/TVLHelper.sol

//@audit positions.length not bounded 
18:         for (uint256 i = 0; i < positions.length; i++) {

//@audit positions.length not bounded 
44:         for (uint256 i = 0; i < positions.length; i++) {

```


*GitHub* : [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L18-L18), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L44-L44)

```solidity
📁 File: contracts/helpers/valueOracle/NoyaValueOracle.sol

//@audit baseCurrencies.length not bounded 
41:         for (uint256 i = 0; i < baseCurrencies.length; i++) {

//@audit oracle.length not bounded 
55:         for (uint256 i = 0; i < oracle.length; i++) {

//@audit sources.length not bounded 
88:         for (uint256 i = 0; i < sources.length; i++) {

```


*GitHub* : [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L41-L41), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L55-L55), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L88-L88)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

//@audit assets.length not bounded 
74:         for (uint256 i = 0; i < assets.length; i++) {

```


*GitHub* : [74](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L74-L74)

### [L-05]<a name="l-05"></a> Burning is missing access control

The function allows any user to arbitrarily burn tokens from a passed in address. If someone approves the contract (e.g. for `type(uint256).max`), any other user can trigger a burn

*There are 1 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

543:     function burnShares(uint256 amount) public {

```


*GitHub* : [543](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L543-L543)

### [L-06]<a name="l-06"></a> Privileged functions can create points of failure(Not captured by 4nalyzer)

Ensure such accounts are protected and consider implementing multi sig to prevent a single point of failure

*There are 144 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

124:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {

135:     function setFeeReceivers(
136:         address _withdrawFeeReceiver,
137:         address _performanceFeeReceiver,
138:         address _managementFeeReceiver
139:     ) public onlyMaintainer {

170:     function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer {

226:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {

257:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
258:         public
259:         onlyManager
260:         whenNotPaused
261:         nonReentrant
262:     {

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


*GitHub* : [124](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L124-L124), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L135-L139), [170](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L170-L170), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L226-L226), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L257-L262), [328](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L328-L328), [360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L360-L360), [370](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L370-L370), [396](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L396-L396), [453](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L453-L453), [475](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L475-L475), [505](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L505-L505), [526](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L526-L526), [548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L548-L548), [659](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L659-L659), [663](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L663-L663), [667](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L667-L667), [673](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L673-L673), [678](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L678-L678), [683](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L683)

```solidity
📁 File: contracts/accountingManager/Registry.sol

158:     function changeVaultAddresses(
159:         uint256 vaultId,
160:         address _governer,
161:         address _maintainer,
162:         address _maintainerWithoutTimelock,
163:         address _keeperContract,
164:         address _watcher,
165:         address _emergency
166:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

188:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
189:         external
190:         onlyVaultMaintainer(vaultId)
191:         vaultExists(vaultId)
192:     {

207:     function updateConnectorTrustedTokens(
208:         uint256 vaultId,
209:         address _connectorAddress,
210:         address[] calldata _tokens,
211:         bool trusted
212:     ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {

238:     function addTrustedPosition(
239:         uint256 vaultId,
240:         uint256 _positionTypeId,
241:         address calculatorConnector,
242:         bool onlyOwner,
243:         bool _isDebt,
244:         bytes calldata _data,
245:         bytes calldata _additionalData
246:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {

266:     function removeTrustedPosition(uint256 vaultId, bytes32 _positionId)
267:         external
268:         onlyVaultMaintainer(vaultId)
269:         vaultExists(vaultId)
270:     {

```


*GitHub* : [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L158-L166), [188](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L188-L192), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L207-L212), [238](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L238-L246), [266](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L266-L270)

```solidity
📁 File: contracts/connectors/AaveConnector.sol

46:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {

62:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
63:         external
64:         onlyManager
65:         nonReentrant
66:     {

81:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {

88:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager {

100:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {

```


*GitHub* : [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L46-L46), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L62-L66), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L81-L81), [88](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L88-L88), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L100-L100)

```solidity
📁 File: contracts/connectors/AerodromeConnector.sol

53:     function supply(DepositData memory data) public onlyManager nonReentrant {

79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant {

100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {

106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {

111:     function claim(address pool) public onlyManager nonReentrant {

```


*GitHub* : [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L53-L53), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L79-L79), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L100-L100), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L106-L106), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L111-L111)

```solidity
📁 File: contracts/connectors/BalancerConnector.sol

53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant {

109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {

115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {

```


*GitHub* : [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L53-L53), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L64-L70), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L109-L109), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L115-L115)

```solidity
📁 File: contracts/connectors/CamelotConnector.sol

43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {

65:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
66:         external
67:         onlyManager
68:         nonReentrant
69:     {

```


*GitHub* : [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L43-L43), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L65-L69)

```solidity
📁 File: contracts/connectors/CompoundConnector.sol

29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {

48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {

63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {

```


*GitHub* : [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L29-L29), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L48-L48), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L63-L63)

```solidity
📁 File: contracts/connectors/CurveConnector.sol

68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {

81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {

103:     function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager {

117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant
121:     {

160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     {

182:     function withdrawFromConvexBooster(uint256 pid, uint256 amount) public onlyManager {

192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager {

202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager {

212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager {

221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {

233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {

247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {

```


*GitHub* : [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L68-L68), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L81-L81), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L103-L103), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L117-L121), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L160-L164), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L182-L182), [192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L192-L192), [202](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L202-L202), [212](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L212-L212), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L221-L221), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L233-L233), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L247-L247)

```solidity
📁 File: contracts/connectors/Dolomite.sol

30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {

58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager
61:         nonReentrant
62:     {

77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
78:         public
79:         onlyManager
80:         nonReentrant
81:     {

98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {

```


*GitHub* : [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L30-L30), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L43-L43), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L58-L62), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L77-L81), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L98-L98)

```solidity
📁 File: contracts/connectors/FraxConnector.sol

38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant
42:     {

68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {

87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {

```


*GitHub* : [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L38-L42), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L68-L68), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L87-L87)

```solidity
📁 File: contracts/connectors/GearBoxV3.sol

24:     function openAccount(address facade, uint256 ref) public onlyManager {

41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {

62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {

```


*GitHub* : [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L24-L24), [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L41-L41), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L62-L68)

```solidity
📁 File: contracts/connectors/LidoConnector.sol

37:     function deposit(uint256 amountIn) external onlyManager nonReentrant {

51:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {

69:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L37-L37), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L51-L51), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L69-L69)

```solidity
📁 File: contracts/connectors/MaverickConnector.sol

64:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant {

78:     function unstake(uint256 lockupId) external onlyManager nonReentrant {

91:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {

115:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
116:         external
117:         onlyManager
118:         nonReentrant
119:     {

137:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {

```


*GitHub* : [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L64-L64), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L78-L78), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L91-L91), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L115-L119), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L137-L137)

```solidity
📁 File: contracts/connectors/MorphoBlueConnector.sol

35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {

58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {

80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant {

95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant {

```


*GitHub* : [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L35-L35), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L58-L58), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L80-L80), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L95-L95)

```solidity
📁 File: contracts/connectors/PancakeswapConnector.sol

31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {

40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant {

50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant {

```


*GitHub* : [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L31-L31), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L40-L40), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L50-L50)

```solidity
📁 File: contracts/connectors/PendleConnector.sol

78:     function supply(address market, uint256 amount) external onlyManager nonReentrant {

97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {

112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {

126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {

149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
150:         external
151:         onlyManager
152:     {

166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
167:         public
168:         onlyManager
169:     {

183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant
187:     {

203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {

216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {

241:     function claimRewards(IPMarket market) external onlyManager nonReentrant {

```


*GitHub* : [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L78-L78), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L97-L97), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L112-L112), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L126-L126), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L137-L137), [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L149-L152), [166](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L166-L169), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L183-L187), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L203-L203), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L216-L216), [241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L241-L241)

```solidity
📁 File: contracts/connectors/PrismaConnector.sol

33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {

52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {

75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {

97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant {

129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L33-L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L52-L56), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L75-L75), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L97-L104), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L129-L129)

```solidity
📁 File: contracts/connectors/SNXConnector.sol

25:     function createAccount() public onlyManager {

30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {

68:     function delegateIntoPreferredPool(
69:         uint128 _accountId,
70:         address collateralType,
71:         uint256 newCollateralAmountD18,
72:         uint256 leverage
73:     ) public onlyManager {

81:     function delegateIntoApprovedPool(
82:         uint256 poolIndex,
83:         uint128 _accountId,
84:         address collateralType,
85:         uint256 newCollateralAmountD18,
86:         uint256 leverage
87:     ) public onlyManager {

94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
95:         public
96:         onlyManager
97:     {

102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager {

```


*GitHub* : [25](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L25-L25), [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L30-L30), [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L46-L46), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L68-L73), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L81-L87), [94](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L94-L97), [102](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L102-L108)

```solidity
📁 File: contracts/connectors/SiloConnector.sol

33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {

52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant
56:     {

85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {

98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L33-L33), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L52-L56), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L85-L85), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L98-L98)

```solidity
📁 File: contracts/connectors/StargateConnector.sol

49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {

76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant {

103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {

```


*GitHub* : [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L49-L49), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L76-L76), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L103-L103)

```solidity
📁 File: contracts/connectors/UNIv3Connector.sol

40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {

63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {

87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {

101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {

```


*GitHub* : [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L40-L40), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L63-L63), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L87-L87), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L101-L101)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

45:     function updateMinimumHealthFactor(uint256 _minimumHealthFactor) external onlyMaintainer {

58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer {

67:     function updateValueOracle(address _valueOracle) external onlyMaintainer {

122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant {

153:     function updateTokenInRegistry(address token) public onlyManager {

204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {

```


*GitHub* : [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L45-L45), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L58-L58), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L67-L67), [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L122-L127), [153](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L153-L153), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L204-L210)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer {

57:     function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {

68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {

```


*GitHub* : [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46-L46), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57-L57), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

28:     function updateTVLInfo() external onlyManager {

```


*GitHub* : [28](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency {

57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {

68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     {

80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency {

90:     function executeSwap(SwapRequest memory _swapRequest)
91:         external
92:         payable
93:         onlyEligibleUser
94:         onlyExistingRoute(_swapRequest.routeId)
95:         nonReentrant
96:         returns (uint256 _amountOut)
97:     {

126:     function executeBridge(BridgeRequest calldata _bridgeRequest)
127:         external
128:         payable
129:         onlyEligibleUser
130:         onlyExistingRoute(_bridgeRequest.routeId)
131:         nonReentrant
132:     {

147:     function addRoutes(RouteData[] memory _routes) public onlyMaintainer {

158:     function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency {

164:     function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) {

```


*GitHub* : [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L48), [57](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L57), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L71), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L97), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L132), [147](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147-L147), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L158-L158), [164](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164-L164)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

77:     function performSwapAction(address caller, SwapRequest calldata _request)
78:         external
79:         payable
80:         override
81:         onlyHandler
82:         returns (uint256)
83:     {

133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
134:         external
135:         payable
136:         override
137:         onlyHandler
138:     {

```


*GitHub* : [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L83), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133-L138)

```solidity
📁 File: contracts/helpers/valueOracle/NoyaValueOracle.sol

37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
38:         public
39:         onlyMaintainer
40:     {

51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
52:         external
53:         onlyMaintainer
54:     {

61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L40), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L54), [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

56:     function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {

70:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
71:         external
72:         onlyMaintainer
73:     {

```


*GitHub* : [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L56-L56), [70](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L73)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

38:     function setPeriod(uint32 _period) external onlyMaintainer {

48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {

```


*GitHub* : [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L38), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48)

### [L-07]<a name="l-07"></a> Deleting mapping in struct will not delete the mapping

The [delete](https://docs.soliditylang.org/en/latest/types.html#delete) keyword resets variables to their initial state. However, it doesn't behave as expected with structs containing mappings. The `delete` keyword only resets the struct's direct properties, leaving the mappings untouched. Explicitly delete the mapping values before deleting the struct.

*There are 3 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

281:             delete depositQueue.queue[firstTemp];

432:             delete withdrawQueue.queue[firstTemp];

```


*GitHub* : [281](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L281-L281), [432](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L432-L432)

```solidity
📁 File: contracts/accountingManager/Registry.sol

280:         delete vault.trustedPositionsBP[_positionId];

```


*GitHub* : [280](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L280-L280)

### [L-08]<a name="l-08"></a> Consider disabling `renounceOwnership()`

Typically, the contract's owner is the account that deploys the contract. As a result, the owner is able to perform certain privileged activities. The OpenZeppelin's `Ownable` is used in this project contract implements `renounceOwnership`. This can represent a certain risk if the ownership is renounced for any other reason than by design. Renouncing ownership will leave the contract without an owner, thereby removing any functionality that is only available to the owner.

*There are 3 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/NoyaFeeReceiver.sol

7: contract NoyaFeeReceiver is Ownable {

```


*GitHub* : [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L7-L7)

```solidity
📁 File: contracts/governance/Keepers.sol

9: contract Keepers is EIP712, Ownable2Step {

```


*GitHub* : [9](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L9-L9)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard {

```


*GitHub* : [10](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10-L10)

### [L-09]<a name="l-09"></a> Possible reentrancy with callback on transfer tokens

The following functions don't apply the [CEI](https://blockchain-academy.hs-mittweida.de/courses/solidity-coding-beginners-to-intermediate/lessons/solidity-11-coding-patterns/topic/checks-effects-interactions/) pattern. It's possible to reenter after the transfer if the token has some kind of callback functionality (e.g. ERC777/ERC1155).

*There are 3 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

// @audit state update on line 215
205:         baseToken.safeTransferFrom(msg.sender, address(this), amount);

// @audit state update on line 436
428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);

// @audit state update on line 441
439:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);

```


*GitHub* : [205](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L205-L205), [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L428-L428), [439](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L439-L439)

### [L-10]<a name="l-10"></a> Events may be emitted out of order due to reentrancy

If a reentrancy occurs, some events may be emitted in an unexpected order, and this may be a problem if a third party expects a specific order for these events. Ensure that events are emitted before external calls and follow the best practice of CEI.

*There are 81 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

216:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);

242:             emit CalculateDeposit(
243:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
244:             );

349:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);

429:             emit ExecuteWithdraw(
430:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
431:             );

562:             emit RetrieveTokensForWithdraw(
563:                 retrieveData[i].withdrawAmount,
564:                 retrieveData[i].connectorAddress,
565:                 amount,
566:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
567:             );

690:         emit Rescue(msg.sender, token, amount);

```


*GitHub* : [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L216-L216), [242](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L242-L244), [349](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L349-L349), [429](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L429-L431), [562](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L562-L567), [690](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L690-L690)

```solidity
📁 File: contracts/connectors/AaveConnector.sol

53:         emit Supply(supplyToken, amount);

75:         emit Borrow(_borrowAsset, _amount);

85:         emit Repay(asset, amount, i);

90:         emit RepayWithCollateral(_borrowAsset, _amount, i);

111:         emit WithdrawCollateral(_collateral, _collateralAmount);

```


*GitHub* : [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L53-L53), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L75-L75), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L85-L85), [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L90-L90), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L111-L111)

```solidity
📁 File: contracts/connectors/AerodromeConnector.sol

72:         emit Supply(data.pool, data.amount0, data.amount1);

97:         emit Withdraw(data.pool, data.amountLiquidity);

```


*GitHub* : [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L72-L72), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L97-L97)

```solidity
📁 File: contracts/connectors/BalancerConnector.sol

106:         emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount);

159:         emit DecreasePosition(p);

```


*GitHub* : [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L106-L106), [159](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L159-L159)

```solidity
📁 File: contracts/connectors/CompoundConnector.sol

37:         emit Supply(market, asset, amount);

59:         emit WithdrawOrBorrow(_market, asset, amount);

67:         emit ClaimRewards(rewardContract, market);

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L37-L37), [59](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L59-L59), [67](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L67-L67)

```solidity
📁 File: contracts/connectors/CurveConnector.sol

149:         emit OpenCurvePosition(pool, depositIndex, amount, minAmount);

174:         emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount);

184:         emit WithdrawFromConvexBooster(pid, amount);

194:         emit WithdrawFromConvexRewardPool(pool, amount);

204:         emit WithdrawFromGauge(pool, amount);

214:         emit WithdrawFromPrisma(depostiToken, amount);

226:         emit HarvestRewards(gauges);

240:         emit HarvestPrismaRewards(pools);

254:         emit HarvestConvexRewards(rewardsPools);

```


*GitHub* : [149](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L149-L149), [174](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L174-L174), [184](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L184-L184), [194](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L194-L194), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L204-L204), [214](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L214-L214), [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L226-L226), [240](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L240-L240), [254](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L254-L254)

```solidity
📁 File: contracts/connectors/FraxConnector.sol

60:         emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount);

79:         emit Withdraw(address(pool), withdrawAmount);

97:         emit Repay(address(pool), sharesToRepay);

```


*GitHub* : [60](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L60-L60), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L79-L79), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L97-L97)

```solidity
📁 File: contracts/connectors/GearBoxV3.sol

33:         emit OpenAccount(facade, ref);

51:         emit CloseAccount(facade, creditAccount);

85:         emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L33-L33), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L51-L51), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L85-L85)

```solidity
📁 File: contracts/connectors/LidoConnector.sol

44:         emit Deposit(amountIn);

62:         emit RequestWithdrawals(amount);

86:         emit ClaimWithdrawal(requestId);

```


*GitHub* : [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L44-L44), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L62-L62), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L86-L86)

```solidity
📁 File: contracts/connectors/MaverickConnector.sol

71:         emit Stake(amount, duration, doDelegation);

83:         emit Unstake(lockupId);

107:         emit AddLiquidityInMaverickPool(p);

130:         emit RemoveLiquidityFromMaverickPool(p);

146:         emit ClaimBoostedPositionRewards(rewardContract);

```


*GitHub* : [71](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L71-L71), [83](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L83-L83), [107](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L107-L107), [130](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L130-L130), [146](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L146-L146)

```solidity
📁 File: contracts/connectors/MorphoBlueConnector.sol

49:         emit Supply(amount, id, sOrC);

72:         emit Withdraw(amount, id, sOrC);

87:         emit Borrow(amount, id);

100:         emit Repay(amount, id);

```


*GitHub* : [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L49-L49), [72](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L72-L72), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L87-L87), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L100-L100)

```solidity
📁 File: contracts/connectors/PancakeswapConnector.sol

33:         emit SendPositionToMasterChef(tokenId);

43:         emit UpdatePosition(tokenId);

53:         emit Withdraw(tokenId);

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L33-L33), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L43-L43), [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L53-L53)

```solidity
📁 File: contracts/connectors/PendleConnector.sol

89:         emit Supply(market, syMinted);

101:         emit MintPTAndYT(market, syAmount);

118:         emit DepositIntoMarket(address(market), SYamount, PTamount);

129:         emit DepositIntoPenpie(_market, _amount);

139:         emit WithdrawFromPenpie(_market, _amount);

156:         emit SwapYTForPT(market, exactYTIn, min, guess);

173:         emit SwapYTForSY(market, exactYTIn, min, orderData);

195:         emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY);

207:         emit BurnLP(address(market), amount);

232:         emit DecreasePosition(address(market), _amount, closePosition);

247:         emit ClaimRewards(address(market));

```


*GitHub* : [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L89-L89), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L101-L101), [118](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L118-L118), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L129-L129), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L139-L139), [156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L156-L156), [173](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L173-L173), [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L195-L195), [207](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L207-L207), [232](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L232-L232), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L247-L247)

```solidity
📁 File: contracts/connectors/PrismaConnector.sol

66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);

85:         emit AddColl(address(zapContract), tm, amountIn);

121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);

135:         emit CloseTrove(address(zapContract), troveManager);

```


*GitHub* : [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L66-L66), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L85-L85), [121](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L121-L121), [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L135-L135)

```solidity
📁 File: contracts/connectors/SiloConnector.sol

41:         emit Deposit(siloToken, dToken, amount, oC);

68:         emit Withdraw(siloToken, wToken, amount, oC, closePosition);

89:         emit Borrow(siloToken, bToken, amount);

106:         emit Repay(siloToken, rToken, amount);

```


*GitHub* : [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L41-L41), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L68-L68), [89](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L89-L89), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L106-L106)

```solidity
📁 File: contracts/connectors/StargateConnector.sol

69:         emit DepositIntoStargatePool(depositRequest);

96:         emit WithdrawFromStargatePool(withdrawRequest);

106:         emit ClaimStargateRewards(poolId);

```


*GitHub* : [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L69-L69), [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L96-L96), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L106-L106)

```solidity
📁 File: contracts/connectors/UNIv3Connector.sol

56:         emit OpenPosition(p, tokenId);

80:         emit DecreasePosition(p);

95:         emit IncreasePosition(p);

```


*GitHub* : [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L56-L56), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L80-L80), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L95-L95)

```solidity
📁 File: contracts/governance/Keepers.sol

115:         emit Execute(destination, data, gasLimit, executor, deadline);

```


*GitHub* : [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L115-L115)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

143:             emit UpdateTokenInRegistry(token, remove);

192:         emit AddLiquidity(tokens, amounts, data);

```


*GitHub* : [143](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L143-L143), [192](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L192-L192)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

117:         emit ExecutionCompleted(
118:             _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
119:         );

139:         emit BridgeExecutionCompleted(_bridgeRequest);

```


*GitHub* : [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L117-L119), [139](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L139-L139)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

182:         emit Forwarded(lifi, address(token), amount, data);

200:         emit Rescued(token, userAddress, amount);

```


*GitHub* : [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L182-L182), [200](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L200-L200)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

52:         emit PoolsForAsset(tokenIn, baseToken, pool);

```


*GitHub* : [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L52-L52)

### [L-11]<a name="l-11"></a> External calls in an unbounded loop can result in a DoS(Not captured by 4nalyzer)

Consider limiting the number of iterations in loops that make external calls, as just a single one of them failing will result in a revert.

*There are 17 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);

555:             uint256 balanceBefore = baseToken.balanceOf(address(this));

556:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
557:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
558:             );

559:             uint256 balanceAfter = baseToken.balanceOf(address(this));

```


*GitHub* : [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L428-L428), [555](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L555-L555), [556](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L556-L558), [559](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L559-L559)

```solidity
📁 File: contracts/connectors/BalancerFlashLoan.sol

81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);

86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");

```


*GitHub* : [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L81-L81), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L86-L86)

```solidity
📁 File: contracts/connectors/SiloConnector.sol

117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));

119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));

```


*GitHub* : [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L117-L117), [119](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L119-L119)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

180:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));

181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));

190:             _updateTokenInRegistry(tokens[i]); // update the token in the registry

215:             _updateTokenInRegistry(tokensIn[i]);

216:             _updateTokenInRegistry(tokensOut[i]);

```


*GitHub* : [180](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L180-L180), [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L181-L181), [182](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L182-L182), [190](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L190-L190), [215](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L215-L215), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L216-L216)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

47:             _updateTokenInRegistry(tokens[i]); // update the token in the registry

```


*GitHub* : [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L44-L44), [47](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L47-L47)

```solidity
📁 File: contracts/helpers/TVLHelper.sol

22:             uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);

```


*GitHub* : [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L22-L22)

### [L-12]<a name="l-12"></a> Functions calling contracts/addresses with transfer hooks are missing reentrancy guards

Even if the function follows the best practice of check-effects-interaction, not using a reentrancy guard when there may be transfer hooks will open the users of this protocol up to [read-only reentrancies](https://chainsecurity.com/curve-lp-oracle-manipulation-post-mortem/) with no way to protect against it, except by block-listing the whole protocol.

*There are 12 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

// @audit function 'sendTokensToTrustedAddress()' is missing Reentrancy guard
156:             IERC20(token).safeTransfer(address(msg.sender), amount);

```


*GitHub* : [156](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L156-L156)

```solidity
📁 File: contracts/accountingManager/NoyaFeeReceiver.sol

// @audit function 'withdrawShares()' is missing Reentrancy guard
24:         AccountingManager(accountingManager).withdraw(amount, receiver);

```


*GitHub* : [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L24-L24)

```solidity
📁 File: contracts/connectors/BalancerFlashLoan.sol

// @audit function 'receiveFlashLoan()' is missing Reentrancy guard
76:                 tokens[i].safeTransfer(receiver, amounts[i]);

```


*GitHub* : [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L76-L76)

```solidity
📁 File: contracts/connectors/CurveConnector.sol

// @audit function 'withdrawFromConvexBooster()' is missing Reentrancy guard
183:         convexBooster.withdraw(pid, amount);

// @audit function 'withdrawFromConvexRewardPool()' is missing Reentrancy guard
193:         IConvexBasicRewards(pool).withdraw(amount, true);

// @audit function 'withdrawFromGauge()' is missing Reentrancy guard
203:         IRewardsGauge(pool).withdraw(amount);

// @audit function 'withdrawFromPrisma()' is missing Reentrancy guard
213:         IDepositToken(depostiToken).withdraw(address(this), amount);

```


*GitHub* : [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L183-L183), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L193-L193), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L203-L203), [213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L213-L213)

```solidity
📁 File: contracts/connectors/SNXConnector.sol

// @audit function 'withdraw()' is missing Reentrancy guard
49:         SNXCoreProxy.withdraw(_accountId, _token, _amount);

```


*GitHub* : [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L49-L49)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

// @audit function 'sendTokensToTrustedAddress()' is missing Reentrancy guard
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);

```


*GitHub* : [96](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L96-L96)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

// @audit function 'sendTokensToTrustedAddress()' is missing Reentrancy guard
32:             IERC20(token).safeTransfer(msg.sender, amount);

// @audit function 'addLiquidity()' is missing Reentrancy guard
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```


*GitHub* : [32](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L32-L32), [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L44-L44)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

// @audit function 'rescueFunds()' is missing Reentrancy guard
198:             IERC20(token).safeTransfer(userAddress, amount);

```


*GitHub* : [198](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L198-L198)

### [L-13]<a name="l-13"></a> Gas griefing/theft is possible on an unsafe external call

A low-level call will copy any amount of bytes to local memory. When bytes are copied from returndata to memory, the memory expansion cost is paid.This means that when using a standard solidity call, the callee can 'returnbomb' the caller, imposing an arbitrary gas cost.Because this gas is paid by the caller and in the caller's context, it can cause the caller to run out of gas and halt execution.Consider replacing all unsafe `call` with `excessivelySafeCall` from this [repository](https://github.com/nomad-xyz/ExcessivelySafeCall).

*There are 2 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

685:             (bool success,) = payable(msg.sender).call{ value: amount }("");

```


*GitHub* : [685](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L685-L685)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

195:             (bool success,) = payable(userAddress).call{ value: amount }("");

```


*GitHub* : [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195)

### [L-14]<a name="l-14"></a> Input array lengths may differ

If the caller makes a copy-paste error, the lengths may be mismatched and an operation believed to have been completed may not in fact have been completed (e.g. if the array being iterated over is shorter than the one being indexed into).

*There are 13 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/Registry.sol

// @audit _enableds[]
195:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];

```


*GitHub* : [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L195-L195)

```solidity
📁 File: contracts/connectors/BalancerConnector.sol

// @audit amounts[]
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);

```


*GitHub* : [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L78-L78)

```solidity
📁 File: contracts/connectors/BalancerFlashLoan.sol

// @audit amounts[]
76:                 tokens[i].safeTransfer(receiver, amounts[i]);

// @audit amounts[]
77:                 amounts[i] = amounts[i] + feeAmounts[i];

// @audit amounts[]
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");

// @audit amounts[]
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);

```


*GitHub* : [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L76-L76), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L77-L77), [86](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L86-L86), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L91-L91)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

// @audit amounts[]
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

// @audit tokensOut[]
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)

// @audit tokensOut[]
216:             _updateTokenInRegistry(tokensOut[i]);

```


*GitHub* : [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L181-L181), [213](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L213-L213), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L216-L216)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

// @audit amounts[]
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```


*GitHub* : [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L44-L44)

```solidity
📁 File: contracts/helpers/valueOracle/NoyaValueOracle.sol

// @audit oracles[]
42:             defaultPriceSource[baseCurrencies[i]] = oracles[i];

// @audit asset[]
56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);

```


*GitHub* : [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L42-L42), [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol

// @audit baseTokens[]
75:             assetsSources[assets[i]][baseTokens[i]] = sources[i];

```


*GitHub* : [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L75-L75)

### [L-15]<a name="l-15"></a> Mapping arrays can grow in size without a way to shrink them

It's a good practice to maintain control over the size of array mappings in Solidity, especially if they are dynamically updated. If a contract includes a mechanism to push items into an array, it should ideally also provide a mechanism to remove items. This is because Solidity arrays don't automatically shrink when items are deleted - their length needs to be manually adjusted.

Ignoring this can lead to bloated and inefficient contracts. For instance, iterating over a large array can cause your contract to hit the block gas limit. Additionally, if entries are only marked for deletion but never actually removed, you may end up dealing with stale or irrelevant data, which can cause logical errors.

Therefore, implementing a method to 'pop' items from mapping arrays helps manage contract's state, improve efficiency and prevent potential issues related to gas limits or stale data. Always ensure to handle potential underflow conditions when popping elements from the mapping array.

*There are 1 instance(s) of this issue:*

```solidity
📁 File: contracts/helpers/valueOracle/NoyaValueOracle.sol

14:     mapping(address => mapping(address => address[])) public priceRoutes;

```


*GitHub* : [14](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L14-L14)

### [L-16]<a name="l-16"></a> Missing zero address check in constructor

Constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a checking, there's a risk that an address parameter could be mistakenly set to the zero address `(0x0)`. This could be due to an error or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it will be irretrievable. It's therefore crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

*There are 16 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/Registry.sol

// @audit missing checks for -->  _flashLoan
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {

```


*GitHub* : [66](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L66-L66)

```solidity
📁 File: contracts/connectors/AerodromeConnector.sol

// @audit missing checks for -->  _voter
40:     constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)
41:         BaseConnector(baseConnectorParams)
42:     {

```


*GitHub* : [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L40-L42)

```solidity
📁 File: contracts/connectors/Dolomite.sol

// @audit missing checks for -->  _dolomiteMargin, _borrowPositionProxy
18:     constructor(
19:         address _depositWithdrawalProxy,
20:         address _dolomiteMargin,
21:         address _borrowPositionProxy,
22:         BaseConnectorCP memory baseConnectorParams
23:     ) BaseConnector(baseConnectorParams) {

```


*GitHub* : [18](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L18-L23)

```solidity
📁 File: contracts/connectors/PancakeswapConnector.sol

// @audit missing checks for -->  _positionManager, _factory
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
20:         UNIv3Connector(_positionManager, _factory, baseConnectorParams)
21:     {

```


*GitHub* : [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L19-L21)

```solidity
📁 File: contracts/connectors/UNIv3Connector.sol

// @audit missing checks for -->  _positionManager, _factory
27:     constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
28:         BaseConnector(baseConnectorParams)
29:     {

```


*GitHub* : [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L27-L29)

```solidity
📁 File: contracts/governance/Keepers.sol

// @audit missing checks for -->  _owners
27:     constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {

```


*GitHub* : [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L27-L27)

```solidity
📁 File: contracts/governance/TimeLock.sol

// @audit missing checks for -->  proposers, executors, owner
7:     constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)
8:         TimelockController(minDelay, proposers, executors, owner)
9:     { }

```


*GitHub* : [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/TimeLock.sol#L7-L9)

```solidity
📁 File: contracts/governance/Watchers.sol

// @audit missing checks for -->  _owners
7:     constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }

```


*GitHub* : [7](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Watchers.sol#L7-L7)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

// @audit missing checks for -->  _registry
22:     constructor(address _registry, uint256 _vaultId) {

```


*GitHub* : [22](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L22-L22)

```solidity
📁 File: contracts/helpers/LZHelpers/LZHelperReceiver.sol

// @audit missing checks for -->  _endpoint, _owner
31:     constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }

```


*GitHub* : [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31-L31)

```solidity
📁 File: contracts/helpers/LZHelpers/LZHelperSender.sol

// @audit missing checks for -->  _endpoint, _owner
29:     constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }

```


*GitHub* : [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L29-L29)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol

// @audit missing checks for -->  _lzHelper
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
20:         OmnichainLogic(_lzHelper, baseConnectorParams)
21:     {

```


*GitHub* : [19](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L21)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol

// @audit missing checks for -->  _lzHelper
11:     constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
12:         OmnichainLogic(_lzHelper, baseConnectorParams)
13:     { }

```


*GitHub* : [11](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L11-L13)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

// @audit missing checks for -->  usersAddresses, _registry
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
35:         NoyaGovernanceBase(_registry, _vaultId)
36:     {

```


*GitHub* : [34](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L36)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

// @audit missing checks for -->  swapHandler, _lifi
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {

```


*GitHub* : [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L27)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

// @audit missing checks for -->  _factory, _registry
31:     constructor(address _factory, PositionRegistry _registry) {

```


*GitHub* : [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L31)

### [L-17]<a name="l-17"></a> Missing contract-existence checks before low-level calls

Low-level calls return success if there is no code present at the specified address.

*There are 5 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

685:             (bool success,) = payable(msg.sender).call{ value: amount }("");

```


*GitHub* : [685](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L685-L685)

```solidity
📁 File: contracts/connectors/BalancerFlashLoan.sol

81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);

```


*GitHub* : [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L81-L81)

```solidity
📁 File: contracts/governance/Keepers.sol

116:         (bool success,) = destination.call{ gas: gasLimit }(data);

```


*GitHub* : [116](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L116-L116)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);

195:             (bool success,) = payable(userAddress).call{ value: amount }("");

```


*GitHub* : [176](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176), [195](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195)

### [L-18]<a name="l-18"></a> Named return variable used before assignment

As no value is written to the variable, the default value is always read. This is usually due to a bug in the code logic that causes an invalid value to be used.

*There are 1 instance(s) of this issue:*

```solidity
📁 File: contracts/connectors/FraxConnector.sol

// @audit tvl
162:         return tvl;

```


*GitHub* : [162](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L162-L162)

### [L-19]<a name="l-19"></a> The `nonReentrant` modifier should be placed first in a function declaration

In functions with multiple modifiers, including `nonReentrant`, the `nonReentrant` modifier should be placed first in the ordering to prevent reentrancy in prior modifiers.

*There are 92 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

226:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
227:         uint256 middleTemp = depositQueue.middle;
228:         uint64 i = 0;
229: 
230:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
231: 
232:         while (
233:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
234:                 && i < maxIterations
235:         ) {
236:             i += 1;
237:             DepositRequest storage data = depositQueue.queue[middleTemp];
238: 
239:             uint256 shares = previewDeposit(data.amount);
240:             data.shares = shares;
241:             data.calculationTime = block.timestamp;
242:             emit CalculateDeposit(
243:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
244:             );
245: 
246:             middleTemp += 1;
247:         }
248: 
249:         depositQueue.middle = middleTemp;
250:     }

257:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
258:         public
259:         onlyManager
260:         whenNotPaused
261:         nonReentrant
262:     {
263:         uint256 firstTemp = depositQueue.first;
264:         uint64 i = 0;
265:         uint256 processedBaseTokenAmount = 0;
266: 
267:         while (
268:             depositQueue.middle > firstTemp
269:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
270:         ) {
271:             i += 1;
272:             DepositRequest memory data = depositQueue.queue[firstTemp];
273: 
274:             emit ExecuteDeposit(
275:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
276:             );
277:             // minting shares for receiver address
278:             _mint(data.receiver, data.shares);
279: 
280:             processedBaseTokenAmount += data.amount;
281:             delete depositQueue.queue[firstTemp];
282:             firstTemp += 1;
283:         }
284:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount;
285: 
286:         totalDepositedAmount += processedBaseTokenAmount;
287: 
288:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
289:             uint256[] memory amounts = new uint256[](1);
290:             amounts[0] = processedBaseTokenAmount;
291:             address[] memory tokens = new address[](1);
292:             tokens[0] = address(baseToken);
293:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
294:         } else {
295:             revert NoyaAccounting_INVALID_CONNECTOR();
296:         }
297: 
298:         depositQueue.first = firstTemp;
299:     }

328:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
329:         uint256 middleTemp = withdrawQueue.middle;
330:         uint64 i = 0;
331:         uint256 processedShares = 0;
332:         uint256 assetsNeededForWithdraw = 0;
333:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
334: 
335:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {
336:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
337:         }
338:         while (
339:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
340:                 && i < maxIterations
341:         ) {
342:             i += 1;
343:             WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
344:             uint256 assets = previewRedeem(data.shares);
345:             data.amount = assets;
346:             data.calculationTime = block.timestamp;
347:             assetsNeededForWithdraw += assets;
348:             processedShares += data.shares;
349:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);
350: 
351:             middleTemp += 1;
352:         }
353:         currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
354:         withdrawQueue.middle = middleTemp;
355:     }

360:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
361:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);
362:         currentWithdrawGroup.isStarted = true;
363:         currentWithdrawGroup.lastId = withdrawQueue.middle;
364:         emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);
365:     }

370:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
371:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
372:         uint256 neededAssets = neededAssetsForWithdraw();
373: 
374:         if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {
375:             revert NoyaAccounting_NOT_READY_TO_FULFILL();
376:         }
377:         currentWithdrawGroup.isFullfilled = true;
378:         amountAskedForWithdraw = 0;
379:         uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
380:         if (availableAssets >= currentWithdrawGroup.totalCBAmount) {
381:             currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;
382:         } else {
383:             currentWithdrawGroup.totalABAmount = availableAssets;
384:         }
385:         currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;
386:         currentWithdrawGroup.totalCBAmount = 0;
387:         emit WithdrawGroupFulfilled(
388:             currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount
389:         );
390:     }

396:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
397:         if (currentWithdrawGroup.isFullfilled == false) {
398:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
399:         }
400:         uint64 i = 0;
401:         uint256 firstTemp = withdrawQueue.first;
402: 
403:         uint256 withdrawFeeAmount = 0;
404:         uint256 processedBaseTokenAmount = 0;
405:         // loop through the withdraw queue and execute the withdraws
406:         while (
407:             currentWithdrawGroup.lastId > firstTemp
408:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
409:                 && i < maxIterations
410:         ) {
411:             i += 1;
412:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
413:             uint256 shares = data.shares;
414:             // calculate the base token amount that the user will receive based on the total available amount
415:             uint256 baseTokenAmount =
416:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
417: 
418:             withdrawRequestsByAddress[data.owner] -= shares;
419:             _burn(data.owner, shares);
420: 
421:             processedBaseTokenAmount += data.amount;
422:             {
423:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
424:                 withdrawFeeAmount += feeAmount;
425:                 baseTokenAmount = baseTokenAmount - feeAmount;
426:             }
427: 
428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);
429:             emit ExecuteWithdraw(
430:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
431:             );
432:             delete withdrawQueue.queue[firstTemp];
433:             // increment the first index of the withdraw queue
434:             firstTemp += 1;
435:         }
436:         totalWithdrawnAmount += processedBaseTokenAmount;
437: 
438:         if (withdrawFeeAmount > 0) {
439:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);
440:         }
441:         withdrawQueue.first = firstTemp;
442:         // if the withdraw group is fullfilled and there are no withdraws that are waiting for execution, we delete the withdraw group
443:         if (currentWithdrawGroup.lastId == firstTemp) {
444:             delete currentWithdrawGroup;
445:         }
446:     }

475:     function recordProfitForFee() public onlyManager nonReentrant {
476:         storedProfitForFee = getProfit();
477:         profitStoredTime = block.timestamp;
478: 
479:         if (storedProfitForFee < totalProfitCalculated) {
480:             return;
481:         }
482: 
483:         preformanceFeeSharesWaitingForDistribution =
484:             previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);
485:         emit RecordProfit(
486:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
487:         );
488:     }

505:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {
506:         if (block.timestamp - lastFeeDistributionTime < 1 days) {
507:             return (0, 0);
508:         }
509:         uint256 timePassed = block.timestamp - lastFeeDistributionTime;
510:         if (timePassed > 10 days) {
511:             timePassed = 10 days;
512:         }
513:         uint256 totalShares = totalSupply();
514:         uint256 currentFeeShares = balanceOf(managementFeeReceiver) + balanceOf(performanceFeeReceiver)
515:             + preformanceFeeSharesWaitingForDistribution;
516: 
517:         uint256 managementFeeAmount =
518:             (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;
519:         _mint(managementFeeReceiver, managementFeeAmount);
520:         emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares);
521:         lastFeeDistributionTime = block.timestamp;
522:         return (managementFeeAmount, timePassed);
523:     }

526:     function collectPerformanceFees() public onlyManager nonReentrant {
527:         if (
528:             preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours
529:                 || block.timestamp - profitStoredTime > 48 hours
530:         ) {
531:             return;
532:         }
533: 
534:         _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);
535: 
536:         totalProfitCalculated = storedProfitForFee;
537: 
538:         emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);
539: 
540:         preformanceFeeSharesWaitingForDistribution = 0;
541:     }

548:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
549:         uint256 amountAskedForWithdraw_temp = 0;
550:         uint256 neededAssets = neededAssetsForWithdraw();
551:         for (uint256 i = 0; i < retrieveData.length; i++) {
552:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
553:                 continue;
554:             }
555:             uint256 balanceBefore = baseToken.balanceOf(address(this));
556:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
557:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
558:             );
559:             uint256 balanceAfter = baseToken.balanceOf(address(this));
560:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
561:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
562:             emit RetrieveTokensForWithdraw(
563:                 retrieveData[i].withdrawAmount,
564:                 retrieveData[i].connectorAddress,
565:                 amount,
566:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
567:             );
568:         }
569:         amountAskedForWithdraw += amountAskedForWithdraw_temp;
570:         if (amountAskedForWithdraw_temp > neededAssets) {
571:             revert NoyaAccounting_INVALID_AMOUNT();
572:         }
573:     }

683:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {
684:         if (token == address(0)) {
685:             (bool success,) = payable(msg.sender).call{ value: amount }("");
686:             require(success, "Transfer failed.");
687:         } else {
688:             IERC20(token).safeTransfer(msg.sender, amount);
689:         }
690:         emit Rescue(msg.sender, token, amount);
691:     }

```


*GitHub* : [226](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L226-L250), [257](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L257-L299), [328](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L328-L355), [360](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L360-L365), [370](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L370-L390), [396](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L396-L446), [475](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L475-L488), [505](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L505-L523), [526](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L526-L541), [548](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L548-L573), [683](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691)

```solidity
📁 File: contracts/accountingManager/Registry.sol

238:     function addTrustedPosition(
239:         uint256 vaultId,
240:         uint256 _positionTypeId,
241:         address calculatorConnector,
242:         bool onlyOwner,
243:         bool _isDebt,
244:         bytes calldata _data,
245:         bytes calldata _additionalData
246:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {
247:         Vault storage vault = vaults[vaultId];
248:         bytes32 positionId = calculatePositionId(calculatorConnector, _positionTypeId, _data);
249:         {
250:             if (vault.trustedPositionsBP[positionId].isEnabled) revert AlreadyExists();
251:             if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();
252:             address[] memory usingTokens = IConnector(calculatorConnector).getUnderlyingTokens(_positionTypeId, _data);
253:             for (uint256 i = 0; i < usingTokens.length; i++) {
254:                 if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) {
255:                     revert TokenNotTrusted(usingTokens[i]);
256:                 }
257:             }
258: 
259:             vault.trustedPositionsBP[positionId] =
260:                 PositionBP(calculatorConnector, _positionTypeId, onlyOwner, true, _isDebt, _data, _additionalData);
261:         }
262:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data);
263:     }

```


*GitHub* : [238](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L238-L263)

```solidity
📁 File: contracts/connectors/AaveConnector.sol

46:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant {
47:         _approveOperations(supplyToken, pool, amount);
48:         IPool(pool).supply(supplyToken, amount, address(this), 0);
49:         registry.updateHoldingPosition(
50:             vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", false
51:         );
52:         _updateTokenInRegistry(supplyToken);
53:         emit Supply(supplyToken, amount);
54:     }

62:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
63:         external
64:         onlyManager
65:         nonReentrant
66:     {
67:         if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {
68:             revert IConnector_UntrustedToken(_borrowAsset);
69:         }
70:         IPool(pool).borrow(_borrowAsset, _amount, _interestRateMode, 0, address(this));
71:         // get the health factor
72:         (,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));
73:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
74:         _updateTokenInRegistry(_borrowAsset);
75:         emit Borrow(_borrowAsset, _amount);
76:     }

81:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant {
82:         _approveOperations(asset, pool, amount);
83:         IPool(pool).repay(asset, amount, i, address(this));
84:         _updateTokenInRegistry(asset);
85:         emit Repay(asset, amount, i);
86:     }

100:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant {
101:         IPool(pool).withdraw(_collateral, _collateralAmount, address(this));
102:         // get the health factor
103:         (uint256 totalCollateralBase,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));
104:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
105:         _updateTokenInRegistry(_collateral);
106:         if (totalCollateralBase <= DUST_LEVEL * 1e7) {
107:             registry.updateHoldingPosition(
108:                 vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", true
109:             );
110:         }
111:         emit WithdrawCollateral(_collateral, _collateralAmount);
112:     }

```


*GitHub* : [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L46-L54), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L62-L76), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L81-L86), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L100-L112)

```solidity
📁 File: contracts/connectors/AerodromeConnector.sol

53:     function supply(DepositData memory data) public onlyManager nonReentrant {
54:         bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));
55:         _approveOperations(IPool(data.pool).token0(), address(aerodromeRouter), data.amount0);
56:         _approveOperations(IPool(data.pool).token1(), address(aerodromeRouter), data.amount1);
57:         aerodromeRouter.addLiquidity(
58:             IPool(data.pool).token0(),
59:             IPool(data.pool).token1(),
60:             IPool(data.pool).stable(),
61:             data.amount0,
62:             data.amount1,
63:             data.min0Min,
64:             data.min1Min,
65:             address(this),
66:             data.deadline
67:         );
68:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
69:         _updateTokenInRegistry(IPool(data.pool).token0());
70:         _updateTokenInRegistry(IPool(data.pool).token1());
71: 
72:         emit Supply(data.pool, data.amount0, data.amount1);
73:     }

79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant {
80:         bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));
81:         _approveOperations(data.pool, address(aerodromeRouter), data.amountLiquidity);
82:         aerodromeRouter.removeLiquidity(
83:             IPool(data.pool).token0(),
84:             IPool(data.pool).token1(),
85:             IPool(data.pool).stable(),
86:             data.amountLiquidity,
87:             data.min0Min,
88:             data.min1Min,
89:             address(this),
90:             data.deadline
91:         );
92:         if (IERC20(data.pool).balanceOf(address(this)) == 0) {
93:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
94:         }
95:         _updateTokenInRegistry(IPool(data.pool).token0());
96:         _updateTokenInRegistry(IPool(data.pool).token1());
97:         emit Withdraw(data.pool, data.amountLiquidity);
98:     }

100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {
101:         address gauge = voter.gauges(pool);
102:         IERC20(pool).forceApprove(address(gauge), liquidity);
103:         IGauge(gauge).deposit(liquidity, address(this));
104:     }

106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {
107:         address gauge = voter.gauges(pool);
108:         IGauge(gauge).withdraw(liquidity);
109:     }

111:     function claim(address pool) public onlyManager nonReentrant {
112:         address gauge = voter.gauges(pool);
113:         IGauge(gauge).getReward(address(this));
114:         _updateTokenInRegistry(IGauge(gauge).rewardToken());
115:     }

```


*GitHub* : [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L53-L73), [79](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L79-L98), [100](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L100-L104), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L106-L109), [111](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L111-L115)

```solidity
📁 File: contracts/connectors/BalancerConnector.sol

53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
54:         for (uint256 i = 0; i < rewardsPools.length; i++) {
55:             IRewardPool baseRewardPool = IRewardPool(rewardsPools[i]);
56:             baseRewardPool.getReward();
57:         }
58:         _updateTokenInRegistry(address(AURA));
59:     }

64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant {
71:         address[] memory tokens;
72:         {
73:             (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(poolId);
74:         }
75:         address pool = IBalancerVault(balancerVault).getPool(poolId);
76: 
77:         for (uint256 i = 0; i < tokens.length; i++) {
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
79:         }
80: 
81:         IBalancerVault(balancerVault).joinPool(
82:             poolId,
83:             address(this), // sender
84:             address(this), // recipient
85:             IBalancerVault.JoinPoolRequest(
86:                 tokens,
87:                 amounts,
88:                 abi.encode(
89:                     IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                     amountsWithoutBPT, //_noBptAmounts,
91:                     minBPT // minimumBPT
92:                 ),
93:                 false
94:             )
95:         );
96:         bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(poolId));
97:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
98: 
99:         if (auraAmount > 0) {
100:             (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);
101: 
102:             uint256 amount = IERC20(pool).balanceOf(address(this));
103:             _approveOperations(pool, _poolInfo.auraPoolAddress, amount);
104:             IRewardPool(_poolInfo.auraPoolAddress).deposit(auraAmount, address(this));
105:         }
106:         emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount);
107:     }

109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {
110:         (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);
111:         _approveOperations(_poolInfo.pool, _poolInfo.auraPoolAddress, _amount);
112:         IRewardPool(_poolInfo.auraPoolAddress).deposit(_amount, address(this));
113:     }

115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {
116:         if (p._auraAmount > 0) {
117:             (PoolInfo memory _poolInfo, bytes32 positionId) = _getPoolInfo(p.poolId);
118: 
119:             IRewardPool(_poolInfo.auraPoolAddress).withdrawAndUnwrap(p._auraAmount, true);
120:         }
121: 
122:         if (p._lpAmount > 0) {
123:             address[] memory tokens;
124:             {
125:                 (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(p.poolId);
126:             }
127:             uint256[] memory _amounts = new uint256[](tokens.length);
128:             _amounts[p.outerIndex] = p.minAmount;
129: 
130:             IBalancerVault(balancerVault).exitPool(
131:                 p.poolId,
132:                 address(this), // sender
133:                 payable(address(this)), // recipient
134:                 IBalancerVault.ExitPoolRequest(
135:                     tokens,
136:                     _amounts,
137:                     abi.encode(
138:                         IBalancerVault.ExitKind.EXACT_BPT_IN_FOR_ONE_TOKEN_OUT,
139:                         p._lpAmount,
140:                         p.withdrawIndex // enterTokenIndex
141:                     ),
142:                     false
143:                 )
144:             );
145: 
146:             if (totalLpBalanceOf(p.poolId) == 0) {
147:                 registry.updateHoldingPosition(
148:                     vaultId,
149:                     registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(p.poolId)),
150:                     "",
151:                     "",
152:                     true
153:                 );
154:             }
155:             _updateTokenInRegistry(tokens[p.outerIndex]);
156:         }
157:         _updateTokenInRegistry(AURA);
158:         _updateTokenInRegistry(BAL);
159:         emit DecreasePosition(p);
160:     }

```


*GitHub* : [53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L53-L59), [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L64-L107), [109](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L109-L113), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L115-L160)

```solidity
📁 File: contracts/connectors/CamelotConnector.sol

43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {
44:         _approveOperations(p.tokenA, address(router), p.amountA);
45:         _approveOperations(p.tokenB, address(router), p.amountB);
46:         router.addLiquidity(
47:             p.tokenA, p.tokenB, p.amountA, p.amountB, p.minAmountA, p.minAmountB, address(this), p.deadline
48:         );
49:         _updateTokenInRegistry(p.tokenA);
50:         _updateTokenInRegistry(p.tokenB);
51:         registry.updateHoldingPosition(
52:             vaultId,
53:             registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),
54:             "",
55:             "",
56:             false
57:         );
58:     }

65:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
66:         external
67:         onlyManager
68:         nonReentrant
69:     {
70:         address pool = factory.getPair(p.tokenA, p.tokenB);
71:         _approveOperations(pool, address(router), p.amountLiquidty);
72:         router.removeLiquidity(
73:             p.tokenA, p.tokenB, p.amountLiquidty, p.minAmountA, p.minAmountB, address(this), p.deadline
74:         );
75:         _updateTokenInRegistry(p.tokenA);
76:         _updateTokenInRegistry(p.tokenB);
77:         if (IERC20(pool).balanceOf(address(this)) == 0) {
78:             registry.updateHoldingPosition(
79:                 vaultId,
80:                 registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),
81:                 "",
82:                 "",
83:                 true
84:             );
85:         }
86:     }

```


*GitHub* : [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L43-L58), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L65-L86)

```solidity
📁 File: contracts/connectors/CompoundConnector.sol

29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {
30:         _approveOperations(asset, market, amount);
31:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
32:         IComet(market).supply(asset, amount);
33:         registry.updateHoldingPosition(
34:             vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false
35:         );
36:         _updateTokenInRegistry(asset);
37:         emit Supply(market, asset, amount);
38:     }

48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {
49:         IComet(_market).withdraw(asset, amount);
50:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
51:         uint256 healthFactor = getAccountHealthFactor(IComet(_market));
52:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
53:         if (getCollBlanace(IComet(_market), false) == 0) {
54:             registry.updateHoldingPosition(
55:                 vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true
56:             );
57:         }
58:         _updateTokenInRegistry(asset);
59:         emit WithdrawOrBorrow(_market, asset, amount);
60:     }

63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {
64:         address rewardToken = IRewards(rewardContract).rewardConfig(market).token;
65:         IRewards(rewardContract).claim(address(market), address(this), true);
66:         _updateTokenInRegistry(rewardToken);
67:         emit ClaimRewards(rewardContract, market);
68:     }

```


*GitHub* : [29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L29-L38), [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L48-L60), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L63-L68)

```solidity
📁 File: contracts/connectors/CurveConnector.sol

68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant {
69:         PoolInfo memory poolInfo = _getPoolInfo(pool);
70: 
71:         _approveOperations(poolInfo.lpToken, poolInfo.gauge, amount);
72:         IRewardsGauge(poolInfo.gauge).deposit(amount);
73:     }

81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant {
82:         PoolInfo memory poolInfo = _getPoolInfo(pool);
83: 
84:         // approve depositToken to spend lpToken
85:         address lpToken = poolInfo.lpToken;
86:         address depostiToken = poolInfo.prismaCurvePool;
87:         if (!curveOrConvex) {
88:             depostiToken = poolInfo.prismaConvexPool;
89:         }
90:         _approveOperations(lpToken, depostiToken, amount);
91: 
92:         // stake LP in Prisma
93:         IDepositToken(depostiToken).deposit(address(this), amount);
94:     }

117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant
121:     {
122:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));
123:         PositionBP memory p = registry.getPositionBP(vaultId, positionId);
124:         PoolInfo memory poolInfo = abi.decode(p.additionalData, (PoolInfo));
125:         address token = poolInfo.tokens[depositIndex];
126:         address poolAddress = (poolInfo.tokens.length > 2 && poolInfo.zap != address(0)) ? poolInfo.zap : pool;
127:         _approveOperations(token, poolAddress, amount);
128:         if (poolInfo.tokens.length == 2) {
129:             uint256[2] memory amounts;
130:             amounts[depositIndex] = amount;
131:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
132:         } else if (poolInfo.tokens.length == 3) {
133:             uint256[3] memory amounts;
134:             amounts[depositIndex] = amount;
135:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
136:         } else if (poolInfo.tokens.length == 4) {
137:             uint256[4] memory amounts;
138:             amounts[depositIndex] = amount;
139:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
140:         } else if (poolInfo.tokens.length == 5) {
141:             uint256[5] memory amounts;
142:             amounts[depositIndex] = amount;
143:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
144:         } else if (poolInfo.tokens.length == 6) {
145:             uint256[6] memory amounts;
146:             amounts[depositIndex] = amount;
147:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount);
148:         }
149:         emit OpenCurvePosition(pool, depositIndex, amount, minAmount);
150:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
151:     }

160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     {
165:         PoolInfo memory poolInfo = _getPoolInfo(pool);
166:         address token = poolInfo.tokens[withdrawIndex];
167:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));
168: 
169:         ICurveSwap(poolInfo.pool).remove_liquidity_one_coin(amount, int128(uint128(withdrawIndex)), minAmount);
170:         _updateTokenInRegistry(token);
171:         if (totalLpBalanceOf(poolInfo) == 0) {
172:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
173:         }
174:         emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount);
175:     }

221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {
222:         for (uint256 i = 0; i < gauges.length; i++) {
223:             IRewardsGauge(gauges[i]).claim_rewards(address(this));
224:         }
225:         _updateTokenInRegistry(CRV);
226:         emit HarvestRewards(gauges);
227:     }

233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {
234:         for (uint256 i = 0; i < pools.length; i++) {
235:             IDepositToken(pools[i]).claimReward(address(this));
236:         }
237:         _updateTokenInRegistry(PRISMA);
238:         _updateTokenInRegistry(CRV);
239:         _updateTokenInRegistry(CVX);
240:         emit HarvestPrismaRewards(pools);
241:     }

247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
248:         for (uint256 i = 0; i < rewardsPools.length; i++) {
249:             IConvexBasicRewards baseRewardPool = IConvexBasicRewards(rewardsPools[i]);
250:             baseRewardPool.getReward(address(this), true);
251:         }
252:         _updateTokenInRegistry(CVX);
253:         _updateTokenInRegistry(CRV);
254:         emit HarvestConvexRewards(rewardsPools);
255:     }

```


*GitHub* : [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L68-L73), [81](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L81-L94), [117](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L117-L151), [160](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L160-L175), [221](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L221-L227), [233](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L233-L241), [247](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CurveConnector.sol#L247-L255)

```solidity
📁 File: contracts/connectors/Dolomite.sol

30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
31:         // get market token
32:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
33:         // approve
34:         _approveOperations(token, address(dolomiteMargin), _amount);
35:         depositWithdrawalProxy.depositWeiIntoDefaultAccount(marketId, _amount);
36:         // Update token
37:         _updateTokenInRegistry(token);
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", false
40:         );
41:     }

43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
44:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
45:         depositWithdrawalProxy.withdrawWeiFromDefaultAccount(
46:             marketId, _amount, AccountBalanceHelper.BalanceCheckFlag.None
47:         );
48:         // Update token
49:         _updateTokenInRegistry(token);
50:         (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));
51:         if (markets.length == 0) {
52:             registry.updateHoldingPosition(
53:                 vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true
54:             );
55:         }
56:     }

58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager
61:         nonReentrant
62:     {
63:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
64: 
65:         if (!registry.isTokenTrusted(vaultId, token, address(this))) {
66:             revert IConnector_UntrustedToken(token);
67:         }
68:         // borrow
69:         borrowPositionProxy.openBorrowPosition(
70:             0, accountId, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
71:         );
72:         registry.updateHoldingPosition(
73:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
74:         );
75:     }

77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
78:         public
79:         onlyManager
80:         nonReentrant
81:     {
82:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
83: 
84:         if (!registry.isTokenTrusted(vaultId, token, address(this))) {
85:             revert IConnector_UntrustedToken(token);
86:         }
87:         if (borrowOrRepay) {
88:             borrowPositionProxy.transferBetweenAccounts(
89:                 accountId, 0, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
90:             );
91:         } else {
92:             borrowPositionProxy.transferBetweenAccounts(
93:                 0, accountId, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
94:             );
95:         }
96:     }

98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
99:         // repay
100:         borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds);
101:         registry.updateHoldingPosition(
102:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
103:         );
104:     }

```


*GitHub* : [30](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L30-L41), [43](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L43-L56), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L58-L75), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L77-L96), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L98-L104)

```solidity
📁 File: contracts/connectors/FraxConnector.sol

38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant
42:     {
43:         bytes32 positionId =
44:             registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));
45:         IERC20 token = IERC20(pool.collateralContract());
46:         if (collateralAmount > 0) {
47:             _approveOperations(address(token), address(pool), collateralAmount);
48:         }
49:         if (borrowAmount > 0) {
50:             pool.borrowAsset(borrowAmount, collateralAmount, address(this));
51:             _updateTokenInRegistry(pool.asset());
52:         } else if (collateralAmount > 0) {
53:             pool.addCollateral(collateralAmount, address(this));
54:         }
55:         if (collateralAmount > 0) {
56:             _updateTokenInRegistry(address(token));
57:         }
58:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
59:         verifyHealthFactor(pool);
60:         emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount);
61:     }

68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant {
69:         uint256 currentCollateral = pool.userCollateralBalance(address(this));
70:         if (withdrawAmount == currentCollateral) {
71:             bytes32 positionId =
72:                 registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));
73: 
74:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
75:         }
76:         pool.removeCollateral(withdrawAmount, address(this));
77:         _updateTokenInRegistry(pool.collateralContract());
78:         verifyHealthFactor(pool);
79:         emit Withdraw(address(pool), withdrawAmount);
80:     }

87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
88:         uint256 repayTokenAmount = pool.toBorrowAmount(sharesToRepay, true);
89:         uint256 sharesOwed = pool.userBorrowShares(address(this));
90:         address asset = pool.asset();
91:         if (sharesToRepay > sharesOwed) {
92:             revert IConnector_InvalidInput();
93:         }
94:         _approveOperations(asset, address(pool), repayTokenAmount);
95:         IFraxPair(pool).repayAsset(sharesToRepay, address(this));
96:         _updateTokenInRegistry(asset);
97:         emit Repay(address(pool), sharesToRepay);
98:     }

```


*GitHub* : [38](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L38-L61), [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L68-L80), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L87-L98)

```solidity
📁 File: contracts/connectors/GearBoxV3.sol

41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant {
42:         ICreditFacadeV3(facade).closeCreditAccount(creditAccount, new MultiCall[](0));
43: 
44:         registry.updateHoldingPosition(
45:             vaultId,
46:             registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),
47:             abi.encode(creditAccount),
48:             "",
49:             true
50:         );
51:         emit CloseAccount(facade, creditAccount);
52:     }

62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {
69:         for (uint256 i = 0; i < calls.length; i++) {
70:             if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
71:             bytes4 method = bytes4(calls[i].callData[:4]);
72: 
73:             if (method == ICreditFacadeV3Multicall.enableToken.selector) {
74:                 (address token) = abi.decode(calls[i].callData[4:], (address));
75:                 _updateTokenInRegistry(token);
76:             }
77:         }
78:         if (approvalToken != address(0)) {
79:             _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount);
80:         }
81:         ICreditFacadeV3(facade).multicall(creditAccount, calls);
82:         if (approvalToken != address(0)) {
83:             _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());
84:         }
85:         emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);
86:     }

```


*GitHub* : [41](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L41-L52), [62](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/GearBoxV3.sol#L62-L86)

```solidity
📁 File: contracts/connectors/LidoConnector.sol

37:     function deposit(uint256 amountIn) external onlyManager nonReentrant {
38:         IWETH(weth).withdraw(amountIn);
39:         // deposit recieved eth into Lido
40:         // refferal address can be different
41:         ILido(lido).submit{ value: amountIn }(address(0));
42:         _updateTokenInRegistry(steth);
43:         _updateTokenInRegistry(weth);
44:         emit Deposit(amountIn);
45:     }

51:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant {
52:         _approveOperations(steth, lidoWithdrawal, amount);
53:         // prepare inputs for requestWithdrawals
54:         uint256[] memory amounts = new uint256[](1);
55:         amounts[0] = amount;
56:         // request for withdrawal
57:         uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this));
58:         bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, "");
59:         registry.updateHoldingPosition(vaultId, positionId, abi.encode(requestIds[0]), abi.encode(amount), false);
60: 
61:         _updateTokenInRegistry(steth);
62:         emit RequestWithdrawals(amount);
63:     }

69:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant {
70:         // approve to lidoWithdrawal to spend withdrawal NFT
71:         ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);
72:         // eth balance before claim
73:         uint256 beforeClaimBalance = address(this).balance;
74:         // claim request withdrawal
75:         ILidoWithdrawal(lidoWithdrawal).claimWithdrawal(requestId);
76:         // emit ClaimWithdrawal event
77:         IWETH(weth).deposit{ value: address(this).balance - beforeClaimBalance }();
78:         registry.updateHoldingPosition(
79:             vaultId,
80:             registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, ""),
81:             abi.encode(requestId),
82:             "",
83:             true
84:         );
85:         _updateTokenInRegistry(weth);
86:         emit ClaimWithdrawal(requestId);
87:     }

```


*GitHub* : [37](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L37-L45), [51](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L51-L63), [69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L69-L87)

```solidity
📁 File: contracts/connectors/MaverickConnector.sol

64:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant {
65:         // approve veMav to spend mav
66:         _approveOperations(mav, veMav, amount);
67:         // stake mav
68:         IveMAV(veMav).stake(amount, duration, doDelegation);
69:         _updateTokenInRegistry(mav);
70:         _updateTokenInRegistry(veMav);
71:         emit Stake(amount, duration, doDelegation);
72:     }

78:     function unstake(uint256 lockupId) external onlyManager nonReentrant {
79:         // unstake veMav
80:         IveMAV(veMav).unstake(lockupId);
81:         _updateTokenInRegistry(mav);
82:         _updateTokenInRegistry(veMav);
83:         emit Unstake(lockupId);
84:     }

91:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant {
92:         uint256 sendEthAmount = p.ethPoolIncluded ? p.tokenARequiredAllowance : 0;
93:         _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); // TODO: check token A is eth
94:         _approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);
95:         // add liquidity
96:         uint256 tokenId;
97:         {
98:             (tokenId,,,) = IMaverickRouter(maverickRouter).addLiquidityToPool{ value: sendEthAmount }(
99:                 p.pool, 0, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline
100:             );
101:         }
102:         registry.updateHoldingPosition(
103:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false
104:         );
105:         _updateTokenInRegistry(p.pool.tokenA());
106:         _updateTokenInRegistry(p.pool.tokenB());
107:         emit AddLiquidityInMaverickPool(p);
108:     }

115:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
116:         external
117:         onlyManager
118:         nonReentrant
119:     {
120:         IMaverickPosition position = IMaverickRouter(maverickRouter).position();
121:         position.approve(maverickRouter, p.tokenId);
122:         IMaverickRouter(maverickRouter).removeLiquidity(
123:             p.pool, address(this), p.tokenId, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline
124:         );
125:         registry.updateHoldingPosition(
126:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true
127:         );
128:         _updateTokenInRegistry(p.pool.tokenA());
129:         _updateTokenInRegistry(p.pool.tokenB());
130:         emit RemoveLiquidityFromMaverickPool(p);
131:     }

137:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {
138:         IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));
139:         uint8 tokenIndex;
140:         for (uint256 i = 0; i < earnedInfo.length; i++) {
141:             if (earnedInfo[i].earned != 0) {
142:                 tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken));
143:                 rewardContract.getReward(address(this), tokenIndex);
144:             }
145:         }
146:         emit ClaimBoostedPositionRewards(rewardContract);
147:     }

```


*GitHub* : [64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L64-L72), [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L78-L84), [91](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L91-L108), [115](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L115-L131), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L137-L147)

```solidity
📁 File: contracts/connectors/MorphoBlueConnector.sol

35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {
36:         MarketParams memory params = morphoBlue.idToMarketParams(id);
37:         if (sOrC) {
38:             _approveOperations(params.loanToken, address(morphoBlue), amount);
39:             morphoBlue.supply(params, amount, 0, address(this), "");
40:             _updateTokenInRegistry(params.loanToken);
41:         } else {
42:             _approveOperations(params.collateralToken, address(morphoBlue), amount);
43:             morphoBlue.supplyCollateral(params, amount, address(this), "");
44:             _updateTokenInRegistry(params.collateralToken);
45:         }
46:         registry.updateHoldingPosition(
47:             vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false
48:         );
49:         emit Supply(amount, id, sOrC);
50:     }

58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {
59:         MarketParams memory params = morphoBlue.idToMarketParams(id);
60:         if (sOrC) {
61:             morphoBlue.withdraw(params, amount, 0, address(this), address(this));
62:         } else {
63:             morphoBlue.withdrawCollateral(params, amount, address(this), address(this));
64:         }
65:         Position memory p = morphoBlue.position(id, address(this));
66:         if (p.collateral == 0 && p.supplyShares == 0) {
67:             registry.updateHoldingPosition(
68:                 vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true
69:             );
70:         }
71:         _updateTokenInRegistry(params.collateralToken);
72:         emit Withdraw(amount, id, sOrC);
73:     }

80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant {
81:         MarketParams memory market = morphoBlue.idToMarketParams(id);
82:         morphoBlue.borrow(market, amount, 0, address(this), address(this));
83:         if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {
84:             revert IConnector_LowHealthFactor(getHealthFactor(id, morphoBlue.market(id)));
85:         }
86:         _updateTokenInRegistry(market.loanToken);
87:         emit Borrow(amount, id);
88:     }

95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant {
96:         MarketParams memory params = morphoBlue.idToMarketParams(id);
97:         _approveOperations(params.loanToken, address(morphoBlue), amount);
98:         morphoBlue.repay(params, amount, 0, address(this), "");
99:         _updateTokenInRegistry(params.loanToken);
100:         emit Repay(amount, id);
101:     }

```


*GitHub* : [35](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L35-L50), [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L58-L73), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L80-L88), [95](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L95-L101)

```solidity
📁 File: contracts/connectors/PancakeswapConnector.sol

31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant {
32:         IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId);
33:         emit SendPositionToMasterChef(tokenId);
34:     }

40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant {
41:         masterchef.updateLiquidity(tokenId);
42:         _updateTokenInRegistry(masterchef.CAKE());
43:         emit UpdatePosition(tokenId);
44:     }

50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant {
51:         masterchef.withdraw(tokenId, address(this));
52:         _updateTokenInRegistry(masterchef.CAKE());
53:         emit Withdraw(tokenId);
54:     }

```


*GitHub* : [31](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L31-L34), [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L40-L44), [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PancakeswapConnector.sol#L50-L54)

```solidity
📁 File: contracts/connectors/PendleConnector.sol

78:     function supply(address market, uint256 amount) external onlyManager nonReentrant {
79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
80: 
81:         (, address _underlyingToken,) = _SY.assetInfo();
82: 
83:         _approveOperations(_underlyingToken, address(_SY), amount);
84:         // Mint SY from underlying token
85:         uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);
86: 
87:         bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));
88:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
89:         emit Supply(market, syMinted);
90:     }

97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant {
98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
99:         IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);
100:         _YT.mintPY(address(this), address(this));
101:         emit MintPTAndYT(market, syAmount);
102:     }

112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {
113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
114:         IERC20(address(_SY)).safeTransfer(address(market), SYamount);
115:         IERC20(address(_PT)).safeTransfer(address(market), PTamount);
116:         market.mint(address(this), SYamount, PTamount);
117:         market.skim();
118:         emit DepositIntoMarket(address(market), SYamount, PTamount);
119:     }

126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {
127:         _approveOperations(_market, pendleMarketDepositHelper.pendleStaking(), _amount);
128:         pendleMarketDepositHelper.depositMarket(_market, _amount);
129:         emit DepositIntoPenpie(_market, _amount);
130:     }

137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant {
138:         pendleMarketDepositHelper.withdrawMarketWithClaim(_market, _amount, true);
139:         emit WithdrawFromPenpie(_market, _amount);
140:     }

183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant
187:     {
188:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
189:         IERC20(address(_PT)).safeTransfer(address(market), exactPTIn);
190:         (uint256 netSyOut, uint256 netSyFee) = market.swapExactPtForSy(address(this), exactPTIn, swapData);
191:         if (netSyOut < minSY) {
192:             revert InsufficientSyOut(netSyOut, minSY);
193:         }
194:         market.skim();
195:         emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY);
196:     }

203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {
204:         IERC20(address(market)).safeTransfer(address(market), amount);
205:         market.burn(address(this), address(market), amount);
206:         market.skim();
207:         emit BurnLP(address(market), amount);
208:     }

216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {
217:         (IPStandardizedYield SY,,) = market.readTokens();
218:         (, address _underlyingToken,) = SY.assetInfo();
219: 
220:         // redeems an amount of base tokens by burning SY
221:         IERC20(address(SY)).safeTransfer(address(SY), _amount);
222:         IPStandardizedYield(address(SY)).redeem(address(this), _amount, _underlyingToken, 1, true);
223:         if (closePosition && isMarketEmpty(market)) {
224:             registry.updateHoldingPosition(
225:                 vaultId,
226:                 registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)),
227:                 "",
228:                 "",
229:                 true
230:             );
231:         }
232:         emit DecreasePosition(address(market), _amount, closePosition);
233:     }

241:     function claimRewards(IPMarket market) external onlyManager nonReentrant {
242:         market.redeemRewards(address(this));
243:         address[] memory rewardTokens = market.getRewardTokens();
244:         for (uint256 i = 0; i < rewardTokens.length; i++) {
245:             _updateTokenInRegistry(rewardTokens[i]);
246:         }
247:         emit ClaimRewards(address(market));
248:     }

```


*GitHub* : [78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L78-L90), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L97-L102), [112](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L112-L119), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L126-L130), [137](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L137-L140), [183](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L183-L196), [203](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L203-L208), [216](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L216-L233), [241](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L241-L248)

```solidity
📁 File: contracts/connectors/PrismaConnector.sol

33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant {
34:         if (approve) {
35:             bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
36: 
37:             if (!registry.isPositionTrustedForConnector(vaultId, positionId, address(this))) {
38:                 revert IConnector_InvalidPosition(positionId);
39:             }
40:         }
41:         IBorrowerOperations(zap.borrowerOps()).setDelegateApproval(address(zap), approve);
42:     }

52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {
57:         bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
58:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
59:         address collateral = abi.decode(positionInfo.additionalData, (address));
60:         address debTtoken = ITroveManager(tm).debtToken();
61:         _approveOperations(collateral, address(zap), dAmount);
62:         zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));
63:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
64:         _updateTokenInRegistry(collateral);
65:         _updateTokenInRegistry(debTtoken);
66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);
67:     }

75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {
76:         bytes32 positionId =
77:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));
78:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
79:         if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {
80:             revert IConnector_InvalidPosition(positionId);
81:         }
82:         address collateral = abi.decode(positionInfo.additionalData, (address));
83:         _approveOperations(collateral, address(zapContract), amountIn);
84:         zapContract.addColl(tm, amountIn, address(this), address(this));
85:         emit AddColl(address(zapContract), tm, amountIn);
86:     }

97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant {
105:         bytes32 positionId =
106:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));
107:         if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {
108:             revert IConnector_InvalidPosition(positionId);
109:         }
110:         IBorrowerOperations borrowerOps = zapContract.borrowerOps();
111:         if (bAmount > 0 && !isBorrowing) {
112:             _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount);
113:         }
114:         borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this));
115:         _updateTokenInRegistry(ITroveManager(tm).debtToken());
116:         // get health factor
117:         uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));
118:         if (minimumHealthFactor > healthFactor) {
119:             revert IConnector_LowHealthFactor(healthFactor);
120:         }
121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);
122:     }

129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant {
130:         bytes32 positionId =
131:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, troveManager));
132:         IBorrowerOperations borrowerOperations = zapContract.borrowerOps();
133:         borrowerOperations.closeTrove(troveManager, address(this));
134:         registry.updateHoldingPosition(vaultId, positionId, "", "", true);
135:         emit CloseTrove(address(zapContract), troveManager);
136:     }

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L33-L42), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L52-L67), [75](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L75-L86), [97](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L97-L122), [129](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L129-L136)

```solidity
📁 File: contracts/connectors/SiloConnector.sol

33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant {
34:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
35:         _approveOperations(dToken, address(silo), amount);
36:         silo.deposit(dToken, amount, oC);
37:         _updateTokenInRegistry(dToken);
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", false
40:         );
41:         emit Deposit(siloToken, dToken, amount, oC);
42:     }

52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant
56:     {
57:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
58:         silo.withdraw(wToken, amount, oC);
59:         _updateTokenInRegistry(wToken);
60:         if (closePosition && isSiloEmpty(silo)) {
61:             registry.updateHoldingPosition(
62:                 vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true
63:             );
64:         }
65:         if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) {
66:             revert IConnector_LowHealthFactor(0);
67:         }
68:         emit Withdraw(siloToken, wToken, amount, oC, closePosition);
69:     }

85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {
86:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
87:         silo.borrow(bToken, amount);
88:         _updateTokenInRegistry(bToken);
89:         emit Borrow(siloToken, bToken, amount);
90:     }

98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {
99:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
100:         _approveOperations(rToken, address(silo), amount);
101:         silo.repay(rToken, amount);
102:         _updateTokenInRegistry(rToken);
103:         if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) {
104:             revert IConnector_LowHealthFactor(0);
105:         }
106:         emit Repay(siloToken, rToken, amount);
107:     }

```


*GitHub* : [33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L33-L42), [52](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L52-L69), [85](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L85-L90), [98](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L98-L107)

```solidity
📁 File: contracts/connectors/StargateConnector.sol

49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {
50:         address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;
51:         address underlyingToken = IStargatePool(lpAddress).token();
52:         if (depositRequest.routerAmount > 0) {
53:             _approveOperations(underlyingToken, address(stargateRouter), depositRequest.routerAmount);
54:             stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this));
55:             _updateTokenInRegistry(underlyingToken);
56:         }
57:         if (depositRequest.LPStakingAmount > 0) {
58:             uint256 stakingAmount = depositRequest.LPStakingAmount;
59:             if (depositRequest.LPStakingAmount == type(uint256).max) {
60:                 stakingAmount = IERC20(lpAddress).balanceOf(address(this));
61:             }
62:             _approveOperations(lpAddress, address(LPStaking), stakingAmount);
63:             LPStaking.deposit(depositRequest.poolId, stakingAmount);
64:         }
65:         _updateTokenInRegistry(rewardToken);
66:         bytes32 positionId =
67:             registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));
68:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
69:         emit DepositIntoStargatePool(depositRequest);
70:     }

76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant {
77:         address lpAddress = LPStaking.poolInfo(withdrawRequest.poolId).lpToken;
78:         address underlyingToken = IStargatePool(lpAddress).token();
79:         if (withdrawRequest.LPStakingAmount > 0) {
80:             IStargateLPStaking(LPStaking).withdraw(withdrawRequest.poolId, withdrawRequest.LPStakingAmount);
81:         }
82:         if (withdrawRequest.routerAmount > 0) {
83:             stargateRouter.instantRedeemLocal(
84:                 uint16(withdrawRequest.poolId), withdrawRequest.routerAmount, address(this)
85:             );
86:             _updateTokenInRegistry(underlyingToken);
87:         }
88:         uint256 LPAmount = LPStaking.userInfo(withdrawRequest.poolId, address(this)).amount;
89:         if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) {
90:             bytes32 positionId = registry.calculatePositionId(
91:                 address(this), STARGATE_LP_POSITION_TYPE, abi.encode(withdrawRequest.poolId)
92:             );
93:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
94:         }
95:         _updateTokenInRegistry(rewardToken);
96:         emit WithdrawFromStargatePool(withdrawRequest);
97:     }

103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {
104:         LPStaking.deposit(poolId, 0);
105:         _updateTokenInRegistry(rewardToken);
106:         emit ClaimStargateRewards(poolId);
107:     }

```


*GitHub* : [49](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L49-L70), [76](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L76-L97), [103](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L103-L107)

```solidity
📁 File: contracts/connectors/UNIv3Connector.sol

40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {
41:         bytes32 positionId =
42:             registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));
43:         p.recipient = address(this);
44:         // Approve NonfungiblePositionManager to spend `token0` and `token1`.
45:         _approveOperations(p.token0, address(positionManager), p.amount0Desired);
46:         _approveOperations(p.token1, address(positionManager), p.amount1Desired);
47: 
48:         // Supply liquidity to pool.
49:         (tokenId,,,) = positionManager.mint(p);
50:         bytes memory positionData = abi.encode(tokenId);
51:         registry.updateHoldingPosition(
52:             vaultId, positionId, positionData, abi.encode(p.tickLower, p.tickUpper, p.fee), false
53:         );
54:         _updateTokenInRegistry(p.token0);
55:         _updateTokenInRegistry(p.token1);
56:         emit OpenPosition(p, tokenId);
57:     }

63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {
64:         (uint128 currentLiquidity, address token0, address token1) = getCurrentLiquidity(p.tokenId);
65:         if (p.liquidity > currentLiquidity) {
66:             revert IConnector_InvalidAmount();
67:         }
68:         positionManager.decreaseLiquidity(p);
69:         _collectFees(p.tokenId);
70:         _updateTokenInRegistry(token0);
71:         _updateTokenInRegistry(token1);
72: 
73:         if (currentLiquidity == p.liquidity) {
74:             positionManager.burn(p.tokenId);
75:             bytes32 positionId =
76:                 registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(token0, token1));
77:             bytes memory positionData = abi.encode(p.tokenId);
78:             registry.updateHoldingPosition(vaultId, positionId, positionData, "", true);
79:         }
80:         emit DecreasePosition(p);
81:     }

87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {
88:         (, address token0, address token1) = getCurrentLiquidity(p.tokenId);
89:         // Approve NonfungiblePositionManager to spend `token0` and `token1`.
90:         _approveOperations(token0, address(positionManager), p.amount0Desired);
91:         _approveOperations(token1, address(positionManager), p.amount1Desired);
92:         positionManager.increaseLiquidity(p);
93:         _updateTokenInRegistry(token0);
94:         _updateTokenInRegistry(token1);
95:         emit IncreasePosition(p);
96:     }

101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
102:         for (uint256 i = 0; i < tokenIds.length; i++) {
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]);
108:         }
109:     }

```


*GitHub* : [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L40-L57), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L63-L81), [87](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L87-L96), [101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L101-L109)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant {
128:         emit TransferPositionToConnector(tokens, amounts, connector, data);
129:         if (registry.isAnActiveConnector(vaultId, connector)) {
130:             IConnector(connector).addLiquidity(tokens, amounts, data);
131:         }
132:     }

204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {
211:         for (uint256 i = 0; i < tokensIn.length; i++) {
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
218:         }
219:     }

```


*GitHub* : [122](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L122-L132), [204](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L204-L219)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
69:         bytes32 txn = keccak256(abi.encode(bridgeRequest));
70:         emit StartBridgeTransaction(bridgeRequest, txn);
71:         if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) {
72:             revert IConnector_BridgeTransactionNotApproved(txn);
73:         }
74:         if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();
75:         if (
76:             destChainAddress[bridgeRequest.destChainId] == address(0)
77:                 || destChainAddress[bridgeRequest.destChainId] != bridgeRequest.receiverAddress
78:         ) {
79:             revert IConnector_InvalidDestinationChain();
80:         }
81:         approvedBridgeTXN[txn] = 0;
82:         swapHandler.executeBridge(bridgeRequest);
83:         _updateTokenInRegistry(bridgeRequest.inputToken);
84:     }

```


*GitHub* : [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L84)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

90:     function executeSwap(SwapRequest memory _swapRequest)
91:         external
92:         payable
93:         onlyEligibleUser
94:         onlyExistingRoute(_swapRequest.routeId)
95:         nonReentrant
96:         returns (uint256 _amountOut)
97:     {
98:         if (_swapRequest.amount == 0) revert InvalidAmount();
99:         RouteData memory swapImplInfo = routes[_swapRequest.routeId];
100:         if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();
101: 
102:         if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {
103:             // set minAmount so that slippage can be checked
104:             uint256 _slippageTolerance = slippageTolerance[_swapRequest.inputToken][_swapRequest.outputToken];
105:             if (_slippageTolerance == 0) {
106:                 _slippageTolerance = genericSlippageTolerance;
107:             }
108:             INoyaValueOracle _priceOracle = INoyaValueOracle(valueOracle);
109:             uint256 _outputTokenValue =
110:                 _priceOracle.getValue(_swapRequest.inputToken, _swapRequest.outputToken, _swapRequest.amount);
111: 
112:             _swapRequest.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);
113:         }
114: 
115:         _amountOut = ISwapAndBridgeImplementation(swapImplInfo.route).performSwapAction(msg.sender, _swapRequest);
116: 
117:         emit ExecutionCompleted(
118:             _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
119:         );
120:     }

126:     function executeBridge(BridgeRequest calldata _bridgeRequest)
127:         external
128:         payable
129:         onlyEligibleUser
130:         onlyExistingRoute(_bridgeRequest.routeId)
131:         nonReentrant
132:     {
133:         RouteData memory bridgeImplInfo = routes[_bridgeRequest.routeId];
134: 
135:         if (!bridgeImplInfo.isBridge) revert RouteNotAllowedForThisAction();
136: 
137:         ISwapAndBridgeImplementation(bridgeImplInfo.route).performBridgeAction(msg.sender, _bridgeRequest);
138: 
139:         emit BridgeExecutionCompleted(_bridgeRequest);
140:     }

```


*GitHub* : [90](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L120), [126](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L140)

### [L-20]<a name="l-20"></a> Contracts are designed to receive ETH but do not implement function for withdrawal

The following contracts can receive ETH but can not withdraw, ETH is occasionally sent by users will be stuck in those contracts. This functionality also applies to baseTokens resulting in locked tokens and loss of funds.

*There are 2 instance(s) of this issue:*

```solidity
📁 File: contracts/connectors/MaverickConnector.sol

56:     receive() external payable { }

```


*GitHub* : [56](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L56-L56)

```solidity
📁 File: contracts/helpers/LZHelpers/LZHelperSender.sol

27:     receive() external payable { }

```


*GitHub* : [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L27-L27)

### [L-21]<a name="l-21"></a> `onlyOwner` functions not accessible if owner renounces ownership

The owner is able to perform certain privileged activities, but it's possible to set the owner to address(0). This can represent a certain risk if the ownership is renounced for any other reason than by design.

Renouncing ownership will leave the contract without an owner, therefore limiting any functionality that needs authority.

*There are 10 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/NoyaFeeReceiver.sol

23:     function withdrawShares(uint256 amount) external onlyOwner {

27:     function burnShares(uint256 amount) external onlyOwner {

```


*GitHub* : [23](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L23-L23), [27](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/NoyaFeeReceiver.sol#L27-L27)

```solidity
📁 File: contracts/governance/Keepers.sol

42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {

63:     function setThreshold(uint8 _threshold) public onlyOwner {

```


*GitHub* : [42](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L42-L42), [63](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L63-L63)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

45:     function addHandler(address _handler, bool state) external onlyOwner {

55:     function addChain(uint256 _chainId, bool state) external onlyOwner {

65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {

77:     function performSwapAction(address caller, SwapRequest calldata _request)
78:         external
79:         payable
80:         override
81:         onlyHandler
82:         returns (uint256)
83:     {

133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
134:         external
135:         payable
136:         override
137:         onlyHandler
138:     {

193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {

```


*GitHub* : [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45), [55](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55-L55), [65](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L65), [77](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L83), [133](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133-L138), [193](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L193)

### [L-22]<a name="l-22"></a> Sending tokens in a loop

Performing token transfers in a loop in a Solidity contract is generally not recommended due to various reasons. One of these reasons is the 'Fail-Silently' issue.

In a Solidity loop, if one transfer operation fails, it causes the entire transaction to fail. This issue can be particularly troublesome when you're dealing with multiple transfers in one transaction. For instance, if you're looping through an array of recipients to distribute dividends or rewards, a single failed transfer will prevent all the subsequent recipients from receiving their transfers. This could be due to the recipient contract throwing an exception or due to other issues like a gas limit being exceeded.

Moreover, such a design could also inadvertently lead to a situation where a malicious contract intentionally causes a failure when receiving Ether to prevent other participants from getting their rightful transfers. This could open up avenues for griefing attacks in the system.

Resolution: To mitigate this problem, it's typically recommended to follow the 'withdraw pattern' in your contracts instead of pushing payments. In this model, each recipient would be responsible for triggering their own payment. This separates each transfer operation, so a failure in one doesn't impact the others. Additionally, it greatly reduces the chance of malicious interference as the control over fund withdrawal lies with the intended recipient and not with an external loop operation.

*There are 3 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

428:             baseToken.safeTransfer(data.receiver, baseTokenAmount);

```


*GitHub* : [428](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L428-L428)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```


*GitHub* : [181](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L181-L181)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");

```


*GitHub* : [44](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L44-L44)

### [L-23]<a name="l-23"></a> Solidity version `0.8.20` may not work on other chains due to `PUSH0`(Not captured by 4nalyzer)

In Solidity `0.8.20`'s compiler, the default target EVM version has been changed to Shanghai. This version introducesa new opcode called `PUSH0`. However, not all Layer 2 solutions have implemented this opcode yet, leading to deployment failures on thesechains. To overcome this problem, it is recommended to utilize an earlier EVM version.

*There are 1 instance(s) of this issue:*

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

2: pragma solidity 0.8.20;

```


*GitHub* : [2](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L2-L2)

### [L-24]<a name="l-24"></a> State variables not capped at reasonable values

Consider adding minimum/maximum value checks to ensure that the state variables below can never be used to excessively harm users, including via griefing

*There are 8 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

// @audit _depositLimitPerTransaction
668:         depositLimitPerTransaction = _depositLimitPerTransaction;

// @audit _depositTotalAmount
669:         depositLimitTotalAmount = _depositTotalAmount;

// @audit _depositWaitingTime
674:         depositWaitingTime = _depositWaitingTime;

// @audit _withdrawWaitingTime
679:         withdrawWaitingTime = _withdrawWaitingTime;

```


*GitHub* : [668](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L668-L668), [669](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L669-L669), [674](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L674-L674), [679](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L679-L679)

```solidity
📁 File: contracts/governance/NoyaGovernanceBase.sol

// @audit _vaultId
24:         vaultId = _vaultId;

```


*GitHub* : [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/NoyaGovernanceBase.sol#L24-L24)

```solidity
📁 File: contracts/helpers/ConnectorMock2.sol

// @audit _vaultId
24:         vaultId = _vaultId;

```


*GitHub* : [24](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L24-L24)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

// @audit _slippageTolerance
58:         genericSlippageTolerance = _slippageTolerance;

```


*GitHub* : [58](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L58-L58)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

// @audit _period
40:         period = _period;

```


*GitHub* : [40](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L40-L40)

### [L-25]<a name="l-25"></a> Consider implementing two-step procedure for updating protocol addresses

A copy-paste error or a typo may end up bricking protocol functionality, or sending tokens to an address with no known private key. Consider implementing a two-step procedure for updating protocol addresses, where the recipient is set as pending, and must 'accept' the assignment by making an affirmative call. A straight forward way of doing this would be to have the target contracts implement [EIP-165](https://eips.ethereum.org/EIPS/eip-165), and to have the 'set' functions ensure that the recipient is of the right interface type.

*There are 10 instance(s) of this issue:*

```solidity
📁 File: contracts/accountingManager/AccountingManager.sol

135:     function setFeeReceivers(
136:         address _withdrawFeeReceiver,
137:         address _performanceFeeReceiver,
138:         address _managementFeeReceiver
139:     ) public onlyMaintainer {

```


*GitHub* : [135](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L135-L139)

```solidity
📁 File: contracts/accountingManager/Registry.sol

84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {

106:     function addVault(
107:         uint256 vaultId,
108:         address _accountingManager,
109:         address _baseToken,
110:         address _governer,
111:         address _maintainer,
112:         address _maintainerWithoutTimelock,
113:         address _keeperContract,
114:         address _watcher,
115:         address _emergency,
116:         address[] calldata _trustedTokens
117:     ) external onlyRole(MAINTAINER_ROLE) {

158:     function changeVaultAddresses(
159:         uint256 vaultId,
160:         address _governer,
161:         address _maintainer,
162:         address _maintainerWithoutTimelock,
163:         address _keeperContract,
164:         address _watcher,
165:         address _emergency
166:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {

```


*GitHub* : [84](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L84-L84), [106](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L106-L117), [158](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L158-L166)

```solidity
📁 File: contracts/helpers/OmniChainHandler/OmnichainLogic.sol

46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer {

```


*GitHub* : [46](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46-L46)

```solidity
📁 File: contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol

68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     {

80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency {

```


*GitHub* : [68](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L71), [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80)

```solidity
📁 File: contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol

45:     function addHandler(address _handler, bool state) external onlyOwner {

```


*GitHub* : [45](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45)

```solidity
📁 File: contracts/helpers/valueOracle/NoyaValueOracle.sol

61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {

```


*GitHub* : [61](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61)

```solidity
📁 File: contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol

48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer {

```


*GitHub* : [48](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48)

### [L-26]<a name="l-26"></a> Using zero as a parameter

Passing `0` or `0x0` as a function argument can sometimes result in a security issue(e.g. passing zero as the slippage parameter). A historical example is the infamous 0x0 address bug where numerous tokens were lost. This happens because `0` can be interpreted as an uninitialized address, leading to transfers to the `0x0` address, effectively burning tokens. Moreover, `0` as a denominator in division operations would cause a runtime exception. It's also often indicative of a logical error in the caller's code.

Consider using a constant variable with a descriptive name, so it's clear that the argument is intentionally being used, and for the right reasons.

*There are 3 instance(s) of this issue:*

```solidity
📁 File: contracts/connectors/Dolomite.sol

50:         (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));

```


*GitHub* : [50](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/Dolomite.sol#L50-L50)

```solidity
📁 File: contracts/helpers/BaseConnector.sol

212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );

```


*GitHub* : [212](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L212-L214)

```solidity
📁 File: contracts/helpers/LZHelpers/LZHelperSender.sol

80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here

```


*GitHub* : [80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L80-L80)

