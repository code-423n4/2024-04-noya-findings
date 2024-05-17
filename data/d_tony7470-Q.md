## [01]
`AccountingManager.sol` charges fees for each withdrawal request. The amount of fees cannot exceed 5 percent. 
```solidity
uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
```
The problem is in the fees calculation. If the withdrawal amount is small enough, the user can avoid paying the fees. Let's suppose that the base token is an expensive token with low decimals, for example WBTC, and the fees is set at 0,1% (1e3). To avoid paying the fees, the user will withdraw such amounts that the fees is rounded down to 0:
```solidity
uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;

feeAmount = 999 * 1e3 / 1e6;

feeAmount = 0;
```
Recommended to round up when calculating fees.

## [02]
The deposit process is divided into several stages: first, the user deposits funds, then the number of shares is calculated, and then they are sent to the user. The problem is that the user may increase the current deposit request after the previous one has already been calculated. This can happen because these functions are spaced out in time, which can be minutes or even hours. If this happens, the user will be sent a number of shares equal to their previous non-updated deposit, but the full amount deposited will be sent, meaning the user will receive much less funds than expected.
It is recommended not to allow users to deposit funds into the current deposit queue after the number of shares has been calculated for it.