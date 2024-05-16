## LightChaser-V3

### Note: Care has been taken to filter out issues already found by 4nalyzer unless the finding included instances which 4nalyzer did not capture.

### Generated for: Code4rena : NOYA

### Generated on: 2024-05-16

## Total findings: 134

### Total Medium findings: 4

### Total Low findings: 37

### Total Gas findings: 46

### Total NonCritical findings: 47

# Summary for Medium findings

| Number | Details | Instances |
|----------|----------|----------|
| [Medium-1] | Privileged functions can create points of failure | 125 |
| [Medium-2] | Contract can't receive NFTs sent with safeTransferFrom method | 1 |
| [Medium-3] | Bridge function must check for native token | 1 |
| [Medium-4] | Function returns non-mutated named return variable | 1 |

# Summary for Low findings

| Number | Details | Instances |
|----------|----------|----------|
| [Low-1] | Subtractions performed on a possibly uninitialized uint  | 1 |
| [Low-2] | Potential division by zero should have zero checks in place  | 5 |
| [Low-3] | Function with two array parameter missing a length check  | 6 |
| [Low-4] | Missing checks for address(0x0) when updating address state variables  | 3 |
| [Low-5] | Code does not follow the best practice of check-effects-interaction  | 7 |
| [Low-6] | Incorrect comparison against a max value  | 2 |
| [Low-7] | Missing empty bytes check when assigning bytes/string state variable  | 1 |
| [Low-8] | Contracts with multiple onlyXYZ modifiers where XYZ is a role can introduce complexities when managing privileges  | 3 |
| [Low-9] | Avoid making withdraw/unstake functions Pausable  | 3 |
| [Low-10] | Greater than comparisons made on state uints that can be set to max  | 4 |
| [Low-11] | Withdraw on tokens which are payable but have no withdraw functionality | 5 |
| [Low-12] | Sending tokens in a for loop | 3 |
| [Low-13] | Contract contains payable functions but no withdraw/sweep function | 3 |
| [Low-14] | Empty receive functions can cause gas issues | 2 |
| [Low-15] | The nonReentrant modifier should be first in a function declaration | 92 |
| [Low-16] | Missing zero address check in constructor | 5 |
| [Low-17] | Use of onlyOwner functions can be lost | 3 |
| [Low-18] | Off-by-one timestamp error | 1 |
| [Low-19] | Constant decimal values | 13 |
| [Low-20] | Calculation will revert when totalSupply() returns zero | 3 |
| [Low-21] | Return values not checked for approve() | 2 |
| [Low-22] | Incorrect withdraw declaration | 8 |
| [Low-23] | Critical functions should have a timelock | 5 |
| [Low-24] | Unbounded loop may run out of gas | 1 |
| [Low-25] | Consider implementing two-step procedure for updating protocol addresses | 2 |
| [Low-26] | Prefer skip over revert model in iteration | 6 |
| [Low-27] | Missing contract-existence checks before low-level calls | 5 |
| [Low-28] | Constructors missing validation | 8 |
| [Low-29] | Vulnerable version of openzeppelin contracts used | 1 |
| [Low-30] | Balances directly compared using ==/!= can be dosed | 5 |
| [Low-31] | Blacklist can be bypassed through front running | 1 |
| [Low-32] | State variables not capped at reasonable values | 5 |
| [Low-33] | Solidity file is susceptible to .selector-related optimizer bug due to the version used | 3 |
| [Low-34] | Functions calling contracts/addresses with transfer hooks are missing reentrancy guards | 8 |
| [Low-35] | Double type casts create complexity within the code | 1 |
| [Low-36] | Events may be emitted out of order due to code not follow the best practice of check-effects-interaction | 24 |
| [Low-37] | Inconsistent checks of address params against address(0) | 5 |
# Summary for NonCritical findings

| Number | Details | Instances |
|----------|----------|----------|
| [NonCritical-1] | Having chainId as a parameter can introduce cross chain replay attacks  | 5 |
| [NonCritical-2] | Functions with unused parameters  | 2 |
| [NonCritical-3] | Consider using time variables when defining time related variables  | 1 |
| [NonCritical-4] | Unnecessary struct attribute prefix  | 2 |
| [NonCritical-5] | Using abi.encodePacked can result in hash collision when used in hashing functions  | 2 |
| [NonCritical-6] | Getting a bool return value does not confirm the existence of a function in an external call  | 1 |
| [NonCritical-7] | Default address(0) can be returned  | 3 |
| [NonCritical-8] | Using zero as a parameter | 22 |
| [NonCritical-9] | Token burning is centralized | 3 |
| [NonCritical-10] | Token minting is centralized | 4 |
| [NonCritical-11] | In functions which accept an address as a parameter, there should be a zero address check to prevent bugs | 130 |
| [NonCritical-12] | Default address values are manually set | 2 |
| [NonCritical-13] | Contract lines should not be longer than 120 characters for readability | 94 |
| [NonCritical-14] | Avoid updating storage when the value hasn't changed | 8 |
| [NonCritical-15] | Specific imports should be used where possible so only used code is imported | 71 |
| [NonCritical-16] | Explicitly define visibility of state variables to prevent misconceptions on what can access the variable | 6 |
| [NonCritical-17] | Contracts should have all public/external functions exposed by interfaces | 231 |
| [NonCritical-18] | Emits without msg.sender parameter | 6 |
| [NonCritical-19] | Functions with array parameters should have length checks in place | 5 |
| [NonCritical-20] | Unused state variables present | 2 |
| [NonCritical-21] | Unused modifiers present | 2 |
| [NonCritical-22] | Defined named returns not used within function  | 21 |
| [NonCritical-23] | Both immutable and constant state variables should be CONSTANT_CASE | 5 |
| [NonCritical-24] | Overly complicated arithmetic | 5 |
| [NonCritical-25] | Use immutable not constant for keccak state variables | 4 |
| [NonCritical-26] | Unused structs present | 2 |
| [NonCritical-27] | Empty bytes check is missing | 42 |
| [NonCritical-28] | Return bool not explicit | 3 |
| [NonCritical-29] | call bypasses function existence check, type checking and argument packing | 3 |
| [NonCritical-30] | Missing events in sensitive functions | 15 |
| [NonCritical-31] | Avoid mutating function parameters | 1 |
| [NonCritical-32] | Don't only depend on Solidity's arithmetic ordering. | 7 |
| [NonCritical-33] | A event should be emitted if a non immutable state variable is set in a constructor | 28 |
| [NonCritical-34] | Non constant/immutable state variables are missing a setter post deployment | 26 |
| [NonCritical-35] | gasLimit should be uint64 | 1 |
| [NonCritical-36] | Contracts use both += 1 and ++ (-- and -= 1) | 1 |
| [NonCritical-37] | Use transfer libraries instead of low level calls | 2 |
| [NonCritical-38] | Use 'using' keyword when using specific imports rather than calling the specific import directly | 3 |
| [NonCritical-39] | Avoid declaring variables with the names of defined functions within the project | 1 |
| [NonCritical-40] | For loop iterates on arrays not indexed | 9 |
| [NonCritical-41] | Constructor with array/string/bytes parameters has no empty array checks | 1 |
| [NonCritical-42] | Consider using AccessControlDefaultAdminRules rather than AccessControl | 2 |
| [NonCritical-43] | Consider using OpenZeppelins SafeCall library when making calls to arbitrary contracts | 1 |
| [NonCritical-44] | It is redundant to store the zero address as a constant state variable | 1 |
| [NonCritical-45] | Avoid using 'owner' or '_owner' as a parameter name | 1 |
| [NonCritical-46] | Modifier checks msg.sender against two addresses. Consider using multiple modifiers for more control | 3 |
| [NonCritical-47] | Redundant function returns constant | 1 |
# Summary for Gas findings

| Number | Details | Instances | Gas |
|----------|----------|----------|----------|
| [Gas-1] | State variables used within a function more than once should be cached to save gas  | 8 | 11200 |
| [Gas-2] | Avoid updating storage when the value hasn't changed  | 1 | 800 |
| [Gas-3] | State variable can be updated more than once in a function  | 2 | 3200 |
| [Gas-4] | Multiple accesses of the same mapping/array key/index should be cached  | 3 | 378 |
| [Gas-5] | bytes.concat() can be used in place of abi.encodePacked  | 1 | 0.0 |
| [Gas-6] | Shortcircuit rules can be be used to optimize some gas usage  | 5 | 136500 |
| [Gas-7] | Using named returns for pure and view functions is cheaper than using regular returns | 94 | 229736 |
| [Gas-8] | x + y is more efficient than using += for state variables (likewise for -=) | 3 | 45 |
| [Gas-9] | There is a 32 byte length threshold for error strings, strings longer than this consume more gas | 2 | 56 |
| [Gas-10] | Usage of smaller uint/int types causes overhead | 29 | 46255 |
| [Gas-11] | Default bool values are manually reset | 1 | 0.0 |
| [Gas-12] | For loops in public or external functions should be avoided due to high gas costs and possible DOS | 25 | 0.0 |
| [Gas-13] | Mappings used within a function more than once should be cached to save gas | 1 | 100 |
| [Gas-14] | Superfluous event fields | 1 | 34 |
| [Gas-15] | String literals passed to abi.encode()/abi.encodePacked() should not be split by commas | 8 | 0.0 |
| [Gas-16] | Consider using OZ EnumerateSet in place of nested mappings | 5 | 25000 |
| [Gas-17] | Using this.<fn>() wastes gas | 1 | 100 |
| [Gas-18] | Use selfBalance() in place of address(this).balance | 3 | 7200 |
| [Gas-19] | Use assembly to emit events | 137 | 713222 |
| [Gas-20] | Use solady library where possible to save gas | 11 | 121000 |
| [Gas-21] | Use assembly in place of abi.decode to extract calldata values more efficiently | 43 | 0.0 |
| [Gas-22] | Identical Deployments Should be Replaced with Clone | 3 | 0.0 |
| [Gas-23] | Where a value is casted more than once, consider caching the result to save gas | 20 | 0.0 |
| [Gas-24] | Unnecessary casting as variable is already of the same type | 2 | 88 |
| [Gas-25] | Simple checks for zero uint can be done using assembly to save gas | 14 | 1176 |
| [Gas-26] | Using nested if to save gas | 49 | 14406 |
| [Gas-27] | Optimize Storage with Byte Truncation for Time Related State Variables | 5 | 50000 |
| [Gas-28] | Using delete instead of setting mapping to 0 saves gas | 1 | 5 |
| [Gas-29] | Stack variable cost less than state variables while used in emiting event | 26 | 6084 |
| [Gas-30] | Low level call can be optimized with assembly | 14 | 48608 |
| [Gas-31] | Remove unused modifiers | 2 | 0.0 |
| [Gas-32] | Inline modifiers used only once | 2 | 0.0 |
| [Gas-33] | Use s.x = s.x + y instead of s.x += y for memory structs (same for -= etc) | 6 | 3600 |
| [Gas-34] | Variable declared within iteration | 6 | 0.0 |
| [Gas-35] | Internal functions only used once can be inlined to save gas | 6 | 1080 |
| [Gas-36] | Constructors can be marked as payable to save deployment gas | 36 | 0.0 |
| [Gas-37] | Empty functions should be removed to save gas | 1 | 0.0 |
| [Gas-38] | There are comparisons to boolean literals (true and false), these can be simplified to save gas | 12 | 2592 |
| [Gas-39] | Only emit event in setter function if the state variable was changed | 21 | 0.0 |
| [Gas-40] | It is a waste of GAS to emit variable literals | 3 | 72 |
| [Gas-41] | Use OZ Array.unsafeAccess() to avoid repeated array length checks | 77 | 12450900 |
| [Gas-42] | Use uint256(1)/uint256(2) instead of true/false to save gas for changes | 11 | 2057000 |
| [Gas-43] | Avoid emitting events in loops | 30 | 337500 |
| [Gas-44] | Consider pre-calculating the address of address(this) to save gas | 167 | 0.0 |
| [Gas-45] | Use 'storage' instead of 'memory' for struct/array state variables | 2 | 8400 |
| [Gas-46] | Use constants instead of type(uint<n>).max | 11 | 0.0 |


## [Medium-1] Privileged functions can create points of failure

### Resolution 
Ensure such accounts are protected and consider implementing multi sig to prevent a single point of failure

Num of instances: 125

### Findings 


<details><summary>Click to show findings</summary>

['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L23-L23)']
```solidity
23:     function withdrawShares(uint256 amount) external onlyOwner  // <= FOUND
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L27-L27)']
```solidity
27:     function burnShares(uint256 amount) external onlyOwner  // <= FOUND
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L232-L236)']
```solidity
232:     function addTrustedPosition(
233:         uint256 vaultId,
234:         uint256 _positionTypeId,
235:         address calculatorConnector,
236:         bool onlyOwner, // <= FOUND
237:         bool _isDebt,
238:         bytes calldata _data,
239:         bytes calldata _additionalData
240:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant 
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L42)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner  // <= FOUND
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L63-L63)']
```solidity
63:     function setThreshold(uint8 _threshold) public onlyOwner  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner  // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52)']
```solidity
52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner  // <= FOUND
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36)']
```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner  // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52)']
```solidity
52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner  // <= FOUND
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45)']
```solidity
45:     function addHandler(address _handler, bool state) external onlyOwner  // <= FOUND
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55-L55)']
```solidity
55:     function addChain(uint256 _chainId, bool state) external onlyOwner  // <= FOUND
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L65)']
```solidity
65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner  // <= FOUND
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L193)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner  // <= FOUND
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L223-L223)']
```solidity
223:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L256)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager // <= FOUND
257:         whenNotPaused
258:         nonReentrant
259:     
```
['[325](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L325-L325)']
```solidity
325:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[357](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L357-L357)']
```solidity
357:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[367](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L367-L367)']
```solidity
367:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L393)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[450](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L450-L450)']
```solidity
450:     function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager  // <= FOUND
```
['[472](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L472-L472)']
```solidity
472:     function recordProfitForFee() public onlyManager nonReentrant  // <= FOUND
```
['[502](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L502-L502)']
```solidity
502:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256)  // <= FOUND
```
['[523](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L523-L523)']
```solidity
523:     function collectPerformanceFees() public onlyManager nonReentrant  // <= FOUND
```
['[545](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L545-L545)']
```solidity
545:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant  // <= FOUND
```
['[105](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L105-L116)']
```solidity
105:     function addVault(
106:         uint256 vaultId,
107:         address _accountingManager, // <= FOUND
108:         address _baseToken,
109:         address _governer,
110:         address _maintainer,
111:         address _maintainerWithoutTimelock,
112:         address _keeperContract,
113:         address _watcher,
114:         address _emergency,
115:         address[] calldata _trustedTokens
116:     ) external onlyRole(MAINTAINER_ROLE)  // <= FOUND
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L45-L45)']
```solidity
45:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L61-L63)']
```solidity
61:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
62:         external
63:         onlyManager // <= FOUND
64:         nonReentrant
65:     
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L80-L80)']
```solidity
80:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant  // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L87-L87)']
```solidity
87:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager  // <= FOUND
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L99-L99)']
```solidity
99:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant  // <= FOUND
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L53-L53)']
```solidity
53:     function supply(DepositData memory data) public onlyManager nonReentrant  // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L79-L79)']
```solidity
79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant  // <= FOUND
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L100-L100)']
```solidity
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant  // <= FOUND
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L106-L106)']
```solidity
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant  // <= FOUND
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L111-L111)']
```solidity
111:     function claim(address pool) public onlyManager nonReentrant  // <= FOUND
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L53-L53)']
```solidity
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant  // <= FOUND
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L64-L70)']
```solidity
64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant  // <= FOUND
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L109-L109)']
```solidity
109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant  // <= FOUND
```
['[115](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L115-L115)']
```solidity
115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant  // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L43-L43)']
```solidity
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant  // <= FOUND
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L64-L66)']
```solidity
64:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
65:         external
66:         onlyManager // <= FOUND
67:         nonReentrant
68:     
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L29-L29)']
```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L48-L48)']
```solidity
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L63-L63)']
```solidity
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant  // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L68-L68)']
```solidity
68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant  // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L81-L81)']
```solidity
81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant  // <= FOUND
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L103-L103)']
```solidity
103:     function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager  // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L117-L119)']
```solidity
117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager // <= FOUND
120:         nonReentrant
121:     
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L160-L162)']
```solidity
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager // <= FOUND
163:         nonReentrant
164:     
```
['[182](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L182-L182)']
```solidity
182:     function withdrawFromConvexBooster(uint256 pid, uint256 amount) public onlyManager  // <= FOUND
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L192-L192)']
```solidity
192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager  // <= FOUND
```
['[202](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L202-L202)']
```solidity
202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager  // <= FOUND
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L212-L212)']
```solidity
212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager  // <= FOUND
```
['[221](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L221-L221)']
```solidity
221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant  // <= FOUND
```
['[233](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L233-L233)']
```solidity
233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant  // <= FOUND
```
['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L247-L247)']
```solidity
247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant  // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L30-L30)']
```solidity
30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant  // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L43-L43)']
```solidity
43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant  // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L58-L60)']
```solidity
58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager // <= FOUND
61:         nonReentrant
62:     
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L77-L79)']
```solidity
77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
78:         public
79:         onlyManager // <= FOUND
80:         nonReentrant
81:     
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L98-L98)']
```solidity
98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant  // <= FOUND
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L38-L40)']
```solidity
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager // <= FOUND
41:         nonReentrant
42:     
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L68-L68)']
```solidity
68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant  // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L87-L87)']
```solidity
87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant  // <= FOUND
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L24-L24)']
```solidity
24:     function openAccount(address facade, uint256 ref) public onlyManager  // <= FOUND
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L41-L41)']
```solidity
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant  // <= FOUND
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L68)']
```solidity
62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant  // <= FOUND
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L36-L36)']
```solidity
36:     function deposit(uint256 amountIn) external onlyManager nonReentrant  // <= FOUND
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L50-L50)']
```solidity
50:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant  // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L68-L68)']
```solidity
68:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant  // <= FOUND
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L63-L63)']
```solidity
63:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant  // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L76-L76)']
```solidity
76:     function unstake(uint256 lockupId) external onlyManager nonReentrant  // <= FOUND
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L88-L88)']
```solidity
88:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant  // <= FOUND
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L111-L113)']
```solidity
111:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
112:         external
113:         onlyManager // <= FOUND
114:         nonReentrant
115:     
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L132-L132)']
```solidity
132:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant  // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L35-L35)']
```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant  // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L58-L58)']
```solidity
58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant  // <= FOUND
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L80-L80)']
```solidity
80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant  // <= FOUND
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L95-L95)']
```solidity
95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant  // <= FOUND
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L31-L31)']
```solidity
31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L40-L40)']
```solidity
40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant  // <= FOUND
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L50-L50)']
```solidity
50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant  // <= FOUND
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L78-L78)']
```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L97-L97)']
```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant  // <= FOUND
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L112-L112)']
```solidity
112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant  // <= FOUND
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L126-L126)']
```solidity
126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant  // <= FOUND
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L137-L137)']
```solidity
137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant  // <= FOUND
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L149-L151)']
```solidity
149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
150:         external
151:         onlyManager // <= FOUND
152:     
```
['[166](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L166-L168)']
```solidity
166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
167:         public
168:         onlyManager // <= FOUND
169:     
```
['[183](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L183-L185)']
```solidity
183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager // <= FOUND
186:         nonReentrant
187:     
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L203-L203)']
```solidity
203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[216](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L216-L216)']
```solidity
216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant  // <= FOUND
```
['[241](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L241-L241)']
```solidity
241:     function claimRewards(IPMarket market) external onlyManager nonReentrant  // <= FOUND
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L33-L33)']
```solidity
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant  // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L54)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager // <= FOUND
55:         nonReentrant
56:     
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L75-L75)']
```solidity
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant  // <= FOUND
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L104)']
```solidity
97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant  // <= FOUND
```
['[129](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L129-L129)']
```solidity
129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant  // <= FOUND
```
['[25](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L25-L25)']
```solidity
25:     function createAccount() public onlyManager  // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L30-L30)']
```solidity
30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager  // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L46-L46)']
```solidity
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager  // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L68-L73)']
```solidity
68:     function delegateIntoPreferredPool(
69:         uint128 _accountId,
70:         address collateralType,
71:         uint256 newCollateralAmountD18,
72:         uint256 leverage
73:     ) public onlyManager  // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L81-L87)']
```solidity
81:     function delegateIntoApprovedPool(
82:         uint256 poolIndex,
83:         uint128 _accountId,
84:         address collateralType,
85:         uint256 newCollateralAmountD18,
86:         uint256 leverage
87:     ) public onlyManager  // <= FOUND
```
['[94](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L94-L96)']
```solidity
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
95:         public
96:         onlyManager // <= FOUND
97:     
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L102-L108)']
```solidity
102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager  // <= FOUND
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L33-L33)']
```solidity
33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant  // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L52-L54)']
```solidity
52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager // <= FOUND
55:         nonReentrant
56:     
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L85-L85)']
```solidity
85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L98-L98)']
```solidity
98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant  // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L49-L49)']
```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant  // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L76-L76)']
```solidity
76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant  // <= FOUND
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L103-L103)']
```solidity
103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L40-L40)']
```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId)  // <= FOUND
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L63-L63)']
```solidity
63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant  // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L87-L87)']
```solidity
87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant  // <= FOUND
```
['[101](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L101-L101)']
```solidity
101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant  // <= FOUND
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L122-L127)']
```solidity
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant  // <= FOUND
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager  // <= FOUND
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L210)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant  // <= FOUND
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57-L57)']
```solidity
57:     function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager  // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68)']
```solidity
68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant  // <= FOUND
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28)']
```solidity
28:     function updateTVLInfo() external onlyManager  // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L79-L79)']
```solidity
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE)  // <= FOUND
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE)  // <= FOUND
```


</details>

## [Medium-2] Contract can't receive NFTs sent with safeTransferFrom method

### Resolution 
The contract under consideration is designed to receive and store ERC721 tokens. However, certain smart wallets or contracts might utilize the `safeTransferFrom` method to send an NFT. The `safeTransferFrom` method checks for the implementation of the `onERC721Received` method when the recipient is a contract. This is to ensure that the recipient contract can appropriately handle ERC721 tokens. Therefore, it's essential for the contract to extend the `ERC721Holder` contract from OpenZeppelin. The `ERC721Holder` contract has the `onERC721Received` method implemented, which allows the contract to correctly receive and store ERC721 tokens sent using `safeTransferFrom`. Do note that the current OZ implementation ERC721 includes a safeTransferFrom function.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L8-L8)']
```solidity
8: contract PancakeswapConnector is UNIv3Connector 
```


</details>

## [Medium-3] Bridge function must check for native token

### Resolution 
Functions that bridge ERC20 tokens often do not interact with Ether (ETH), the native cryptocurrency of Ethereum. In these functions, `msg.value` represents the amount of Ether sent in the transaction. 

When a function is marked as `payable`, it indicates that the function is allowed to receive Ether. However, if these functions are not designed to handle Ether, and someone unintentionally or intentionally sends Ether to these functions, the Ether could be locked in the contract forever, leading to a loss of funds. This is because if the contract does not have a specific function to withdraw or refund this Ether, there's no way to retrieve it.

To mitigate this issue, these functions should explicitly require that `msg.value == 0`. This statement ensures that no Ether is being sent in the transaction. If `msg.value` is not equal to zero, the transaction will revert, thereby preventing accidental loss of Ether. 

In conclusion, requiring `msg.value == 0` in functions that bridge ERC20 tokens ensures that only token transactions are processed, and prevents inadvertent loss of Ether, thereby increasing the security of the contract.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L126)']
```solidity
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


</details>

## [Medium-4] Function returns non-mutated named return variable

### Resolution 
In Solidity, functions often declare named return variables, which are expected to be assigned new values within the function. However, a common issue arises when such a function concludes without actually mutating the named return variable. This results in the function returning the default value of the variable type, which might not be the intended behavior and can lead to incorrect or unexpected outcomes. To avoid this issue, ensure that all named return variables are appropriately assigned within the function. If a function is meant to modify and return a value, it should explicitly do so before reaching the end of its execution path. This practice not only clarifies the function's intent but also prevents potential bugs related to unanticipated return values.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L150-L162)']
```solidity
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
151:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
152:         IFraxPair pool = IFraxPair(abi.decode(positionInfo.data, (address)));
153:         uint256 collateralAmount = pool.userCollateralBalance(address(this));
154:         uint256 borrowerShares = pool.userBorrowShares(address(this));
155:         uint256 _borrowerAmount = pool.toBorrowAmount(borrowerShares, true);
156: 
157:         uint256 borrowValue = _getValue(pool.asset(), base, _borrowerAmount);
158:         uint256 collateralValue = _getValue(pool.collateralContract(), base, collateralAmount);
159:         if (collateralValue > borrowValue) {
160:             return collateralValue - borrowValue;
161:         }
162:         return tvl; // <= FOUND
163:     }
```


</details>

## [Low-1] Subtractions performed on a possibly uninitialized uint 

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L14-L33)']
```solidity
14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) { // <= FOUND
15:         uint256 totalTVL;
16:         uint256 totalDebt;
17:         HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
18:         for (uint256 i = 0; i < positions.length; i++) {
19:             if (positions[i].calculatorConnector == address(0)) {
20:                 continue;
21:             }
22:             uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);
23:             bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);
24:             if (isPositionDebt) {
25:                 totalDebt += tvl;
26:             } else {
27:                 totalTVL += tvl;
28:             }
29:         }
30:         if (totalTVL < totalDebt) {
31:             return 0;
32:         }
33:         return (totalTVL - totalDebt); // <= FOUND
34:     }
```


</details>

## [Low-2] Potential division by zero should have zero checks in place 

### Resolution 
Implement a zero address check for found instances

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L223-L239)']
```solidity
223:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused { // <= FOUND
224:         uint256 middleTemp = depositQueue.middle;
225:         uint64 i = 0;
226: 
227:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
228: 
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
231:                 && i < maxIterations
232:         ) {
233:             i += 1;
234:             DepositRequest storage data = depositQueue.queue[middleTemp];
235: 
236:             uint256 shares = previewDeposit(data.amount);
237:             data.shares = shares;
238:             data.calculationTime = block.timestamp;
239:             emit CalculateDeposit( // <= FOUND
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
242: 
243:             middleTemp += 1;
244:         }
245: 
246:         depositQueue.middle = middleTemp;
247:     }
```
['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L125-L132)']
```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) { // <= FOUND
126:         PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
127:         (address pool) = abi.decode(pBP.data, (address));
128:         uint256 balance = IERC20(pool).balanceOf(address(this));
129:         uint256 totalSupply = IERC20(pool).totalSupply();
130:         (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();
131:         uint256 amount0 = balance * reserve0 / totalSupply; // <= FOUND
132:         uint256 amount1 = balance * reserve1 / totalSupply; // <= FOUND
133:         return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1);
134:     }
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L172)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) { // <= FOUND
163:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
164:         PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
165:         uint256 lpBalance = totalLpBalanceOf(pool);
166:         (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);
167:         uint256 _totalSupply = IERC20(pool.pool).totalSupply();
168: 
169:         uint256 _weight = pool.weights[pool.tokenIndex];
170: 
171:         uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]);
172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply); // <= FOUND
173:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L95)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
88:         (address tokenA, address tokenB) =
89:             abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address, address));
90:         address pool = factory.getPair(tokenA, tokenB);
91:         uint256 totalSupply = IERC20(pool).totalSupply();
92:         (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();
93: 
94:         uint256 balanceThis = IERC20(pool).balanceOf(address(this));
95:         return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply; // <= FOUND
96:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L109-L128)']
```solidity
109:     function getValueFromChainlinkFeed(
110:         AggregatorV3Interface source,
111:         uint256 amountIn,
112:         uint256 sourceTokenUnit,
113:         bool isInverse
114:     ) public view returns (uint256) {
115:         int256 price;
116:         uint256 updatedAt;
117:         (, price,, updatedAt,) = source.latestRoundData();
118:         uint256 uintprice = uint256(price);
119:         if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
120:             revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
121:         }
122:         if (price <= 0) {
123:             revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
124:         }
125:         if (isInverse) {
126:             return (amountIn * sourceTokenUnit) / uintprice; // <= FOUND
127:         }
128:         return (amountIn * uintprice) / (sourceTokenUnit); // <= FOUND
129:     }
```


</details>

## [Low-3] Function with two array parameter missing a length check 

### Resolution 
In Solidity, if two array parameters are used within a function and one of their lengths is used as the for-loop range, it's essential to have a length check. If the arrays are not the same length, you could experience out-of-bounds errors or unintended behavior. This could happen if the function tries to access an index that doesn't exist in the shorter array.

Resolution: Always validate that the lengths of both arrays are the same before entering the loop. Add a require statement at the start of the function to check that both arrays are of equal length. This helps maintain the integrity of the function and prevents potential errors due to differing array lengths. This requirement ensures the function fails early if the arrays don't match, rather than failing unpredictably or silently during execution.

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L185-L191)']
```solidity
185:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
186:         external
187:         onlyVaultMaintainer(vaultId)
188:         vaultExists(vaultId)
189:     {
190:         Vault storage vault = vaults[vaultId];
191:         for (uint256 i = 0; i < _connectorAddresses.length; i++) { // <= FOUND
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]);
194:         }
195:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L64-L77)']
```solidity
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
77:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
79:         }
80: 
81:         IBalancerVault(balancerVault).joinPool(
82:             poolId,
83:             address(this), 
84:             address(this), 
85:             IBalancerVault.JoinPoolRequest(
86:                 tokens,
87:                 amounts,
88:                 abi.encode(
89:                     IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                     amountsWithoutBPT, 
91:                     minBPT 
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
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L211)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {
211:         for (uint256 i = 0; i < tokensIn.length; i++) { // <= FOUND
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
218:         }
219:     }
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L41)']
```solidity
37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
38:         public
39:         onlyMaintainer
40:     {
41:         for (uint256 i = 0; i < baseCurrencies.length; i++) { // <= FOUND
42:             defaultPriceSource[baseCurrencies[i]] = oracles[i];
43:         }
44:         emit UpdatedDefaultPriceSource(baseCurrencies, oracles);
45:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L55)']
```solidity
51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
52:         external
53:         onlyMaintainer
54:     {
55:         for (uint256 i = 0; i < oracle.length; i++) { // <= FOUND
56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
57:         }
58:         emit UpdatedAssetPriceSource(asset, baseToken, oracle);
59:     }
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L66-L70)']
```solidity
66:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
67:         external
68:         onlyMaintainer
69:     {
70:         for (uint256 i = 0; i < assets.length; i++) { // <= FOUND
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);
73:         }
74:     }
```


</details>

## [Low-4] Missing checks for address(0x0) when updating address state variables 

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {
85:         emit updateFlashloanAddress(_flashLoan, flashLoan);
86:         flashLoan = _flashLoan;
87:     }
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L42)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
43:         uint256 numOwnersTemp = numOwners;
44:         for (uint256 i = 0; i < _owners.length; i++) {
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) {
46:                 isOwner[_owners[i]] = true;
47:                 numOwnersTemp++;
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
49:                 isOwner[_owners[i]] = false;
50:                 numOwnersTemp--;
51:             }
52:         }
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
54:         numOwners = numOwnersTemp;
55:         emit UpdateOwners(_owners, addOrRemove);
56:     }
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager {
154:         _updateTokenInRegistry(token);
155:     }
```


</details>

## [Low-5] Code does not follow the best practice of check-effects-interaction 

### Resolution 
The "check-effects-interaction" pattern is a best practice in smart contract development, emphasizing the order of operations in functions to prevent reentrancy attacks. Violations arise when a function interacts with external contracts before settling internal state changes or checks. This misordering can expose the contract to potential threats. To adhere to this pattern, first ensure all conditions or checks are satisfied, then update any internal states, and only after these steps, interact with external contracts or addresses. Rearranging operations to this recommended sequence bolsters contract security and aligns with established best practices in the Ethereum community.

Num of instances: 7

### Findings 


<details><summary>Click to show findings</summary>

['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L160-L169)']
```solidity
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     {
165:         PoolInfo memory poolInfo = _getPoolInfo(pool);
166:         address token = poolInfo.tokens[withdrawIndex];
167:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));
168: 
169:         ICurveSwap(poolInfo.pool).remove_liquidity_one_coin(amount, int128(uint128(withdrawIndex)), minAmount); // <= FOUND
170:         _updateTokenInRegistry(token);
171:         if (totalLpBalanceOf(poolInfo) == 0) {
172:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
173:         }
174:         emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount);
175:     }
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L78-L79)']
```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant { // <= FOUND
79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens(); // <= FOUND
80: 
81:         (, address _underlyingToken,) = _SY.assetInfo();
82: 
83:         _approveOperations(_underlyingToken, address(_SY), amount);
84:         
85:         uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);
86: 
87:         bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));
88:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
89:         emit Supply(market, syMinted);
90:     }
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L60)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {
57:         bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
58:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
59:         address collateral = abi.decode(positionInfo.additionalData, (address));
60:         address debTtoken = ITroveManager(tm).debtToken(); // <= FOUND
61:         _approveOperations(collateral, address(zap), dAmount);
62:         zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));
63:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
64:         _updateTokenInRegistry(collateral);
65:         _updateTokenInRegistry(debTtoken);
66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount);
67:     }
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L117)']
```solidity
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
112:             _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount); // <= FOUND
113:         }
114:         borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this));
115:         _updateTokenInRegistry(ITroveManager(tm).debtToken()); // <= FOUND
116:         
117:         uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this)); // <= FOUND
118:         if (minimumHealthFactor > healthFactor) {
119:             revert IConnector_LowHealthFactor(healthFactor);
120:         }
121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);
122:     }
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L49-L60)']
```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant { // <= FOUND
50:         address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;
51:         address underlyingToken = IStargatePool(lpAddress).token(); // <= FOUND
52:         if (depositRequest.routerAmount > 0) {
53:             _approveOperations(underlyingToken, address(stargateRouter), depositRequest.routerAmount);
54:             stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this));
55:             _updateTokenInRegistry(underlyingToken);
56:         }
57:         if (depositRequest.LPStakingAmount > 0) {
58:             uint256 stakingAmount = depositRequest.LPStakingAmount;
59:             if (depositRequest.LPStakingAmount == type(uint256).max) {
60:                 stakingAmount = IERC20(lpAddress).balanceOf(address(this)); // <= FOUND
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
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L84-L104)']
```solidity
84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
85:         external
86:         returns (uint256)
87:     {
88:         emit TransferTokensToTrustedAddress(token, amount, caller, data);
89:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
90:         if (msg.sender == accountingManager) {
91:             (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);
92: 
93:             (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
94:             Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData);
95: 
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount); // <= FOUND
97:             amount = newAmount;
98:         } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {
99:             IERC20(token).safeTransfer(address(msg.sender), amount); // <= FOUND
100:         } else {
101:             uint256 routeId = abi.decode(data, (uint256));
102:             swapHandler.verifyRoute(routeId, msg.sender);
103:             if (caller != address(this)) revert IConnector_InvalidAddress(caller);
104:             IERC20(token).safeTransfer(msg.sender, amount); // <= FOUND
105:         }
106:         _updateTokenInRegistry(token);
107:         return amount;
108:     }
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60-L74)']
```solidity
60:     function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) { // <= FOUND
61:         uint128 amountIn128 = uint128(amount);
62:         address pool = assetToBaseToPool[tokenIn][baseToken];
63:         if (pool == address(0)) {
64:             pool = assetToBaseToPool[baseToken][tokenIn];
65:         }
66:         if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
67: 
68:         
69:         uint32[] memory secondsAgos = new uint32[](2);
70:         secondsAgos[0] = period;
71:         secondsAgos[1] = 0;
72: 
73:         
74:         (int56[] memory tickCumulatives,) = IUniswapV3Pool(pool).observe(secondsAgos); // <= FOUND
75: 
76:         
77:         int56 tickCumulativesDelta = tickCumulatives[1] - tickCumulatives[0];
78: 
79:         
80:         
81:         int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));
82:         if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {
83:             timeWeightedAverageTick--;
84:         }
85:         _amountOut = OracleLibrary.getQuoteAtTick(timeWeightedAverageTick, amountIn128, tokenIn, baseToken);
86:     }
```


</details>

## [Low-6] Incorrect comparison against a max value 

### Resolution 
Comparing a value using `>= MAX_VALUE` is conceptually incorrect when `MAX_VALUE` is defined as the upper limit that a variable can take. According to the definition of a maximum value, the condition should only revert if the variable is greater than `MAX_VALUE`, not equal to it. Using `>=` can introduce unintended behavior, as the condition will trigger a revert even when the variable reaches its legitimate upper bound. This can lead to bugs and vulnerabilities, as well as hamper the contract's intended functionality. The resolution is to strictly use `>` when making comparisons against a defined `MAX_VALUE` to align with its conceptual definition and to prevent unintended reverts or vulnerabilities.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L301-L301)']
```solidity
301:             if (vault.holdingPositions.length >= maxNumHoldingPositions) { // <= FOUND
```
['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L301-L302)']
```solidity
301:             if (vault.holdingPositions.length >= maxNumHoldingPositions) { // <= FOUND
302:                 revert TooManyPositions(); // <= FOUND
303:             }
```


</details>

## [Low-7] Missing empty bytes check when assigning bytes/string state variable 

### Resolution 
In programming, especially when dealing with dynamically sized types like bytes and strings in Solidity, omitting a check for empty values when assigning to a state variable can lead to unexpected behavior or vulnerabilities. This oversight may allow zero-length or null values to be stored, which could be problematic in contexts where valid data is expected. Implementing explicit checks for empty bytes or strings before assignment ensures data integrity and can prevent potential logic errors or exploits in smart contracts. It's a crucial practice in robust smart contract development to validate data thoroughly before state modifications.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L37)']
```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
37:         messageSetting = _messageSetting; // <= FOUND
38:     }
```


</details>

## [Low-8] Contracts with multiple onlyXYZ modifiers where XYZ is a role can introduce complexities when managing privileges 

### Resolution 
In smart contracts, using multiple `onlyXYZ` modifiers for different roles can complicate privilege management. OpenZeppelin's AccessControl offers a streamlined solution, enabling easier and more flexible role-based permission handling. It simplifies the assignment and revocation of roles compared to multiple individual modifiers, reducing potential errors and improving contract maintainability. This modular approach to access management makes it more straightforward to define, manage, and audit roles and permissions within a contract.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L12-L46)']
```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard {
13:     
15:     bytes32 public constant MAINTAINER_ROLE = keccak256("MAINTAINER_ROLE");
32:     modifier onlyVaultMaintainer(uint256 _vaultId) { // <= FOUND
33:         if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) {
34:             revert UnauthorizedAccess();
35:         }
36:         _;
37:     }
38: 


39:     modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) { // <= FOUND
40:         if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
41:             revert UnauthorizedAccess();
42:         }
43:         _;
44:     }
45: 


46:     modifier onlyVaultGoverner(uint256 _vaultId) { // <= FOUND
47:         if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
48:             revert UnauthorizedAccess();
49:         }
50:         _;
51:     }
52: 


```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L6-L85)']
```solidity
6: contract NoyaGovernanceBase {
7:     PositionRegistry public registry;
8:     uint256 public vaultId;
31:     modifier onlyManager() { // <= FOUND
32:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
33:         if (!(msg.sender == keeperContract || msg.sender == emergencyManager || msg.sender == registry.flashLoan())) {
34:             revert NoyaGovernance_Unauthorized(msg.sender);
35:         }
36:         _;
37:     }


43:     modifier onlyEmergency() { // <= FOUND
44:         (,,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
45:         if (msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);
46:         _;
47:     }
48:     
53:     modifier onlyEmergencyOrWatcher() { // <= FOUND


53:     modifier onlyEmergencyOrWatcher() { // <= FOUND
54:         (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
55:         if (msg.sender != emergencyManager && msg.sender != watcherContract) {
56:             revert NoyaGovernance_Unauthorized(msg.sender);
57:         }
58:         _;
59:     }


65:     modifier onlyMaintainerOrEmergency() { // <= FOUND
66:         (, address maintainer,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
67:         if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender);
68:         _;
69:     }
70:     
75:     modifier onlyMaintainer() { // <= FOUND


75:     modifier onlyMaintainer() { // <= FOUND
76:         (, address maintainer,,,,) = registry.getGovernanceAddresses(vaultId);
77:         if (msg.sender != maintainer) revert NoyaGovernance_Unauthorized(msg.sender);
78:         _;
79:     }
80:     
85:     modifier onlyGovernance() { // <= FOUND


85:     modifier onlyGovernance() { // <= FOUND
86:         (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);
87:         if (msg.sender != governer) revert NoyaGovernance_Unauthorized(msg.sender);
88:         _;
89:     }
90: }


```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10-L29)']
```solidity
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard {
11:     using SafeERC20 for IERC20;
12: 
24:     modifier onlyEligibleUser() { // <= FOUND
25:         require(isEligibleToUse[msg.sender], "NoyaSwapHandler: Not eligible to use");
26:         _;
27:     }
28: 
29:     modifier onlyExistingRoute(uint256 _routeId) { // <= FOUND
30:         if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();


29:     modifier onlyExistingRoute(uint256 _routeId) { // <= FOUND
30:         if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound();
31:         _;
32:     }
33: 
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
35:         NoyaGovernanceBase(_registry, _vaultId)


```


</details>

## [Low-9] Avoid making withdraw/unstake functions Pausable 

### Resolution 
Making withdraw or unstake functions pausable can create a risk by potentially locking users' funds indefinitely, especially in scenarios where the contract is paused for a prolonged period. This design could undermine trust and may not align with the decentralization principles of blockchain. It's advisable to design these functions with user security and accessibility in mind, ensuring that pausing capabilities are used judiciously and transparently, with clear conditions for resuming normal operations.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[367](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L367-L367)']
```solidity
367:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L393)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused  // <= FOUND
```
['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L301-L301)']
```solidity
301:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused  // <= FOUND
```


</details>

## [Low-10] Greater than comparisons made on state uints that can be set to max 

### Resolution 
When state variables (uints) that can be set to their maximum value (type(uint256).max for example) are used in "greater than" comparisons, it introduces a risk of logic errors. If the state variable ever reaches this max value, any comparison expecting it to increment further will fail. This can halt or disrupt contract functionality. To avoid this, implement checks to ensure that the state variable doesn't exceed a certain threshold below the max value.

Num of instances: 4

### Findings 


<details><summary>Click to show findings</summary>

['[198](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L198-L205)']
```solidity
198:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {
199:         if (amount == 0) {
200:             revert NoyaAccounting_INVALID_AMOUNT();
201:         }
202: 
203:         baseToken.safeTransferFrom(msg.sender, address(this), amount);
204: 
205:         if (amount > depositLimitPerTransaction) { // <= FOUND
206:             revert NoyaAccounting_DepositLimitPerTransactionExceeded();
207:         }
208: 
209:         if (TVL() > depositLimitTotalAmount) { // <= FOUND
210:             revert NoyaAccounting_TotalDepositLimitExceeded();
211:         }
212: 
213:         depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);
214:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);
215:         depositQueue.last += 1;
216:         depositQueue.totalAWFDeposit += amount;
217:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L109-L119)']
```solidity
109:     function getValueFromChainlinkFeed(
110:         AggregatorV3Interface source,
111:         uint256 amountIn,
112:         uint256 sourceTokenUnit,
113:         bool isInverse
114:     ) public view returns (uint256) {
115:         int256 price;
116:         uint256 updatedAt;
117:         (, price,, updatedAt,) = source.latestRoundData();
118:         uint256 uintprice = uint256(price);
119:         if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) { // <= FOUND
120:             revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
121:         }
122:         if (price <= 0) {
123:             revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
124:         }
125:         if (isInverse) {
126:             return (amountIn * sourceTokenUnit) / uintprice;
127:         }
128:         return (amountIn * uintprice) / (sourceTokenUnit);
129:     }
```
['[664](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L664-L665)']
```solidity
664:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {
665:         depositLimitPerTransaction = _depositLimitPerTransaction; // <= FOUND
666:         depositLimitTotalAmount = _depositTotalAmount; // <= FOUND
667:         emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount);
668:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L53-L57)']
```solidity
53:     function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer {
54:         if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {
55:             revert NoyaChainlinkOracle_INVALID_INPUT();
56:         }
57:         chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold; // <= FOUND
58:         emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold);
59:     }
```


</details>

## [Low-11] Withdraw on tokens which are payable but have no withdraw functionality

### Resolution 
Executing a `.withdraw` function on an externally determined contract can be risky. Even if the target contract is payable, it might not implement a withdraw function or might implement it differently than expected. If the contract doesn't have a withdraw function, a function call will lead to a transaction failure. Moreover, if the external contract has malevolent code in its `.withdraw` function, it could exploit your contract in unexpected ways. To mitigate this risk, ensure you interact only with trusted contracts, ideally those adhering to standard interfaces like ERC20's `transfer`. Avoid arbitrary calls to `.withdraw` without a clear understanding of the target contract's functionality.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L106-L108)']
```solidity
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant {
107:         address gauge = voter.gauges(pool);
108:         IGauge(gauge).withdraw(liquidity); // <= FOUND
109:     }
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L48-L49)']
```solidity
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {
49:         IComet(_market).withdraw(asset, amount); // <= FOUND
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
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L192-L193)']
```solidity
192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager {
193:         IConvexBasicRewards(pool).withdraw(amount, true); // <= FOUND
194:         emit WithdrawFromConvexRewardPool(pool, amount);
195:     }
```
['[202](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L202-L203)']
```solidity
202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager {
203:         IRewardsGauge(pool).withdraw(amount); // <= FOUND
204:         emit WithdrawFromGauge(pool, amount);
205:     }
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L212-L213)']
```solidity
212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager {
213:         IDepositToken(depostiToken).withdraw(address(this), amount); // <= FOUND
214:         emit WithdrawFromPrisma(depostiToken, amount);
215:     }
```


</details>

## [Low-12] Sending tokens in a for loop

### Resolution 
Performing token transfers in a loop in a Solidity contract is generally not recommended due to various reasons. One of these reasons is the "Fail-Silently" issue.

In a Solidity loop, if one transfer operation fails, it causes the entire transaction to fail. This issue can be particularly troublesome when you're dealing with multiple transfers in one transaction. For instance, if you're looping through an array of recipients to distribute dividends or rewards, a single failed transfer will prevent all the subsequent recipients from receiving their transfers. This could be due to the recipient contract throwing an exception or due to other issues like a gas limit being exceeded.

Moreover, such a design could also inadvertently lead to a situation where a malicious contract intentionally causes a failure when receiving Ether to prevent other participants from getting their rightful transfers. This could open up avenues for griefing attacks in the system.

Resolution: To mitigate this problem, it's typically recommended to follow the "withdraw pattern" in your contracts instead of pushing payments. In this model, each recipient would be responsible for triggering their own payment. This separates each transfer operation, so a failure in one doesn't impact the others. Additionally, it greatly reduces the chance of malicious interference as the control over fund withdrawal lies with the intended recipient and not with an external loop operation.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L74-L76)']
```solidity
74:            for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]); // <= FOUND
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L74-L76)']
```solidity
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]); // <= FOUND
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L89-L91)']
```solidity
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]); // <= FOUND
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
```


</details>

## [Low-13] Contract contains payable functions but no withdraw/sweep function

### Resolution 
In smart contract development, particularly for Ethereum, having payable functions without a corresponding withdraw or sweep function can lead to potential issues. Payable functions allow the contract to receive Ether, but without a mechanism to withdraw these funds, the Ether can become locked within the contract indefinitely. This situation might be intentional in some cases (like a burn function), but generally, it’s a design oversight. A withdraw or sweep function is necessary to transfer Ether out of the contract to a specific address, typically the owner's or a designated recipient. Without this, the contract lacks flexibility in managing its funds, potentially leading to lost or inaccessible Ether.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L10-L10)']
```solidity
10: contract SwapAndBridgeHandler is NoyaGovernanceBase, ISwapAndBridgeHandler, ReentrancyGuard 
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10-L10)']
```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard 
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L29-L29)']
```solidity
29: contract MaverickConnector is BaseConnector, IERC721Receiver 
```


</details>

## [Low-14] Empty receive functions can cause gas issues

### Resolution 
In Solidity, functions that receive Ether without corresponding functionality to utilize or withdraw these funds can inadvertently lead to a permanent loss of value. This is because if someone sends Ether to the contract, they may be unable to retrieve it. To avoid this, functions receiving Ether should be accompanied by additional methods that process or allow the withdrawal of these funds. If the intent is to use the received Ether, it should trigger a separate function; if not, it should revert the transaction (for instance, via `require(msg.sender == address(weth))`). Access control checks can also prevent unintended Ether transfers, despite the slight gas cost they entail. If concerns over gas costs persist, at minimum, include a rescue function to recover unused Ether. Missteps in handling Ether in smart contracts can lead to irreversible financial losses, hence these precautions are crucial.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[56](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L56-L56)']
```solidity
56:     receive() external payable { }
```
['[56](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L56-L56)']
```solidity
56:     receive() external payable { }
```


</details>

## [Low-15] The nonReentrant modifier should be first in a function declaration

### Resolution 
In Solidity, the `nonReentrant` modifier is essential for securing smart contracts against reentrancy attacks. It should be positioned first in a function declaration. This placement is critical because it ensures that the modifier's protection is applied before any other code or modifiers in the function. If placed later, other modifiers could potentially be executed in a reentrant manner before `nonReentrant` has a chance to lock the function, leaving the contract vulnerable. Thus, prioritizing `nonReentrant` as the first modifier is a best practice for robust smart contract security, effectively guarding against unintended reentries and related exploits.

Num of instances: 92

### Findings 


<details><summary>Click to show findings</summary>

['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L223-L223)']
```solidity
223:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused { // <= FOUND
224:         uint256 middleTemp = depositQueue.middle;
225:         uint64 i = 0;
226: 
227:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
228: 
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
231:                 && i < maxIterations
232:         ) {
233:             i += 1;
234:             DepositRequest storage data = depositQueue.queue[middleTemp];
235: 
236:             uint256 shares = previewDeposit(data.amount);
237:             data.shares = shares;
238:             data.calculationTime = block.timestamp;
239:             emit CalculateDeposit(
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
242: 
243:             middleTemp += 1;
244:         }
245: 
246:         depositQueue.middle = middleTemp;
247:     }
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L258)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant // <= FOUND
259:     {
260:         uint256 firstTemp = depositQueue.first;
261:         uint64 i = 0;
262:         uint256 processedBaseTokenAmount = 0;
263: 
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1;
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1;
280:         }
281:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount;
282: 
283:         totalDepositedAmount += processedBaseTokenAmount;
284: 
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         } else {
292:             revert NoyaAccounting_INVALID_CONNECTOR();
293:         }
294: 
295:         depositQueue.first = firstTemp;
296:     }
```
['[325](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L325-L325)']
```solidity
325:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused { // <= FOUND
326:         uint256 middleTemp = withdrawQueue.middle;
327:         uint64 i = 0;
328:         uint256 processedShares = 0;
329:         uint256 assetsNeededForWithdraw = 0;
330:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
331: 
332:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {
333:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
334:         }
335:         while (
336:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
337:                 && i < maxIterations
338:         ) {
339:             i += 1;
340:             WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
341:             uint256 assets = previewRedeem(data.shares);
342:             data.amount = assets;
343:             data.calculationTime = block.timestamp;
344:             assetsNeededForWithdraw += assets;
345:             processedShares += data.shares;
346:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);
347: 
348:             middleTemp += 1;
349:         }
350:         currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
351:         withdrawQueue.middle = middleTemp;
352:     }
```
['[357](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L357-L357)']
```solidity
357:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused { // <= FOUND
358:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);
359:         currentWithdrawGroup.isStarted = true;
360:         currentWithdrawGroup.lastId = withdrawQueue.middle;
361:         emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);
362:     }
```
['[367](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L367-L367)']
```solidity
367:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused { // <= FOUND
368:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
369:         uint256 neededAssets = neededAssetsForWithdraw();
370: 
371:         if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {
372:             revert NoyaAccounting_NOT_READY_TO_FULFILL();
373:         }
374:         currentWithdrawGroup.isFullfilled = true;
375:         amountAskedForWithdraw = 0;
376:         uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
377:         if (availableAssets >= currentWithdrawGroup.totalCBAmount) {
378:             currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;
379:         } else {
380:             currentWithdrawGroup.totalABAmount = availableAssets;
381:         }
382:         currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;
383:         currentWithdrawGroup.totalCBAmount = 0;
384:         emit WithdrawGroupFulfilled(
385:             currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount
386:         );
387:     }
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L393)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused { // <= FOUND
394:         if (currentWithdrawGroup.isFullfilled == false) {
395:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
396:         }
397:         uint64 i = 0;
398:         uint256 firstTemp = withdrawQueue.first;
399: 
400:         uint256 withdrawFeeAmount = 0;
401:         uint256 processedBaseTokenAmount = 0;
402:         
403:         while (
404:             currentWithdrawGroup.lastId > firstTemp
405:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
406:                 && i < maxIterations
407:         ) {
408:             i += 1;
409:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
410:             uint256 shares = data.shares;
411:             
412:             uint256 baseTokenAmount =
413:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
414: 
415:             withdrawRequestsByAddress[data.owner] -= shares;
416:             _burn(data.owner, shares);
417: 
418:             processedBaseTokenAmount += data.amount;
419:             {
420:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
421:                 withdrawFeeAmount += feeAmount;
422:                 baseTokenAmount = baseTokenAmount - feeAmount;
423:             }
424: 
425:             baseToken.safeTransfer(data.receiver, baseTokenAmount);
426:             emit ExecuteWithdraw(
427:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
428:             );
429:             delete withdrawQueue.queue[firstTemp];
430:             
431:             firstTemp += 1;
432:         }
433:         totalWithdrawnAmount += processedBaseTokenAmount;
434: 
435:         if (withdrawFeeAmount > 0) {
436:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);
437:         }
438:         withdrawQueue.first = firstTemp;
439:         
440:         if (currentWithdrawGroup.lastId == firstTemp) {
441:             delete currentWithdrawGroup;
442:         }
443:     }
```
['[472](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L472-L472)']
```solidity
472:     function recordProfitForFee() public onlyManager nonReentrant { // <= FOUND
473:         storedProfitForFee = getProfit();
474:         profitStoredTime = block.timestamp;
475: 
476:         if (storedProfitForFee < totalProfitCalculated) {
477:             return;
478:         }
479: 
480:         preformanceFeeSharesWaitingForDistribution =
481:             previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);
482:         emit RecordProfit(
483:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
484:         );
485:     }
```
['[502](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L502-L502)']
```solidity
502:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) { // <= FOUND
503:         if (block.timestamp - lastFeeDistributionTime < 1 days) {
504:             return (0, 0);
505:         }
506:         uint256 timePassed = block.timestamp - lastFeeDistributionTime;
507:         if (timePassed > 10 days) {
508:             timePassed = 10 days;
509:         }
510:         uint256 totalShares = totalSupply();
511:         uint256 currentFeeShares = balanceOf(managementFeeReceiver) + balanceOf(performanceFeeReceiver)
512:             + preformanceFeeSharesWaitingForDistribution;
513: 
514:         uint256 managementFeeAmount =
515:             (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;
516:         _mint(managementFeeReceiver, managementFeeAmount);
517:         emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares);
518:         lastFeeDistributionTime = block.timestamp;
519:         return (managementFeeAmount, timePassed);
520:     }
```
['[523](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L523-L523)']
```solidity
523:     function collectPerformanceFees() public onlyManager nonReentrant { // <= FOUND
524:         if (
525:             preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours
526:                 || block.timestamp - profitStoredTime > 48 hours
527:         ) {
528:             return;
529:         }
530: 
531:         _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);
532: 
533:         totalProfitCalculated = storedProfitForFee;
534: 
535:         emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);
536: 
537:         preformanceFeeSharesWaitingForDistribution = 0;
538:     }
```
['[545](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L545-L545)']
```solidity
545:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant { // <= FOUND
546:         uint256 amountAskedForWithdraw_temp = 0;
547:         uint256 neededAssets = neededAssetsForWithdraw();
548:         for (uint256 i = 0; i < retrieveData.length; i++) {
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
566:         amountAskedForWithdraw += amountAskedForWithdraw_temp;
567:         if (amountAskedForWithdraw_temp > neededAssets) {
568:             revert NoyaAccounting_INVALID_AMOUNT();
569:         }
570:     }
```
['[680](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L680-L680)']
```solidity
680:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { // <= FOUND
681:         if (token == address(0)) {
682:             (bool success,) = payable(msg.sender).call{ value: amount }("");
683:             require(success, "Transfer failed.");
684:         } else {
685:             IERC20(token).safeTransfer(msg.sender, amount);
686:         }
687:         emit Rescue(msg.sender, token, amount);
688:     }
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L232-L240)']
```solidity
232:     function addTrustedPosition(
233:         uint256 vaultId,
234:         uint256 _positionTypeId,
235:         address calculatorConnector,
236:         bool onlyOwner,
237:         bool _isDebt,
238:         bytes calldata _data,
239:         bytes calldata _additionalData
240:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant { // <= FOUND
241:         Vault storage vault = vaults[vaultId];
242:         bytes32 positionId = calculatePositionId(calculatorConnector, _positionTypeId, _data);
243:         {
244:             if (vault.trustedPositionsBP[positionId].isEnabled) revert AlreadyExists();
245:             if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();
246:             address[] memory usingTokens = IConnector(calculatorConnector).getUnderlyingTokens(_positionTypeId, _data);
247:             for (uint256 i = 0; i < usingTokens.length; i++) {
248:                 if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) {
249:                     revert TokenNotTrusted(usingTokens[i]);
250:                 }
251:             }
252: 
253:             vault.trustedPositionsBP[positionId] =
254:                 PositionBP(calculatorConnector, _positionTypeId, onlyOwner, true, _isDebt, _data, _additionalData);
255:         }
256:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data);
257:     }
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L45-L45)']
```solidity
45:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant { // <= FOUND
46:         _approveOperations(supplyToken, pool, amount);
47:         IPool(pool).supply(supplyToken, amount, address(this), 0);
48:         registry.updateHoldingPosition(
49:             vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", false
50:         );
51:         _updateTokenInRegistry(supplyToken);
52:         emit Supply(supplyToken, amount);
53:     }
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L61-L64)']
```solidity
61:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
62:         external
63:         onlyManager
64:         nonReentrant // <= FOUND
65:     {
66:         if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {
67:             revert IConnector_UntrustedToken(_borrowAsset);
68:         }
69:         IPool(pool).borrow(_borrowAsset, _amount, _interestRateMode, 0, address(this));
70:         
71:         (,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));
72:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
73:         _updateTokenInRegistry(_borrowAsset);
74:         emit Borrow(_borrowAsset, _amount);
75:     }
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L80-L80)']
```solidity
80:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant { // <= FOUND
81:         _approveOperations(asset, pool, amount);
82:         IPool(pool).repay(asset, amount, i, address(this));
83:         _updateTokenInRegistry(asset);
84:         emit Repay(asset, amount, i);
85:     }
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L99-L99)']
```solidity
99:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant { // <= FOUND
100:         IPool(pool).withdraw(_collateral, _collateralAmount, address(this));
101:         
102:         (uint256 totalCollateralBase,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));
103:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
104:         _updateTokenInRegistry(_collateral);
105:         if (totalCollateralBase <= DUST_LEVEL * 1e7) {
106:             registry.updateHoldingPosition(
107:                 vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", true
108:             );
109:         }
110:         emit WithdrawCollateral(_collateral, _collateralAmount);
111:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L53-L53)']
```solidity
53:     function supply(DepositData memory data) public onlyManager nonReentrant { // <= FOUND
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
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L79-L79)']
```solidity
79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant { // <= FOUND
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
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L100-L100)']
```solidity
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant { // <= FOUND
101:         address gauge = voter.gauges(pool);
102:         IERC20(pool).forceApprove(address(gauge), liquidity);
103:         IGauge(gauge).deposit(liquidity, address(this));
104:     }
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L106-L106)']
```solidity
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant { // <= FOUND
107:         address gauge = voter.gauges(pool);
108:         IGauge(gauge).withdraw(liquidity);
109:     }
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L111-L111)']
```solidity
111:     function claim(address pool) public onlyManager nonReentrant { // <= FOUND
112:         address gauge = voter.gauges(pool);
113:         IGauge(gauge).getReward(address(this));
114:         _updateTokenInRegistry(IGauge(gauge).rewardToken());
115:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L53-L53)']
```solidity
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant { // <= FOUND
54:         for (uint256 i = 0; i < rewardsPools.length; i++) {
55:             IRewardPool baseRewardPool = IRewardPool(rewardsPools[i]);
56:             baseRewardPool.getReward();
57:         }
58:         _updateTokenInRegistry(address(AURA));
59:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L64-L70)']
```solidity
64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant { // <= FOUND
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
83:             address(this), 
84:             address(this), 
85:             IBalancerVault.JoinPoolRequest(
86:                 tokens,
87:                 amounts,
88:                 abi.encode(
89:                     IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                     amountsWithoutBPT, 
91:                     minBPT 
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
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L109-L109)']
```solidity
109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant { // <= FOUND
110:         (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);
111:         _approveOperations(_poolInfo.pool, _poolInfo.auraPoolAddress, _amount);
112:         IRewardPool(_poolInfo.auraPoolAddress).deposit(_amount, address(this));
113:     }
```
['[115](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L115-L115)']
```solidity
115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant { // <= FOUND
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
132:                 address(this), 
133:                 payable(address(this)), 
134:                 IBalancerVault.ExitPoolRequest(
135:                     tokens,
136:                     _amounts,
137:                     abi.encode(
138:                         IBalancerVault.ExitKind.EXACT_BPT_IN_FOR_ONE_TOKEN_OUT,
139:                         p._lpAmount,
140:                         p.withdrawIndex 
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
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L43-L43)']
```solidity
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant { // <= FOUND
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
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L64-L67)']
```solidity
64:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
65:         external
66:         onlyManager
67:         nonReentrant // <= FOUND
68:     {
69:         address pool = factory.getPair(p.tokenA, p.tokenB);
70:         _approveOperations(pool, address(router), p.amountLiquidty);
71:         router.removeLiquidity(
72:             p.tokenA, p.tokenB, p.amountLiquidty, p.minAmountA, p.minAmountB, address(this), p.deadline
73:         );
74:         _updateTokenInRegistry(p.tokenA);
75:         _updateTokenInRegistry(p.tokenB);
76:         if (IERC20(pool).balanceOf(address(this)) == 0) {
77:             registry.updateHoldingPosition(
78:                 vaultId,
79:                 registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)),
80:                 "",
81:                 "",
82:                 true
83:             );
84:         }
85:     }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L29-L29)']
```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant { // <= FOUND
30:         _approveOperations(asset, market, amount);
31:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
32:         IComet(market).supply(asset, amount);
33:         registry.updateHoldingPosition(
34:             vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false
35:         );
36:         _updateTokenInRegistry(asset);
37:         emit Supply(market, asset, amount);
38:     }
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L48-L48)']
```solidity
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant { // <= FOUND
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
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L63-L63)']
```solidity
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant { // <= FOUND
64:         address rewardToken = IRewards(rewardContract).rewardConfig(market).token;
65:         IRewards(rewardContract).claim(address(market), address(this), true);
66:         _updateTokenInRegistry(rewardToken);
67:         emit ClaimRewards(rewardContract, market);
68:     }
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L68-L68)']
```solidity
68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant { // <= FOUND
69:         PoolInfo memory poolInfo = _getPoolInfo(pool);
70: 
71:         _approveOperations(poolInfo.lpToken, poolInfo.gauge, amount);
72:         IRewardsGauge(poolInfo.gauge).deposit(amount);
73:     }
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L81-L81)']
```solidity
81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant { // <= FOUND
82:         PoolInfo memory poolInfo = _getPoolInfo(pool);
83: 
84:         
85:         address lpToken = poolInfo.lpToken;
86:         address depostiToken = poolInfo.prismaCurvePool;
87:         if (!curveOrConvex) {
88:             depostiToken = poolInfo.prismaConvexPool;
89:         }
90:         _approveOperations(lpToken, depostiToken, amount);
91: 
92:         
93:         IDepositToken(depostiToken).deposit(address(this), amount);
94:     }
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L117-L120)']
```solidity
117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant // <= FOUND
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
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L160-L163)']
```solidity
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant // <= FOUND
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
```
['[221](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L221-L221)']
```solidity
221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant { // <= FOUND
222:         for (uint256 i = 0; i < gauges.length; i++) {
223:             IRewardsGauge(gauges[i]).claim_rewards(address(this));
224:         }
225:         _updateTokenInRegistry(CRV);
226:         emit HarvestRewards(gauges);
227:     }
```
['[233](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L233-L233)']
```solidity
233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant { // <= FOUND
234:         for (uint256 i = 0; i < pools.length; i++) {
235:             IDepositToken(pools[i]).claimReward(address(this));
236:         }
237:         _updateTokenInRegistry(PRISMA);
238:         _updateTokenInRegistry(CRV);
239:         _updateTokenInRegistry(CVX);
240:         emit HarvestPrismaRewards(pools);
241:     }
```
['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L247-L247)']
```solidity
247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant { // <= FOUND
248:         for (uint256 i = 0; i < rewardsPools.length; i++) {
249:             IConvexBasicRewards baseRewardPool = IConvexBasicRewards(rewardsPools[i]);
250:             baseRewardPool.getReward(address(this), true);
251:         }
252:         _updateTokenInRegistry(CVX);
253:         _updateTokenInRegistry(CRV);
254:         emit HarvestConvexRewards(rewardsPools);
255:     }
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L30-L30)']
```solidity
30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant { // <= FOUND
31:         
32:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
33:         
34:         _approveOperations(token, address(dolomiteMargin), _amount);
35:         depositWithdrawalProxy.depositWeiIntoDefaultAccount(marketId, _amount);
36:         
37:         _updateTokenInRegistry(token);
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", false
40:         );
41:     }
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L43-L43)']
```solidity
43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant { // <= FOUND
44:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
45:         depositWithdrawalProxy.withdrawWeiFromDefaultAccount(
46:             marketId, _amount, AccountBalanceHelper.BalanceCheckFlag.None
47:         );
48:         
49:         _updateTokenInRegistry(token);
50:         (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));
51:         if (markets.length == 0) {
52:             registry.updateHoldingPosition(
53:                 vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true
54:             );
55:         }
56:     }
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L58-L61)']
```solidity
58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager
61:         nonReentrant // <= FOUND
62:     {
63:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
64: 
65:         if (!registry.isTokenTrusted(vaultId, token, address(this))) {
66:             revert IConnector_UntrustedToken(token);
67:         }
68:         
69:         borrowPositionProxy.openBorrowPosition(
70:             0, accountId, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
71:         );
72:         registry.updateHoldingPosition(
73:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
74:         );
75:     }
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L77-L80)']
```solidity
77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
78:         public
79:         onlyManager
80:         nonReentrant // <= FOUND
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
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L98-L98)']
```solidity
98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant { // <= FOUND
99:         
100:         borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds);
101:         registry.updateHoldingPosition(
102:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
103:         );
104:     }
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L38-L41)']
```solidity
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant // <= FOUND
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
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L68-L68)']
```solidity
68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant { // <= FOUND
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
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L87-L87)']
```solidity
87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant { // <= FOUND
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
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L41-L41)']
```solidity
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant { // <= FOUND
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
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L68)']
```solidity
62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant { // <= FOUND
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
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L36-L36)']
```solidity
36:     function deposit(uint256 amountIn) external onlyManager nonReentrant { // <= FOUND
37:         IWETH(weth).withdraw(amountIn);
38:         
39:         
40:         ILido(lido).submit{ value: amountIn }(address(0));
41:         _updateTokenInRegistry(steth);
42:         _updateTokenInRegistry(weth);
43:         emit Deposit(amountIn);
44:     }
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L50-L50)']
```solidity
50:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant { // <= FOUND
51:         _approveOperations(steth, lidoWithdrawal, amount);
52:         
53:         uint256[] memory amounts = new uint256[](1);
54:         amounts[0] = amount;
55:         
56:         uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this));
57:         bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, "");
58:         registry.updateHoldingPosition(vaultId, positionId, abi.encode(requestIds[0]), abi.encode(amount), false);
59: 
60:         _updateTokenInRegistry(steth);
61:         emit RequestWithdrawals(amount);
62:     }
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L68-L68)']
```solidity
68:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant { // <= FOUND
69:         
70:         ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId);
71:         
72:         uint256 beforeClaimBalance = address(this).balance;
73:         
74:         ILidoWithdrawal(lidoWithdrawal).claimWithdrawal(requestId);
75:         
76:         IWETH(weth).deposit{ value: address(this).balance - beforeClaimBalance }();
77:         registry.updateHoldingPosition(
78:             vaultId,
79:             registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, ""),
80:             abi.encode(requestId),
81:             "",
82:             true
83:         );
84:         _updateTokenInRegistry(weth);
85:         emit ClaimWithdrawal(requestId);
86:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L63-L63)']
```solidity
63:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant { // <= FOUND
64:         
65:         _approveOperations(mav, veMav, amount);
66:         
67:         IveMAV(veMav).stake(amount, duration, doDelegation);
68:         _updateTokenInRegistry(mav);
69:         _updateTokenInRegistry(veMav);
70:         emit Stake(amount, duration, doDelegation);
71:     }
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L76-L76)']
```solidity
76:     function unstake(uint256 lockupId) external onlyManager nonReentrant { // <= FOUND
77:         
78:         IveMAV(veMav).unstake(lockupId);
79:         _updateTokenInRegistry(mav);
80:         _updateTokenInRegistry(veMav);
81:         emit Unstake(lockupId);
82:     }
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L88-L88)']
```solidity
88:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant { // <= FOUND
89:         uint256 sendEthAmount = p.ethPoolIncluded ? p.tokenARequiredAllowance : 0;
90:         _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); 
91:         _approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);
92:         
93:         uint256 tokenId;
94:         {
95:             (tokenId,,,) = IMaverickRouter(maverickRouter).addLiquidityToPool{ value: sendEthAmount }(
96:                 p.pool, 0, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline
97:             );
98:         }
99:         registry.updateHoldingPosition(
100:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false
101:         );
102:         _updateTokenInRegistry(p.pool.tokenA());
103:         _updateTokenInRegistry(p.pool.tokenB());
104:         emit AddLiquidityInMaverickPool(p);
105:     }
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L111-L114)']
```solidity
111:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
112:         external
113:         onlyManager
114:         nonReentrant // <= FOUND
115:     {
116:         IMaverickPosition position = IMaverickRouter(maverickRouter).position();
117:         position.approve(maverickRouter, p.tokenId);
118:         IMaverickRouter(maverickRouter).removeLiquidity(
119:             p.pool, address(this), p.tokenId, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline
120:         );
121:         registry.updateHoldingPosition(
122:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true
123:         );
124:         _updateTokenInRegistry(p.pool.tokenA());
125:         _updateTokenInRegistry(p.pool.tokenB());
126:         emit RemoveLiquidityFromMaverickPool(p);
127:     }
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L132-L132)']
```solidity
132:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant { // <= FOUND
133:         IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));
134:         uint8 tokenIndex;
135:         for (uint256 i = 0; i < earnedInfo.length; i++) {
136:             if (earnedInfo[i].earned != 0) {
137:                 tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken));
138:                 rewardContract.getReward(address(this), tokenIndex);
139:             }
140:         }
141:         emit ClaimBoostedPositionRewards(rewardContract);
142:     }
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L35-L35)']
```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant { // <= FOUND
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
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L58-L58)']
```solidity
58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant { // <= FOUND
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
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L80-L80)']
```solidity
80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant { // <= FOUND
81:         MarketParams memory market = morphoBlue.idToMarketParams(id);
82:         morphoBlue.borrow(market, amount, 0, address(this), address(this));
83:         if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {
84:             revert IConnector_LowHealthFactor(getHealthFactor(id, morphoBlue.market(id)));
85:         }
86:         _updateTokenInRegistry(market.loanToken);
87:         emit Borrow(amount, id);
88:     }
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L95-L95)']
```solidity
95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant { // <= FOUND
96:         MarketParams memory params = morphoBlue.idToMarketParams(id);
97:         _approveOperations(params.loanToken, address(morphoBlue), amount);
98:         morphoBlue.repay(params, amount, 0, address(this), "");
99:         _updateTokenInRegistry(params.loanToken);
100:         emit Repay(amount, id);
101:     }
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L31-L31)']
```solidity
31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant { // <= FOUND
32:         IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId);
33:         emit SendPositionToMasterChef(tokenId);
34:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L40-L40)']
```solidity
40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant { // <= FOUND
41:         masterchef.updateLiquidity(tokenId);
42:         _updateTokenInRegistry(masterchef.CAKE());
43:         emit UpdatePosition(tokenId);
44:     }
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L50-L50)']
```solidity
50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant { // <= FOUND
51:         masterchef.withdraw(tokenId, address(this));
52:         _updateTokenInRegistry(masterchef.CAKE());
53:         emit Withdraw(tokenId);
54:     }
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L78-L78)']
```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant { // <= FOUND
79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
80: 
81:         (, address _underlyingToken,) = _SY.assetInfo();
82: 
83:         _approveOperations(_underlyingToken, address(_SY), amount);
84:         
85:         uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);
86: 
87:         bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));
88:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
89:         emit Supply(market, syMinted);
90:     }
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L97-L97)']
```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant { // <= FOUND
98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
99:         IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);
100:         _YT.mintPY(address(this), address(this));
101:         emit MintPTAndYT(market, syAmount);
102:     }
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L112-L112)']
```solidity
112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant { // <= FOUND
113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
114:         IERC20(address(_SY)).safeTransfer(address(market), SYamount);
115:         IERC20(address(_PT)).safeTransfer(address(market), PTamount);
116:         market.mint(address(this), SYamount, PTamount);
117:         market.skim();
118:         emit DepositIntoMarket(address(market), SYamount, PTamount);
119:     }
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L126-L126)']
```solidity
126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant { // <= FOUND
127:         _approveOperations(_market, pendleMarketDepositHelper.pendleStaking(), _amount);
128:         pendleMarketDepositHelper.depositMarket(_market, _amount);
129:         emit DepositIntoPenpie(_market, _amount);
130:     }
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L137-L137)']
```solidity
137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant { // <= FOUND
138:         pendleMarketDepositHelper.withdrawMarketWithClaim(_market, _amount, true);
139:         emit WithdrawFromPenpie(_market, _amount);
140:     }
```
['[183](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L183-L186)']
```solidity
183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant // <= FOUND
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
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L203-L203)']
```solidity
203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant { // <= FOUND
204:         IERC20(address(market)).safeTransfer(address(market), amount);
205:         market.burn(address(this), address(market), amount);
206:         market.skim();
207:         emit BurnLP(address(market), amount);
208:     }
```
['[216](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L216-L216)']
```solidity
216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant { // <= FOUND
217:         (IPStandardizedYield SY,,) = market.readTokens();
218:         (, address _underlyingToken,) = SY.assetInfo();
219: 
220:         
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
```
['[241](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L241-L241)']
```solidity
241:     function claimRewards(IPMarket market) external onlyManager nonReentrant { // <= FOUND
242:         market.redeemRewards(address(this));
243:         address[] memory rewardTokens = market.getRewardTokens();
244:         for (uint256 i = 0; i < rewardTokens.length; i++) {
245:             _updateTokenInRegistry(rewardTokens[i]);
246:         }
247:         emit ClaimRewards(address(market));
248:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L33-L33)']
```solidity
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant { // <= FOUND
34:         if (approve) {
35:             bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
36: 
37:             if (!registry.isPositionTrustedForConnector(vaultId, positionId, address(this))) {
38:                 revert IConnector_InvalidPosition(positionId);
39:             }
40:         }
41:         IBorrowerOperations(zap.borrowerOps()).setDelegateApproval(address(zap), approve);
42:     }
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L55)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant // <= FOUND
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
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L75-L75)']
```solidity
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant { // <= FOUND
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
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L104)']
```solidity
97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant { // <= FOUND
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
116:         
117:         uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));
118:         if (minimumHealthFactor > healthFactor) {
119:             revert IConnector_LowHealthFactor(healthFactor);
120:         }
121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);
122:     }
```
['[129](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L129-L129)']
```solidity
129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant { // <= FOUND
130:         bytes32 positionId =
131:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, troveManager));
132:         IBorrowerOperations borrowerOperations = zapContract.borrowerOps();
133:         borrowerOperations.closeTrove(troveManager, address(this));
134:         registry.updateHoldingPosition(vaultId, positionId, "", "", true);
135:         emit CloseTrove(address(zapContract), troveManager);
136:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L33-L33)']
```solidity
33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant { // <= FOUND
34:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
35:         _approveOperations(dToken, address(silo), amount);
36:         silo.deposit(dToken, amount, oC);
37:         _updateTokenInRegistry(dToken);
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", false
40:         );
41:         emit Deposit(siloToken, dToken, amount, oC);
42:     }
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L52-L55)']
```solidity
52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant // <= FOUND
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
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L85-L85)']
```solidity
85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant { // <= FOUND
86:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
87:         silo.borrow(bToken, amount);
88:         _updateTokenInRegistry(bToken);
89:         emit Borrow(siloToken, bToken, amount);
90:     }
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L98-L98)']
```solidity
98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant { // <= FOUND
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
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L49-L49)']
```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant { // <= FOUND
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
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L76-L76)']
```solidity
76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant { // <= FOUND
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
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L103-L103)']
```solidity
103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant { // <= FOUND
104:         LPStaking.deposit(poolId, 0);
105:         _updateTokenInRegistry(rewardToken);
106:         emit ClaimStargateRewards(poolId);
107:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L40-L40)']
```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) { // <= FOUND
41:         bytes32 positionId =
42:             registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));
43:         p.recipient = address(this);
44:         
45:         _approveOperations(p.token0, address(positionManager), p.amount0Desired);
46:         _approveOperations(p.token1, address(positionManager), p.amount1Desired);
47: 
48:         
49:         (tokenId,,,) = positionManager.mint(p);
50:         bytes memory positionData = abi.encode(tokenId);
51:         registry.updateHoldingPosition(
52:             vaultId, positionId, positionData, abi.encode(p.tickLower, p.tickUpper, p.fee), false
53:         );
54:         _updateTokenInRegistry(p.token0);
55:         _updateTokenInRegistry(p.token1);
56:         emit OpenPosition(p, tokenId);
57:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L63-L63)']
```solidity
63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant { // <= FOUND
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
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L87-L87)']
```solidity
87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant { // <= FOUND
88:         (, address token0, address token1) = getCurrentLiquidity(p.tokenId);
89:         
90:         _approveOperations(token0, address(positionManager), p.amount0Desired);
91:         _approveOperations(token1, address(positionManager), p.amount1Desired);
92:         positionManager.increaseLiquidity(p);
93:         _updateTokenInRegistry(token0);
94:         _updateTokenInRegistry(token1);
95:         emit IncreasePosition(p);
96:     }
```
['[101](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L101-L101)']
```solidity
101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant { // <= FOUND
102:         for (uint256 i = 0; i < tokenIds.length; i++) {
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]);
108:         }
109:     }
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L122-L127)']
```solidity
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant { // <= FOUND
128:         emit TransferPositionToConnector(tokens, amounts, connector, data);
129:         if (registry.isAnActiveConnector(vaultId, connector)) {
130:             IConnector(connector).addLiquidity(tokens, amounts, data);
131:         }
132:     }
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L210)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant { // <= FOUND
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
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68)']
```solidity
68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant { // <= FOUND
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
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L95)']
```solidity
90:     function executeSwap(SwapRequest memory _swapRequest)
91:         external
92:         payable
93:         onlyEligibleUser
94:         onlyExistingRoute(_swapRequest.routeId)
95:         nonReentrant // <= FOUND
96:         returns (uint256 _amountOut)
97:     {
98:         if (_swapRequest.amount == 0) revert InvalidAmount();
99:         RouteData memory swapImplInfo = routes[_swapRequest.routeId];
100:         if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();
101: 
102:         if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {
103:             
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
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L131)']
```solidity
126:     function executeBridge(BridgeRequest calldata _bridgeRequest)
127:         external
128:         payable
129:         onlyEligibleUser
130:         onlyExistingRoute(_bridgeRequest.routeId)
131:         nonReentrant // <= FOUND
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


</details>

## [Low-16] Missing zero address check in constructor

### Resolution 
In Solidity, constructors often take address parameters to initialize important components of a contract, such as owner or linked contracts. However, without a check, there's a risk that an address parameter could be mistakenly set to the zero address (0x0). This could occur due to a mistake or oversight during contract deployment. A zero address in a crucial role can cause serious issues, as it cannot perform actions like a normal address, and any funds sent to it are irretrievable. Therefore, it's crucial to include a zero address check in constructors to prevent such potential problems. If a zero address is detected, the constructor should revert the transaction.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L27-L27)']
```solidity
27:     constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams) // <= FOUND
28:         BaseConnector(baseConnectorParams)
29:     {
30:         positionManager = INonfungiblePositionManager(_positionManager);
31:         factory = IUniswapV3Factory(_factory);
32:     }
```
['[22](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L22-L22)']
```solidity
22:     constructor(address _registry, uint256 _vaultId) { // <= FOUND
23:         registry = PositionRegistry(_registry);
24:         vaultId = _vaultId;
25:     }
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L19)']
```solidity
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams) // <= FOUND
20:         OmnichainLogic(_lzHelper, baseConnectorParams)
21:     {
22:         DUST_LEVEL = dl;
23:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L27)']
```solidity
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) { // <= FOUND
28:         isHandler[swapHandler] = true;
29:         lifi = _lifi;
30:     }
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L31)']
```solidity
31:     constructor(address _factory, PositionRegistry _registry) { // <= FOUND
32:         factory = _factory;
33:         registry = _registry;
34:     }
```


</details>

## [Low-17] Use of onlyOwner functions can be lost

### Resolution 
In Solidity, renouncing ownership of a contract essentially transfers ownership to the zero address. This is an irreversible operation and has considerable security implications. If the renounceOwnership function is used, the contract will lose the ability to perform any operations that are limited to the owner. This can be problematic if there are any bugs, flaws, or unexpected events that require owner intervention to resolve. Therefore, in some instances, it is better to disable or omit the renounceOwnership function, and instead implement a secure transferOwnership function. This way, if necessary, ownership can be transferred to a new, trusted party without losing the potential for administrative intervention.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L7-L7)']
```solidity
7: contract NoyaFeeReceiver is Ownable  // <= FOUND
```
['[9](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L9-L9)']
```solidity
9: contract Keepers is EIP712, Ownable2Step  // <= FOUND
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L10-L10)']
```solidity
10: contract LifiImplementation is ISwapAndBridgeImplementation, Ownable2Step, ReentrancyGuard  // <= FOUND
```


</details>

## [Low-18] Off-by-one timestamp error

### Resolution 
In Solidity, using `>=` or `<=` to compare against `block.timestamp` (alias `now`) may introduce off-by-one errors due to the fact that `block.timestamp` is only updated once per block and its value remains constant throughout the block's execution. If an operation happens at the exact second when `block.timestamp` changes, it could result in unexpected behavior. To avoid this, it's safer to use strict inequality operators (`>` or `<`). For instance, if a condition should only be met after a certain time, use `block.timestamp > time` rather than `block.timestamp >= time`. This way, potential off-by-one errors due to the exact timing of block mining are mitigated, leading to safer, more predictable contract behavior.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L98)']
```solidity
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
94:         require(isOwner[msg.sender], "Not an owner");
95:         require(sigR.length == threshold, "Not enough signatures");
96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");
97:         require(executor == msg.sender, "Invalid executor");
98:         require(block.timestamp <= deadline, "Transaction expired"); // <= FOUND
99:         {
100:             bytes32 txInputHash =
101:                 keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
103:             address lastAdd = address(0);
104:             for (uint256 i = 0; i < threshold;) {
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
106:                 require(recovered > lastAdd && isOwner[recovered]);
107:                 lastAdd = recovered;
108:                 unchecked {
109:                     ++i;
110:                 }
111:             }
112: 
113:             nonce++;
114:         }
115:         emit Execute(destination, data, gasLimit, executor, deadline);
116:         (bool success,) = destination.call{ gas: gasLimit }(data);
117:         require(success, "Transaction execution reverted.");
118:     }
```


</details>

## [Low-19] Constant decimal values

### Resolution 
The use of fixed decimal values such as 1e18 or 1e8 in Solidity contracts can lead to inaccuracies, bugs, and vulnerabilities, particularly when interacting with tokens having different decimal configurations. Not all ERC20 tokens follow the standard 18 decimal places, and assumptions about decimal places can lead to miscalculations.

Resolution: Always retrieve and use the `decimals()` function from the token contract itself when performing calculations involving token amounts. This ensures that your contract correctly handles tokens with any number of decimal places, mitigating the risk of numerical errors or under/overflows that could jeopardize contract integrity and user funds.

Num of instances: 13

### Findings 


<details><summary>Click to show findings</summary>

['[239](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L239-L240)']
```solidity
239:             emit CalculateDeposit(
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount // <= FOUND
241:             );
```
['[271](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L271-L272)']
```solidity
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount // <= FOUND
273:             );
```
['[172](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L172-L172)']
```solidity
172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply); // <= FOUND
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L78-L78)']
```solidity
78:         return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase; // <= FOUND
```
['[119](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L119-L119)']
```solidity
119:                 if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18; // <= FOUND
```
['[136](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L136-L137)']
```solidity
136:         
137:         uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV; // <= FOUND
```
['[271](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L271-L271)']
```solidity
271:                 SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18; // <= FOUND
```
['[275](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L275-L275)']
```solidity
275:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18; // <= FOUND
```
['[280](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L280-L280)']
```solidity
280:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18; // <= FOUND
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L123-L123)']
```solidity
123:             uint256 price = _getValue(assets[i], base, 1e18); // <= FOUND
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L124-L124)']
```solidity
124:             totalDepositAmount += depositAmount * price / 1e18; // <= FOUND
```
['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L125-L125)']
```solidity
125:             totalBAmount += borrowAmount * price / 1e18; // <= FOUND
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L10-L10)']
```solidity
10:         return (0, 1e18, 0, block.timestamp, 0); // <= FOUND
```


</details>

## [Low-20] Calculation will revert when totalSupply() returns zero

### Resolution 
In the instance where the function totalSupply() returns zero, it will inevitably lead to a division by zero error when used in mathematical operations, causing the transaction to fail and potentially disrupting contract functionality. This situation can inadvertently serve as a blocking mechanism, preventing valid transactions and operations. It's crucial to accommodate this special scenario in your code. One resolution could be implementing condition checks in your function to detect a zero totalSupply() and handle it differently, perhaps by returning a specific value or altering the operational flow, thus ensuring that transactions do not revert and the contract functions smoothly even in this edge case.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L125-L132)']
```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) { // <= FOUND
126:         PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
127:         (address pool) = abi.decode(pBP.data, (address));
128:         uint256 balance = IERC20(pool).balanceOf(address(this));
129:         uint256 totalSupply = IERC20(pool).totalSupply();
130:         (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();
131:         uint256 amount0 = balance * reserve0 / totalSupply; // <= FOUND
132:         uint256 amount1 = balance * reserve1 / totalSupply; // <= FOUND
133:         return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1);
134:     }
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L172)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) { // <= FOUND
163:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
164:         PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
165:         uint256 lpBalance = totalLpBalanceOf(pool);
166:         (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);
167:         uint256 _totalSupply = IERC20(pool.pool).totalSupply();
168: 
169:         uint256 _weight = pool.weights[pool.tokenIndex];
170: 
171:         uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]);
172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply); // <= FOUND
173:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L95)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
88:         (address tokenA, address tokenB) =
89:             abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address, address));
90:         address pool = factory.getPair(tokenA, tokenB);
91:         uint256 totalSupply = IERC20(pool).totalSupply();
92:         (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();
93: 
94:         uint256 balanceThis = IERC20(pool).balanceOf(address(this));
95:         return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply; // <= FOUND
96:     }
```


</details>

## [Low-21] Return values not checked for approve()

### Resolution 
The ERC-20 token standard does not dictate that the approve function must return a value. The function signature in the ERC-20 standard is function approve(address spender, uint tokens) public returns (bool success);. However, a well-implemented ERC-20 token contract will typically have approve return a boolean value indicating whether or not the operation was successful.

It's crucial to note that not all token contracts follow this practice. Some might not return a value, or they might return a value in a non-standard way. This inconsistency among token contracts is one reason why it's important to handle token interactions carefully in your smart contracts and to check the return value of approve when possible.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L70-L71)']
```solidity
70:         
71:         ILidoWithdrawal(lidoWithdrawal).approve(lidoWithdrawal, requestId); // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L117-L117)']
```solidity
117:         position.approve(maverickRouter, p.tokenId); // <= FOUND
```


</details>

## [Low-22] Incorrect withdraw declaration

### Resolution 
In Solidity, it's essential for clarity and interoperability to correctly specify return types in function declarations. If the `withdraw` function is expected to return a `bool` to indicate success or failure, its omission could lead to ambiguity or unexpected behavior when interacting with or calling this function from other contracts or off-chain systems. Missing return values can mislead developers and potentially lead to contract integrations built on incorrect assumptions. To resolve this, the function declaration for `withdraw` should be modified to explicitly include the `bool` return type, ensuring clarity and correctness in contract interactions.

Num of instances: 8

### Findings 


<details><summary>Click to show findings</summary>

['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L301-L301)']
```solidity
301:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused  // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L79-L79)']
```solidity
79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant  // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L43-L43)']
```solidity
43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant  // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L68-L68)']
```solidity
68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant  // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L58-L58)']
```solidity
58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant  // <= FOUND
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L50-L50)']
```solidity
50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant  // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L46-L46)']
```solidity
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager  // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L52-L52)']
```solidity
52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition) // <= FOUND
53:         external
54:         onlyManager
55:         nonReentrant
56:     
```


</details>

## [Low-23] Critical functions should have a timelock

### Resolution 
Critical functions, especially those affecting protocol parameters or user funds, are potential points of failure or exploitation. To mitigate risks, incorporating a timelock on such functions can be beneficial. A timelock requires a waiting period between the time an action is initiated and when it's executed, giving stakeholders time to react, potentially vetoing malicious or erroneous changes. To implement, integrate a smart contract like OpenZeppelin's `TimelockController` or build a custom mechanism. This ensures governance decisions or administrative changes are transparent and allows for community or multi-signature interventions, enhancing protocol security and trustworthiness.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L63-L63)']
```solidity
63:     function setThreshold(uint8 _threshold) public onlyOwner  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner  // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L79-L79)']
```solidity
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE)  // <= FOUND
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE)  // <= FOUND
```


</details>

## [Low-24] Unbounded loop may run out of gas

### Resolution 
Unbounded loops in smart contracts pose a risk because they iterate over an unknown number of elements, potentially consuming all available gas for a transaction. This can result in unintended transaction failures. Gas consumption increases linearly with the number of iterations, and if it surpasses the gas limit, the transaction reverts, wasting the gas spent. To mitigate this, developers should either set a maximum limit on loop iterations.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L84)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
82:                 require(success, "BalancerFlashLoan: Flash loan failed");
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
94:     }
```


</details>

## [Low-25] Consider implementing two-step procedure for updating protocol addresses

### Resolution 
Implementing a two-step procedure for updating protocol addresses adds an extra layer of security. In such a system, the first step initiates the change, and the second step, after a predefined delay, confirms and finalizes it. This delay allows stakeholders or monitoring tools to observe and react to unintended or malicious changes. If an unauthorized change is detected, corrective actions can be taken before the change is finalized. To achieve this, introduce a "proposed address" state variable and a "delay period". Upon an update request, set the "proposed address". After the delay, if not contested, the main protocol address can be updated.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) { // <= FOUND
85:         emit updateFlashloanAddress(_flashLoan, flashLoan);
86:         flashLoan = _flashLoan;
87:     }
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager { // <= FOUND
154:         _updateTokenInRegistry(token);
155:     }
```


</details>

## [Low-26] Prefer skip over revert model in iteration

### Resolution 
It is preferable to skip operations on an array index when a condition is not met rather than reverting the whole transaction as reverting can introduce the possiblity of malicous actors purposefully introducing array objects which fail conditional checks within for/while loops so group operations fail. As such it is recommended to simply skip such array indices over reverting unless there is a valid security or logic reason behind not doing so.

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L247-L249)']
```solidity
247:             for (uint256 i = 0; i < usingTokens.length; i++) { // <= FOUND
248:                 if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) {
249:                     revert TokenNotTrusted(usingTokens[i]); // <= FOUND
250:                 }
251:             }
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L69-L70)']
```solidity
69:        for (uint256 i = 0; i < calls.length; i++) { // <= FOUND
70:             if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target); // <= FOUND
71:             bytes4 method = bytes4(calls[i].callData[:4]);
72: 
73:             if (method == ICreditFacadeV3Multicall.enableToken.selector) {
74:                 (address token) = abi.decode(calls[i].callData[4:], (address));
75:                 _updateTokenInRegistry(token);
76:             }
77:         }
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L69-L70)']
```solidity
69:         for (uint256 i = 0; i < calls.length; i++) { // <= FOUND
70:             if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target); // <= FOUND
71:             bytes4 method = bytes4(calls[i].callData[:4]);
72: 
73:             if (method == ICreditFacadeV3Multicall.enableToken.selector) {
74:                 (address token) = abi.decode(calls[i].callData[4:], (address));
75:                 _updateTokenInRegistry(token);
76:             }
77:         }
```
['[104](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L104-L106)']
```solidity
104:             for (uint256 i = 0; i < threshold;) { // <= FOUND
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
106:                 require(recovered > lastAdd && isOwner[recovered]); // <= FOUND
107:                 lastAdd = recovered;
108:                 unchecked {
109:                     ++i;
110:                 }
111:             }
```
['[178](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L178-L184)']
```solidity
178:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
179:             
180:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
183:             if (_balanceAfter < amounts[i] + _balance) {
184:                 revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]); // <= FOUND
185:             }
186:         }
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L89-L92)']
```solidity
89:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens"); // <= FOUND
93:         }
```


</details>

## [Low-27] Missing contract-existence checks before low-level calls

### Resolution 
Low-level calls in Solidity, when made to addresses without contract code, don't fail but return a successful status. This behavior can be misleading, leading to unintended consequences in dApps. Ignoring this can potentially mean acting on false positive results. To address this, apart from the conventional zero-address check, developers should verify the existence of contract code at the target address by ensuring that the code length at the specified address (`<address>.code.length`) is greater than zero. By doing so, it provides a more robust validation before executing low-level calls, safeguarding against unintentional interactions with empty addresses.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[680](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L680-L682)']
```solidity
680:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {
681:         if (token == address(0)) {
682:             (bool success,) = payable(msg.sender).call{ value: amount }(""); // <= FOUND
683:             require(success, "Transfer failed.");
684:         } else {
685:             IERC20(token).safeTransfer(msg.sender, amount);
686:         }
687:         emit Rescue(msg.sender, token, amount);
688:     }
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L81)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
82:                 require(success, "BalancerFlashLoan: Flash loan failed");
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) {
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
94:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L116)']
```solidity
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
94:         require(isOwner[msg.sender], "Not an owner");
95:         require(sigR.length == threshold, "Not enough signatures");
96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");
97:         require(executor == msg.sender, "Invalid executor");
98:         require(block.timestamp <= deadline, "Transaction expired");
99:         {
100:             bytes32 txInputHash =
101:                 keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
103:             address lastAdd = address(0);
104:             for (uint256 i = 0; i < threshold;) {
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
106:                 require(recovered > lastAdd && isOwner[recovered]);
107:                 lastAdd = recovered;
108:                 unchecked {
109:                     ++i;
110:                 }
111:             }
112: 
113:             nonce++;
114:         }
115:         emit Execute(destination, data, gasLimit, executor, deadline);
116:         (bool success,) = destination.call{ gas: gasLimit }(data); // <= FOUND
117:         require(success, "Transaction execution reverted.");
118:     }
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L176)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     {
170:         if (!_isNative(token)) {
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId));
172: 
173:             _setAllowance(token, lifi, amount);
174:         }
175: 
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data); // <= FOUND
177: 
178:         if (!success) {
179:             revert FailedToForward(err);
180:         }
181: 
182:         emit Forwarded(lifi, address(token), amount, data);
183:     }
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L195)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {
194:         if (token == address(0)) {
195:             (bool success,) = payable(userAddress).call{ value: amount }(""); // <= FOUND
196:             require(success, "Transfer failed.");
197:         } else {
198:             IERC20(token).safeTransfer(userAddress, amount);
199:         }
200:         emit Rescued(token, userAddress, amount);
201:     }
```


</details>

## [Low-28] Constructors missing validation

### Resolution 
In Solidity, when values are being assigned in constructors to unsigned or integer variables, it's crucial to ensure the provided values adhere to the protocol's specific operational boundaries as laid out in the project specifications and documentation. If the constructors lack appropriate validation checks, there's a risk of setting state variables with values that could cause unexpected and potentially detrimental behavior within the contract's operations, violating the intended logic of the protocol. This can compromise the contract's security and impact the maintainability and reliability of the system. In order to avoid such issues, it is recommended to incorporate rigorous validation checks in constructors. These checks should align with the project's defined rules and constraints, making use of Solidity's built-in require function to enforce these conditions. If the validation checks fail, the require function will cause the transaction to revert, ensuring the integrity and adherence to the protocol's expected behavior.

Num of instances: 8

### Findings 


<details><summary>Click to show findings</summary>

['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L66-L76)']
```solidity
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
67:         require(_governer != address(0));
68:         require(_maintainer != address(0));
69:         require(_emergency != address(0));
70:         _grantRole(GOVERNER_ROLE, _governer);
71:         _grantRole(MAINTAINER_ROLE, _maintainer);
72:         _grantRole(EMERGENCY_ROLE, _emergency);
73:         _setRoleAdmin(GOVERNER_ROLE, GOVERNER_ROLE);
74:         _setRoleAdmin(MAINTAINER_ROLE, GOVERNER_ROLE);
75:         _setRoleAdmin(EMERGENCY_ROLE, GOVERNER_ROLE);
76:         flashLoan = _flashLoan; // <= FOUND
77:     }
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L24-L28)']
```solidity
24:     constructor(address _balancerVault, PositionRegistry _registry) {
25:         require(_balancerVault != address(0));
26:         require(address(_registry) != address(0));
27:         vault = IBalancerVault(_balancerVault);
28:         registry = _registry; // <= FOUND
29:     }
```
['[21](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L21-L23)']
```solidity
21:     constructor(PositionRegistry _registry, uint256 _vaultId) {
22:         require(address(_registry) != address(0));
23:         registry = _registry; // <= FOUND
24:         vaultId = _vaultId; // <= FOUND
25:     }
```
['[22](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L22-L24)']
```solidity
22:     constructor(address _registry, uint256 _vaultId) {
23:         registry = PositionRegistry(_registry);
24:         vaultId = _vaultId; // <= FOUND
25:     }
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L22)']
```solidity
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
20:         OmnichainLogic(_lzHelper, baseConnectorParams)
21:     {
22:         DUST_LEVEL = dl; // <= FOUND
23:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L29)']
```solidity
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
28:         isHandler[swapHandler] = true;
29:         lifi = _lifi; // <= FOUND
30:     }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L29-L31)']
```solidity
29:     constructor(PositionRegistry _registry) {
30:         require(address(_registry) != address(0));
31:         registry = _registry; // <= FOUND
32:     }
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L33)']
```solidity
31:     constructor(address _factory, PositionRegistry _registry) {
32:         factory = _factory; // <= FOUND
33:         registry = _registry; // <= FOUND
34:     }
```


</details>

## [Low-29] Vulnerable version of openzeppelin contracts used

### Resolution 
OpenZeppelin versions of 4.9.2 and below are vulnerable to exploits, please consider upgrading to 4.9.3 or above. See: https://security.snyk.io/package/npm/@openzeppelin%2Fcontracts for more details

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[1](https://github.com/code-423n4/2024-04-noya/tree/main/package.json#L1-L22)']
```solidity
1: {
2:   "name": "noya-vaults",
3:   "scripts": {
4:     "compile": "forge build"
5:   },
6:   "devDependencies": {
7:     "@nomicfoundation/hardhat-toolbox": "^3.0.0",
8:     "hardhat": "^2.19.1"
9:   },
10:   "dependencies": {
11:     "@balancer-labs/v2-interfaces": "^0.4.0",
12:     "@gearbox-protocol/core-v2": "^1.21.1",
13:     "@layerzerolabs/lz-evm-messagelib-v2": "^2.1.18",
14:     "@layerzerolabs/lz-evm-oapp-v2": "^2.0.25",
15:     "@layerzerolabs/lz-evm-protocol-v2": "^2.0.25",
16:     "@layerzerolabs/ua-utils": "^0.0.26",
17:     "@nomicfoundation/hardhat-chai-matchers": "^2.0.0",
18:     "@nomicfoundation/hardhat-ethers": "^3.0.0",
19:     "@nomicfoundation/hardhat-network-helpers": "^1.0.0",
20:     "@nomicfoundation/hardhat-verify": "^1.0.0",
21:     "@openzeppelin/contracts": "^4.8.1", // <= FOUND
22:     "@openzeppelin/contracts-3.4": "npm:@openzeppelin/contracts@3.4.2-solc-0.7", // <= FOUND
23:     "@openzeppelin/contracts-5.0": "npm:@openzeppelin/contracts@^5.0.1",
24:     "@openzeppelin/contracts-upgradeable": "^4.8.1 || ^5.0.0",
25:     "@tenderly/hardhat-tenderly": "^2.1.0",
26:     "@typechain/ethers-v6": "^0.4.0",
27:     "@typechain/hardhat": "^8.0.0",
28:     "@types/chai": "^4.2.0",
29:     "@types/mocha": ">=9.1.0",
30:     "@types/node": "*",
31:     "@uniswap/v3-core": "^1.0.1",
32:     "@uniswap/v3-periphery": "^1.4.4",
33:     "chai": "^4.2.0",
34:     "dotenv": "^16.3.2",
35:     "ethers": "^6.8.1",
36:     "hardhat-contract-sizer": "^2.10.0",
37:     "hardhat-deploy": "^0.11.44",
38:     "hardhat-gas-reporter": "^1.0.8",
39:     "ds-test": "https://github.com/dapphub/ds-test.git",
40:     "solidity-bytes-utils": "^0.8.0",
41:     "solidity-coverage": "^0.8.11",
42:     "solidity-docgen": "^0.6.0-beta.36",
43:     "tenderly": "^0.8.0",
44:     "ts-node": ">=8.0.0",
45:     "typechain": "^8.2.0",
46:     "typescript": ">=4.5.0"
47:   }
48: }
49: 
```


</details>

## [Low-30] Balances directly compared using ==/!= can be dosed

### Resolution 
Comparing balances directly using the `==` or `!=` operators in Solidity can lead to potential Denial of Service (DoS) vulnerabilities. This is because direct comparisons assume exact balance amounts, which may not account for dynamic changes due to transfers, fees, or other contract interactions. An attacker could manipulate balances to match or deviate from a specific target, causing functions that rely on these comparisons to behave unpredictably or fail. A more robust approach is to use range checks or tolerate minor deviations in balance comparisons. This approach reduces the risk of DoS attacks by not relying on exact balance equality or inequality for critical contract operations.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L92-L92)']
```solidity
92:         if (IERC20(data.pool).balanceOf(address(this)) == 0) { // <= FOUND
```
['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L92-L92)']
```solidity
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens"); // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L76-L76)']
```solidity
76:         if (IERC20(pool).balanceOf(address(this)) == 0) { // <= FOUND
```
['[305](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L305-L307)']
```solidity
305:         return (
306:             _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0 // <= FOUND
307:                 && market.balanceOf(address(this)) == 0 // <= FOUND
308:         );
```
['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L92-L92)']
```solidity
92:         _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0); // <= FOUND
```


</details>

## [Low-31] Blacklist can be bypassed through front running

### Resolution 
Front running is a strategy where a malicious actor exploits knowledge of upcoming transactions to their advantage, typically in financial markets or blockchain networks. When applied to bypassing blacklists, an attacker can observe a transaction intended to blacklist their address and preemptively execute a transfer of their assets to another address under their control, thus circumventing restrictions. This can be done by paying higher gas fees to ensure their transaction is processed first. It undermines security measures by exploiting the transparency and deterministic processing order of blockchain transactions, highlighting the need for more sophisticated anti-manipulation and monitoring mechanisms.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L65)']
```solidity
65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner {
66:         isBridgeWhiteListed[bridgeName] = state;
67:         emit AddedBridgeBlacklist(bridgeName, state);
68:     }
```


</details>

## [Low-32] State variables not capped at reasonable values

### Resolution 
Setting boundaries on state variables in smart contracts is essential for maintaining system integrity and user protection. Without caps on values, variables could reach extremes that exploit or disrupt contract functionality, leading to potential loss or unintended consequences for users. Implementing checks for minimum and maximum permissible values can prevent such issues, ensuring variables remain within a safe and reasonable range. This practice guards against attacks aimed at destabilizing the contract, such as griefing, where attackers intentionally cause distress by exploiting vulnerabilities. Proper validation promotes contract reliability, user trust, and a healthier ecosystem by mitigating risks associated with unbounded state changes.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[664](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L664-L665)']
```solidity
664:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {
665:         depositLimitPerTransaction = _depositLimitPerTransaction; // <= FOUND
666:         depositLimitTotalAmount = _depositTotalAmount; // <= FOUND
667:         emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount);
668:     }
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L58)']
```solidity
57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {
58:         genericSlippageTolerance = _slippageTolerance; // <= FOUND
59:         emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);
60:     }
```
['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L156-L175)']
```solidity
156:     function changeVaultAddresses(
157:         uint256 vaultId,
158:         address _governer,
159:         address _maintainer,
160:         address _maintainerWithoutTimelock,
161:         address _keeperContract,
162:         address _watcher,
163:         address _emergency
164:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {
165:         require(_governer != address(0));
166:         require(_maintainer != address(0));
167:         require(_keeperContract != address(0));
168:         require(_watcher != address(0));
169: 
170:         vaults[vaultId].governer = _governer; // <= FOUND
171:         vaults[vaultId].maintainer = _maintainer; // <= FOUND
172:         vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock; // <= FOUND
173:         vaults[vaultId].keeperContract = _keeperContract; // <= FOUND
174:         vaults[vaultId].watcherContract = _watcher; // <= FOUND
175:         vaults[vaultId].emergency = _emergency; // <= FOUND
176:         emit VaultAddressesChanged(
177:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
178:         );
179:     }
```
['[362](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L362-L372)']
```solidity
362:     function updateHoldingPostionWithTime(
363:         uint256 vaultId,
364:         bytes32 _positionId,
365:         bytes calldata _data,
366:         bytes calldata additionalData,
367:         bool removePosition,
368:         uint256 positionTimestamp
369:     ) external vaultExists(vaultId) {
370:         uint256 positionIndex = updateHoldingPosition(vaultId, _positionId, _data, additionalData, removePosition); // <= FOUND
371:         if (positionIndex != type(uint256).max) {
372:             vaults[vaultId].holdingPositions[positionIndex].positionTimestamp = positionTimestamp; // <= FOUND
373:         }
374:     }
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L72)']
```solidity
68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     {
72:         slippageTolerance[_inputToken][_outputToken] = _slippageTolerance; // <= FOUND
73:         emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance);
74:     }
```


</details>

## [Low-33] Solidity file is susceptible to .selector-related optimizer bug due to the version used

### Resolution 
In Solidity versions prior to 0.8.21, a bug related to the .selector usage in optimizer settings could lead to incorrect code generation, where function evaluations using .selector might not execute as intended. This issue is classified as low-severity, mainly affecting uncommon code patterns where a function call is used instead of a direct contract name for selector lookup. Files using .selector with affected Solidity versions should be reviewed and updated to mitigate potential issues, ensuring contracts function correctly and securely.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L73)']
```solidity
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
73:             if (method == ICreditFacadeV3Multicall.enableToken.selector) { // <= FOUND
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
['[144](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L144-L145)']
```solidity
144:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {
145:         return this.onERC721Received.selector; // <= FOUND
146:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L64-L65)']
```solidity
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {
65:         return this.onERC721Received.selector; // <= FOUND
66:     }
```


</details>

## [Low-34] Functions calling contracts/addresses with transfer hooks are missing reentrancy guards

### Resolution 
While adherence to the check-effects-interaction pattern is commendable, the absence of a reentrancy guard in functions, especially where transfer hooks might be present, can expose the protocol users to risks of read-only reentrancies. Such reentrancy vulnerabilities can be exploited to execute malicious actions even without altering the contract state. Without a reentrancy guard, the only potential mitigation would be to blocklist the entire protocol - an extreme and disruptive measure. Therefore, incorporating a reentrancy guard into these functions is vital to bolster security, as it helps protect against both traditional reentrancy attacks and read-only reentrancies, ensuring robust and safe protocol operations.

Num of instances: 8

### Findings 


<details><summary>Click to show findings</summary>

['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L149-L154)']
```solidity
149:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
150:         external
151:         returns (uint256)
152:     {
153:         emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
154:         if (registry.isAnActiveConnector(vaultId, msg.sender)) { // <= FOUND
155:             IERC20(token).safeTransfer(address(msg.sender), amount);
156:             return amount;
157:         }
158:         return 0;
159:     }
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L91)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]); // <= FOUND
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
82:                 require(success, "BalancerFlashLoan: Flash loan failed");
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) {
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]); // <= FOUND
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
94:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L84-L104)']
```solidity
84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
85:         external
86:         returns (uint256)
87:     {
88:         emit TransferTokensToTrustedAddress(token, amount, caller, data);
89:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
90:         if (msg.sender == accountingManager) {
91:             (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);
92: 
93:             (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
94:             Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData);
95: 
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount); // <= FOUND
97:             amount = newAmount;
98:         } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) { // <= FOUND
99:             IERC20(token).safeTransfer(address(msg.sender), amount);
100:         } else {
101:             uint256 routeId = abi.decode(data, (uint256));
102:             swapHandler.verifyRoute(routeId, msg.sender);
103:             if (caller != address(this)) revert IConnector_InvalidAddress(caller);
104:             IERC20(token).safeTransfer(msg.sender, amount); // <= FOUND
105:         }
106:         _updateTokenInRegistry(token);
107:         return amount;
108:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L36)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     {
31:         if (data.length == 0) { // <= FOUND
32:             IERC20(token).safeTransfer(msg.sender, amount); // <= FOUND
33:             return amount;
34:         }
35:         (uint256 amountToSend, uint256 amountToReturn) = abi.decode(data, (uint256, uint256));
36:         IERC20(token).safeTransfer(msg.sender, amountToSend); // <= FOUND
37:         return amountToReturn;
38:     }
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L197)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner { // <= FOUND
194:         if (token == address(0)) {
195:             (bool success,) = payable(userAddress).call{ value: amount }("");
196:             require(success, "Transfer failed.");
197:         } else { // <= FOUND
198:             IERC20(token).safeTransfer(userAddress, amount);
199:         }
200:         emit Rescued(token, userAddress, amount);
201:     }
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L91)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]); // <= FOUND
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
82:                 require(success, "BalancerFlashLoan: Flash loan failed");
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) {
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]); // <= FOUND
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
94:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L36)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     {
31:         if (data.length == 0) {
32:             IERC20(token).safeTransfer(msg.sender, amount); // <= FOUND
33:             return amount;
34:         }
35:         (uint256 amountToSend, uint256 amountToReturn) = abi.decode(data, (uint256, uint256));
36:         IERC20(token).safeTransfer(msg.sender, amountToSend); // <= FOUND
37:         return amountToReturn;
38:     }
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L198)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner {
194:         if (token == address(0)) {
195:             (bool success,) = payable(userAddress).call{ value: amount }("");
196:             require(success, "Transfer failed.");
197:         } else {
198:             IERC20(token).safeTransfer(userAddress, amount); // <= FOUND
199:         }
200:         emit Rescued(token, userAddress, amount);
201:     }
```


</details>

## [Low-35] Double type casts create complexity within the code

### Resolution 
Double type casting should be avoided in Solidity contracts to prevent unintended consequences and ensure accurate data representation. Performing multiple type casts in succession can lead to unexpected truncation, rounding errors, or loss of precision, potentially compromising the contract's functionality and reliability. Furthermore, double type casting can make the code less readable and harder to maintain, increasing the likelihood of errors and misunderstandings during development and debugging. To ensure precise and consistent data handling, developers should use appropriate data types and avoid unnecessary or excessive type casting, promoting a more robust and dependable contract execution.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L81-L83)']
```solidity
81:         
82:         
83:         int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period))); // <= FOUND
```


</details>

## [Low-36] Events may be emitted out of order due to code not follow the best practice of check-effects-interaction

### Resolution 
The "check-effects-interaction" pattern also impacts event ordering. When a contract doesn't adhere to this pattern, events might be emitted in a sequence that doesn't reflect the actual logical flow of operations. This can cause confusion during event tracking, potentially leading to erroneous off-chain interpretations. To rectify this, always ensure that checks are performed first, state modifications come next, and interactions with external contracts or addresses are done last. This will ensure events are emitted in a logical, consistent manner, providing a clear and accurate chronological record of on-chain actions for off-chain systems and observers.

Num of instances: 24

### Findings 


<details><summary>Click to show findings</summary>

['[680](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L680-L687)']
```solidity
680:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { // <= FOUND
681:         if (token == address(0)) {
682:             (bool success,) = payable(msg.sender).call{ value: amount }("");
683:             require(success, "Transfer failed.");
684:         } else {
685:             IERC20(token).safeTransfer(msg.sender, amount); // <= FOUND
686:         }
687:         emit Rescue(msg.sender, token, amount); // <= FOUND
688:     }
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L232-L256)']
```solidity
232:     function addTrustedPosition(
233:         uint256 vaultId,
234:         uint256 _positionTypeId,
235:         address calculatorConnector,
236:         bool onlyOwner,
237:         bool _isDebt,
238:         bytes calldata _data,
239:         bytes calldata _additionalData
240:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {
241:         Vault storage vault = vaults[vaultId];
242:         bytes32 positionId = calculatePositionId(calculatorConnector, _positionTypeId, _data);
243:         {
244:             if (vault.trustedPositionsBP[positionId].isEnabled) revert AlreadyExists();
245:             if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();
246:             address[] memory usingTokens = IConnector(calculatorConnector).getUnderlyingTokens(_positionTypeId, _data); // <= FOUND
247:             for (uint256 i = 0; i < usingTokens.length; i++) {
248:                 if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) {
249:                     revert TokenNotTrusted(usingTokens[i]);
250:                 }
251:             }
252: 
253:             vault.trustedPositionsBP[positionId] =
254:                 PositionBP(calculatorConnector, _positionTypeId, onlyOwner, true, _isDebt, _data, _additionalData);
255:         }
256:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data); // <= FOUND
257:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L64-L106)']
```solidity
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
83:             address(this), 
84:             address(this), 
85:             IBalancerVault.JoinPoolRequest(
86:                 tokens,
87:                 amounts,
88:                 abi.encode(
89:                     IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                     amountsWithoutBPT, 
91:                     minBPT 
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
102:             uint256 amount = IERC20(pool).balanceOf(address(this)); // <= FOUND
103:             _approveOperations(pool, _poolInfo.auraPoolAddress, amount);
104:             IRewardPool(_poolInfo.auraPoolAddress).deposit(auraAmount, address(this));
105:         }
106:         emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount); // <= FOUND
107:     }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L29-L37)']
```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant { // <= FOUND
30:         _approveOperations(asset, market, amount);
31:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
32:         IComet(market).supply(asset, amount); // <= FOUND
33:         registry.updateHoldingPosition(
34:             vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false
35:         );
36:         _updateTokenInRegistry(asset);
37:         emit Supply(market, asset, amount); // <= FOUND
38:     }
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L48-L59)']
```solidity
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant { // <= FOUND
49:         IComet(_market).withdraw(asset, amount); // <= FOUND
50:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
51:         uint256 healthFactor = getAccountHealthFactor(IComet(_market));
52:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
53:         if (getCollBlanace(IComet(_market), false) == 0) {
54:             registry.updateHoldingPosition(
55:                 vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true
56:             );
57:         }
58:         _updateTokenInRegistry(asset);
59:         emit WithdrawOrBorrow(_market, asset, amount); // <= FOUND
60:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L63-L67)']
```solidity
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant { // <= FOUND
64:         address rewardToken = IRewards(rewardContract).rewardConfig(market).token; // <= FOUND
65:         IRewards(rewardContract).claim(address(market), address(this), true); // <= FOUND
66:         _updateTokenInRegistry(rewardToken);
67:         emit ClaimRewards(rewardContract, market); // <= FOUND
68:     }
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L117-L149)']
```solidity
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
131:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount); // <= FOUND
132:         } else if (poolInfo.tokens.length == 3) {
133:             uint256[3] memory amounts;
134:             amounts[depositIndex] = amount;
135:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount); // <= FOUND
136:         } else if (poolInfo.tokens.length == 4) {
137:             uint256[4] memory amounts;
138:             amounts[depositIndex] = amount;
139:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount); // <= FOUND
140:         } else if (poolInfo.tokens.length == 5) {
141:             uint256[5] memory amounts;
142:             amounts[depositIndex] = amount;
143:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount); // <= FOUND
144:         } else if (poolInfo.tokens.length == 6) {
145:             uint256[6] memory amounts;
146:             amounts[depositIndex] = amount;
147:             ICurveSwap(poolAddress).add_liquidity(amounts, minAmount); // <= FOUND
148:         }
149:         emit OpenCurvePosition(pool, depositIndex, amount, minAmount); // <= FOUND
150:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
151:     }
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L160-L174)']
```solidity
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     {
165:         PoolInfo memory poolInfo = _getPoolInfo(pool);
166:         address token = poolInfo.tokens[withdrawIndex];
167:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));
168: 
169:         ICurveSwap(poolInfo.pool).remove_liquidity_one_coin(amount, int128(uint128(withdrawIndex)), minAmount); // <= FOUND
170:         _updateTokenInRegistry(token);
171:         if (totalLpBalanceOf(poolInfo) == 0) {
172:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
173:         }
174:         emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount); // <= FOUND
175:     }
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L192-L194)']
```solidity
192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager { // <= FOUND
193:         IConvexBasicRewards(pool).withdraw(amount, true); // <= FOUND
194:         emit WithdrawFromConvexRewardPool(pool, amount); // <= FOUND
195:     }
```
['[202](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L202-L204)']
```solidity
202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager { // <= FOUND
203:         IRewardsGauge(pool).withdraw(amount); // <= FOUND
204:         emit WithdrawFromGauge(pool, amount); // <= FOUND
205:     }
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L212-L214)']
```solidity
212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager { // <= FOUND
213:         IDepositToken(depostiToken).withdraw(address(this), amount); // <= FOUND
214:         emit WithdrawFromPrisma(depostiToken, amount); // <= FOUND
215:     }
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L24-L33)']
```solidity
24:     function openAccount(address facade, uint256 ref) public onlyManager { // <= FOUND
25:         address c = ICreditFacadeV3(facade).openCreditAccount(address(this), new MultiCall[](0), ref); // <= FOUND
26:         registry.updateHoldingPosition(
27:             vaultId,
28:             registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),
29:             abi.encode(c),
30:             "",
31:             false
32:         );
33:         emit OpenAccount(facade, ref); // <= FOUND
34:     }
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L41-L51)']
```solidity
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant { // <= FOUND
42:         ICreditFacadeV3(facade).closeCreditAccount(creditAccount, new MultiCall[](0)); // <= FOUND
43: 
44:         registry.updateHoldingPosition(
45:             vaultId,
46:             registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)),
47:             abi.encode(creditAccount),
48:             "",
49:             true
50:         );
51:         emit CloseAccount(facade, creditAccount); // <= FOUND
52:     }
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L85)']
```solidity
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
79:             _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount); // <= FOUND
80:         }
81:         ICreditFacadeV3(facade).multicall(creditAccount, calls); // <= FOUND
82:         if (approvalToken != address(0)) {
83:             _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager()); // <= FOUND
84:         }
85:         emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount); // <= FOUND
86:     }
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L78-L89)']
```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant { // <= FOUND
79:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens(); // <= FOUND
80: 
81:         (, address _underlyingToken,) = _SY.assetInfo();
82: 
83:         _approveOperations(_underlyingToken, address(_SY), amount);
84:         
85:         uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);
86: 
87:         bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));
88:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
89:         emit Supply(market, syMinted); // <= FOUND
90:     }
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L97-L101)']
```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant { // <= FOUND
98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens(); // <= FOUND
99:         IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);
100:         _YT.mintPY(address(this), address(this));
101:         emit MintPTAndYT(market, syAmount); // <= FOUND
102:     }
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L149-L156)']
```solidity
149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
150:         external
151:         onlyManager
152:     {
153:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens(); // <= FOUND
154:         _approveOperations(address(_YT), address(pendleRouter), exactYTIn);
155:         pendleRouter.swapExactYtForPt(address(this), market, exactYTIn, min, guess);
156:         emit SwapYTForPT(market, exactYTIn, min, guess); // <= FOUND
157:     }
```
['[166](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L166-L173)']
```solidity
166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
167:         public
168:         onlyManager
169:     {
170:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens(); // <= FOUND
171:         _approveOperations(address(_YT), address(pendleRouter), exactYTIn);
172:         pendleRouter.swapExactYtForSy(address(this), market, exactYTIn, min, orderData);
173:         emit SwapYTForSY(market, exactYTIn, min, orderData); // <= FOUND
174:     }
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L66)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {
57:         bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
58:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
59:         address collateral = abi.decode(positionInfo.additionalData, (address));
60:         address debTtoken = ITroveManager(tm).debtToken(); // <= FOUND
61:         _approveOperations(collateral, address(zap), dAmount);
62:         zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));
63:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
64:         _updateTokenInRegistry(collateral);
65:         _updateTokenInRegistry(debTtoken);
66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount); // <= FOUND
67:     }
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L121)']
```solidity
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
112:             _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount); // <= FOUND
113:         }
114:         borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this));
115:         _updateTokenInRegistry(ITroveManager(tm).debtToken()); // <= FOUND
116:         
117:         uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this)); // <= FOUND
118:         if (minimumHealthFactor > healthFactor) {
119:             revert IConnector_LowHealthFactor(healthFactor);
120:         }
121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing); // <= FOUND
122:     }
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L49-L69)']
```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant { // <= FOUND
50:         address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;
51:         address underlyingToken = IStargatePool(lpAddress).token(); // <= FOUND
52:         if (depositRequest.routerAmount > 0) {
53:             _approveOperations(underlyingToken, address(stargateRouter), depositRequest.routerAmount);
54:             stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this));
55:             _updateTokenInRegistry(underlyingToken);
56:         }
57:         if (depositRequest.LPStakingAmount > 0) {
58:             uint256 stakingAmount = depositRequest.LPStakingAmount;
59:             if (depositRequest.LPStakingAmount == type(uint256).max) {
60:                 stakingAmount = IERC20(lpAddress).balanceOf(address(this)); // <= FOUND
61:             }
62:             _approveOperations(lpAddress, address(LPStaking), stakingAmount);
63:             LPStaking.deposit(depositRequest.poolId, stakingAmount);
64:         }
65:         _updateTokenInRegistry(rewardToken);
66:         bytes32 positionId =
67:             registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));
68:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
69:         emit DepositIntoStargatePool(depositRequest); // <= FOUND
70:     }
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L76-L96)']
```solidity
76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant { // <= FOUND
77:         address lpAddress = LPStaking.poolInfo(withdrawRequest.poolId).lpToken;
78:         address underlyingToken = IStargatePool(lpAddress).token(); // <= FOUND
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
89:         if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) { // <= FOUND
90:             bytes32 positionId = registry.calculatePositionId(
91:                 address(this), STARGATE_LP_POSITION_TYPE, abi.encode(withdrawRequest.poolId)
92:             );
93:             registry.updateHoldingPosition(vaultId, positionId, "", "", true);
94:         }
95:         _updateTokenInRegistry(rewardToken);
96:         emit WithdrawFromStargatePool(withdrawRequest); // <= FOUND
97:     }
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L182)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     {
170:         if (!_isNative(token)) {
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId)); // <= FOUND
172: 
173:             _setAllowance(token, lifi, amount);
174:         }
175: 
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);
177: 
178:         if (!success) {
179:             revert FailedToForward(err);
180:         }
181: 
182:         emit Forwarded(lifi, address(token), amount, data); // <= FOUND
183:     }
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L200)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner { // <= FOUND
194:         if (token == address(0)) {
195:             (bool success,) = payable(userAddress).call{ value: amount }(""); // <= FOUND
196:             require(success, "Transfer failed.");
197:         } else {
198:             IERC20(token).safeTransfer(userAddress, amount); // <= FOUND
199:         }
200:         emit Rescued(token, userAddress, amount); // <= FOUND
201:     }
```


</details>

## [Low-37] Inconsistent checks of address params against address(0)

### Resolution 
Only some address parameters are checked against address(0), to ensure consistency ensure all address parameters are checked.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L184-L184)']
```solidity
184:     function _update(address from, address to, uint256 amount) internal override { // <= FOUND '    function _update(address from, address to, uint256 amount) internal override '
185:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {
186:             revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
187:         }
188:         super._update(from, to, amount);
189:     }
```
['[105](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L105-L114)']
```solidity
105:     function addVault(
106:         uint256 vaultId,
107:         address _accountingManager,
108:         address _baseToken,
109:         address _governer,
110:         address _maintainer,
111:         address _maintainerWithoutTimelock, // <= FOUND 'address _maintainerWithoutTimelock'
112:         address _keeperContract,
113:         address _watcher,
114:         address _emergency, // <= FOUND 'address _emergency'
115:         address[] calldata _trustedTokens
116:     ) external onlyRole(MAINTAINER_ROLE) {
117:         if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();
118:         Vault storage vault = vaults[vaultId];
119:         require(_governer != address(0));
120:         require(_accountingManager != address(0));
121:         require(_baseToken != address(0));
122:         require(_maintainer != address(0));
123:         require(_keeperContract != address(0));
124:         require(_watcher != address(0));
125: 
126:         vault.accountManager = _accountingManager;
127:         vault.baseToken = _baseToken;
128:         vault.governer = _governer;
129:         vault.maintainer = _maintainer;
130:         vault.maintainerWithoutTimeLock = _maintainerWithoutTimelock;
131:         vault.keeperContract = _keeperContract;
132:         vault.watcherContract = _watcher;
133:         vault.emergency = _emergency;
134:         
135:         vault.connectors[vault.accountManager].enabled = true;
136:         vault.enabled = true;
137:         for (uint256 i = 0; i < _trustedTokens.length; i++) {
138:             vault.connectors[vault.accountManager].trustedTokens[_trustedTokens[i]] = true;
139:         }
140:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));
141:         emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens);
142:         emit VaultAddressesChanged(
143:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
144:         );
145:     }
```
['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L156-L163)']
```solidity
156:     function changeVaultAddresses(
157:         uint256 vaultId,
158:         address _governer,
159:         address _maintainer,
160:         address _maintainerWithoutTimelock, // <= FOUND 'address _maintainerWithoutTimelock'
161:         address _keeperContract,
162:         address _watcher,
163:         address _emergency // <= FOUND 'address _emergency'
164:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {
165:         require(_governer != address(0));
166:         require(_maintainer != address(0));
167:         require(_keeperContract != address(0));
168:         require(_watcher != address(0));
169: 
170:         vaults[vaultId].governer = _governer;
171:         vaults[vaultId].maintainer = _maintainer;
172:         vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock;
173:         vaults[vaultId].keeperContract = _keeperContract;
174:         vaults[vaultId].watcherContract = _watcher;
175:         vaults[vaultId].emergency = _emergency;
176:         emit VaultAddressesChanged(
177:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
178:         );
179:     }
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L74)']
```solidity
62:     function executeCommands(
63:         address facade, // <= FOUND 'address facade'
64:         address creditAccount, // <= FOUND 'address creditAccount'
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {
69:         for (uint256 i = 0; i < calls.length; i++) {
70:             if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
71:             bytes4 method = bytes4(calls[i].callData[:4]);
72: 
73:             if (method == ICreditFacadeV3Multicall.enableToken.selector) {
74:                 (address token) = abi.decode(calls[i].callData[4:], (address)); // <= FOUND 'address token'
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
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L193)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner { // <= FOUND 'address token'
194:         if (token == address(0)) {
195:             (bool success,) = payable(userAddress).call{ value: amount }("");
196:             require(success, "Transfer failed.");
197:         } else {
198:             IERC20(token).safeTransfer(userAddress, amount);
199:         }
200:         emit Rescued(token, userAddress, amount);
201:     }
```


</details>

## [NonCritical-1] Having chainId as a parameter can introduce cross chain replay attacks 

### Resolution 
Accepting chainId as a parameter in a Solidity contract could open up possibilities for cross-chain replay attacks. An attacker could execute a transaction on one chain, then 'replay' it on another chain where the contract has been deployed, leading to unintended consequences. It's crucial to get the chainId within the contract using `block.chainId` to ensure that the transactions are valid and specific to the chain the contract resides on. The `block.chainId` value is provided by the EVM and can be trusted, as it's difficult to manipulate and is unique to each Ethereum-based network. This enhances the security of cross-chain operations.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner  // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner  // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46-L46)']
```solidity
46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer  // <= FOUND
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L32-L32)']
```solidity
32:     function updateTVL(uint256 chainId, uint256 tvl, uint256 updateTime) external nonReentrant  // <= FOUND
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55-L55)']
```solidity
55:     function addChain(uint256 _chainId, bool state) external onlyOwner  // <= FOUND
```


</details>

## [NonCritical-2] Functions with unused parameters 

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L27)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data) // <= FOUND
28:         external
29:         returns (uint256)
30:     {
31:         if (data.length == 0) {
32:             IERC20(token).safeTransfer(msg.sender, amount);
33:             return amount;
34:         }
35:         (uint256 amountToSend, uint256 amountToReturn) = abi.decode(data, (uint256, uint256));
36:         IERC20(token).safeTransfer(msg.sender, amountToSend);
37:         return amountToReturn;
38:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L40-L40)']
```solidity
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external { // <= FOUND
41:         for (uint256 i = 0; i < tokens.length; i++) {
42:             
43: 
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
45:         }
46:         for (uint256 i = 0; i < tokens.length; i++) {
47:             _updateTokenInRegistry(tokens[i]); 
48:         }
49:     }
```


</details>

## [NonCritical-3] Consider using time variables when defining time related variables 

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L19-L20)']
```solidity
19:     
20:     uint32 public period = 1800; // <= FOUND
```


</details>

## [NonCritical-4] Unnecessary struct attribute prefix 

### Resolution 
In struct definitions, using redundant prefixes for attributes is unnecessary. For instance, in a struct named Employee, attributes like employeeName, employeeID, and employeeEmail can be simplified to name, ID, and email respectively, since they are already inherently associated with Employee. By removing these repetitive prefixes, the code becomes more concise and easier to read, maintaining its contextual clarity.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L7-L8)']
```solidity
7: struct PoolInfo { // <= FOUND
8:     address pool; // <= FOUND
9:     address[] tokens;
10:     uint256 tokenIndex;
11:     bytes32 poolId; // <= FOUND
12:     uint256[] weights;
13:     address auraPoolAddress;
14:     uint256 boosterPoolId;
15: }
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L8-L9)']
```solidity
8: struct ChainInfo { // <= FOUND
9:     uint256 chainId; // <= FOUND
10:     address lzHelperAddress;
11: }
```


</details>

## [NonCritical-5] Using abi.encodePacked can result in hash collision when used in hashing functions 

### Resolution 
Consider using abi.encode as this pads data to 32 byte segments

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[136](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L136-L136)']
```solidity
136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L102-L102)']
```solidity
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
```


</details>

## [NonCritical-6] Getting a bool return value does not confirm the existence of a function in an external call 

### Resolution 
External calls to contracts using `address.call()` might return a boolean indicating success or failure. However, this boolean doesn't guarantee the existence of a called function. If a function isn't present, the call won't revert but will simply return `false`. This behavior might lead developers into mistakenly believing they're interacting with a legitimate or expected function, whereas it might not exist at all—a scenario sometimes termed as "phantom functions". Resolution: Instead of solely relying on the boolean, further validate the contract you're interacting with, or use interfaces or abstract contracts to enforce the existence of expected functions.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L176)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     {
170:         if (!_isNative(token)) {
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId));
172: 
173:             _setAllowance(token, lifi, amount);
174:         }
175: 
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data); // <= FOUND
177: 
178:         if (!success) {
179:             revert FailedToForward(err);
180:         }
181: 
182:         emit Forwarded(lifi, address(token), amount, data);
183:     }
```


</details>

## [NonCritical-7] Default address(0) can be returned 

### Resolution 
Allowing a function in Solidity to return the default address (address(0)) can be problematic as it can represent uninitialized or invalid addresses. If such an address is utilized in transfer operations or other sensitive actions, it could lead to loss of funds or unpredicted behavior. It's prudent to include checks in your functions to prevent the return of the zero address, enhancing contract security.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[440](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L440-L440)']
```solidity
440:     function getGovernanceAddresses(uint256 vaultId)
441:         public
442:         view
443:         returns (address, address, address, address, address, address)
444:     {
445:         return (
446:             vaults[vaultId].governer,
447:             vaults[vaultId].maintainer,
448:             vaults[vaultId].maintainerWithoutTimeLock,
449:             vaults[vaultId].keeperContract,
450:             vaults[vaultId].watcherContract,
451:             vaults[vaultId].emergency
452:         );
453:     }
```
['[507](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L507-L507)']
```solidity
507:     function getVaultAddresses(uint256 vaultId) public view returns (address, address) {
508:         return (vaults[vaultId].accountManager, vaults[vaultId].baseToken);
509:     }
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L116-L116)']
```solidity
116:     function getCurrentLiquidity(uint256 tokenId) public view returns (uint128, address, address) {
117:         (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);
118:         return (liquidity, token0, token1);
119:     }
```


</details>

## [NonCritical-8] Using zero as a parameter

### Resolution 
Taking 0 as a valid argument in Solidity without checks can lead to severe security issues. A historical example is the infamous 0x0 address bug where numerous tokens were lost. This happens because '0' can be interpreted as an uninitialized address, leading to transfers to the '0x0' address, effectively burning tokens. Moreover, 0 as a denominator in division operations would cause a runtime exception. It's also often indicative of a logical error in the caller's code. It's important to always validate input and handle edge cases like 0 appropriately. Use `require()` statements to enforce conditions and provide clear error messages to facilitate debugging and safer code.

Num of instances: 22

### Findings 


<details><summary>Click to show findings</summary>

['[198](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L198-L213)']
```solidity
198:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused { // <= FOUND
199:         if (amount == 0) {
200:             revert NoyaAccounting_INVALID_AMOUNT();
201:         }
202: 
203:         baseToken.safeTransferFrom(msg.sender, address(this), amount);
204: 
205:         if (amount > depositLimitPerTransaction) {
206:             revert NoyaAccounting_DepositLimitPerTransactionExceeded();
207:         }
208: 
209:         if (TVL() > depositLimitTotalAmount) {
210:             revert NoyaAccounting_TotalDepositLimitExceeded();
211:         }
212: 
213:         depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0); // <= FOUND
214:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);
215:         depositQueue.last += 1;
216:         depositQueue.totalAWFDeposit += amount;
217:     }
```
['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L301-L310)']
```solidity
301:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused { // <= FOUND
302:         if (balanceOf(msg.sender) < share + withdrawRequestsByAddress[msg.sender]) {
303:             revert NoyaAccounting_INSUFFICIENT_FUNDS(
304:                 balanceOf(msg.sender), share, withdrawRequestsByAddress[msg.sender]
305:             );
306:         }
307:         withdrawRequestsByAddress[msg.sender] += share;
308: 
309:         
310:         withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0); // <= FOUND
311:         emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);
312:         withdrawQueue.last += 1;
313:     }
```
['[105](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L105-L140)']
```solidity
105:     function addVault(
106:         uint256 vaultId,
107:         address _accountingManager,
108:         address _baseToken,
109:         address _governer,
110:         address _maintainer,
111:         address _maintainerWithoutTimelock,
112:         address _keeperContract,
113:         address _watcher,
114:         address _emergency,
115:         address[] calldata _trustedTokens
116:     ) external onlyRole(MAINTAINER_ROLE) {
117:         if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();
118:         Vault storage vault = vaults[vaultId];
119:         require(_governer != address(0));
120:         require(_accountingManager != address(0));
121:         require(_baseToken != address(0));
122:         require(_maintainer != address(0));
123:         require(_keeperContract != address(0));
124:         require(_watcher != address(0));
125: 
126:         vault.accountManager = _accountingManager;
127:         vault.baseToken = _baseToken;
128:         vault.governer = _governer;
129:         vault.maintainer = _maintainer;
130:         vault.maintainerWithoutTimeLock = _maintainerWithoutTimelock;
131:         vault.keeperContract = _keeperContract;
132:         vault.watcherContract = _watcher;
133:         vault.emergency = _emergency;
134:         
135:         vault.connectors[vault.accountManager].enabled = true;
136:         vault.enabled = true;
137:         for (uint256 i = 0; i < _trustedTokens.length; i++) {
138:             vault.connectors[vault.accountManager].trustedTokens[_trustedTokens[i]] = true;
139:         }
140:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max)); // <= FOUND
141:         emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens);
142:         emit VaultAddressesChanged(
143:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
144:         );
145:     }
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L45-L47)']
```solidity
45:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant { // <= FOUND
46:         _approveOperations(supplyToken, pool, amount);
47:         IPool(pool).supply(supplyToken, amount, address(this), 0); // <= FOUND
48:         registry.updateHoldingPosition(
49:             vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", false
50:         );
51:         _updateTokenInRegistry(supplyToken);
52:         emit Supply(supplyToken, amount);
53:     }
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L61-L69)']
```solidity
61:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
62:         external
63:         onlyManager
64:         nonReentrant
65:     {
66:         if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) {
67:             revert IConnector_UntrustedToken(_borrowAsset);
68:         }
69:         IPool(pool).borrow(_borrowAsset, _amount, _interestRateMode, 0, address(this)); // <= FOUND
70:         
71:         (,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this));
72:         if (healthFactor < minimumHealthFactor) revert IConnector_LowHealthFactor(healthFactor);
73:         _updateTokenInRegistry(_borrowAsset);
74:         emit Borrow(_borrowAsset, _amount);
75:     }
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L81)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
82:                 require(success, "BalancerFlashLoan: Flash loan failed");
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) {
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
94:     }
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L43-L50)']
```solidity
43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant { // <= FOUND
44:         address token = dolomiteMargin.getMarketTokenAddress(marketId);
45:         depositWithdrawalProxy.withdrawWeiFromDefaultAccount(
46:             marketId, _amount, AccountBalanceHelper.BalanceCheckFlag.None
47:         );
48:         
49:         _updateTokenInRegistry(token);
50:         (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0)); // <= FOUND
51:         if (markets.length == 0) {
52:             registry.updateHoldingPosition(
53:                 vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true
54:             );
55:         }
56:     }
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L58-L58)']
```solidity
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
68:         
69:         borrowPositionProxy.openBorrowPosition(
70:             0, accountId, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
71:         );
72:         registry.updateHoldingPosition(
73:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
74:         );
75:     }
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L77-L92)']
```solidity
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
88:             borrowPositionProxy.transferBetweenAccounts( // <= FOUND
89:                 accountId, 0, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
90:             );
91:         } else {
92:             borrowPositionProxy.transferBetweenAccounts( // <= FOUND
93:                 0, accountId, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
94:             );
95:         }
96:     }
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L98-L100)']
```solidity
98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant { // <= FOUND
99:         
100:         borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds); // <= FOUND
101:         registry.updateHoldingPosition(
102:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
103:         );
104:     }
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L88-L96)']
```solidity
88:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant { // <= FOUND
89:         uint256 sendEthAmount = p.ethPoolIncluded ? p.tokenARequiredAllowance : 0;
90:         _approveOperations(p.pool.tokenA(), maverickRouter, p.tokenARequiredAllowance); 
91:         _approveOperations(p.pool.tokenB(), maverickRouter, p.tokenBRequiredAllowance);
92:         
93:         uint256 tokenId;
94:         {
95:             (tokenId,,,) = IMaverickRouter(maverickRouter).addLiquidityToPool{ value: sendEthAmount }(
96:                 p.pool, 0, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline // <= FOUND
97:             );
98:         }
99:         registry.updateHoldingPosition(
100:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false
101:         );
102:         _updateTokenInRegistry(p.pool.tokenA());
103:         _updateTokenInRegistry(p.pool.tokenB());
104:         emit AddLiquidityInMaverickPool(p);
105:     }
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L35-L39)']
```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant { // <= FOUND
36:         MarketParams memory params = morphoBlue.idToMarketParams(id);
37:         if (sOrC) {
38:             _approveOperations(params.loanToken, address(morphoBlue), amount);
39:             morphoBlue.supply(params, amount, 0, address(this), ""); // <= FOUND
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
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L58-L61)']
```solidity
58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant { // <= FOUND
59:         MarketParams memory params = morphoBlue.idToMarketParams(id);
60:         if (sOrC) {
61:             morphoBlue.withdraw(params, amount, 0, address(this), address(this)); // <= FOUND
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
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L80-L82)']
```solidity
80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant { // <= FOUND
81:         MarketParams memory market = morphoBlue.idToMarketParams(id);
82:         morphoBlue.borrow(market, amount, 0, address(this), address(this)); // <= FOUND
83:         if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {
84:             revert IConnector_LowHealthFactor(getHealthFactor(id, morphoBlue.market(id)));
85:         }
86:         _updateTokenInRegistry(market.loanToken);
87:         emit Borrow(amount, id);
88:     }
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L95-L98)']
```solidity
95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant { // <= FOUND
96:         MarketParams memory params = morphoBlue.idToMarketParams(id);
97:         _approveOperations(params.loanToken, address(morphoBlue), amount);
98:         morphoBlue.repay(params, amount, 0, address(this), ""); // <= FOUND
99:         _updateTokenInRegistry(params.loanToken);
100:         emit Repay(amount, id);
101:     }
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L114)']
```solidity
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
114:         borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this)); // <= FOUND
115:         _updateTokenInRegistry(ITroveManager(tm).debtToken());
116:         
117:         uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));
118:         if (minimumHealthFactor > healthFactor) {
119:             revert IConnector_LowHealthFactor(healthFactor);
120:         }
121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);
122:     }
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L103-L104)']
```solidity
103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant { // <= FOUND
104:         LPStaking.deposit(poolId, 0); // <= FOUND
105:         _updateTokenInRegistry(rewardToken);
106:         emit ClaimStargateRewards(poolId);
107:     }
```
['[135](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L135-L138)']
```solidity
135:     function _updateTokenInRegistry(address token, bool remove) internal { // <= FOUND
136:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
137:         
138:         bytes32 positionId = registry.calculatePositionId(accountingManager, 0, abi.encode(token)); // <= FOUND
139:         
140:         uint256 positionIndex =
141:             registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));
142:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
143:             emit UpdateTokenInRegistry(token, remove);
144:             registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);
145:         }
146:     }
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L79-L82)']
```solidity
79:     function _updateTokenInRegistry(address token, bool remove) internal { // <= FOUND
80:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
81:         
82:         bytes32 positionId = registry.calculatePositionId(accountingManager, 0, abi.encode(token)); // <= FOUND
83:         
84:         uint256 positionIndex =
85:             registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));
86:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
87:             registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);
88:         }
89:     }
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L212)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {
211:         for (uint256 i = 0; i < tokensIn.length; i++) {
212:             _executeSwap( // <= FOUND
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
218:         }
219:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L75-L80)']
```solidity
75:     function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public { // <= FOUND
76:         if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
77: 
78:         uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
79:         bytes memory data = abi.encode(vaultId, tvl, updateTime);
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this)));  // <= FOUND
81:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L109-L123)']
```solidity
109:     function getValueFromChainlinkFeed(
110:         AggregatorV3Interface source,
111:         uint256 amountIn,
112:         uint256 sourceTokenUnit,
113:         bool isInverse
114:     ) public view returns (uint256) {
115:         int256 price;
116:         uint256 updatedAt;
117:         (, price,, updatedAt,) = source.latestRoundData();
118:         uint256 uintprice = uint256(price);
119:         if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
120:             revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
121:         }
122:         if (price <= 0) {
123:             revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0)); // <= FOUND
124:         }
125:         if (isInverse) {
126:             return (amountIn * sourceTokenUnit) / uintprice;
127:         }
128:         return (amountIn * uintprice) / (sourceTokenUnit);
129:     }
```


</details>

## [NonCritical-9] Token burning is centralized

### Resolution 
Centralized ERC20 token burning, where only a select few addresses have control over the burn function, can be viewed negatively. It introduces risks of manipulation, as the power to alter token supply is concentrated in the hands of a small group, potentially affecting token value unfairly. Such centralization can also introduce risks if the admin account(s) is compromised. Consider implementing a timelock feature so users can decide to opt out of the protocol if they do not agree with actions taken.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L27-L27)']
```solidity
27:     function burnShares(uint256 amount) external onlyOwner { // <= FOUND
28:         AccountingManager(accountingManager).burnShares(amount);
29:     }
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L203-L205)']
```solidity
203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant { // <= FOUND
204:         IERC20(address(market)).safeTransfer(address(market), amount);
205:         market.burn(address(this), address(market), amount); // <= FOUND
206:         market.skim();
207:         emit BurnLP(address(market), amount);
208:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L63-L74)']
```solidity
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
74:             positionManager.burn(p.tokenId); // <= FOUND
75:             bytes32 positionId =
76:                 registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(token0, token1));
77:             bytes memory positionData = abi.encode(p.tokenId);
78:             registry.updateHoldingPosition(vaultId, positionId, positionData, "", true);
79:         }
80:         emit DecreasePosition(p);
81:     }
```


</details>

## [NonCritical-10] Token minting is centralized

### Resolution 
Centralized ERC20 token minting, where only a select few addresses have control over the mint function, can be viewed negatively. It introduces risks of manipulation, as the power to alter token supply is concentrated in the hands of a small group, potentially affecting token value unfairly. Such centralization can also introduce risks if the admin account(s) is compromised. Consider implementing a timelock feature so users can decide to opt out of the protocol if they do not agree with actions taken.

Num of instances: 4

### Findings 


<details><summary>Click to show findings</summary>

['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L97-L97)']
```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant { // <= FOUND
98:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
99:         IERC20(address(_SY)).safeTransfer(address(_YT), syAmount);
100:         _YT.mintPY(address(this), address(this));
101:         emit MintPTAndYT(market, syAmount);
102:     }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L102-L102)']
```solidity
102:     function mintOrBurnSUSD( // <= FOUND
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager {
109:         
110:         address usdToken = SNXCoreProxy.getUsdToken();
111:         if (mintOrBurn) {
112:             SNXCoreProxy.mintUsd(_accountId, poolId, collateralType, _amount);
113:         } else {
114:             _approveOperations(usdToken, address(SNXCoreProxy), _amount);
115:             SNXCoreProxy.burnUsd(_accountId, poolId, collateralType, _amount);
116:         }
117:         _updateTokenInRegistry(collateralType);
118:         _updateTokenInRegistry(usdToken);
119:     }
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L112-L116)']
```solidity
112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {
113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
114:         IERC20(address(_SY)).safeTransfer(address(market), SYamount);
115:         IERC20(address(_PT)).safeTransfer(address(market), PTamount);
116:         market.mint(address(this), SYamount, PTamount); // <= FOUND
117:         market.skim();
118:         emit DepositIntoMarket(address(market), SYamount, PTamount);
119:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L40-L49)']
```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {
41:         bytes32 positionId =
42:             registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));
43:         p.recipient = address(this);
44:         
45:         _approveOperations(p.token0, address(positionManager), p.amount0Desired);
46:         _approveOperations(p.token1, address(positionManager), p.amount1Desired);
47: 
48:         
49:         (tokenId,,,) = positionManager.mint(p); // <= FOUND
50:         bytes memory positionData = abi.encode(tokenId);
51:         registry.updateHoldingPosition(
52:             vaultId, positionId, positionData, abi.encode(p.tickLower, p.tickUpper, p.fee), false
53:         );
54:         _updateTokenInRegistry(p.token0);
55:         _updateTokenInRegistry(p.token1);
56:         emit OpenPosition(p, tokenId);
57:     }
```


</details>

## [NonCritical-11] In functions which accept an address as a parameter, there should be a zero address check to prevent bugs

### Resolution 
In smart contract development, especially with Solidity, it's crucial to validate inputs to functions. When a function accepts an Ethereum address as a parameter, implementing a zero address check (i.e., ensuring the address is not `0x0`) is a best practice to prevent potential bugs and vulnerabilities. The zero address (`0x0`) is a default value and generally indicates an uninitialized or invalid state. Passing the zero address to certain functions can lead to unintended behaviors, like funds getting locked permanently or transactions failing silently. By checking for and rejecting the zero address, developers can ensure that the function operates as intended and interacts only with valid Ethereum addresses. This check enhances the contract's robustness and security.

Num of instances: 130

### Findings 


<details><summary>Click to show findings</summary>

['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L149-L149)']
```solidity
149:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
150:         external
151:         returns (uint256)
152:     
```
['[198](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L198-L198)']
```solidity
198:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused 
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L254)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     
```
['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L301-L301)']
```solidity
301:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused 
```
['[629](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L629-L629)']
```solidity
629:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) 
```
['[639](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L639-L639)']
```solidity
639:     function _getValue(address token, address base, uint256 amount) internal view returns (uint256) 
```
['[690](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L690-L690)']
```solidity
690:     function mint(uint256 shares, address receiver) public override returns (uint256) 
```
['[694](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L694-L694)']
```solidity
694:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) 
```
['[698](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L698-L698)']
```solidity
698:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) 
```
['[702](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L702-L702)']
```solidity
702:     function deposit(uint256 assets, address receiver) public override returns (uint256) 
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) 
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L185-L185)']
```solidity
185:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
186:         external
187:         onlyVaultMaintainer(vaultId)
188:         vaultExists(vaultId)
189:     
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L203-L203)']
```solidity
203:     function updateConnectorTrustedTokens(
204:         uint256 vaultId,
205:         address _connectorAddress,
206:         address[] calldata _tokens,
207:         bool trusted
208:     ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) 
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L232-L232)']
```solidity
232:     function addTrustedPosition(
233:         uint256 vaultId,
234:         uint256 _positionTypeId,
235:         address calculatorConnector,
236:         bool onlyOwner,
237:         bool _isDebt,
238:         bytes calldata _data,
239:         bytes calldata _additionalData
240:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant 
```
['[385](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L385-L385)']
```solidity
385:     function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
386:         public
387:         view
388:         returns (uint256)
389:     
```
['[427](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L427-L427)']
```solidity
427:     function isPositionTrustedForConnector(uint256 vaultId, bytes32 _positionId, address connector)
428:         public
429:         view
430:         returns (bool)
431:     
```
['[461](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L461-L461)']
```solidity
461:     function isTokenTrusted(uint256 vaultId, address token, address connector) public view returns (bool) 
```
['[477](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L477-L477)']
```solidity
477:     function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)
478:         public
479:         pure
480:         returns (bytes32)
481:     
```
['[490](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L490-L490)']
```solidity
490:     function isAnActiveConnector(uint256 vaultId, address connectorAddress) public view returns (bool) 
```
['[516](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L516-L516)']
```solidity
516:     function isAddressTrusted(uint256 vaultId, address addr) public view returns (bool) 
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L45-L45)']
```solidity
45:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant 
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L61-L61)']
```solidity
61:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
62:         external
63:         onlyManager
64:         nonReentrant
65:     
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L80-L80)']
```solidity
80:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L87-L87)']
```solidity
87:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager 
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L99-L99)']
```solidity
99:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant 
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L113-L113)']
```solidity
113:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) 
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L100-L100)']
```solidity
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant 
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L106-L106)']
```solidity
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant 
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L111-L111)']
```solidity
111:     function claim(address pool) public onlyManager nonReentrant 
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L162)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) 
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L53-L53)']
```solidity
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant 
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L162)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L29-L29)']
```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant 
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L48-L48)']
```solidity
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant 
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L63-L63)']
```solidity
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant 
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L162)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L68-L68)']
```solidity
68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant 
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L81-L81)']
```solidity
81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant 
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L103-L103)']
```solidity
103:     function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager 
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L160-L160)']
```solidity
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L192-L192)']
```solidity
192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager 
```
['[202](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L202-L202)']
```solidity
202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager 
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L212-L212)']
```solidity
212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager 
```
['[221](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L221-L221)']
```solidity
221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant 
```
['[233](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L233-L233)']
```solidity
233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant 
```
['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L247-L247)']
```solidity
247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant 
```
['[258](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L258-L258)']
```solidity
258:     function _getPoolInfo(address pool) internal view returns (PoolInfo memory) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L24-L24)']
```solidity
24:     function openAccount(address facade, uint256 ref) public onlyManager 
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L41-L41)']
```solidity
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[144](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L144-L144)']
```solidity
144:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L137-L137)']
```solidity
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) 
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L78-L78)']
```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant 
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L97-L97)']
```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant 
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L126-L126)']
```solidity
126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant 
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L137-L137)']
```solidity
137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant 
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L149-L149)']
```solidity
149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
150:         external
151:         onlyManager
152:     
```
['[166](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L166-L166)']
```solidity
166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
167:         public
168:         onlyManager
169:     
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[293](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L293-L293)']
```solidity
293:     function getYTValue(address market, uint256 balance) public view returns (uint256) 
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L33-L33)']
```solidity
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant 
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L52)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L75-L75)']
```solidity
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant 
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L97)']
```solidity
97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant 
```
['[129](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L129-L129)']
```solidity
129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L30-L30)']
```solidity
30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager 
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L46-L46)']
```solidity
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager 
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L64-L64)']
```solidity
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L68-L68)']
```solidity
68:     function delegateIntoPreferredPool(
69:         uint128 _accountId,
70:         address collateralType,
71:         uint256 newCollateralAmountD18,
72:         uint256 leverage
73:     ) public onlyManager 
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L81-L81)']
```solidity
81:     function delegateIntoApprovedPool(
82:         uint256 poolIndex,
83:         uint128 _accountId,
84:         address collateralType,
85:         uint256 newCollateralAmountD18,
86:         uint256 leverage
87:     ) public onlyManager 
```
['[94](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L94-L94)']
```solidity
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
95:         public
96:         onlyManager
97:     
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L102-L102)']
```solidity
102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L33-L33)']
```solidity
33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant 
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L52-L52)']
```solidity
52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant
56:     
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L71-L71)']
```solidity
71:     function getData(address siloToken)
72:         public
73:         view
74:         returns (uint256 userLTV, uint256 LiquidationThreshold, bool isSolvent)
75:     
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L85-L85)']
```solidity
85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant 
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L98-L98)']
```solidity
98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) 
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L42)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner 
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L84)']
```solidity
84:     function execute(
85:         address destination,
86:         bytes calldata data,
87:         uint256 gasLimit,
88:         address executor,
89:         bytes32[] memory sigR,
90:         bytes32[] memory sigS,
91:         uint8[] memory sigV,
92:         uint256 deadline
93:     ) public 
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L58-L58)']
```solidity
58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer 
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L67-L67)']
```solidity
67:     function updateValueOracle(address _valueOracle) external onlyMaintainer 
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L27)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L122-L122)']
```solidity
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant 
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L79-L79)']
```solidity
79:     function _updateTokenInRegistry(address token, bool remove) internal 
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager 
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L91-L91)']
```solidity
91:     function _updateTokenInRegistry(address token) internal 
```
['[169](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L169-L169)']
```solidity
169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
170:         external
171:         override
172:         nonReentrant
173:     
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L204)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L71-L71)']
```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) 
```
['[253](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L253-L253)']
```solidity
253:     function _getValue(address token, address baseToken, uint256 amount) internal view returns (uint256) 
```
['[267](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L267-L267)']
```solidity
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) 
```
['[271](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L271-L271)']
```solidity
271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) 
```
['[277](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L277-L277)']
```solidity
277:     function _approveOperations(address _token, address _spender, uint256 _amount) internal virtual 
```
['[285](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L285-L285)']
```solidity
285:     function _revokeApproval(address _token, address _spender) internal virtual 
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L27)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L40-L40)']
```solidity
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L71-L71)']
```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) 
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L79-L79)']
```solidity
79:     function _updateTokenInRegistry(address token, bool remove) internal 
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L91-L91)']
```solidity
91:     function _updateTokenInRegistry(address token) internal 
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L65-L65)']
```solidity
65:     function _lzReceive(Origin calldata _origin, bytes32, bytes calldata _message, address, bytes calldata)
66:         internal
67:         override
68:     
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52)']
```solidity
52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner 
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51-L51)']
```solidity
51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) 
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33-L33)']
```solidity
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) 
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L48)']
```solidity
48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L68)']
```solidity
68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80)']
```solidity
80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency 
```
['[164](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164-L164)']
```solidity
164:     function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) 
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45)']
```solidity
45:     function addHandler(address _handler, bool state) external onlyOwner 
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L133-L133)']
```solidity
133:     function performBridgeAction(address caller, BridgeRequest calldata _request)
134:         external
135:         payable
136:         override
137:         onlyHandler
138:     
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L165)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L185-L185)']
```solidity
185:     function _setAllowance(IERC20 token, address spender, uint256 amount) internal 
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L37)']
```solidity
37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
38:         public
39:         onlyMaintainer
40:     
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L51)']
```solidity
51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
52:         external
53:         onlyMaintainer
54:     
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61)']
```solidity
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L71)']
```solidity
71:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) 
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L81)']
```solidity
81:     function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
82:         internal
83:         view
84:         returns (uint256 value)
85:     
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L66-L66)']
```solidity
66:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
67:         external
68:         onlyMaintainer
69:     
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L132-L132)']
```solidity
132:     function getTokenDecimals(address token) public view returns (uint256) 
```


</details>

## [NonCritical-12] Default address values are manually set

### Resolution 
In instances where a new variable is defined, there is no need to set it to it's default value.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L103-L103)']
```solidity
103:             address lastAdd = address(0); // <= FOUND
```
['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L23-L25)']
```solidity
23:     
25:     address public constant ETH = address(0); // <= FOUND
```


</details>

## [NonCritical-13] Contract lines should not be longer than 120 characters for readability

### Resolution 
Consider spreading these lines over multiple lines to aid in readability and the support of VIM users everywhere.

Num of instances: 94

### Findings 


<details><summary>Click to show findings</summary>

['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L92-L92)']
```solidity
92:      * @notice Mints Principal Tokens (PT) and Yield Tokens (YT) in the specified market using Standardized Yield (SY) tokens // <= FOUND
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L254-L254)']
```solidity
254:      * @dev The TVL is calculated by calculating the value of YT, LP and PT in terms of SY and then converting to the base token // <= FOUND
```
['[298](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L298-L298)']
```solidity
298:      * @notice Checks whether all positions (SY, PT, YT, and LP (in the pool and in penpie)) in a given market are empty for this contract // <= FOUND
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L54-L54)']
```solidity
54:         bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool)); // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L81-L81)']
```solidity
81:         // the value function is inside the accounting manager contract (so we can use the accounting manager address as the calculator connector) // <= FOUND
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L17-L17)']
```solidity
17:      * @param _registry The PositionRegistry contract that stores governance addresses and other configurations for vaults // <= FOUND
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L27-L27)']
```solidity
27:      * @notice Ensures the caller is the designated manager for the vault, either the keeper contract or the emergency manager // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L43-L43)']
```solidity
43:      * @dev for the connectors that borrowing is allowed, the health factor should be higher than this value (so we keep a safe margin) // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L79-L79)']
```solidity
79:      * @dev in case the caller is the accounting manager, the function will check with the watcher contract the number of tokens to withdraw // <= FOUND
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L148-L148)']
```solidity
148:      * @notice Updates the token registry to reflect the current balance of a specified token. It can add a new token to the registry or remove a token with zero balance. // <= FOUND
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L149-L149)']
```solidity
149:      * @dev This function is called to ensure the registry is accurate after liquidity is added, removed, or swaps are performed. It should reflect the current state of tokens held by this connector. // <= FOUND
```
['[166](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L166-L166)']
```solidity
166:      * @dev This function is called to add liquidity to this connector. It should be implemented in the connector contract to handle the specific liquidity adding process for the connector by overriding the _addLiquidity function (optional). // <= FOUND
```
['[187](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L187-L187)']
```solidity
187:         _addLiquidity(tokens, amounts, data); // call the specific implementation if the connector needs to do something after the liquidity is added // <= FOUND
```
['[171](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L171-L171)']
```solidity
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId)); // <= FOUND
```
['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L23-L23)']
```solidity
23:      * @notice Constructs the Keepers multisignature wallet with a set of owners and a threshold for transaction execution // <= FOUND
```
['[39](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L39-L39)']
```solidity
39:      * @param addOrRemove An array of booleans corresponding to the addresses in _owners; `true` to add, `false` to remove // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L72-L72)']
```solidity
72:      * @param data The data payload of the transaction (same as msg.data (https://github.com/safe-global/safe-smart-account/blob/2278f7ccd502878feb5cec21dd6255b82df374b5/contracts/base/Executor.sol#L24)) // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L81-L81)']
```solidity
81:      *     - Sequentially verifying each signature to confirm it's valid, from an owner, and not reused within the same transaction (guarding against replay attacks). // <= FOUND
```
['[26](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L26-L26)']
```solidity
26:     /// @dev withdrawRequestsByAddress is used to prevent users from withdrawing or transferring more than their shares, while their withdraw request are waiting for execution // <= FOUND
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L29-L29)']
```solidity
29:     /// @dev we use this variable to prevent the withdraw group from being fullfilled before the needed amount is gathered // <= FOUND
```
['[39](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L39-L39)']
```solidity
39:     /// @dev This variable is used to calculate the performance fee and prevent the strategy manager to increase the profit of the vault by depositing the profit to the vault // <= FOUND
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L42-L42)']
```solidity
42:     /// @notice profitStoredTime is the time that the profit is cached. We allow the strategy manager to get the performance fee only if the profit is cached for more than 12 hours // <= FOUND
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L44-L44)']
```solidity
44:     /// @notice lastFeeDistributionTime is the time that the last fee distribution is done. This variable is used to calculate the management fee (x% of the total assets per year) // <= FOUND
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L48-L48)']
```solidity
48:     /// @notice preformanceFeeSharesWaitingForDistribution is the total amount of shares that are waiting for distribution of the performance fee // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L49-L49)']
```solidity
49:     /// @dev we use this variable to prevent the strategy manager to get the performance fee before the lock period is passed // <= FOUND
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L66-L66)']
```solidity
66:     /// @notice managementFee is the fee that is taken for the total assets of the vault (x% of the total assets per year) // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L76-L76)']
```solidity
76:     /// @dev if isStarted is true and isFullfilled is false, it means that the withdraw group is active and we are gethering funds for these withdrawals // <= FOUND
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L78-L78)']
```solidity
78:     /// @dev if isStarted is true and isFullfilled is true, it means that the withdraw group is fullfilled and but there are still some withdraws that are waiting for execution // <= FOUND
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L88-L88)']
```solidity
88:     /// @notice depositLimitPerTransaction is the total amount of the base token that can be deposited to the vault per transaction // <= FOUND
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L91-L91)']
```solidity
91:     /// @notice valueOracle is the address of the value oracle that is used to calculate the price of the assets (used to get TVL of holding tokens) // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L133-L133)']
```solidity
133:     /// @param _performanceFeeReceiver is the address that the performance fee is sent to (this should be the NoyaFeeReceiver contract address) // <= FOUND
```
['[134](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L134-L134)']
```solidity
134:     /// @param _managementFeeReceiver is the address that the management fee is sent to(this should be another instance of NoyaFeeReceiver contract address) // <= FOUND
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L184-L184)']
```solidity
184:     /// @notice by overriding this function we can prevent users from withdrawing or transferring more than their shares, while their withdraw request are waiting for execution // <= FOUND
```
['[222](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L222-L222)']
```solidity
222:     * @notice calculateDepositShares is a function that calculates the shares of the deposits that are waiting for calculation // <= FOUND
```
['[224](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L224-L224)']
```solidity
224:     * @dev this function is used to calculate the users desposit shares that has been deposited before the oldest update time of the vault // <= FOUND
```
['[319](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L319-L319)']
```solidity
319:      * @dev This function iterates through withdrawal requests queued for calculation and assigns the corresponding amount of base tokens to each request based on the current share price. It is intended to be called by the vault manager to process queued withdrawals efficiently. // <= FOUND
```
['[320](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L320-L320)']
```solidity
320:      * @param maxIterations The maximum number of iterations the function will process to prevent gas limit issues. This allows for batch processing of withdrawal calculations. // <= FOUND
```
['[322](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L322-L322)']
```solidity
322:      * 1. Iterate through the withdrawal queue and calculate the amount of base tokens to be assigned to each withdrawal request. // <= FOUND
```
['[358](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L358-L358)']
```solidity
358:     /// @dev after starting the withdraw group, we can not start another withdraw group until the current withdraw group is fullfilled // <= FOUND
```
['[359](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L359-L359)']
```solidity
359:     /// @dev after starting the withdraw group, we can not calculate the withdraw shares until the withdraw group is fullfilled // <= FOUND
```
['[442](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L442-L442)']
```solidity
442:         // if the withdraw group is fullfilled and there are no withdraws that are waiting for execution, we delete the withdraw group // <= FOUND
```
['[450](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L450-L450)']
```solidity
450:     /// @param depositOrWithdraw is a boolean that indicates if the function is used to reset the middle index of the deposit or withdraw queue // <= FOUND
```
['[451](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L451-L451)']
```solidity
451:     /// @dev in case of a price manipulation, we can reset the middle index of the deposit or withdraw queue to prevent the users from getting more shares than they should // <= FOUND
```
['[452](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L452-L452)']
```solidity
452:     /// @dev by resetting the middle index of the deposit or withdraw queue, we force the users to wait for the calculation of their shares // <= FOUND
```
['[473](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L473-L473)']
```solidity
473:     /// @dev in this function, we calculate the profit of the vault and record it for the performance fee, if the profit is more than the total profit that is calculated // <= FOUND
```
['[474](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L474-L474)']
```solidity
474:     /// @dev we mint the shares to address(this) so after the lock period is passed, the strategy manager can get the performance fee  shares by calling the collectPerformanceFees function // <= FOUND
```
['[492](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L492-L492)']
```solidity
492:     /// @dev the access to this function is public so everyone can prevent the strategy manager from getting the performance fee  more than it should // <= FOUND
```
['[525](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L525-L525)']
```solidity
525:     /// @notice collectPerformanceFees after the lock period is passed, the strategy manager can get the performance fee shares by calling this function // <= FOUND
```
['[547](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L547-L547)']
```solidity
547:     /// @notice retrieveTokensForWithdraw the manager can call this function to get tokens from the connectors to fulfill the withdraw requests // <= FOUND
```
['[577](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L577-L577)']
```solidity
577:      * @notice Calculates the vault's current profit based on the Total Value Locked (TVL), total deposited, and withdrawn amounts // <= FOUND
```
['[590](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L590-L590)']
```solidity
590:     /// @notice by overriding the totalAssets function, we can calculate the total assets of the vault and use the 4626 standard to calculate the shares price // <= FOUND
```
['[614](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L614-L614)']
```solidity
614:     /// @notice if the withdraw group is not fullfilled, we can get the needed assets for the withdraw using this function // <= FOUND
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L28-L28)']
```solidity
28:      * @param _owner The address that will own the LZHelperReceiver contract, typically a governance or deployer address with the ability to execute administrative functions // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L35-L35)']
```solidity
35:      * @dev This function allows the contract owner to map a LayerZero chain ID to its corresponding chain information, including the native chain ID and the address of a helper contract specific to LayerZero on that chain. // <= FOUND
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L38-L38)']
```solidity
38:      * @param lzHelperAddress The address of the helper contract deployed on the chainId that interacts with LayerZero for cross-chain messaging // <= FOUND
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L47-L47)']
```solidity
47:      * @dev This function allows the contract owner to map a vault ID to its corresponding chain information, including the base chain ID and the address of the OmniChainManager contract that manages the vault on the base chain. // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L58-L58)']
```solidity
58:      * @dev Overrides the `_lzReceive` function from `OAppReceiver` to process incoming messages. It's designed to decode the received message containing TVL update information for a specific vault and then call the associated OmnichainManager to update the TVL accordingly. // <= FOUND
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L59-L59)']
```solidity
59:      * @param _origin Struct containing information about the origin chain of the message, including the LayerZero chain ID and other metadata // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L60-L60)']
```solidity
60:      * @param _message The encoded message data containing the vault ID, updated TVL value, and the timestamp of the update // <= FOUND
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L62-L62)']
```solidity
62:      * This function decodes the message and then utilizes the `OmnichainManagerBaseChain` contract associated with the specified vault to update its TVL. It ensures that messages are processed only from configured chains and vaults to maintain data integrity and security. // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L87-L87)']
```solidity
87:     * @dev If the tokens are not ETH or USD, it should support the decimals() function in IERC20Metadata interface since the logic depends on it // <= FOUND
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L113-L113)']
```solidity
113:     * @dev The Chainlink price is the price of a token based on another token(or currency) so if we need to claculate the price of the later based on the first, we should put isInverse to true // <= FOUND
```
['[114](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L114-L114)']
```solidity
114:         uint256 lpAmount = LPStaking.userInfo(poolId, address(this)).amount + IERC20(lpAddress).balanceOf(address(this)); // <= FOUND
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L32-L32)']
```solidity
32:      * @dev Allows the owner to configure how messages are sent through LayerZero, adjusting parameters like gas limits or message fees. // <= FOUND
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L33-L33)']
```solidity
33:      * @param _messageSetting The new message settings to be used for LayerZero sends (see https://docs.layerzero.network/contracts/options) // <= FOUND
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L45-L45)']
```solidity
45:      * @dev Stores LayerZero-specific identifiers and helper contract addresses for cross-chain communication to a specified chain. // <= FOUND
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L57-L57)']
```solidity
57:      * @dev Maps a vault ID to its corresponding base chain ID and omnichain manager contract, setting up the infrastructure for cross-chain TVL updates. // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L68-L68)']
```solidity
68:      * @dev Constructs and sends a message containing the vault ID, new TVL, and the time of the update through LayerZero. This function can only be called by the vault's omnichain manager. // <= FOUND
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L80-L80)']
```solidity
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here // <= FOUND
```
['[104](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L104-L104)']
```solidity
104:     * @dev adds one dummy holding position to the vault so it can be used as a placeholder at index 0 of the holdingPositions array // <= FOUND
```
['[135](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L135-L135)']
```solidity
135:         // Enable the accounting manager connector so the vault can use the "getValue" function of the accounting manager for calculating the value of tokens // <= FOUND
```
['[284](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L284-L284)']
```solidity
284:     * @dev This function is used to update the information of an holding position (holding position is a position that the connector is holding) // <= FOUND
```
['[329](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L329-L329)']
```solidity
329:     * @dev This function is used to update the information of an holding position (holding position is a position that the connector is holding)  // <= FOUND
```
['[288](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L288-L288)']
```solidity
288:     * @param d data is the information that represents the position (e.g. the address of the pool in curve connector, the address of the pool in uniswap connector, etc.) // <= FOUND
```
['[291](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L291-L291)']
```solidity
291:     * @param holdingPositionId The id of the holding position (calculated using the positionId, the connector and the data) // <= FOUND
```
['[369](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L369-L369)']
```solidity
369:     /// @dev in scenarios where the positionTimestamp is not the current time (e.g. when we have positions on other chains) // <= FOUND
```
['[16](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L16-L16)']
```solidity
16:      * @return The current TVL calculated using the TVLHelper utility, which aggregates the value of assets managed by the vault on this chain. // <= FOUND
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L24-L24)']
```solidity
24:      * Triggers an update of the vault's TVL information, sending the latest data to the base chain via the LZHelperSender contract. // <= FOUND
```
['[25](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L25-L25)']
```solidity
25:      * This function is restricted to be called by managers only, ensuring that TVL updates are controlled and authorized. // <= FOUND
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L27-L27)']
```solidity
27:      * @dev This function is called by the LayerZero helper to adjust the TVL in response to changes detected on other chains. It's critical for maintaining an accurate and up-to-date reflection of the assets managed across the entire ecosystem. // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L46-L46)']
```solidity
46:      * @dev Overrides the `_getPositionTVL` function from `OmnichainLogic` to provide specific logic for interpreting TVL data related to omnichain positions on the base chain. // <= FOUND
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L48-L48)']
```solidity
48:      * @return The TVL associated with the specified omnichain position, derived from additional data stored in the position. // <= FOUND
```
['[39](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L39-L39)']
```solidity
39:     /// @dev in case we have a position that we can't fetch the latest update at the moment, we get the oldest update time of all of them to avoid any issues with the TVL // <= FOUND
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L8-L8)']
```solidity
8:  * @notice OmnichainLogic is a base contract for OmnichainManagerBaseChain and OmnichainManagerNormalChain, which are used to manage cross-chain communication and transactions. // <= FOUND
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L10-L10)']
```solidity
10:  *     - Mapping Addresses for Cross-Chain Bridges: At its core, the contract uses something called destChainAddress mapping. This is essentially a way to keep track of where assets should be sent across different blockchain networks. It's a crucial part of making sure that when assets are bridged, they end up exactly where they're supposed to, maintaining accuracy across a complex web of chains. // <= FOUND
```
['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L12-L12)']
```solidity
12:  *     - A Two-Step Approval for Transactions: Before any asset can make the jump to another chain, the contract requires each transaction to be approved not once, but twice. First, someone needs to give the green light indicating that the transaction is okay (that's where updateBridgeTransactionApproval comes into play). Then, and only then, can the actual transaction process begin (startBridgeTransaction). This double-check adds an extra layer of security, ensuring every transaction is intended and verified. // <= FOUND
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L29-L29)']
```solidity
29:      * @notice Initializes the OmnichainLogic contract with the address of the LayerZero helper contract and base connector parameters // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L30-L30)']
```solidity
30:      * @param _lzHelper Address of the LayerZero helper contract responsible for managing cross-chain communication (in OmnichainManagerNormalChain this is LZHelperSender and in OmnichainManagerBaseChain this is LZHelperReceiver) // <= FOUND
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L41-L41)']
```solidity
41:      * @dev This function allows the maintainer to set or update the destination address for each supported chain, facilitating targeted cross-chain transactions. // <= FOUND
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L53-L53)']
```solidity
53:      * @dev This toggles the approval state of a bridge transaction identified by its hash. If previously unapproved or expired, it approves it; if already approved, it revokes approval. // <= FOUND
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L64-L64)']
```solidity
64:      * @dev Validates the bridge request against approvals and destination chain information before executing the bridge transaction via the `GenericSwapAndBridgeHandler`. // <= FOUND
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L65-L65)']
```solidity
65:      * @param bridgeRequest A struct containing details of the bridge transaction, including source and destination chain IDs, addresses, and token information // <= FOUND
```
['[115](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L115-L115)']
```solidity
115:      * @notice The ```_getHealthFactor``` function returns the current health factor of a respective position given an exchange rate // <= FOUND
```
['[114](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L114-L114)']
```solidity
114:         borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this)); // <= FOUND
```


</details>

## [NonCritical-14] Avoid updating storage when the value hasn't changed

### Resolution 
In Solidity, manipulating contract storage comes with significant gas costs. One can optimize gas usage by preventing unnecessary storage updates when the new value is the same as the existing one. If an existing value is the same as the new one, not reassigning it to the storage could potentially save substantial amounts of gas, notably 2900 gas for a 'Gsreset'. This saving may come at the expense of a cold storage load operation ('Gcoldsload'), which costs 2100 gas, or a warm storage access operation ('Gwarmaccess'), which costs 100 gas. Therefore, the gas efficiency of your contract can be significantly improved by adding a check that compares the new value with the current one before any storage update operation. If the values are the same, you can bypass the storage operation, thereby saving gas.

Num of instances: 8

### Findings 


<details><summary>Click to show findings</summary>

['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L63-L63)']
```solidity
63:     function setThreshold(uint8 _threshold) public onlyOwner {
64:         require(_threshold <= numOwners && _threshold > 1);
65:         threshold = _threshold;
66:         emit UpdateThreshold(_threshold);
67:     }
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L79-L79)']
```solidity
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) {
80:         require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);
81:         maxNumHoldingPositions = _maxNumHoldingPositions;
82:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) {
85:         emit updateFlashloanAddress(_flashLoan, flashLoan);
86:         flashLoan = _flashLoan;
87:     }
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L42)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
43:         uint256 numOwnersTemp = numOwners;
44:         for (uint256 i = 0; i < _owners.length; i++) {
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) {
46:                 isOwner[_owners[i]] = true;
47:                 numOwnersTemp++;
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
49:                 isOwner[_owners[i]] = false;
50:                 numOwnersTemp--;
51:             }
52:         }
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
54:         numOwners = numOwnersTemp;
55:         emit UpdateOwners(_owners, addOrRemove);
56:     }
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36)']
```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
37:         messageSetting = _messageSetting;
38:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L40-L40)']
```solidity
40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant {
41:         masterchef.updateLiquidity(tokenId);
42:         _updateTokenInRegistry(masterchef.CAKE());
43:         emit UpdatePosition(tokenId);
44:     }
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager {
154:         _updateTokenInRegistry(token);
155:     }
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28)']
```solidity
28:     function updateTVLInfo() external onlyManager {
29:         uint256 tvl = getTVL();
30:         LZHelperSender(lzHelper).updateTVL(vaultId, tvl, block.timestamp);
31:     }
```


</details>

## [NonCritical-15] Specific imports should be used where possible so only used code is imported

### Resolution 
In many cases only some functionality is used from an import. In such cases it makes more sense to use {} to specify what to import and thus save gas whilst improving readability

Num of instances: 71

### Findings 


<details><summary>Click to show findings</summary>

['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L8-L8)']
```solidity
8: import "@openzeppelin/contracts-5.0/utils/ReentrancyGuard.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L6-L6)']
```solidity
6: import "../interface/Accounting/IAccountingManager.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L8-L8)']
```solidity
8: import "../helpers/TVLHelper.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/access/AccessControl.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L6-L6)']
```solidity
6: import "../interface/IPositionRegistry.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L4-L4)']
```solidity
4: import "../helpers/BaseConnector.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Aerodrome/IPool.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L6-L6)']
```solidity
6: import "../external/interfaces/Aerodrome/IRouter.sol";
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L7-L7)']
```solidity
7: import "../external/interfaces/Aerodrome/IVoter.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L8-L8)']
```solidity
8: import "../external/interfaces/Aerodrome/IGauge.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Balancer/IBalancerVault.sol";
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L10-L10)']
```solidity
10: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L7-L7)']
```solidity
7: import "../external/interfaces/Camelot/ICamelotRouter.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L8-L8)']
```solidity
8: import "../external/interfaces/Camelot/ICamelotFactory.sol";
```
['[9](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L9-L9)']
```solidity
9: import "../external/interfaces/Camelot/ICamelotPair.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Curve/IRewardsGauge.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L6-L6)']
```solidity
6: import "../external/interfaces/Convex/IConvexBasicRewards.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Dolomite/IDepositWithdrawalProxy.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L6-L6)']
```solidity
6: import "../external/interfaces/Dolomite/IBorrowPositionProxyV1.sol";
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L7-L7)']
```solidity
7: import "../external/interfaces/Dolomite/IDolomiteMargin.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Frax/IFraxPair.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Gearbox/ICreditManagerV3.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L6-L6)']
```solidity
6: import "../external/interfaces/Gearbox/ICreditFacadeV3.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L4-L4)']
```solidity
4: import "../external/interfaces/Lido/ILidoWithdrawal.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Maverick/IMaverickRouter.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Morpho/IMorpho.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L6-L6)']
```solidity
6: import "../external/libraries/Morpho/SharesMathLib.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L4-L4)']
```solidity
4: import "./UNIv3Connector.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Pancakeswap/IMasterChefV3.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L6-L6)']
```solidity
6: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L5-L5)']
```solidity
5: import "../external/libraries/Pendle/PendleLpOracleLib.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L8-L8)']
```solidity
8: import "../external/interfaces/Pendle/IPendleRouter.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/SNXV3/IV3CoreProxy.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Silo/ISilo.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L6-L6)']
```solidity
6: import "../external/libraries/Silo/SolvencyV2.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/Stargate/IStargateRouter.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L4-L4)']
```solidity
4: import "../external/interfaces/UNIv3/INonfungiblePositionManager.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L5-L5)']
```solidity
5: import "../external/interfaces/UNIv3/IUniswapV3Factory.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/utils/cryptography/EIP712.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L6-L6)']
```solidity
6: import "@openzeppelin/contracts-5.0/utils/cryptography/ECDSA.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/TimeLock.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/governance/TimelockController.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Watchers.sol#L4-L4)']
```solidity
4: import "./Keepers.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L4-L4)']
```solidity
4: import "../interface/IConnector.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L8-L8)']
```solidity
8: import "@openzeppelin/contracts-5.0/token/ERC721/utils/ERC721Holder.sol";
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L10-L10)']
```solidity
10: import "../interface/valueOracle/INoyaValueOracle.sol";
```
['[11](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L11-L11)']
```solidity
11: import "../governance/Watchers.sol";
```
['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L12-L12)']
```solidity
12: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721Receiver.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L5-L5)']
```solidity
5: import "../OmniChainHandler/OmnichainManagerBaseChain.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L6-L6)']
```solidity
6: import "@layerzerolabs/lz-evm-oapp-v2/contracts/oapp/OApp.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L5-L5)']
```solidity
5: import "../OmniChainHandler/OmnichainManagerNormalChain.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L4-L4)']
```solidity
4: import "../../helpers/SwapHandler/GenericSwapAndBridgeHandler.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L5-L5)']
```solidity
5: import "../BaseConnector.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L6-L6)']
```solidity
6: import "./OmnichainLogic.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L5-L5)']
```solidity
5: import "../../interface/IConnector.sol";
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L7-L7)']
```solidity
7: import "../TVLHelper.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L8-L8)']
```solidity
8: import "../LZHelpers/LZHelperSender.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L5-L5)']
```solidity
5: import "../../interface/valueOracle/INoyaValueOracle.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L5-L5)']
```solidity
5: import "../../governance/NoyaGovernanceBase.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L6-L6)']
```solidity
6: import "../../interface/SwapHandler/ISwapAndBridgeHandler.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L6-L6)']
```solidity
6: import "../../../interface/SwapHandler/ISwapAndBridgeHandler.sol";
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L7-L7)']
```solidity
7: import "../../../interface/ITokenTransferCallBack.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L6-L6)']
```solidity
6: import "../../accountingManager/Registry.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L4-L4)']
```solidity
4: import "../../../interface/valueOracle/INoyaValueOracle.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L5-L5)']
```solidity
5: import "../../../interface/valueOracle/AggregatorV3Interface.sol";
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L6-L6)']
```solidity
6: import "../../../accountingManager/Registry.sol";
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8-L8)']
```solidity
8: import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol";
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L4-L4)']
```solidity
4: import "@uniswap/v3-core/contracts/interfaces/IUniswapV3Factory.sol";
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L5-L5)']
```solidity
5: import "../../../external/libraries/uniswap/OracleLibrary.sol";
```


</details>

## [NonCritical-16] Explicitly define visibility of state variables to prevent misconceptions on what can access the variable

### Resolution 
Such state variables should be marked as private as this is the default visibility

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L23-L23)']
```solidity
23:     bytes messageSetting; // <= FOUND
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L17-L17)']
```solidity
17:     address caller; // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L30-L30)']
```solidity
30:     address mav; // <= FOUND
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L31-L31)']
```solidity
31:     address veMav; // <= FOUND
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L32-L32)']
```solidity
32:     address maverickRouter; // <= FOUND
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L24-L24)']
```solidity
24:     address rewardToken; // <= FOUND
```


</details>

## [NonCritical-17] Contracts should have all public/external functions exposed by interfaces

### Resolution 
Contracts should expose all public and external functions through interfaces. This practice ensures a clear and consistent definition of how the contract can be interacted with, promoting better transparency and integration.

Num of instances: 231

### Findings 


<details><summary>Click to show findings</summary>

['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L149-L149)']
```solidity
149:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
150:         external
151:         returns (uint256)
152:     
```
['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L23-L23)']
```solidity
23:     function withdrawShares(uint256 amount) external onlyOwner 
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L27-L27)']
```solidity
27:     function burnShares(uint256 amount) external onlyOwner 
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L79-L79)']
```solidity
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) 
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L84)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) 
```
['[105](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L105-L105)']
```solidity
105:     function addVault(
106:         uint256 vaultId,
107:         address _accountingManager,
108:         address _baseToken,
109:         address _governer,
110:         address _maintainer,
111:         address _maintainerWithoutTimelock,
112:         address _keeperContract,
113:         address _watcher,
114:         address _emergency,
115:         address[] calldata _trustedTokens
116:     ) external onlyRole(MAINTAINER_ROLE) 
```
['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L156-L156)']
```solidity
156:     function changeVaultAddresses(
157:         uint256 vaultId,
158:         address _governer,
159:         address _maintainer,
160:         address _maintainerWithoutTimelock,
161:         address _keeperContract,
162:         address _watcher,
163:         address _emergency
164:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) 
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L185-L185)']
```solidity
185:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
186:         external
187:         onlyVaultMaintainer(vaultId)
188:         vaultExists(vaultId)
189:     
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L203-L203)']
```solidity
203:     function updateConnectorTrustedTokens(
204:         uint256 vaultId,
205:         address _connectorAddress,
206:         address[] calldata _tokens,
207:         bool trusted
208:     ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) 
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L232-L232)']
```solidity
232:     function addTrustedPosition(
233:         uint256 vaultId,
234:         uint256 _positionTypeId,
235:         address calculatorConnector,
236:         bool onlyOwner,
237:         bool _isDebt,
238:         bytes calldata _data,
239:         bytes calldata _additionalData
240:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant 
```
['[260](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L260-L260)']
```solidity
260:     function removeTrustedPosition(uint256 vaultId, bytes32 _positionId)
261:         external
262:         onlyVaultMaintainer(vaultId)
263:         vaultExists(vaultId)
264:     
```
['[362](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L362-L362)']
```solidity
362:     function updateHoldingPostionWithTime(
363:         uint256 vaultId,
364:         bytes32 _positionId,
365:         bytes calldata _data,
366:         bytes calldata additionalData,
367:         bool removePosition,
368:         uint256 positionTimestamp
369:     ) external vaultExists(vaultId) 
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L45-L45)']
```solidity
45:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant 
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L61-L61)']
```solidity
61:     function borrow(uint256 _amount, uint256 _interestRateMode, address _borrowAsset)
62:         external
63:         onlyManager
64:         nonReentrant
65:     
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L80-L80)']
```solidity
80:     function repay(address asset, uint256 amount, uint256 i) external onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L87-L87)']
```solidity
87:     function repayWithCollateral(uint256 _amount, uint256 i, address _borrowAsset) external onlyManager 
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L99-L99)']
```solidity
99:     function withdrawCollateral(uint256 _collateralAmount, address _collateral) external onlyManager nonReentrant 
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L37-L37)']
```solidity
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
38:         external
39:         nonReentrant
40:     
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L43-L43)']
```solidity
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant 
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L64-L64)']
```solidity
64:     function removeLiquidityFromCamelotPool(CamelotRemoveLiquidityParams calldata p)
65:         external
66:         onlyManager
67:         nonReentrant
68:     
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L29-L29)']
```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant 
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L48-L48)']
```solidity
48:     function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant 
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L63-L63)']
```solidity
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant 
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L38-L38)']
```solidity
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant
42:     
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L36-L36)']
```solidity
36:     function deposit(uint256 amountIn) external onlyManager nonReentrant 
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L63-L63)']
```solidity
63:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant 
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L76-L76)']
```solidity
76:     function unstake(uint256 lockupId) external onlyManager nonReentrant 
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L88-L88)']
```solidity
88:     function addLiquidityInMaverickPool(MavericAddLiquidityParams calldata p) external onlyManager nonReentrant 
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L111-L111)']
```solidity
111:     function removeLiquidityFromMaverickPool(MavericRemoveLiquidityParams calldata p)
112:         external
113:         onlyManager
114:         nonReentrant
115:     
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L132-L132)']
```solidity
132:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant 
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L35-L35)']
```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant 
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L58-L58)']
```solidity
58:     function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant 
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L80-L80)']
```solidity
80:     function borrow(uint256 amount, Id id) external onlyManager nonReentrant 
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L31-L31)']
```solidity
31:     function sendPositionToMasterChef(uint256 tokenId) external onlyManager nonReentrant 
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L78-L78)']
```solidity
78:     function supply(address market, uint256 amount) external onlyManager nonReentrant 
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L97-L97)']
```solidity
97:     function mintPTAndYT(address market, uint256 syAmount) external onlyManager nonReentrant 
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L112-L112)']
```solidity
112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant 
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L149-L149)']
```solidity
149:     function swapYTForPT(address market, uint256 exactYTIn, uint256 min, ApproxParams memory guess)
150:         external
151:         onlyManager
152:     
```
['[183](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L183-L183)']
```solidity
183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant
187:     
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L203-L203)']
```solidity
203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant 
```
['[216](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L216-L216)']
```solidity
216:     function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant 
```
['[241](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L241-L241)']
```solidity
241:     function claimRewards(IPMarket market) external onlyManager nonReentrant 
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L33-L33)']
```solidity
33:     function deposit(address siloToken, address dToken, uint256 amount, bool oC) external onlyManager nonReentrant 
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L52-L52)']
```solidity
52:     function withdraw(address siloToken, address wToken, uint256 amount, bool oC, bool closePosition)
53:         external
54:         onlyManager
55:         nonReentrant
56:     
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L85-L85)']
```solidity
85:     function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant 
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L98-L98)']
```solidity
98:     function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant 
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L49-L49)']
```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant 
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L76-L76)']
```solidity
76:     function withdrawFromStargatePool(StargateRequest calldata withdrawRequest) external onlyManager nonReentrant 
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L103-L103)']
```solidity
103:     function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant 
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L40-L40)']
```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) 
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L63-L63)']
```solidity
63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L87-L87)']
```solidity
87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant 
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Watchers.sol#L8-L8)']
```solidity
8:     function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view 
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L45-L45)']
```solidity
45:     function updateMinimumHealthFactor(uint256 _minimumHealthFactor) external onlyMaintainer 
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L58-L58)']
```solidity
58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer 
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L67-L67)']
```solidity
67:     function updateValueOracle(address _valueOracle) external onlyMaintainer 
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L27)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L122-L122)']
```solidity
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens,
124:         uint256[] memory amounts,
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant 
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L204)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant 
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L27-L27)']
```solidity
27:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
28:         external
29:         returns (uint256)
30:     
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L40-L40)']
```solidity
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external 
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L51-L51)']
```solidity
51:     function updatePositionToRegistryUsingType(bytes32 _positionId, bytes memory data, bool remove) external 
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L59-L59)']
```solidity
59:     function addPositionToRegistryUsingType(uint256 _positionType, bytes memory data) external 
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L65-L65)']
```solidity
65:     function addPositionToRegistry(bytes memory data) external 
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L46-L46)']
```solidity
46:     function updateChainInfo(uint256 chainId, address destinationAddress) external onlyMaintainer 
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L32-L32)']
```solidity
32:     function updateTVL(uint256 chainId, uint256 tvl, uint256 updateTime) external nonReentrant 
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28)']
```solidity
28:     function updateTVLInfo() external onlyManager 
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L48)']
```solidity
48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency 
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L57)']
```solidity
57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L68)']
```solidity
68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
69:         external
70:         onlyMaintainerOrEmergency
71:     
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80-L80)']
```solidity
80:     function addEligibleUser(address _user) external onlyMaintainerOrEmergency 
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L90)']
```solidity
90:     function executeSwap(SwapRequest memory _swapRequest)
91:         external
92:         payable
93:         onlyEligibleUser
94:         onlyExistingRoute(_swapRequest.routeId)
95:         nonReentrant
96:         returns (uint256 _amountOut)
97:     
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L126)']
```solidity
126:     function executeBridge(BridgeRequest calldata _bridgeRequest)
127:         external
128:         payable
129:         onlyEligibleUser
130:         onlyExistingRoute(_bridgeRequest.routeId)
131:         nonReentrant
132:     
```
['[158](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L158-L158)']
```solidity
158:     function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency 
```
['[164](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L164-L164)']
```solidity
164:     function verifyRoute(uint256 _routeId, address addr) external view onlyExistingRoute(_routeId) 
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L45)']
```solidity
45:     function addHandler(address _handler, bool state) external onlyOwner 
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L55-L55)']
```solidity
55:     function addChain(uint256 _chainId, bool state) external onlyOwner 
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L65-L65)']
```solidity
65:     function addBridgeBlacklist(string memory bridgeName, bool state) external onlyOwner 
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L193-L193)']
```solidity
193:     function rescueFunds(address token, address userAddress, uint256 amount) external onlyOwner 
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L51)']
```solidity
51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
52:         external
53:         onlyMaintainer
54:     
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61)']
```solidity
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer 
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L53-L53)']
```solidity
53:     function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer 
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L66-L66)']
```solidity
66:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
67:         external
68:         onlyMaintainer
69:     
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L38)']
```solidity
38:     function setPeriod(uint32 _period) external onlyMaintainer 
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48)']
```solidity
48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer 
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L5-L5)']
```solidity
5:     function latestRoundData()
6:         external
7:         view
8:         returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)
9:     
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L123-L123)']
```solidity
123:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer 
```
['[134](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L134-L134)']
```solidity
134:     function setFeeReceivers(
135:         address _withdrawFeeReceiver,
136:         address _performanceFeeReceiver,
137:         address _managementFeeReceiver
138:     ) public onlyMaintainer 
```
['[169](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L169-L169)']
```solidity
169:     function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer 
```
['[198](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L198-L198)']
```solidity
198:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused 
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L223-L223)']
```solidity
223:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused 
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L254)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     
```
['[301](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L301-L301)']
```solidity
301:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused 
```
['[325](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L325-L325)']
```solidity
325:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused 
```
['[357](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L357-L357)']
```solidity
357:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused 
```
['[367](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L367-L367)']
```solidity
367:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused 
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L393)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused 
```
['[450](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L450-L450)']
```solidity
450:     function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager 
```
['[472](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L472-L472)']
```solidity
472:     function recordProfitForFee() public onlyManager nonReentrant 
```
['[490](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L490-L490)']
```solidity
490:     function checkIfTVLHasDroped() public nonReentrant 
```
['[502](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L502-L502)']
```solidity
502:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) 
```
['[523](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L523-L523)']
```solidity
523:     function collectPerformanceFees() public onlyManager nonReentrant 
```
['[540](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L540-L540)']
```solidity
540:     function burnShares(uint256 amount) public 
```
['[545](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L545-L545)']
```solidity
545:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant 
```
['[579](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L579-L579)']
```solidity
579:     function getProfit() public view returns (uint256) 
```
['[593](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L593-L593)']
```solidity
593:     function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
594:         public
595:         view
596:         returns (DepositRequest[] memory depositData, WithdrawRequest[] memory withdrawData)
597:     
```
['[613](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L613-L613)']
```solidity
613:     function neededAssetsForWithdraw() public view returns (uint256) 
```
['[624](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L624-L624)']
```solidity
624:     function TVL() public view returns (uint256) 
```
['[629](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L629-L629)']
```solidity
629:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) 
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L75-L75)']
```solidity
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) 
```
['[656](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L656-L656)']
```solidity
656:     function emergencyStop() public whenNotPaused onlyEmergency 
```
['[660](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L660-L660)']
```solidity
660:     function unpause() public whenPaused onlyEmergency 
```
['[664](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L664-L664)']
```solidity
664:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer 
```
['[670](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L670-L670)']
```solidity
670:     function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer 
```
['[675](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L675-L675)']
```solidity
675:     function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer 
```
['[680](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L680-L680)']
```solidity
680:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant 
```
['[219](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L219-L219)']
```solidity
219:     function getPositionBP(uint256 vaultId, bytes32 _positionId) public view returns (PositionBP memory) 
```
['[327](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L327-L327)']
```solidity
327:     function updateHoldingPosition(
328:         uint256 vaultId,
329:         bytes32 _positionId,
330:         bytes calldata _data,
331:         bytes calldata additionalData,
332:         bool removePosition
333:     ) public vaultExists(vaultId) returns (uint256) 
```
['[385](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L385-L385)']
```solidity
385:     function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
386:         public
387:         view
388:         returns (uint256)
389:     
```
['[399](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L399-L399)']
```solidity
399:     function getHoldingPosition(uint256 vaultId, uint256 i) public view returns (HoldingPI memory) 
```
['[407](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L407-L407)']
```solidity
407:     function getHoldingPositions(uint256 vaultId) public view returns (HoldingPI[] memory) 
```
['[417](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L417-L417)']
```solidity
417:     function isPositionTrusted(uint256 vaultId, bytes32 _positionId) public view returns (bool) 
```
['[427](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L427-L427)']
```solidity
427:     function isPositionTrustedForConnector(uint256 vaultId, bytes32 _positionId, address connector)
428:         public
429:         view
430:         returns (bool)
431:     
```
['[440](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L440-L440)']
```solidity
440:     function getGovernanceAddresses(uint256 vaultId)
441:         public
442:         view
443:         returns (address, address, address, address, address, address)
444:     
```
['[461](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L461-L461)']
```solidity
461:     function isTokenTrusted(uint256 vaultId, address token, address connector) public view returns (bool) 
```
['[477](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L477-L477)']
```solidity
477:     function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)
478:         public
479:         pure
480:         returns (bytes32)
481:     
```
['[490](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L490-L490)']
```solidity
490:     function isAnActiveConnector(uint256 vaultId, address connectorAddress) public view returns (bool) 
```
['[499](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L499-L499)']
```solidity
499:     function isPositionDebt(uint256 vaultId, bytes32 _positionId) public view returns (bool) 
```
['[507](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L507-L507)']
```solidity
507:     function getVaultAddresses(uint256 vaultId) public view returns (address, address) 
```
['[516](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L516-L516)']
```solidity
516:     function isAddressTrusted(uint256 vaultId, address addr) public view returns (bool) 
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L53-L53)']
```solidity
53:     function supply(DepositData memory data) public onlyManager nonReentrant 
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L79-L79)']
```solidity
79:     function withdraw(WithdrawData memory data) public onlyManager nonReentrant 
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L100-L100)']
```solidity
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant 
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L106-L106)']
```solidity
106:     function unstake(address pool, uint256 liquidity) public onlyManager nonReentrant 
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L111-L111)']
```solidity
111:     function claim(address pool) public onlyManager nonReentrant 
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L53-L53)']
```solidity
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant 
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L64-L64)']
```solidity
64:     function openPosition(
65:         bytes32 poolId,
66:         uint256[] memory amounts,
67:         uint256[] memory amountsWithoutBPT,
68:         uint256 minBPT,
69:         uint256 auraAmount
70:     ) public onlyManager nonReentrant 
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L109-L109)']
```solidity
109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant 
```
['[115](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L115-L115)']
```solidity
115:     function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant 
```
['[175](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L175-L175)']
```solidity
175:     function totalLpBalanceOf(PoolInfo memory pool) public view returns (uint256) 
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L184-L184)']
```solidity
184:     function totalLpBalanceOf(bytes32 poolId) public view returns (uint256) 
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L74-L74)']
```solidity
74:     function getAccountHealthFactor(IComet comet) public view returns (uint256) 
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L84-L84)']
```solidity
84:     function getBorrowBalanceInBase(IComet comet) public view returns (uint256 borrowBalanceInVirtualBase) 
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L95-L95)']
```solidity
95:     function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) 
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L141-L141)']
```solidity
141:     function isInAsset(uint16 assetsIn, uint8 assetOffset) public pure returns (bool) 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L68-L68)']
```solidity
68:     function depositIntoGauge(address pool, uint256 amount) public onlyManager nonReentrant 
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L81-L81)']
```solidity
81:     function depositIntoPrisma(address pool, uint256 amount, bool curveOrConvex) public onlyManager nonReentrant 
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L103-L103)']
```solidity
103:     function depositIntoConvexBooster(address pool, uint256 pid, uint256 amount, bool stake) public onlyManager 
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L117-L117)']
```solidity
117:     function openCurvePosition(address pool, uint256 depositIndex, uint256 amount, uint256 minAmount)
118:         public
119:         onlyManager
120:         nonReentrant
121:     
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L160-L160)']
```solidity
160:     function decreaseCurvePosition(address pool, uint256 withdrawIndex, uint256 amount, uint256 minAmount)
161:         public
162:         onlyManager
163:         nonReentrant
164:     
```
['[182](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L182-L182)']
```solidity
182:     function withdrawFromConvexBooster(uint256 pid, uint256 amount) public onlyManager 
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L192-L192)']
```solidity
192:     function withdrawFromConvexRewardPool(address pool, uint256 amount) public onlyManager 
```
['[202](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L202-L202)']
```solidity
202:     function withdrawFromGauge(address pool, uint256 amount) public onlyManager 
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L212-L212)']
```solidity
212:     function withdrawFromPrisma(address depostiToken, uint256 amount) public onlyManager 
```
['[221](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L221-L221)']
```solidity
221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant 
```
['[233](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L233-L233)']
```solidity
233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant 
```
['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L247-L247)']
```solidity
247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant 
```
['[279](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L279-L279)']
```solidity
279:     function LPToUnder(PoolInfo memory info, uint256 balance) public view returns (uint256, address) 
```
['[297](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L297-L297)']
```solidity
297:     function estimateWithdrawAmount(ICurveSwap curvePool, uint256 amount, uint256 index)
298:         public
299:         view
300:         returns (uint256)
301:     
```
['[311](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L311-L311)']
```solidity
311:     function totalLpBalanceOf(PoolInfo memory info) public view returns (uint256) 
```
['[325](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L325-L325)']
```solidity
325:     function balanceOfConvexRewardPool(PoolInfo memory info) public view returns (uint256) 
```
['[335](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L335-L335)']
```solidity
335:     function balanceOfLPToken(PoolInfo memory info) public view returns (uint256) 
```
['[344](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L344-L344)']
```solidity
344:     function balanceOfRewardPool(PoolInfo memory info) public view returns (uint256) 
```
['[354](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L354-L354)']
```solidity
354:     function balanceOfPrisma(address prismaPool) public view returns (uint256) 
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L30-L30)']
```solidity
30:     function deposit(uint256 marketId, uint256 _amount) public onlyManager nonReentrant 
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L43-L43)']
```solidity
43:     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant 
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L58-L58)']
```solidity
58:     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
59:         public
60:         onlyManager
61:         nonReentrant
62:     
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L77-L77)']
```solidity
77:     function transferBetweenAccounts(uint256 accountId, uint256 marketId, uint256 _amountWei, bool borrowOrRepay)
78:         public
79:         onlyManager
80:         nonReentrant
81:     
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L98-L98)']
```solidity
98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L68-L68)']
```solidity
68:     function withdraw(IFraxPair pool, uint256 withdrawAmount) public onlyManager nonReentrant 
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L87-L87)']
```solidity
87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant 
```
['[104](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L104-L104)']
```solidity
104:     function verifyHealthFactor(IFraxPair pool) public view 
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L24-L24)']
```solidity
24:     function openAccount(address facade, uint256 ref) public onlyManager 
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L41-L41)']
```solidity
41:     function closeAccount(address facade, address creditAccount) public onlyManager nonReentrant 
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L62)']
```solidity
62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant 
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L50-L50)']
```solidity
50:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L68-L68)']
```solidity
68:     function claimWithdrawal(uint256 requestId) public onlyManager nonReentrant 
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L95-L95)']
```solidity
95:     function repay(uint256 amount, Id id) public onlyManager nonReentrant 
```
['[108](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L108-L108)']
```solidity
108:     function getHealthFactor(Id _id, Market memory _market) public view returns (uint256) 
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L137-L137)']
```solidity
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) 
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L40-L40)']
```solidity
40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant 
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L50-L50)']
```solidity
50:     function withdraw(uint256 tokenId) public onlyManager nonReentrant 
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L126-L126)']
```solidity
126:     function depositIntoPenpie(address _market, uint256 _amount) public onlyManager nonReentrant 
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L137-L137)']
```solidity
137:     function withdrawFromPenpie(address _market, uint256 _amount) public onlyManager nonReentrant 
```
['[166](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L166-L166)']
```solidity
166:     function swapYTForSY(address market, uint256 exactYTIn, uint256 min, LimitOrderData memory orderData)
167:         public
168:         onlyManager
169:     
```
['[293](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L293-L293)']
```solidity
293:     function getYTValue(address market, uint256 balance) public view returns (uint256) 
```
['[303](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L303-L303)']
```solidity
303:     function isMarketEmpty(IPMarket market) public view returns (bool) 
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L33-L33)']
```solidity
33:     function approveZap(IStakeNTroveZap zap, address tm, bool approve) public onlyManager nonReentrant 
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L52)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L75-L75)']
```solidity
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant 
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L97-L97)']
```solidity
97:     function adjustTrove(
98:         IStakeNTroveZap zapContract,
99:         address tm,
100:         uint256 mFee,
101:         uint256 wAmount,
102:         uint256 bAmount,
103:         bool isBorrowing
104:     ) public onlyManager nonReentrant 
```
['[129](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L129-L129)']
```solidity
129:     function closeTrove(IStakeNTroveZap zapContract, address troveManager) public onlyManager nonReentrant 
```
['[25](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L25-L25)']
```solidity
25:     function createAccount() public onlyManager 
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L30-L30)']
```solidity
30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager 
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L46-L46)']
```solidity
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L68-L68)']
```solidity
68:     function delegateIntoPreferredPool(
69:         uint128 _accountId,
70:         address collateralType,
71:         uint256 newCollateralAmountD18,
72:         uint256 leverage
73:     ) public onlyManager 
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L81-L81)']
```solidity
81:     function delegateIntoApprovedPool(
82:         uint256 poolIndex,
83:         uint128 _accountId,
84:         address collateralType,
85:         uint256 newCollateralAmountD18,
86:         uint256 leverage
87:     ) public onlyManager 
```
['[94](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L94-L94)']
```solidity
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor)
95:         public
96:         onlyManager
97:     
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L102-L102)']
```solidity
102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId,
105:         uint128 poolId,
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L71-L71)']
```solidity
71:     function getData(address siloToken)
72:         public
73:         view
74:         returns (uint256 userLTV, uint256 LiquidationThreshold, bool isSolvent)
75:     
```
['[130](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L130-L130)']
```solidity
130:     function isSiloEmpty(ISilo silo) public view returns (bool) 
```
['[101](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L101-L101)']
```solidity
101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant 
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L116-L116)']
```solidity
116:     function getCurrentLiquidity(uint256 tokenId) public view returns (uint128, address, address) 
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L42)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner 
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L63-L63)']
```solidity
63:     function setThreshold(uint8 _threshold) public onlyOwner 
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L84)']
```solidity
84:     function execute(
85:         address destination,
86:         bytes calldata data,
87:         uint256 gasLimit,
88:         address executor,
89:         bytes32[] memory sigR,
90:         bytes32[] memory sigS,
91:         uint8[] memory sigV,
92:         uint256 deadline
93:     ) public 
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L124-L124)']
```solidity
124:     function domainSeparatorV4() public view returns (bytes32) 
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager 
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L75-L75)']
```solidity
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L71-L71)']
```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L71-L71)']
```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) 
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L75-L75)']
```solidity
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) 
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner 
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52)']
```solidity
52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner 
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36)']
```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner 
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner 
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L52-L52)']
```solidity
52:     function addVaultInfo(uint256 vaultId, uint256 baseChainId, address omniChainManager) public onlyOwner 
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L75-L75)']
```solidity
75:     function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public 
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57-L57)']
```solidity
57:     function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager 
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L68)']
```solidity
68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant 
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L19-L19)']
```solidity
19:     function getTVL() public view returns (uint256) 
```
['[147](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147-L147)']
```solidity
147:     function addRoutes(RouteData[] memory _routes) public onlyMaintainer 
```
['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L14-L14)']
```solidity
14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) 
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L41-L41)']
```solidity
41:     function getLatestUpdateTime(uint256 vaultId, PositionRegistry registry) public view returns (uint256) 
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L37)']
```solidity
37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
38:         public
39:         onlyMaintainer
40:     
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L71)']
```solidity
71:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) 
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L71)']
```solidity
71:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) 
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L109-L109)']
```solidity
109:     function getValueFromChainlinkFeed(
110:         AggregatorV3Interface source,
111:         uint256 amountIn,
112:         uint256 sourceTokenUnit,
113:         bool isInverse
114:     ) public view returns (uint256) 
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L132-L132)']
```solidity
132:     function getTokenDecimals(address token) public view returns (uint256) 
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L137-L137)']
```solidity
137:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) 
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60-L60)']
```solidity
60:     function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) 
```


</details>

## [NonCritical-18] Emits without msg.sender parameter

### Resolution 
In Solidity, when `msg.sender` plays a crucial role in a function's logic, it's important for transparency and auditability that any events emitted by this function include `msg.sender` as a parameter. This practice enhances the traceability and accountability of transactions, allowing users and external observers to easily track who initiated a particular action. Including `msg.sender` in event logs helps in creating a clear and verifiable record of interactions with the contract, thereby increasing user trust and facilitating easier debugging and analysis of contract behavior. It's a key aspect of writing clear, transparent, and user-friendly smart contracts.

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[198](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L198-L214)']
```solidity
198:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {
199:         if (amount == 0) {
200:             revert NoyaAccounting_INVALID_AMOUNT();
201:         }
202: 
203:         baseToken.safeTransferFrom(msg.sender, address(this), amount); // <= FOUND
204: 
205:         if (amount > depositLimitPerTransaction) {
206:             revert NoyaAccounting_DepositLimitPerTransactionExceeded();
207:         }
208: 
209:         if (TVL() > depositLimitTotalAmount) {
210:             revert NoyaAccounting_TotalDepositLimitExceeded();
211:         }
212: 
213:         depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);
214:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer); // <= FOUND
215:         depositQueue.last += 1;
216:         depositQueue.totalAWFDeposit += amount;
217:     }
```
['[327](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L327-L353)']
```solidity
327:     function updateHoldingPosition(
328:         uint256 vaultId,
329:         bytes32 _positionId,
330:         bytes calldata _data,
331:         bytes calldata additionalData,
332:         bool removePosition
333:     ) public vaultExists(vaultId) returns (uint256) {
334:         Vault storage vault = vaults[vaultId];
335:         if (!vault.connectors[msg.sender].enabled) revert UnauthorizedAccess(); // <= FOUND
336:         if (!vault.trustedPositionsBP[_positionId].isEnabled) revert InvalidPosition(_positionId);
337:         bytes32 holdingPositionId = keccak256(abi.encode(msg.sender, _positionId, _data)); // <= FOUND
338:         uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
339:         if (positionIndex == 0 && removePosition) return type(uint256).max;
340:         if (removePosition) {
341:             if (positionIndex < vault.holdingPositions.length - 1) {
342:                 vault.holdingPositions[positionIndex] = vault.holdingPositions[vault.holdingPositions.length - 1];
343:                 vault.isPositionUsed[keccak256(
344:                     abi.encode(
345:                         vault.holdingPositions[positionIndex].calculatorConnector,
346:                         vault.holdingPositions[positionIndex].positionId,
347:                         vault.holdingPositions[positionIndex].data
348:                     )
349:                 )] = positionIndex;
350:             }
351:             vault.holdingPositions.pop();
352:             vault.isPositionUsed[holdingPositionId] = 0;
353:             emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex); // <= FOUND
354:             return type(uint256).max;
355:         }
356:         return
357:             updateHoldingPosition(vault, vaultId, _positionId, _data, additionalData, positionIndex, holdingPositionId);
358:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L115)']
```solidity
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
94:         require(isOwner[msg.sender], "Not an owner"); // <= FOUND
95:         require(sigR.length == threshold, "Not enough signatures");
96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");
97:         require(executor == msg.sender, "Invalid executor"); // <= FOUND
98:         require(block.timestamp <= deadline, "Transaction expired");
99:         {
100:             bytes32 txInputHash =
101:                 keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
103:             address lastAdd = address(0);
104:             for (uint256 i = 0; i < threshold;) {
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
106:                 require(recovered > lastAdd && isOwner[recovered]);
107:                 lastAdd = recovered;
108:                 unchecked {
109:                     ++i;
110:                 }
111:             }
112: 
113:             nonce++;
114:         }
115:         emit Execute(destination, data, gasLimit, executor, deadline); // <= FOUND
116:         (bool success,) = destination.call{ gas: gasLimit }(data);
117:         require(success, "Transaction execution reverted.");
118:     }
```
['[169](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L169-L192)']
```solidity
169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
170:         external
171:         override
172:         nonReentrant
173:     {
174:         if (!registry.isAddressTrusted(vaultId, msg.sender)) { // <= FOUND
175:             revert IConnector_InvalidAddress(msg.sender); // <= FOUND
176:         }
177: 
178:         for (uint256 i = 0; i < tokens.length; i++) {
179:             
180:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, ""); // <= FOUND
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
183:             if (_balanceAfter < amounts[i] + _balance) {
184:                 revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
185:             }
186:         }
187:         _addLiquidity(tokens, amounts, data); 
188: 
189:         for (uint256 i = 0; i < tokens.length; i++) {
190:             _updateTokenInRegistry(tokens[i]); 
191:         }
192:         emit AddLiquidity(tokens, amounts, data); // <= FOUND
193:     }
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L117)']
```solidity
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
103:             
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
115:         _amountOut = ISwapAndBridgeImplementation(swapImplInfo.route).performSwapAction(msg.sender, _swapRequest); // <= FOUND
116: 
117:         emit ExecutionCompleted( // <= FOUND
118:             _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
119:         );
120:     }
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L126-L139)']
```solidity
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
137:         ISwapAndBridgeImplementation(bridgeImplInfo.route).performBridgeAction(msg.sender, _bridgeRequest); // <= FOUND
138: 
139:         emit BridgeExecutionCompleted(_bridgeRequest); // <= FOUND
140:     }
```


</details>

## [NonCritical-19] Functions with array parameters should have length checks in place

### Resolution 
Functions in Solidity that accept array parameters should incorporate length checks as a security measure. This is to prevent potential overflow errors, unwanted gas consumption, and manipulation attempts. Without length checks, an attacker could pass excessively large arrays as input, causing excessive computation and potentially causing the function to exceed the block gas limit, leading to a denial-of-service. Additionally, unexpected array sizes could lead to logic errors within the function. As a resolution, always validate array length at the start of functions handling array inputs, ensuring it aligns with the expectations of the function logic. This makes the code more robust and predictable.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L37-L37)']
```solidity
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData) // <= FOUND
38:         external
39:         nonReentrant
40:     {
41:         caller = msg.sender;
42:         emit MakeFlashLoan(tokens, amounts);
43:         vault.flashLoan(this, tokens, amounts, userData);
44:         caller = address(0);
45:     }
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L98-L98)']
```solidity
98:     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant { // <= FOUND
99:         
100:         borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds);
101:         registry.updateHoldingPosition(
102:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
103:         );
104:     }
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L122-L124)']
```solidity
122:     function transferPositionToAnotherConnector(
123:         address[] memory tokens, // <= FOUND
124:         uint256[] memory amounts, // <= FOUND
125:         bytes memory data,
126:         address connector
127:     ) external onlyManager nonReentrant {
128:         emit TransferPositionToConnector(tokens, amounts, connector, data);
129:         if (registry.isAnActiveConnector(vaultId, connector)) {
130:             IConnector(connector).addLiquidity(tokens, amounts, data);
131:         }
132:     }
```
['[267](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L267-L267)']
```solidity
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) { // <= FOUND
268:         return true;
269:     }
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L61)']
```solidity
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer { // <= FOUND
62:         priceRoutes[asset][base] = s;
63:         emit UpdatedPriceRoute(asset, base, s);
64:     }
```


</details>

## [NonCritical-20] Unused state variables present

### Resolution 
If these serve no purpose, they should be safely removed

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L17-L17)']
```solidity
17:     uint256 public constant SNX_POOL_POSITION_ID = 2; // <= FOUND
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24)']
```solidity
24:     uint32 constant TVL_UPDATE = 1; // <= FOUND
```


</details>

## [NonCritical-21] Unused modifiers present

### Resolution 
If these serve no purpose, they should be safely removed

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L53-L53)']
```solidity
53:     modifier onlyEmergencyOrWatcher() { // <= FOUND
54:         (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
55:         if (msg.sender != emergencyManager && msg.sender != watcherContract) {
56:             revert NoyaGovernance_Unauthorized(msg.sender);
57:         }
58:         _;
59:     }
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L85-L85)']
```solidity
85:     modifier onlyGovernance() { // <= FOUND
86:         (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);
87:         if (msg.sender != governer) revert NoyaGovernance_Unauthorized(msg.sender);
88:         _;
89:     }
```


</details>

## [NonCritical-22] Defined named returns not used within function 

### Resolution 
Such instances can be replaced with unnamed returns

Num of instances: 21

### Findings 


<details><summary>Click to show findings</summary>

['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L113-L113)']
```solidity
113:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) { // <= FOUND
114:         (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this));
115:         uint256 poolBaseAmount = totalCollateralBase - totalDebtBase;
116:         return valueOracle.getValue(poolBaseToken, base, poolBaseAmount);
117:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L87)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
88:         (address tokenA, address tokenB) =
89:             abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address, address));
90:         address pool = factory.getPair(tokenA, tokenB);
91:         uint256 totalSupply = IERC20(pool).totalSupply();
92:         (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();
93: 
94:         uint256 balanceThis = IERC20(pool).balanceOf(address(this));
95:         return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply;
96:     }
```
['[265](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L265-L265)']
```solidity
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
266:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
267:         PoolInfo memory poolInfo = abi.decode(PTI.additionalData, (PoolInfo));
268:         uint256 lpBalance = totalLpBalanceOf(poolInfo);
269:         (uint256 amount, address token) = LPToUnder(poolInfo, lpBalance);
270:         return _getValue(token, base, amount);
271:     }
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L106-L106)']
```solidity
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
107:         uint256 accountId = abi.decode(p.data, (uint256));
108: 
109:         (uint256[] memory markets, address[] memory tokens,, Types.Wei[] memory amounts) =
110:             dolomiteMargin.getAccountBalances(Info(address(this), accountId));
111:         uint256 totalDebt = 0;
112:         uint256 totalCollateral = 0;
113:         for (uint256 i = 0; i < markets.length; i++) {
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value);
115:             if (amounts[i].sign) {
116:                 totalCollateral += value;
117:             } else {
118:                 totalDebt += value;
119:             }
120:         }
121:         return totalCollateral - totalDebt;
122:     }
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L150-L162)']
```solidity
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
151:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
152:         IFraxPair pool = IFraxPair(abi.decode(positionInfo.data, (address)));
153:         uint256 collateralAmount = pool.userCollateralBalance(address(this));
154:         uint256 borrowerShares = pool.userBorrowShares(address(this));
155:         uint256 _borrowerAmount = pool.toBorrowAmount(borrowerShares, true);
156: 
157:         uint256 borrowValue = _getValue(pool.asset(), base, _borrowerAmount);
158:         uint256 collateralValue = _getValue(pool.collateralContract(), base, collateralAmount);
159:         if (collateralValue > borrowValue) {
160:             return collateralValue - borrowValue;
161:         }
162:         return tvl; // <= FOUND
163:     }
```
['[93](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L93-L93)']
```solidity
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
94:         address creditAccount = abi.decode(p.data, (address));
95:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
96:         ICreditFacadeV3 facade = ICreditFacadeV3(abi.decode(positionInfo.data, (address)));
97:         CollateralDebtData memory d = ICreditManagerV3(facade.creditManager()).calcDebtAndCollateral(
98:             creditAccount, CollateralCalcTask.DEBT_COLLATERAL_SAFE_PRICES
99:         );
100:         if (d.totalDebtUSD > d.totalValueUSD) {
101:             return 0;
102:         }
103:         return _getValue(address(840), base, (d.totalValueUSD - d.totalDebtUSD));
104:     }
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L90-L90)']
```solidity
90:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
91:         (uint256 amount) = abi.decode(p.additionalData, (uint256));
92:         return _getValue(steth, base, amount);
93:     }
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L148-L148)']
```solidity
148:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
149:         PositionBP memory position = registry.getPositionBP(vaultId, p.positionId);
150:         IMaverickPool pool = abi.decode(position.data, (IMaverickPool));
151: 
152:         (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool);
153:         return _getValue(pool.tokenA(), base, a) + _getValue(pool.tokenB(), base, b);
154:     }
```
['[118](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L118-L129)']
```solidity
118:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
119:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
120:         if (positionInfo.positionTypeId == MORPHO_POSITION_ID) {
121:             Id id = abi.decode(positionInfo.data, (Id));
122:             MarketParams memory params = morphoBlue.idToMarketParams(id);
123:             Market memory market = morphoBlue.market(id);
124:             Position memory pos = morphoBlue.position(id, address(this));
125:             uint256 borrowAmount =
126:                 uint256(pos.borrowShares).toAssetsUp(market.totalBorrowAssets, market.totalBorrowShares);
127:             uint256 supplyAmount =
128:                 uint256(pos.supplyShares).toAssetsUp(market.totalSupplyAssets, market.totalSupplyShares);
129:             tvl = _getValue( // <= FOUND
130:                 params.loanToken,
131:                 base,
132:                 supplyAmount + borrowAmount + convertCToL(pos.collateral, params.oracle, params.collateralToken)
133:             );
134:         }
135:     }
```
['[257](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L257-L284)']
```solidity
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
258:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
259:         if (positionInfo.positionTypeId == PENDLE_POSITION_ID) {
260:             uint256 underlyingBalance = 0;
261:             address market = abi.decode(positionInfo.data, (address));
262:             (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
263:             (, address _underlyingToken,) = _SY.assetInfo();
264: 
265:             uint256 SYAmount = _SY.balanceOf(address(this));
266: 
267:             
268:             uint256 lpBalance =
269:                 IERC20(market).balanceOf(address(this)) + pendleMarketDepositHelper.balance(market, address(this));
270:             if (lpBalance > 0) {
271:                 SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;
272:             }
273: 
274:             uint256 PTAmount = _PT.balanceOf(address(this));
275:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;
276: 
277:             uint256 YTBalance = _YT.balanceOf(address(this));
278:             if (YTBalance > 0) SYAmount += getYTValue(market, YTBalance);
279: 
280:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;
281: 
282:             tvl = valueOracle.getValue(_underlyingToken, base, underlyingBalance); // <= FOUND
283:         }
284:         return tvl; // <= FOUND
285:     }
```
['[145](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L145-L145)']
```solidity
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
146:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
147:         if (positionInfo.positionTypeId == PRISMA_POSITION_ID) {
148:             (address zap, address troveManager) = abi.decode(positionInfo.data, (address, address));
149:             IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();
150:             address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;
151:             address debTtoken = ITroveManager(troveManager).debtToken();
152:             (uint256 collateralBalance, uint256 debtBalance) =
153:                 ITroveManager(troveManager).getTroveCollAndDebt(address(this));
154:             return _getValue(collateral, base, collateralBalance) - _getValue(debTtoken, base, debtBalance);
155:         }
156:     }
```
['[121](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L121-L125)']
```solidity
121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
122:         (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address));
123:         (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =
124:             SNXCoreProxy.getAccountCollateral(accountId, collateralType);
125:         tvl = _getValue(collateralType, base, totalDeposited + totalAssigned); // <= FOUND
126:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L109-L127)']
```solidity
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
110:         PositionBP memory bp = registry.getPositionBP(vaultId, p.positionId);
111:         (address siloToken) = abi.decode(bp.data, (address));
112:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
113:         (address[] memory assets, IBaseSilo.AssetStorage[] memory assetsS) = silo.getAssetsWithState();
114:         uint256 totalDepositAmount = 0;
115:         uint256 totalBAmount = 0;
116:         for (uint256 i = 0; i < assets.length; i++) {
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));
120:             if (depositAmount == 0 && borrowAmount == 0) {
121:                 continue;
122:             }
123:             uint256 price = _getValue(assets[i], base, 1e18);
124:             totalDepositAmount += depositAmount * price / 1e18;
125:             totalBAmount += borrowAmount * price / 1e18;
126:         }
127:         tvl = totalDepositAmount - totalBAmount; // <= FOUND
128:     }
```
['[110](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L110-L110)']
```solidity
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
111:         PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
112:         uint256 poolId = abi.decode(pBP.data, (uint256));
113:         address lpAddress = LPStaking.poolInfo(poolId).lpToken;
114:         uint256 lpAmount = LPStaking.userInfo(poolId, address(this)).amount + IERC20(lpAddress).balanceOf(address(this));
115:         if (lpAmount == 0) {
116:             return 0;
117:         }
118:         address underlyingToken = IStargatePool(lpAddress).token();
119:         uint256 underlyingAmount = IStargatePool(lpAddress).amountLPtoLD(lpAmount);
120:         return _getValue(underlyingToken, base, underlyingAmount);
121:     }
```
['[127](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L127-L149)']
```solidity
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
128:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
129:         uint256 tokenId = abi.decode(p.data, (uint256));
130:         (address token0, address token1) = abi.decode(positionInfo.data, (address, address));
131:         uint256 amount0;
132:         uint256 amount1;
133:         (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));
134:         {
135:             IUniswapV3Pool pool = IUniswapV3Pool(factory.getPool(token0, token1, fee));
136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));
137: 
138:             (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);
139: 
140:             (uint160 sqrtPriceX96,,,,,,) = pool.slot0();
141:             (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
142:                 sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity
143:             );
144:             amount0 += tokensOwed0;
145:             amount1 += tokensOwed1;
146:         }
147: 
148:         tvl += valueOracle.getValue(token0, base, amount0); // <= FOUND
149:         tvl += valueOracle.getValue(token1, base, amount1); // <= FOUND
150:     }
```
['[271](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L271-L271)']
```solidity
271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) { // <= FOUND
272:         return 0;
273:     }
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L71-L74)']
```solidity
71:     function getData(address siloToken) // <= FOUND
72:         public
73:         view
74:         returns (uint256 userLTV, uint256 LiquidationThreshold, bool isSolvent) // <= FOUND
75:     {
76:         return SolvencyV2.getData(ISilo(siloRepository.getSilo(siloToken)), address(this), minimumHealthFactor);
77:     }
```
['[189](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L189-L189)']
```solidity
189:     function _isNative(IERC20 token) internal pure returns (bool isNative) { // <= FOUND
190:         return address(token) == address(0);
191:     }
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L84)']
```solidity
81:     function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources) // <= FOUND
82:         internal
83:         view
84:         returns (uint256 value) // <= FOUND
85:     {
86:         uint256 initialValue = amount;
87:         address quotingToken = asset;
88:         for (uint256 i = 0; i < sources.length; i++) {
89:             initialValue = _getValue(asset, sources[i], initialValue);
90:             quotingToken = sources[i];
91:         }
92:         return _getValue(quotingToken, baseToken, initialValue);
93:     }
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L137-L137)']
```solidity
137:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) { // <= FOUND
138:         if (assetsSources[asset][baseToken] != address(0)) {
139:             return (assetsSources[asset][baseToken], false);
140:         } else if (assetsSources[baseToken][asset] != address(0)) {
141:             return (assetsSources[baseToken][asset], true);
142:         }
143:         return (address(0), false);
144:     }
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L5-L8)']
```solidity
5:     function latestRoundData() // <= FOUND
6:         external
7:         view
8:         returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound) // <= FOUND
9:     {
10:         return (0, 1e18, 0, block.timestamp, 0);
11:     }
```


</details>

## [NonCritical-23] Both immutable and constant state variables should be CONSTANT_CASE

### Resolution 
Make found instants CAPITAL_CASE

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[21](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L21-L21)']
```solidity
21: address immutable poolBaseToken; // <= FOUND
```
['[16](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L16-L16)']
```solidity
16: INonfungiblePositionManager public immutable positionManager; // <= FOUND
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L17-L17)']
```solidity
17: IUniswapV3Factory public immutable factory; // <= FOUND
```
['[13](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L13-L13)']
```solidity
13: IMorpho public immutable morphoBlue; // <= FOUND
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L17-L17)']
```solidity
17: address immutable pool; // <= FOUND
```


</details>

## [NonCritical-24] Overly complicated arithmetic

### Resolution 
To maintain readability in code, particularly in Solidity which can involve complex mathematical operations, it is often recommended to limit the number of arithmetic operations to a maximum of 2-3 per line. Too many operations in a single line can make the code difficult to read and understand, increase the likelihood of mistakes, and complicate the process of debugging and reviewing the code. Consider splitting such operations over more than one line, take special care when dealing with division however. Try to limit the number of arithmetic operations to a maximum of 3 per line.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[514](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L514-L515)']
```solidity
514:         uint256 managementFeeAmount =
515:             (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days; // <= FOUND
```
['[172](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L172-L172)']
```solidity
172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply); // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L117-L118)']
```solidity
117:                 uint256 collateralValueInVirtualBase =
118:                     collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice; // <= FOUND
```
['[317](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L317-L317)']
```solidity
317:         return lpBalance + rewardBalance + convexRewardBalance + prismaBalance + prismaConvexBalance; // <= FOUND
```
['[128](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L128-L129)']
```solidity
128:         uint256 currentPositionLTV =
129:             (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount; // <= FOUND
```


</details>

## [NonCritical-25] Use immutable not constant for keccak state variables

### Resolution 
It's crucial to leverage the right features for the appropriate contexts in Solidity, despite the compiler's ability to correct common developer mistakes. Both `constant` and `immutable` variables have distinct uses. `Constant` variables are best suited for hard-coded, literal values within your contract, where the value doesn't need to be computed or modified. 

On the other hand, `immutable` variables are ideal for situations where the value might be the result of an expression or received from a constructor. While both serve to define unchanging variables, they function differently and their proper utilization contributes to clearer, more efficient code. Remember, even if the compiler can correct certain mistakes, best practices dictate using the correct feature for the task at hand.

Num of instances: 4

### Findings 


<details><summary>Click to show findings</summary>

['[15](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L15-L15)']
```solidity
15: bytes32 public constant MAINTAINER_ROLE = keccak256("MAINTAINER_ROLE"); // <= FOUND
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L17-L17)']
```solidity
17: bytes32 public constant GOVERNER_ROLE = keccak256("GOVERNER_ROLE"); // <= FOUND
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L19-L19)']
```solidity
19: bytes32 public constant EMERGENCY_ROLE = keccak256("EMERGENCY_ROLE"); // <= FOUND
```
['[11](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L11-L11)']
```solidity
11: bytes32 public constant TXTYPE_HASH = keccak256( // <= FOUND
```


</details>

## [NonCritical-26] Unused structs present

### Resolution 
If these serve no purpose, they should be safely removed

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L7-L7)']
```solidity
7: struct FraxPoolInfo { // <= FOUND
8:     address collateralContract;
9:     address assetContract;
10:     bool isActive;
11: }
```
['[13](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L13-L13)']
```solidity
13: struct FraxBorrowRequest { // <= FOUND
14:     address poolAddress;
15:     uint256 amount;
16: }
```


</details>

## [NonCritical-27] Empty bytes check is missing

### Resolution 
When developing smart contracts in Solidity, it's crucial to validate the inputs of your functions. This includes ensuring that the bytes parameters are not empty, especially when they represent crucial data such as addresses, identifiers, or raw data that the contract needs to process.

Missing empty bytes checks can lead to unexpected behaviour in your contract. For instance, certain operations might fail, produce incorrect results, or consume unnecessary gas when performed with empty bytes. Moreover, missing input validation can potentially expose your contract to malicious activity, including exploitation of unhandled edge cases.

To mitigate these issues, always validate that bytes parameters are not empty when the logic of your contract requires it.

Num of instances: 42

### Findings 


<details><summary>Click to show findings</summary>

['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L149-L149)']
```solidity
149:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
150:         external
151:         returns (uint256)
152:     {
153:         emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
154:         if (registry.isAnActiveConnector(vaultId, msg.sender)) {
155:             IERC20(token).safeTransfer(address(msg.sender), amount);
156:             return amount;
157:         }
158:         return 0;
159:     }
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L254)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     {
260:         uint256 firstTemp = depositQueue.first;
261:         uint64 i = 0;
262:         uint256 processedBaseTokenAmount = 0;
263: 
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1;
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1;
280:         }
281:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount;
282: 
283:         totalDepositedAmount += processedBaseTokenAmount;
284: 
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         } else {
292:             revert NoyaAccounting_INVALID_CONNECTOR();
293:         }
294: 
295:         depositQueue.first = firstTemp;
296:     }
```
['[646](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L646-L646)']
```solidity
646:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
647:         if (positionTypeId == 0) {
648:             address[] memory tokens = new address[](1);
649:             tokens[0] = abi.decode(data, (address));
650:             return tokens;
651:         }
652:         return new address[](0);
653:     }
```
['[219](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L219-L219)']
```solidity
219:     function getPositionBP(uint256 vaultId, bytes32 _positionId) public view returns (PositionBP memory) {
220:         return vaults[vaultId].trustedPositionsBP[_positionId];
221:     }
```
['[362](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L362-L362)']
```solidity
362:     function updateHoldingPostionWithTime(
363:         uint256 vaultId,
364:         bytes32 _positionId,
365:         bytes calldata _data,
366:         bytes calldata additionalData,
367:         bool removePosition,
368:         uint256 positionTimestamp
369:     ) external vaultExists(vaultId) {
370:         uint256 positionIndex = updateHoldingPosition(vaultId, _positionId, _data, additionalData, removePosition);
371:         if (positionIndex != type(uint256).max) {
372:             vaults[vaultId].holdingPositions[positionIndex].positionTimestamp = positionTimestamp;
373:         }
374:     }
```
['[385](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L385-L385)']
```solidity
385:     function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
386:         public
387:         view
388:         returns (uint256)
389:     {
390:         bytes32 holdingPositionId = keccak256(abi.encode(_connector, _positionId, data));
391:         return vaults[vaultId].isPositionUsed[holdingPositionId];
392:     }
```
['[417](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L417-L417)']
```solidity
417:     function isPositionTrusted(uint256 vaultId, bytes32 _positionId) public view returns (bool) {
418:         return vaults[vaultId].trustedPositionsBP[_positionId].isEnabled;
419:     }
```
['[427](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L427-L427)']
```solidity
427:     function isPositionTrustedForConnector(uint256 vaultId, bytes32 _positionId, address connector)
428:         public
429:         view
430:         returns (bool)
431:     {
432:         PositionBP memory position = vaults[vaultId].trustedPositionsBP[_positionId];
433:         return position.isEnabled && (!position.onlyOwner || position.calculatorConnector == connector);
434:     }
```
['[477](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L477-L477)']
```solidity
477:     function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)
478:         public
479:         pure
480:         returns (bytes32)
481:     {
482:         return keccak256(abi.encode(calculatorConnector, positionTypeId, data));
483:     }
```
['[499](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L499-L499)']
```solidity
499:     function isPositionDebt(uint256 vaultId, bytes32 _positionId) public view returns (bool) {
500:         return vaults[vaultId].trustedPositionsBP[_positionId].isDebt;
501:     }
```
['[128](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L128-L128)']
```solidity
128:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
129:         return new address[](0);
130:     }
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L117-L117)']
```solidity
117:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
118:         address[] memory tokens = new address[](2);
119:         (address pool) = abi.decode(data, (address));
120:         tokens[0] = IPool(pool).token0();
121:         tokens[1] = IPool(pool).token1();
122:         return tokens;
123:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L109-L109)']
```solidity
109:     function depositIntoAuraBooster(bytes32 poolId, uint256 _amount) public onlyManager nonReentrant {
110:         (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);
111:         _approveOperations(_poolInfo.pool, _poolInfo.auraPoolAddress, _amount);
112:         IRewardPool(_poolInfo.auraPoolAddress).deposit(_amount, address(this));
113:     }
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L184-L184)']
```solidity
184:     function totalLpBalanceOf(bytes32 poolId) public view returns (uint256) {
185:         (PoolInfo memory pool,) = _getPoolInfo(poolId);
186:         return totalLpBalanceOf(pool);
187:     }
```
['[189](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L189-L189)']
```solidity
189:     function _getPoolInfo(bytes32 pooId) internal view returns (PoolInfo memory, bytes32) {
190:         bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(pooId));
191:         PositionBP memory p = registry.getPositionBP(vaultId, positionId);
192:         return (abi.decode(p.additionalData, (PoolInfo)), positionId);
193:     }
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L37-L37)']
```solidity
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
38:         external
39:         nonReentrant
40:     {
41:         caller = msg.sender;
42:         emit MakeFlashLoan(tokens, amounts);
43:         vault.flashLoan(this, tokens, amounts, userData);
44:         caller = address(0);
45:     }
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L98-L98)']
```solidity
98:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
99:         (address tokenA, address tokenB) = abi.decode(data, (address, address));
100:         address[] memory tokens = new address[](2);
101:         tokens[0] = tokenA;
102:         tokens[1] = tokenB;
103:         return tokens;
104:     }
```
['[134](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L134-L134)']
```solidity
134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
135:         return new address[](0);
136:     }
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L142-L142)']
```solidity
142:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
143:         address[] memory tokens = new address[](2);
144:         (address pool) = abi.decode(data, (address));
145:         tokens[0] = IFraxPair(pool).collateralContract();
146:         tokens[1] = IFraxPair(pool).asset();
147:         return tokens;
148:     }
```
['[144](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L144-L144)']
```solidity
144:     function onERC721Received(address, address, uint256, bytes memory) public virtual override returns (bytes4) {
145:         return this.onERC721Received.selector;
146:     }
```
['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L156-L156)']
```solidity
156:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
157:         (address pool) = abi.decode(data, (address));
158:         address[] memory tokens = new address[](2);
159:         tokens[0] = IMaverickPool(pool).tokenA();
160:         tokens[1] = IMaverickPool(pool).tokenB();
161:         return tokens;
162:     }
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L141-L141)']
```solidity
141:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
142:         Id id = abi.decode(data, (Id));
143:         MarketParams memory params = morphoBlue.idToMarketParams(id);
144:         address[] memory tokens = new address[](2);
145:         tokens[0] = params.loanToken;
146:         tokens[1] = params.collateralToken;
147:         return tokens;
148:     }
```
['[183](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L183-L183)']
```solidity
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
```
['[311](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L311-L311)']
```solidity
311:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
312:         address market = abi.decode(data, (address));
313:         (IPStandardizedYield SY,,) = IPMarket(market).readTokens();
314:         address[] memory tokens = new address[](1);
315:         (, tokens[0],) = SY.assetInfo();
316:         return tokens;
317:     }
```
['[164](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L164-L164)']
```solidity
164:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
165:         (address zap, address troveManager) = abi.decode(data, (address, address));
166:         IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();
167:         address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;
168:         address debTtoken = ITroveManager(troveManager).debtToken();
169:         address[] memory tokens = new address[](2);
170:         tokens[0] = collateral;
171:         tokens[1] = debTtoken;
172:         return tokens;
173:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L64-L64)']
```solidity
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {
65:         return this.onERC721Received.selector;
66:     }
```
['[143](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L143-L143)']
```solidity
143:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
144:         (address siloToken) = abi.decode(data, (address));
145:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
146:         (address[] memory assets,) = silo.getAssetsWithState();
147:         return assets;
148:     }
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L123-L123)']
```solidity
123:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
124:         uint256 poolId = abi.decode(data, (uint256));
125:         address lpAddress = LPStaking.poolInfo(poolId).lpToken;
126:         address[] memory tokens = new address[](1);
127:         tokens[0] = IStargatePool(lpAddress).token();
128:         return tokens;
129:     }
```
['[152](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L152-L152)']
```solidity
152:     function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
153:         address[] memory tokens = new address[](2);
154:         (tokens[0], tokens[1]) = abi.decode(data, (address, address));
155:         return tokens;
156:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L84-L84)']
```solidity
84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
85:         external
86:         returns (uint256)
87:     {
88:         emit TransferTokensToTrustedAddress(token, amount, caller, data);
89:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
90:         if (msg.sender == accountingManager) {
91:             (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);
92: 
93:             (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
94:             Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData);
95: 
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);
97:             amount = newAmount;
98:         } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {
99:             IERC20(token).safeTransfer(address(msg.sender), amount);
100:         } else {
101:             uint256 routeId = abi.decode(data, (uint256));
102:             swapHandler.verifyRoute(routeId, msg.sender);
103:             if (caller != address(this)) revert IConnector_InvalidAddress(caller);
104:             IERC20(token).safeTransfer(msg.sender, amount);
105:         }
106:         _updateTokenInRegistry(token);
107:         return amount;
108:     }
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L122-L122)']
```solidity
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
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L232-L232)']
```solidity
232:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
233:         if (positionTypeId == 0) {
234:             address[] memory tokens = new address[](1);
235:             tokens[0] = abi.decode(data, (address));
236:             return tokens;
237:         }
238:         return _getUnderlyingTokens(positionTypeId, data);
239:     }
```
['[263](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L263-L263)']
```solidity
263:     function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {
264:         return new address[](0);
265:     }
```
['[267](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L267-L267)']
```solidity
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {
268:         return true;
269:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L51-L51)']
```solidity
51:     function updatePositionToRegistryUsingType(bytes32 _positionId, bytes memory data, bool remove) external {
52:         registry.updateHoldingPosition(vaultId, _positionId, data, "", remove);
53:     }
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L59-L59)']
```solidity
59:     function addPositionToRegistryUsingType(uint256 _positionType, bytes memory data) external {
60:         registry.updateHoldingPosition(
61:             vaultId, registry.calculatePositionId(address(this), _positionType, ""), data, "", false
62:         );
63:     }
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L65-L65)']
```solidity
65:     function addPositionToRegistry(bytes memory data) external {
66:         registry.updateHoldingPosition(
67:             vaultId, registry.calculatePositionId(address(this), positionType, ""), data, "", false
68:         );
69:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L75-L75)']
```solidity
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
76:         return new address[](0);
77:     }
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L65-L65)']
```solidity
65:     function _lzReceive(Origin calldata _origin, bytes32, bytes calldata _message, address, bytes calldata)
66:         internal
67:         override
68:     {
69:         (uint256 vaultId, uint256 tvl, uint256 updateTime) = abi.decode(_message, (uint256, uint256, uint256));
70:         uint256 _srcChainId = chainInfo[_origin.srcEid].chainId;
71:         OmnichainManagerBaseChain(vaultIdToVaultInfo[vaultId].omniChainManager).updateTVL(_srcChainId, tvl, updateTime);
72:     }
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36)']
```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner {
37:         messageSetting = _messageSetting;
38:     }
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L57-L57)']
```solidity
57:     function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {
58:         if (approvedBridgeTXN[transactionHash] != 0) delete approvedBridgeTXN[transactionHash];
59:         else approvedBridgeTXN[transactionHash] = block.timestamp;
60:         emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp);
61:     }
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L165)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     {
170:         if (!_isNative(token)) {
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId));
172: 
173:             _setAllowance(token, lifi, amount);
174:         }
175: 
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);
177: 
178:         if (!success) {
179:             revert FailedToForward(err);
180:         }
181: 
182:         emit Forwarded(lifi, address(token), amount, data);
183:     }
```


</details>

## [NonCritical-28] Return bool not explicit

### Resolution 
In Solidity, when designing functions that return boolean values, it's crucial for clarity and maintainability to explicitly handle both `true` and `false` return scenarios. If a function is intended to return `true` under certain conditions, it should also explicitly return `false` when these conditions are not met, and vice versa. This approach eliminates ambiguity and makes the code's intent more transparent. Explicitly handling all possible outcomes of a boolean function ensures that future modifications or extensions of the contract do not unintentionally alter its logic. It contributes to better readability, easier debugging, and reduces the risk of bugs related to unintended fall-through cases.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[267](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L267-L268)']
```solidity
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool) {
268:         return true; // <= FOUND
269:     }
```
['[110](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L110-L124)']
```solidity
110:     function verifySwapData(SwapRequest calldata _request) public view override returns (bool) {
111:         bytes4 selector = bytes4(_request.data[:4]);
112:         if (selector != LI_FI_GENERIC_SWAP_SELECTOR) {
113:             revert InvalidSelector();
114:         }
115:         (address sendingAssetId, uint256 amount, address from, address receivingAssetId, uint256 receivingAmount) =
116:             ILiFi(lifi).extractGenericSwapParameters(_request.data);
117: 
118:         if (from != _request.from) revert InvalidReceiver(from, _request.from);
119:         if (receivingAmount < _request.minAmount) revert InvalidMinAmount();
120:         if (sendingAssetId != _request.inputToken) revert InvalidInputToken();
121:         if (receivingAssetId != _request.outputToken) revert InvalidOutputToken();
122:         if (amount != _request.amount) revert InvalidAmount();
123: 
124:         return true; // <= FOUND
125:     }
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L150-L162)']
```solidity
150:     function verifyBridgeData(BridgeRequest calldata _request) public view override returns (bool) {
151:         ILiFi.BridgeData memory bridgeData = ILiFi(lifi).extractBridgeData(_request.data);
152: 
153:         if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
154:         if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId();
155:         if (bridgeData.sendingAssetId != _request.inputToken) revert InvalidFromToken();
156:         if (bridgeData.receiver != _request.receiverAddress) {
157:             revert InvalidReceiver(bridgeData.receiver, _request.receiverAddress);
158:         }
159:         if (bridgeData.minAmount > _request.amount) revert InvalidMinAmount();
160:         if (bridgeData.destinationChainId != _request.destChainId) revert InvalidToChainId();
161: 
162:         return true; // <= FOUND
163:     }
```


</details>

## [NonCritical-29] call bypasses function existence check, type checking and argument packing

### Resolution 
Using the `.call` method in Solidity enables direct communication with an address, bypassing function existence checks, type checking, and argument packing. While this can save gas and provide flexibility, it can also introduce security risks and potential errors. The absence of these checks can lead to unexpected behavior if the callee contract's interface changes or if the input parameters are not crafted with care. The resolution to these issues is to use Solidity's high-level interface for calling functions when possible, as it automatically manages these aspects. If using `.call` is necessary, ensure that the inputs are carefully validated and that awareness of the called contract's behavior is maintained.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L81-L82)']
```solidity
81:                 
82:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L116-L116)']
```solidity
116:         (bool success,) = destination.call{ gas: gasLimit }(data); // <= FOUND
```
['[176](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176)']
```solidity
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data); // <= FOUND
```


</details>

## [NonCritical-30] Missing events in sensitive functions

### Resolution 
Sensitive setter functions in smart contracts often alter critical state variables. Without events emitted in these functions, external observers or dApps cannot easily track or react to these state changes. Missing events can obscure contract activity, hampering transparency and making integration more challenging. To resolve this, incorporate appropriate event emissions within these functions. Events offer an efficient way to log crucial changes, aiding in real-time tracking and post-transaction verification.

Num of instances: 15

### Findings 


<details><summary>Click to show findings</summary>

['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L79-L79)']
```solidity
79:     function setMaxNumHoldingPositions(uint256 _maxNumHoldingPositions) external onlyRole(MAINTAINER_ROLE) { // <= FOUND
80:         require(_maxNumHoldingPositions <= MAX_NUM_HOLDING_POSITIONS);
81:         maxNumHoldingPositions = _maxNumHoldingPositions;
82:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner { // <= FOUND
41:         require(lzHelperAddress != address(0));
42:         chainInfo[lzChainId] = ChainInfo(chainId, lzHelperAddress);
43:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L51-L51)']
```solidity
51:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner { // <= FOUND
52:         require(lzHelperAddress != address(0));
53:         chainInfo[chainId] = ChainInfo(lzChainId, lzHelperAddress);
54:     }
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L185-L185)']
```solidity
185:     function _setAllowance(IERC20 token, address spender, uint256 amount) internal { // <= FOUND
186:         token.forceApprove(spender, amount);
187:     }
```
['[362](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L362-L362)']
```solidity
362:     function updateHoldingPostionWithTime( // <= FOUND
363:         uint256 vaultId,
364:         bytes32 _positionId,
365:         bytes calldata _data,
366:         bytes calldata additionalData,
367:         bool removePosition,
368:         uint256 positionTimestamp
369:     ) external vaultExists(vaultId) {
370:         uint256 positionIndex = updateHoldingPosition(vaultId, _positionId, _data, additionalData, removePosition);
371:         if (positionIndex != type(uint256).max) {
372:             vaults[vaultId].holdingPositions[positionIndex].positionTimestamp = positionTimestamp;
373:         }
374:     }
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L153-L153)']
```solidity
153:     function updateTokenInRegistry(address token) public onlyManager { // <= FOUND
154:         _updateTokenInRegistry(token);
155:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L51-L51)']
```solidity
51:     function updatePositionToRegistryUsingType(bytes32 _positionId, bytes memory data, bool remove) external { // <= FOUND
52:         registry.updateHoldingPosition(vaultId, _positionId, data, "", remove);
53:     }
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L36-L36)']
```solidity
36:     function updateMessageSetting(bytes memory _messageSetting) public onlyOwner { // <= FOUND
37:         messageSetting = _messageSetting;
38:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L75-L75)']
```solidity
75:     function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public { // <= FOUND
76:         if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
77: 
78:         uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
79:         bytes memory data = abi.encode(vaultId, tvl, updateTime);
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); 
81:     }
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L32-L32)']
```solidity
32:     function updateTVL(uint256 chainId, uint256 tvl, uint256 updateTime) external nonReentrant { // <= FOUND
33:         if (msg.sender != lzHelper) revert IConnector_InvalidSender();
34: 
35:         registry.updateHoldingPostionWithTime(
36:             vaultId,
37:             registry.calculatePositionId(address(this), OMNICHAIN_POSITION_ID, abi.encode(chainId)),
38:             "",
39:             abi.encode(tvl),
40:             tvl <= DUST_LEVEL,
41:             updateTime
42:         );
43:     }
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28-L28)']
```solidity
28:     function updateTVLInfo() external onlyManager { // <= FOUND
29:         uint256 tvl = getTVL();
30:         LZHelperSender(lzHelper).updateTVL(vaultId, tvl, block.timestamp);
31:     }
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L184-L184)']
```solidity
184:     function _update(address from, address to, uint256 amount) internal override { // <= FOUND
185:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {
186:             revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
187:         }
188:         super._update(from, to, amount);
189:     }
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L91-L91)']
```solidity
91:     function _updateTokenInRegistry(address token) internal { // <= FOUND
92:         _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0);
93:     }
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L79-L79)']
```solidity
79:     function _updateTokenInRegistry(address token, bool remove) internal { // <= FOUND
80:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
81:         
82:         bytes32 positionId = registry.calculatePositionId(accountingManager, 0, abi.encode(token));
83:         
84:         uint256 positionIndex =
85:             registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));
86:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
87:             registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);
88:         }
89:     }
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L91-L91)']
```solidity
91:     function _updateTokenInRegistry(address token) internal { // <= FOUND
92:         _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0);
93:     }
```


</details>

## [NonCritical-31] Avoid mutating function parameters

### Resolution 
Function parameters in Solidity are passed by value, meaning they are essentially local copies. Mutating them can lead to confusion and errors because the changes don't persist outside the function. By keeping function parameters immutable, you ensure clarity in code behavior, preventing unintended side-effects. If you need to modify a value based on a parameter, use a local variable inside the function, leaving the original parameter unaltered. By adhering to this practice, you maintain a clear distinction between input data and the internal processing logic, improving code readability and reducing the potential for bugs.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L84-L97)']
```solidity
84:     function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
85:         external
86:         returns (uint256)
87:     {
88:         emit TransferTokensToTrustedAddress(token, amount, caller, data);
89:         (address accountingManager,) = registry.getVaultAddresses(vaultId);
90:         if (msg.sender == accountingManager) {
91:             (,,,, address watcherContract,) = registry.getGovernanceAddresses(vaultId);
92: 
93:             (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes));
94:             Watchers(watcherContract).verifyRemoveLiquidity(amount, newAmount, newData);
95: 
96:             IERC20(token).safeTransfer(address(accountingManager), newAmount);
97:             amount = newAmount; // <= FOUND
98:         } else if (registry.isAnActiveConnector(vaultId, msg.sender) || msg.sender == registry.flashLoan()) {
99:             IERC20(token).safeTransfer(address(msg.sender), amount);
100:         } else {
101:             uint256 routeId = abi.decode(data, (uint256));
102:             swapHandler.verifyRoute(routeId, msg.sender);
103:             if (caller != address(this)) revert IConnector_InvalidAddress(caller);
104:             IERC20(token).safeTransfer(msg.sender, amount);
105:         }
106:         _updateTokenInRegistry(token);
107:         return amount;
108:     }
```


</details>

## [NonCritical-32] Don't only depend on Solidity's arithmetic ordering.

### Resolution 
Relying on Solidity's default arithmetic operator precedence can lead to misunderstood or overlooked nuances in code execution. Misinterpretation risks can be significant, especially when different developers or auditors review the code. To ensure clarity and minimize potential errors, it's recommended to use parentheses. These not only override the default precedence when needed but also emphasize the intended order of operations. By deliberately showing the intended calculation sequence using parentheses, developers make the code's logic explicit, reducing the risk of unintended behaviors and making the codebase more maintainable and understandable for all stakeholders.

Num of instances: 7

### Findings 


<details><summary>Click to show findings</summary>

['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L124-L124)']
```solidity
124:             totalDepositAmount += depositAmount * price / 1e18; // <= FOUND
```
['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L125-L125)']
```solidity
125:             totalBAmount += borrowAmount * price / 1e18; // <= FOUND
```
['[412](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L412-L414)']
```solidity
412:             
413:             uint256 baseTokenAmount =
414:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled; // <= FOUND
```
['[420](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L420-L420)']
```solidity
420:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION; // <= FOUND
```
['[131](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L131-L131)']
```solidity
131:         uint256 amount0 = balance * reserve0 / totalSupply; // <= FOUND
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L132-L132)']
```solidity
132:         uint256 amount1 = balance * reserve1 / totalSupply; // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L117-L118)']
```solidity
117:                 uint256 collateralValueInVirtualBase =
118:                     collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice; // <= FOUND
```


</details>

## [NonCritical-33] A event should be emitted if a non immutable state variable is set in a constructor

Num of instances: 28

### Findings 


<details><summary>Click to show findings</summary>

['[93](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L93-L98)']
```solidity
93:     constructor(AccountingManagerConstructorParams memory p)
94:         ERC4626(IERC20(p._baseTokenAddress))
95:         ERC20(p._name, p._symbol)
96:         NoyaGovernanceBase(PositionRegistry(p._registry), p._vaultId)
97:     {
98:         baseToken = IERC20(p._baseTokenAddress); // <= FOUND
99:         valueOracle = INoyaValueOracle(p._valueOracle); // <= FOUND
100:         lastFeeDistributionTime = block.timestamp; // <= FOUND
101:         withdrawFeeReceiver = p._withdrawFeeReceiver; // <= FOUND
102:         performanceFeeReceiver = p._performanceFeeReceiver; // <= FOUND
103:         managementFeeReceiver = p._managementFeeReceiver; // <= FOUND
104: 
105:         require(p._baseTokenAddress != address(0));
106:         require(p._valueOracle != address(0));
107:         require(p._withdrawFeeReceiver != address(0));
108:         require(p._performanceFeeReceiver != address(0));
109:         require(p._managementFeeReceiver != address(0));
110: 
111:         if (
112:             p._withdrawFee > WITHDRAWAL_MAX_FEE || p._performanceFee > PERFORMANCE_MAX_FEE
113:                 || p._managementFee > MANAGEMENT_MAX_FEE
114:         ) {
115:             revert NoyaAccounting_INVALID_FEE();
116:         }
117:         withdrawFee = p._withdrawFee; // <= FOUND
118:         performanceFee = p._performanceFee; // <= FOUND
119:         managementFee = p._managementFee; // <= FOUND
120:     }
```
['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L14-L19)']
```solidity
14:     constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
15:         require(_accountingManager != address(0));
16:         require(_baseToken != address(0));
17:         require(_receiver != address(0));
18:         accountingManager = _accountingManager; // <= FOUND
19:         baseToken = _baseToken; // <= FOUND
20:         receiver = _receiver; // <= FOUND
21:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L33-L36)']
```solidity
33:     constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {
34:         swapHandler = params.swapHandler; // <= FOUND
35:         valueOracle = params.valueOracle; // <= FOUND
36:         minimumHealthFactor = MINIMUM_HEALTH_FACTOR; // <= FOUND
37:     }
```
['[34](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L40)']
```solidity
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
35:         NoyaGovernanceBase(_registry, _vaultId)
36:     {
37:         for (uint256 i = 0; i < usersAddresses.length; i++) {
38:             isEligibleToUse[usersAddresses[i]] = true;
39:         }
40:         valueOracle = INoyaValueOracle(_valueOracle); // <= FOUND
41:         require(_valueOracle != address(0));
42:     }
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L66-L76)']
```solidity
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
67:         require(_governer != address(0));
68:         require(_maintainer != address(0));
69:         require(_emergency != address(0));
70:         _grantRole(GOVERNER_ROLE, _governer);
71:         _grantRole(MAINTAINER_ROLE, _maintainer);
72:         _grantRole(EMERGENCY_ROLE, _emergency);
73:         _setRoleAdmin(GOVERNER_ROLE, GOVERNER_ROLE);
74:         _setRoleAdmin(MAINTAINER_ROLE, GOVERNER_ROLE);
75:         _setRoleAdmin(EMERGENCY_ROLE, GOVERNER_ROLE);
76:         flashLoan = _flashLoan; // <= FOUND
77:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L40-L45)']
```solidity
40:     constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)
41:         BaseConnector(baseConnectorParams)
42:     {
43:         require(_router != address(0));
44:         aerodromeRouter = IRouter(_router); // <= FOUND
45:         voter = IVoter(_voter); // <= FOUND
46:     }
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L42-L48)']
```solidity
42:     constructor(address _balancerVault, address bal, address aura, BaseConnectorCP memory baseConnectorParams)
43:         BaseConnector(baseConnectorParams)
44:     {
45:         require(_balancerVault != address(0));
46:         require(bal != address(0));
47:         require(aura != address(0));
48:         AURA = aura; // <= FOUND
49:         BAL = bal; // <= FOUND
50:         balancerVault = _balancerVault; // <= FOUND
51:     }
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L24-L28)']
```solidity
24:     constructor(address _balancerVault, PositionRegistry _registry) {
25:         require(_balancerVault != address(0));
26:         require(address(_registry) != address(0));
27:         vault = IBalancerVault(_balancerVault); // <= FOUND
28:         registry = _registry; // <= FOUND
29:     }
```
['[21](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L21-L24)']
```solidity
21:     constructor(PositionRegistry _registry, uint256 _vaultId) {
22:         require(address(_registry) != address(0));
23:         registry = _registry; // <= FOUND
24:         vaultId = _vaultId; // <= FOUND
25:     }
```
['[22](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L22-L24)']
```solidity
22:     constructor(address _registry, uint256 _vaultId) {
23:         registry = PositionRegistry(_registry); // <= FOUND
24:         vaultId = _vaultId; // <= FOUND
25:     }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L29-L31)']
```solidity
29:     constructor(PositionRegistry _registry) {
30:         require(address(_registry) != address(0));
31:         registry = _registry; // <= FOUND
32:     }
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L44-L46)']
```solidity
44:     constructor(address _reg) {
45:         require(_reg != address(0));
46:         registry = PositionRegistry(_reg); // <= FOUND
47:     }
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L32)']
```solidity
31:     constructor(address _factory, PositionRegistry _registry) {
32:         factory = _factory; // <= FOUND
33:         registry = _registry; // <= FOUND
34:     }
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L36-L40)']
```solidity
36:     constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
37:         require(_router != address(0));
38:         require(_factory != address(0));
39:         router = ICamelotRouter(_router); // <= FOUND
40:         factory = ICamelotFactory(_factory); // <= FOUND
41:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L27-L31)']
```solidity
27:     constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
28:         BaseConnector(baseConnectorParams)
29:     {
30:         positionManager = INonfungiblePositionManager(_positionManager);
31:         factory = IUniswapV3Factory(_factory); // <= FOUND
32:     }
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L45-L59)']
```solidity
45:     constructor(
46:         address _convexBooster,
47:         address cvx,
48:         address crv,
49:         address prisma,
50:         BaseConnectorCP memory baseConnectorParams
51:     ) BaseConnector(baseConnectorParams) {
52:         require(_convexBooster != address(0));
53:         require(cvx != address(0));
54:         require(crv != address(0));
55:         require(prisma != address(0));
56:         convexBooster = IBooster(_convexBooster); // <= FOUND
57:         CVX = cvx; // <= FOUND
58:         CRV = crv; // <= FOUND
59:         PRISMA = prisma; // <= FOUND
60:     }
```
['[18](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L18-L27)']
```solidity
18:     constructor(
19:         address _depositWithdrawalProxy,
20:         address _dolomiteMargin,
21:         address _borrowPositionProxy,
22:         BaseConnectorCP memory baseConnectorParams
23:     ) BaseConnector(baseConnectorParams) {
24:         require(_depositWithdrawalProxy != address(0));
25:         depositWithdrawalProxy = IDepositWithdrawalProxy(_depositWithdrawalProxy); // <= FOUND
26:         dolomiteMargin = IDolomiteMargin(_dolomiteMargin); // <= FOUND
27:         borrowPositionProxy = IBorrowPositionProxyV1(_borrowPositionProxy); // <= FOUND
28:     }
```
['[20](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L20-L30)']
```solidity
20:     constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)
21:         BaseConnector(baseConnectorParams)
22:     {
23:         require(_lido != address(0));
24:         require(_lidoW != address(0));
25:         require(_steth != address(0));
26:         require(w != address(0));
27:         lido = _lido; // <= FOUND
28:         lidoWithdrawal = _lidoW; // <= FOUND
29:         steth = _steth; // <= FOUND
30:         weth = w; // <= FOUND
31:     }
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L43-L53)']
```solidity
43:     constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)
44:         BaseConnector(baseCP)
45:     {
46:         require(_mav != address(0));
47:         require(_veMav != address(0));
48:         require(mr != address(0));
49:         require(pi != address(0));
50:         mav = _mav; // <= FOUND
51:         veMav = _veMav; // <= FOUND
52:         maverickRouter = mr; // <= FOUND
53:         positionInspector = IPositionInspector(pi); // <= FOUND
54:     }
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L19-L23)']
```solidity
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
20:         UNIv3Connector(_positionManager, _factory, baseConnectorParams)
21:     {
22:         require(MC != address(0));
23:         masterchef = IMasterchefV3(MC); // <= FOUND
24:     }
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L57-L65)']
```solidity
57:     constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)
58:         BaseConnector(baseCP)
59:     {
60:         require(_pendleMarketDepositHelper != address(0));
61:         require(_pendleRouter != address(0));
62:         require(SR != address(0));
63:         pendleMarketDepositHelper = IPendleMarketDepositHelper(_pendleMarketDepositHelper); // <= FOUND
64:         pendleRouter = IPAllActionV3(_pendleRouter); // <= FOUND
65:         staticRouter = IPendleStaticRouter(SR); // <= FOUND
66:     }
```
['[20](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L20-L22)']
```solidity
20:     constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
21:         require(_SNXCoreProxy != address(0));
22:         SNXCoreProxy = IV3CoreProxy(_SNXCoreProxy); // <= FOUND
23:     }
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L17-L23)']
```solidity
17:     constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
18:         require(SR != address(0));
19: 
20:         siloRepository = ISiloRepository(SR); // <= FOUND
21:         MINIMUM_HEALTH_FACTOR = 5e17; // <= FOUND
22: 
23:         minimumHealthFactor = MINIMUM_HEALTH_FACTOR; // <= FOUND
24:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L33-L41)']
```solidity
33:     constructor(address lpStacking, address _stargateRouter, BaseConnectorCP memory baseConnectorParams)
34:         BaseConnector(baseConnectorParams)
35:     {
36:         require(lpStacking != address(0));
37:         require(_stargateRouter != address(0));
38: 
39:         LPStaking = IStargateLPStaking(lpStacking); // <= FOUND
40:         stargateRouter = IStargateRouter(_stargateRouter); // <= FOUND
41:         rewardToken = LPStaking.stargate(); // <= FOUND
42:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L27-L32)']
```solidity
27:     constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
28:         require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);
29:         for (uint256 i = 0; i < _owners.length; i++) {
30:             isOwner[_owners[i]] = true;
31:         }
32:         numOwners = _owners.length; // <= FOUND
33:         threshold = _threshold; // <= FOUND
34:     }
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L19-L22)']
```solidity
19:     constructor(uint256 dl, address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
20:         OmnichainLogic(_lzHelper, baseConnectorParams)
21:     {
22:         DUST_LEVEL = dl; // <= FOUND
23:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L29)']
```solidity
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
28:         isHandler[swapHandler] = true;
29:         lifi = _lifi; // <= FOUND
30:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33-L36)']
```solidity
33:     constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
34:         BaseConnector(baseConnectorParams)
35:     {
36:         lzHelper = _lzHelper; // <= FOUND
37:         require(_lzHelper != address(0));
38:     }
```


</details>

## [NonCritical-34] Non constant/immutable state variables are missing a setter post deployment

### Resolution 
Non-constant or non-immutable state variables lacking a setter function can create inflexibility in contract operations. If there's no way to update these variables post-deployment, the contract might not adapt to changing conditions or requirements, which can be a significant drawback, especially in upgradable or long-lived contracts. To resolve this, implement setter functions guarded by appropriate access controls, like `onlyOwner` or similar modifiers, so that these variables can be updated as required while maintaining security. This enables smoother contract maintenance and feature upgrades.

Num of instances: 26

### Findings 


<details><summary>Click to show findings</summary>

['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L8-L8)']
```solidity
8:     address public receiver;
```
['[9](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L9-L9)']
```solidity
9:     address public accountingManager;
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L27-L27)']
```solidity
27:     address internal balancerVault;
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L29-L29)']
```solidity
29:     address public BAL;
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L30-L30)']
```solidity
30:     address public AURA;
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L32-L32)']
```solidity
32:     uint256 public BALANCER_LP_POSITION = 1;
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L8-L8)']
```solidity
8:     uint256 public COMPOUND_LP = 2;
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L27-L27)']
```solidity
27:     address public CVX;
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L28-L28)']
```solidity
28:     address public CRV;
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L29-L29)']
```solidity
29:     address public PRISMA;
```
['[22](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L22-L22)']
```solidity
22:     uint256 public COLLATERAL_AND_DEBT_POSITION_TYPE = 1;
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L8-L8)']
```solidity
8:     address public lido;
```
['[9](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L9-L9)']
```solidity
9:     address public lidoWithdrawal;
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L10-L10)']
```solidity
10:     address public steth;
```
['[11](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L11-L11)']
```solidity
11:     address public weth;
```
['[13](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L13-L13)']
```solidity
13:     uint256 public LIDO_WITHDRAWAL_REQUEST_ID = 10;
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L30-L30)']
```solidity
30:     address mav;
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L31-L31)']
```solidity
31:     address veMav;
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L32-L32)']
```solidity
32:     address maverickRouter;
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L35-L35)']
```solidity
35:     uint256 public MAVERICK_LP = 10;
```
['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L12-L12)']
```solidity
12:     IMasterchefV3 public masterchef;
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L8-L8)']
```solidity
8:     uint256 public vaultId;
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L28-L28)']
```solidity
28:     uint256 public MINIMUM_HEALTH_FACTOR = 15e17;
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L31-L31)']
```solidity
31:     uint256 public DUST_LEVEL = 1;
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L17-L17)']
```solidity
17:     uint256 public vaultId = 0;
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L17-L17)']
```solidity
17:     address payable public lzHelper;
```


</details>

## [NonCritical-35] gasLimit should be uint64

### Resolution 
To ensure compatability with the EVM gasLimits should be uint64 to prevent values higher than what is compatible. In instances where L2's are used this is even more paramount as a gasLimit higher than max(uint64) may be allowed within the L2, this may not be the case with hte underlying L1 such as ZKEVM and the EVM

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L108)']
```solidity
84:     
100:     function execute(
101:         address destination,
102:         bytes calldata data,
103:         uint256 gasLimit, // <= FOUND
104:         address executor,
105:         bytes32[] memory sigR,
106:         bytes32[] memory sigS,
107:         uint8[] memory sigV,
108:         uint256 deadline // <= FOUND
109:     ) public {
```


</details>

## [NonCritical-36] Contracts use both += 1 and ++ (-- and -= 1)

### Resolution 
For consistency consider only using one of these incrementing methods.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[15](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L15-L605)']
```solidity
15: contract AccountingManager is IAccountingManager, ERC4626, ReentrancyGuard, Pausable, NoyaGovernanceBase {
16:     using SafeERC20 for IERC20;
17: 
20:     DepositQueue public depositQueue;
21:     
22:     WithdrawQueue public withdrawQueue;
23: 
26:     mapping(address => uint256) public withdrawRequestsByAddress;
27:     
29:     uint256 public amountAskedForWithdraw;
30: 
33:     uint256 public totalDepositedAmount;
34:     
36:     uint256 public totalWithdrawnAmount;
37:     
40:     uint256 public storedProfitForFee;
41:     
42:     uint256 public profitStoredTime;
43:     
44:     uint256 public lastFeeDistributionTime;
45:     
46:     uint256 public totalProfitCalculated;
47:     
49:     uint256 public preformanceFeeSharesWaitingForDistribution;
50: 
51:     uint256 public constant FEE_PRECISION = 1e6;
52:     uint256 public constant WITHDRAWAL_MAX_FEE = 5e4;
53:     uint256 public constant MANAGEMENT_MAX_FEE = 5e5;
54:     uint256 public constant PERFORMANCE_MAX_FEE = 1e5;
55: 
59:     IERC20 public baseToken;
60: 
62:     uint256 public withdrawFee; 
63:     
64:     uint256 public performanceFee;
65:     
66:     uint256 public managementFee;
67:     
68:     address public withdrawFeeReceiver;
69:     
70:     address public performanceFeeReceiver;
71:     
72:     address public managementFeeReceiver;
73: 
78:     WithdrawGroup public currentWithdrawGroup;
79: 
81:     uint256 public depositWaitingTime = 30 minutes;
82:     
83:     uint256 public withdrawWaitingTime = 6 hours;
84: 
86:     uint256 public depositLimitTotalAmount = 1e6 * 200_000;
87:     
88:     uint256 public depositLimitPerTransaction = 1e6 * 2000;
89: 
91:     INoyaValueOracle public valueOracle;
92: 
93:     constructor(AccountingManagerConstructorParams memory p)
94:         ERC4626(IERC20(p._baseTokenAddress))
95:         ERC20(p._name, p._symbol)
96:         NoyaGovernanceBase(PositionRegistry(p._registry), p._vaultId)
97:     {
98:         baseToken = IERC20(p._baseTokenAddress);
99:         valueOracle = INoyaValueOracle(p._valueOracle);
100:         lastFeeDistributionTime = block.timestamp;
101:         withdrawFeeReceiver = p._withdrawFeeReceiver;
102:         performanceFeeReceiver = p._performanceFeeReceiver;
103:         managementFeeReceiver = p._managementFeeReceiver;
104: 
105:         require(p._baseTokenAddress != address(0));
106:         require(p._valueOracle != address(0));
107:         require(p._withdrawFeeReceiver != address(0));
108:         require(p._performanceFeeReceiver != address(0));
109:         require(p._managementFeeReceiver != address(0));
110: 
111:         if (
112:             p._withdrawFee > WITHDRAWAL_MAX_FEE || p._performanceFee > PERFORMANCE_MAX_FEE
113:                 || p._managementFee > MANAGEMENT_MAX_FEE
114:         ) {
115:             revert NoyaAccounting_INVALID_FEE();
116:         }
117:         withdrawFee = p._withdrawFee;
118:         performanceFee = p._performanceFee;
119:         managementFee = p._managementFee;
120:     }
121: 
123:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {
124:         require(address(_valueOracle) != address(0));
125:         valueOracle = _valueOracle;
126:         emit ValueOracleUpdated(address(_valueOracle));
127:     }
128: 
134:     function setFeeReceivers(
135:         address _withdrawFeeReceiver,
136:         address _performanceFeeReceiver,
137:         address _managementFeeReceiver
138:     ) public onlyMaintainer {
139:         require(_withdrawFeeReceiver != address(0));
140:         require(_performanceFeeReceiver != address(0));
141:         require(_managementFeeReceiver != address(0));
142:         withdrawFeeReceiver = _withdrawFeeReceiver;
143:         performanceFeeReceiver = _performanceFeeReceiver;
144:         managementFeeReceiver = _managementFeeReceiver;
145:         emit FeeRecepientsChanged(_withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver);
146:     }
147: 
149:     function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
150:         external
151:         returns (uint256)
152:     {
153:         emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
154:         if (registry.isAnActiveConnector(vaultId, msg.sender)) {
155:             IERC20(token).safeTransfer(address(msg.sender), amount);
156:             return amount;
157:         }
158:         return 0;
159:     }
160: 
169:     function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer {
170:         if (
171:             _withdrawFee > WITHDRAWAL_MAX_FEE || _performanceFee > PERFORMANCE_MAX_FEE
172:                 || _managementFee > MANAGEMENT_MAX_FEE
173:         ) {
174:             revert NoyaAccounting_INVALID_FEE();
175:         }
176:         withdrawFee = _withdrawFee;
177:         performanceFee = _performanceFee;
178:         managementFee = _managementFee;
179:         emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee);
180:     }
181: 
184:     function _update(address from, address to, uint256 amount) internal override {
185:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) {
186:             revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
187:         }
188:         super._update(from, to, amount);
189:     }
190: 
198:     function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {
199:         if (amount == 0) {
200:             revert NoyaAccounting_INVALID_AMOUNT();
201:         }
202: 
203:         baseToken.safeTransferFrom(msg.sender, address(this), amount);
204: 
205:         if (amount > depositLimitPerTransaction) {
206:             revert NoyaAccounting_DepositLimitPerTransactionExceeded();
207:         }
208: 
209:         if (TVL() > depositLimitTotalAmount) {
210:             revert NoyaAccounting_TotalDepositLimitExceeded();
211:         }
212: 
213:         depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);
214:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);
215:         depositQueue.last += 1; // <= FOUND
216:         depositQueue.totalAWFDeposit += amount;
217:     }
218: 
223:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
224:         uint256 middleTemp = depositQueue.middle;
225:         uint64 i = 0;
226: 
227:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
228: 
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
231:                 && i < maxIterations
232:         ) {
233:             i += 1; // <= FOUND
234:             DepositRequest storage data = depositQueue.queue[middleTemp];
235: 
236:             uint256 shares = previewDeposit(data.amount);
237:             data.shares = shares;
238:             data.calculationTime = block.timestamp;
239:             emit CalculateDeposit(
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
242: 
243:             middleTemp += 1; // <= FOUND
244:         }
245: 
246:         depositQueue.middle = middleTemp;
247:     }
248: 
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     {
260:         uint256 firstTemp = depositQueue.first;
261:         uint64 i = 0;
262:         uint256 processedBaseTokenAmount = 0;
263: 
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1; // <= FOUND
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1; // <= FOUND
280:         }
281:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount;
282: 
283:         totalDepositedAmount += processedBaseTokenAmount;
284: 
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         } else {
292:             revert NoyaAccounting_INVALID_CONNECTOR();
293:         }
294: 
295:         depositQueue.first = firstTemp;
296:     }
297: 
301:     function withdraw(uint256 share, address receiver) public nonReentrant whenNotPaused {
302:         if (balanceOf(msg.sender) < share + withdrawRequestsByAddress[msg.sender]) {
303:             revert NoyaAccounting_INSUFFICIENT_FUNDS(
304:                 balanceOf(msg.sender), share, withdrawRequestsByAddress[msg.sender]
305:             );
306:         }
307:         withdrawRequestsByAddress[msg.sender] += share;
308: 
309:         
310:         withdrawQueue.queue[withdrawQueue.last] = WithdrawRequest(msg.sender, receiver, block.timestamp, 0, share, 0);
311:         emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp);
312:         withdrawQueue.last += 1; // <= FOUND
313:     }
314:     
325:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
326:         uint256 middleTemp = withdrawQueue.middle;
327:         uint64 i = 0;
328:         uint256 processedShares = 0;
329:         uint256 assetsNeededForWithdraw = 0;
330:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
331: 
332:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {
333:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
334:         }
335:         while (
336:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
337:                 && i < maxIterations
338:         ) {
339:             i += 1; // <= FOUND
340:             WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
341:             uint256 assets = previewRedeem(data.shares);
342:             data.amount = assets;
343:             data.calculationTime = block.timestamp;
344:             assetsNeededForWithdraw += assets;
345:             processedShares += data.shares;
346:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);
347: 
348:             middleTemp += 1; // <= FOUND
349:         }
350:         currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
351:         withdrawQueue.middle = middleTemp;
352:     }
353: 
357:     function startCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
358:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false);
359:         currentWithdrawGroup.isStarted = true;
360:         currentWithdrawGroup.lastId = withdrawQueue.middle;
361:         emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount);
362:     }
363: 
367:     function fulfillCurrentWithdrawGroup() public onlyManager nonReentrant whenNotPaused {
368:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false);
369:         uint256 neededAssets = neededAssetsForWithdraw();
370: 
371:         if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) {
372:             revert NoyaAccounting_NOT_READY_TO_FULFILL();
373:         }
374:         currentWithdrawGroup.isFullfilled = true;
375:         amountAskedForWithdraw = 0;
376:         uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
377:         if (availableAssets >= currentWithdrawGroup.totalCBAmount) {
378:             currentWithdrawGroup.totalABAmount = currentWithdrawGroup.totalCBAmount;
379:         } else {
380:             currentWithdrawGroup.totalABAmount = availableAssets;
381:         }
382:         currentWithdrawGroup.totalCBAmountFullfilled = currentWithdrawGroup.totalCBAmount;
383:         currentWithdrawGroup.totalCBAmount = 0;
384:         emit WithdrawGroupFulfilled(
385:             currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount
386:         );
387:     }
388: 
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
394:         if (currentWithdrawGroup.isFullfilled == false) {
395:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
396:         }
397:         uint64 i = 0;
398:         uint256 firstTemp = withdrawQueue.first;
399: 
400:         uint256 withdrawFeeAmount = 0;
401:         uint256 processedBaseTokenAmount = 0;
402:         
403:         while (
404:             currentWithdrawGroup.lastId > firstTemp
405:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
406:                 && i < maxIterations
407:         ) {
408:             i += 1; // <= FOUND
409:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
410:             uint256 shares = data.shares;
411:             
412:             uint256 baseTokenAmount =
413:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
414: 
415:             withdrawRequestsByAddress[data.owner] -= shares;
416:             _burn(data.owner, shares);
417: 
418:             processedBaseTokenAmount += data.amount;
419:             {
420:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
421:                 withdrawFeeAmount += feeAmount;
422:                 baseTokenAmount = baseTokenAmount - feeAmount;
423:             }
424: 
425:             baseToken.safeTransfer(data.receiver, baseTokenAmount);
426:             emit ExecuteWithdraw(
427:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
428:             );
429:             delete withdrawQueue.queue[firstTemp];
430:             
431:             firstTemp += 1; // <= FOUND
432:         }
433:         totalWithdrawnAmount += processedBaseTokenAmount;
434: 
435:         if (withdrawFeeAmount > 0) {
436:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);
437:         }
438:         withdrawQueue.first = firstTemp;
439:         
440:         if (currentWithdrawGroup.lastId == firstTemp) {
441:             delete currentWithdrawGroup;
442:         }
443:     }
444: 
450:     function resetMiddle(uint256 newMiddle, bool depositOrWithdraw) public onlyManager {
451:         if (depositOrWithdraw) {
452:             emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw);
453: 
454:             if (newMiddle > depositQueue.middle || newMiddle < depositQueue.first) {
455:                 revert NoyaAccounting_INVALID_AMOUNT();
456:             }
457:             depositQueue.middle = newMiddle;
458:         } else {
459:             emit ResetMiddle(newMiddle, withdrawQueue.middle, depositOrWithdraw);
460: 
461:             if (newMiddle > withdrawQueue.middle || newMiddle < withdrawQueue.first || currentWithdrawGroup.isStarted) {
462:                 revert NoyaAccounting_INVALID_AMOUNT();
463:             }
464:             withdrawQueue.middle = newMiddle;
465:         }
466:     }
467: 
472:     function recordProfitForFee() public onlyManager nonReentrant {
473:         storedProfitForFee = getProfit();
474:         profitStoredTime = block.timestamp;
475: 
476:         if (storedProfitForFee < totalProfitCalculated) {
477:             return;
478:         }
479: 
480:         preformanceFeeSharesWaitingForDistribution =
481:             previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);
482:         emit RecordProfit(
483:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
484:         );
485:     }
486: 
490:     function checkIfTVLHasDroped() public nonReentrant {
491:         uint256 currentProfit = getProfit();
492:         if (currentProfit < storedProfitForFee) {
493:             emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
494:             preformanceFeeSharesWaitingForDistribution = 0;
495:             profitStoredTime = 0;
496:         }
497:     }
498: 
502:     function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {
503:         if (block.timestamp - lastFeeDistributionTime < 1 days) {
504:             return (0, 0);
505:         }
506:         uint256 timePassed = block.timestamp - lastFeeDistributionTime;
507:         if (timePassed > 10 days) {
508:             timePassed = 10 days;
509:         }
510:         uint256 totalShares = totalSupply();
511:         uint256 currentFeeShares = balanceOf(managementFeeReceiver) + balanceOf(performanceFeeReceiver)
512:             + preformanceFeeSharesWaitingForDistribution;
513: 
514:         uint256 managementFeeAmount =
515:             (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days;
516:         _mint(managementFeeReceiver, managementFeeAmount);
517:         emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares);
518:         lastFeeDistributionTime = block.timestamp;
519:         return (managementFeeAmount, timePassed);
520:     }
521: 
523:     function collectPerformanceFees() public onlyManager nonReentrant {
524:         if (
525:             preformanceFeeSharesWaitingForDistribution == 0 || block.timestamp - profitStoredTime < 12 hours
526:                 || block.timestamp - profitStoredTime > 48 hours
527:         ) {
528:             return;
529:         }
530: 
531:         _mint(performanceFeeReceiver, preformanceFeeSharesWaitingForDistribution);
532: 
533:         totalProfitCalculated = storedProfitForFee;
534: 
535:         emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution);
536: 
537:         preformanceFeeSharesWaitingForDistribution = 0;
538:     }
539: 
540:     function burnShares(uint256 amount) public {
541:         _burn(msg.sender, amount);
542:     }
543: 
545:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
546:         uint256 amountAskedForWithdraw_temp = 0;
547:         uint256 neededAssets = neededAssetsForWithdraw();
548:         for (uint256 i = 0; i < retrieveData.length; i++) { // <= FOUND
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
566:         amountAskedForWithdraw += amountAskedForWithdraw_temp;
567:         if (amountAskedForWithdraw_temp > neededAssets) {
568:             revert NoyaAccounting_INVALID_AMOUNT();
569:         }
570:     }
571: 
579:     function getProfit() public view returns (uint256) {
580:         uint256 tvl = TVL();
581:         if (tvl + totalWithdrawnAmount > totalDepositedAmount) {
582:             return tvl + totalWithdrawnAmount - totalDepositedAmount;
583:         }
584:         return 0;
585:     }
586: 
588:     function totalAssets() public view override returns (uint256) {
589:         return TVL();
590:     }
591:     
593:     function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
594:         public
595:         view
596:         returns (DepositRequest[] memory depositData, WithdrawRequest[] memory withdrawData)
597:     {
598:         if (depositOrWithdraw) {
599:             depositData = new DepositRequest[](items.length);
600:             for (uint256 i = 0; i < items.length; i++) { // <= FOUND
601:                 depositData[i] = depositQueue.queue[items[i]];
602:             }
603:         } else {
604:             withdrawData = new WithdrawRequest[](items.length);
605:             for (uint256 i = 0; i < items.length; i++) { // <= FOUND
606:                 withdrawData[i] = withdrawQueue.queue[items[i]];
607:             }
608:         }
609:         return (depositData, withdrawData);
610:     }
611:     
613:     function neededAssetsForWithdraw() public view returns (uint256) {
614:         uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
615:         if ( 
616:             currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true
617:                 || availableAssets >= currentWithdrawGroup.totalCBAmount
618:         ) {
619:             return 0;
620:         }
621:         return currentWithdrawGroup.totalCBAmount - availableAssets;
622:     }
623: 
624:     function TVL() public view returns (uint256) {
625:         return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this))
626:             - depositQueue.totalAWFDeposit;
627:     }
628: 
629:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {
630:         PositionBP memory p = registry.getPositionBP(vaultId, position.positionId);
631:         if (p.positionTypeId == 0) {
632:             address token = abi.decode(p.data, (address));
633:             uint256 amount = IERC20(token).balanceOf(abi.decode(position.data, (address)));
634:             return _getValue(token, base, amount);
635:         }
636:         return 0;
637:     }
638: 
639:     function _getValue(address token, address base, uint256 amount) internal view returns (uint256) {
640:         if (token == base) {
641:             return amount;
642:         }
643:         return valueOracle.getValue(token, base, amount);
644:     }
645: 
646:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
647:         if (positionTypeId == 0) {
648:             address[] memory tokens = new address[](1);
649:             tokens[0] = abi.decode(data, (address));
650:             return tokens;
651:         }
652:         return new address[](0);
653:     }
654: 
656:     function emergencyStop() public whenNotPaused onlyEmergency {
657:         _pause();
658:     }
659: 
660:     function unpause() public whenPaused onlyEmergency {
661:         _unpause();
662:     }
663: 
664:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer {
665:         depositLimitPerTransaction = _depositLimitPerTransaction;
666:         depositLimitTotalAmount = _depositTotalAmount;
667:         emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount);
668:     }
669: 
670:     function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer {
671:         depositWaitingTime = _depositWaitingTime;
672:         emit SetDepositWaitingTime(_depositWaitingTime);
673:     }
674: 
675:     function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer {
676:         withdrawWaitingTime = _withdrawWaitingTime;
677:         emit SetWithdrawWaitingTime(_withdrawWaitingTime);
678:     }
679: 
680:     function rescue(address token, uint256 amount) public onlyEmergency nonReentrant {
681:         if (token == address(0)) {
682:             (bool success,) = payable(msg.sender).call{ value: amount }("");
683:             require(success, "Transfer failed.");
684:         } else {
685:             IERC20(token).safeTransfer(msg.sender, amount);
686:         }
687:         emit Rescue(msg.sender, token, amount);
688:     }
689: 
690:     function mint(uint256 shares, address receiver) public override returns (uint256) {
691:         revert NoyaAccounting_NOT_ALLOWED();
692:     }
693: 
694:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {
695:         revert NoyaAccounting_NOT_ALLOWED();
696:     }
697: 
698:     function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {
699:         revert NoyaAccounting_NOT_ALLOWED();
700:     }
701: 
702:     function deposit(uint256 assets, address receiver) public override returns (uint256) {
703:         revert NoyaAccounting_NOT_ALLOWED();
704:     }
705: }
```


</details>

## [NonCritical-37] Use transfer libraries instead of low level calls

### Resolution 
Using transfer libraries like OpenZeppelin's Address.sendValue is preferred over low-level calls for transferring Ether in Solidity. These libraries provide clearer, more semantically meaningful methods compared to low-level call() functions. They encapsulate best practices for error handling and gas management, enhancing the security and readability of your code. Low-level calls lack these built-in safety checks and can be more error-prone, especially when dealing with Ether transfers.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[682](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L682-L682)']
```solidity
682:             (bool success,) = payable(msg.sender).call{ value: amount }(""); // <= FOUND
```
['[195](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195)']
```solidity
195:             (bool success,) = payable(userAddress).call{ value: amount }(""); // <= FOUND
```


</details>

## [NonCritical-38] Use 'using' keyword when using specific imports rather than calling the specific import directly

### Resolution 
In Solidity, the `using` keyword can streamline the use of library functions for specific types. Instead of calling library functions directly with their full import paths, you can declare a library once with `using` for a specific type. This approach makes your code more readable and concise. For example, instead of `LibraryName.functionName(variable)`, you would first declare `using LibraryName for TypeName;` at the contract level. After this, you can call library functions directly on variables of `TypeName` like `variable.functionName()`. This method not only enhances code clarity but also promotes cleaner and more organized code, especially when multiple functions from the same library are used frequently.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[227](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L227-L227)']
```solidity
227:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry); // <= FOUND 'TVLHelper.'
```
['[625](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L625-L625)']
```solidity
625:         return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this)) // <= FOUND 'TVLHelper.'
626:             - depositQueue.totalAWFDeposit;
```
['[21](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L21-L21)']
```solidity
21:         return TVLHelper.getTVL(vaultId, registry, baseToken); // <= FOUND 'TVLHelper.'
```


</details>

## [NonCritical-39] Avoid declaring variables with the names of defined functions within the project

### Resolution 
Having such variables can create confusion in both developers and in users of the project. Consider renaming these variables to improve code clarity.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L23-L23)']
```solidity
23:             bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId); // <= FOUND
```


</details>

## [NonCritical-40] For loop iterates on arrays not indexed

### Resolution 
Ensuring matching input array lengths in functions is crucial to prevent logical errors and inconsistencies in smart contracts. Mismatched array lengths can lead to incomplete operations or incorrect data handling, particularly if one array's length is assumed to reflect another's. For instance, iterating over a shorter array than intended could result in unprocessed elements from a longer array, potentially causing unintended consequences in contract execution. Validating that all input arrays have intended lengths before performing operations helps safeguard against such errors, ensuring that all elements are appropriately processed and the contract behaves as expected.

Num of instances: 9

### Findings 


<details><summary>Click to show findings</summary>

['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L74-L77)']
```solidity
74:            for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i]; // <= FOUND
78:             }
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L74-L77)']
```solidity
74:             for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i]; // <= FOUND
78:             }
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L113-L115)']
```solidity
113:        for (uint256 i = 0; i < markets.length; i++) { // <= FOUND
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value); // <= FOUND
115:             if (amounts[i].sign) { // <= FOUND
116:                 totalCollateral += value;
117:             } else {
118:                 totalDebt += value;
119:             }
120:         }
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L113-L115)']
```solidity
113:         for (uint256 i = 0; i < markets.length; i++) { // <= FOUND
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value); // <= FOUND
115:             if (amounts[i].sign) { // <= FOUND
116:                 totalCollateral += value;
117:             } else {
118:                 totalDebt += value;
119:             }
120:         }
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L116-L119)']
```solidity
116:        for (uint256 i = 0; i < assets.length; i++) { // <= FOUND
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this)); // <= FOUND
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)); // <= FOUND
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this)); // <= FOUND
120:             if (depositAmount == 0 && borrowAmount == 0) {
121:                 continue;
122:             }
123:             uint256 price = _getValue(assets[i], base, 1e18);
124:             totalDepositAmount += depositAmount * price / 1e18;
125:             totalBAmount += borrowAmount * price / 1e18;
126:         }
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L116-L119)']
```solidity
116:         for (uint256 i = 0; i < assets.length; i++) { // <= FOUND
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this)); // <= FOUND
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)); // <= FOUND
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this)); // <= FOUND
120:             if (depositAmount == 0 && borrowAmount == 0) {
121:                 continue;
122:             }
123:             uint256 price = _getValue(assets[i], base, 1e18);
124:             totalDepositAmount += depositAmount * price / 1e18;
125:             totalBAmount += borrowAmount * price / 1e18;
126:         }
```
['[178](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L178-L184)']
```solidity
178:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
179:             
180:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
183:             if (_balanceAfter < amounts[i] + _balance) { // <= FOUND
184:                 revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]); // <= FOUND
185:             }
186:         }
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L211-L216)']
```solidity
211:        for (uint256 i = 0; i < tokensIn.length; i++) { // <= FOUND
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]); // <= FOUND
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
218:         }
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L211-L216)']
```solidity
211:         for (uint256 i = 0; i < tokensIn.length; i++) { // <= FOUND
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]); // <= FOUND
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
218:         }
```


</details>

## [NonCritical-41] Constructor with array/string/bytes parameters has no empty array checks

### Resolution 
Failing to validate for empty array inputs in constructors can lead to vulnerabilities or logical errors in smart contracts. Constructors often initialize key contract settings, and arrays may represent crucial data like access controls, initial states, or configuration parameters. Without empty array checks, a contract might be deployed in an unintended state, lacking necessary data for its operations or security measures. 

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[34](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L34)']
```solidity
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
35:         NoyaGovernanceBase(_registry, _vaultId)
36:     {
37:         for (uint256 i = 0; i < usersAddresses.length; i++) {
38:             isEligibleToUse[usersAddresses[i]] = true;
39:         }
40:         valueOracle = INoyaValueOracle(_valueOracle);
41:         require(_valueOracle != address(0));
42:     }
```


</details>

## [NonCritical-42] Consider using AccessControlDefaultAdminRules rather than AccessControl

### Resolution 
Using `AccessControlDefaultAdminRules` over `AccessControl` in Solidity contracts provides a predefined set of rules for administrative privileges, simplifying the management of roles and permissions. It offers a structured approach to defining who can grant or revoke roles, enhancing security and governance within contracts by standardizing access controls and reducing the risk of misconfiguration.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L12-L12)']
```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard  // <= FOUND
```
['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L12-L12)']
```solidity
12: contract PositionRegistry is AccessControl, IPositionRegistry, ReentrancyGuard  // <= FOUND
```


</details>

## [NonCritical-43] Consider using OpenZeppelins SafeCall library when making calls to arbitrary contracts

### Resolution 
Using OpenZeppelin's `SafeCall` library for interactions with arbitrary contracts is a best practice in smart contract development. This library provides functions that ensure safer external calls by validating that calls are successfully completed, helping to prevent common pitfalls such as reentrancy attacks or unexpected failures. It encapsulates low-level call operations with safety checks, reducing the risk of vulnerabilities associated with direct interactions with unknown code. Incorporating `SafeCall` enhances contract security and robustness, making it a wise choice for developers aiming to safeguard their applications.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L116)']
```solidity
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
94:         require(isOwner[msg.sender], "Not an owner");
95:         require(sigR.length == threshold, "Not enough signatures");
96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");
97:         require(executor == msg.sender, "Invalid executor");
98:         require(block.timestamp <= deadline, "Transaction expired");
99:         {
100:             bytes32 txInputHash =
101:                 keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
103:             address lastAdd = address(0);
104:             for (uint256 i = 0; i < threshold;) {
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
106:                 require(recovered > lastAdd && isOwner[recovered]);
107:                 lastAdd = recovered;
108:                 unchecked {
109:                     ++i;
110:                 }
111:             }
112: 
113:             nonce++;
114:         }
115:         emit Execute(destination, data, gasLimit, executor, deadline);
116:         (bool success,) = destination.call{ gas: gasLimit }(data); // <= FOUND
117:         require(success, "Transaction execution reverted.");
118:     }
```


</details>

## [NonCritical-44] It is redundant to store the zero address as a constant state variable

### Resolution 
Storing the zero address (address(0)) as a constant state variable in a Solidity contract is redundant because address(0) is a well-known, fixed value that represents an uninitialized or non-existent address. Directly using address(0) in comparisons or assignments is more gas-efficient and clearer.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L23-L23)']
```solidity
23: address public constant ETH = address(0); // <= FOUND
```


</details>

## [NonCritical-45] Avoid using 'owner' or '_owner' as a parameter name

### Resolution 
Using 'owner' or '_owner' as a parameter name in functions, especially in contracts inheriting from or interacting with OpenZeppelin's `Ownable` contract, can lead to confusion and potential bugs. These contracts often have a state variable named `owner`, managed by the `Ownable` pattern for access control. Using the same name for function parameters may obscure the contract's `owner` state variable, complicating code readability and maintenance. Prefer alternative descriptive names for parameters to maintain clarity and prevent conflicts with established ownership patterns.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[694](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L694-L694)']
```solidity
694:     function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256)  // <= FOUND
```


</details>

## [NonCritical-46] Modifier checks msg.sender against two addresses. Consider using multiple modifiers for more control

### Resolution 
In Solidity, using a single modifier to check msg.sender against two different addresses can make the code less flexible and harder to maintain. Instead, consider using multiple modifiers for greater control and clarity. Separating these checks into individual modifiers improves readability and reusability, as each modifier can then be applied independently to different functions according to specific access requirements. This approach enhances the modularity of the contract and makes it easier to update or extend access control logic in the future, aligning with best practices for smart contract development and security.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L31-L33)']
```solidity
31:     modifier onlyManager() {
32:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
33:         if (!(msg.sender == keeperContract || msg.sender == emergencyManager || msg.sender == registry.flashLoan())) { // <= FOUND
34:             revert NoyaGovernance_Unauthorized(msg.sender);
35:         }
36:         _;
37:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L53-L55)']
```solidity
53:     modifier onlyEmergencyOrWatcher() {
54:         (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
55:         if (msg.sender != emergencyManager && msg.sender != watcherContract) { // <= FOUND
56:             revert NoyaGovernance_Unauthorized(msg.sender);
57:         }
58:         _;
59:     }
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L65-L67)']
```solidity
65:     modifier onlyMaintainerOrEmergency() {
66:         (, address maintainer,,,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
67:         if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender); // <= FOUND
68:         _;
69:     }
```


</details>

## [NonCritical-47] Redundant function returns constant

### Resolution 
Functions which only return a predefined constant have a similar redundancy as empty code blocks. If these blocks are not used to satisfy interface enforcements, or similar rulings, they should be removed.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L71-L72)']
```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
72:         return 0; // <= FOUND
73:     }
```


</details>

## [Gas-1] State variables used within a function more than once should be cached to save gas 

### Resolution 
Cache such variables and perform operations on them, if operations include modifications to the state variable(s) then remember to equate the state variable to it's cached counterpart at the end

Num of instances: 8

### Findings 


<details><summary>Click to show findings</summary>

['[579](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L579-L582)']
```solidity
579:     function getProfit() public view returns (uint256) { // <= FOUND 'function getProfit'
580:         uint256 tvl = TVL();
581:         if (tvl + totalWithdrawnAmount > totalDepositedAmount) { // <= FOUND 'totalWithdrawnAmount'
582:             return tvl + totalWithdrawnAmount - totalDepositedAmount; // <= FOUND 'totalWithdrawnAmount'
583:         }
584:         return 0;
585:     }
```
['[472](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L472-L483)']
```solidity
472:     function recordProfitForFee() public onlyManager nonReentrant { // <= FOUND 'function recordProfitForFee'
473:         storedProfitForFee = getProfit();
474:         profitStoredTime = block.timestamp;
475: 
476:         if (storedProfitForFee < totalProfitCalculated) { // <= FOUND 'totalProfitCalculated'
477:             return;
478:         }
479: 
480:         preformanceFeeSharesWaitingForDistribution = // <= FOUND 'preformanceFeeSharesWaitingForDistribution'
481:             previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION); // <= FOUND 'totalProfitCalculated'
482:         emit RecordProfit(
483:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp // <= FOUND 'totalProfitCalculated'
484:         );
485:     }
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L50-L60)']
```solidity
50:     function requestWithdrawals(uint256 amount) public onlyManager nonReentrant { // <= FOUND 'function requestWithdrawals'
51:         _approveOperations(steth, lidoWithdrawal, amount); // <= FOUND 'lidoWithdrawal'
52:         
53:         uint256[] memory amounts = new uint256[](1);
54:         amounts[0] = amount;
55:         
56:         uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this)); // <= FOUND 'lidoWithdrawal'
57:         bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, "");
58:         registry.updateHoldingPosition(vaultId, positionId, abi.encode(requestIds[0]), abi.encode(amount), false);
59: 
60:         _updateTokenInRegistry(steth); // <= FOUND 'steth'
61:         emit RequestWithdrawals(amount);
62:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L63-L69)']
```solidity
63:     function stake(uint256 amount, uint256 duration, bool doDelegation) external onlyManager nonReentrant { // <= FOUND 'function stake'
64:         
65:         _approveOperations(mav, veMav, amount); // <= FOUND 'veMav'
66:         
67:         IveMAV(veMav).stake(amount, duration, doDelegation); // <= FOUND 'veMav'
68:         _updateTokenInRegistry(mav);
69:         _updateTokenInRegistry(veMav); // <= FOUND 'veMav'
70:         emit Stake(amount, duration, doDelegation);
71:     }
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L49-L54)']
```solidity
49:     function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant { // <= FOUND 'function depositIntoStargatePool'
50:         address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;
51:         address underlyingToken = IStargatePool(lpAddress).token();
52:         if (depositRequest.routerAmount > 0) {
53:             _approveOperations(underlyingToken, address(stargateRouter), depositRequest.routerAmount); // <= FOUND 'stargateRouter'
54:             stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this)); // <= FOUND 'stargateRouter'
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
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L45-L49)']
```solidity
45:     function supply(address supplyToken, uint256 amount) external onlyManager nonReentrant { // <= FOUND 'function supply'
46:         _approveOperations(supplyToken, pool, amount);
47:         IPool(pool).supply(supplyToken, amount, address(this), 0);
48:         registry.updateHoldingPosition( // <= FOUND 'registry'
49:             vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", false // <= FOUND 'registry'
50:         );
51:         _updateTokenInRegistry(supplyToken);
52:         emit Supply(supplyToken, amount);
53:     }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L29-L34)']
```solidity
29:     function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant { // <= FOUND 'function supply'
30:         _approveOperations(asset, market, amount);
31:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset); // <= FOUND 'registry'
32:         IComet(market).supply(asset, amount);
33:         registry.updateHoldingPosition( // <= FOUND 'registry'
34:             vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false // <= FOUND 'registry'
35:         );
36:         _updateTokenInRegistry(asset);
37:         emit Supply(market, asset, amount);
38:     }
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L35-L47)']
```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant { // <= FOUND 'function supply'
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
46:         registry.updateHoldingPosition( // <= FOUND 'registry'
47:             vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false // <= FOUND 'registry'
48:         );
49:         emit Supply(amount, id, sOrC);
50:     }
```


</details>

## [Gas-2] Avoid updating storage when the value hasn't changed 

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[286](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L286-L317)']
```solidity
286:     function updateHoldingPosition(
287:         Vault storage vault,
288:         uint256 vaultId,
289:         bytes32 _positionId,
290:         bytes calldata d,
291:         bytes calldata AD,
292:         uint256 index,
293:         bytes32 holdingPositionId
294:     ) internal returns (uint256) {
295:         emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index);
296: 
297:         if (index == 0) {
298:             if (!isPositionTrustedForConnector(vaultId, _positionId, msg.sender)) {
299:                 revert InvalidPosition(_positionId);
300:             }
301:             if (vault.holdingPositions.length >= maxNumHoldingPositions) {
302:                 revert TooManyPositions();
303:             }
304:             vault.isPositionUsed[holdingPositionId] = vault.holdingPositions.length; // <= FOUND
305:             vault.holdingPositions.push(
306:                 HoldingPI(
307:                     vaults[vaultId].trustedPositionsBP[_positionId].calculatorConnector,
308:                     msg.sender,
309:                     _positionId,
310:                     d,
311:                     AD,
312:                     type(uint256).max
313:                 )
314:             );
315:             return vault.holdingPositions.length - 1;
316:         }
317:         vault.holdingPositions[index].additionalData = AD; // <= FOUND
318:         return index;
319:     }
```


</details>

## [Gas-3] State variable can be updated more than once in a function 

### Resolution 
Updating a state variable multiple times within a function can lead to inefficiencies and unintended behaviors. Every state change in Ethereum consumes gas, increasing the transaction cost. Moreover, frequent state changes can introduce vulnerabilities if interim values can be externally observed or acted upon. To address this, one should consolidate updates to occur only once, at the end of the function. This minimizes gas usage and ensures consistent state. 

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L37-L44)']
```solidity
37:     function makeFlashLoan(IERC20[] memory tokens, uint256[] memory amounts, bytes memory userData)
38:         external
39:         nonReentrant
40:     {
41:         caller = msg.sender; // <= FOUND
42:         emit MakeFlashLoan(tokens, amounts);
43:         vault.flashLoan(this, tokens, amounts, userData);
44:         caller = address(0); // <= FOUND
45:     }
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60-L64)']
```solidity
60:     function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) {
61:         uint128 amountIn128 = uint128(amount);
62:         address pool = assetToBaseToPool[tokenIn][baseToken]; // <= FOUND
63:         if (pool == address(0)) {
64:             pool = assetToBaseToPool[baseToken][tokenIn]; // <= FOUND
65:         }
66:         if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
67: 
68:         
69:         uint32[] memory secondsAgos = new uint32[](2);
70:         secondsAgos[0] = period;
71:         secondsAgos[1] = 0;
72: 
73:         
74:         (int56[] memory tickCumulatives,) = IUniswapV3Pool(pool).observe(secondsAgos);
75: 
76:         
77:         int56 tickCumulativesDelta = tickCumulatives[1] - tickCumulatives[0];
78: 
79:         
80:         
81:         int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period)));
82:         if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {
83:             timeWeightedAverageTick--;
84:         }
85:         _amountOut = OracleLibrary.getQuoteAtTick(timeWeightedAverageTick, amountIn128, tokenIn, baseToken);
86:     }
```


</details>

## [Gas-4] Multiple accesses of the same mapping/array key/index should be cached 

### Resolution 
Caching repeated accesses to the same mapping or array key/index in smart contracts can lead to significant gas savings. In Solidity, each read operation from storage (like accessing a value in a mapping or array using a key or index) costs gas. By storing the accessed value in a local variable and reusing it within the function, you avoid multiple expensive storage read operations. This practice is particularly beneficial in loops or functions with multiple reads of the same data. Implementing this caching approach enhances efficiency and reduces transaction costs, which is crucial for optimizing smart contract performance and user experience on the blockchain.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L156-L175)']
```solidity
156:     function changeVaultAddresses(
157:         uint256 vaultId,
158:         address _governer,
159:         address _maintainer,
160:         address _maintainerWithoutTimelock,
161:         address _keeperContract,
162:         address _watcher,
163:         address _emergency
164:     ) external onlyVaultGoverner(vaultId) vaultExists(vaultId) {
165:         require(_governer != address(0));
166:         require(_maintainer != address(0));
167:         require(_keeperContract != address(0));
168:         require(_watcher != address(0));
169: 
170:         vaults[vaultId].governer = _governer; // <= FOUND
171:         vaults[vaultId].maintainer = _maintainer; // <= FOUND
172:         vaults[vaultId].maintainerWithoutTimeLock = _maintainerWithoutTimelock; // <= FOUND
173:         vaults[vaultId].keeperContract = _keeperContract; // <= FOUND
174:         vaults[vaultId].watcherContract = _watcher; // <= FOUND
175:         vaults[vaultId].emergency = _emergency; // <= FOUND
176:         emit VaultAddressesChanged(
177:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
178:         );
179:     }
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L171)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
163:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
164:         PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
165:         uint256 lpBalance = totalLpBalanceOf(pool);
166:         (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);
167:         uint256 _totalSupply = IERC20(pool.pool).totalSupply();
168: 
169:         uint256 _weight = pool.weights[pool.tokenIndex]; // <= FOUND
170: 
171:         uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]); // <= FOUND
172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);
173:     }
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L68-L81)']
```solidity
68:     function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
69:         bytes32 txn = keccak256(abi.encode(bridgeRequest));
70:         emit StartBridgeTransaction(bridgeRequest, txn);
71:         if (approvedBridgeTXN[txn] == 0 || approvedBridgeTXN[txn] + BRIDGE_TXN_WAITING_TIME > block.timestamp) { // <= FOUND
72:             revert IConnector_BridgeTransactionNotApproved(txn);
73:         }
74:         if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput();
75:         if (
76:             destChainAddress[bridgeRequest.destChainId] == address(0)
77:                 || destChainAddress[bridgeRequest.destChainId] != bridgeRequest.receiverAddress
78:         ) {
79:             revert IConnector_InvalidDestinationChain();
80:         }
81:         approvedBridgeTXN[txn] = 0; // <= FOUND
82:         swapHandler.executeBridge(bridgeRequest);
83:         _updateTokenInRegistry(bridgeRequest.inputToken);
84:     }
```


</details>

## [Gas-5] bytes.concat() can be used in place of abi.encodePacked 

### Resolution 
Given concatenation is not going to be used for hashing bytes.concat is the preferred method to use as its more gas efficient when used with bytes variables

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L102-L102)']
```solidity
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash)); // <= FOUND
```


</details>

## [Gas-6] Shortcircuit rules can be be used to optimize some gas usage 

### Resolution 
Reading state variables takes alot of gas to do, so if you have a conditional statement regarding a state varaible alongide others which are not related to state vars, it is advisable to have conditions which do not involve state vars be declared first in the overall conditional so unnecessary state variable lookups can be avoided.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L72-L72)']
```solidity
72:         if (asset == baseToken || amount == 0) { // <= FOUND
```
['[403](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L403-L407)']
```solidity
403:         
404:         while (
405:             currentWithdrawGroup.lastId > firstTemp
406:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp // <= FOUND
407:                 && i < maxIterations // <= FOUND
408:         ) {
```
['[264](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L264-L266)']
```solidity
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI // <= FOUND
267:         ) {
```
['[285](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L285-L285)']
```solidity
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) { // <= FOUND
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L64-L64)']
```solidity
64:         require(_threshold <= numOwners && _threshold > 1); // <= FOUND
```


</details>

## [Gas-7] Using named returns for pure and view functions is cheaper than using regular returns

Num of instances: 94

### Findings 


<details><summary>Click to show findings</summary>

['[579](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L579-L584)']
```solidity
579:     function getProfit() public view returns (uint256) {
580:         uint256 tvl = TVL();
581:         if (tvl + totalWithdrawnAmount > totalDepositedAmount) {
582:             return tvl + totalWithdrawnAmount - totalDepositedAmount; // <= FOUND
583:         }
584:         return 0; // <= FOUND
585:     }
```
['[588](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L588-L589)']
```solidity
588:     function totalAssets() public view override returns (uint256) {
589:         return TVL(); // <= FOUND
590:     }
```
['[593](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L593-L609)']
```solidity
593:     function getQueueItems(bool depositOrWithdraw, uint256[] memory items)
594:         public
595:         view
596:         returns (DepositRequest[] memory depositData, WithdrawRequest[] memory withdrawData)
597:     {
598:         if (depositOrWithdraw) {
599:             depositData = new DepositRequest[](items.length);
600:             for (uint256 i = 0; i < items.length; i++) {
601:                 depositData[i] = depositQueue.queue[items[i]];
602:             }
603:         } else {
604:             withdrawData = new WithdrawRequest[](items.length);
605:             for (uint256 i = 0; i < items.length; i++) {
606:                 withdrawData[i] = withdrawQueue.queue[items[i]];
607:             }
608:         }
609:         return (depositData, withdrawData); // <= FOUND
610:     }
```
['[613](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L613-L621)']
```solidity
613:     function neededAssetsForWithdraw() public view returns (uint256) {
614:         uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
615:         if ( 
616:             currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true
617:                 || availableAssets >= currentWithdrawGroup.totalCBAmount
618:         ) {
619:             return 0; // <= FOUND
620:         }
621:         return currentWithdrawGroup.totalCBAmount - availableAssets; // <= FOUND
622:     }
```
['[624](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L624-L625)']
```solidity
624:     function TVL() public view returns (uint256) {
625:         return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this)) // <= FOUND
626:             - depositQueue.totalAWFDeposit;
627:     }
```
['[629](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L629-L636)']
```solidity
629:     function getPositionTVL(HoldingPI memory position, address base) public view returns (uint256) {
630:         PositionBP memory p = registry.getPositionBP(vaultId, position.positionId);
631:         if (p.positionTypeId == 0) {
632:             address token = abi.decode(p.data, (address));
633:             uint256 amount = IERC20(token).balanceOf(abi.decode(position.data, (address)));
634:             return _getValue(token, base, amount); // <= FOUND
635:         }
636:         return 0; // <= FOUND
637:     }
```
['[639](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L639-L643)']
```solidity
639:     function _getValue(address token, address base, uint256 amount) internal view returns (uint256) {
640:         if (token == base) {
641:             return amount; // <= FOUND
642:         }
643:         return valueOracle.getValue(token, base, amount); // <= FOUND
644:     }
```
['[646](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L646-L652)']
```solidity
646:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
647:         if (positionTypeId == 0) {
648:             address[] memory tokens = new address[](1);
649:             tokens[0] = abi.decode(data, (address));
650:             return tokens; // <= FOUND
651:         }
652:         return new address[](0); // <= FOUND
653:     }
```
['[219](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L219-L220)']
```solidity
219:     function getPositionBP(uint256 vaultId, bytes32 _positionId) public view returns (PositionBP memory) {
220:         return vaults[vaultId].trustedPositionsBP[_positionId]; // <= FOUND
221:     }
```
['[385](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L385-L391)']
```solidity
385:     function getHoldingPositionIndex(uint256 vaultId, bytes32 _positionId, address _connector, bytes memory data)
386:         public
387:         view
388:         returns (uint256)
389:     {
390:         bytes32 holdingPositionId = keccak256(abi.encode(_connector, _positionId, data));
391:         return vaults[vaultId].isPositionUsed[holdingPositionId]; // <= FOUND
392:     }
```
['[399](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L399-L400)']
```solidity
399:     function getHoldingPosition(uint256 vaultId, uint256 i) public view returns (HoldingPI memory) {
400:         return vaults[vaultId].holdingPositions[i]; // <= FOUND
401:     }
```
['[407](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L407-L408)']
```solidity
407:     function getHoldingPositions(uint256 vaultId) public view returns (HoldingPI[] memory) {
408:         return vaults[vaultId].holdingPositions; // <= FOUND
409:     }
```
['[417](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L417-L418)']
```solidity
417:     function isPositionTrusted(uint256 vaultId, bytes32 _positionId) public view returns (bool) {
418:         return vaults[vaultId].trustedPositionsBP[_positionId].isEnabled; // <= FOUND
419:     }
```
['[427](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L427-L433)']
```solidity
427:     function isPositionTrustedForConnector(uint256 vaultId, bytes32 _positionId, address connector)
428:         public
429:         view
430:         returns (bool)
431:     {
432:         PositionBP memory position = vaults[vaultId].trustedPositionsBP[_positionId];
433:         return position.isEnabled && (!position.onlyOwner || position.calculatorConnector == connector); // <= FOUND
434:     }
```
['[440](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L440-L445)']
```solidity
440:     function getGovernanceAddresses(uint256 vaultId)
441:         public
442:         view
443:         returns (address, address, address, address, address, address)
444:     {
445:         return ( // <= FOUND
446:             vaults[vaultId].governer,
447:             vaults[vaultId].maintainer,
448:             vaults[vaultId].maintainerWithoutTimeLock,
449:             vaults[vaultId].keeperContract,
450:             vaults[vaultId].watcherContract,
451:             vaults[vaultId].emergency
452:         );
453:     }
```
['[461](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L461-L462)']
```solidity
461:     function isTokenTrusted(uint256 vaultId, address token, address connector) public view returns (bool) {
462:         return ( // <= FOUND
463:             vaults[vaultId].connectors[vaults[vaultId].accountManager].trustedTokens[token]
464:                 || vaults[vaultId].connectors[connector].trustedTokens[token]
465:         );
466:     }
```
['[490](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L490-L491)']
```solidity
490:     function isAnActiveConnector(uint256 vaultId, address connectorAddress) public view returns (bool) {
491:         return vaults[vaultId].connectors[connectorAddress].enabled; // <= FOUND
492:     }
```
['[499](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L499-L500)']
```solidity
499:     function isPositionDebt(uint256 vaultId, bytes32 _positionId) public view returns (bool) {
500:         return vaults[vaultId].trustedPositionsBP[_positionId].isDebt; // <= FOUND
501:     }
```
['[507](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L507-L508)']
```solidity
507:     function getVaultAddresses(uint256 vaultId) public view returns (address, address) {
508:         return (vaults[vaultId].accountManager, vaults[vaultId].baseToken); // <= FOUND
509:     }
```
['[516](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L516-L518)']
```solidity
516:     function isAddressTrusted(uint256 vaultId, address addr) public view returns (bool) {
517:         if (addr == vaults[vaultId].accountManager) return true; // <= FOUND
518:         return isAnActiveConnector(vaultId, addr); // <= FOUND
519:     }
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L113-L116)']
```solidity
113:     function _getPositionTVL(HoldingPI memory, address base) public view override returns (uint256 tvl) {
114:         (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this));
115:         uint256 poolBaseAmount = totalCollateralBase - totalDebtBase;
116:         return valueOracle.getValue(poolBaseToken, base, poolBaseAmount); // <= FOUND
117:     }
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L117-L122)']
```solidity
117:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
118:         address[] memory tokens = new address[](2);
119:         (address pool) = abi.decode(data, (address));
120:         tokens[0] = IPool(pool).token0();
121:         tokens[1] = IPool(pool).token1();
122:         return tokens; // <= FOUND
123:     }
```
['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L125-L133)']
```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
126:         PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
127:         (address pool) = abi.decode(pBP.data, (address));
128:         uint256 balance = IERC20(pool).balanceOf(address(this));
129:         uint256 totalSupply = IERC20(pool).totalSupply();
130:         (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();
131:         uint256 amount0 = balance * reserve0 / totalSupply;
132:         uint256 amount1 = balance * reserve1 / totalSupply;
133:         return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1); // <= FOUND
134:     }
```
['[162](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L162-L172)']
```solidity
162:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
163:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
164:         PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
165:         uint256 lpBalance = totalLpBalanceOf(pool);
166:         (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);
167:         uint256 _totalSupply = IERC20(pool.pool).totalSupply();
168: 
169:         uint256 _weight = pool.weights[pool.tokenIndex];
170: 
171:         uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]);
172:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply); // <= FOUND
173:     }
```
['[175](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L175-L181)']
```solidity
175:     function totalLpBalanceOf(PoolInfo memory pool) public view returns (uint256) {
176:         uint256 auraShares;
177:         if (pool.auraPoolAddress != address(0)) {
178:             auraShares = IERC20(pool.auraPoolAddress).balanceOf(address(this));
179:             auraShares = IRewardPool(pool.auraPoolAddress).convertToAssets(auraShares);
180:         }
181:         return IERC20(pool.pool).balanceOf(address(this)) + auraShares; // <= FOUND
182:     }
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L184-L186)']
```solidity
184:     function totalLpBalanceOf(bytes32 poolId) public view returns (uint256) {
185:         (PoolInfo memory pool,) = _getPoolInfo(poolId);
186:         return totalLpBalanceOf(pool); // <= FOUND
187:     }
```
['[189](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L189-L192)']
```solidity
189:     function _getPoolInfo(bytes32 pooId) internal view returns (PoolInfo memory, bytes32) {
190:         bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(pooId));
191:         PositionBP memory p = registry.getPositionBP(vaultId, positionId);
192:         return (abi.decode(p.additionalData, (PoolInfo)), positionId); // <= FOUND
193:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L87-L95)']
```solidity
87:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
88:         (address tokenA, address tokenB) =
89:             abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address, address));
90:         address pool = factory.getPair(tokenA, tokenB);
91:         uint256 totalSupply = IERC20(pool).totalSupply();
92:         (uint256 reserves0, uint256 reserves1,,) = ICamelotPair(pool).getReserves();
93: 
94:         uint256 balanceThis = IERC20(pool).balanceOf(address(this));
95:         return balanceThis * (_getValue(tokenA, base, reserves0) + _getValue(tokenB, base, reserves1)) / totalSupply; // <= FOUND
96:     }
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L98-L103)']
```solidity
98:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
99:         (address tokenA, address tokenB) = abi.decode(data, (address, address));
100:         address[] memory tokens = new address[](2);
101:         tokens[0] = tokenA;
102:         tokens[1] = tokenB;
103:         return tokens; // <= FOUND
104:     }
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L74-L78)']
```solidity
74:     function getAccountHealthFactor(IComet comet) public view returns (uint256) {
75:         
76:         uint256 borrowBalanceInBase = getBorrowBalanceInBase(comet);
77:         if (borrowBalanceInBase == 0) return type(uint256).max; // <= FOUND
78:         return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase; // <= FOUND
79:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L84-L86)']
```solidity
84:     function getBorrowBalanceInBase(IComet comet) public view returns (uint256 borrowBalanceInVirtualBase) {
85:         uint256 borrowBalanceInBase = comet.borrowBalanceOf(address(this));
86:         if (borrowBalanceInBase == 0) return 0; // <= FOUND
87:         address basePriceFeed = comet.baseTokenPriceFeed();
88:         uint256 basePriceInVirtualBase = comet.getPrice(basePriceFeed);
89:         borrowBalanceInVirtualBase = (borrowBalanceInBase * basePriceInVirtualBase) / comet.baseScale();
90:     }
```
['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L125-L131)']
```solidity
125:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
126:         address market = abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address));
127: 
128:         uint256 positiveBalance = getCollBlanace(IComet(market), false);
129:         uint256 negativeBalance = getBorrowBalanceInBase(IComet(market));
130:         uint256 balance = positiveBalance - negativeBalance;
131:         return (valueOracle.getValue(IComet(market).baseToken(), base, balance)); // <= FOUND
132:     }
```
['[134](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L134-L135)']
```solidity
134:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
135:         return new address[](0); // <= FOUND
136:     }
```
['[258](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L258-L261)']
```solidity
258:     function _getPoolInfo(address pool) internal view returns (PoolInfo memory) {
259:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool));
260:         PositionBP memory p = registry.getPositionBP(vaultId, positionId);
261:         return abi.decode(p.additionalData, (PoolInfo)); // <= FOUND
262:     }
```
['[265](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L265-L270)']
```solidity
265:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
266:         PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
267:         PoolInfo memory poolInfo = abi.decode(PTI.additionalData, (PoolInfo));
268:         uint256 lpBalance = totalLpBalanceOf(poolInfo);
269:         (uint256 amount, address token) = LPToUnder(poolInfo, lpBalance);
270:         return _getValue(token, base, amount); // <= FOUND
271:     }
```
['[279](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L279-L287)']
```solidity
279:     function LPToUnder(PoolInfo memory info, uint256 balance) public view returns (uint256, address) {
280:         if (balance == 0) return (0, info.tokens[info.defaultWithdrawIndex]); // <= FOUND
281:         uint256 underlyingAssetAmount =
282:             estimateWithdrawAmount(ICurveSwap(info.pool), balance, info.defaultWithdrawIndex);
283:         if (info.poolAddressIfDefaultWithdrawTokenIsAnotherPosition != address(0)) {
284:             return
285:                 LPToUnder(_getPoolInfo(info.poolAddressIfDefaultWithdrawTokenIsAnotherPosition), underlyingAssetAmount);
286:         }
287:         return (underlyingAssetAmount, info.tokens[info.defaultWithdrawIndex]); // <= FOUND
288:     }
```
['[297](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L297-L303)']
```solidity
297:     function estimateWithdrawAmount(ICurveSwap curvePool, uint256 amount, uint256 index)
298:         public
299:         view
300:         returns (uint256)
301:     {
302:         int128 tokenIndex = int128(uint128(index));
303:         return curvePool.calc_withdraw_one_coin(amount, tokenIndex); // <= FOUND
304:     }
```
['[311](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L311-L317)']
```solidity
311:     function totalLpBalanceOf(PoolInfo memory info) public view returns (uint256) {
312:         uint256 lpBalance = balanceOfLPToken(info);
313:         uint256 rewardBalance = balanceOfRewardPool(info);
314:         uint256 convexRewardBalance = balanceOfConvexRewardPool(info);
315:         uint256 prismaBalance = balanceOfPrisma(info.prismaCurvePool);
316:         uint256 prismaConvexBalance = balanceOfPrisma(info.prismaConvexPool);
317:         return lpBalance + rewardBalance + convexRewardBalance + prismaBalance + prismaConvexBalance; // <= FOUND
318:     }
```
['[325](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L325-L327)']
```solidity
325:     function balanceOfConvexRewardPool(PoolInfo memory info) public view returns (uint256) {
326:         if (info.convexRewardPool == address(0)) return 0; // <= FOUND
327:         return IConvexBasicRewards(info.convexRewardPool).balanceOf(address(this)); // <= FOUND
328:     }
```
['[335](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L335-L336)']
```solidity
335:     function balanceOfLPToken(PoolInfo memory info) public view returns (uint256) {
336:         return IERC20(info.lpToken).balanceOf(address(this)); // <= FOUND
337:     }
```
['[344](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L344-L346)']
```solidity
344:     function balanceOfRewardPool(PoolInfo memory info) public view returns (uint256) {
345:         if (info.gauge == address(0)) return 0; // <= FOUND
346:         return IRewardsGauge(info.gauge).balanceOf(address(this)); // <= FOUND
347:     }
```
['[354](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L354-L356)']
```solidity
354:     function balanceOfPrisma(address prismaPool) public view returns (uint256) {
355:         if (prismaPool == address(0)) return 0; // <= FOUND
356:         return IDepositToken(prismaPool).balanceOf(address(this)); // <= FOUND
357:     }
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L106-L121)']
```solidity
106:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
107:         uint256 accountId = abi.decode(p.data, (uint256));
108: 
109:         (uint256[] memory markets, address[] memory tokens,, Types.Wei[] memory amounts) =
110:             dolomiteMargin.getAccountBalances(Info(address(this), accountId));
111:         uint256 totalDebt = 0;
112:         uint256 totalCollateral = 0;
113:         for (uint256 i = 0; i < markets.length; i++) {
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value);
115:             if (amounts[i].sign) {
116:                 totalCollateral += value;
117:             } else {
118:                 totalDebt += value;
119:             }
120:         }
121:         return totalCollateral - totalDebt; // <= FOUND
122:     }
```
['[120](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L120-L139)']
```solidity
120:     function _getHealthFactor(IFraxPair _fraxlendPair, uint256 _exchangeRate) internal view virtual returns (uint256) {
121:         
122:         uint256 borrowerShares = _fraxlendPair.userBorrowShares(address(this));
123:         uint256 _borrowerAmount = _fraxlendPair.toBorrowAmount(borrowerShares, true);
124:         if (_borrowerAmount == 0) return type(uint256).max; // <= FOUND
125:         uint256 _collateralAmount = _fraxlendPair.userCollateralBalance(address(this));
126:         if (_collateralAmount == 0) return 0; // <= FOUND
127:         (uint256 LTV_PRECISION,,,, uint256 EXCHANGE_PRECISION,,,) = _fraxlendPair.getConstants();
128:         uint256 currentPositionLTV =
129:             (((_borrowerAmount * _exchangeRate) * LTV_PRECISION) / EXCHANGE_PRECISION) / _collateralAmount;
130: 
131:         
132:         uint256 fraxlendPairMaxLTV = _fraxlendPair.maxLTV();
133:         if (currentPositionLTV == 0) return type(uint256).max;  // <= FOUND
134: 
135:         
136:         uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;
137: 
138:         
139:         return currentHF; // <= FOUND
140:     }
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L142-L147)']
```solidity
142:     function _getUnderlyingTokens(uint256 p, bytes memory data) public view override returns (address[] memory) {
143:         address[] memory tokens = new address[](2);
144:         (address pool) = abi.decode(data, (address));
145:         tokens[0] = IFraxPair(pool).collateralContract();
146:         tokens[1] = IFraxPair(pool).asset();
147:         return tokens; // <= FOUND
148:     }
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L150-L162)']
```solidity
150:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
151:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
152:         IFraxPair pool = IFraxPair(abi.decode(positionInfo.data, (address)));
153:         uint256 collateralAmount = pool.userCollateralBalance(address(this));
154:         uint256 borrowerShares = pool.userBorrowShares(address(this));
155:         uint256 _borrowerAmount = pool.toBorrowAmount(borrowerShares, true);
156: 
157:         uint256 borrowValue = _getValue(pool.asset(), base, _borrowerAmount);
158:         uint256 collateralValue = _getValue(pool.collateralContract(), base, collateralAmount);
159:         if (collateralValue > borrowValue) {
160:             return collateralValue - borrowValue; // <= FOUND
161:         }
162:         return tvl; // <= FOUND
163:     }
```
['[93](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L93-L103)']
```solidity
93:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
94:         address creditAccount = abi.decode(p.data, (address));
95:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
96:         ICreditFacadeV3 facade = ICreditFacadeV3(abi.decode(positionInfo.data, (address)));
97:         CollateralDebtData memory d = ICreditManagerV3(facade.creditManager()).calcDebtAndCollateral(
98:             creditAccount, CollateralCalcTask.DEBT_COLLATERAL_SAFE_PRICES
99:         );
100:         if (d.totalDebtUSD > d.totalValueUSD) {
101:             return 0; // <= FOUND
102:         }
103:         return _getValue(address(840), base, (d.totalValueUSD - d.totalDebtUSD)); // <= FOUND
104:     }
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L90-L92)']
```solidity
90:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
91:         (uint256 amount) = abi.decode(p.additionalData, (uint256));
92:         return _getValue(steth, base, amount); // <= FOUND
93:     }
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L148-L153)']
```solidity
148:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
149:         PositionBP memory position = registry.getPositionBP(vaultId, p.positionId);
150:         IMaverickPool pool = abi.decode(position.data, (IMaverickPool));
151: 
152:         (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool);
153:         return _getValue(pool.tokenA(), base, a) + _getValue(pool.tokenB(), base, b); // <= FOUND
154:     }
```
['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L156-L161)']
```solidity
156:     function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
157:         (address pool) = abi.decode(data, (address));
158:         address[] memory tokens = new address[](2);
159:         tokens[0] = IMaverickPool(pool).tokenA();
160:         tokens[1] = IMaverickPool(pool).tokenB();
161:         return tokens; // <= FOUND
162:     }
```
['[108](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L108-L115)']
```solidity
108:     function getHealthFactor(Id _id, Market memory _market) public view returns (uint256) {
109:         MarketParams memory market = morphoBlue.idToMarketParams(_id);
110:         Position memory p = morphoBlue.position(_id, address(this));
111:         uint256 borrowAmount = uint256(p.borrowShares).toAssetsUp(_market.totalBorrowAssets, _market.totalBorrowShares);
112:         if (borrowAmount == 0) return type(uint256).max; // <= FOUND
113: 
114:         
115:         return market.lltv * convertCToL(p.collateral, market.oracle, market.collateralToken) / borrowAmount; // <= FOUND
116:     }
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L137-L138)']
```solidity
137:     function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {
138:         return amount * IOracle(marketOracle).price() / ORACLE_PRICE_SCALE; // <= FOUND
139:     }
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L141-L147)']
```solidity
141:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
142:         Id id = abi.decode(data, (Id));
143:         MarketParams memory params = morphoBlue.idToMarketParams(id);
144:         address[] memory tokens = new address[](2);
145:         tokens[0] = params.loanToken;
146:         tokens[1] = params.collateralToken;
147:         return tokens; // <= FOUND
148:     }
```
['[257](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L257-L284)']
```solidity
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
258:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
259:         if (positionInfo.positionTypeId == PENDLE_POSITION_ID) {
260:             uint256 underlyingBalance = 0;
261:             address market = abi.decode(positionInfo.data, (address));
262:             (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
263:             (, address _underlyingToken,) = _SY.assetInfo();
264: 
265:             uint256 SYAmount = _SY.balanceOf(address(this));
266: 
267:             
268:             uint256 lpBalance =
269:                 IERC20(market).balanceOf(address(this)) + pendleMarketDepositHelper.balance(market, address(this));
270:             if (lpBalance > 0) {
271:                 SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;
272:             }
273: 
274:             uint256 PTAmount = _PT.balanceOf(address(this));
275:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;
276: 
277:             uint256 YTBalance = _YT.balanceOf(address(this));
278:             if (YTBalance > 0) SYAmount += getYTValue(market, YTBalance);
279: 
280:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;
281: 
282:             tvl = valueOracle.getValue(_underlyingToken, base, underlyingBalance);
283:         }
284:         return tvl; // <= FOUND
285:     }
```
['[293](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L293-L295)']
```solidity
293:     function getYTValue(address market, uint256 balance) public view returns (uint256) {
294:         (uint256 netSyOut,,,,,,) = staticRouter.swapExactYtForSyStatic(market, balance);
295:         return netSyOut; // <= FOUND
296:     }
```
['[303](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L303-L305)']
```solidity
303:     function isMarketEmpty(IPMarket market) public view returns (bool) {
304:         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
305:         return ( // <= FOUND
306:             _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0
307:                 && market.balanceOf(address(this)) == 0
308:         );
309:     }
```
['[311](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L311-L316)']
```solidity
311:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
312:         address market = abi.decode(data, (address));
313:         (IPStandardizedYield SY,,) = IPMarket(market).readTokens();
314:         address[] memory tokens = new address[](1);
315:         (, tokens[0],) = SY.assetInfo();
316:         return tokens; // <= FOUND
317:     }
```
['[145](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L145-L154)']
```solidity
145:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
146:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
147:         if (positionInfo.positionTypeId == PRISMA_POSITION_ID) {
148:             (address zap, address troveManager) = abi.decode(positionInfo.data, (address, address));
149:             IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();
150:             address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;
151:             address debTtoken = ITroveManager(troveManager).debtToken();
152:             (uint256 collateralBalance, uint256 debtBalance) =
153:                 ITroveManager(troveManager).getTroveCollAndDebt(address(this));
154:             return _getValue(collateral, base, collateralBalance) - _getValue(debTtoken, base, debtBalance); // <= FOUND
155:         }
156:     }
```
['[164](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L164-L172)']
```solidity
164:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
165:         (address zap, address troveManager) = abi.decode(data, (address, address));
166:         IBorrowerOperations borrowerOperations = IStakeNTroveZap(zap).borrowerOps();
167:         address collateral = borrowerOperations.troveManagersData(troveManager).collateralToken;
168:         address debTtoken = ITroveManager(troveManager).debtToken();
169:         address[] memory tokens = new address[](2);
170:         tokens[0] = collateral;
171:         tokens[1] = debTtoken;
172:         return tokens; // <= FOUND
173:     }
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L71-L76)']
```solidity
71:     function getData(address siloToken)
72:         public
73:         view
74:         returns (uint256 userLTV, uint256 LiquidationThreshold, bool isSolvent)
75:     {
76:         return SolvencyV2.getData(ISilo(siloRepository.getSilo(siloToken)), address(this), minimumHealthFactor); // <= FOUND
77:     }
```
['[130](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L130-L140)']
```solidity
130:     function isSiloEmpty(ISilo silo) public view returns (bool) {
131:         (, IBaseSilo.AssetStorage[] memory assetsS) = silo.getAssetsWithState();
132:         for (uint256 i = 0; i < assetsS.length; i++) {
133:             if (
134:                 IERC20(assetsS[i].collateralToken).balanceOf(address(this))
135:                     + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0
136:             ) {
137:                 return false; // <= FOUND
138:             }
139:         }
140:         return true; // <= FOUND
141:     }
```
['[143](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L143-L147)']
```solidity
143:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
144:         (address siloToken) = abi.decode(data, (address));
145:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
146:         (address[] memory assets,) = silo.getAssetsWithState();
147:         return assets; // <= FOUND
148:     }
```
['[110](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L110-L120)']
```solidity
110:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
111:         PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
112:         uint256 poolId = abi.decode(pBP.data, (uint256));
113:         address lpAddress = LPStaking.poolInfo(poolId).lpToken;
114:         uint256 lpAmount = LPStaking.userInfo(poolId, address(this)).amount + IERC20(lpAddress).balanceOf(address(this));
115:         if (lpAmount == 0) {
116:             return 0; // <= FOUND
117:         }
118:         address underlyingToken = IStargatePool(lpAddress).token();
119:         uint256 underlyingAmount = IStargatePool(lpAddress).amountLPtoLD(lpAmount);
120:         return _getValue(underlyingToken, base, underlyingAmount); // <= FOUND
121:     }
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L123-L128)']
```solidity
123:     function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
124:         uint256 poolId = abi.decode(data, (uint256));
125:         address lpAddress = LPStaking.poolInfo(poolId).lpToken;
126:         address[] memory tokens = new address[](1);
127:         tokens[0] = IStargatePool(lpAddress).token();
128:         return tokens; // <= FOUND
129:     }
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L116-L118)']
```solidity
116:     function getCurrentLiquidity(uint256 tokenId) public view returns (uint128, address, address) {
117:         (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId);
118:         return (liquidity, token0, token1); // <= FOUND
119:     }
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L124-L125)']
```solidity
124:     function domainSeparatorV4() public view returns (bytes32) {
125:         return _domainSeparatorV4(); // <= FOUND
126:     }
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L232-L238)']
```solidity
232:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
233:         if (positionTypeId == 0) {
234:             address[] memory tokens = new address[](1);
235:             tokens[0] = abi.decode(data, (address));
236:             return tokens; // <= FOUND
237:         }
238:         return _getUnderlyingTokens(positionTypeId, data); // <= FOUND
239:     }
```
['[249](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L249-L250)']
```solidity
249:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
250:         return _getPositionTVL(p, baseToken); // <= FOUND
251:     }
```
['[253](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L253-L260)']
```solidity
253:     function _getValue(address token, address baseToken, uint256 amount) internal view returns (uint256) {
254:         if (token == baseToken) {
255:             return amount; // <= FOUND
256:         }
257:         if (amount == 0) {
258:             return 0; // <= FOUND
259:         }
260:         return valueOracle.getValue(token, baseToken, amount); // <= FOUND
261:     }
```
['[263](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L263-L264)']
```solidity
263:     function _getUnderlyingTokens(uint256, bytes memory) public view virtual returns (address[] memory) {
264:         return new address[](0); // <= FOUND
265:     }
```
['[271](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L271-L272)']
```solidity
271:     function _getPositionTVL(HoldingPI memory, address) public view virtual returns (uint256 tvl) {
272:         return 0; // <= FOUND
273:     }
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L71-L72)']
```solidity
71:     function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
72:         return 0; // <= FOUND
73:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L75-L76)']
```solidity
75:     function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
76:         return new address[](0); // <= FOUND
77:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L51-L56)']
```solidity
51:     function _getPositionTVL(HoldingPI memory position, address) public view override returns (uint256) {
52:         uint256 positionTypeId = registry.getPositionBP(vaultId, position.positionId).positionTypeId;
53:         if (positionTypeId == OMNICHAIN_POSITION_ID) {
54:             return (abi.decode(position.additionalData, (uint256))); // <= FOUND
55:         }
56:         return 0; // <= FOUND
57:     }
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L19-L21)']
```solidity
19:     function getTVL() public view returns (uint256) {
20:         (, address baseToken) = registry.getVaultAddresses(vaultId);
21:         return TVLHelper.getTVL(vaultId, registry, baseToken); // <= FOUND
22:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L33-L40)']
```solidity
33:     function _getPositionTVL(HoldingPI memory position, address base) public view override returns (uint256) {
34:         PositionBP memory bp = registry.getPositionBP(vaultId, position.positionId);
35:         if (bp.positionTypeId == 0) {
36:             address token = abi.decode(bp.data, (address));
37:             uint256 amount = IERC20(token).balanceOf(address(this));
38:             return _getValue(token, base, amount); // <= FOUND
39:         }
40:         return 0; // <= FOUND
41:     }
```
['[110](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L110-L124)']
```solidity
110:     function verifySwapData(SwapRequest calldata _request) public view override returns (bool) {
111:         bytes4 selector = bytes4(_request.data[:4]);
112:         if (selector != LI_FI_GENERIC_SWAP_SELECTOR) {
113:             revert InvalidSelector();
114:         }
115:         (address sendingAssetId, uint256 amount, address from, address receivingAssetId, uint256 receivingAmount) =
116:             ILiFi(lifi).extractGenericSwapParameters(_request.data);
117: 
118:         if (from != _request.from) revert InvalidReceiver(from, _request.from);
119:         if (receivingAmount < _request.minAmount) revert InvalidMinAmount();
120:         if (sendingAssetId != _request.inputToken) revert InvalidInputToken();
121:         if (receivingAssetId != _request.outputToken) revert InvalidOutputToken();
122:         if (amount != _request.amount) revert InvalidAmount();
123: 
124:         return true; // <= FOUND
125:     }
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L150-L162)']
```solidity
150:     function verifyBridgeData(BridgeRequest calldata _request) public view override returns (bool) {
151:         ILiFi.BridgeData memory bridgeData = ILiFi(lifi).extractBridgeData(_request.data);
152: 
153:         if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted();
154:         if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId();
155:         if (bridgeData.sendingAssetId != _request.inputToken) revert InvalidFromToken();
156:         if (bridgeData.receiver != _request.receiverAddress) {
157:             revert InvalidReceiver(bridgeData.receiver, _request.receiverAddress);
158:         }
159:         if (bridgeData.minAmount > _request.amount) revert InvalidMinAmount();
160:         if (bridgeData.destinationChainId != _request.destChainId) revert InvalidToChainId();
161: 
162:         return true; // <= FOUND
163:     }
```
['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L14-L33)']
```solidity
14:     function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
15:         uint256 totalTVL;
16:         uint256 totalDebt;
17:         HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
18:         for (uint256 i = 0; i < positions.length; i++) {
19:             if (positions[i].calculatorConnector == address(0)) {
20:                 continue;
21:             }
22:             uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);
23:             bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);
24:             if (isPositionDebt) {
25:                 totalDebt += tvl;
26:             } else {
27:                 totalTVL += tvl;
28:             }
29:         }
30:         if (totalTVL < totalDebt) {
31:             return 0; // <= FOUND
32:         }
33:         return (totalTVL - totalDebt); // <= FOUND
34:     }
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L41-L52)']
```solidity
41:     function getLatestUpdateTime(uint256 vaultId, PositionRegistry registry) public view returns (uint256) {
42:         uint256 latestUpdateTime;
43:         HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
44:         for (uint256 i = 0; i < positions.length; i++) {
45:             if (latestUpdateTime == 0 || positions[i].positionTimestamp < latestUpdateTime) {
46:                 latestUpdateTime = positions[i].positionTimestamp;
47:             }
48:         }
49:         if (latestUpdateTime == 0) {
50:             latestUpdateTime = block.timestamp;
51:         }
52:         return latestUpdateTime; // <= FOUND
53:     }
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L78)']
```solidity
71:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
72:         if (asset == baseToken || amount == 0) {
73:             return amount; // <= FOUND
74:         }
75: 
76:         address[] memory sources = priceRoutes[asset][baseToken];
77: 
78:         return _getValue(asset, baseToken, amount, sources); // <= FOUND
79:     }
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L92)']
```solidity
81:     function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
82:         internal
83:         view
84:         returns (uint256 value)
85:     {
86:         uint256 initialValue = amount;
87:         address quotingToken = asset;
88:         for (uint256 i = 0; i < sources.length; i++) {
89:             initialValue = _getValue(asset, sources[i], initialValue);
90:             quotingToken = sources[i];
91:         }
92:         return _getValue(quotingToken, baseToken, initialValue); // <= FOUND
93:     }
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L95-L109)']
```solidity
95:     function _getValue(address quotingToken, address baseToken, uint256 amount) internal view returns (uint256) {
96:         INoyaValueOracle oracle = priceSource[quotingToken][baseToken];
97:         if (address(oracle) == address(0)) {
98:             oracle = priceSource[baseToken][quotingToken];
99:         }
100:         if (address(oracle) == address(0)) {
101:             oracle = defaultPriceSource[baseToken];
102:         }
103:         if (address(oracle) == address(0)) {
104:             oracle = defaultPriceSource[quotingToken];
105:         }
106:         if (address(oracle) == address(0)) {
107:             revert NoyaOracle_PriceOracleUnavailable(quotingToken, baseToken);
108:         }
109:         return oracle.getValue(quotingToken, baseToken, amount); // <= FOUND
110:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L84-L95)']
```solidity
84:     function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
85:         if (asset == baseToken) {
86:             return amount; // <= FOUND
87:         }
88: 
89:         (address primarySource, bool isPrimaryInverse) = getSourceOfAsset(asset, baseToken);
90:         if (primarySource == address(0)) {
91:             revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(asset, baseToken, primarySource);
92:         }
93:         address decimalsSource = isPrimaryInverse ? baseToken : asset;
94:         decimalsSource = decimalsSource == ETH || decimalsSource == USD ? primarySource : decimalsSource;
95:         return getValueFromChainlinkFeed( // <= FOUND
96:             AggregatorV3Interface(primarySource), amount, getTokenDecimals(decimalsSource), isPrimaryInverse
97:         );
98:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L109-L128)']
```solidity
109:     function getValueFromChainlinkFeed(
110:         AggregatorV3Interface source,
111:         uint256 amountIn,
112:         uint256 sourceTokenUnit,
113:         bool isInverse
114:     ) public view returns (uint256) {
115:         int256 price;
116:         uint256 updatedAt;
117:         (, price,, updatedAt,) = source.latestRoundData();
118:         uint256 uintprice = uint256(price);
119:         if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
120:             revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
121:         }
122:         if (price <= 0) {
123:             revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
124:         }
125:         if (isInverse) {
126:             return (amountIn * sourceTokenUnit) / uintprice; // <= FOUND
127:         }
128:         return (amountIn * uintprice) / (sourceTokenUnit); // <= FOUND
129:     }
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L132-L134)']
```solidity
132:     function getTokenDecimals(address token) public view returns (uint256) {
133:         uint256 decimals = IERC20Metadata(token).decimals();
134:         return 10 ** decimals; // <= FOUND
135:     }
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L137-L143)']
```solidity
137:     function getSourceOfAsset(address asset, address baseToken) public view returns (address source, bool isInverse) {
138:         if (assetsSources[asset][baseToken] != address(0)) {
139:             return (assetsSources[asset][baseToken], false); // <= FOUND
140:         } else if (assetsSources[baseToken][asset] != address(0)) {
141:             return (assetsSources[baseToken][asset], true); // <= FOUND
142:         }
143:         return (address(0), false); // <= FOUND
144:     }
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L5-L10)']
```solidity
5:     function latestRoundData()
6:         external
7:         view
8:         returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)
9:     {
10:         return (0, 1e18, 0, block.timestamp, 0); // <= FOUND
11:     }
```
['[477](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L477-L482)']
```solidity
477:     function calculatePositionId(address calculatorConnector, uint256 positionTypeId, bytes memory data)
478:         public
479:         pure
480:         returns (bytes32)
481:     {
482:         return keccak256(abi.encode(calculatorConnector, positionTypeId, data)); // <= FOUND
483:     }
```
['[128](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L128-L129)']
```solidity
128:     function _getUnderlyingTokens(uint256, bytes memory) public pure override returns (address[] memory) {
129:         return new address[](0); // <= FOUND
130:     }
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L141-L142)']
```solidity
141:     function isInAsset(uint16 assetsIn, uint8 assetOffset) public pure returns (bool) {
142:         return (assetsIn & (uint16(1) << assetOffset) != 0); // <= FOUND
143:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L64-L65)']
```solidity
64:     function onERC721Received(address, address, uint256, bytes memory) external pure override returns (bytes4) {
65:         return this.onERC721Received.selector; // <= FOUND
66:     }
```
['[152](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L152-L155)']
```solidity
152:     function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
153:         address[] memory tokens = new address[](2);
154:         (tokens[0], tokens[1]) = abi.decode(data, (address, address));
155:         return tokens; // <= FOUND
156:     }
```
['[189](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L189-L190)']
```solidity
189:     function _isNative(IERC20 token) internal pure returns (bool isNative) {
190:         return address(token) == address(0); // <= FOUND
191:     }
```


</details>

## [Gas-8] x + y is more efficient than using += for state variables (likewise for -=)

### Resolution 
In instances found where either += or -= are used against state variables use x = x + y instead

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[545](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L545-L566)']
```solidity
545:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
546:         uint256 amountAskedForWithdraw_temp = 0;
547:         uint256 neededAssets = neededAssetsForWithdraw();
548:         for (uint256 i = 0; i < retrieveData.length; i++) {
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
566:         amountAskedForWithdraw += amountAskedForWithdraw_temp; // <= FOUND
567:         if (amountAskedForWithdraw_temp > neededAssets) {
568:             revert NoyaAccounting_INVALID_AMOUNT();
569:         }
570:     }
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L283)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     {
260:         uint256 firstTemp = depositQueue.first;
261:         uint64 i = 0;
262:         uint256 processedBaseTokenAmount = 0;
263: 
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1;
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1;
280:         }
281:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount;
282: 
283:         totalDepositedAmount += processedBaseTokenAmount; // <= FOUND
284: 
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         } else {
292:             revert NoyaAccounting_INVALID_CONNECTOR();
293:         }
294: 
295:         depositQueue.first = firstTemp;
296:     }
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L433)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
394:         if (currentWithdrawGroup.isFullfilled == false) {
395:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
396:         }
397:         uint64 i = 0;
398:         uint256 firstTemp = withdrawQueue.first;
399: 
400:         uint256 withdrawFeeAmount = 0;
401:         uint256 processedBaseTokenAmount = 0;
402:         
403:         while (
404:             currentWithdrawGroup.lastId > firstTemp
405:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
406:                 && i < maxIterations
407:         ) {
408:             i += 1;
409:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
410:             uint256 shares = data.shares;
411:             
412:             uint256 baseTokenAmount =
413:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
414: 
415:             withdrawRequestsByAddress[data.owner] -= shares;
416:             _burn(data.owner, shares);
417: 
418:             processedBaseTokenAmount += data.amount;
419:             {
420:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
421:                 withdrawFeeAmount += feeAmount;
422:                 baseTokenAmount = baseTokenAmount - feeAmount;
423:             }
424: 
425:             baseToken.safeTransfer(data.receiver, baseTokenAmount);
426:             emit ExecuteWithdraw(
427:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
428:             );
429:             delete withdrawQueue.queue[firstTemp];
430:             
431:             firstTemp += 1;
432:         }
433:         totalWithdrawnAmount += processedBaseTokenAmount; // <= FOUND
434: 
435:         if (withdrawFeeAmount > 0) {
436:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);
437:         }
438:         withdrawQueue.first = firstTemp;
439:         
440:         if (currentWithdrawGroup.lastId == firstTemp) {
441:             delete currentWithdrawGroup;
442:         }
443:     }
```


</details>

## [Gas-9] There is a 32 byte length threshold for error strings, strings longer than this consume more gas

### Resolution 
In require statements found which are longer than 32 characters, shorten these to 32 character or less

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L92)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) {
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) {
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
82:                 require(success, "BalancerFlashLoan: Flash loan failed"); // <= FOUND
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) {
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) {
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens"); // <= FOUND
93:         }
94:     }
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L84)']
```solidity
77:     function performSwapAction(address caller, SwapRequest calldata _request)
78:         external
79:         payable
80:         override
81:         onlyHandler
82:         returns (uint256)
83:     {
84:         require(verifySwapData(_request), "LifiImplementation: INVALID_SWAP_DATA"); // <= FOUND
85:         uint256 balanceOut0 = 0;
86:         if (_request.outputToken == address(0)) {
87:             balanceOut0 = address(_request.from).balance;
88:         } else {
89:             balanceOut0 = IERC20(_request.outputToken).balanceOf(_request.from);
90:         }
91:         _forward(IERC20(_request.inputToken), _request.from, _request.amount, caller, _request.data, _request.routeId);
92:         uint256 balanceOut1 = 0;
93:         if (_request.outputToken == address(0)) {
94:             balanceOut1 = address(_request.from).balance;
95:         } else {
96:             balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);
97:         }
98: 
99:         emit Swapped(balanceOut0, balanceOut1, _request.outputToken);
100: 
101:         return balanceOut1 - balanceOut0;
102:     }
```


</details>

## [Gas-10] Usage of smaller uint/int types causes overhead

### Resolution 
When using a smaller int/uint type it first needs to be converted to it's 258 bit counterpart to be operated, this increases the gass cost and thus should be avoided. However it does make sense to use smaller int/uint values within structs provided you pack the struct properly.

Num of instances: 29

### Findings 


<details><summary>Click to show findings</summary>

['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L95-L97)']
```solidity
95:     function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) {
96:         IComet.UserBasic memory userBasic = comet.userBasic(address(this));
97:         uint16 assetsIn = userBasic.assetsIn; // <= FOUND
98:         uint256 basePrice = comet.getPrice(comet.baseTokenPriceFeed());
99:         uint256 baseScale = comet.baseScale();
100:         if (userBasic.principal > 0) {
101:             uint256 principalInBase = uint256(uint104(userBasic.principal));
102:             CollValue += principalInBase;
103:         }
104:         uint8 numberOfAssets = comet.numAssets(); // <= FOUND
105: 
106:         
107:         for (uint8 i; i < numberOfAssets; ++i) { // <= FOUND
108:             if (isInAsset(assetsIn, i)) {
109:                 IComet.AssetInfo memory info = comet.getAssetInfo(i);
110: 
111:                 
112:                 (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset);
113: 
114:                 
115:                 uint256 collateralPriceInVirtualBase = comet.getPrice(info.priceFeed);
116: 
117:                 uint256 collateralValueInVirtualBase =
118:                     collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice;
119:                 if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;
120:                 else CollValue += collateralValueInVirtualBase;
121:             } 
122:         }
123:     }
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L141-L141)']
```solidity
141:     function isInAsset(uint16 assetsIn, uint8 assetOffset) public pure returns (bool) { // <= FOUND
142:         return (assetsIn & (uint16(1) << assetOffset) != 0);
143:     }
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L132-L134)']
```solidity
132:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {
133:         IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));
134:         uint8 tokenIndex; // <= FOUND
135:         for (uint256 i = 0; i < earnedInfo.length; i++) {
136:             if (earnedInfo[i].earned != 0) {
137:                 tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken));
138:                 rewardContract.getReward(address(this), tokenIndex);
139:             }
140:         }
141:         emit ClaimBoostedPositionRewards(rewardContract);
142:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L63-L63)']
```solidity
63:     function setThreshold(uint8 _threshold) public onlyOwner { // <= FOUND
64:         require(_threshold <= numOwners && _threshold > 1);
65:         threshold = _threshold;
66:         emit UpdateThreshold(_threshold);
67:     }
```
['[15](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L15-L15)']
```solidity
15: uint8 public threshold; // <= FOUND
```
['[127](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L127-L140)']
```solidity
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
128:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
129:         uint256 tokenId = abi.decode(p.data, (uint256));
130:         (address token0, address token1) = abi.decode(positionInfo.data, (address, address));
131:         uint256 amount0;
132:         uint256 amount1;
133:         (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24)); // <= FOUND
134:         {
135:             IUniswapV3Pool pool = IUniswapV3Pool(factory.getPool(token0, token1, fee));
136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));
137: 
138:             (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key); // <= FOUND
139: 
140:             (uint160 sqrtPriceX96,,,,,,) = pool.slot0(); // <= FOUND
141:             (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
142:                 sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity
143:             );
144:             amount0 += tokensOwed0;
145:             amount1 += tokensOwed1;
146:         }
147: 
148:         tvl += valueOracle.getValue(token0, base, amount0);
149:         tvl += valueOracle.getValue(token1, base, amount1);
150:     }
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L48-L48)']
```solidity
48:     function addPool(address tokenIn, address baseToken, uint24 fee) external onlyMaintainer { // <= FOUND
49:         address pool = IUniswapV3Factory(factory).getPool(tokenIn, baseToken, fee);
50:         require(pool != address(0), "pool doesn't exist");
51:         assetToBaseToPool[tokenIn][baseToken] = pool;
52:         emit PoolsForAsset(tokenIn, baseToken, pool);
53:     }
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L60-L61)']
```solidity
60:     function getValue(address tokenIn, address baseToken, uint256 amount) public view returns (uint256 _amountOut) {
61:         uint128 amountIn128 = uint128(amount); // <= FOUND
62:         address pool = assetToBaseToPool[tokenIn][baseToken];
63:         if (pool == address(0)) {
64:             pool = assetToBaseToPool[baseToken][tokenIn];
65:         }
66:         if (pool == address(0)) revert INoyaOracle_ValueOracleUnavailable(tokenIn, baseToken);
67: 
68:         
69:         uint32[] memory secondsAgos = new uint32[](2);
70:         secondsAgos[0] = period;
71:         secondsAgos[1] = 0;
72: 
73:         
74:         (int56[] memory tickCumulatives,) = IUniswapV3Pool(pool).observe(secondsAgos);
75: 
76:         
77:         int56 tickCumulativesDelta = tickCumulatives[1] - tickCumulatives[0]; // <= FOUND
78: 
79:         
80:         
81:         int24 timeWeightedAverageTick = int24(tickCumulativesDelta / int56(int32(period))); // <= FOUND
82:         if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {
83:             timeWeightedAverageTick--;
84:         }
85:         _amountOut = OracleLibrary.getQuoteAtTick(timeWeightedAverageTick, amountIn128, tokenIn, baseToken);
86:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L40-L40)']
```solidity
40:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner { // <= FOUND
41:         require(lzHelperAddress != address(0));
42:         chainInfo[lzChainId] = ChainInfo(chainId, lzHelperAddress);
43:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L51-L51)']
```solidity
51:     function setChainInfo(uint256 chainId, uint32 lzChainId, address lzHelperAddress) public onlyOwner { // <= FOUND
52:         require(lzHelperAddress != address(0));
53:         chainInfo[chainId] = ChainInfo(lzChainId, lzHelperAddress);
54:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L75-L78)']
```solidity
75:     function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
76:         if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
77: 
78:         uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId; // <= FOUND
79:         bytes memory data = abi.encode(vaultId, tvl, updateTime);
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); 
81:     }
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L38-L38)']
```solidity
38:     function setPeriod(uint32 _period) external onlyMaintainer { // <= FOUND
39:         if (_period == 0) revert INoyaValueOracle_InvalidInput();
40:         period = _period;
41:         emit NewPeriod(_period);
42:     }
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L24-L24)']
```solidity
24: uint32 constant TVL_UPDATE = 1; // <= FOUND
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L19-L19)']
```solidity
19: uint32 public period = 1800; // <= FOUND
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L223-L225)']
```solidity
223:     function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
224:         uint256 middleTemp = depositQueue.middle;
225:         uint64 i = 0; // <= FOUND
226: 
227:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
228: 
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
231:                 && i < maxIterations
232:         ) {
233:             i += 1;
234:             DepositRequest storage data = depositQueue.queue[middleTemp];
235: 
236:             uint256 shares = previewDeposit(data.amount);
237:             data.shares = shares;
238:             data.calculationTime = block.timestamp;
239:             emit CalculateDeposit(
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
242: 
243:             middleTemp += 1;
244:         }
245: 
246:         depositQueue.middle = middleTemp;
247:     }
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L261)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     {
260:         uint256 firstTemp = depositQueue.first;
261:         uint64 i = 0; // <= FOUND
262:         uint256 processedBaseTokenAmount = 0;
263: 
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1;
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1;
280:         }
281:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount;
282: 
283:         totalDepositedAmount += processedBaseTokenAmount;
284: 
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         } else {
292:             revert NoyaAccounting_INVALID_CONNECTOR();
293:         }
294: 
295:         depositQueue.first = firstTemp;
296:     }
```
['[325](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L325-L327)']
```solidity
325:     function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
326:         uint256 middleTemp = withdrawQueue.middle;
327:         uint64 i = 0; // <= FOUND
328:         uint256 processedShares = 0;
329:         uint256 assetsNeededForWithdraw = 0;
330:         uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);
331: 
332:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) {
333:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
334:         }
335:         while (
336:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
337:                 && i < maxIterations
338:         ) {
339:             i += 1;
340:             WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
341:             uint256 assets = previewRedeem(data.shares);
342:             data.amount = assets;
343:             data.calculationTime = block.timestamp;
344:             assetsNeededForWithdraw += assets;
345:             processedShares += data.shares;
346:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);
347: 
348:             middleTemp += 1;
349:         }
350:         currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
351:         withdrawQueue.middle = middleTemp;
352:     }
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L397)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
394:         if (currentWithdrawGroup.isFullfilled == false) {
395:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
396:         }
397:         uint64 i = 0; // <= FOUND
398:         uint256 firstTemp = withdrawQueue.first;
399: 
400:         uint256 withdrawFeeAmount = 0;
401:         uint256 processedBaseTokenAmount = 0;
402:         
403:         while (
404:             currentWithdrawGroup.lastId > firstTemp
405:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
406:                 && i < maxIterations
407:         ) {
408:             i += 1;
409:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
410:             uint256 shares = data.shares;
411:             
412:             uint256 baseTokenAmount =
413:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;
414: 
415:             withdrawRequestsByAddress[data.owner] -= shares;
416:             _burn(data.owner, shares);
417: 
418:             processedBaseTokenAmount += data.amount;
419:             {
420:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
421:                 withdrawFeeAmount += feeAmount;
422:                 baseTokenAmount = baseTokenAmount - feeAmount;
423:             }
424: 
425:             baseToken.safeTransfer(data.receiver, baseTokenAmount);
426:             emit ExecuteWithdraw(
427:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
428:             );
429:             delete withdrawQueue.queue[firstTemp];
430:             
431:             firstTemp += 1;
432:         }
433:         totalWithdrawnAmount += processedBaseTokenAmount;
434: 
435:         if (withdrawFeeAmount > 0) {
436:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);
437:         }
438:         withdrawQueue.first = firstTemp;
439:         
440:         if (currentWithdrawGroup.lastId == firstTemp) {
441:             delete currentWithdrawGroup;
442:         }
443:     }
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/WETH_Oracle.sol#L5-L8)']
```solidity
5:     function latestRoundData()
6:         external
7:         view
8:         returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound) // <= FOUND
9:     {
10:         return (0, 1e18, 0, block.timestamp, 0);
11:     }
```
['[297](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L297-L302)']
```solidity
297:     function estimateWithdrawAmount(ICurveSwap curvePool, uint256 amount, uint256 index)
298:         public
299:         view
300:         returns (uint256)
301:     {
302:         int128 tokenIndex = int128(uint128(index)); // <= FOUND
303:         return curvePool.calc_withdraw_one_coin(amount, tokenIndex);
304:     }
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L30-L30)']
```solidity
30:     function deposit(address _token, uint256 _amount, uint128 _accountId) public onlyManager { // <= FOUND
31:         
32:         _approveOperations(_token, address(SNXCoreProxy), _amount);
33: 
34:         SNXCoreProxy.deposit(_accountId, _token, _amount);
35:         registry.updateHoldingPosition(
36:             vaultId,
37:             registry.calculatePositionId(address(this), SNX_POSITION_ID, ""),
38:             abi.encode(_accountId, _token),
39:             "",
40:             false
41:         );
42:         
43:         _updateTokenInRegistry(_token);
44:     }
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L46-L46)']
```solidity
46:     function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager { // <= FOUND
47:         
48:         _approveOperations(_token, address(SNXCoreProxy), _amount);
49:         SNXCoreProxy.withdraw(_accountId, _token, _amount);
50:         (uint256 c,,) = SNXCoreProxy.getAccountCollateral(_accountId, _token);
51:         if (c == 0) {
52:             registry.updateHoldingPosition(
53:                 vaultId,
54:                 registry.calculatePositionId(address(this), SNX_POSITION_ID, ""),
55:                 abi.encode(_accountId, _token),
56:                 "",
57:                 true
58:             );
59:         }
60:         
61:         _updateTokenInRegistry(_token);
62:     }
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L68-L76)']
```solidity
68:     function delegateIntoPreferredPool(
69:         uint128 _accountId, // <= FOUND
70:         address collateralType,
71:         uint256 newCollateralAmountD18,
72:         uint256 leverage
73:     ) public onlyManager {
74:         
75: 
76:         uint128 poolId = SNXCoreProxy.getPreferredPool(); // <= FOUND
77: 
78:         SNXCoreProxy.delegateCollateral(_accountId, poolId, collateralType, newCollateralAmountD18, leverage);
79:     }
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L81-L83)']
```solidity
81:     function delegateIntoApprovedPool(
82:         uint256 poolIndex,
83:         uint128 _accountId, // <= FOUND
84:         address collateralType,
85:         uint256 newCollateralAmountD18,
86:         uint256 leverage
87:     ) public onlyManager {
88:         uint256[] memory poolIds = SNXCoreProxy.getApprovedPools();
89:         SNXCoreProxy.delegateCollateral(
90:             _accountId, uint128(poolIds[poolIndex]), collateralType, newCollateralAmountD18, leverage
91:         );
92:     }
```
['[94](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L94-L94)']
```solidity
94:     function claimRewards(uint128 accountId, uint128 poolId, address collateralType, address distributor) // <= FOUND
95:         public
96:         onlyManager
97:     {
98:         SNXCoreProxy.claimRewards(accountId, poolId, collateralType, distributor);
99:         _updateTokenInRegistry(collateralType);
100:     }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L102-L105)']
```solidity
102:     function mintOrBurnSUSD(
103:         uint256 _amount,
104:         uint128 _accountId, // <= FOUND
105:         uint128 poolId, // <= FOUND
106:         address collateralType,
107:         bool mintOrBurn
108:     ) public onlyManager {
109:         
110:         address usdToken = SNXCoreProxy.getUsdToken();
111:         if (mintOrBurn) {
112:             SNXCoreProxy.mintUsd(_accountId, poolId, collateralType, _amount);
113:         } else {
114:             _approveOperations(usdToken, address(SNXCoreProxy), _amount);
115:             SNXCoreProxy.burnUsd(_accountId, poolId, collateralType, _amount);
116:         }
117:         _updateTokenInRegistry(collateralType);
118:         _updateTokenInRegistry(usdToken);
119:     }
```
['[121](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L121-L122)']
```solidity
121:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
122:         (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address)); // <= FOUND
123:         (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =
124:             SNXCoreProxy.getAccountCollateral(accountId, collateralType);
125:         tvl = _getValue(collateralType, base, totalDeposited + totalAssigned);
126:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L63-L64)']
```solidity
63:     function decreasePosition(DecreaseLiquidityParams memory p) external onlyManager nonReentrant {
64:         (uint128 currentLiquidity, address token0, address token1) = getCurrentLiquidity(p.tokenId); // <= FOUND
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
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L116-L117)']
```solidity
116:     function getCurrentLiquidity(uint256 tokenId) public view returns (uint128, address, address) {
117:         (,, address token0, address token1,,,, uint128 liquidity,,,,) = positionManager.positions(tokenId); // <= FOUND
118:         return (liquidity, token0, token1);
119:     }
```


</details>

## [Gas-11] Default bool values are manually reset

### Resolution 
Using .delete is better than resetting a Solidity variable to its default value manually because it frees up storage space on the Ethereum blockchain, resulting in gas cost savings. 

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L49)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner { // <= FOUND
43:         uint256 numOwnersTemp = numOwners;
44:         for (uint256 i = 0; i < _owners.length; i++) {
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) {
46:                 isOwner[_owners[i]] = true;
47:                 numOwnersTemp++;
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
49:                 isOwner[_owners[i]] = false; // <= FOUND
50:                 numOwnersTemp--;
51:             }
52:         }
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
54:         numOwners = numOwnersTemp;
55:         emit UpdateOwners(_owners, addOrRemove);
56:     }
```


</details>

## [Gas-12] For loops in public or external functions should be avoided due to high gas costs and possible DOS

### Resolution 
In Solidity, for loops can potentially cause Denial of Service (DoS) attacks if not handled carefully. DoS attacks can occur when an attacker intentionally exploits the gas cost of a function, causing it to run out of gas or making it too expensive for other users to call. Below are some scenarios where for loops can lead to DoS attacks: Nested for loops can become exceptionally gas expensive and should be used sparingly

Num of instances: 25

### Findings 


<details><summary>Click to show findings</summary>

['[105](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L105-L137)']
```solidity
105:     function addVault(
106:         uint256 vaultId,
107:         address _accountingManager,
108:         address _baseToken,
109:         address _governer,
110:         address _maintainer,
111:         address _maintainerWithoutTimelock,
112:         address _keeperContract,
113:         address _watcher,
114:         address _emergency,
115:         address[] calldata _trustedTokens
116:     ) external onlyRole(MAINTAINER_ROLE) {
117:         if (vaults[vaultId].accountManager != address(0)) revert AlreadyExists();
118:         Vault storage vault = vaults[vaultId];
119:         require(_governer != address(0));
120:         require(_accountingManager != address(0));
121:         require(_baseToken != address(0));
122:         require(_maintainer != address(0));
123:         require(_keeperContract != address(0));
124:         require(_watcher != address(0));
125: 
126:         vault.accountManager = _accountingManager;
127:         vault.baseToken = _baseToken;
128:         vault.governer = _governer;
129:         vault.maintainer = _maintainer;
130:         vault.maintainerWithoutTimeLock = _maintainerWithoutTimelock;
131:         vault.keeperContract = _keeperContract;
132:         vault.watcherContract = _watcher;
133:         vault.emergency = _emergency;
134:         
135:         vault.connectors[vault.accountManager].enabled = true;
136:         vault.enabled = true;
137:         for (uint256 i = 0; i < _trustedTokens.length; i++) { // <= FOUND
138:             vault.connectors[vault.accountManager].trustedTokens[_trustedTokens[i]] = true;
139:         }
140:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max));
141:         emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens);
142:         emit VaultAddressesChanged(
143:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
144:         );
145:     }
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L185-L191)']
```solidity
185:     function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds)
186:         external
187:         onlyVaultMaintainer(vaultId)
188:         vaultExists(vaultId)
189:     {
190:         Vault storage vault = vaults[vaultId];
191:         for (uint256 i = 0; i < _connectorAddresses.length; i++) { // <= FOUND
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]);
194:         }
195:     }
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L203-L210)']
```solidity
203:     function updateConnectorTrustedTokens(
204:         uint256 vaultId,
205:         address _connectorAddress,
206:         address[] calldata _tokens,
207:         bool trusted
208:     ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
209:         Vault storage vault = vaults[vaultId];
210:         for (uint256 i = 0; i < _tokens.length; i++) { // <= FOUND
211:             vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = trusted;
212:         }
213:         emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted);
214:     }
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L232-L247)']
```solidity
232:     function addTrustedPosition(
233:         uint256 vaultId,
234:         uint256 _positionTypeId,
235:         address calculatorConnector,
236:         bool onlyOwner,
237:         bool _isDebt,
238:         bytes calldata _data,
239:         bytes calldata _additionalData
240:     ) external onlyVaultMaintainerWithoutTimeLock(vaultId) vaultExists(vaultId) nonReentrant {
241:         Vault storage vault = vaults[vaultId];
242:         bytes32 positionId = calculatePositionId(calculatorConnector, _positionTypeId, _data);
243:         {
244:             if (vault.trustedPositionsBP[positionId].isEnabled) revert AlreadyExists();
245:             if (vault.connectors[calculatorConnector].enabled == false) revert NotExist();
246:             address[] memory usingTokens = IConnector(calculatorConnector).getUnderlyingTokens(_positionTypeId, _data);
247:             for (uint256 i = 0; i < usingTokens.length; i++) { // <= FOUND
248:                 if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) {
249:                     revert TokenNotTrusted(usingTokens[i]);
250:                 }
251:             }
252: 
253:             vault.trustedPositionsBP[positionId] =
254:                 PositionBP(calculatorConnector, _positionTypeId, onlyOwner, true, _isDebt, _data, _additionalData);
255:         }
256:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data);
257:     }
```
['[260](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L260-L268)']
```solidity
260:     function removeTrustedPosition(uint256 vaultId, bytes32 _positionId)
261:         external
262:         onlyVaultMaintainer(vaultId)
263:         vaultExists(vaultId)
264:     {
265:         Vault storage vault = vaults[vaultId];
266:         if (!vault.trustedPositionsBP[_positionId].isEnabled) revert NotExist();
267:         uint256 length = vault.holdingPositions.length;
268:         for (uint256 i = 0; i < length; i++) { // <= FOUND
269:             if (vault.holdingPositions[i].positionId == _positionId) {
270:                 revert CannotRemovePosition(vaultId, _positionId);
271:             }
272:         }
273:         emit TrustedPositionRemoved(vaultId, _positionId);
274:         delete vault.trustedPositionsBP[_positionId];
275:     }
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L54-L89)']
```solidity
54:     function receiveFlashLoan(
55:         IERC20[] memory tokens,
56:         uint256[] memory amounts,
57:         uint256[] memory feeAmounts,
58:         bytes memory userData
59:     ) external override {
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData);
61:         require(msg.sender == address(vault));
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[]));
69:         (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
70:         if (!(caller == keeperContract)) {
71:             revert Unauthorized(caller);
72:         }
73:         if (registry.isAnActiveConnector(vaultId, receiver)) {
74:             for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
75:                 
76:                 tokens[i].safeTransfer(receiver, amounts[i]);
77:                 amounts[i] = amounts[i] + feeAmounts[i];
78:             }
79:             for (uint256 i = 0; i < destinationConnector.length; i++) { // <= FOUND
80:                 
81:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]);
82:                 require(success, "BalancerFlashLoan: Flash loan failed");
83:             }
84:             for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
85:                 
86:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), "");
87:             }
88:         }
89:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
90:             
91:             tokens[i].safeTransfer(msg.sender, amounts[i]);
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens");
93:         }
94:     }
```
['[132](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L132-L135)']
```solidity
132:     function claimBoostedPositionRewards(IMaverickReward rewardContract) external onlyManager nonReentrant {
133:         IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this));
134:         uint8 tokenIndex;
135:         for (uint256 i = 0; i < earnedInfo.length; i++) { // <= FOUND
136:             if (earnedInfo[i].earned != 0) {
137:                 tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken));
138:                 rewardContract.getReward(address(this), tokenIndex);
139:             }
140:         }
141:         emit ClaimBoostedPositionRewards(rewardContract);
142:     }
```
['[241](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L241-L244)']
```solidity
241:     function claimRewards(IPMarket market) external onlyManager nonReentrant {
242:         market.redeemRewards(address(this));
243:         address[] memory rewardTokens = market.getRewardTokens();
244:         for (uint256 i = 0; i < rewardTokens.length; i++) { // <= FOUND
245:             _updateTokenInRegistry(rewardTokens[i]);
246:         }
247:         emit ClaimRewards(address(market));
248:     }
```
['[169](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L169-L189)']
```solidity
169:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
170:         external
171:         override
172:         nonReentrant
173:     {
174:         if (!registry.isAddressTrusted(vaultId, msg.sender)) {
175:             revert IConnector_InvalidAddress(msg.sender);
176:         }
177: 
178:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
179:             
180:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this));
181:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this));
183:             if (_balanceAfter < amounts[i] + _balance) {
184:                 revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]);
185:             }
186:         }
187:         _addLiquidity(tokens, amounts, data); 
188: 
189:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
190:             _updateTokenInRegistry(tokens[i]); 
191:         }
192:         emit AddLiquidity(tokens, amounts, data);
193:     }
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L204-L211)']
```solidity
204:     function swapHoldings(
205:         address[] memory tokensIn,
206:         address[] memory tokensOut,
207:         uint256[] memory amountsIn,
208:         bytes[] memory swapData,
209:         uint256[] memory routeIds
210:     ) external onlyManager nonReentrant {
211:         for (uint256 i = 0; i < tokensIn.length; i++) { // <= FOUND
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]);
218:         }
219:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L40-L46)']
```solidity
40:     function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
41:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
42:             
43: 
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
45:         }
46:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
47:             _updateTokenInRegistry(tokens[i]); 
48:         }
49:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L55)']
```solidity
51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle)
52:         external
53:         onlyMaintainer
54:     {
55:         for (uint256 i = 0; i < oracle.length; i++) { // <= FOUND
56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
57:         }
58:         emit UpdatedAssetPriceSource(asset, baseToken, oracle);
59:     }
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L66-L70)']
```solidity
66:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources)
67:         external
68:         onlyMaintainer
69:     {
70:         for (uint256 i = 0; i < assets.length; i++) { // <= FOUND
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]);
73:         }
74:     }
```
['[545](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L545-L548)']
```solidity
545:     function retrieveTokensForWithdraw(RetrieveData[] calldata retrieveData) public onlyManager nonReentrant {
546:         uint256 amountAskedForWithdraw_temp = 0;
547:         uint256 neededAssets = neededAssetsForWithdraw();
548:         for (uint256 i = 0; i < retrieveData.length; i++) { // <= FOUND
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
566:         amountAskedForWithdraw += amountAskedForWithdraw_temp;
567:         if (amountAskedForWithdraw_temp > neededAssets) {
568:             revert NoyaAccounting_INVALID_AMOUNT();
569:         }
570:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L53-L54)']
```solidity
53:     function harvestAuraRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
54:         for (uint256 i = 0; i < rewardsPools.length; i++) { // <= FOUND
55:             IRewardPool baseRewardPool = IRewardPool(rewardsPools[i]);
56:             baseRewardPool.getReward();
57:         }
58:         _updateTokenInRegistry(address(AURA));
59:     }
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L64-L77)']
```solidity
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
77:         for (uint256 i = 0; i < tokens.length; i++) { // <= FOUND
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
79:         }
80: 
81:         IBalancerVault(balancerVault).joinPool(
82:             poolId,
83:             address(this), 
84:             address(this), 
85:             IBalancerVault.JoinPoolRequest(
86:                 tokens,
87:                 amounts,
88:                 abi.encode(
89:                     IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                     amountsWithoutBPT, 
91:                     minBPT 
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
```
['[221](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L221-L222)']
```solidity
221:     function harvestRewards(address[] calldata gauges) public onlyManager nonReentrant {
222:         for (uint256 i = 0; i < gauges.length; i++) { // <= FOUND
223:             IRewardsGauge(gauges[i]).claim_rewards(address(this));
224:         }
225:         _updateTokenInRegistry(CRV);
226:         emit HarvestRewards(gauges);
227:     }
```
['[233](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L233-L234)']
```solidity
233:     function harvestPrismaRewards(address[] calldata pools) public onlyManager nonReentrant {
234:         for (uint256 i = 0; i < pools.length; i++) { // <= FOUND
235:             IDepositToken(pools[i]).claimReward(address(this));
236:         }
237:         _updateTokenInRegistry(PRISMA);
238:         _updateTokenInRegistry(CRV);
239:         _updateTokenInRegistry(CVX);
240:         emit HarvestPrismaRewards(pools);
241:     }
```
['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L247-L248)']
```solidity
247:     function harvestConvexRewards(address[] calldata rewardsPools) public onlyManager nonReentrant {
248:         for (uint256 i = 0; i < rewardsPools.length; i++) { // <= FOUND
249:             IConvexBasicRewards baseRewardPool = IConvexBasicRewards(rewardsPools[i]);
250:             baseRewardPool.getReward(address(this), true);
251:         }
252:         _updateTokenInRegistry(CVX);
253:         _updateTokenInRegistry(CRV);
254:         emit HarvestConvexRewards(rewardsPools);
255:     }
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L62-L69)']
```solidity
62:     function executeCommands(
63:         address facade,
64:         address creditAccount,
65:         MultiCall[] calldata calls,
66:         address approvalToken,
67:         uint256 amount
68:     ) public onlyManager nonReentrant {
69:         for (uint256 i = 0; i < calls.length; i++) { // <= FOUND
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
['[101](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L101-L102)']
```solidity
101:     function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
102:         for (uint256 i = 0; i < tokenIds.length; i++) { // <= FOUND
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]);
108:         }
109:     }
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L44)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner {
43:         uint256 numOwnersTemp = numOwners;
44:         for (uint256 i = 0; i < _owners.length; i++) { // <= FOUND
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) {
46:                 isOwner[_owners[i]] = true;
47:                 numOwnersTemp++;
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
49:                 isOwner[_owners[i]] = false;
50:                 numOwnersTemp--;
51:             }
52:         }
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
54:         numOwners = numOwnersTemp;
55:         emit UpdateOwners(_owners, addOrRemove);
56:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L84-L104)']
```solidity
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
94:         require(isOwner[msg.sender], "Not an owner");
95:         require(sigR.length == threshold, "Not enough signatures");
96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");
97:         require(executor == msg.sender, "Invalid executor");
98:         require(block.timestamp <= deadline, "Transaction expired");
99:         {
100:             bytes32 txInputHash =
101:                 keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));
102:             bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
103:             address lastAdd = address(0);
104:             for (uint256 i = 0; i < threshold;) { // <= FOUND
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
106:                 require(recovered > lastAdd && isOwner[recovered]);
107:                 lastAdd = recovered;
108:                 unchecked {
109:                     ++i;
110:                 }
111:             }
112: 
113:             nonce++;
114:         }
115:         emit Execute(destination, data, gasLimit, executor, deadline);
116:         (bool success,) = destination.call{ gas: gasLimit }(data);
117:         require(success, "Transaction execution reverted.");
118:     }
```
['[147](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L147-L148)']
```solidity
147:     function addRoutes(RouteData[] memory _routes) public onlyMaintainer {
148:         for (uint256 i = 0; i < _routes.length;) { // <= FOUND
149:             routes.push(_routes[i]);
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);
151:             unchecked {
152:                 i++;
153:             }
154:         }
155:     }
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L41)']
```solidity
37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles)
38:         public
39:         onlyMaintainer
40:     {
41:         for (uint256 i = 0; i < baseCurrencies.length; i++) { // <= FOUND
42:             defaultPriceSource[baseCurrencies[i]] = oracles[i];
43:         }
44:         emit UpdatedDefaultPriceSource(baseCurrencies, oracles);
45:     }
```


</details>

## [Gas-13] Mappings used within a function more than once should be cached to save gas

### Resolution 
Cache such mappings and perform operations on them, if operations include modifications to the mapping(s) then remember to equate the mapping to it's cached counterpart at the end

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L75-L78)']
```solidity
75:     function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public { // <= FOUND
76:         if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender(); // <= FOUND
77: 
78:         uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId; // <= FOUND
79:         bytes memory data = abi.encode(vaultId, tvl, updateTime);
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); 
81:     }
```


</details>

## [Gas-14] Superfluous event fields

### Resolution 
The Ethereum network automatically appends certain data, including `block.number` and `block.timestamp`, to every event emitted by smart contracts. This inherent feature means that explicitly adding these parameters to your event logs isn't necessary, as they're already accessible through the transaction receipt. In fact, manually adding these details to your events can lead to wasted gas because it increases the data payload of the transaction, thereby upping the associated gas cost. For gas-efficient coding, it's best to rely on the default inclusions of `block.number` and `block.timestamp` rather than duplicating these in your events.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[25](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L25-L25)']
```solidity
25: event UpdateBridgeTransactionApproval(bytes32 transactionHash, uint256 timestamp); // <= FOUND
```


</details>

## [Gas-15] String literals passed to abi.encode()/abi.encodePacked() should not be split by commas

### Resolution 
In Solidity, string literals are considered as a single unit regardless of their segmentation into multiple parts across different lines for readability. When passed to functions like abi.encode() or abi.encodePacked(), these chunks should not be separated by commas, as it effectively divides them into multiple distinct strings rather than treating them as parts of a single string.

Incorporating commas not only disrupts the intended coherence of the string, but also incurs additional gas costs. Each new comma that is introduced causes an extra 21 gas to be expended due to the stack operations and separate memory storage (MSTORE) commands that are generated.

Num of instances: 8

### Findings 


<details><summary>Click to show findings</summary>

['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L33-L34)']
```solidity
33:         registry.updateHoldingPosition(
34:             vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false // <= FOUND
35:         );
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L54-L55)']
```solidity
54:             registry.updateHoldingPosition(
55:                 vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true // <= FOUND
56:             );
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L99-L100)']
```solidity
99:         registry.updateHoldingPosition(
100:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false // <= FOUND
101:         );
```
['[121](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L121-L122)']
```solidity
121:         registry.updateHoldingPosition(
122:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true // <= FOUND
123:         );
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L46-L47)']
```solidity
46:         registry.updateHoldingPosition(
47:             vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false // <= FOUND
48:         );
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L67-L68)']
```solidity
67:             registry.updateHoldingPosition(
68:                 vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true // <= FOUND
69:             );
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L38-L39)']
```solidity
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", false // <= FOUND
40:         );
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L61-L62)']
```solidity
61:             registry.updateHoldingPosition(
62:                 vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true // <= FOUND
63:             );
```


</details>

## [Gas-16] Consider using OZ EnumerateSet in place of nested mappings

### Resolution 
Nested mappings and multi-dimensional arrays in Solidity operate through a process of double hashing, wherein the original storage slot and the first key are concatenated and hashed, and then this hash is again concatenated with the second key and hashed. This process can be quite gas expensive due to the double-hashing operation and subsequent storage operation (sstore).

A possible optimization involves manually concatenating the keys followed by a single hash operation and an sstore. However, this technique introduces the risk of storage collision, especially when there are other nested hash maps in the contract that use the same key types. Because Solidity is unaware of the number and structure of nested hash maps in a contract, it follows a conservative approach in computing the storage slot to avoid possible collisions.

OpenZeppelin's EnumerableSet provides a potential solution to this problem. It creates a data structure that combines the benefits of set operations with the ability to enumerate stored elements, which is not natively available in Solidity. EnumerableSet handles the element uniqueness internally and can therefore provide a more gas-efficient and collision-resistant alternative to nested mappings or multi-dimensional arrays in certain scenarios. 

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[15](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L15-L15)']
```solidity
15:     mapping(address => mapping(address => uint256)) public slippageTolerance; // <= FOUND
```
['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L14-L14)']
```solidity
14:     mapping(address => mapping(address => address[])) public priceRoutes; // <= FOUND
```
['[16](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L16-L16)']
```solidity
16:     mapping(address => mapping(address => INoyaValueOracle)) public priceSource; // <= FOUND
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L19-L19)']
```solidity
19:     mapping(address => mapping(address => address)) private assetsSources; // <= FOUND
```
['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L14-L14)']
```solidity
14:     mapping(address => mapping(address => address)) public assetToBaseToPool; // <= FOUND
```


</details>

## [Gas-17] Using this.<fn>() wastes gas

### Resolution 
In Solidity, when you call a function within the same contract using `this.<functionName>()`, it is considered an external function call. Even though it's a function within the same contract, calling it with `this` makes it behave as if it's an external function. This results in more gas being consumed because external function calls in Ethereum require more computational resources than internal calls.

The reason is that external calls need to go through the full process of transferring control between contracts, which includes steps such as saving and restoring the state, copying arguments to the memory, etc. In contrast, an internal function call is more like a traditional function call in a non-contract programming context, and it's far less resource-intensive.

As a result, it is advisable to use direct function calls, like `<functionName>()`, whenever calling functions within the same contract to optimize for gas efficiency.

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L65-L65)']
```solidity
65:         return this.onERC721Received.selector; // <= FOUND
```


</details>

## [Gas-18] Use selfBalance() in place of address(this).balance

### Resolution 
In Solidity, using `selfBalance` instead of `address(this).balance` is advantageous for gas optimization. `address(this).balance` performs an external call to retrieve the contract's balance, which costs extra gas. As a resolution, defining a `selfBalance` state variable that's updated accordingly provides a more gas-efficient approach. Using selfBalance instead of address(this).balance can save around 800 gas per call. This is because address(this).balance makes an EXTBAL operation, which costs 700 gas, and additionally, the operation is a SLOAD, which costs around 800 gas. Please note that these estimates are based on the Ethereum gas schedule and might vary depending on the Ethereum network state and its future upgrades.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L72-L73)']
```solidity
72:         
73:         uint256 beforeClaimBalance = address(this).balance; // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L76-L77)']
```solidity
76:         
77:         IWETH(weth).deposit{ value: address(this).balance - beforeClaimBalance }(); // <= FOUND
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L80-L80)']
```solidity
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this)));  // <= FOUND
```


</details>

## [Gas-19] Use assembly to emit events

### Resolution 
With the use of inline assembly in Solidity, we can take advantage of low-level features like scratch space and the free memory pointer, offering more gas-efficient ways of emitting events. The scratch space is a certain area of memory where we can temporarily store data, and the free memory pointer indicates the next available memory slot. Using these, we can efficiently assemble event data without incurring additional memory expansion costs. However, safety is paramount: to avoid overwriting or leakage, we must cache the free memory pointer before use and restore it afterward, ensuring that it points to the correct memory location post-operation.

Num of instances: 137

### Findings 


<details><summary>Click to show findings</summary>

['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L126-L126)']
```solidity
126:         emit ValueOracleUpdated(address(_valueOracle)); // <= FOUND
```
['[145](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L145-L145)']
```solidity
145:         emit FeeRecepientsChanged(_withdrawFeeReceiver, _performanceFeeReceiver, _managementFeeReceiver); // <= FOUND
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L153-L153)']
```solidity
153:         emit TransferTokensToTrustedAddress(token, amount, _caller, _data); // <= FOUND
```
['[179](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L179-L179)']
```solidity
179:         emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee); // <= FOUND
```
['[214](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L214-L214)']
```solidity
214:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer); // <= FOUND
```
['[239](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L239-L239)']
```solidity
239:             emit CalculateDeposit( // <= FOUND
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
```
['[271](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L271-L271)']
```solidity
271:             emit ExecuteDeposit( // <= FOUND
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
```
['[311](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L311-L311)']
```solidity
311:         emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp); // <= FOUND
```
['[346](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L346-L346)']
```solidity
346:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp); // <= FOUND
```
['[361](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L361-L361)']
```solidity
361:         emit WithdrawGroupStarted(currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount); // <= FOUND
```
['[384](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L384-L384)']
```solidity
384:         emit WithdrawGroupFulfilled( // <= FOUND
385:             currentWithdrawGroup.lastId, currentWithdrawGroup.totalCBAmount, currentWithdrawGroup.totalABAmount
386:         );
```
['[426](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L426-L426)']
```solidity
426:             emit ExecuteWithdraw( // <= FOUND
427:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
428:             );
```
['[452](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L452-L452)']
```solidity
452:             emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw); // <= FOUND
```
['[459](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L459-L459)']
```solidity
459:             emit ResetMiddle(newMiddle, withdrawQueue.middle, depositOrWithdraw); // <= FOUND
```
['[482](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L482-L482)']
```solidity
482:         emit RecordProfit( // <= FOUND
483:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
484:         );
```
['[493](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L493-L493)']
```solidity
493:             emit ResetFee(currentProfit, storedProfitForFee, block.timestamp); // <= FOUND
```
['[517](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L517-L517)']
```solidity
517:         emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares); // <= FOUND
```
['[535](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L535-L535)']
```solidity
535:         emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution); // <= FOUND
```
['[559](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L559-L559)']
```solidity
559:             emit RetrieveTokensForWithdraw( // <= FOUND
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
```
['[667](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L667-L667)']
```solidity
667:         emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount); // <= FOUND
```
['[672](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L672-L672)']
```solidity
672:         emit SetDepositWaitingTime(_depositWaitingTime); // <= FOUND
```
['[677](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L677-L677)']
```solidity
677:         emit SetWithdrawWaitingTime(_withdrawWaitingTime); // <= FOUND
```
['[687](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L687-L687)']
```solidity
687:         emit Rescue(msg.sender, token, amount); // <= FOUND
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L85-L85)']
```solidity
85:         emit updateFlashloanAddress(_flashLoan, flashLoan); // <= FOUND
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L141-L141)']
```solidity
141:         emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens); // <= FOUND
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L142-L142)']
```solidity
142:         emit VaultAddressesChanged( // <= FOUND
143:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency
144:         );
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L193-L193)']
```solidity
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
```
['[213](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L213-L213)']
```solidity
213:         emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted); // <= FOUND
```
['[256](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L256-L256)']
```solidity
256:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data); // <= FOUND
```
['[273](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L273-L273)']
```solidity
273:         emit TrustedPositionRemoved(vaultId, _positionId); // <= FOUND
```
['[295](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L295-L295)']
```solidity
295:         emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index); // <= FOUND
```
['[353](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L353-L353)']
```solidity
353:             emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex); // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L52-L52)']
```solidity
52:         emit Supply(supplyToken, amount); // <= FOUND
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L74-L74)']
```solidity
74:         emit Borrow(_borrowAsset, _amount); // <= FOUND
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L84-L84)']
```solidity
84:         emit Repay(asset, amount, i); // <= FOUND
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L89-L89)']
```solidity
89:         emit RepayWithCollateral(_borrowAsset, _amount, i); // <= FOUND
```
['[110](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L110-L110)']
```solidity
110:         emit WithdrawCollateral(_collateral, _collateralAmount); // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L72-L72)']
```solidity
72:         emit Supply(data.pool, data.amount0, data.amount1); // <= FOUND
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L97-L97)']
```solidity
97:         emit Withdraw(data.pool, data.amountLiquidity); // <= FOUND
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L106-L106)']
```solidity
106:         emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount); // <= FOUND
```
['[159](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L159-L159)']
```solidity
159:         emit DecreasePosition(p); // <= FOUND
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L42-L42)']
```solidity
42:         emit MakeFlashLoan(tokens, amounts); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L60-L60)']
```solidity
60:         emit ReceiveFlashLoan(tokens, amounts, feeAmounts, userData); // <= FOUND
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L37-L37)']
```solidity
37:         emit Supply(market, asset, amount); // <= FOUND
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L59-L59)']
```solidity
59:         emit WithdrawOrBorrow(_market, asset, amount); // <= FOUND
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L67-L67)']
```solidity
67:         emit ClaimRewards(rewardContract, market); // <= FOUND
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L149-L149)']
```solidity
149:         emit OpenCurvePosition(pool, depositIndex, amount, minAmount); // <= FOUND
```
['[174](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L174-L174)']
```solidity
174:         emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount); // <= FOUND
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L184-L184)']
```solidity
184:         emit WithdrawFromConvexBooster(pid, amount); // <= FOUND
```
['[194](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L194-L194)']
```solidity
194:         emit WithdrawFromConvexRewardPool(pool, amount); // <= FOUND
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L204-L204)']
```solidity
204:         emit WithdrawFromGauge(pool, amount); // <= FOUND
```
['[214](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L214-L214)']
```solidity
214:         emit WithdrawFromPrisma(depostiToken, amount); // <= FOUND
```
['[226](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L226-L226)']
```solidity
226:         emit HarvestRewards(gauges); // <= FOUND
```
['[240](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L240-L240)']
```solidity
240:         emit HarvestPrismaRewards(pools); // <= FOUND
```
['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L254-L254)']
```solidity
254:         emit HarvestConvexRewards(rewardsPools); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L60-L60)']
```solidity
60:         emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount); // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L79-L79)']
```solidity
79:         emit Withdraw(address(pool), withdrawAmount); // <= FOUND
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L97-L97)']
```solidity
97:         emit Repay(address(pool), sharesToRepay); // <= FOUND
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L33-L33)']
```solidity
33:         emit OpenAccount(facade, ref); // <= FOUND
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L51-L51)']
```solidity
51:         emit CloseAccount(facade, creditAccount); // <= FOUND
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L85-L85)']
```solidity
85:         emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount); // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L43-L43)']
```solidity
43:         emit Deposit(amountIn); // <= FOUND
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L61-L61)']
```solidity
61:         emit RequestWithdrawals(amount); // <= FOUND
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L85-L85)']
```solidity
85:         emit ClaimWithdrawal(requestId); // <= FOUND
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L70-L70)']
```solidity
70:         emit Stake(amount, duration, doDelegation); // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L81-L81)']
```solidity
81:         emit Unstake(lockupId); // <= FOUND
```
['[104](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L104-L104)']
```solidity
104:         emit AddLiquidityInMaverickPool(p); // <= FOUND
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L126-L126)']
```solidity
126:         emit RemoveLiquidityFromMaverickPool(p); // <= FOUND
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L141-L141)']
```solidity
141:         emit ClaimBoostedPositionRewards(rewardContract); // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L49-L49)']
```solidity
49:         emit Supply(amount, id, sOrC); // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L72-L72)']
```solidity
72:         emit Withdraw(amount, id, sOrC); // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L87-L87)']
```solidity
87:         emit Borrow(amount, id); // <= FOUND
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L100-L100)']
```solidity
100:         emit Repay(amount, id); // <= FOUND
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L33-L33)']
```solidity
33:         emit SendPositionToMasterChef(tokenId); // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L43-L43)']
```solidity
43:         emit UpdatePosition(tokenId); // <= FOUND
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L53-L53)']
```solidity
53:         emit Withdraw(tokenId); // <= FOUND
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L89-L89)']
```solidity
89:         emit Supply(market, syMinted); // <= FOUND
```
['[101](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L101-L101)']
```solidity
101:         emit MintPTAndYT(market, syAmount); // <= FOUND
```
['[118](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L118-L118)']
```solidity
118:         emit DepositIntoMarket(address(market), SYamount, PTamount); // <= FOUND
```
['[129](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L129-L129)']
```solidity
129:         emit DepositIntoPenpie(_market, _amount); // <= FOUND
```
['[139](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L139-L139)']
```solidity
139:         emit WithdrawFromPenpie(_market, _amount); // <= FOUND
```
['[156](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L156-L156)']
```solidity
156:         emit SwapYTForPT(market, exactYTIn, min, guess); // <= FOUND
```
['[173](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L173-L173)']
```solidity
173:         emit SwapYTForSY(market, exactYTIn, min, orderData); // <= FOUND
```
['[195](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L195-L195)']
```solidity
195:         emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY); // <= FOUND
```
['[207](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L207-L207)']
```solidity
207:         emit BurnLP(address(market), amount); // <= FOUND
```
['[232](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L232-L232)']
```solidity
232:         emit DecreasePosition(address(market), _amount, closePosition); // <= FOUND
```
['[247](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L247-L247)']
```solidity
247:         emit ClaimRewards(address(market)); // <= FOUND
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L66-L66)']
```solidity
66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount); // <= FOUND
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L85-L85)']
```solidity
85:         emit AddColl(address(zapContract), tm, amountIn); // <= FOUND
```
['[121](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L121-L121)']
```solidity
121:         emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing); // <= FOUND
```
['[135](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L135-L135)']
```solidity
135:         emit CloseTrove(address(zapContract), troveManager); // <= FOUND
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L41-L41)']
```solidity
41:         emit Deposit(siloToken, dToken, amount, oC); // <= FOUND
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L68-L68)']
```solidity
68:         emit Withdraw(siloToken, wToken, amount, oC, closePosition); // <= FOUND
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L89-L89)']
```solidity
89:         emit Borrow(siloToken, bToken, amount); // <= FOUND
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L106-L106)']
```solidity
106:         emit Repay(siloToken, rToken, amount); // <= FOUND
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L69-L69)']
```solidity
69:         emit DepositIntoStargatePool(depositRequest); // <= FOUND
```
['[96](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L96-L96)']
```solidity
96:         emit WithdrawFromStargatePool(withdrawRequest); // <= FOUND
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L106-L106)']
```solidity
106:         emit ClaimStargateRewards(poolId); // <= FOUND
```
['[56](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L56-L56)']
```solidity
56:         emit OpenPosition(p, tokenId); // <= FOUND
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L95-L95)']
```solidity
95:         emit IncreasePosition(p); // <= FOUND
```
['[107](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L107-L107)']
```solidity
107:             emit CollectFees(tokenIds[i]); // <= FOUND
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L55-L55)']
```solidity
55:         emit UpdateOwners(_owners, addOrRemove); // <= FOUND
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L66-L66)']
```solidity
66:         emit UpdateThreshold(_threshold); // <= FOUND
```
['[115](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L115-L115)']
```solidity
115:         emit Execute(destination, data, gasLimit, executor, deadline); // <= FOUND
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L50-L50)']
```solidity
50:         emit MinimumHealthFactorUpdated(_minimumHealthFactor); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L60-L60)']
```solidity
60:         emit SwapHandlerUpdated(_swapHandler); // <= FOUND
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L69-L69)']
```solidity
69:         emit ValueOracleUpdated(_valueOracle); // <= FOUND
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L88-L88)']
```solidity
88:         emit TransferTokensToTrustedAddress(token, amount, caller, data); // <= FOUND
```
['[128](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L128-L128)']
```solidity
128:         emit TransferPositionToConnector(tokens, amounts, connector, data); // <= FOUND
```
['[143](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L143-L143)']
```solidity
143:             emit UpdateTokenInRegistry(token, remove); // <= FOUND
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L192-L192)']
```solidity
192:         emit AddLiquidity(tokens, amounts, data); // <= FOUND
```
['[217](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L217-L217)']
```solidity
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]); // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L49-L49)']
```solidity
49:         emit UpdateChainInfo(chainId, destinationAddress); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L60-L60)']
```solidity
60:         emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp); // <= FOUND
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L70-L70)']
```solidity
70:         emit StartBridgeTransaction(bridgeRequest, txn); // <= FOUND
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L50-L50)']
```solidity
50:         emit SetValueOracle(_valueOracle); // <= FOUND
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59-L59)']
```solidity
59:         emit SetSlippageTolerance(address(0), address(0), _slippageTolerance); // <= FOUND
```
['[73](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L73-L73)']
```solidity
73:         emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance); // <= FOUND
```
['[82](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L82-L82)']
```solidity
82:         emit AddEligibleUser(_user); // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L117-L117)']
```solidity
117:         emit ExecutionCompleted( // <= FOUND
118:             _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
119:         );
```
['[139](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L139-L139)']
```solidity
139:         emit BridgeExecutionCompleted(_bridgeRequest); // <= FOUND
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L150-L150)']
```solidity
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge); // <= FOUND
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160-L160)']
```solidity
160:         emit RouteUpdate(_routeId, false); // <= FOUND
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L47-L47)']
```solidity
47:         emit AddedHandler(_handler, state); // <= FOUND
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L57-L57)']
```solidity
57:         emit AddedChain(_chainId, state); // <= FOUND
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L67-L67)']
```solidity
67:         emit AddedBridgeBlacklist(bridgeName, state); // <= FOUND
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L99-L99)']
```solidity
99:         emit Swapped(balanceOut0, balanceOut1, _request.outputToken); // <= FOUND
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L141-L141)']
```solidity
141:         emit Bridged(_request.from, _request.inputToken, _request.amount, _request.data); // <= FOUND
```
['[182](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L182-L182)']
```solidity
182:         emit Forwarded(lifi, address(token), amount, data); // <= FOUND
```
['[200](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L200-L200)']
```solidity
200:         emit Rescued(token, userAddress, amount); // <= FOUND
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L44-L44)']
```solidity
44:         emit UpdatedDefaultPriceSource(baseCurrencies, oracles); // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L58-L58)']
```solidity
58:         emit UpdatedAssetPriceSource(asset, baseToken, oracle); // <= FOUND
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L63-L63)']
```solidity
63:         emit UpdatedPriceRoute(asset, base, s); // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L58-L58)']
```solidity
58:         emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold); // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L72-L72)']
```solidity
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L41-L41)']
```solidity
41:         emit NewPeriod(_period); // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L52-L52)']
```solidity
52:         emit PoolsForAsset(tokenIn, baseToken, pool); // <= FOUND
```


</details>

## [Gas-20] Use solady library where possible to save gas

### Resolution 
The following OpenZeppelin imports have a Solady equivalent, as such they can be used to save GAS as Solady modules have been specifically designed to be as GAS efficient as possible

Num of instances: 11

### Findings 


<details><summary>Click to show findings</summary>

['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable.sol"; // <= FOUND
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/access/Ownable2Step.sol"; // <= FOUND
```
['[6](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L6-L6)']
```solidity
6: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721.sol"; // <= FOUND
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L8-L8)']
```solidity
8: import "@openzeppelin/contracts-5.0/token/ERC721/utils/ERC721Holder.sol"; // <= FOUND
```
['[12](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L12-L12)']
```solidity
12: import "@openzeppelin/contracts-5.0/token/ERC721/IERC721Receiver.sol"; // <= FOUND
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L5-L5)']
```solidity
5: import { ERC4626, ERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/extensions/ERC4626.sol"; // <= FOUND
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L10-L10)']
```solidity
10: import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol"; // <= FOUND
```
['[4](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L4-L4)']
```solidity
4: import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol"; // <= FOUND
```
['[10](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L10-L10)']
```solidity
10: import { SafeERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol"; // <= FOUND
```
['[5](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L5-L5)']
```solidity
5: import { SafeERC20, IERC20 } from "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol"; // <= FOUND
```
['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L8-L8)']
```solidity
8: import "@openzeppelin/contracts-5.0/token/ERC20/extensions/IERC20Metadata.sol"; // <= FOUND
```


</details>

## [Gas-21] Use assembly in place of abi.decode to extract calldata values more efficiently

### Resolution 
Using inline assembly to extract calldata values can be more gas-efficient than using `abi.decode` in Solidity. Inline assembly gives more direct access to EVM operations, enabling optimized usage of calldata. However, assembly should be used judiciously as it's more prone to errors. Opt for this approach when performance is critical and the complexity it introduces is manageable.

Num of instances: 43

### Findings 


<details><summary>Click to show findings</summary>

['[632](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L632-L632)']
```solidity
632:             address token = abi.decode(p.data, (address)); // <= FOUND
```
['[633](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L633-L633)']
```solidity
633:             uint256 amount = IERC20(token).balanceOf(abi.decode(position.data, (address))); // <= FOUND
```
['[235](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L235-L235)']
```solidity
235:             tokens[0] = abi.decode(data, (address)); // <= FOUND
```
['[119](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L119-L119)']
```solidity
119:         (address pool) = abi.decode(data, (address)); // <= FOUND
```
['[127](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L127-L127)']
```solidity
127:         (address pool) = abi.decode(pBP.data, (address)); // <= FOUND
```
['[164](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L164-L164)']
```solidity
164:         PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo)); // <= FOUND
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L192-L192)']
```solidity
192:         return (abi.decode(p.additionalData, (PoolInfo)), positionId); // <= FOUND
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L62-L68)']
```solidity
62:         (
63:             uint256 vaultId,
64:             address receiver,
65:             address[] memory destinationConnector,
66:             bytes[] memory callingData,
67:             uint256[] memory gas
68:         ) = abi.decode(userData, (uint256, address, address[], bytes[], uint256[])); // <= FOUND
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L88-L89)']
```solidity
88:         (address tokenA, address tokenB) =
89:             abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address, address)); // <= FOUND
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L99-L99)']
```solidity
99:         (address tokenA, address tokenB) = abi.decode(data, (address, address)); // <= FOUND
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L126-L126)']
```solidity
126:         address market = abi.decode(registry.getPositionBP(vaultId, p.positionId).data, (address)); // <= FOUND
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L124-L124)']
```solidity
124:         PoolInfo memory poolInfo = abi.decode(p.additionalData, (PoolInfo)); // <= FOUND
```
['[261](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L261-L261)']
```solidity
261:         return abi.decode(p.additionalData, (PoolInfo)); // <= FOUND
```
['[267](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L267-L267)']
```solidity
267:         PoolInfo memory poolInfo = abi.decode(PTI.additionalData, (PoolInfo)); // <= FOUND
```
['[107](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L107-L107)']
```solidity
107:         uint256 accountId = abi.decode(p.data, (uint256)); // <= FOUND
```
['[152](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L152-L152)']
```solidity
152:         IFraxPair pool = IFraxPair(abi.decode(positionInfo.data, (address))); // <= FOUND
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L74-L74)']
```solidity
74:                 (address token) = abi.decode(calls[i].callData[4:], (address)); // <= FOUND
```
['[94](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L94-L94)']
```solidity
94:         address creditAccount = abi.decode(p.data, (address)); // <= FOUND
```
['[96](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L96-L96)']
```solidity
96:         ICreditFacadeV3 facade = ICreditFacadeV3(abi.decode(positionInfo.data, (address))); // <= FOUND
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L91-L91)']
```solidity
91:         (uint256 amount) = abi.decode(p.additionalData, (uint256)); // <= FOUND
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L150-L150)']
```solidity
150:         IMaverickPool pool = abi.decode(position.data, (IMaverickPool)); // <= FOUND
```
['[121](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L121-L121)']
```solidity
121:             Id id = abi.decode(positionInfo.data, (Id)); // <= FOUND
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L142-L142)']
```solidity
142:         Id id = abi.decode(data, (Id)); // <= FOUND
```
['[261](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L261-L261)']
```solidity
261:             address market = abi.decode(positionInfo.data, (address)); // <= FOUND
```
['[312](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L312-L312)']
```solidity
312:         address market = abi.decode(data, (address)); // <= FOUND
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L59-L59)']
```solidity
59:         address collateral = abi.decode(positionInfo.additionalData, (address)); // <= FOUND
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L148-L148)']
```solidity
148:             (address zap, address troveManager) = abi.decode(positionInfo.data, (address, address)); // <= FOUND
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L165-L165)']
```solidity
165:         (address zap, address troveManager) = abi.decode(data, (address, address)); // <= FOUND
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L122-L122)']
```solidity
122:         (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address)); // <= FOUND
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L111-L111)']
```solidity
111:         (address siloToken) = abi.decode(bp.data, (address)); // <= FOUND
```
['[144](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L144-L144)']
```solidity
144:         (address siloToken) = abi.decode(data, (address)); // <= FOUND
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L112-L112)']
```solidity
112:         uint256 poolId = abi.decode(pBP.data, (uint256)); // <= FOUND
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L124-L124)']
```solidity
124:         uint256 poolId = abi.decode(data, (uint256)); // <= FOUND
```
['[129](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L129-L129)']
```solidity
129:         uint256 tokenId = abi.decode(p.data, (uint256)); // <= FOUND
```
['[130](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L130-L130)']
```solidity
130:         (address token0, address token1) = abi.decode(positionInfo.data, (address, address)); // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L133-L133)']
```solidity
133:         (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24)); // <= FOUND
```
['[154](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L154-L154)']
```solidity
154:         (tokens[0], tokens[1]) = abi.decode(data, (address, address)); // <= FOUND
```
['[93](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L93-L93)']
```solidity
93:             (uint256 newAmount, bytes memory newData) = abi.decode(data, (uint256, bytes)); // <= FOUND
```
['[101](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L101-L101)']
```solidity
101:             uint256 routeId = abi.decode(data, (uint256)); // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L35-L35)']
```solidity
35:         (uint256 amountToSend, uint256 amountToReturn) = abi.decode(data, (uint256, uint256)); // <= FOUND
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L69-L69)']
```solidity
69:         (uint256 vaultId, uint256 tvl, uint256 updateTime) = abi.decode(_message, (uint256, uint256, uint256)); // <= FOUND
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L54-L54)']
```solidity
54:             return (abi.decode(position.additionalData, (uint256))); // <= FOUND
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L36-L36)']
```solidity
36:             address token = abi.decode(bp.data, (address)); // <= FOUND
```


</details>

## [Gas-22] Identical Deployments Should be Replaced with Clone

### Resolution 
In the context of smart contracts, deploying multiple identical contracts can lead to inefficient use of gas and unnecessarily duplicate code on the blockchain. A more gas-efficient approach is to use a "clone" pattern. By deploying a master contract and then creating clones of it, only the differences between the instances are stored for each clone. This approach leverages the EIP-1167 standard, which defines a minimal proxy contract that points to the implementation contract. Clones can be far cheaper to deploy compared to full instances. So, the resolution is to replace identical deployments with clones, saving on gas and storage space.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L69-L69)']
```solidity
69:         address pool = factory.getPair(p.tokenA, p.tokenB); // <= FOUND
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L90-L90)']
```solidity
90:         address pool = factory.getPair(tokenA, tokenB); // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L49-L49)']
```solidity
49:         address pool = IUniswapV3Factory(factory).getPool(tokenIn, baseToken, fee); // <= FOUND
```


</details>

## [Gas-23] Where a value is casted more than once, consider caching the result to save gas

### Resolution 
Casting values multiple times in Solidity can be gas-inefficient. When a value undergoes repeated type conversions, the EVM must execute additional operations for each cast, consuming more gas than necessary. To optimize for gas efficiency, cache the result of the initial cast in a local variable and reuse it, rather than performing multiple casts. This not only conserves gas but also enhances code readability, reducing potential error points. For example, instead of repeatedly casting an `address` to `uint256`, cast once, store the result in a local variable, and reference that variable in subsequent operations.

Num of instances: 20

### Findings 


<details><summary>Click to show findings</summary>

['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L123-L126)']
```solidity
123:     function updateValueOracle(INoyaValueOracle _valueOracle) public onlyMaintainer {
124:         require(address(_valueOracle) != address(0)); // <= FOUND
125:         valueOracle = _valueOracle;
126:         emit ValueOracleUpdated(address(_valueOracle)); // <= FOUND
127:     }
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L38-L56)']
```solidity
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant
42:     {
43:         bytes32 positionId =
44:             registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));
45:         IERC20 token = IERC20(pool.collateralContract());
46:         if (collateralAmount > 0) {
47:             _approveOperations(address(token), address(pool), collateralAmount); // <= FOUND
48:         }
49:         if (borrowAmount > 0) {
50:             pool.borrowAsset(borrowAmount, collateralAmount, address(this));
51:             _updateTokenInRegistry(pool.asset());
52:         } else if (collateralAmount > 0) {
53:             pool.addCollateral(collateralAmount, address(this));
54:         }
55:         if (collateralAmount > 0) {
56:             _updateTokenInRegistry(address(token)); // <= FOUND
57:         }
58:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
59:         verifyHealthFactor(pool);
60:         emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount); // <= FOUND
61:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L87-L97)']
```solidity
87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
88:         uint256 repayTokenAmount = pool.toBorrowAmount(sharesToRepay, true);
89:         uint256 sharesOwed = pool.userBorrowShares(address(this));
90:         address asset = pool.asset();
91:         if (sharesToRepay > sharesOwed) {
92:             revert IConnector_InvalidInput();
93:         }
94:         _approveOperations(asset, address(pool), repayTokenAmount); // <= FOUND
95:         IFraxPair(pool).repayAsset(sharesToRepay, address(this));
96:         _updateTokenInRegistry(asset);
97:         emit Repay(address(pool), sharesToRepay); // <= FOUND
98:     }
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L112-L118)']
```solidity
112:     function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {
113:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
114:         IERC20(address(_SY)).safeTransfer(address(market), SYamount); // <= FOUND
115:         IERC20(address(_PT)).safeTransfer(address(market), PTamount); // <= FOUND
116:         market.mint(address(this), SYamount, PTamount);
117:         market.skim();
118:         emit DepositIntoMarket(address(market), SYamount, PTamount); // <= FOUND
119:     }
```
['[183](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L183-L195)']
```solidity
183:     function swapExactPTForSY(IPMarket market, uint256 exactPTIn, bytes calldata swapData, uint256 minSY)
184:         external
185:         onlyManager
186:         nonReentrant
187:     {
188:         (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
189:         IERC20(address(_PT)).safeTransfer(address(market), exactPTIn); // <= FOUND
190:         (uint256 netSyOut, uint256 netSyFee) = market.swapExactPtForSy(address(this), exactPTIn, swapData);
191:         if (netSyOut < minSY) {
192:             revert InsufficientSyOut(netSyOut, minSY);
193:         }
194:         market.skim();
195:         emit SwapExactPTForSY(address(market), exactPTIn, swapData, minSY); // <= FOUND
196:     }
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L203-L207)']
```solidity
203:     function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {
204:         IERC20(address(market)).safeTransfer(address(market), amount); // <= FOUND
205:         market.burn(address(this), address(market), amount); // <= FOUND
206:         market.skim();
207:         emit BurnLP(address(market), amount); // <= FOUND
208:     }
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L66)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {
57:         bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
58:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
59:         address collateral = abi.decode(positionInfo.additionalData, (address));
60:         address debTtoken = ITroveManager(tm).debtToken();
61:         _approveOperations(collateral, address(zap), dAmount); // <= FOUND
62:         zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));
63:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
64:         _updateTokenInRegistry(collateral);
65:         _updateTokenInRegistry(debTtoken);
66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount); // <= FOUND
67:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L75-L85)']
```solidity
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {
76:         bytes32 positionId =
77:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));
78:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
79:         if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {
80:             revert IConnector_InvalidPosition(positionId);
81:         }
82:         address collateral = abi.decode(positionInfo.additionalData, (address));
83:         _approveOperations(collateral, address(zapContract), amountIn); // <= FOUND
84:         zapContract.addColl(tm, amountIn, address(this), address(this));
85:         emit AddColl(address(zapContract), tm, amountIn); // <= FOUND
86:     }
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L182)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     {
170:         if (!_isNative(token)) {
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId)); // <= FOUND
172: 
173:             _setAllowance(token, lifi, amount);
174:         }
175: 
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);
177: 
178:         if (!success) {
179:             revert FailedToForward(err);
180:         }
181: 
182:         emit Forwarded(lifi, address(token), amount, data); // <= FOUND
183:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L53-L56)']
```solidity
53:     function supply(DepositData memory data) public onlyManager nonReentrant {
54:         bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));
55:         _approveOperations(IPool(data.pool).token0(), address(aerodromeRouter), data.amount0); // <= FOUND 'address(aerodromeRouter)'
56:         _approveOperations(IPool(data.pool).token1(), address(aerodromeRouter), data.amount1); // <= FOUND 'address(aerodromeRouter)'
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
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L43-L45)']
```solidity
43:     function addLiquidityInCamelotPool(CamelotAddLiquidityParams calldata p) external onlyManager nonReentrant {
44:         _approveOperations(p.tokenA, address(router), p.amountA); // <= FOUND 'address(router)'
45:         _approveOperations(p.tokenB, address(router), p.amountB); // <= FOUND 'address(router)'
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
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L38-L56)']
```solidity
38:     function borrowAndSupply(IFraxPair pool, uint256 borrowAmount, uint256 collateralAmount)
39:         external
40:         onlyManager
41:         nonReentrant
42:     {
43:         bytes32 positionId =
44:             registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool));
45:         IERC20 token = IERC20(pool.collateralContract());
46:         if (collateralAmount > 0) {
47:             _approveOperations(address(token), address(pool), collateralAmount); // <= FOUND 'address(pool)'
48:         }
49:         if (borrowAmount > 0) {
50:             pool.borrowAsset(borrowAmount, collateralAmount, address(this));
51:             _updateTokenInRegistry(pool.asset());
52:         } else if (collateralAmount > 0) {
53:             pool.addCollateral(collateralAmount, address(this));
54:         }
55:         if (collateralAmount > 0) {
56:             _updateTokenInRegistry(address(token)); // <= FOUND 'address(token)'
57:         }
58:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
59:         verifyHealthFactor(pool);
60:         emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount); // <= FOUND 'address(pool)'
61:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L87-L97)']
```solidity
87:     function repay(IFraxPair pool, uint256 sharesToRepay) public onlyManager nonReentrant {
88:         uint256 repayTokenAmount = pool.toBorrowAmount(sharesToRepay, true);
89:         uint256 sharesOwed = pool.userBorrowShares(address(this));
90:         address asset = pool.asset();
91:         if (sharesToRepay > sharesOwed) {
92:             revert IConnector_InvalidInput();
93:         }
94:         _approveOperations(asset, address(pool), repayTokenAmount); // <= FOUND 'address(pool)'
95:         IFraxPair(pool).repayAsset(sharesToRepay, address(this));
96:         _updateTokenInRegistry(asset);
97:         emit Repay(address(pool), sharesToRepay); // <= FOUND 'address(pool)'
98:     }
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L35-L42)']
```solidity
35:     function supply(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {
36:         MarketParams memory params = morphoBlue.idToMarketParams(id);
37:         if (sOrC) {
38:             _approveOperations(params.loanToken, address(morphoBlue), amount); // <= FOUND 'address(morphoBlue)'
39:             morphoBlue.supply(params, amount, 0, address(this), "");
40:             _updateTokenInRegistry(params.loanToken);
41:         } else {
42:             _approveOperations(params.collateralToken, address(morphoBlue), amount); // <= FOUND 'address(morphoBlue)'
43:             morphoBlue.supplyCollateral(params, amount, address(this), "");
44:             _updateTokenInRegistry(params.collateralToken);
45:         }
46:         registry.updateHoldingPosition(
47:             vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false
48:         );
49:         emit Supply(amount, id, sOrC);
50:     }
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L52-L66)']
```solidity
52:     function openTrove(IStakeNTroveZap zap, address tm, uint256 maxFee, uint256 dAmount, uint256 bAmount)
53:         public
54:         onlyManager
55:         nonReentrant
56:     {
57:         bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm));
58:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
59:         address collateral = abi.decode(positionInfo.additionalData, (address));
60:         address debTtoken = ITroveManager(tm).debtToken();
61:         _approveOperations(collateral, address(zap), dAmount); // <= FOUND 'address(zap)'
62:         zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this));
63:         registry.updateHoldingPosition(vaultId, positionId, "", "", false);
64:         _updateTokenInRegistry(collateral);
65:         _updateTokenInRegistry(debTtoken);
66:         emit OpenTrove(address(zap), tm, maxFee, dAmount, bAmount); // <= FOUND 'address(zap)'
67:     }
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L75-L85)']
```solidity
75:     function addColl(IStakeNTroveZap zapContract, address tm, uint256 amountIn) public onlyManager nonReentrant {
76:         bytes32 positionId =
77:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));
78:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, positionId);
79:         if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {
80:             revert IConnector_InvalidPosition(positionId);
81:         }
82:         address collateral = abi.decode(positionInfo.additionalData, (address));
83:         _approveOperations(collateral, address(zapContract), amountIn); // <= FOUND 'address(zapContract)'
84:         zapContract.addColl(tm, amountIn, address(this), address(this));
85:         emit AddColl(address(zapContract), tm, amountIn); // <= FOUND 'address(zapContract)'
86:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L40-L46)']
```solidity
40:     function openPosition(MintParams memory p) external onlyManager nonReentrant returns (uint256 tokenId) {
41:         bytes32 positionId =
42:             registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1));
43:         p.recipient = address(this);
44:         
45:         _approveOperations(p.token0, address(positionManager), p.amount0Desired); // <= FOUND 'address(positionManager)'
46:         _approveOperations(p.token1, address(positionManager), p.amount1Desired); // <= FOUND 'address(positionManager)'
47: 
48:         
49:         (tokenId,,,) = positionManager.mint(p);
50:         bytes memory positionData = abi.encode(tokenId);
51:         registry.updateHoldingPosition(
52:             vaultId, positionId, positionData, abi.encode(p.tickLower, p.tickUpper, p.fee), false
53:         );
54:         _updateTokenInRegistry(p.token0);
55:         _updateTokenInRegistry(p.token1);
56:         emit OpenPosition(p, tokenId);
57:     }
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L87-L91)']
```solidity
87:     function increasePosition(IncreaseLiquidityParams memory p) external onlyManager nonReentrant {
88:         (, address token0, address token1) = getCurrentLiquidity(p.tokenId);
89:         
90:         _approveOperations(token0, address(positionManager), p.amount0Desired); // <= FOUND 'address(positionManager)'
91:         _approveOperations(token1, address(positionManager), p.amount1Desired); // <= FOUND 'address(positionManager)'
92:         positionManager.increaseLiquidity(p);
93:         _updateTokenInRegistry(token0);
94:         _updateTokenInRegistry(token1);
95:         emit IncreasePosition(p);
96:     }
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L94)']
```solidity
77:     function performSwapAction(address caller, SwapRequest calldata _request)
78:         external
79:         payable
80:         override
81:         onlyHandler
82:         returns (uint256)
83:     {
84:         require(verifySwapData(_request), "LifiImplementation: INVALID_SWAP_DATA");
85:         uint256 balanceOut0 = 0;
86:         if (_request.outputToken == address(0)) {
87:             balanceOut0 = address(_request.from).balance; // <= FOUND 'address(_request.from)'
88:         } else {
89:             balanceOut0 = IERC20(_request.outputToken).balanceOf(_request.from);
90:         }
91:         _forward(IERC20(_request.inputToken), _request.from, _request.amount, caller, _request.data, _request.routeId);
92:         uint256 balanceOut1 = 0;
93:         if (_request.outputToken == address(0)) {
94:             balanceOut1 = address(_request.from).balance; // <= FOUND 'address(_request.from)'
95:         } else {
96:             balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);
97:         }
98: 
99:         emit Swapped(balanceOut0, balanceOut1, _request.outputToken);
100: 
101:         return balanceOut1 - balanceOut0;
102:     }
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L165-L182)']
```solidity
165:     function _forward(IERC20 token, address from, uint256 amount, address caller, bytes calldata data, uint256 routeId)
166:         internal
167:         virtual
168:         nonReentrant
169:     {
170:         if (!_isNative(token)) {
171:             ITokenTransferCallBack(from).sendTokensToTrustedAddress(address(token), amount, caller, abi.encode(routeId)); // <= FOUND 'address(token)'
172: 
173:             _setAllowance(token, lifi, amount);
174:         }
175: 
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data);
177: 
178:         if (!success) {
179:             revert FailedToForward(err);
180:         }
181: 
182:         emit Forwarded(lifi, address(token), amount, data); // <= FOUND 'address(token)'
183:     }
```


</details>

## [Gas-24] Unnecessary casting as variable is already of the same type

### Resolution 
Unnecessary casting of a variable to the same type is redundant and can contribute to gas inefficiency and code clutter. This situation commonly arises when developers, perhaps due to oversight or misunderstanding, explicitly cast a variable to its existing type. For example, casting a `uint256` variable to `uint256` again does not change its type or value but adds unnecessary operations to the code.

**Resolution**: Developers should scrutinize their code to identify and remove any unnecessary type casting. Utilizing linters or static analysis tools can aid in detecting such redundancies. Ensuring that the code is clean and efficient not only saves gas but also enhances readability and maintainability.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L100-L102)']
```solidity
100:     function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {
101:         address gauge = voter.gauges(pool);
102:         IERC20(pool).forceApprove(address(gauge), liquidity); // <= FOUND
103:         IGauge(gauge).deposit(liquidity, address(this));
104:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L63-L65)']
```solidity
63:     function claimRewards(address rewardContract, address market) external onlyManager nonReentrant {
64:         address rewardToken = IRewards(rewardContract).rewardConfig(market).token;
65:         IRewards(rewardContract).claim(address(market), address(this), true); // <= FOUND
66:         _updateTokenInRegistry(rewardToken);
67:         emit ClaimRewards(rewardContract, market);
68:     }
```


</details>

## [Gas-25] Simple checks for zero uint can be done using assembly to save gas

### Resolution 
Using assembly for simple zero checks on unsigned integers can save gas due to lower-level, optimized operations. 

**Resolution**: Implement inline assembly with Solidity's `assembly` block to perform zero checks. Ensure thorough testing and verification, as assembly lacks the safety checks of high-level Solidity, potentially introducing vulnerabilities if not used carefully.

Num of instances: 14

### Findings 


<details><summary>Click to show findings</summary>

['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L77-L77)']
```solidity
77:         if (borrowBalanceInBase == 0) return type(uint256).max; // <= FOUND
```
['[86](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L86-L86)']
```solidity
86:         if (borrowBalanceInBase == 0) return 0; // <= FOUND
```
['[280](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L280-L280)']
```solidity
280:         if (balance == 0) return (0, info.tokens[info.defaultWithdrawIndex]); // <= FOUND
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L124-L124)']
```solidity
124:         if (_borrowerAmount == 0) return type(uint256).max; // <= FOUND
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L126-L126)']
```solidity
126:         if (_collateralAmount == 0) return 0; // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L133-L133)']
```solidity
133:         if (currentPositionLTV == 0) return type(uint256).max;  // <= FOUND
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L112-L112)']
```solidity
112:         if (borrowAmount == 0) return type(uint256).max; // <= FOUND
```
['[39](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L39-L39)']
```solidity
39:         if (_period == 0) revert INoyaValueOracle_InvalidInput(); // <= FOUND
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L142-L142)']
```solidity
142:         return (assetsIn & (uint16(1) << assetOffset) != 0); // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L58-L58)']
```solidity
58:         if (approvedBridgeTXN[transactionHash] != 0) delete approvedBridgeTXN[transactionHash]; // <= FOUND
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L78-L78)']
```solidity
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]); // <= FOUND
```
['[275](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L275-L275)']
```solidity
275:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18; // <= FOUND
```
['[278](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L278-L278)']
```solidity
278:             if (YTBalance > 0) SYAmount += getYTValue(market, YTBalance); // <= FOUND
```
['[280](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L280-L280)']
```solidity
280:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18; // <= FOUND
```


</details>

## [Gas-26] Using nested if to save gas

### Resolution 
Using nested `if` statements instead of logical AND (`&&`) operators can potentially save gas in Solidity contracts. When a series of conditions are connected with `&&`, all conditions must be evaluated even if the first one fails. In contrast, nested `if` statements allow for short-circuiting; if the first condition fails, the rest are skipped, saving gas. This approach is more gas-efficient, especially when dealing with complex or gas-intensive conditions. However, it's crucial to balance gas savings with code readability and maintainability, ensuring that the code remains clear and easy to understand.

Num of instances: 49

### Findings 


<details><summary>Click to show findings</summary>

['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L185-L185)']
```solidity
185:        if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) { // <= FOUND
186:             revert NoyaAccounting_INSUFFICIENT_FUNDS(balanceOf(from), amount, withdrawRequestsByAddress[from]);
187:         }
```
['[285](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L285-L285)']
```solidity
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) { // <= FOUND
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         }
```
['[332](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L332-L332)']
```solidity
332:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) { // <= FOUND
333:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
334:         }
```
['[371](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L371-L371)']
```solidity
371:         if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) { // <= FOUND
372:             revert NoyaAccounting_NOT_READY_TO_FULFILL();
373:         }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L40-L40)']
```solidity
40:        if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
41:             revert UnauthorizedAccess();
42:         }
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L47-L47)']
```solidity
47:        if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
48:             revert UnauthorizedAccess();
49:         }
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L66-L66)']
```solidity
66:         if (p.collateral == 0 && p.supplyShares == 0) { // <= FOUND
67:             registry.updateHoldingPosition(
68:                 vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true
69:             );
70:         }
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L223-L223)']
```solidity
223:         if (closePosition && isMarketEmpty(market)) { // <= FOUND
224:             registry.updateHoldingPosition(
225:                 vaultId,
226:                 registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)),
227:                 "",
228:                 "",
229:                 true
230:             );
231:         }
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L111-L111)']
```solidity
111:         if (bAmount > 0 && !isBorrowing) { // <= FOUND
112:             _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount);
113:         }
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L60-L60)']
```solidity
60:         if (closePosition && isSiloEmpty(silo)) { // <= FOUND
61:             registry.updateHoldingPosition(
62:                 vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true
63:             );
64:         }
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L55-L55)']
```solidity
55:         if (msg.sender != emergencyManager && msg.sender != watcherContract) { // <= FOUND
56:             revert NoyaGovernance_Unauthorized(msg.sender);
57:         }
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L142-L142)']
```solidity
142:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) { // <= FOUND
143:             emit UpdateTokenInRegistry(token, remove);
144:             registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);
145:         }
```
['[86](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L86-L86)']
```solidity
86:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) { // <= FOUND
87:             registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);
88:         }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L102-L102)']
```solidity
102:         if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) { // <= FOUND
103:             
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
```
['[82](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L82-L82)']
```solidity
82:         if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) { // <= FOUND
83:             timeWeightedAverageTick--;
84:         }
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L185-L185)']
```solidity
185:         if (!(from == address(0)) && balanceOf(from) < amount + withdrawRequestsByAddress[from]) { // <= FOUND
```
['[229](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L229-L231)']
```solidity
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime // <= FOUND
231:                 && i < maxIterations // <= FOUND
232:         ) {
```
['[264](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L264-L266)']
```solidity
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI // <= FOUND
267:         ) {
```
['[285](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L285-L285)']
```solidity
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) { // <= FOUND
```
['[332](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L332-L332)']
```solidity
332:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) { // <= FOUND
```
['[335](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L335-L337)']
```solidity
335:         while (
336:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime // <= FOUND
337:                 && i < maxIterations // <= FOUND
338:         ) {
```
['[358](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L358-L358)']
```solidity
358:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false); // <= FOUND
```
['[368](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L368-L368)']
```solidity
368:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false); // <= FOUND
```
['[371](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L371-L371)']
```solidity
371:         if (neededAssets != 0 && amountAskedForWithdraw != currentWithdrawGroup.totalCBAmount) { // <= FOUND
```
['[403](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L403-L407)']
```solidity
403:         
404:         while (
405:             currentWithdrawGroup.lastId > firstTemp
406:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp // <= FOUND
407:                 && i < maxIterations // <= FOUND
408:         ) {
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L40-L40)']
```solidity
40:         if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L47-L47)']
```solidity
47:         if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
```
['[339](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L339-L339)']
```solidity
339:         if (positionIndex == 0 && removePosition) return type(uint256).max; // <= FOUND
```
['[433](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L433-L433)']
```solidity
433:         return position.isEnabled && (!position.onlyOwner || position.calculatorConnector == connector); // <= FOUND
```
['[126](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L126-L126)']
```solidity
126:         address poolAddress = (poolInfo.tokens.length > 2 && poolInfo.zap != address(0)) ? poolInfo.zap : pool; // <= FOUND
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L66-L66)']
```solidity
66:         if (p.collateral == 0 && p.supplyShares == 0) { // <= FOUND
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L223-L223)']
```solidity
223:         if (closePosition && isMarketEmpty(market)) { // <= FOUND
```
['[305](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L305-L307)']
```solidity
305:         return (
306:             _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0 // <= FOUND
307:                 && market.balanceOf(address(this)) == 0 // <= FOUND
308:         );
```
['[111](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L111-L111)']
```solidity
111:         if (bAmount > 0 && !isBorrowing) { // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L60-L60)']
```solidity
60:         if (closePosition && isSiloEmpty(silo)) { // <= FOUND
```
['[120](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L120-L120)']
```solidity
120:             if (depositAmount == 0 && borrowAmount == 0) { // <= FOUND
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L28-L28)']
```solidity
28:         require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1); // <= FOUND
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L45-L45)']
```solidity
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) { // <= FOUND
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L48-L48)']
```solidity
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) { // <= FOUND
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L53-L53)']
```solidity
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1); // <= FOUND
```
['[64](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L64-L64)']
```solidity
64:         require(_threshold <= numOwners && _threshold > 1); // <= FOUND
```
['[96](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L96-L96)']
```solidity
96:         require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match"); // <= FOUND
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L106-L106)']
```solidity
106:                 require(recovered > lastAdd && isOwner[recovered]); // <= FOUND
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L55-L55)']
```solidity
55:         if (msg.sender != emergencyManager && msg.sender != watcherContract) { // <= FOUND
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L67-L67)']
```solidity
67:         if (msg.sender != maintainer && msg.sender != emergencyManager) revert NoyaGovernance_Unauthorized(msg.sender); // <= FOUND
```
['[86](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L86-L86)']
```solidity
86:         if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) { // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30-L30)']
```solidity
30:         if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound(); // <= FOUND
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L102-L102)']
```solidity
102:         if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) { // <= FOUND
```
['[82](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L82-L82)']
```solidity
82:         if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) { // <= FOUND
```


</details>

## [Gas-27] Optimize Storage with Byte Truncation for Time Related State Variables

### Resolution 
Storage optimization in Solidity contracts is vital for reducing gas costs, especially when storing time-related state variables. Using `uint32` for storing time values like timestamps is often sufficient, given it can represent dates up to the year 2106. By truncating larger default integer types to `uint32`, you significantly save on storage space and consequently on gas costs for deployment and state modifications. However, ensure that the truncation does not lead to overflow issues and that the variable's size is adequate for the application's expected lifespan and precision requirements. Adopting this optimization practice contributes to more efficient and cost-effective smart contract development.

Num of instances: 5

### Findings 


<details><summary>Click to show findings</summary>

['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L42-L42)']
```solidity
42: uint256 public profitStoredTime; // <= FOUND
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L44-L44)']
```solidity
44: uint256 public lastFeeDistributionTime; // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L81-L81)']
```solidity
81: uint256 public depositWaitingTime = 30 minutes; // <= FOUND
```
['[83](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L83-L83)']
```solidity
83: uint256 public withdrawWaitingTime = 6 hours; // <= FOUND
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L19-L19)']
```solidity
19: uint256 public constant BRIDGE_TXN_WAITING_TIME = 30 minutes; // <= FOUND
```


</details>

## [Gas-28] Using delete instead of setting mapping to 0 saves gas

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L81-L81)']
```solidity
81:         approvedBridgeTXN[txn] = 0; // <= FOUND
```


</details>

## [Gas-29] Stack variable cost less than state variables while used in emiting event

### Resolution 
When emitting events in Solidity, using stack variables (local variables within a function) instead of state variables can lead to significant gas savings. Stack variables reside in memory only for the duration of the function execution and are less costly to access compared to state variables, which are stored on the blockchain. When an event is emitted, accessing these stack variables requires less gas than fetching data from state variables, which involves reading from the contract's storage - a more expensive operation. Thus, for efficiency, prefer using local variables within functions for event emission, especially in functions that are called frequently.

Num of instances: 26

### Findings 


<details><summary>Click to show findings</summary>

['[482](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L482-L483)']
```solidity
482:         emit RecordProfit( // <= FOUND
483:             storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp // <= FOUND
484:         );
```
['[493](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L493-L493)']
```solidity
493:             emit ResetFee(currentProfit, storedProfitForFee, block.timestamp); // <= FOUND
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L58-L58)']
```solidity
58:         emit UpdatedAssetPriceSource(asset, baseToken, oracle); // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L52-L52)']
```solidity
52:         emit PoolsForAsset(tokenIn, baseToken, pool); // <= FOUND
```
['[214](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L214-L214)']
```solidity
214:         emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer); // <= FOUND
```
['[311](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L311-L311)']
```solidity
311:         emit RecordWithdraw(withdrawQueue.last, msg.sender, receiver, share, block.timestamp); // <= FOUND
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L88-L88)']
```solidity
88:         emit TransferTokensToTrustedAddress(token, amount, caller, data); // <= FOUND
```
['[142](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L142-L143)']
```solidity
142:         emit VaultAddressesChanged( // <= FOUND
143:             vaultId, _governer, _maintainer, _maintainerWithoutTimelock, _keeperContract, _watcher, _emergency // <= FOUND
144:         );
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L85-L85)']
```solidity
85:         emit updateFlashloanAddress(_flashLoan, flashLoan); // <= FOUND
```
['[559](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L559-L563)']
```solidity
559:             emit RetrieveTokensForWithdraw( // <= FOUND
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp // <= FOUND
564:             );
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L149-L149)']
```solidity
149:         emit OpenCurvePosition(pool, depositIndex, amount, minAmount); // <= FOUND
```
['[174](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L174-L174)']
```solidity
174:         emit DecreaseCurvePosition(pool, withdrawIndex, amount, minAmount); // <= FOUND
```
['[194](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L194-L194)']
```solidity
194:         emit WithdrawFromConvexRewardPool(pool, amount); // <= FOUND
```
['[204](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L204-L204)']
```solidity
204:         emit WithdrawFromGauge(pool, amount); // <= FOUND
```
['[141](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L141-L141)']
```solidity
141:         emit VaultAdded(vaultId, _accountingManager, _baseToken, _trustedTokens); // <= FOUND
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L193-L193)']
```solidity
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
```
['[213](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L213-L213)']
```solidity
213:         emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted); // <= FOUND
```
['[256](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L256-L256)']
```solidity
256:         emit TrustedPositionAdded(vaultId, positionId, calculatorConnector, _positionTypeId, onlyOwner, _isDebt, _data); // <= FOUND
```
['[273](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L273-L273)']
```solidity
273:         emit TrustedPositionRemoved(vaultId, _positionId); // <= FOUND
```
['[295](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L295-L295)']
```solidity
295:         emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index); // <= FOUND
```
['[353](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L353-L353)']
```solidity
353:             emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex); // <= FOUND
```
['[182](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L182-L182)']
```solidity
182:         emit Forwarded(lifi, address(token), amount, data); // <= FOUND
```
['[535](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L535-L535)']
```solidity
535:         emit CollectPerformanceFee(preformanceFeeSharesWaitingForDistribution); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L60-L60)']
```solidity
60:         emit BorrowAndSupply(address(pool), borrowAmount, collateralAmount); // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L79-L79)']
```solidity
79:         emit Withdraw(address(pool), withdrawAmount); // <= FOUND
```
['[97](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L97-L97)']
```solidity
97:         emit Repay(address(pool), sharesToRepay); // <= FOUND
```


</details>

## [Gas-30] Low level call can be optimized with assembly

### Resolution 
Optimizing low-level calls using assembly in Solidity can be beneficial, particularly when dealing with function return data. Typically, even if return data from a low-level call is not used, Solidity still allocates memory to store it, which incurs gas costs. By using assembly, developers can bypass the automatic memory allocation for unused return data. This manual optimization involves handling the call at the assembly level and deliberately choosing not to store the return data in memory when it's not needed.

Num of instances: 14

### Findings 


<details><summary>Click to show findings</summary>

['[682](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L682-L682)']
```solidity
682:             (bool success,) = payable(msg.sender).call{ value: amount }(""); // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L81-L82)']
```solidity
81:                 
82:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L116-L116)']
```solidity
116:         (bool success,) = destination.call{ gas: gasLimit }(data); // <= FOUND
```
['[176](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176)']
```solidity
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data); // <= FOUND
```
['[195](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195)']
```solidity
195:             (bool success,) = payable(userAddress).call{ value: amount }(""); // <= FOUND
```
['[682](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L682-L682)']
```solidity
682:             (bool success,) = payable(msg.sender).call{ value: amount }(""); // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L81-L82)']
```solidity
81:                 
82:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L116-L116)']
```solidity
116:         (bool success,) = destination.call{ gas: gasLimit }(data); // <= FOUND
```
['[176](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176-L176)']
```solidity
176:         (bool success, bytes memory err) = lifi.call{ value: msg.value }(data); // <= FOUND
```
['[195](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195)']
```solidity
195:             (bool success,) = payable(userAddress).call{ value: amount }(""); // <= FOUND
```
['[682](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L682-L682)']
```solidity
682:             (bool success,) = payable(msg.sender).call{ value: amount }(""); // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L81-L82)']
```solidity
81:                 
82:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L116-L116)']
```solidity
116:         (bool success,) = destination.call{ gas: gasLimit }(data); // <= FOUND
```
['[195](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L195-L195)']
```solidity
195:             (bool success,) = payable(userAddress).call{ value: amount }(""); // <= FOUND
```


</details>

## [Gas-31] Remove unused modifiers

### Resolution 
Unused modifiers in a Solidity contract can clutter the codebase and lead to confusion. It's best to remove any modifiers that are not actively used in the contract. This cleanup enhances code readability and maintainability, making it easier for developers to understand and audit the contract's functionality. Additionally, removing redundant code elements can slightly reduce deployment costs.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L53-L53)']
```solidity
53:     modifier onlyEmergencyOrWatcher() { // <= FOUND
54:         (,,,, address watcherContract, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
55:         if (msg.sender != emergencyManager && msg.sender != watcherContract) {
56:             revert NoyaGovernance_Unauthorized(msg.sender);
57:         }
58:         _;
59:     }
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L85-L85)']
```solidity
85:     modifier onlyGovernance() { // <= FOUND
86:         (address governer,,,,,) = registry.getGovernanceAddresses(vaultId);
87:         if (msg.sender != governer) revert NoyaGovernance_Unauthorized(msg.sender);
88:         _;
89:     }
```


</details>

## [Gas-32] Inline modifiers used only once

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[39](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L39-L39)']
```solidity
39:     modifier onlyVaultMaintainerWithoutTimeLock(uint256 _vaultId) { // <= FOUND
40:         if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
41:             revert UnauthorizedAccess();
42:         }
43:         _;
44:     }
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L46-L46)']
```solidity
46:     modifier onlyVaultGoverner(uint256 _vaultId) { // <= FOUND
47:         if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) {
48:             revert UnauthorizedAccess();
49:         }
50:         _;
51:     }
```


</details>

## [Gas-33] Use s.x = s.x + y instead of s.x += y for memory structs (same for -= etc)

### Resolution 
In Solidity, optimizing gas usage is crucial, particularly for frequently executed operations. For memory structs, using explicit assignment (e.g., `s.x = s.x + y`) instead of shorthand operations (e.g., `s.x += y`) can result in a minor gas saving, around 100 gas. This difference arises from the way the Solidity compiler optimizes bytecode. While such savings might seem small, they can add up in contracts with high transaction volume. This optimization applies to other compound assignment operators like `-=` and `*=` as well. It's a subtle efficiency gain that developers can leverage, especially in complex contracts where every gas unit counts.

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[254](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L254-L281)']
```solidity
254:     function executeDeposit(uint256 maxI, address connector, bytes memory addLPdata)
255:         public
256:         onlyManager
257:         whenNotPaused
258:         nonReentrant
259:     {
260:         uint256 firstTemp = depositQueue.first;
261:         uint64 i = 0;
262:         uint256 processedBaseTokenAmount = 0;
263: 
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1; // <= FOUND
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit(
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount // <= FOUND
273:             );
274:             
275:             _mint(data.receiver, data.shares); // <= FOUND
276: 
277:             processedBaseTokenAmount += data.amount; // <= FOUND
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1; // <= FOUND
280:         }
281:         depositQueue.totalAWFDeposit -= processedBaseTokenAmount; // <= FOUND
282: 
283:         totalDepositedAmount += processedBaseTokenAmount; // <= FOUND
284: 
285:         if (registry.isAnActiveConnector(vaultId, connector) && processedBaseTokenAmount > 0) {
286:             uint256[] memory amounts = new uint256[](1);
287:             amounts[0] = processedBaseTokenAmount;
288:             address[] memory tokens = new address[](1);
289:             tokens[0] = address(baseToken);
290:             IConnector(connector).addLiquidity(tokens, amounts, addLPdata);
291:         } else {
292:             revert NoyaAccounting_INVALID_CONNECTOR();
293:         }
294: 
295:         depositQueue.first = firstTemp;
296:     }
```
['[393](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L393-L415)']
```solidity
393:     function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused { // <= FOUND
394:         if (currentWithdrawGroup.isFullfilled == false) {
395:             revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
396:         }
397:         uint64 i = 0;
398:         uint256 firstTemp = withdrawQueue.first;
399: 
400:         uint256 withdrawFeeAmount = 0;
401:         uint256 processedBaseTokenAmount = 0;
402:         
403:         while (
404:             currentWithdrawGroup.lastId > firstTemp
405:                 && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp
406:                 && i < maxIterations
407:         ) {
408:             i += 1; // <= FOUND
409:             WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
410:             uint256 shares = data.shares; // <= FOUND
411:             
412:             uint256 baseTokenAmount =
413:                 data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled; // <= FOUND
414: 
415:             withdrawRequestsByAddress[data.owner] -= shares; // <= FOUND
416:             _burn(data.owner, shares); // <= FOUND
417: 
418:             processedBaseTokenAmount += data.amount; // <= FOUND
419:             {
420:                 uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
421:                 withdrawFeeAmount += feeAmount; // <= FOUND
422:                 baseTokenAmount = baseTokenAmount - feeAmount;
423:             }
424: 
425:             baseToken.safeTransfer(data.receiver, baseTokenAmount); // <= FOUND
426:             emit ExecuteWithdraw(
427:                 firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp // <= FOUND
428:             );
429:             delete withdrawQueue.queue[firstTemp];
430:             
431:             firstTemp += 1; // <= FOUND
432:         }
433:         totalWithdrawnAmount += processedBaseTokenAmount; // <= FOUND
434: 
435:         if (withdrawFeeAmount > 0) {
436:             baseToken.safeTransfer(withdrawFeeReceiver, withdrawFeeAmount);
437:         }
438:         withdrawQueue.first = firstTemp;
439:         
440:         if (currentWithdrawGroup.lastId == firstTemp) {
441:             delete currentWithdrawGroup;
442:         }
443:     }
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L95-L120)']
```solidity
95:     function getCollBlanace(IComet comet, bool riskAdjusted) public view returns (uint256 CollValue) { // <= FOUND
96:         IComet.UserBasic memory userBasic = comet.userBasic(address(this));
97:         uint16 assetsIn = userBasic.assetsIn;
98:         uint256 basePrice = comet.getPrice(comet.baseTokenPriceFeed());
99:         uint256 baseScale = comet.baseScale();
100:         if (userBasic.principal > 0) {
101:             uint256 principalInBase = uint256(uint104(userBasic.principal));
102:             CollValue += principalInBase; // <= FOUND
103:         }
104:         uint8 numberOfAssets = comet.numAssets();
105: 
106:         
107:         for (uint8 i; i < numberOfAssets; ++i) {
108:             if (isInAsset(assetsIn, i)) {
109:                 IComet.AssetInfo memory info = comet.getAssetInfo(i);
110: 
111:                 
112:                 (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset); // <= FOUND
113: 
114:                 
115:                 uint256 collateralPriceInVirtualBase = comet.getPrice(info.priceFeed); // <= FOUND
116: 
117:                 uint256 collateralValueInVirtualBase =
118:                     collateralBalance * collateralPriceInVirtualBase * baseScale / info.scale / basePrice; // <= FOUND
119:                 if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18; // <= FOUND
120:                 else CollValue += collateralValueInVirtualBase; // <= FOUND
121:             } 
122:         }
123:     }
```
['[257](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L257-L280)']
```solidity
257:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
258:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
259:         if (positionInfo.positionTypeId == PENDLE_POSITION_ID) { // <= FOUND
260:             uint256 underlyingBalance = 0;
261:             address market = abi.decode(positionInfo.data, (address)); // <= FOUND
262:             (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
263:             (, address _underlyingToken,) = _SY.assetInfo();
264: 
265:             uint256 SYAmount = _SY.balanceOf(address(this));
266: 
267:             
268:             uint256 lpBalance =
269:                 IERC20(market).balanceOf(address(this)) + pendleMarketDepositHelper.balance(market, address(this));
270:             if (lpBalance > 0) {
271:                 SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18; // <= FOUND
272:             }
273: 
274:             uint256 PTAmount = _PT.balanceOf(address(this));
275:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18; // <= FOUND
276: 
277:             uint256 YTBalance = _YT.balanceOf(address(this));
278:             if (YTBalance > 0) SYAmount += getYTValue(market, YTBalance); // <= FOUND
279: 
280:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18; // <= FOUND
281: 
282:             tvl = valueOracle.getValue(_underlyingToken, base, underlyingBalance);
283:         }
284:         return tvl;
285:     }
```
['[127](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L127-L149)']
```solidity
127:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
128:         PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
129:         uint256 tokenId = abi.decode(p.data, (uint256));
130:         (address token0, address token1) = abi.decode(positionInfo.data, (address, address)); // <= FOUND
131:         uint256 amount0;
132:         uint256 amount1;
133:         (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));
134:         {
135:             IUniswapV3Pool pool = IUniswapV3Pool(factory.getPool(token0, token1, fee));
136:             bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));
137: 
138:             (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);
139: 
140:             (uint160 sqrtPriceX96,,,,,,) = pool.slot0();
141:             (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
142:                 sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity
143:             );
144:             amount0 += tokensOwed0; // <= FOUND
145:             amount1 += tokensOwed1; // <= FOUND
146:         }
147: 
148:         tvl += valueOracle.getValue(token0, base, amount0); // <= FOUND
149:         tvl += valueOracle.getValue(token1, base, amount1); // <= FOUND
150:     }
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L109-L125)']
```solidity
109:     function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) { // <= FOUND
110:         PositionBP memory bp = registry.getPositionBP(vaultId, p.positionId);
111:         (address siloToken) = abi.decode(bp.data, (address)); // <= FOUND
112:         ISilo silo = ISilo(siloRepository.getSilo(siloToken));
113:         (address[] memory assets, IBaseSilo.AssetStorage[] memory assetsS) = silo.getAssetsWithState();
114:         uint256 totalDepositAmount = 0;
115:         uint256 totalBAmount = 0;
116:         for (uint256 i = 0; i < assets.length; i++) {
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)); // <= FOUND
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));
120:             if (depositAmount == 0 && borrowAmount == 0) {
121:                 continue;
122:             }
123:             uint256 price = _getValue(assets[i], base, 1e18);
124:             totalDepositAmount += depositAmount * price / 1e18; // <= FOUND
125:             totalBAmount += borrowAmount * price / 1e18; // <= FOUND
126:         }
127:         tvl = totalDepositAmount - totalBAmount;
128:     }
```


</details>

## [Gas-34] Variable declared within iteration

### Resolution 
Please elaborate and generalise the following with detail and  feel free to use your own knowledge and lmit ur words to 100 words please: 

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[548](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L548-L549)']
```solidity
548:        for (uint256 i = 0; i < retrieveData.length; i++) { // <= FOUND
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) { // <= FOUND
550:                 continue;
551:             } // <= FOUND
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress( // <= FOUND
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         } // <= FOUND
```
['[548](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L548-L549)']
```solidity
548:         for (uint256 i = 0; i < retrieveData.length; i++) { // <= FOUND
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) { // <= FOUND
550:                 continue;
551:             } // <= FOUND
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress( // <= FOUND
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         } // <= FOUND
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L113-L117)']
```solidity
113:        for (uint256 i = 0; i < markets.length; i++) { // <= FOUND
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value); // <= FOUND
115:             if (amounts[i].sign) { // <= FOUND
116:                 totalCollateral += value;
117:             } else { // <= FOUND
118:                 totalDebt += value;
119:             }
120:         }
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L113-L117)']
```solidity
113:         for (uint256 i = 0; i < markets.length; i++) { // <= FOUND
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value); // <= FOUND
115:             if (amounts[i].sign) { // <= FOUND
116:                 totalCollateral += value;
117:             } else { // <= FOUND
118:                 totalDebt += value;
119:             }
120:         }
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L116-L120)']
```solidity
116:        for (uint256 i = 0; i < assets.length; i++) { // <= FOUND
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this)); // <= FOUND
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this)); // <= FOUND
120:             if (depositAmount == 0 && borrowAmount == 0) { // <= FOUND
121:                 continue;
122:             } // <= FOUND
123:             uint256 price = _getValue(assets[i], base, 1e18);
124:             totalDepositAmount += depositAmount * price / 1e18;
125:             totalBAmount += borrowAmount * price / 1e18;
126:         } // <= FOUND
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L116-L120)']
```solidity
116:         for (uint256 i = 0; i < assets.length; i++) { // <= FOUND
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this)); // <= FOUND
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this)); // <= FOUND
120:             if (depositAmount == 0 && borrowAmount == 0) { // <= FOUND
121:                 continue;
122:             } // <= FOUND
123:             uint256 price = _getValue(assets[i], base, 1e18);
124:             totalDepositAmount += depositAmount * price / 1e18;
125:             totalBAmount += borrowAmount * price / 1e18;
126:         } // <= FOUND
```


</details>

## [Gas-35] Internal functions only used once can be inlined to save gas

### Resolution 
If a internal function is only used once it doesn't make sense to modularise it unless the function which does call the function would be overly long and complex otherwise

Num of instances: 6

### Findings 


<details><summary>Click to show findings</summary>

['[120](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L120-L120)']
```solidity
120:     function _getHealthFactor(IFraxPair _fraxlendPair, uint256 _exchangeRate) internal view virtual returns (uint256)  // <= FOUND
```
['[221](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L221-L221)']
```solidity
221:     function _executeSwap(SwapRequest memory swapRequest) internal returns (uint256 amountOut)  // <= FOUND
```
['[267](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L267-L267)']
```solidity
267:     function _addLiquidity(address[] memory, uint256[] memory, bytes memory) internal virtual returns (bool)  // <= FOUND
```
['[285](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L285-L285)']
```solidity
285:     function _revokeApproval(address _token, address _spender) internal virtual  // <= FOUND
```
['[185](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L185-L185)']
```solidity
185:     function _setAllowance(IERC20 token, address spender, uint256 amount) internal  // <= FOUND
```
['[189](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L189-L189)']
```solidity
189:     function _isNative(IERC20 token) internal pure returns (bool isNative)  // <= FOUND
```


</details>

## [Gas-36] Constructors can be marked as payable to save deployment gas

Num of instances: 36

### Findings 


<details><summary>Click to show findings</summary>

['[93](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L93-L93)']
```solidity
93:     constructor(AccountingManagerConstructorParams memory p)
94:         ERC4626(IERC20(p._baseTokenAddress))
95:         ERC20(p._name, p._symbol)
96:         NoyaGovernanceBase(PositionRegistry(p._registry), p._vaultId)
97:     {
98:         baseToken = IERC20(p._baseTokenAddress);
99:         valueOracle = INoyaValueOracle(p._valueOracle);
100:         lastFeeDistributionTime = block.timestamp;
101:         withdrawFeeReceiver = p._withdrawFeeReceiver;
102:         performanceFeeReceiver = p._performanceFeeReceiver;
103:         managementFeeReceiver = p._managementFeeReceiver;
104: 
105:         require(p._baseTokenAddress != address(0));
106:         require(p._valueOracle != address(0));
107:         require(p._withdrawFeeReceiver != address(0));
108:         require(p._performanceFeeReceiver != address(0));
109:         require(p._managementFeeReceiver != address(0));
110: 
111:         if (
112:             p._withdrawFee > WITHDRAWAL_MAX_FEE || p._performanceFee > PERFORMANCE_MAX_FEE
113:                 || p._managementFee > MANAGEMENT_MAX_FEE
114:         ) {
115:             revert NoyaAccounting_INVALID_FEE();
116:         }
117:         withdrawFee = p._withdrawFee;
118:         performanceFee = p._performanceFee;
119:         managementFee = p._managementFee;
120:     }
```
['[14](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/NoyaFeeReceiver.sol#L14-L14)']
```solidity
14:     constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
15:         require(_accountingManager != address(0));
16:         require(_baseToken != address(0));
17:         require(_receiver != address(0));
18:         accountingManager = _accountingManager;
19:         baseToken = _baseToken;
20:         receiver = _receiver;
21:     }
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L66-L66)']
```solidity
66:     constructor(address _governer, address _maintainer, address _emergency, address _flashLoan) {
67:         require(_governer != address(0));
68:         require(_maintainer != address(0));
69:         require(_emergency != address(0));
70:         _grantRole(GOVERNER_ROLE, _governer);
71:         _grantRole(MAINTAINER_ROLE, _maintainer);
72:         _grantRole(EMERGENCY_ROLE, _emergency);
73:         _setRoleAdmin(GOVERNER_ROLE, GOVERNER_ROLE);
74:         _setRoleAdmin(MAINTAINER_ROLE, GOVERNER_ROLE);
75:         _setRoleAdmin(EMERGENCY_ROLE, GOVERNER_ROLE);
76:         flashLoan = _flashLoan;
77:     }
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L32-L32)']
```solidity
32:     constructor(address _pool, address _poolBaseToken, BaseConnectorCP memory baseConnectorParams)
33:         BaseConnector(baseConnectorParams)
34:     {
35:         require(_pool != address(0));
36:         require(_poolBaseToken != address(0));
37:         poolBaseToken = _poolBaseToken;
38:         pool = _pool;
39:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L40-L40)']
```solidity
40:     constructor(address _router, address _voter, BaseConnectorCP memory baseConnectorParams)
41:         BaseConnector(baseConnectorParams)
42:     {
43:         require(_router != address(0));
44:         aerodromeRouter = IRouter(_router);
45:         voter = IVoter(_voter);
46:     }
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L42-L42)']
```solidity
42:     constructor(address _balancerVault, address bal, address aura, BaseConnectorCP memory baseConnectorParams)
43:         BaseConnector(baseConnectorParams)
44:     {
45:         require(_balancerVault != address(0));
46:         require(bal != address(0));
47:         require(aura != address(0));
48:         AURA = aura;
49:         BAL = bal;
50:         balancerVault = _balancerVault;
51:     }
```
['[24](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L24-L24)']
```solidity
24:     constructor(address _balancerVault, PositionRegistry _registry) {
25:         require(_balancerVault != address(0));
26:         require(address(_registry) != address(0));
27:         vault = IBalancerVault(_balancerVault);
28:         registry = _registry;
29:     }
```
['[36](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L36-L36)']
```solidity
36:     constructor(address _router, address _factory, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
37:         require(_router != address(0));
38:         require(_factory != address(0));
39:         router = ICamelotRouter(_router);
40:         factory = ICamelotFactory(_factory);
41:     }
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L17-L17)']
```solidity
17:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L45-L45)']
```solidity
45:     constructor(
46:         address _convexBooster,
47:         address cvx,
48:         address crv,
49:         address prisma,
50:         BaseConnectorCP memory baseConnectorParams
51:     ) BaseConnector(baseConnectorParams) {
52:         require(_convexBooster != address(0));
53:         require(cvx != address(0));
54:         require(crv != address(0));
55:         require(prisma != address(0));
56:         convexBooster = IBooster(_convexBooster);
57:         CVX = cvx;
58:         CRV = crv;
59:         PRISMA = prisma;
60:     }
```
['[18](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L18-L18)']
```solidity
18:     constructor(
19:         address _depositWithdrawalProxy,
20:         address _dolomiteMargin,
21:         address _borrowPositionProxy,
22:         BaseConnectorCP memory baseConnectorParams
23:     ) BaseConnector(baseConnectorParams) {
24:         require(_depositWithdrawalProxy != address(0));
25:         depositWithdrawalProxy = IDepositWithdrawalProxy(_depositWithdrawalProxy);
26:         dolomiteMargin = IDolomiteMargin(_dolomiteMargin);
27:         borrowPositionProxy = IBorrowPositionProxyV1(_borrowPositionProxy);
28:     }
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L17-L17)']
```solidity
17:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L17-L17)']
```solidity
17:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
['[20](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L20-L20)']
```solidity
20:     constructor(address _lido, address _lidoW, address _steth, address w, BaseConnectorCP memory baseConnectorParams)
21:         BaseConnector(baseConnectorParams)
22:     {
23:         require(_lido != address(0));
24:         require(_lidoW != address(0));
25:         require(_steth != address(0));
26:         require(w != address(0));
27:         lido = _lido;
28:         lidoWithdrawal = _lidoW;
29:         steth = _steth;
30:         weth = w;
31:     }
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L43-L43)']
```solidity
43:     constructor(address _mav, address _veMav, address mr, address pi, BaseConnectorCP memory baseCP)
44:         BaseConnector(baseCP)
45:     {
46:         require(_mav != address(0));
47:         require(_veMav != address(0));
48:         require(mr != address(0));
49:         require(pi != address(0));
50:         mav = _mav;
51:         veMav = _veMav;
52:         maverickRouter = mr;
53:         positionInspector = IPositionInspector(pi);
54:     }
```
['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L23-L23)']
```solidity
23:     constructor(address MB, BaseConnectorCP memory baseCP) BaseConnector(baseCP) {
24:         require(MB != address(0));
25:         morphoBlue = IMorpho(MB);
26:     }
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L19-L19)']
```solidity
19:     constructor(address MC, address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
20:         UNIv3Connector(_positionManager, _factory, baseConnectorParams)
21:     {
22:         require(MC != address(0));
23:         masterchef = IMasterchefV3(MC);
24:     }
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L57-L57)']
```solidity
57:     constructor(address _pendleMarketDepositHelper, address _pendleRouter, address SR, BaseConnectorCP memory baseCP)
58:         BaseConnector(baseCP)
59:     {
60:         require(_pendleMarketDepositHelper != address(0));
61:         require(_pendleRouter != address(0));
62:         require(SR != address(0));
63:         pendleMarketDepositHelper = IPendleMarketDepositHelper(_pendleMarketDepositHelper);
64:         pendleRouter = IPAllActionV3(_pendleRouter);
65:         staticRouter = IPendleStaticRouter(SR);
66:     }
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L17-L17)']
```solidity
17:     constructor(BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) { }
```
['[20](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L20-L20)']
```solidity
20:     constructor(address _SNXCoreProxy, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
21:         require(_SNXCoreProxy != address(0));
22:         SNXCoreProxy = IV3CoreProxy(_SNXCoreProxy);
23:     }
```
['[17](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L17-L17)']
```solidity
17:     constructor(address SR, BaseConnectorCP memory baseConnectorParams) BaseConnector(baseConnectorParams) {
18:         require(SR != address(0));
19: 
20:         siloRepository = ISiloRepository(SR);
21:         MINIMUM_HEALTH_FACTOR = 5e17;
22: 
23:         minimumHealthFactor = MINIMUM_HEALTH_FACTOR;
24:     }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L33-L33)']
```solidity
33:     constructor(address lpStacking, address _stargateRouter, BaseConnectorCP memory baseConnectorParams)
34:         BaseConnector(baseConnectorParams)
35:     {
36:         require(lpStacking != address(0));
37:         require(_stargateRouter != address(0));
38: 
39:         LPStaking = IStargateLPStaking(lpStacking);
40:         stargateRouter = IStargateRouter(_stargateRouter);
41:         rewardToken = LPStaking.stargate();
42:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L27-L27)']
```solidity
27:     constructor(address _positionManager, address _factory, BaseConnectorCP memory baseConnectorParams)
28:         BaseConnector(baseConnectorParams)
29:     {
30:         positionManager = INonfungiblePositionManager(_positionManager);
31:         factory = IUniswapV3Factory(_factory);
32:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L27-L27)']
```solidity
27:     constructor(address[] memory _owners, uint8 _threshold) EIP712("Keepers", "1") Ownable2Step() Ownable(msg.sender) {
28:         require(_owners.length <= 10 && _threshold <= _owners.length && _threshold > 1);
29:         for (uint256 i = 0; i < _owners.length; i++) {
30:             isOwner[_owners[i]] = true;
31:         }
32:         numOwners = _owners.length;
33:         threshold = _threshold;
34:     }
```
['[21](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/NoyaGovernanceBase.sol#L21-L21)']
```solidity
21:     constructor(PositionRegistry _registry, uint256 _vaultId) {
22:         require(address(_registry) != address(0));
23:         registry = _registry;
24:         vaultId = _vaultId;
25:     }
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/TimeLock.sol#L7-L7)']
```solidity
7:     constructor(uint256 minDelay, address[] memory proposers, address[] memory executors, address owner)
8:         TimelockController(minDelay, proposers, executors, owner)
9:     { }
```
['[7](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Watchers.sol#L7-L7)']
```solidity
7:     constructor(address[] memory _owners, uint8 _threshold) Keepers(_owners, _threshold) { }
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L33-L33)']
```solidity
33:     constructor(BaseConnectorCP memory params) NoyaGovernanceBase(params.registry, params.vaultId) {
34:         swapHandler = params.swapHandler;
35:         valueOracle = params.valueOracle;
36:         minimumHealthFactor = MINIMUM_HEALTH_FACTOR;
37:     }
```
['[22](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L22-L22)']
```solidity
22:     constructor(address _registry, uint256 _vaultId) {
23:         registry = PositionRegistry(_registry);
24:         vaultId = _vaultId;
25:     }
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperReceiver.sol#L31-L31)']
```solidity
31:     constructor(address _endpoint, address _owner) OAppReceiver() OAppCore(_endpoint, _owner) { }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L29-L29)']
```solidity
29:     constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
```
['[34](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L34-L34)']
```solidity
34:     constructor(address[] memory usersAddresses, address _valueOracle, PositionRegistry _registry, uint256 _vaultId)
35:         NoyaGovernanceBase(_registry, _vaultId)
36:     {
37:         for (uint256 i = 0; i < usersAddresses.length; i++) {
38:             isEligibleToUse[usersAddresses[i]] = true;
39:         }
40:         valueOracle = INoyaValueOracle(_valueOracle);
41:         require(_valueOracle != address(0));
42:     }
```
['[27](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L27-L27)']
```solidity
27:     constructor(address swapHandler, address _lifi) Ownable2Step() Ownable(msg.sender) {
28:         isHandler[swapHandler] = true;
29:         lifi = _lifi;
30:     }
```
['[29](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L29-L29)']
```solidity
29:     constructor(PositionRegistry _registry) {
30:         require(address(_registry) != address(0));
31:         registry = _registry;
32:     }
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L44-L44)']
```solidity
44:     constructor(address _reg) {
45:         require(_reg != address(0));
46:         registry = PositionRegistry(_reg);
47:     }
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L31-L31)']
```solidity
31:     constructor(address _factory, PositionRegistry _registry) {
32:         factory = _factory;
33:         registry = _registry;
34:     }
```


</details>

## [Gas-37] Empty functions should be removed to save gas

Num of instances: 1

### Findings 


<details><summary>Click to show findings</summary>

['[8](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Watchers.sol#L8-L8)']
```solidity
8:     function verifyRemoveLiquidity(uint256 withdrawAmount, uint256 sentAmount, bytes memory data) external view { }
```


</details>

## [Gas-38] There are comparisons to boolean literals (true and false), these can be simplified to save gas

### Resolution 
In Solidity, gas optimization is crucial due to the cost associated with executing operations on the Ethereum network. Simplifying comparisons to boolean literals is one such optimization technique. Instead of explicitly comparing a boolean expression to true or false, you can use the expression directly or its negation. For example, replace if (x == true) with if (x) and if (x == false) with if (!x). This simplification reduces the bytecode size of the contract, thereby saving gas. It also enhances code readability and clarity.

Num of instances: 12

### Findings 


<details><summary>Click to show findings</summary>

['[332](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L332-L332)']
```solidity
332:         if (currentWithdrawGroup.isFullfilled == false && currentWithdrawGroup.isStarted == true) { // <= FOUND
```
['[358](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L358-L358)']
```solidity
358:         require(currentWithdrawGroup.isStarted == false && currentWithdrawGroup.isFullfilled == false); // <= FOUND
```
['[368](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L368-L368)']
```solidity
368:         require(currentWithdrawGroup.isStarted == true && currentWithdrawGroup.isFullfilled == false); // <= FOUND
```
['[394](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L394-L394)']
```solidity
394:         if (currentWithdrawGroup.isFullfilled == false) { // <= FOUND
```
['[615](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L615-L616)']
```solidity
615:         if ( 
616:             currentWithdrawGroup.isStarted == false || currentWithdrawGroup.isFullfilled == true // <= FOUND
617:                 || availableAssets >= currentWithdrawGroup.totalCBAmount
618:         ) {
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L33-L33)']
```solidity
33:         if (msg.sender != vaults[_vaultId].maintainer || hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L40-L40)']
```solidity
40:         if (msg.sender != vaults[_vaultId].maintainerWithoutTimeLock && hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L47-L47)']
```solidity
47:         if (msg.sender != vaults[_vaultId].governer && hasRole(EMERGENCY_ROLE, msg.sender) == false) { // <= FOUND
```
['[245](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L245-L245)']
```solidity
245:             if (vault.connectors[calculatorConnector].enabled == false) revert NotExist(); // <= FOUND
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L153-L153)']
```solidity
153:         if (isBridgeWhiteListed[bridgeData.bridge] == false) revert BridgeBlacklisted(); // <= FOUND
```
['[154](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L154-L154)']
```solidity
154:         if (isChainSupported[bridgeData.destinationChainId] == false) revert InvalidChainId(); // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L35-L35)']
```solidity
35:         require(isHandler[msg.sender] == true, "LifiImplementation: INVALID_SENDER"); // <= FOUND
```


</details>

## [Gas-39] Only emit event in setter function if the state variable was changed

### Resolution 
Emitting events in setter functions of smart contracts only when state variables change saves gas. This is because emitting events consumes gas, and unnecessary events, where no actual state change occurs, lead to wasteful consumption.

Num of instances: 21

### Findings 


<details><summary>Click to show findings</summary>

['[169](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L169-L179)']
```solidity
169:     function setFees(uint256 _withdrawFee, uint256 _performanceFee, uint256 _managementFee) public onlyMaintainer { // <= FOUND
170:         if (
171:             _withdrawFee > WITHDRAWAL_MAX_FEE || _performanceFee > PERFORMANCE_MAX_FEE
172:                 || _managementFee > MANAGEMENT_MAX_FEE
173:         ) {
174:             revert NoyaAccounting_INVALID_FEE();
175:         }
176:         withdrawFee = _withdrawFee;
177:         performanceFee = _performanceFee;
178:         managementFee = _managementFee;
179:         emit FeeRatesChanged(_withdrawFee, _performanceFee, _managementFee); // <= FOUND
180:     }
```
['[664](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L664-L667)']
```solidity
664:     function setDepositLimits(uint256 _depositLimitPerTransaction, uint256 _depositTotalAmount) public onlyMaintainer { // <= FOUND
665:         depositLimitPerTransaction = _depositLimitPerTransaction;
666:         depositLimitTotalAmount = _depositTotalAmount;
667:         emit SetDepositLimits(_depositLimitPerTransaction, _depositTotalAmount); // <= FOUND
668:     }
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L84-L85)']
```solidity
84:     function setFlashLoanAddress(address _flashLoan) external onlyRole(MAINTAINER_ROLE) { // <= FOUND
85:         emit updateFlashloanAddress(_flashLoan, flashLoan); // <= FOUND
86:         flashLoan = _flashLoan;
87:     }
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L63-L66)']
```solidity
63:     function setThreshold(uint8 _threshold) public onlyOwner { // <= FOUND
64:         require(_threshold <= numOwners && _threshold > 1);
65:         threshold = _threshold;
66:         emit UpdateThreshold(_threshold); // <= FOUND
67:     }
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L48-L50)']
```solidity
48:     function setValueOracle(address _valueOracle) external onlyMaintainerOrEmergency { // <= FOUND
49:         valueOracle = INoyaValueOracle(_valueOracle);
50:         emit SetValueOracle(_valueOracle); // <= FOUND
51:     }
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57-L59)']
```solidity
57:     function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency { // <= FOUND
58:         genericSlippageTolerance = _slippageTolerance;
59:         emit SetSlippageTolerance(address(0), address(0), _slippageTolerance); // <= FOUND
60:     }
```
['[68](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L68-L73)']
```solidity
68:     function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance) // <= FOUND
69:         external
70:         onlyMaintainerOrEmergency
71:     {
72:         slippageTolerance[_inputToken][_outputToken] = _slippageTolerance;
73:         emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance); // <= FOUND
74:     }
```
['[158](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L158-L160)']
```solidity
158:     function setEnableRoute(uint256 _routeId, bool enable) external onlyMaintainerOrEmergency { // <= FOUND
159:         routes[_routeId].isEnabled = enable;
160:         emit RouteUpdate(_routeId, false); // <= FOUND
161:     }
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L66-L72)']
```solidity
66:     function setAssetSources(address[] calldata assets, address[] calldata baseTokens, address[] calldata sources) // <= FOUND
67:         external
68:         onlyMaintainer
69:     {
70:         for (uint256 i = 0; i < assets.length; i++) {
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
73:         }
74:     }
```
['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L203-L213)']
```solidity
203:     function updateConnectorTrustedTokens( // <= FOUND
204:         uint256 vaultId,
205:         address _connectorAddress,
206:         address[] calldata _tokens,
207:         bool trusted
208:     ) external onlyVaultMaintainer(vaultId) vaultExists(vaultId) {
209:         Vault storage vault = vaults[vaultId];
210:         for (uint256 i = 0; i < _tokens.length; i++) {
211:             vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = trusted;
212:         }
213:         emit ConnectorTrustedTokensUpdated(vaultId, _connectorAddress, _tokens, trusted); // <= FOUND
214:     }
```
['[40](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L40-L43)']
```solidity
40:     function updatePosition(uint256 tokenId) public onlyManager nonReentrant { // <= FOUND
41:         masterchef.updateLiquidity(tokenId);
42:         _updateTokenInRegistry(masterchef.CAKE());
43:         emit UpdatePosition(tokenId); // <= FOUND
44:     }
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L42-L55)']
```solidity
42:     function updateOwners(address[] memory _owners, bool[] memory addOrRemove) public onlyOwner { // <= FOUND
43:         uint256 numOwnersTemp = numOwners;
44:         for (uint256 i = 0; i < _owners.length; i++) {
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) {
46:                 isOwner[_owners[i]] = true;
47:                 numOwnersTemp++;
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) {
49:                 isOwner[_owners[i]] = false;
50:                 numOwnersTemp--;
51:             }
52:         }
53:         require(numOwnersTemp <= 10 && threshold <= numOwnersTemp && threshold > 1);
54:         numOwners = numOwnersTemp;
55:         emit UpdateOwners(_owners, addOrRemove); // <= FOUND
56:     }
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L45-L50)']
```solidity
45:     function updateMinimumHealthFactor(uint256 _minimumHealthFactor) external onlyMaintainer { // <= FOUND
46:         if (_minimumHealthFactor < MINIMUM_HEALTH_FACTOR) {
47:             revert IConnector_LowHealthFactor(_minimumHealthFactor);
48:         }
49:         minimumHealthFactor = _minimumHealthFactor;
50:         emit MinimumHealthFactorUpdated(_minimumHealthFactor); // <= FOUND
51:     }
```
['[58](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L58-L60)']
```solidity
58:     function updateSwapHandler(address payable _swapHandler) external onlyMaintainer { // <= FOUND
59:         swapHandler = SwapAndBridgeHandler(_swapHandler);
60:         emit SwapHandlerUpdated(_swapHandler); // <= FOUND
61:     }
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L67-L69)']
```solidity
67:     function updateValueOracle(address _valueOracle) external onlyMaintainer { // <= FOUND
68:         valueOracle = INoyaValueOracle(_valueOracle);
69:         emit ValueOracleUpdated(_valueOracle); // <= FOUND
70:     }
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L37-L44)']
```solidity
37:     function updateDefaultPriceSource(address[] calldata baseCurrencies, INoyaValueOracle[] calldata oracles) // <= FOUND
38:         public
39:         onlyMaintainer
40:     {
41:         for (uint256 i = 0; i < baseCurrencies.length; i++) {
42:             defaultPriceSource[baseCurrencies[i]] = oracles[i];
43:         }
44:         emit UpdatedDefaultPriceSource(baseCurrencies, oracles); // <= FOUND
45:     }
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L51-L58)']
```solidity
51:     function updateAssetPriceSource(address[] calldata asset, address[] calldata baseToken, address[] calldata oracle) // <= FOUND
52:         external
53:         onlyMaintainer
54:     {
55:         for (uint256 i = 0; i < oracle.length; i++) {
56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]);
57:         }
58:         emit UpdatedAssetPriceSource(asset, baseToken, oracle); // <= FOUND
59:     }
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L63)']
```solidity
61:     function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer { // <= FOUND
62:         priceRoutes[asset][base] = s;
63:         emit UpdatedPriceRoute(asset, base, s); // <= FOUND
64:     }
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L53-L58)']
```solidity
53:     function updateChainlinkPriceAgeThreshold(uint256 _chainlinkPriceAgeThreshold) external onlyMaintainer { // <= FOUND
54:         if (_chainlinkPriceAgeThreshold <= 1 hours || _chainlinkPriceAgeThreshold >= 10 days) {
55:             revert NoyaChainlinkOracle_INVALID_INPUT();
56:         }
57:         chainlinkPriceAgeThreshold = _chainlinkPriceAgeThreshold;
58:         emit ChainlinkPriceAgeThresholdUpdated(_chainlinkPriceAgeThreshold); // <= FOUND
59:     }
```
['[670](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L670-L672)']
```solidity
670:     function changeDepositWaitingTime(uint256 _depositWaitingTime) public onlyMaintainer { // <= FOUND
671:         depositWaitingTime = _depositWaitingTime;
672:         emit SetDepositWaitingTime(_depositWaitingTime); // <= FOUND
673:     }
```
['[675](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L675-L677)']
```solidity
675:     function changeWithdrawWaitingTime(uint256 _withdrawWaitingTime) public onlyMaintainer { // <= FOUND
676:         withdrawWaitingTime = _withdrawWaitingTime;
677:         emit SetWithdrawWaitingTime(_withdrawWaitingTime); // <= FOUND
678:     }
```


</details>

## [Gas-40] It is a waste of GAS to emit variable literals

### Resolution 
Emitting variable literals (true, false, 'hello', 1 etc...) in events is inefficient, as it consumes extra gas without providing added value. These literals are fixed values that can be accessed or hardcoded elsewhere in the smart contract or application, making their inclusion in events redundant and an unnecessary drain on resources during transaction execution.

Num of instances: 3

### Findings 


<details><summary>Click to show findings</summary>

['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L59-L59)']
```solidity
59:         emit SetSlippageTolerance(address(0), address(0), _slippageTolerance); // <= FOUND
```
['[295](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L295-L295)']
```solidity
295:         emit HoldingPositionUpdated(vaultId, _positionId, d, AD, false, index); // <= FOUND
```
['[160](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L160-L160)']
```solidity
160:         emit RouteUpdate(_routeId, false); // <= FOUND
```


</details>

## [Gas-41] Use OZ Array.unsafeAccess() to avoid repeated array length checks

### Resolution 
The OpenZeppelin Array.unsafeAccess() method is a optimization strategy for Solidity, aimed at reducing gas costs by bypassing automatic length checks on storage array accesses. In Solidity, every access to an array element involves a hidden gas cost due to a length check, ensuring that accesses do not exceed the array bounds. However, if a developer has already verified the array's bounds earlier in the function or knows through logic that the access is safe, directly accessing the array elements without redundant length checks can save gas. This approach requires careful consideration to avoid out-of-bounds errors, as it trades off safety checks for efficiency.

Num of instances: 77

### Findings 


<details><summary>Click to show findings</summary>

['[549](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L549-L549)']
```solidity
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) { // <= FOUND
```
['[553](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L553-L554)']
```solidity
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress( // <= FOUND
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data // <= FOUND
555:             );
```
['[558](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L558-L558)']
```solidity
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount; // <= FOUND
```
['[559](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L559-L561)']
```solidity
559:             emit RetrieveTokensForWithdraw(
560:                 retrieveData[i].withdrawAmount, // <= FOUND
561:                 retrieveData[i].connectorAddress, // <= FOUND
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
```
['[601](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L601-L601)']
```solidity
601:                 depositData[i] = depositQueue.queue[items[i]]; // <= FOUND
```
['[606](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L606-L606)']
```solidity
606:                 withdrawData[i] = withdrawQueue.queue[items[i]]; // <= FOUND
```
['[138](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L138-L138)']
```solidity
138:             vault.connectors[vault.accountManager].trustedTokens[_trustedTokens[i]] = true; // <= FOUND
```
['[192](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L192-L192)']
```solidity
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i]; // <= FOUND
```
['[193](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L193-L193)']
```solidity
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L211-L211)']
```solidity
211:             vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = trusted; // <= FOUND
```
['[248](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L248-L248)']
```solidity
248:                 if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) { // <= FOUND
```
['[249](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L249-L249)']
```solidity
249:                     revert TokenNotTrusted(usingTokens[i]); // <= FOUND
```
['[269](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L269-L269)']
```solidity
269:             if (vault.holdingPositions[i].positionId == _positionId) { // <= FOUND
```
['[400](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L400-L400)']
```solidity
400:         return vaults[vaultId].holdingPositions[i]; // <= FOUND
```
['[55](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L55-L55)']
```solidity
55:             IRewardPool baseRewardPool = IRewardPool(rewardsPools[i]); // <= FOUND
```
['[78](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L78-L78)']
```solidity
78:             if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]); // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L76-L77)']
```solidity
76:                 
77:                 tokens[i].safeTransfer(receiver, amounts[i]); // <= FOUND
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L77-L77)']
```solidity
77:                 amounts[i] = amounts[i] + feeAmounts[i]; // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L81-L82)']
```solidity
81:                 
82:                 (bool success,) = destinationConnector[i].call{ value: 0, gas: gas[i] }(callingData[i]); // <= FOUND
```
['[86](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L86-L87)']
```solidity
86:                 
87:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), ""); // <= FOUND
```
['[91](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L91-L92)']
```solidity
91:             
92:             tokens[i].safeTransfer(msg.sender, amounts[i]); // <= FOUND
```
['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L92-L92)']
```solidity
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens"); // <= FOUND
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L223-L223)']
```solidity
223:             IRewardsGauge(gauges[i]).claim_rewards(address(this)); // <= FOUND
```
['[235](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L235-L235)']
```solidity
235:             IDepositToken(pools[i]).claimReward(address(this)); // <= FOUND
```
['[249](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L249-L249)']
```solidity
249:             IConvexBasicRewards baseRewardPool = IConvexBasicRewards(rewardsPools[i]); // <= FOUND
```
['[114](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L114-L114)']
```solidity
114:             uint256 value = valueOracle.getValue(tokens[i], base, amounts[i].value); // <= FOUND
```
['[115](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L115-L115)']
```solidity
115:             if (amounts[i].sign) { // <= FOUND
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L70-L70)']
```solidity
70:             if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target); // <= FOUND
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L71-L71)']
```solidity
71:             bytes4 method = bytes4(calls[i].callData[:4]); // <= FOUND
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L74-L74)']
```solidity
74:                 (address token) = abi.decode(calls[i].callData[4:], (address)); // <= FOUND
```
['[136](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L136-L136)']
```solidity
136:             if (earnedInfo[i].earned != 0) { // <= FOUND
```
['[137](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L137-L137)']
```solidity
137:                 tokenIndex = rewardContract.tokenIndex(address(earnedInfo[i].rewardToken)); // <= FOUND
```
['[245](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L245-L245)']
```solidity
245:             _updateTokenInRegistry(rewardTokens[i]); // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L117-L117)']
```solidity
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this)); // <= FOUND
```
['[118](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L118-L118)']
```solidity
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)); // <= FOUND
```
['[119](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L119-L119)']
```solidity
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this)); // <= FOUND
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L123-L123)']
```solidity
123:             uint256 price = _getValue(assets[i], base, 1e18); // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L133-L135)']
```solidity
133:             if (
134:                 IERC20(assetsS[i].collateralToken).balanceOf(address(this)) // <= FOUND
135:                     + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0 // <= FOUND
136:             ) {
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L103-L103)']
```solidity
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]); // <= FOUND
```
['[104](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L104-L104)']
```solidity
104:             _collectFees(tokenIds[i]); // <= FOUND
```
['[107](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L107-L107)']
```solidity
107:             emit CollectFees(tokenIds[i]); // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L30-L30)']
```solidity
30:             isOwner[_owners[i]] = true; // <= FOUND
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L45-L45)']
```solidity
45:             if (addOrRemove[i] && !isOwner[_owners[i]]) { // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L46-L46)']
```solidity
46:                 isOwner[_owners[i]] = true; // <= FOUND
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L48-L48)']
```solidity
48:             } else if (!addOrRemove[i] && isOwner[_owners[i]]) { // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L49-L49)']
```solidity
49:                 isOwner[_owners[i]] = false; // <= FOUND
```
['[105](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L105-L105)']
```solidity
105:                 address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]); // <= FOUND
```
['[180](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L180-L181)']
```solidity
180:             
181:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this)); // <= FOUND
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L44-L44)']
```solidity
44:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, ""); // <= FOUND
```
['[182](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L182-L182)']
```solidity
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this)); // <= FOUND
```
['[183](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L183-L183)']
```solidity
183:             if (_balanceAfter < amounts[i] + _balance) { // <= FOUND
```
['[184](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L184-L184)']
```solidity
184:                 revert IConnector_InsufficientDepositAmount(_balanceAfter - _balance, amounts[i]); // <= FOUND
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L47-L47)']
```solidity
47:             _updateTokenInRegistry(tokens[i]);  // <= FOUND
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L212-L213)']
```solidity
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0) // <= FOUND
214:             );
```
['[215](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L215-L215)']
```solidity
215:             _updateTokenInRegistry(tokensIn[i]); // <= FOUND
```
['[216](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L216-L216)']
```solidity
216:             _updateTokenInRegistry(tokensOut[i]); // <= FOUND
```
['[217](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L217-L217)']
```solidity
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]); // <= FOUND
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L44-L46)']
```solidity
44:             
45: 
46:             ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, ""); // <= FOUND
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L38-L38)']
```solidity
38:             isEligibleToUse[usersAddresses[i]] = true; // <= FOUND
```
['[149](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L149-L149)']
```solidity
149:             routes.push(_routes[i]); // <= FOUND
```
['[150](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L150-L150)']
```solidity
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge); // <= FOUND
```
['[19](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L19-L19)']
```solidity
19:             if (positions[i].calculatorConnector == address(0)) { // <= FOUND
```
['[22](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L22-L22)']
```solidity
22:             uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken); // <= FOUND
```
['[23](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L23-L23)']
```solidity
23:             bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId); // <= FOUND
```
['[45](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L45-L45)']
```solidity
45:             if (latestUpdateTime == 0 || positions[i].positionTimestamp < latestUpdateTime) { // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/TVLHelper.sol#L46-L46)']
```solidity
46:                 latestUpdateTime = positions[i].positionTimestamp; // <= FOUND
```
['[42](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L42-L42)']
```solidity
42:             defaultPriceSource[baseCurrencies[i]] = oracles[i]; // <= FOUND
```
['[56](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L56-L56)']
```solidity
56:             priceSource[asset[i]][baseToken[i]] = INoyaValueOracle(oracle[i]); // <= FOUND
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L89-L89)']
```solidity
89:             initialValue = _getValue(asset, sources[i], initialValue); // <= FOUND
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L90-L90)']
```solidity
90:             quotingToken = sources[i]; // <= FOUND
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L71-L71)']
```solidity
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i]; // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L72-L72)']
```solidity
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L30-L30)']
```solidity
30:         if (routes[_routeId].route == address(0) && !routes[_routeId].isEnabled) revert RouteNotFound(); // <= FOUND
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L99-L99)']
```solidity
99:         RouteData memory swapImplInfo = routes[_swapRequest.routeId]; // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L133-L133)']
```solidity
133:         RouteData memory bridgeImplInfo = routes[_bridgeRequest.routeId]; // <= FOUND
```
['[159](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L159-L159)']
```solidity
159:         routes[_routeId].isEnabled = enable; // <= FOUND
```
['[165](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L165-L165)']
```solidity
165:         if (routes[_routeId].route != addr) { // <= FOUND
```


</details>

## [Gas-42] Use uint256(1)/uint256(2) instead of true/false to save gas for changes

### Resolution 
In Solidity, the use of `uint256` values instead of boolean for certain state variables can result in gas savings. This is due to how Ethereum's storage optimization works: changing a variable from `0` to a non-zero value (like flipping `false` to `true`) incurs a higher gas cost compared to modifying an already non-zero value. By using `uint256` with values `1` and `2` instead of `true` and `false`, you avoid the higher cost associated with the `0` to non-zero change, since `1` and `2` are both non-zero. This approach is notably used in OpenZeppelin's `ReentrancyGuard` as a gas optimization technique. However, this should be applied where it makes sense and where gas optimization is critical, as it can decrease code readability.

Num of instances: 11

### Findings 


<details><summary>Click to show findings</summary>

['[359](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L359-L359)']
```solidity
359:         currentWithdrawGroup.isStarted = true; // <= FOUND
```
['[374](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L374-L374)']
```solidity
374:         currentWithdrawGroup.isFullfilled = true; // <= FOUND
```
['[135](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L135-L136)']
```solidity
135:         
136:         vault.connectors[vault.accountManager].enabled = true; // <= FOUND
```
['[136](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L136-L136)']
```solidity
136:         vault.enabled = true; // <= FOUND
```
['[138](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L138-L138)']
```solidity
138:             vault.connectors[vault.accountManager].trustedTokens[_trustedTokens[i]] = true; // <= FOUND
```
['[30](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L30-L30)']
```solidity
30:             isOwner[_owners[i]] = true; // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L46-L46)']
```solidity
46:                 isOwner[_owners[i]] = true; // <= FOUND
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L38-L38)']
```solidity
38:             isEligibleToUse[usersAddresses[i]] = true; // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L81-L81)']
```solidity
81:         isEligibleToUse[_user] = true; // <= FOUND
```
['[28](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L28-L28)']
```solidity
28:         isHandler[swapHandler] = true; // <= FOUND
```
['[49](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/governance/Keepers.sol#L49-L49)']
```solidity
49:                 isOwner[_owners[i]] = false; // <= FOUND
```


</details>

## [Gas-43] Avoid emitting events in loops

### Resolution 
Emitting events inside loops can significantly increase gas costs in Ethereum smart contracts, as each event emission consumes gas. This practice can quickly escalate transaction fees, especially with a high number of iterations. To optimize for efficiency and cost, it's advisable to minimize event emissions within loops, possibly aggregating data to emit a single event post-loop or reconsidering the design to reduce looped emissions. This approach helps maintain manageable transaction costs and enhances contract performance.

Num of instances: 30

### Findings 


<details><summary>Click to show findings</summary>

['[548](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L548-L559)']
```solidity
548:        for (uint256 i = 0; i < retrieveData.length; i++) {
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw( // <= FOUND
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
```
['[191](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L191-L193)']
```solidity
191:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
194:         }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L102-L107)']
```solidity
102:        for (uint256 i = 0; i < tokenIds.length; i++) {
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]); // <= FOUND
108:         }
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L211-L217)']
```solidity
211:        for (uint256 i = 0; i < tokensIn.length; i++) {
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]); // <= FOUND
218:         }
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L150)']
```solidity
148:        for (uint256 i = 0; i < _routes.length;) {
149:             routes.push(_routes[i]);
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge); // <= FOUND
151:             unchecked {
152:                 i++;
153:             }
154:         }
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L72)']
```solidity
70:        for (uint256 i = 0; i < assets.length; i++) {
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
73:         }
```
['[548](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L548-L559)']
```solidity
548:         for (uint256 i = 0; i < retrieveData.length; i++) {
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw( // <= FOUND
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
```
['[191](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L191-L193)']
```solidity
191:         for (uint256 i = 0; i < _connectorAddresses.length; i++) {
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
194:         }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L102-L107)']
```solidity
102:         for (uint256 i = 0; i < tokenIds.length; i++) {
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]); // <= FOUND
108:         }
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L211-L217)']
```solidity
211:         for (uint256 i = 0; i < tokensIn.length; i++) {
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]); // <= FOUND
218:         }
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L150)']
```solidity
148:         for (uint256 i = 0; i < _routes.length;) {
149:             routes.push(_routes[i]);
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge); // <= FOUND
151:             unchecked {
152:                 i++;
153:             }
154:         }
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L72)']
```solidity
70:         for (uint256 i = 0; i < assets.length; i++) {
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
73:         }
```
['[229](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L229-L239)']
```solidity
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
231:                 && i < maxIterations
232:         ) {
233:             i += 1;
234:             DepositRequest storage data = depositQueue.queue[middleTemp];
235: 
236:             uint256 shares = previewDeposit(data.amount);
237:             data.shares = shares;
238:             data.calculationTime = block.timestamp;
239:             emit CalculateDeposit( // <= FOUND
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
242: 
243:             middleTemp += 1;
244:         }
```
['[264](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L264-L271)']
```solidity
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1;
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit( // <= FOUND
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1;
280:         }
```
['[335](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L335-L346)']
```solidity
335:         while (
336:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
337:                 && i < maxIterations
338:         ) {
339:             i += 1;
340:             WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
341:             uint256 assets = previewRedeem(data.shares);
342:             data.amount = assets;
343:             data.calculationTime = block.timestamp;
344:             assetsNeededForWithdraw += assets;
345:             processedShares += data.shares;
346:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp); // <= FOUND
347: 
348:             middleTemp += 1;
349:         }
```
['[548](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L548-L559)']
```solidity
548:        for (uint256 i = 0; i < retrieveData.length; i++) {
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw( // <= FOUND
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
```
['[191](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L191-L193)']
```solidity
191:        for (uint256 i = 0; i < _connectorAddresses.length; i++) {
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
194:         }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L102-L107)']
```solidity
102:        for (uint256 i = 0; i < tokenIds.length; i++) {
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]); // <= FOUND
108:         }
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L211-L217)']
```solidity
211:        for (uint256 i = 0; i < tokensIn.length; i++) {
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]); // <= FOUND
218:         }
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L150)']
```solidity
148:        for (uint256 i = 0; i < _routes.length;) {
149:             routes.push(_routes[i]);
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge); // <= FOUND
151:             unchecked {
152:                 i++;
153:             }
154:         }
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L72)']
```solidity
70:        for (uint256 i = 0; i < assets.length; i++) {
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
73:         }
```
['[548](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L548-L559)']
```solidity
548:         for (uint256 i = 0; i < retrieveData.length; i++) {
549:             if (!registry.isAnActiveConnector(vaultId, retrieveData[i].connectorAddress)) {
550:                 continue;
551:             }
552:             uint256 balanceBefore = baseToken.balanceOf(address(this));
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data
555:             );
556:             uint256 balanceAfter = baseToken.balanceOf(address(this));
557:             if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
558:             amountAskedForWithdraw_temp += retrieveData[i].withdrawAmount;
559:             emit RetrieveTokensForWithdraw( // <= FOUND
560:                 retrieveData[i].withdrawAmount,
561:                 retrieveData[i].connectorAddress,
562:                 amount,
563:                 amountAskedForWithdraw + amountAskedForWithdraw_temp
564:             );
565:         }
```
['[191](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L191-L193)']
```solidity
191:         for (uint256 i = 0; i < _connectorAddresses.length; i++) {
192:             vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
193:             emit ConnectorAdded(vaultId, _connectorAddresses[i]); // <= FOUND
194:         }
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L102-L107)']
```solidity
102:         for (uint256 i = 0; i < tokenIds.length; i++) {
103:             (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
104:             _collectFees(tokenIds[i]);
105:             _updateTokenInRegistry(token0);
106:             _updateTokenInRegistry(token1);
107:             emit CollectFees(tokenIds[i]); // <= FOUND
108:         }
```
['[211](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L211-L217)']
```solidity
211:         for (uint256 i = 0; i < tokensIn.length; i++) {
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0)
214:             );
215:             _updateTokenInRegistry(tokensIn[i]);
216:             _updateTokenInRegistry(tokensOut[i]);
217:             emit SwapHoldings(tokensIn[i], tokensOut[i], amountsIn[i], swapData[i]); // <= FOUND
218:         }
```
['[148](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L148-L150)']
```solidity
148:         for (uint256 i = 0; i < _routes.length;) {
149:             routes.push(_routes[i]);
150:             emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge); // <= FOUND
151:             unchecked {
152:                 i++;
153:             }
154:         }
```
['[70](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L70-L72)']
```solidity
70:         for (uint256 i = 0; i < assets.length; i++) {
71:             assetsSources[assets[i]][baseTokens[i]] = sources[i];
72:             emit AssetSourceUpdated(assets[i], baseTokens[i], sources[i]); // <= FOUND
73:         }
```
['[229](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L229-L239)']
```solidity
229:         while (
230:             depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
231:                 && i < maxIterations
232:         ) {
233:             i += 1;
234:             DepositRequest storage data = depositQueue.queue[middleTemp];
235: 
236:             uint256 shares = previewDeposit(data.amount);
237:             data.shares = shares;
238:             data.calculationTime = block.timestamp;
239:             emit CalculateDeposit( // <= FOUND
240:                 middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
241:             );
242: 
243:             middleTemp += 1;
244:         }
```
['[264](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L264-L271)']
```solidity
264:         while (
265:             depositQueue.middle > firstTemp
266:                 && depositQueue.queue[firstTemp].calculationTime + depositWaitingTime <= block.timestamp && i < maxI
267:         ) {
268:             i += 1;
269:             DepositRequest memory data = depositQueue.queue[firstTemp];
270: 
271:             emit ExecuteDeposit( // <= FOUND
272:                 firstTemp, data.receiver, block.timestamp, data.shares, data.amount, data.shares * 1e18 / data.amount
273:             );
274:             
275:             _mint(data.receiver, data.shares);
276: 
277:             processedBaseTokenAmount += data.amount;
278:             delete depositQueue.queue[firstTemp];
279:             firstTemp += 1;
280:         }
```
['[335](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L335-L346)']
```solidity
335:         while (
336:             withdrawQueue.last > middleTemp && withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime
337:                 && i < maxIterations
338:         ) {
339:             i += 1;
340:             WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
341:             uint256 assets = previewRedeem(data.shares);
342:             data.amount = assets;
343:             data.calculationTime = block.timestamp;
344:             assetsNeededForWithdraw += assets;
345:             processedShares += data.shares;
346:             emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp); // <= FOUND
347: 
348:             middleTemp += 1;
349:         }
```


</details>

## [Gas-44] Consider pre-calculating the address of address(this) to save gas

### Resolution 
Consider saving the address(this) value within a constant using foundry's script.sol or solady's LibRlp.sol to save gas

Num of instances: 167

### Findings 


<details><summary>Click to show findings</summary>

['[203](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L203-L203)']
```solidity
203:         baseToken.safeTransferFrom(msg.sender, address(this), amount); // <= FOUND
```
['[376](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L376-L376)']
```solidity
376:         uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit; // <= FOUND
```
['[552](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L552-L552)']
```solidity
552:             uint256 balanceBefore = baseToken.balanceOf(address(this)); // <= FOUND
```
['[553](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L553-L554)']
```solidity
553:             uint256 amount = IConnector(retrieveData[i].connectorAddress).sendTokensToTrustedAddress(
554:                 address(baseToken), retrieveData[i].withdrawAmount, address(this), retrieveData[i].data // <= FOUND
555:             );
```
['[556](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L556-L556)']
```solidity
556:             uint256 balanceAfter = baseToken.balanceOf(address(this)); // <= FOUND
```
['[625](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/AccountingManager.sol#L625-L625)']
```solidity
625:         return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this)) // <= FOUND
626:             - depositQueue.totalAWFDeposit;
```
['[47](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L47-L47)']
```solidity
47:         IPool(pool).supply(supplyToken, amount, address(this), 0); // <= FOUND
```
['[48](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L48-L49)']
```solidity
48:         registry.updateHoldingPosition(
49:             vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", false // <= FOUND
50:         );
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L66-L66)']
```solidity
66:         if (!registry.isTokenTrusted(vaultId, _borrowAsset, address(this))) { // <= FOUND
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L69-L69)']
```solidity
69:         IPool(pool).borrow(_borrowAsset, _amount, _interestRateMode, 0, address(this)); // <= FOUND
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L71-L72)']
```solidity
71:         
72:         (,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this)); // <= FOUND
```
['[82](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L82-L82)']
```solidity
82:         IPool(pool).repay(asset, amount, i, address(this)); // <= FOUND
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L100-L100)']
```solidity
100:         IPool(pool).withdraw(_collateral, _collateralAmount, address(this)); // <= FOUND
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L102-L103)']
```solidity
102:         
103:         (uint256 totalCollateralBase,,,,, uint256 healthFactor) = IPool(pool).getUserAccountData(address(this)); // <= FOUND
```
['[106](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L106-L107)']
```solidity
106:             registry.updateHoldingPosition(
107:                 vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", true // <= FOUND
108:             );
```
['[114](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AaveConnector.sol#L114-L114)']
```solidity
114:         (uint256 totalCollateralBase, uint256 totalDebtBase,,,,) = IPool(pool).getUserAccountData(address(this)); // <= FOUND
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L54-L54)']
```solidity
54:         bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool)); // <= FOUND
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L57-L65)']
```solidity
57:         aerodromeRouter.addLiquidity(
58:             IPool(data.pool).token0(),
59:             IPool(data.pool).token1(),
60:             IPool(data.pool).stable(),
61:             data.amount0,
62:             data.amount1,
63:             data.min0Min,
64:             data.min1Min,
65:             address(this), // <= FOUND
66:             data.deadline
67:         );
```
['[82](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L82-L89)']
```solidity
82:         aerodromeRouter.removeLiquidity(
83:             IPool(data.pool).token0(),
84:             IPool(data.pool).token1(),
85:             IPool(data.pool).stable(),
86:             data.amountLiquidity,
87:             data.min0Min,
88:             data.min1Min,
89:             address(this), // <= FOUND
90:             data.deadline
91:         );
```
['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L92-L92)']
```solidity
92:         if (IERC20(data.pool).balanceOf(address(this)) == 0) { // <= FOUND
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L103-L103)']
```solidity
103:         IGauge(gauge).deposit(liquidity, address(this)); // <= FOUND
```
['[113](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L113-L113)']
```solidity
113:         IGauge(gauge).getReward(address(this)); // <= FOUND
```
['[128](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/AerodromeConnector.sol#L128-L128)']
```solidity
128:         uint256 balance = IERC20(pool).balanceOf(address(this)); // <= FOUND
```
['[81](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L81-L84)']
```solidity
81:         IBalancerVault(balancerVault).joinPool(
82:             poolId,
83:             address(this),  // <= FOUND
84:             address(this),  // <= FOUND
85:             IBalancerVault.JoinPoolRequest(
86:                 tokens,
87:                 amounts,
88:                 abi.encode(
89:                     IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
90:                     amountsWithoutBPT, 
91:                     minBPT 
92:                 ),
93:                 false
94:             )
95:         );
```
['[96](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L96-L96)']
```solidity
96:         bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(poolId)); // <= FOUND
```
['[102](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L102-L102)']
```solidity
102:             uint256 amount = IERC20(pool).balanceOf(address(this)); // <= FOUND
```
['[104](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L104-L104)']
```solidity
104:             IRewardPool(_poolInfo.auraPoolAddress).deposit(auraAmount, address(this)); // <= FOUND
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L112-L112)']
```solidity
112:         IRewardPool(_poolInfo.auraPoolAddress).deposit(_amount, address(this)); // <= FOUND
```
['[130](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L130-L133)']
```solidity
130:             IBalancerVault(balancerVault).exitPool(
131:                 p.poolId,
132:                 address(this),  // <= FOUND
133:                 payable(address(this)),  // <= FOUND
134:                 IBalancerVault.ExitPoolRequest(
135:                     tokens,
136:                     _amounts,
137:                     abi.encode(
138:                         IBalancerVault.ExitKind.EXACT_BPT_IN_FOR_ONE_TOKEN_OUT,
139:                         p._lpAmount,
140:                         p.withdrawIndex 
141:                     ),
142:                     false
143:                 )
144:             );
```
['[147](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L147-L149)']
```solidity
147:                 registry.updateHoldingPosition(
148:                     vaultId,
149:                     registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(p.poolId)), // <= FOUND
150:                     "",
151:                     "",
152:                     true
153:                 );
```
['[178](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L178-L178)']
```solidity
178:             auraShares = IERC20(pool.auraPoolAddress).balanceOf(address(this)); // <= FOUND
```
['[181](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L181-L181)']
```solidity
181:         return IERC20(pool.pool).balanceOf(address(this)) + auraShares; // <= FOUND
```
['[190](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerConnector.sol#L190-L190)']
```solidity
190:         bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(pooId)); // <= FOUND
```
['[86](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L86-L87)']
```solidity
86:                 
87:                 BaseConnector(receiver).sendTokensToTrustedAddress(address(tokens[i]), amounts[i], address(this), ""); // <= FOUND
```
['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/BalancerFlashLoan.sol#L92-L92)']
```solidity
92:             require(tokens[i].balanceOf(address(this)) == 0, "BalancerFlashLoan: Flash loan extra tokens"); // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L46-L47)']
```solidity
46:         router.addLiquidity(
47:             p.tokenA, p.tokenB, p.amountA, p.amountB, p.minAmountA, p.minAmountB, address(this), p.deadline // <= FOUND
48:         );
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L51-L53)']
```solidity
51:         registry.updateHoldingPosition(
52:             vaultId,
53:             registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)), // <= FOUND
54:             "",
55:             "",
56:             false
57:         );
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L71-L72)']
```solidity
71:         router.removeLiquidity(
72:             p.tokenA, p.tokenB, p.amountLiquidty, p.minAmountA, p.minAmountB, address(this), p.deadline // <= FOUND
73:         );
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L76-L76)']
```solidity
76:         if (IERC20(pool).balanceOf(address(this)) == 0) { // <= FOUND
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L77-L79)']
```solidity
77:             registry.updateHoldingPosition(
78:                 vaultId,
79:                 registry.calculatePositionId(address(this), CAMELOT_POSITION_ID, abi.encode(p.tokenA, p.tokenB)), // <= FOUND
80:                 "",
81:                 "",
82:                 true
83:             );
```
['[94](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CamelotConnector.sol#L94-L94)']
```solidity
94:         uint256 balanceThis = IERC20(pool).balanceOf(address(this)); // <= FOUND
```
['[31](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L31-L31)']
```solidity
31:         if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset); // <= FOUND
```
['[33](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L33-L34)']
```solidity
33:         registry.updateHoldingPosition(
34:             vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(market)), "", "", false // <= FOUND
35:         );
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L54-L55)']
```solidity
54:             registry.updateHoldingPosition(
55:                 vaultId, registry.calculatePositionId(address(this), COMPOUND_LP, abi.encode(_market)), "", "", true // <= FOUND
56:             );
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L65-L65)']
```solidity
65:         IRewards(rewardContract).claim(address(market), address(this), true); // <= FOUND
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L85-L85)']
```solidity
85:         uint256 borrowBalanceInBase = comet.borrowBalanceOf(address(this)); // <= FOUND
```
['[96](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L96-L96)']
```solidity
96:         IComet.UserBasic memory userBasic = comet.userBasic(address(this)); // <= FOUND
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L112-L113)']
```solidity
112:                 
113:                 (uint256 collateralBalance,) = comet.userCollateral(address(this), info.asset); // <= FOUND
```
['[93](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L93-L94)']
```solidity
93:         
94:         IDepositToken(depostiToken).deposit(address(this), amount); // <= FOUND
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L122-L122)']
```solidity
122:         bytes32 positionId = registry.calculatePositionId(address(this), CURVE_LP_POSITION, abi.encode(pool)); // <= FOUND
```
['[213](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L213-L213)']
```solidity
213:         IDepositToken(depostiToken).withdraw(address(this), amount); // <= FOUND
```
['[223](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L223-L223)']
```solidity
223:             IRewardsGauge(gauges[i]).claim_rewards(address(this)); // <= FOUND
```
['[235](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L235-L235)']
```solidity
235:             IDepositToken(pools[i]).claimReward(address(this)); // <= FOUND
```
['[250](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L250-L250)']
```solidity
250:             baseRewardPool.getReward(address(this), true); // <= FOUND
```
['[327](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L327-L327)']
```solidity
327:         return IConvexBasicRewards(info.convexRewardPool).balanceOf(address(this)); // <= FOUND
```
['[336](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L336-L336)']
```solidity
336:         return IERC20(info.lpToken).balanceOf(address(this)); // <= FOUND
```
['[346](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L346-L346)']
```solidity
346:         return IRewardsGauge(info.gauge).balanceOf(address(this)); // <= FOUND
```
['[356](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CurveConnector.sol#L356-L356)']
```solidity
356:         return IDepositToken(prismaPool).balanceOf(address(this)); // <= FOUND
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L38-L39)']
```solidity
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", false // <= FOUND
40:         );
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L50-L50)']
```solidity
50:         (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0)); // <= FOUND
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L52-L53)']
```solidity
52:             registry.updateHoldingPosition(
53:                 vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true // <= FOUND
54:             );
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L65-L65)']
```solidity
65:         if (!registry.isTokenTrusted(vaultId, token, address(this))) { // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L72-L73)']
```solidity
72:         registry.updateHoldingPosition(
73:             vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true // <= FOUND
74:         );
```
['[109](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/Dolomite.sol#L109-L110)']
```solidity
109:         (uint256[] memory markets, address[] memory tokens,, Types.Wei[] memory amounts) =
110:             dolomiteMargin.getAccountBalances(Info(address(this), accountId)); // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L43-L44)']
```solidity
43:         bytes32 positionId =
44:             registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool)); // <= FOUND
```
['[50](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L50-L50)']
```solidity
50:             pool.borrowAsset(borrowAmount, collateralAmount, address(this)); // <= FOUND
```
['[53](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L53-L53)']
```solidity
53:             pool.addCollateral(collateralAmount, address(this)); // <= FOUND
```
['[69](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L69-L69)']
```solidity
69:         uint256 currentCollateral = pool.userCollateralBalance(address(this)); // <= FOUND
```
['[71](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L71-L72)']
```solidity
71:             bytes32 positionId =
72:                 registry.calculatePositionId(address(this), COLLATERAL_AND_DEBT_POSITION_TYPE, abi.encode(pool)); // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L76-L76)']
```solidity
76:         pool.removeCollateral(withdrawAmount, address(this)); // <= FOUND
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L89-L89)']
```solidity
89:         uint256 sharesOwed = pool.userBorrowShares(address(this)); // <= FOUND
```
['[95](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L95-L95)']
```solidity
95:         IFraxPair(pool).repayAsset(sharesToRepay, address(this)); // <= FOUND
```
['[122](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L122-L123)']
```solidity
122:         
123:         uint256 borrowerShares = _fraxlendPair.userBorrowShares(address(this)); // <= FOUND
```
['[125](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L125-L125)']
```solidity
125:         uint256 _collateralAmount = _fraxlendPair.userCollateralBalance(address(this)); // <= FOUND
```
['[153](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L153-L153)']
```solidity
153:         uint256 collateralAmount = pool.userCollateralBalance(address(this)); // <= FOUND
```
['[154](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L154-L154)']
```solidity
154:         uint256 borrowerShares = pool.userBorrowShares(address(this)); // <= FOUND
```
['[25](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L25-L25)']
```solidity
25:         address c = ICreditFacadeV3(facade).openCreditAccount(address(this), new MultiCall[](0), ref); // <= FOUND
```
['[26](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L26-L28)']
```solidity
26:         registry.updateHoldingPosition(
27:             vaultId,
28:             registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)), // <= FOUND
29:             abi.encode(c),
30:             "",
31:             false
32:         );
```
['[44](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/GearBoxV3.sol#L44-L46)']
```solidity
44:         registry.updateHoldingPosition(
45:             vaultId,
46:             registry.calculatePositionId(address(this), GEARBOX_POSITION_ID, abi.encode(facade)), // <= FOUND
47:             abi.encode(creditAccount),
48:             "",
49:             true
50:         );
```
['[56](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L56-L57)']
```solidity
56:         
57:         uint256[] memory requestIds = ILidoWithdrawal(lidoWithdrawal).requestWithdrawals(amounts, address(this)); // <= FOUND
```
['[57](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L57-L57)']
```solidity
57:         bytes32 positionId = registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, ""); // <= FOUND
```
['[72](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L72-L73)']
```solidity
72:         
73:         uint256 beforeClaimBalance = address(this).balance; // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L76-L77)']
```solidity
76:         
77:         IWETH(weth).deposit{ value: address(this).balance - beforeClaimBalance }(); // <= FOUND
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/LidoConnector.sol#L77-L79)']
```solidity
77:         registry.updateHoldingPosition(
78:             vaultId,
79:             registry.calculatePositionId(address(this), LIDO_WITHDRAWAL_REQUEST_ID, ""), // <= FOUND
80:             abi.encode(requestId),
81:             "",
82:             true
83:         );
```
['[99](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L99-L100)']
```solidity
99:         registry.updateHoldingPosition(
100:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", false // <= FOUND
101:         );
```
['[118](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L118-L119)']
```solidity
118:         IMaverickRouter(maverickRouter).removeLiquidity(
119:             p.pool, address(this), p.tokenId, p.params, p.minTokenAAmount, p.minTokenBAmount, p.deadline // <= FOUND
120:         );
```
['[121](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L121-L122)']
```solidity
121:         registry.updateHoldingPosition(
122:             vaultId, registry.calculatePositionId(address(this), MAVERICK_LP, abi.encode(p.pool)), "", "", true // <= FOUND
123:         );
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L133-L133)']
```solidity
133:         IMaverickReward.EarnedInfo[] memory earnedInfo = rewardContract.earned(address(this)); // <= FOUND
```
['[138](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L138-L138)']
```solidity
138:                 rewardContract.getReward(address(this), tokenIndex); // <= FOUND
```
['[152](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MaverickConnector.sol#L152-L152)']
```solidity
152:         (uint256 a, uint256 b) = positionInspector.addressBinReservesAllKindsAllTokenIds(address(this), pool); // <= FOUND
```
['[39](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L39-L39)']
```solidity
39:             morphoBlue.supply(params, amount, 0, address(this), ""); // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L43-L43)']
```solidity
43:             morphoBlue.supplyCollateral(params, amount, address(this), ""); // <= FOUND
```
['[46](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L46-L47)']
```solidity
46:         registry.updateHoldingPosition(
47:             vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", false // <= FOUND
48:         );
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L61-L61)']
```solidity
61:             morphoBlue.withdraw(params, amount, 0, address(this), address(this)); // <= FOUND
```
['[63](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L63-L63)']
```solidity
63:             morphoBlue.withdrawCollateral(params, amount, address(this), address(this)); // <= FOUND
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L65-L65)']
```solidity
65:         Position memory p = morphoBlue.position(id, address(this)); // <= FOUND
```
['[67](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L67-L68)']
```solidity
67:             registry.updateHoldingPosition(
68:                 vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true // <= FOUND
69:             );
```
['[82](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L82-L82)']
```solidity
82:         morphoBlue.borrow(market, amount, 0, address(this), address(this)); // <= FOUND
```
['[98](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L98-L98)']
```solidity
98:         morphoBlue.repay(params, amount, 0, address(this), ""); // <= FOUND
```
['[110](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L110-L110)']
```solidity
110:         Position memory p = morphoBlue.position(_id, address(this)); // <= FOUND
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L124-L124)']
```solidity
124:             Position memory pos = morphoBlue.position(id, address(this)); // <= FOUND
```
['[32](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L32-L32)']
```solidity
32:         IERC721(address(positionManager)).safeTransferFrom(address(this), address(masterchef), tokenId); // <= FOUND
```
['[51](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PancakeswapConnector.sol#L51-L51)']
```solidity
51:         masterchef.withdraw(tokenId, address(this)); // <= FOUND
```
['[85](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L85-L86)']
```solidity
85:         
86:         uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1); // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L87-L87)']
```solidity
87:         bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)); // <= FOUND
```
['[100](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L100-L100)']
```solidity
100:         _YT.mintPY(address(this), address(this)); // <= FOUND
```
['[116](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L116-L116)']
```solidity
116:         market.mint(address(this), SYamount, PTamount); // <= FOUND
```
['[155](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L155-L155)']
```solidity
155:         pendleRouter.swapExactYtForPt(address(this), market, exactYTIn, min, guess); // <= FOUND
```
['[172](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L172-L172)']
```solidity
172:         pendleRouter.swapExactYtForSy(address(this), market, exactYTIn, min, orderData); // <= FOUND
```
['[190](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L190-L190)']
```solidity
190:         (uint256 netSyOut, uint256 netSyFee) = market.swapExactPtForSy(address(this), exactPTIn, swapData); // <= FOUND
```
['[205](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L205-L205)']
```solidity
205:         market.burn(address(this), address(market), amount); // <= FOUND
```
['[222](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L222-L222)']
```solidity
222:         IPStandardizedYield(address(SY)).redeem(address(this), _amount, _underlyingToken, 1, true); // <= FOUND
```
['[224](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L224-L226)']
```solidity
224:             registry.updateHoldingPosition(
225:                 vaultId,
226:                 registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)), // <= FOUND
227:                 "",
228:                 "",
229:                 true
230:             );
```
['[242](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L242-L242)']
```solidity
242:         market.redeemRewards(address(this)); // <= FOUND
```
['[265](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L265-L265)']
```solidity
265:             uint256 SYAmount = _SY.balanceOf(address(this)); // <= FOUND
```
['[268](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L268-L270)']
```solidity
268:             
269:             uint256 lpBalance =
270:                 IERC20(market).balanceOf(address(this)) + pendleMarketDepositHelper.balance(market, address(this)); // <= FOUND
```
['[274](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L274-L274)']
```solidity
274:             uint256 PTAmount = _PT.balanceOf(address(this)); // <= FOUND
```
['[277](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L277-L277)']
```solidity
277:             uint256 YTBalance = _YT.balanceOf(address(this)); // <= FOUND
```
['[305](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PendleConnector.sol#L305-L307)']
```solidity
305:         return (
306:             _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0 // <= FOUND
307:                 && market.balanceOf(address(this)) == 0 // <= FOUND
308:         );
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L35-L35)']
```solidity
35:             bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm)); // <= FOUND
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L37-L37)']
```solidity
37:             if (!registry.isPositionTrustedForConnector(vaultId, positionId, address(this))) { // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L35-L35)']
```solidity
35:         bytes32 positionId = registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zap, tm)); // <= FOUND
```
['[62](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L62-L62)']
```solidity
62:         zap.openTrove(tm, maxFee, dAmount, bAmount, address(this), address(this)); // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L76-L77)']
```solidity
76:         bytes32 positionId =
77:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm)); // <= FOUND
```
['[79](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L79-L79)']
```solidity
79:         if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) { // <= FOUND
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L84-L84)']
```solidity
84:         zapContract.addColl(tm, amountIn, address(this), address(this)); // <= FOUND
```
['[114](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L114-L114)']
```solidity
114:         borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this)); // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L117-L118)']
```solidity
117:         
118:         uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this)); // <= FOUND
```
['[130](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L130-L131)']
```solidity
130:         bytes32 positionId =
131:             registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, troveManager)); // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L133-L133)']
```solidity
133:         borrowerOperations.closeTrove(troveManager, address(this)); // <= FOUND
```
['[152](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/PrismaConnector.sol#L152-L153)']
```solidity
152:             (uint256 collateralBalance, uint256 debtBalance) =
153:                 ITroveManager(troveManager).getTroveCollAndDebt(address(this)); // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L35-L37)']
```solidity
35:         registry.updateHoldingPosition(
36:             vaultId,
37:             registry.calculatePositionId(address(this), SNX_POSITION_ID, ""), // <= FOUND
38:             abi.encode(_accountId, _token),
39:             "",
40:             false
41:         );
```
['[52](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SNXConnector.sol#L52-L54)']
```solidity
52:             registry.updateHoldingPosition(
53:                 vaultId,
54:                 registry.calculatePositionId(address(this), SNX_POSITION_ID, ""), // <= FOUND
55:                 abi.encode(_accountId, _token),
56:                 "",
57:                 true
58:             );
```
['[38](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L38-L39)']
```solidity
38:         registry.updateHoldingPosition(
39:             vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", false // <= FOUND
40:         );
```
['[61](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L61-L62)']
```solidity
61:             registry.updateHoldingPosition(
62:                 vaultId, registry.calculatePositionId(address(this), SILO_LP_ID, abi.encode(siloToken)), "", "", true // <= FOUND
63:             );
```
['[65](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L65-L65)']
```solidity
65:         if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) { // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L76-L76)']
```solidity
76:         return SolvencyV2.getData(ISilo(siloRepository.getSilo(siloToken)), address(this), minimumHealthFactor); // <= FOUND
```
['[117](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L117-L117)']
```solidity
117:             uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this)); // <= FOUND
```
['[118](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L118-L118)']
```solidity
118:             depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)); // <= FOUND
```
['[119](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L119-L119)']
```solidity
119:             uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this)); // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/SiloConnector.sol#L133-L135)']
```solidity
133:             if (
134:                 IERC20(assetsS[i].collateralToken).balanceOf(address(this)) // <= FOUND
135:                     + IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this)) > 0 // <= FOUND
136:             ) {
```
['[54](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L54-L54)']
```solidity
54:             stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this)); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L60-L60)']
```solidity
60:                 stakingAmount = IERC20(lpAddress).balanceOf(address(this)); // <= FOUND
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L66-L67)']
```solidity
66:         bytes32 positionId =
67:             registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId)); // <= FOUND
```
['[83](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L83-L84)']
```solidity
83:             stargateRouter.instantRedeemLocal(
84:                 uint16(withdrawRequest.poolId), withdrawRequest.routerAmount, address(this) // <= FOUND
85:             );
```
['[88](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L88-L88)']
```solidity
88:         uint256 LPAmount = LPStaking.userInfo(withdrawRequest.poolId, address(this)).amount; // <= FOUND
```
['[89](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L89-L89)']
```solidity
89:         if (IERC20(lpAddress).balanceOf(address(this)) + LPAmount == 0) { // <= FOUND
```
['[90](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L90-L91)']
```solidity
90:             bytes32 positionId = registry.calculatePositionId(
91:                 address(this), STARGATE_LP_POSITION_TYPE, abi.encode(withdrawRequest.poolId) // <= FOUND
92:             );
```
['[114](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L114-L114)']
```solidity
114:         uint256 lpAmount = LPStaking.userInfo(poolId, address(this)).amount + IERC20(lpAddress).balanceOf(address(this)); // <= FOUND
```
['[41](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L41-L42)']
```solidity
41:         bytes32 positionId =
42:             registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(p.token0, p.token1)); // <= FOUND
```
['[43](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L43-L43)']
```solidity
43:         p.recipient = address(this); // <= FOUND
```
['[75](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L75-L76)']
```solidity
75:             bytes32 positionId =
76:                 registry.calculatePositionId(address(this), UNI_LP_POSITION_TYPE, abi.encode(token0, token1)); // <= FOUND
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L123-L123)']
```solidity
123:         CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max); // <= FOUND
```
['[103](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L103-L103)']
```solidity
103:             if (caller != address(this)) revert IConnector_InvalidAddress(caller); // <= FOUND
```
['[84](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L84-L86)']
```solidity
84:         
85:         uint256 positionIndex =
86:             registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this))); // <= FOUND
```
['[87](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L87-L87)']
```solidity
87:             registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove); // <= FOUND
```
['[92](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L92-L92)']
```solidity
92:         _updateTokenInRegistry(token, IERC20(token).balanceOf(address(this)) == 0); // <= FOUND
```
['[180](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L180-L181)']
```solidity
180:             
181:             uint256 _balance = IERC20(tokens[i]).balanceOf(address(this)); // <= FOUND
```
['[182](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L182-L182)']
```solidity
182:             uint256 _balanceAfter = IERC20(tokens[i]).balanceOf(address(this)); // <= FOUND
```
['[212](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L212-L213)']
```solidity
212:             _executeSwap(
213:                 SwapRequest(address(this), routeIds[i], amountsIn[i], tokensIn[i], tokensOut[i], swapData[i], true, 0) // <= FOUND
214:             );
```
['[278](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/BaseConnector.sol#L278-L278)']
```solidity
278:         uint256 currentAllowance = IERC20(_token).allowance(address(this), _spender); // <= FOUND
```
['[60](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L60-L61)']
```solidity
60:         registry.updateHoldingPosition(
61:             vaultId, registry.calculatePositionId(address(this), _positionType, ""), data, "", false // <= FOUND
62:         );
```
['[66](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/ConnectorMock2.sol#L66-L67)']
```solidity
66:         registry.updateHoldingPosition(
67:             vaultId, registry.calculatePositionId(address(this), positionType, ""), data, "", false // <= FOUND
68:         );
```
['[80](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/LZHelpers/LZHelperSender.sol#L80-L80)']
```solidity
80:         _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this)));  // <= FOUND
```
['[74](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L74-L74)']
```solidity
74:         if (bridgeRequest.from != address(this)) revert IConnector_InvalidInput(); // <= FOUND
```
['[35](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L35-L37)']
```solidity
35:         registry.updateHoldingPostionWithTime(
36:             vaultId,
37:             registry.calculatePositionId(address(this), OMNICHAIN_POSITION_ID, abi.encode(chainId)), // <= FOUND
38:             "",
39:             abi.encode(tvl),
40:             tvl <= DUST_LEVEL,
41:             updateTime
42:         );
```
['[37](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L37-L37)']
```solidity
37:             uint256 amount = IERC20(token).balanceOf(address(this)); // <= FOUND
```


</details>

## [Gas-45] Use 'storage' instead of 'memory' for struct/array state variables

### Resolution 
In Solidity, choosing between `memory` and `storage` for variables, especially when dealing with structs or arrays, is crucial for optimizing gas costs. Variables declared as `storage` are pointers to the blockchain data, leading to lower gas consumption when fields are accessed or modified, as they don't require reading the entire structure. In contrast, `memory` variables copy the entire struct or array from `storage`, incurring significant gas costs, especially for large or complex structures. Therefore, use `storage` for state variables or when working within functions to manipulate existing contract data. Reserve `memory` for temporary data or when data needs to be passed to external functions as copies, ensuring efficient use of gas and avoiding unnecessary costs.

Num of instances: 2

### Findings 


<details><summary>Click to show findings</summary>

['[432](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L432-L432)']
```solidity
432:         PositionBP memory position = vaults[vaultId].trustedPositionsBP[_positionId]; // <= FOUND
```
['[76](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/helpers/valueOracle/NoyaValueOracle.sol#L76-L76)']
```solidity
76:         address[] memory sources = priceRoutes[asset][baseToken]; // <= FOUND
```


</details>

## [Gas-46] Use constants instead of type(uint<n>).max

### Resolution 
In smart contract development, utilizing constants for known maximum or minimum values, rather than computing `type(uint<n>).max` or assuming `0` for `.min`, can significantly reduce gas costs. Constants require less runtime computation and storage, optimizing contract efficiency—a crucial strategy for developers aiming for cost-effective and performant code.

Num of instances: 11

### Findings 


<details><summary>Click to show findings</summary>

['[140](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L140-L140)']
```solidity
140:         vault.holdingPositions.push(HoldingPI(address(0), address(0), bytes32(0), "", "", type(uint256).max)); // <= FOUND
```
['[312](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L312-L312)']
```solidity
312:                     type(uint256).max // <= FOUND
```
['[339](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L339-L339)']
```solidity
339:         if (positionIndex == 0 && removePosition) return type(uint256).max; // <= FOUND
```
['[354](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L354-L354)']
```solidity
354:             return type(uint256).max; // <= FOUND
```
['[371](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/accountingManager/Registry.sol#L371-L371)']
```solidity
371:         if (positionIndex != type(uint256).max) { // <= FOUND
```
['[77](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/CompoundConnector.sol#L77-L77)']
```solidity
77:         if (borrowBalanceInBase == 0) return type(uint256).max; // <= FOUND
```
['[124](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L124-L124)']
```solidity
124:         if (_borrowerAmount == 0) return type(uint256).max; // <= FOUND
```
['[133](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/FraxConnector.sol#L133-L133)']
```solidity
133:         if (currentPositionLTV == 0) return type(uint256).max;  // <= FOUND
```
['[112](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/MorphoBlueConnector.sol#L112-L112)']
```solidity
112:         if (borrowAmount == 0) return type(uint256).max; // <= FOUND
```
['[59](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/StargateConnector.sol#L59-L59)']
```solidity
59:             if (depositRequest.LPStakingAmount == type(uint256).max) { // <= FOUND
```
['[123](https://github.com/code-423n4/2024-04-noya/tree/main//contracts/connectors/UNIv3Connector.sol#L123-L123)']
```solidity
123:         CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max); // <= FOUND
```


</details>
