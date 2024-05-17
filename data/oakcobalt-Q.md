### Low-01 Strategy manager might get the performance fee even though profit dropped. 
**Instances(1)**
In AccountingManager.sol, performance fee is only intended to be awarded when there's a profit increase. Current mechanism is whenever there is a profit increase `getProfit()` >= totalProfitCalculated, the manager role would call `recordProfitForFee()` and the performance fee is recorded in `performanceFeeSharesWaitingForDistribution`. 
```solidity
    function recordProfitForFee() public onlyManager nonReentrant {
        storedProfitForFee = getProfit();
        profitStoredTime = block.timestamp;

        if (storedProfitForFee < totalProfitCalculated) {
            return;
        }

|>      preformanceFeeSharesWaitingForDistribution =
            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);
        emit RecordProfit(
            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
        );
    }
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L483)

And whenever there is a profit drop, someone /any can call `checkIfTVLHasDroped()`, such that `performanceFeeSharesWaitingForDistribution` will be cleared to 0. 
```solidity
    function checkIfTVLHasDroped() public nonReentrant {
        uint256 currentProfit = getProfit();
        if (currentProfit < storedProfitForFee) {
            emit ResetFee(currentProfit, storedProfitForFee, block.timestamp);
|>          preformanceFeeSharesWaitingForDistribution = 0;
            profitStoredTime = 0;
        }
    }
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L497)

The problem is there is no ensuring that `checkIfTVLHasDroped()` will be called in time or at all by anyone to clear recorded performance fee. The impact is that performance fee can be awarded even though there is a profit drop, which unfairly deflates users' share value.

Recommendations:
Considering make `checkIfTVLHasDroped()` as a hook everytime [TVL()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L628) is called, so that performance fee can be updated automatically in various flows.

### Low-02 In the multisig Keepers.sol, any tx that has more than required number of signatures will revert due to vulnerable signature threshold checks.
**Instances(1)**
In Keepers::execute, the signature threshold check is vulnerable and will revert execution if more than the required number of signatures are passed.
```solidity
//contracts/governance/Keepers.sol
    function execute(
    ...
|>       require(sigR.length == threshold, "Not enough signatures");
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L96)

Recommendations:
Change the check `sigR.length >= threshold`.

### Low-03 Keepers cannot execute any external calls that require `msg.value`.
**Instances(1)**
In Keepers::execute, if signature threshold is met, any external call can be executed through a low-level call. However, current implementation will prevent any msg.value to be sent over the call, disabling the ability for keeprs to call a payable external method.
```solidity
//contracts/governance/Keepers.sol
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
...
|>      (bool success,) = destination.call{ gas: gasLimit }(data);
        require(success, "Transaction execution reverted.");
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/governance/Keepers.sol#L116)

Recommendations:
In destination.call, add msg.value options to enable calling a payable method with native ETH.

### Low-04 bridgeRequest encoding with no nonce implementation, risk of bridging revert in edge conditions
**Instances(1)**
In OmnichainLogic::startBridgeTransaction, bridgeRequest is encoded without a nonce. This means that if two adjacent bridgeRequet are identical (e.g. sending tokens), the encoding will be identical, resulting in a conflicted key in approvedBrdigeTXN mapping.
```solidity
//contracts/helpers/OmniChainHandler/OmnichainLogic.sol
    function startBridgeTransaction(BridgeRequest memory bridgeRequest) public onlyManager nonReentrant {
|>       bytes32 txn = keccak256(abi.encode(bridgeRequest));
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L69)

When the manager approve the two identical bridgeQuest, the second `updateBridgeTransactionApproval()` call will actually delete the approval for the first bridgeQuest. In the above edge condition, two adjacent bridgeRequest share the save approvedBrdigeTXN mapping storage. 
```solidity
    function updateBridgeTransactionApproval(bytes32 transactionHash) public onlyManager {
|>      if (approvedBridgeTXN[transactionHash] != 0) delete approvedBridgeTXN[transactionHash];
        else approvedBridgeTXN[transactionHash] = block.timestamp;
        emit UpdateBridgeTransactionApproval(transactionHash, block.timestamp);
    }
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L58)

As a result, after BRIDGE_TXN_WAITING_TIME time has passed, executing either bridgeQuest will [revert and fail due to canceled approval info](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainLogic.sol#L71).

Recommendations:
Consider adding a nonce in bridgeRequest encoding.

### Low-05  executeSwap and executeBridge are not able to perform swap or bridge with Native token due to missing msg.value implementation
**Instances(2)**
LifiImplementation.sol supports [swapping/bridging with native tokens](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/Implementaions/LifiImplementation.sol#L176). 

However, this native ETH swapping bridging functionality will be disabled by GenericSwapAndBridgeHandler.sol, because the handler failed to add msg.value compatibility.
(1)
```solidity
//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol
    function executeSwap(SwapRequest memory _swapRequest)
        external
        payable
        onlyEligibleUser
        onlyExistingRoute(_swapRequest.routeId)
        nonReentrant
        returns (uint256 _amountOut)
    {
...
          //@audit even though executeSwap is payable, ETH will not be forwarded to SwapImplementation contract
|>        _amountOut = ISwapAndBridgeImplementation(swapImplInfo.route).performSwapAction(msg.sender, _swapRequest);
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L115)

(2)
```solidity
//contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol
    function executeBridge(BridgeRequest calldata _bridgeRequest)
        external
        payable
        onlyEligibleUser
        onlyExistingRoute(_bridgeRequest.routeId)
        nonReentrant
    {
...
          //@audit even though executeBridge is payable, ETH will not be forwarded to SwapImplementation contract        ISwapAndBridgeImplementation(bridgeImplInfo.route).performBridgeAction(msg.sender, _bridgeRequest);
...
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L137)

In addition, any native ETH sent through GenericSwapAndBridgeHandler::executeBridge might be stuck in the contract if any future external bridging protocol doesn't revert the tx. 

Recommendations:
Pass `msg.value` to the implementation contract's methods.

### Low-06 AccountingManager's TVL will be incorrect if debt and non-debt positions have the same underlying token.
**Instances(1)**
A trustedPosition can either be a debt position or non-debt position. And all underlying token's holdingPositions that are calculated by AccountingManager have the same trustedPosition id encoding method(BaseConnector::_updateTokenInRegistry).
```solidity
//contracts/helpers/BaseConnector.sol
    function _updateTokenInRegistry(address token, bool remove) internal {
        (address accountingManager,) = registry.getVaultAddresses(vaultId);
        // the value function is inside the accounting manager contract (so we can use the accounting manager address as the calculator connector)
          //@audit All holding positions with the same underlying token will use the same trustedPositionID = keccak256(abi.encode(accountingManager, 0, abi.encode(token)))
|>        bytes32 positionId = registry.calculatePositionId(accountingManager, 0, abi.encode(token));
        // if the token is not in the registry, we add it or remove it if the remove flag is true
        uint256 positionIndex =
            registry.getHoldingPositionIndex(vaultId, positionId, address(this), abi.encode(address(this)));
        if ((positionIndex == 0 && !remove) || (positionIndex > 0 && remove)) {
            emit UpdateTokenInRegistry(token, remove);
            registry.updateHoldingPosition(vaultId, positionId, abi.encode(address(this)), "", remove);
        }
```
(https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L138)

As seen above, all holding positions with the same underlying token will use the same trustedPositionID = `keccak256(abi.encode(accountingManager, 0, abi.encode(token)))`. This means that the vault will have the debt holdingPositions and non-debt holdingPositions sharing the same trustedPosition ID.

This creates a problem when calculating TVL (TVLHelpper::getTVL), because both debt /non-debt holdingPositions will [be counted the same way](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/TVLHelper.sol#L24-L27) based on their shared trustedPosition. So the shared trustedPostion is a debt position, the non-debt holding position will also be counted as debt. Vice versa.

Recommendations:
Consider changing BaseConnector's _updateTokenInRegistry to allow for debt holding positions to use a different trusted position Id, perhaps input a different position type.
