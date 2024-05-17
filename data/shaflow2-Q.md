| Severity | Title                                                        |
|----------|--------------------------------------------------------------|
| L-1     | When a connector is disabled, its position will still be calculated       |
| L-2     | The contract is not compatible with Tokens with Blocklists, May be blocked by attackers in the queue |
| L-3     | The contract is not compatible with tokens with Balance changes outside of transfers |
| L-4     | EligibleUser can not be canceled                                     |
| L-5     | The BalancerConnector contract failed to update the position in a timely manner after calling the openPosition function |
| L-6     | ReceiveFlashLoan function obtained the emergencyManager variable, but did not use it, causing EmergencyManager to be unable to call flashloan |
| L-7     | DolomiteConnector lacks health value management |
| L-8   | Suggest calling the _quote function to obtain gas consumption instead of directly passing in address (this).balance                                  |
| N-1   | Delete useless local variables                                       |
| N-2   | Delete useless global variables                                      |
| N-3   | Suggest using the enabled field to check if vault exists              |
| N-4   | Delete extra spaces in comments                                      |
| N-5   | First check the rationality of the parameters before assigning values |
| N-6   | PendleConnector connector did not update underlyingtoken position in a timely manner after Supply |
| N-7   | Extra checks                                                            |
| N-8   | Overloaded function without changing anything                          |
| N-9   | The functions in ConnectorMock2.sol are not restricted from being called |

# [L-1] When a connector is disabled, its position will still be calculated

## impact

The AddConnector function can be used to enable and disable a connector
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
When an existing connector is removed, its position will still be calculated  

## POC
```solidity
    function testVaultTVL() public {
        _dealWhale(
            baseToken,
            address(alice),
            address(0x1AB4973a48dc892Cd9971ECE8e01DcC7688f8F23),
            100000 * 1e6
        );

        vm.startPrank(alice);
        SafeERC20.forceApprove(
            IERC20(USDC),
            address(accountingManager),
            100000 * 1e6
        );
        accountingManager.deposit(address(alice), 100000 * 1e6, address(0));
        vm.stopPrank();

        vm.startPrank(owner);
        accountingManager.calculateDepositShares(1);
        vm.warp(block.timestamp + 35 minutes);
        accountingManager.executeDeposit(1, address(connector2), "");
        vm.stopPrank();
        console.log(accountingManager.TVL());

        vm.startPrank(owner);
        address[] memory connectors = new address[](1);
        connectors[0] = connector2;
        bool[] memory enabled = new bool[](1);
        enabled[0] = false;
        registry.addConnector(vaultId, connectors, enabled);
        vm.stopPrank();
        console.log(accountingManager.TVL());
    }
```
tow TVL log both 100000000000
## Suggestion
In the getTVL function of TVLHelper, check if the position holder connector is disabled.

# [L-2] The contract is not compatible with Tokens with Blocklists, May be blocked by attackers in the queue
## impact
If the token contains a blacklist address, a malicious attacker can completely block the withdraw queue functions of the AccountingManager contract.
They only need to set the receiver to the address on the blacklist when calling the withdraw function, so that when the project side calls the executeWithdraw function, the token will be forwarded to the blacklist address, the transaction will be rolled back, and the entire withdraw queue will be blocked
```solidity
            baseToken.safeTransfer(data.receiver, baseTokenAmount);
```
## POC
example:
1. alice deposit 1 token with blocklists
2. when all deposit step complete,she withdraw 1 token and set the receiver to the address on the blacklist
3. When the project party calls executeWithdraw for withdrawal, the transaction will be rolled back

Changes required to run the test: The basetoken needs to include boldlists, and ADDRESS.INeBlockLISTS needs to be set to an address on the blacklist
```solidity
    function testVaultWithdrawDos2() public {
        //deal(baseToken, address(alice), 1e8);

        vm.startPrank(alice);
        SafeERC20.forceApprove(IERC20(USDC), address(accountingManager), 1e8);
        accountingManager.deposit(address(alice), 1e8, address(0));
        vm.stopPrank();

        vm.startPrank(owner);
        accountingManager.calculateDepositShares(1);
        vm.warp(block.timestamp + 35 minutes);
        accountingManager.executeDeposit(1, address(connector2), "");
        vm.stopPrank();

        vm.startPrank(alice);
        accountingManager.withdraw(
            1e8,
            address(ADDRESS_IN_BLOCKLISTS)
        );
        vm.stopPrank();

        vm.startPrank(owner);
        accountingManager.calculateWithdrawShares(1);
        accountingManager.startCurrentWithdrawGroup();
        RetrieveData[] memory retrieveData = new RetrieveData[](1);
        retrieveData[0] = RetrieveData(
            1e8,
            address(connector2),
            abi.encode(1e8, 1e8)
        );
        accountingManager.retrieveTokensForWithdraw(retrieveData);
        accountingManager.fulfillCurrentWithdrawGroup();
        vm.warp(block.timestamp + 7 hours);
        vm.expectRevert();
        accountingManager.executeWithdraw(1);
        vm.stopPrank();
    }
```

## Suggestion
I didn't think of a better way to prevent it, the only way I can think of is to check if the receiver is in the blocklists when calling the withdraw function.

# [L-3] The contract is not compatible with tokens with Balance changes outside of transfers
## impact
Due to the long cycle of deposit and withdrawal, if there are changes in the token balance beyond transfer during this process, it may cause unexpected results
Here are one example:
Contract balance decreases during deposit

BaseToken.balanceOf(address(this)) may be smaller than deployQueue. totalAWFDeposit, causing some underflows\
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L617C35-L617C101](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L617C35-L617C101)
```solidity
    uint256 availableAssets = baseToken.balanceOf(address(this)) - depositQueue.totalAWFDeposit;
```
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L628](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L628)
```solidity
        return TVLHelper.getTVL(vaultId, registry, address(baseToken)) + baseToken.balanceOf(address(this))
            - depositQueue.totalAWFDeposit;
```

## Suggestion
Remove the ERC20 token behaviors in scope from the balance changes outside of transfers token.

# [L-4] EligibleUser can not be canclled
## impact

EligibleUser can only be set to true and cannot be cancelled, which poses certain risks
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L80)
```solidity
    function addEligibleUser(address _user) external onlyMaintainerOrEmergency {
        isEligibleToUse[_user] = true;
        emit AddEligibleUser(_user);
    }
```

## Suggestion
```solidity
-    function addEligibleUser(address _user) external onlyMaintainerOrEmergency {
+    function addEligibleUser(address _user,bool isenable) external onlyMaintainerOrEmergency {
-        isEligibleToUse[_user] = true;
+        isEligibleToUse[_user] = isenable;
        emit AddEligibleUser(_user);
    }
```

# [L-5] The BalancerConnector contract failed to update the position in a timely manner after calling the openPosition function

## impact
The BalancerConnector contract may fail to update the position in a timely manner after calling the openPosition function, which may result in the position not being cleared in a timely manner.
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L64](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L64)
```solidity
    function openPosition(
        bytes32 poolId,
        uint256[] memory amounts,
        uint256[] memory amountsWithoutBPT,
        uint256 minBPT,
        uint256 auraAmount
    ) public onlyManager nonReentrant {
        address[] memory tokens;
        {
            (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(poolId);
        }
        address pool = IBalancerVault(balancerVault).getPool(poolId);

        for (uint256 i = 0; i < tokens.length; i++) {
            if (amounts[i] > 0) _approveOperations(tokens[i], balancerVault, amounts[i]);
        }

        IBalancerVault(balancerVault).joinPool(
            poolId,
            address(this), // sender
            address(this), // recipient
            IBalancerVault.JoinPoolRequest(
                tokens,
                amounts,
                abi.encode(
                    IBalancerVault.JoinKind.EXACT_TOKENS_IN_FOR_BPT_OUT,
                    amountsWithoutBPT, //_noBptAmounts,
                    minBPT // minimumBPT
                ),
                false
            )
        );
        bytes32 positionId = registry.calculatePositionId(address(this), BALANCER_LP_POSITION, abi.encode(poolId));
        registry.updateHoldingPosition(vaultId, positionId, "", "", false);

        if (auraAmount > 0) {
            (PoolInfo memory _poolInfo,) = _getPoolInfo(poolId);

            uint256 amount = IERC20(pool).balanceOf(address(this));
            _approveOperations(pool, _poolInfo.auraPoolAddress, amount);
            IRewardPool(_poolInfo.auraPoolAddress).deposit(auraAmount, address(this));
        }
        emit OpenPosition(poolId, amounts, amountsWithoutBPT, minBPT, auraAmount);
    }
```

## Suggestion
Update position at the end of the function
```solidity
    for(uint i = 0; i < tokens.length; i++){
        _updateTokenInRegistry(tokens[i]);
    }
```

# [L-6] ReceiveFlashLoan function obtained the emergencyManager variable, but did not use it,causing EmergencyManager to be unable to call flashloan
## impact
RecepteFlashLoan function obtained the emergencyManager variable, but did not use it. I guess the developer intended that emergencyManager could also call flashLoan, but did not implement it.

github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L69](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L69)
```solidity
        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
        if (!(caller == keeperContract)) {
            revert Unauthorized(caller);
        }
```
## Suggestion
```solidity
        (,,, address keeperContract,, address emergencyManager) = registry.getGovernanceAddresses(vaultId);
-        if (!(caller == keeperContract)) {
+        if (!(caller == KeeperContract || caller == emergencyManager)) {
            revert Unauthorized(caller);
        }
```

# [L-7] DolomiteConnector lacks health value management
# impact
The DolomiteConnector contract has borrowed positions, but the contract has not been designed with a relevant health value management system, which may result in low health values of the contract account positions, which cannot be detected in a timely manner, leading to liquidation
# Suggestion
Add a function to obtain health values and check the health values when calling the withdraw function
# [L-8] Suggest calling the _quote function to obtain gas consumption instead of directly passing in address (this).balance
## impact
The LZHelperSender contract directly passes in all the ETH in the contract as gas fees when sending cross chain messages. Conversely, the function should be called first to obtain gas consumption
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L80](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L80)
```solidity
    function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
        if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
        bytes memory data = abi.encode(vaultId, tvl, updateTime);
        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
    }
```
## Suggestion
```solidity
    function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
        if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();
        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
        bytes memory data = abi.encode(vaultId, tvl, updateTime);
-        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
+        _lzSend(lzChainId, data, messageSetting, _quote(lzChainId, data, messageSetting, false), payable(address(this))); // TODO: send event here
    }
```

# [N-1] Delete useless local variables

## impact
In the calculateWithdrawShares function, a local variable processedShares is defined to store the total shares calculated. This variable has not been used to update global variables, trigger events, or participate in the calculation of local variables. It has no effect and is recommended to be deleted.

## Suggestion
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L328](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L328)
```solidity
    function calculateWithdrawShares(
        uint256 maxIterations
    ) public onlyManager nonReentrant whenNotPaused {
        uint256 middleTemp = withdrawQueue.middle;
        uint64 i = 0;
-        uint256 processedShares = 0;
        uint256 assetsNeededForWithdraw = 0;
        uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(
            vaultId,
            registry
        );

        if (
            currentWithdrawGroup.isFullfilled == false &&
            currentWithdrawGroup.isStarted == true
        ) {
            revert NoyaAccounting_ThereIsAnActiveWithdrawGroup();
        }
        while (
            withdrawQueue.last > middleTemp &&
            withdrawQueue.queue[middleTemp].recordTime <= oldestUpdateTime &&
            i < maxIterations
        ) {
            i += 1;
            WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
            uint256 assets = previewRedeem(data.shares);
            data.amount = assets;
            data.calculationTime = block.timestamp;
            assetsNeededForWithdraw += assets;
-            processedShares += data.shares;
            emit CalculateWithdraw(
                middleTemp,
                data.owner,
                data.receiver,
                data.shares,
                assets,
                block.timestamp
            );

            middleTemp += 1;
        }
        currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
        withdrawQueue.middle = middleTemp;
    }

```

# [N-2] Delete useless global variables

## Impact
In NoyaFeeReceiver, an unused global variable is defined, it is recommended to delete it
## Suggestion
```solidity
-    address public baseToken;

    event ManagementFeeReceived(address indexed token, uint256 amount);

-    constructor(address _accountingManager, address _baseToken, address _receiver) Ownable(msg.sender) {
+    constructor(address _accountingManager, address _receiver) Ownable(msg.sender) {
        require(_accountingManager != address(0));
        require(_baseToken != address(0));
        require(_receiver != address(0));
        accountingManager = _accountingManager;
-        baseToken = _baseToken;
        receiver = _receiver;
    }
```

# [N-3] Suggest using the enabled field to check if vault exists

## Impact
In the vaultExists modify, checking the accounting manager address to determine the existence of a vault is different from checking the connector and renders the vault. enabled field useless.
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L53](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/Registry.sol#L53)
```solidity
    modifier vaultExists(uint256 _vaultId) {
        if (vaults[_vaultId].accountManager == address(0)) revert NotExist();
        _;
    }
```

## Suggestion

```solidity
    modifier vaultExists(uint256 _vaultId) {
-        if (vaults[_vaultId].accountManager == address(0)) revert NotExist();
+        if (!vaults[_vaultId].enabled) revert NotExist();
        _;
    }
```

# [N-4] Delete extra spaces in comments
## Impact
Delete extra spaces in comments
## Suggestion
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L157](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L157)
```solidity
-    ///@notice disables the route  if required.
+    ///@notice disables the route if required.
```

# [N-5] First check the rationality of the parameters before assigning values
## Impact
Perhaps due to carelessness, the constructor of OmnichainLogic.sol assigned parameters first, followed by a feasibility check.
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L33)
```solidity
    constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
        BaseConnector(baseConnectorParams)
    {
        lzHelper = _lzHelper;
        require(_lzHelper != address(0));
    }
```
## Suggestion
```solidity
    constructor(address payable _lzHelper, BaseConnectorCP memory baseConnectorParams)
        BaseConnector(baseConnectorParams)
    {
        require(_lzHelper != address(0));
        lzHelper = _lzHelper;
    }
```
# [N-6] PendleConnector connector did not update underlyingtoken position in a timely manner after Supply
## impact
PendleConnector connector did not update underlyingtoken position in a timely manner after Supply
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L78](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L78)
```solidity
    function supply(address market, uint256 amount) external onlyManager nonReentrant {
        (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();

        (, address _underlyingToken,) = _SY.assetInfo();

        _approveOperations(_underlyingToken, address(_SY), amount);
        // Mint SY from underlying token
        uint256 syMinted = _SY.deposit(address(this), _underlyingToken, amount, 1);

        bytes32 positionId = registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market));
        registry.updateHoldingPosition(vaultId, positionId, "", "", false);
        emit Supply(market, syMinted);
    }
```
## Suggestion
```solidity
+       updateHoldingPosition(_underlyingToken);
        emit Supply(market, syMinted);
    }
```
# [N-7] Extra checks

## impact
In the compoundConnector contract, each function checks whether the assert is a trustToken.
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L29](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L29)
```solidity
    function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {
        _approveOperations(asset, market, amount);
        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
```
```solidity
    function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {
        IComet(_market).withdraw(asset, amount);
        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
```
One step check is redundant because at the end of the function, _updateTokenInRegistry (assert) is called; Function Update Position
One step check is redundant because at the end of the function, _updateTokenInRegistry (assert) is called; Function updates position. If the assert is not a trust token, the position update will be reverted.
## Suggestion
```solidity
    function supply(address market, address asset, uint256 amount) external onlyManager nonReentrant {
        _approveOperations(asset, market, amount);
-        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
```
```solidity
    function withdrawOrBorrow(address _market, address asset, uint256 amount) external onlyManager nonReentrant {
        IComet(_market).withdraw(asset, amount);
-        if (!registry.isTokenTrusted(vaultId, asset, address(this))) revert IConnector_UntrustedToken(asset);
```

# [N-8] Overloaded function without changing anything
## impact
The CompoundConnector contract overloaded the _getUnderlyingTokens function, but did not change any content
github:[https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L134](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L134)
```solidity
    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
        return new address[](0);
    }

```
## Suggestion
Suggest deleting overloads or making modifications
```solidity
-    function _getUnderlyingTokens(uint256, bytes memory data) public view override returns (address[] memory) {
+    function _getUnderlyingTokens(uint256, bytes memory data) public pure override returns (address[] memory) {
        return new address[](0);
    }

```

# [N-9] The functions in ConnectorMock2. sol are not restricted from being called

## impact

In the readme file, ConnectorMock2. sol appears in the audit scope and should not have appeared, as this contract is only used for testing and all functions inside are not restricted in their invocation.

## Suggestion

Remove ConnectorMock2.sol from readme file.


