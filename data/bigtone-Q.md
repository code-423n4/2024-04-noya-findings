
# L1. BalancerConnector doesn't support the Native token (0x0) 
[openPosition](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol#L81)
[decreasePosition](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol#L133)
```solidity
    function decreasePosition(DecreasePositionParams memory p) public onlyManager nonReentrant {
        if (p._auraAmount > 0) {
            (PoolInfo memory _poolInfo, bytes32 positionId) = _getPoolInfo(p.poolId);

            IRewardPool(_poolInfo.auraPoolAddress).withdrawAndUnwrap(p._auraAmount, true);
        }

        if (p._lpAmount > 0) {
            address[] memory tokens;
            {
                (tokens,,) = IBalancerVault(balancerVault).getPoolTokens(p.poolId);
            }
            uint256[] memory _amounts = new uint256[](tokens.length);
            _amounts[p.outerIndex] = p.minAmount;

            IBalancerVault(balancerVault).exitPool( // @audit missing msg.value
                p.poolId,
                address(this), // sender
                payable(address(this)), // recipient // @audit no receive() function for receiving Native token?
                IBalancerVault.ExitPoolRequest(
                    tokens,
                    _amounts,
                    abi.encode(
                        IBalancerVault.ExitKind.EXACT_BPT_IN_FOR_ONE_TOKEN_OUT,
                        p._lpAmount,
                        p.withdrawIndex // enterTokenIndex
                    ),
                    false
                )
            );
```

# L2. Use a nonReentrant modifier to avoid the unexpected reentrancy bugs
[repayWithCollateral](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/AaveConnector.sol#L88)
[depositIntoConvexBooster](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L103)
[withdrawFromConvexBooster](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L182)
[withdrawFromConvexRewardPool](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L192)
[withdrawFromGauge](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L202)
[withdrawFromPrisma](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CurveConnector.sol#L212)
[openAccount](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol#L24)
[deposit](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol#L30)
[withdraw](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol#L46)



# L3. When calling updateHoldingPosition in the closeBorrowPosition, `removePosition` should be false.
[closeBorrowPosition](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/Dolomite.sol#L102)
```solidity
function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
        // repay
        borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds);
        registry.updateHoldingPosition(
            vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true // @audit false?
        );
    }
```

# L4. Missing invoking the `_updateTokenInRegistry` in the executeCommands in GearBoxV3 contract.
[executeCommands](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/GearBoxV3.sol#L62~L86)

```solidity
    function executeCommands(
        address facade,
        address creditAccount,
        MultiCall[] calldata calls,
        address approvalToken,
        uint256 amount
    ) public onlyManager nonReentrant {
        for (uint256 i = 0; i < calls.length; i++) {
            if (calls[i].target != facade) revert IConnector_InvalidTarget(calls[i].target);
            bytes4 method = bytes4(calls[i].callData[:4]);

            if (method == ICreditFacadeV3Multicall.enableToken.selector) {
                (address token) = abi.decode(calls[i].callData[4:], (address));
                _updateTokenInRegistry(token);
            }
        }
        if (approvalToken != address(0)) {
            _approveOperations(approvalToken, ICreditFacadeV3(facade).creditManager(), amount);
        }
        ICreditFacadeV3(facade).multicall(creditAccount, calls);
        if (approvalToken != address(0)) {
            _revokeApproval(approvalToken, ICreditFacadeV3(facade).creditManager());
        } // @audit missing _updateTokenInRegistry(approvalToken)
+        _updateTokenInRegistry(approvalToken);
        emit ExecuteCommands(facade, creditAccount, calls, approvalToken, amount);
    }
```

# L5. Missing invoking the `_updateTokenInRegistry` in the executeCommands in GearBoxV3 contract.
[depositIntoStargatePool](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/StargateConnector.sol#L63)
```solidity
    function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {
        address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;
        address underlyingToken = IStargatePool(lpAddress).token();
        if (depositRequest.routerAmount > 0) {
            _approveOperations(underlyingToken, address(stargateRouter), depositRequest.routerAmount);
            stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this));
            _updateTokenInRegistry(underlyingToken);
        }
        if (depositRequest.LPStakingAmount > 0) {
            uint256 stakingAmount = depositRequest.LPStakingAmount;
            if (depositRequest.LPStakingAmount == type(uint256).max) {
                stakingAmount = IERC20(lpAddress).balanceOf(address(this));
            }
            _approveOperations(lpAddress, address(LPStaking), stakingAmount);
            LPStaking.deposit(depositRequest.poolId, stakingAmount); // @audit _updatetokenInRegistry(lpAddress)?
+            _updateTokenInRegistry(lpAddress);
        }
        _updateTokenInRegistry(rewardToken);
        bytes32 positionId =
            registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));
        registry.updateHoldingPosition(vaultId, positionId, "", "", false);
        emit DepositIntoStargatePool(depositRequest);
    }
```

# L6. Missing checking if market.loanToken is TokenTrusted in the MorphoBlueConnector contract
[borrow](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol#L82)
[repay](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/MorphoBlueConnector.sol#L97)
```solidity
    function borrow(uint256 amount, Id id) external onlyManager nonReentrant {
        MarketParams memory market = morphoBlue.idToMarketParams(id);
        morphoBlue.borrow(market, amount, 0, address(this), address(this));
+        if (!registry.isTokenTrusted(vaultId, market.loanToken, address(this))) revert IConnector_UntrustedToken(_borrowAsset);
        if (getHealthFactor(id, morphoBlue.market(id)) < minimumHealthFactor) {
            revert IConnector_LowHealthFactor(getHealthFactor(id, morphoBlue.market(id)));
        }
        _updateTokenInRegistry(market.loanToken);
        emit Borrow(amount, id);
    }
```

# L7. Unnecessary approval may cause a security issue
[withdraw](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/SNXConnector.sol#L48)
```solidity
    function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
        // Deposit
-        _approveOperations(_token, address(SNXCoreProxy), _amount); // @audit remove this?
        SNXCoreProxy.withdraw(_accountId, _token, _amount);
        (uint256 c,,) = SNXCoreProxy.getAccountCollateral(_accountId, _token);
        if (c == 0) {
            registry.updateHoldingPosition(
                vaultId,
                registry.calculatePositionId(address(this), SNX_POSITION_ID, ""),
                abi.encode(_accountId, _token),
                "",
                true
            );
        }
        // Update token
        _updateTokenInRegistry(_token);
    }
```