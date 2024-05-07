# QA Report for **NOYA**

## Table of Contents

| Issue ID | Description |
| -------- | ----------- |
| [QA-01](#qa-01-an-attacker-can-grief-honest-users-attempt-to-deposit-when-the-vault-is-close-to-depositlimittotalamount-due-to-not-having-a-minimum-deposit-amount) | An attacker can grief honest users attempt to deposit when the vault is close to `depositLimitTotalAmount` due to not having a minimum deposit amount |
| [QA-02](#qa-02-no-slippage-applied-when-depositing-into-a-stargate-pool-and-other-connectors) | No slippage applied when depositing into a Stargate pool and other connectors |
| [QA-03](#qa-03-deadline-logic-should-be-included-when-collecting-the-fees) | Deadline logic should be included when collecting the fees |
| [QA-04](#qa-04-aerodromeconnector-is-not-compatible-with-executions-that-deal-with-weth/eth) | `AerodromeConnector` is not compatible with executions that deal with `WETH/ETH` |
| [QA-05](#qa-05-admin-can-make-all-parties-immediately-have-an-unhealthy-position) | Admin can make all parties immediately have an unhealthy position |
| [QA-06](#qa-06-getting-price-from-chainlinkoracleconnector#getvaluefromchainlinkfeed()-should-be-wrapped-in-a-try-catch) | Getting price from `ChainlinkOracleConnector#getValueFromChainlinkFeed()` should be wrapped in a try catch |
| [QA-07](#qa-07-stargateconnector#claimstargaterewards()-can-easily-be-broken-for-some-tokens) | `StargateConnector#claimStargateRewards()` can easily be broken for some tokens |
| [QA-08](#qa-08-lidoconnector#deposit()-does-not-function-according-to-spec) | `LidoConnector#deposit()` does not function according to spec |
| [QA-09](#qa-09-morphoblueconnector#wthdraw()-is-not-being-queried-in-the-most-safe-manner-would-fail-in-some-cases) | `MorphoBlueConnector#wthdraw()` is not being queried in the most safe manner would fail in some cases |
| [QA-10](#qa-10-protocol-does-not-implement-the-estimatefees()-function-to-know-how-much-a-tx-should-cost) | Protocol does not implement the `estimateFees()` function to know how much a tx should cost |
| [QA-11](#qa-11-no-checks-for-min/max-circuit-breakers-while-querying-chainlink-data) | No checks for min/max circuit breakers while querying chainlink data |
| [QA-12](#qa-12-updatetvl-has-no-checks-to-ensure-the-payload-data-being-sent-via-_lzsend-is-not-of-extraordinary-size) | `updateTVL` has no checks to ensure the payload data being sent via `_lzSend` is not of extraordinary size |
| [QA-13](#qa-13-hardcoded-non-existing-underlying-tokens-and-0-as-tvl) | Hardcoded non-existing underlying tokens and 0 as TVL |
| [QA-14](#qa-14-protocol-is-to-be-deployed-on-some-optimistic-l2-chains-but-in-no-instance-do-they-consider-the-sequencer-going-down) | Protocol is to be deployed on some optimistic L2 chains but in no instance do they consider the sequencer going down |
| [QA-15](#qa-15-aaveconnector-could-end-up-holding-dust-positions) | `AAVEConnector` could end up holding dust positions |
| [QA-16](#qa-16-fix-typos) | Fix Typos |
| [QA-17](#qa-17-using-the-reserves-directly-could-make-the-execution-of-calculating-the-position-tvl-easily-susceptible-to-an-atomic-arbitrage-attack) | Using the reserves directly could make the execution of calculating the position TVL easily susceptible to an atomic arbitrage attack |
| [QA-18](#qa-18-addliquidity()-doesnt-actually-add-any-liquidity) | `addLiquidity()` doesn't actually add any liquidity |
| [QA-19](#qa-19-sendtokenstotrustedaddress()-is-unprotected-and-anyone-can-take-funds-from-the-contract) | `sendTokensToTrustedAddress()` is unprotected and anyone can take funds from the contract |
| [QA-20](#qa-20-docuentation-should-never-lead-to-invalid-links) | Docuentation should never lead to invalid links |
| [QA-21](#qa-21-setters-should-always-have-equality-checkers) | Setters should always have equality checkers |
| [QA-22](#qa-22-make-tvlhelper#gettvl()-more-effective) | Make `TVLHelper#getTVL()` more effective |
| [QA-23](#qa-23-protocol-currently-hardcodes-the-logic-of-pricing-weth) | Protocol currently hardcodes the logic of pricing WETH |
| [QA-24](#qa-24-make-keepers#execute()-more-effective) | Make `Keepers#execute()` more effective |
| [QA-25](#qa-25-some-tokens-don't-support-.balanceof()-causing-some-attempts-to-_swap_-to-fail) | Some tokens don't support `.balanceOf()` causing some attempts to _swap_ to fail |

## QA-01 An attacker can grief honest users attempt to deposit when the vault is close to `depositLimitTotalAmount` due to not having a minimum deposit amount

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L200-L220

```solidity
    function deposit(address receiver, uint256 amount, address referrer) public nonReentrant whenNotPaused {
        if (amount == 0) {
            revert NoyaAccounting_INVALID_AMOUNT();
        }

        baseToken.safeTransferFrom(msg.sender, address(this), amount);

        if (amount > depositLimitPerTransaction) {
            revert NoyaAccounting_DepositLimitPerTransactionExceeded();
        }

        if (TVL() > depositLimitTotalAmount) {
            revert NoyaAccounting_TotalDepositLimitExceeded();
        }

        depositQueue.queue[depositQueue.last] = DepositRequest(receiver, block.timestamp, 0, amount, 0);
        emit RecordDeposit(depositQueue.last, receiver, block.timestamp, amount, referrer);
        depositQueue.last += 1;
        depositQueue.totalAWFDeposit += amount;
    }

```

Users can deposit base token to the vault using this function, and there are a few checks, however there is no minimum deposit amount, so whenever the `TVL()` is close to `depositLimitTotalAmount` and a honest user attempts to deposit the difference between TVL() & depositLimitTotalAmount or even with a minute difference inbetween, another user can just front run their call with as low as 1 wei (if the honest user's transaction was to get TVL() == depositLimitTotalAmount which would then cause their attempt at depositing to revert.

### Impact

Griefing honest user's attempts at depositing.

> Borderline low/medium, as this means that the invariant of the `depositLimitTotalAmount` being the max a vault can have might never be reached since it costs very little for a user to front run this.

### Recommended Mitigation Steps

Consider having a minimum deposit amount so as to ensure these are valid requests at depositing.

## QA-02 No slippage applied when depositing into a Stargate pool and other connectors

### Proof of Concept

Protocol supports multiple connectors, and a total of 20 of these connectors are in scope for this contest, now going through most of them we can see that whenever there is a need to deposit or add liquidity via these connectors there is always a slippage check, in most cases passed via the params struct used to query these functionalities, an example could be from the [UNIv3Connector](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L40-L96), where [both the struct params for minting and increasing liquidity](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/UNIv3/INonfungiblePositionManager.sol#L14-L51) have a minimum amount outs parameter that gets checked.

Another example can be seen directly from this [instance in the `AerodromeConnector`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L63-L64) or even here in the [`BalancerConnector`](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L22), however take a look at how tokens are deposited into the Stargate pool in order to add liquidity https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L49-L70

```solidity
    function depositIntoStargatePool(StargateRequest calldata depositRequest) external onlyManager nonReentrant {
        address lpAddress = LPStaking.poolInfo(depositRequest.poolId).lpToken;
        address underlyingToken = IStargatePool(lpAddress).token();
        if (depositRequest.routerAmount > 0) {
            _approveOperations(underlyingToken, address(stargateRouter), depositRequest.routerAmount);
            //@audit
            stargateRouter.addLiquidity(depositRequest.poolId, depositRequest.routerAmount, address(this));
            _updateTokenInRegistry(underlyingToken);
        }
        if (depositRequest.LPStakingAmount > 0) {
            uint256 stakingAmount = depositRequest.LPStakingAmount;
            if (depositRequest.LPStakingAmount == type(uint256).max) {
                stakingAmount = IERC20(lpAddress).balanceOf(address(this));
            }
            _approveOperations(lpAddress, address(LPStaking), stakingAmount);
            LPStaking.deposit(depositRequest.poolId, stakingAmount);
        }
        _updateTokenInRegistry(rewardToken);
        bytes32 positionId =
            registry.calculatePositionId(address(this), STARGATE_LP_POSITION_TYPE, abi.encode(depositRequest.poolId));
        registry.updateHoldingPosition(vaultId, positionId, "", "", false);
        emit DepositIntoStargatePool(depositRequest);
    }
```

We can see that no slippage logic whatsoever is applied, would be important to note that some of the other connectors have the slippage checked in the external integration they are connecting, i.e in the case where the "minAmount" is less than has been specified the external integration reverts the call, but since that's not the case for `Stargate` then there is a need to natively have the slippage check in the `StargateConnector` and not assume that the slippage check is being delegated, since the [amount of liquidity that ends up being added](https://github.com/stargate-protocol/stargate/blob/main/contracts/Router.sol#L95C1-L105C6) would be what's deposited into via `LPStaking`, so there is a need to ensure that the rate used to get the amount added has not been manipulated or atleast has not dropped over an acceptable difference https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L63

```solidity
            LPStaking.deposit(depositRequest.poolId, stakingAmount);
```

### Impact

Desynchronization in the way connectors are being integrated into NOYA, in this case some connectors have slippage-protected executions, but others do not which could have direct impact on the TVL of the vault.

> Borderline low/medium consider upgrading if applicable.
> Additionally, this bug idea is present in all the other connectors where their integrations does not check for slippage.

### Recommended Mitigation Steps

Consider natively checking for slippage in the `StargateConnector`.

## QA-03 Deadline logic should be included when collecting the fees

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L101-L125

```solidity
    function collectAllFees(uint256[] memory tokenIds) public onlyManager nonReentrant {
        for (uint256 i = 0; i < tokenIds.length; i++) {
            (, address token0, address token1) = getCurrentLiquidity(tokenIds[i]);
            _collectFees(tokenIds[i]);
            _updateTokenInRegistry(token0);
            _updateTokenInRegistry(token1);
            emit CollectFees(tokenIds[i]);
        }
    }


    function _collectFees(uint256 tokenId) internal returns (uint256 amount0, uint256 amount1) {
        CollectParams memory params = CollectParams(tokenId, address(this), type(uint128).max, type(uint128).max);
        (amount0, amount1) = positionManager.collect(params);
    }
```

These functions are used so as to collect fees, however they do not include any deadline logic whatsoever, which means that the attempt at claiming the fees could be hanging in the mempool forever.

It is important to note that the value of fee tokens is constantly fluctuating in the vast majority of pools, so a trade could be profitable at time X but heavily losing at time X + Y. Unfortunately collectAllFees() does not include a deadline parameter similar to most swapping functions like in Uniswap periphery.

Validators can delay the execution of the TX until the fee amounts are available again to be collected, this time with a different evaluation.

### Impact

Loss of fees to be collected.

### Recommended Mitigation Steps

Introduce a deadlining logic when collected the fees.
Impact

An attacker can inflate the value of liquidity through reserve ratio manipulation (even without manipulating the aggregated oracle) and take out a undercollateralized USDS loan.

Proof of Concept

The value of a liquidity position in Salty is determined by:

## QA-04 `AerodromeConnector` is not compatible with executions that deal with `WETH/ETH`

### Proof of Concept

Going to the [AerodromeConnector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L72) contract we can see that it lacks any method for supporting `addLiquidityETH()`/ `removeLiquidityETH()` from Aerodrome.

Keep in mind that the `aerodromeRouter` integrates includes both `addLiquidityETH` and `addLiquidity` and also `removeLiquidity()` & `removeLiquidityETH()` where the ETH prefixed ones deal with executions that deal with `WETH/ETH`, and the `addLiquidityETH()` is even payable, all this can be confirmed from the Router contract provided by Aerodrome: https://github.com/aerodrome-finance/contracts/blob/b934e7ae398ea6c251a4d5af2119776c06f1f23d/contracts/Router.sol#L205-L305.

This then easily means that transactions that deal with native ETH/WETH are completely blocked off from the Connector.

### Impact

Borderline medium/low, since this means that a functionality's availability could be affected in the connect, for e.g there is no how the `addLiquidityETH()` would be processed since it needs the function to be `payable` modified and is not even linked to the contract.

### Recommended Mitigation Steps

Consider supporting the both `ETH` modified increment and decrement of liquidity

## QA-05 Admin can make all parties immediately have an unhealthy position

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L45-L53

```solidity
    function updateMinimumHealthFactor(uint256 _minimumHealthFactor) external onlyMaintainer {
        if (_minimumHealthFactor < MINIMUM_HEALTH_FACTOR) {
            revert IConnector_LowHealthFactor(_minimumHealthFactor);
        }
        minimumHealthFactor = _minimumHealthFactor;
        emit MinimumHealthFactorUpdated(_minimumHealthFactor);
    }


```

We can see that no Max check is applied, so if an admin passes in outrages value like 10e18, then even someone that has 9x their borrowed value as collateral is immediately liquidatable

### Impact

Considering Code4rena's new rule on QA, this is good to point

### Recommended Mitigation Steps

## QA-06 Getting price from `ChainlinkOracleConnector#getValueFromChainlinkFeed()` should be wrapped in a try catch

### Proof of Concept

First take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L110

```solidity
 function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
        if (asset == baseToken || amount == 0) {
            return amount;
        }

        address[] memory sources = priceRoutes[asset][baseToken];

        return _getValue(asset, baseToken, amount, sources);
    }

    function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
        internal
        view
        returns (uint256 value)
    {
        uint256 initialValue = amount;
        address quotingToken = asset;
        for (uint256 i = 0; i < sources.length; i++) {
            initialValue = _getValue(asset, sources[i], initialValue);
            quotingToken = sources[i];
        }
        return _getValue(quotingToken, baseToken, initialValue);
    }

    function _getValue(address quotingToken, address baseToken, uint256 amount) internal view returns (uint256) {
        INoyaValueOracle oracle = priceSource[quotingToken][baseToken];
        if (address(oracle) == address(0)) {
            oracle = priceSource[baseToken][quotingToken];
        }
        if (address(oracle) == address(0)) {
            oracle = defaultPriceSource[baseToken];
        }
        if (address(oracle) == address(0)) {
            oracle = defaultPriceSource[quotingToken];
        }
        if (address(oracle) == address(0)) {
            revert NoyaOracle_PriceOracleUnavailable(quotingToken, baseToken);
        }
        return oracle.getValue(quotingToken, baseToken, amount);
    }
```

Now see the function `oracle.getValue()` finally ends up calling at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L117-L137

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
        uint256 uintprice = uint256(price);
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
        }
        if (price <= 0) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
        if (isInverse) {
            return (amountIn * sourceTokenUnit) / uintprice;
        }
        return (amountIn * uintprice) / (sourceTokenUnit);
    }
```

This function is used to calculate the price of an asset, and is queried via the `getValue()` function, would be key to note that the feeds integrated could be denominated in USD or ETH as hinted by the contract, now protocol implements the `isPrimaryInverse` incase the base and quote tokens are swapped, however we can see that this call lacks error handling for the potential failure of ` source.latestRoundData()` which could fail due to the call to `oracle.latestRoundData()` , note that Chainlink pricefeeds could revert due to whatever reason, i.e say maintenance or maybe the Chainlink team decide to change the underlying address. Now this omission of not considering this call failing would lead to systemic issues, since calls to this would now revert halting any action that requires this call to succeed.

> Keep in mind that the `getValue()` function is heavily used within the protocol in multiple core logics from getting the current position's TVL in `AccountingManger.sol` and some other contracts like the `CompuondConnector` , `OmnichainManagerNormalChain` to multiple other core instances across protocol as can be seen with this [search command](https://github.com/search?q=repo%3Acode-423n4%2F2024-04-noya+getValue+NOT+language%3AText&type=code).

### Impact

Borderline medium/low, as this essentially breaks core functionalities like liquidating and whatever requires for the usd value of an asset to be queried since there would be a complete revert.

### Recommended Mitigation Steps

Wrap the ` source.latestRoundData()` call in a try-catch block, then handle the error (e.g., revert with a specific message or use an alternative pricing method, the latter is a better fix as it ensures the protocol still functions as expected on the fallback oracle.

## QA-07 `StargateConnector#claimStargateRewards()` can easily be broken for some tokens

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/StargateConnector.sol#L103-L107

```solidity
    function claimStargateRewards(uint256 poolId) external onlyManager nonReentrant {
        LPStaking.deposit(poolId, 0);
        _updateTokenInRegistry(rewardToken);
        emit ClaimStargateRewards(poolId);
    }
```

This is the method used in claiming the rewards from stargate, we can see that the approach does this by querying ` LPStaking.deposit(poolId, 0);` however going to the `LPstaking.sol` contract being queried we can see the below https://github.com/stargate-protocol/stargate/blob/main/contracts/LPStaking.sol#L153C1-L166C6

```rust
    function deposit(uint256 _pid, uint256 _amount) public {
        PoolInfo storage pool = poolInfo[_pid];
        UserInfo storage user = userInfo[_pid][msg.sender];
        updatePool(_pid);
        if (user.amount > 0) {
            uint256 pending = user.amount.mul(pool.accStargatePerShare).div(1e12).sub(user.rewardDebt);
            safeStargateTransfer(msg.sender, pending);
        }
        //@audit
        pool.lpToken.safeTransferFrom(address(msg.sender), address(this), _amount);
        user.amount = user.amount.add(_amount);
        user.rewardDebt = user.amount.mul(pool.accStargatePerShare).div(1e12);
        lpBalances[_pid] = lpBalances[_pid].add(_amount);
        emit Deposit(msg.sender, _pid, _amount);
    }
```

That is the `_amount` being passed to be deposited need to be transferred from from the account making this call, i.e in our case that's the StargateConnector.

Now from the `readME`, it's been explicitly stated that any ERC20 token is supported, i.e https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/README.md#L272-L274

```markdown
| Question                   | Answer |
| -------------------------- | ------ |
| ERC20 used by the protocol | Any    |
```

Additionally, under the ERC-20 token behaviours in scope, the below has been explicitly stated in the readMe, https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/README.md#L294

```markdown
| [Revert on zero value transfers](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-zero-value-transfers) | Yes |
```

Which then means that in the case where the `lptoken` being transferred does revert on zero transfers then the attempt at depositing into LPStaking fails and so does the attempt at claiming the rewards.

### Impact

Functionality of a protocol is affected (claiming rewards) and so is it's availability, as it'd be impossible to claim rewards for these tokens via `StargateConnector#claimStargateRewards()`, since on the query to `LPStaking.deposit()`, [this line](https://github.com/stargate-protocol/stargate/blob/main/contracts/LPStaking.sol#L161) reverts the call.

> This was submitted as QA due to the root cause being present in the bot report, however this could be more impactful than QA to protocol

### Recommended Mitigation Steps

Consider explicitly stating these tokens are not supported, or atleast depositing 1 wei of lptoken when attempting to claim the rewards so as to ensure [this line](https://github.com/stargate-protocol/stargate/blob/main/contracts/LPStaking.sol#L161) from the `LPStaking.sol` contract doesn't revert.

## QA-08 `LidoConnector#deposit()` does not function according to spec

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/LidoConnector.sol#L36-L45

```solidity

    function deposit(uint256 amountIn) external onlyManager nonReentrant {
        IWETH(weth).withdraw(amountIn);
        // deposit recieved eth into Lido
        // refferal address can be different
        ILido(lido).submit{ value: amountIn }(address(0));
        _updateTokenInRegistry(steth);
        _updateTokenInRegistry(weth);
        emit Deposit(amountIn);
    }
```

This function is used for depositing into `Lido` and it does this via the `submit()` function, now the documentation explicitly state that the referral address can be different however the referral address in this case has been hardcoded to `0`.

From the official lido docs we can see that the address passed in the `submit()` call is indeed the referral address, i.e https://docs.lido.fi/contracts/lido#submit-1.

### Impact

Protocol's functionality is not working according to spec, since the referral address has been hardcoded where as it should be passed as a param and forwarded to `Lido`.

### Recommended Mitigation Steps

Consider not hardcoding the referral address.

## QA-09 `MorphoBlueConnector#wthdraw()` is not being queried in the most safe manner would fail in some cases

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L58-L73

```solidity
    function withdraw(uint256 amount, Id id, bool sOrC) external onlyManager nonReentrant {
        MarketParams memory params = morphoBlue.idToMarketParams(id);
        if (sOrC) {
            morphoBlue.withdraw(params, amount, 0, address(this), address(this));
        } else {
            morphoBlue.withdrawCollateral(params, amount, address(this), address(this));
        }
        Position memory p = morphoBlue.position(id, address(this));
        if (p.collateral == 0 && p.supplyShares == 0) {
            registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), MORPHO_POSITION_ID, abi.encode(id)), "", "", true
            );
        }
        _updateTokenInRegistry(params.collateralToken);
        emit Withdraw(amount, id, sOrC);
    }
```

This function, queries the `IMorpho#withdraw()` thats defined here https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Morpho/IMorpho.sol#L155-L175 in order to complete the withdrawals, from the attached snippet we can see that it's been advised to instead query this function while passing the `shares` instead of the amount of assets, as this way no reversions would occur due to underflow, but from the attached snippet above we can see that the atttempt to withdraw via the MorphoBlueConnector instead passes the shares as 0 and amounts as non-zerp which could cause some reverts, i.e `morphoBlue.withdraw(params, amount, 0, address(this), address(this))`

### Impact

As documented via the integration the not so safe method is being used when withdrawing, according to the logic we should expect underflow errors that would cause the executions to revert due to not passing in the `shares` paameter instead, would be key to note that whereas this might not be a problem when partial shares are being withdrawn, it would be an issue when the vault manager wants to withdraw all the shares.

### Recommended Mitigation Steps

Consider passing in a `shares` value instead as correctly documented here: https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/interfaces/Morpho/IMorpho.sol#L155-L175.

## QA-10 Protocol does not implement the `estimateFees()` function to know how much a tx should cost

### Proof of Concept

Navigating to https://docs.layerzero.network/v1/developers/troubleshooting/integration-checklist we can see that there is an `estimateFees()` function that exist and is to be used before queries to send cross chain messages so as to know the right amount of gas to pass.

However navigating to the https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/ section in scope we can see no implementation of this function, potentially causing attempts at cross messaging to fail since not enough gas would be provided.

### Impact

Cross chain messaging attempts might now fail which could block the messaging channel since not enough gas would be provided in some cases.

### Recommended Mitigation Steps

Consider implementing `estimateFees()` and ensure that this function is queried to know the right amount of gas fees to pass.

## QA-11 No checks for min/max circuit breakers while querying chainlink data

### Proof of Concept

Take a look at the functionality used for getting prices from Chainlink https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L117-L138

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
        uint256 uintprice = uint256(price);
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
        }
        if (price <= 0) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
        if (isInverse) {
            return (amountIn * sourceTokenUnit) / uintprice;
        }
        return (amountIn * uintprice) / (sourceTokenUnit);
    }

```

Would be key to note that Chainlink's `latestRoundData` is being queried, but no min/max checks are applied, leading to contracts working with flawed pricing.

### Impact

If the prices ever go over the min/max boundary then protocol is going to ingest heavily inflated/deflated pricing data as the prices returned would be wrong.

Considering protocol plans to support a lot of tokens this would to be a problem as multiple tokens would have their source feed's aggregators with this min/max circuit breakers and as such it should be checked for an asset that has it, since this has quite a high impact with a low likelihood, but would be key to note that this has happened before with `LUNA`.

### Recommended Mitigation Steps

Consider attaching the min/max checkers for aggregators that have it.

## QA-12 `updateTVL` has no checks to ensure the payload data being sent via `_lzSend` is not of extraordinary size

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L75-L81

```solidity
    function updateTVL(uint256 vaultId, uint256 tvl, uint256 updateTime) public {
        if (msg.sender != vaultIdToVaultInfo[vaultId].omniChainManager) revert InvalidSender();

        uint32 lzChainId = chainInfo[vaultIdToVaultInfo[vaultId].baseChainId].lzChainId;
        bytes memory data = abi.encode(vaultId, tvl, updateTime);
        _lzSend(lzChainId, data, messageSetting, MessagingFee(address(this).balance, 0), payable(address(this))); // TODO: send event here
    }
```

We can see that this function is used to send a TVL update for a specified vault to its base chai, however the payload data being passed is gotten as `bytes memory data = abi.encode(vaultId, tvl, updateTime);` this means that an arbitrary amount of data could be passed.

Now whenever a very large arbitrary data is passed as the payload, its massiveness could actually cause the channel to be blocked since the data can't be consumed.

### Impact

Failures in updating TVL since there are no checks to ensure the payload data being sent via `_lzSend` is not of extraordinary size.

### Recommended Mitigation Steps

Consider having a max amount of payload Data accepted to curb this.

## QA-13 Hardcoded non-existing underlying tokens and 0 as TVL

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L71-L77

```solidity
    function getPositionTVL(HoldingPI memory p, address baseToken) public view returns (uint256) {
        return 0;
    }

    function getUnderlyingTokens(uint256 positionTypeId, bytes memory data) public view returns (address[] memory) {
        return new address[](0);
    }
```

Evidently no logic is correctly applied when getting the contract's state data, a hardcoded value of `0` has been placed as the `TVL` and then no tokens are claimed to be supported which is the exact opposite of what's been stated in the readME.

### Impact

QA since this is from a mock contract, however it's been explicitly stated in the [readMe](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/README.md#L22) that the contract is in scope.

### Recommended Mitigation Steps

Either remove the contract from the scope of the audit or rightly align it with the docs

## QA-14 Protocol is to be deployed on some optimistic L2 chains but in no instance do they consider the sequencer going down

### Proof of Concept

First note that protocol is to be deployed on multiple chains as outlined for this contest here: https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/README.md#L270-L279

```markdown
### General questions

| Question                                | Answer                                                                     |
| --------------------------------------- | -------------------------------------------------------------------------- |
| Chains the protocol will be deployed on | Ethereum,Arbitrum,Base,BSC,Optimism,Polygon,zkSync,Other,Avaxpolygon zkevm |
```

This list includes multiple optimistic L2s, and with optimistic L2s like Arbitrum, Blast, Optimisim, the sequencer could infact go down, which then leads us to the issue with the timing logics across protocol.

This in short breaks multiple/any timing logics for the L2 to-deploy contracts, keep in mind that in instances where the L2 goes down, the time still counts.

Additionally, take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L117-L138

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
        uint256 uintprice = uint256(price);
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
        }
        if (price <= 0) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
        if (isInverse) {
            return (amountIn * sourceTokenUnit) / uintprice;
        }
        return (amountIn * uintprice) / (sourceTokenUnit);
    }

```

We can see that this is the logic for getting the value and it queries prices from Chainlink that's implemented in the protocol, note that a call to `latestRoundData()` is being made.

However, one thing with using Chainlink on L2 chains is that there is a need to check if the sequencer is down to avoid prices from looking like they are fresh although they are not.
The bug could be leveraged by malicious actors to take advantage of the sequencer downtime.

### Impact

Core functionalities across protocol would be somewhat broken on L2 chains where the networks could be down for a while.

As this in it's sense is like a `pausing` functionality on the chain and any action that's time-restricted has a potential of been flawly finalized, popular bug ideas include users not being able say add collateral if they had borrowed a position making them immediately liquidatable when the sequencer comes back on, etc. but this could be coined to fit into any time-restricted logic.

If the sequencer goes down, the protocol will allow users to continue to operate at the previous (stale) prices.

### Recommended Mitigation Steps

Consider reimplementing the timing logics on the L2 side of the protocol to take the fact that the sequencer could indeed be down into account.

Additionally, since Chainlink recommends that all Optimistic L2 oracles consult the Sequencer Uptime Feed to ensure that the sequencer is live before trusting the data returned by the oracle introduce a seqeuncer check to ensure that the sequencer is active and prices returned are accurate.

## QA-15 `AAVEConnector` could end up holding dust positions

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L79-L98

```solidity
    function withdraw(WithdrawData memory data) public onlyManager nonReentrant {
        bytes32 positionId = registry.calculatePositionId(address(this), AERODROME_POSITION_TYPE, abi.encode(data.pool));
        _approveOperations(data.pool, address(aerodromeRouter), data.amountLiquidity);
        aerodromeRouter.removeLiquidity(
            IPool(data.pool).token0(),
            IPool(data.pool).token1(),
            IPool(data.pool).stable(),
            data.amountLiquidity,
            data.min0Min,
            data.min1Min,
            address(this),
            data.deadline
        );
        if (IERC20(data.pool).balanceOf(address(this)) == 0) {
            registry.updateHoldingPosition(vaultId, positionId, "", "", true);
        }
        _updateTokenInRegistry(IPool(data.pool).token0());
        _updateTokenInRegistry(IPool(data.pool).token1());
        emit Withdraw(data.pool, data.amountLiquidity);
    }
```

We can see that this function is used to withdraw tokens from Aerodrome pool, issue is that unlike other connectors for example see the AaveConnector https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AaveConnector.sol#L106-L109

```solidity
        if (totalCollateralBase <= DUST_LEVEL * 1e7) {
            registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), AAVE_POSITION_ID, ""), "", "", true
            );
```

We can see that there is a check if the positions are now dust positions, however as seen in the snippet from the `AerodromeConnector`'s it instead checks if the `balance == 0` which means that dust positions are going to be supported in the connector.

> Note that, setting the `true` bool means to remove the position in the Registry.

### Impact

`AerodromeConnector` allows dust positions.

### Recommended Mitigation Steps

Consider instead of checking a pure zero balance, check if the position is now dust and remove it in https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L79-L98.

## QA-16 Fix Typos

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L75-L79

```solidity
    /// @notice currentWithdrawGroup is holding the current withdraw group that is waiting for execution
    /// @dev if isStarted is true and isFullfilled is false, it means that the withdraw group is active and we are gethering funds for these withdrawals
    /// @dev if isStarted is false and isFullfilled is false, it means that there is no active withdraw group
    /// @dev if isStarted is true and isFullfilled is true, it means that the withdraw group is fullfilled and but there are still some withdraws that are waiting for execution
    WithdrawGroup public currentWithdrawGroup;
```

This line: `    /// @dev if isStarted is true and isFullfilled is false, it means that the withdraw group is active and we are gethering funds for these withdrawals` meant to say `    /// @dev if isStarted is true and isFullfilled is false, it means that the withdraw group is active and we are gAthering funds for these withdrawals`

- Another instance is the error being passed when rettrieveing tokens for withdrawals https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L560

```solidity
            if (balanceBefore + amount > balanceAfter) revert NoyaAccounting_banalceAfterIsNotEnough();
```

The error `NoyaAccounting_banalceAfterIsNotEnough` should read `balance` instead of `banalce`.

### Impact

Bad code docs

### Recommended Mitigation Steps

Fix the typo

## QA-17 Using the reserves directly could make the execution of calculating the position TVL easily susceptible to an atomic arbitrage attack

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L124-L134

```solidity

    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
        PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
        (address pool) = abi.decode(pBP.data, (address));
        uint256 balance = IERC20(pool).balanceOf(address(this));
        uint256 totalSupply = IERC20(pool).totalSupply();
        (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();
        uint256 amount0 = balance * reserve0 / totalSupply;
        uint256 amount1 = balance * reserve1 / totalSupply;
        return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1);
    }
```

Now here is the implementation of `_getValue()` https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L253-L261

```solidity
    function _getValue(address token, address baseToken, uint256 amount) internal view returns (uint256) {
        if (token == baseToken) {
            return amount;
        }
        if (amount == 0) {
            return 0;
        }
        return valueOracle.getValue(token, baseToken, amount);
    }
```

And the query to `valueOracle.getValue()` just does an evaluation of ` (amount of tokens passed) * price`, i.e from the above we can deduce that the current idea uses the reserves and token prices to calculate the position's TVL.
The value of a liquidity position in Noya is determined by:

- Checking the reserves of the pool/liquidity position (easy to manipulate)
- Valuing the tokens that comprise the liquidity position using an aggregated oracle (difficult to manipulate)

So when the ratio of the tokens deviates from the "correct" ratio (where the ratio corresponds exactly to the correct value of the tokens), the liquidity will always be worth more as calculated by the USD value of the individual tokens. Would be key to note that there is the well known frontrunning attack on liquidity deposits which works based on this fact.

#### Minimalistic Mathematical POC

Let's go through a simple example The pool is USDT-DAI, both tokens with 18 decimals and the oracle always returns a value of $1 for both tokens _(hardcoding $1 for minimalism)_

Currently there is 1e18 tokens in each pool, and let's say that the constant k is 1e36

So the invariant formula: x \* y = K

$$
x = 1e18\

y = 1e18\

k = 1e36\
$$

Let's do a swap which doubles the x variable and recalculate the corresponding y value:

$$
2e18 * y = 1e36 \

y = 0.5e18 \

(x = 2e18)
$$

Now if we apply the correct oracle price of the tokens, which is $1 per 1e18 wei, the value of the LP position is now worth (0.5 + 2) = $2.5 , which is **more**, than the correct value of $2.

A simplified explanation of value inflation in the context of Automated Market Makers (AMMs) and liquidity pools (LPs) can be understood as follows:

When significant trades occur that significantly alter the reserve ratio of a liquidity pool, it can lead to financial outcomes for traders and liquidity providers. If trades cause the reserve ratio to deviate from its ideal balance, traders may incur losses, while liquidity providers (LPs) can benefit from these imbalances. This is the fundamental mechanism behind AMM arbitrage and slippage attacks.

When the price of the LP token is significantly divergent from its correct reserve ratio, it can be perceived as a temporary increase in the token's price, especially when the token's value is evaluated in terms of its USD equivalent. This price inflation results from the trader manipulating the market losing a substantial amount of value in USD terms.

This analogy helps clarify why it's feasible to inflate the LP token's price but not to deflate it. Adjusting the reserve ratio to align with its ideal balance is the strategy for reducing the USD-denominated value of the token. However, the true value of the token should ideally remain close to its correct price, making deflation impossible.

This could idea could then easily lead to an attack since we can now inflate the LP price to borrow more than the liquidity position's real worth. The attacker can then dump and then misbalance the vault potentially making it undercollateralized and then collapse.

### Impact

An attacker can inflate the value of liquidity through reserve ratio manipulation (even without manipulating the aggregated oracle) and integrate with the protocol

> This was submitted as QA due to the likelihood of the attack and the somewhat of a protection provided by the idea of having a Vault manager that deals with a position, however this protection can be a bit sidestepped if we then consider that this could be coupled with atomic arbitraging where an attacker can even intentionally make bad trades only to manipulate pool reserves, walk away with bad debts and the net profit.

More info on this bug idea can be seen [here](https://github.com/code-423n4/2024-01-salty-findings/issues?q=is%3Aissue+Using+Atomic+arbitrage+an+attacker+can+knowingly+make+bad+trades+only+to+manipulate+pool+reserves+and+walk+away+with+bad+debts+and+net+profit+is%3Aclosed).

### Recommended Mitigation Steps

Valuing LP positions is tricky. The current method is to "trust" the untrustworthy pool reserves. Instead, we could value the liquidity as if the ratio was at the correct ratio, rather than the current pool ratio. Here is an example of a protocol implementing this solution for Uniswap v3 positions:

https://github.com/arcadia-finance/accounts-v2/blob/main/src/asset-modules/UniswapV3/UniswapV3AM.sol

## QA-18 `addLiquidity()` doesn't actually add any liquidity

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L40-L49

```solidity
    function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data) external {
        for (uint256 i = 0; i < tokens.length; i++) {
            // gather all of the tokens

            ITokenTransferCallBack(msg.sender).sendTokensToTrustedAddress(tokens[i], amounts[i], msg.sender, "");
        }
        for (uint256 i = 0; i < tokens.length; i++) {
            _updateTokenInRegistry(tokens[i]); // update the token in the registry
        }
    }
```

We can see that this function is used to add liquidity, however in real sense it doesn't add any liquidity compared to a similar implementation here [BaseConnector.\_addLiquidity](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L169-L194) since in this case the tokens are only sent to the trusted addresses however no addition of liquidity is being done.

### Impact

QA since this is from a mock contract, however it's been explicitly stated in the [readMe](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/README.md#L22) that the contract is in scope.

### Recommended Mitigation Steps

Ensure that liquidity is effectively added when necessary.

## QA-19 `sendTokensToTrustedAddress()` is unprotected and anyone can take funds from the contract

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L27-L39

```solidity
    function sendTokensToTrustedAddress(address token, uint256 amount, address caller, bytes memory data)
        external
        returns (uint256)
    {
        if (data.length == 0) {
            IERC20(token).safeTransfer(msg.sender, amount);
            return amount;
        }
        (uint256 amountToSend, uint256 amountToReturn) = abi.decode(data, (uint256, uint256));
        IERC20(token).safeTransfer(msg.sender, amountToSend);
        return amountToReturn;
    }

```

One can see that this function is unprotected and as such any one ca withdraw any amount from the contract.

### Impact

QA since this is from a mock contract, however it's been explicitly stated in the [readMe](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/README.md#L22) that the contract is in scope.

### Recommended Mitigation Steps

Employ some sort of protection around this.

## QA-20 Documentation should never lead to invalid links

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L29-L35

```solidity
    constructor(address _endpoint, address _owner) OAppSender() OAppCore(_endpoint, _owner) { }
    /**
     * @notice Updates the message setting for LayerZero sends
     * @dev Allows the owner to configure how messages are sent through LayerZero, adjusting parameters like gas limits or message fees.
     * @param _messageSetting The new message settings to be used for LayerZero sends (see https://docs.layerzero.network/contracts/options)
     */

```

However navigating to the link [https://docs.layerzero.network/contracts/options](https://docs.layerzero.network/contracts/options) we see an error 404.

### Impact

Users could assume protocol is dealing with shady business having linked url links being inactive.

### Recommended Mitigation Steps

Fix links

## QA-21 Setters should always have equality checkers

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L45-L69

```solidity
    function addHandler(address _handler, bool state) external onlyOwner {
        isHandler[_handler] = state;
        emit AddedHandler(_handler, state);
    }

    /**
     * @notice adding or removing a chain to the list of supported chains
     * @param _chainId uint256 chain id
     * @param state bool state of the chain
     */
    function addChain(uint256 _chainId, bool state) external onlyOwner {
        isChainSupported[_chainId] = state;
        emit AddedChain(_chainId, state);
    }

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

No checks to see if the states are not the already passed in values

### Impact

### Recommended Mitigation Steps

## QA-22 Make `TVLHelper#getTVL()` more effective

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L14-L36

```solidity
    function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
        uint256 totalTVL;
        uint256 totalDebt;
        HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
        for (uint256 i = 0; i < positions.length; i++) {
            if (positions[i].calculatorConnector == address(0)) {
                continue;
            }
            uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);
            bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);
            if (isPositionDebt) {
                totalDebt += tvl;
            } else {
                totalTVL += tvl;
            }
        }
        //@audit the check her would be better if not srict.
        if (totalTVL < totalDebt) {
            return 0;
        }
        return (totalTVL - totalDebt);
    }
```

### Impact

Unnecessary utilization of opcodes such as subtraction, which shouldn't really be the case.

### Recommended Mitigation Steps

Modify https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L14-L36 to

```diff
    function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
        uint256 totalTVL;
        uint256 totalDebt;
        HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
        for (uint256 i = 0; i < positions.length; i++) {
            if (positions[i].calculatorConnector == address(0)) {
                continue;
            }
            uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);
            bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);
            if (isPositionDebt) {
                totalDebt += tvl;
            } else {
                totalTVL += tvl;
            }
        }
        //@audit the check her would be better if not srict.
-        if (totalTVL < totalDebt) {
+        if (totalTVL <= totalDebt) {
            return 0;
        }
        return (totalTVL - totalDebt);
    }
```

## QA-23 Protocol currently hardcodes the logic of pricing WETH

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/WETH_Oracle.sol

```solidity
// SPDX-License-Identifier: Apache-2.0
pragma solidity 0.8.20;

contract WETH_Oracle {
    function latestRoundData()
        external
        view
        returns (uint80 roundId, int256 answer, uint256 startedAt, uint256 updatedAt, uint80 answeredInRound)
    {
        return (0, 1e18, 0, block.timestamp, 0);
    }
}

```

We can see that this contract is used to get the current `WETH` price, however it doesn't comply with the logic around an oracle, i.e there should be a base and a quote token, currently the price is always hardcoded to be `1e18` and then this price ends up being used in multiple instances in scope, however this is not against any qoute token as such the hardcoding logic is flawed, additionally this doesn't take into account that the `WETH` token could depeg.

### Impact

Considering this price would be used in multiple instances it is then advisable to have this correctly query the value of WETH against a valid quote token or atleast the subtle fact that it could depeg, otherwise instances where this function would then be used in `ChainlinkOracleConnector#getValueFromChainlinkFeed()` could lead to an over/undervalue of the real value of assets.

### Recommended Mitigation Steps

Consider correctly applying logic pertaining to oracles and have the base/quote tokens rightly integrated.

## QA-24 Make `Keepers#execute()` more effective

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L84-L119

```solidity
    function execute(
        address destination,
        bytes calldata data,
        uint256 gasLimit,
        address executor,
        bytes32[] memory sigR,
        bytes32[] memory sigS,
        uint8[] memory sigV,
        uint256 deadline
    ) public {
        require(isOwner[msg.sender], "Not an owner");//@audit if more than  the required signature supports the motion the execution stil fails due to the strict sigR.length check
        require(sigR.length == threshold, "Not enough signatures");
        require(sigR.length == sigS.length && sigR.length == sigV.length, "Lengths do not match");
        require(executor == msg.sender, "Invalid executor");
        require(block.timestamp <= deadline, "Transaction expired");
        {
            bytes32 txInputHash =
                keccak256(abi.encode(TXTYPE_HASH, nonce, destination, data, gasLimit, executor, deadline));
            bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));
            address lastAdd = address(0);
            //@audit there is no enforcal that the signatures are going to be provided in an ascending manner in regards to the `recovered > lastAdd` check which would then make executions fail even when valid signatures have been passed... QA since this just needs rearrangement of the way the signatures are passed
            for (uint256 i = 0; i < threshold;) {
                address recovered = ECDSA.recover(totalHash, sigV[i], sigR[i], sigS[i]);
                require(recovered > lastAdd && isOwner[recovered]);
                lastAdd = recovered;
                unchecked {
                    ++i;
                }
            }

            nonce++;
        }
        emit Execute(destination, data, gasLimit, executor, deadline);
        (bool success,) = destination.call{ gas: gasLimit }(data);
        require(success, "Transaction execution reverted.");
    }
```

This function is used so as to executes a transaction if it has been approved by the required number of owners, however there are two noteworthy mentions in regards to the signature verification process that could lead to unexpected behavior or exploitation.

1. **Strict Signature Length Check**: The function requires the number of provided signatures (`sigR`) to exactly match the threshold set by the contract owner. This means that if more than the required number of signatures are provided, the execution will still fail due to the strict length check. This could potentially prevent legitimate transactions from being executed.

2. **Signature Order Verification**: The loop that verifies the signatures does not enforce that the signatures are provided in ascending order. This means that if the signatures are not provided in the expected order, the execution will fail even if valid signatures have been passed. This could lead to legitimate transactions being rejected.

### Impact

QA, since this doesn't really affect the `execute()'s` functionality except if the admin passes in the somewhat wrong data.

### Recommended Mitigation Steps

- Modify the signature length check to allow for additional signatures beyond the required threshold. This will ensure that legitimate transactions with extra signatures can still be executed, so use a `>=` instead.

Implement logic to enforce that the provided signatures are in ascending order. This can be done by checking that each recovered address (`recovered`) is greater than the previous one (`lastAdd`). This will prevent valid transactions from being rejected due to signature order issues.

## QA-25 Some tokens don't support `.balanceOf()` causing some attempts to _swap_ to fail

### Proof of Concept

Take a look at https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L77-L102

```solidity
    function performSwapAction(address caller, SwapRequest calldata _request)
        external
        payable
        override
        onlyHandler
        returns (uint256)
    {
        require(verifySwapData(_request), "LifiImplementation: INVALID_SWAP_DATA");
        uint256 balanceOut0 = 0;
        if (_request.outputToken == address(0)) {
            balanceOut0 = address(_request.from).balance;
        } else {
            balanceOut0 = IERC20(_request.outputToken).balanceOf(_request.from);
        }
        _forward(IERC20(_request.inputToken), _request.from, _request.amount, caller, _request.data, _request.routeId);
        uint256 balanceOut1 = 0;
        if (_request.outputToken == address(0)) {
            balanceOut1 = address(_request.from).balance;
        } else {
            balanceOut1 = IERC20(_request.outputToken).balanceOf(_request.from);
        }

        emit Swapped(balanceOut0, balanceOut1, _request.outputToken);

        return balanceOut1 - balanceOut0;
    }
```

This inherently called whenever there is an attempt to perform any sort of swap action out there, however it always queries the `balanceOf()` method on these tokens which for some tokens would revert causing the attempt to transsfer these tokens and swap them to also revert.

### Impact

See _Proof of Concept_.

### Recommended Mitigation Steps

Consider querying `balanceOf()` on a low level
