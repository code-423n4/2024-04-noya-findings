# LOW REPORT

## [L-01] The `managementFeeAmount` can be manipulated via donation attack

The `collectManagementFees` is in charge to mint the shares for the `managementFeeReceiver`:

```solidity
 function collectManagementFees() public onlyManager nonReentrant returns (uint256, uint256) {
        if (block.timestamp - lastFeeDistributionTime < 1 days) {
            return (0, 0);
        }
        uint256 timePassed = block.timestamp - lastFeeDistributionTime;
        if (timePassed > 10 days) {
            timePassed = 10 days;
        }
        uint256 totalShares = totalSupply();
        uint256 currentFeeShares = balanceOf(managementFeeReceiver) + balanceOf(performanceFeeReceiver)
            + preformanceFeeSharesWaitingForDistribution;  <------

        uint256 managementFeeAmount =
            (timePassed * managementFee * (totalShares - currentFeeShares)) / FEE_PRECISION / 365 days; 
        _mint(managementFeeReceiver, managementFeeAmount);
        emit CollectManagementFee(managementFeeAmount, timePassed, totalShares, currentFeeShares);
        lastFeeDistributionTime = block.timestamp;
        return (managementFeeAmount, timePassed);
    }
```

The problem is that the `managementFeeAmount` can be manipulated sending tokens to directly to the `managementFeeReceiver` or `performanceFeeReceiver` reducing his fees in more proportion than an attacker donation.

##Impact

The `managementFeeReceiver` can receive less fess if a an attacker send tokens directly to his wallet.

## Tool used
Manual review

## Recommendation
Consider don't relay in balanceOf because can be easily manipulated instead relay on internal accounting.


## [L-02] Burn shares is not implementing `whenNotPaused` modifier

The burn function is missing `whenNotPaused` modifier which is implemented in the rest of the public users functions.

```solidity

    function burnShares(uint256 amount) public {
        _burn(msg.sender, amount);
    }

```
[[Link]](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L543C1-L546C1)


## Impact
Users can burn his shares even when the contract is paused.

## Tool used
Manual review

## Recommendation

Implement `whenNotPaused` modifier in the burn function

