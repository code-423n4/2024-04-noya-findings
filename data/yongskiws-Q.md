# QA-1 Hardcoded decimal places caused incorrect
When calculating  in terms of underlying token then it is multiplied by the corresponding price finally its divided by the corresponding decimal places. But here it has been divided by the 1e18. 

for example
If we consider the WBTC here
Consider the current price of WBTC = 30000 USD 
2 WBTC token = 2 x 10^8 (Decimals of WBTC = 10 ^ 8)
So usdValue = 30000 x 2 x 10^ 8 / 1e18
This value round off to zero.
But the correct value should be = 30000 x 2 x 10^ 8 / 10^ 8 = 60000 USD

``` solidity
connectors\CompoundConnector.sol
  119,110:                 if (riskAdjusted) CollValue += collateralValueInVirtualBase * info.liquidateCollateralFactor / 1e18;
  78,46:         return getCollBlanace(comet, true) * 1e18 / borrowBalanceInBase;

connectors\PendleConnector.sol
  271,79:                 SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;
  275,92:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;
  280,82:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;

connectors\SiloConnector.sol
  124,57:             totalDepositAmount += depositAmount * price / 1e18;
  125,50:             totalBAmount += borrowAmount * price / 1e18;


connectors\BalancerConnector.sol
  172,19:         return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);

connectors\FraxConnector.sol
  136,51:         uint256 currentHF = (fraxlendPairMaxLTV * 1e18) / currentPositionLTV;

connectors\PendleConnector.sol
  271,81:                 SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;
  275,94:             if (PTAmount > 0) SYAmount += PTAmount * IPMarket(market).getPtToAssetRate(10) / 1e18;
  280,84:             if (SYAmount > 0) underlyingBalance += SYAmount * _SY.exchangeRate() / 1e18;

connectors\SiloConnector.sol
  123,56:             uint256 price = _getValue(assets[i], base, 1e18);
  124,59:             totalDepositAmount += depositAmount * price / 1e18;
  125,52:             totalBAmount += borrowAmount * price / 1e18;

```
Recommendation: 
It should be divided by the corresponding decimals for each underlying tokens.

# QA-2 Invalid Validation `sendTokensToTrustedAddress`

Ensure that only authorized entities can call this function by adding validation

File: accountingManager.sol

``` solidity
    function sendTokensToTrustedAddress(address token, uint256 amount, address _caller, bytes calldata _data)
        external
        returns (uint256)
    {
        emit TransferTokensToTrustedAddress(token, amount, _caller, _data);
        if (registry.isAnActiveConnector(vaultId, msg.sender)) {
            IERC20(token).safeTransfer(address(msg.sender), amount);
            return amount;
        }
        return 0;
    }
```

Recommendation: check or check again add some parameters 

# QA-3 consider Use of delete on Dynamic Arrays `depositQueue``

Removes elements from an array by shifting elements and reducing the size of the array.

File: accountingManager.sol

Recommendation:

``` solidity
// Example of a function to remove elements from the depositQueue array
function removeDepositQueueItem(uint index) internal {
    require(index < depositQueue.length, "Index out of bounds");
    for (uint i = index; i < depositQueue.length - 1; i++) {
        depositQueue[i] = depositQueue[i + 1];
    }
    depositQueue.pop();
}
```

# QA-4 Added Check for Overly Low Cost Values on constructor

Added checks to ensure that fees are not set to undesired values.

File: accountingManager.sol

``` solidity

        if (
            p._withdrawFee > WITHDRAWAL_MAX_FEE || p._performanceFee > PERFORMANCE_MAX_FEE
                || p._managementFee > MANAGEMENT_MAX_FEE
        ) {
            revert NoyaAccounting_INVALID_FEE();
        }


```

Recommendation:

``` solidity
if (
    p._withdrawFee > WITHDRAWAL_MAX_FEE || p._withdrawFee < MIN_WITHDRAWAL_FEE ||
    p._performanceFee > PERFORMANCE_MAX_FEE || p._performanceFee < MIN_PERFORMANCE_FEE ||
    p._managementFee > MANAGEMENT_MAX_FEE || p._managementFee < MIN_MANAGEMENT_FEE
) {
    revert NoyaAccounting_INVALID_FEE();
}
```

# QA-5 Underlying assets stealing via share price manipulation 1 wei 

ERC4626 vaults are subject to a share price manipulation attack that allows an attacker to steal underlying tokens from other depositors (this is a known issue of Solmate's ERC4626 implementation).

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L226

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L257


Recommendation:

consider requiring a reasonably high minimal amount of assets during first deposit. The amount needs to be high enough to mint many shares to reduce the rounding error and low enough to be affordable to users.
On the first deposit, consider minting a fixed and high amount of shares, irrespective of the deposited amount.
Consider seeding the pools during deployment. This needs to be done in the deployment transactions to avoiding front-running attacks. The amount needs to be high enough to reduce the rounding error.
Consider sending first 1000 wei of shares to the zero address. This will significantly increase the cost of the attack by forcing an attacker to pay 1000 times of the share price they want to set. For a well-intended user, 1000 wei of shares is a negligible amount that won't diminish their share significantly.


# QA-6 No slippage check during in accountingManager 

the value of accountingManager shares will be less, as a result this may cause users to withdraw less assets than expected.The EIP-4626 mentions that "If implementors intend to support EOA account access directly, they should consider adding an additional function call for deposit/mint/withdraw/redeem with the means to accommodate slippage loss or unexpected deposit/withdrawal limits, since they have no other means to revert the transaction if the exact output amount is not achieved."

```solidity
noya\accountingManager\AccountingManager.sol

    function calculateDepositShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
        uint256 middleTemp = depositQueue.middle;
        uint64 i = 0;

        uint256 oldestUpdateTime = TVLHelper.getLatestUpdateTime(vaultId, registry);

        while (
            depositQueue.last > middleTemp && depositQueue.queue[middleTemp].recordTime <= oldestUpdateTime
                && i < maxIterations
        ) {
            i += 1;
            DepositRequest storage data = depositQueue.queue[middleTemp];

            uint256 shares = previewDeposit(data.amount);
            data.shares = shares;
            data.calculationTime = block.timestamp;
            emit CalculateDeposit(
                middleTemp, data.receiver, block.timestamp, shares, data.amount, shares * 1e18 / data.amount
            );

            middleTemp += 1;
        }

        depositQueue.middle = middleTemp;
    }

    function recordProfitForFee() public onlyManager nonReentrant {
        storedProfitForFee = getProfit();
        profitStoredTime = block.timestamp;

        if (storedProfitForFee < totalProfitCalculated) {
            return;
        }

        preformanceFeeSharesWaitingForDistribution =
            previewDeposit(((storedProfitForFee - totalProfitCalculated) * performanceFee) / FEE_PRECISION);
        emit RecordProfit(
            storedProfitForFee, totalProfitCalculated, preformanceFeeSharesWaitingForDistribution, block.timestamp
        );
```

Recommendation:

Introduce additional parameters in deposit, mint, withdraw, and redeem functions that allow users to specify slippage tolerance

