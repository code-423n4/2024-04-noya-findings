# L - BTC/USD shouldn’t be used to price WBTC 

# **Vulnerability Detail**

Based on the developer comment, the contract aim to derive the price of the WBTC based on the BTC/USD price feed. Such attitude is vulnerable and highly encourage you not to use such attitude. If the WBTC bridge is compromised and WBTC depegs from BTC, the protocol will continue to price WBTC using the BTC/USD price, even though WBTC will instantly become worth far less than native BTC due to the bridge compromise.
# **Impact**

Users could then buy WBTC for a far lower value than native BTC, deposit it into the protocol, and borrow against it using the value of native BTC. This would allow attackers to drain the protocol in the event of a bridge compromise leading to a depeg event.
# **Recommendation**

To help address this issue, the protocol could use [Chainlink’s WBTC/BTC price feed](https://etherscan.io/address/0xfdFD9C85aD200c506Cf9e21F1FD8dd01932FBB23) to monitor for a depeg event.

---

# L - _getPositionTVL in the Silo connector could be manipulated by simply sending token. The amount must be retrieved directly from the Silo.

As we can see that depositAmount / borrowAmount fetched directly from the Silo connector. Such attitude is vulnerable to the griefing/DoS/price manipulation. I would recommend to use the state function , that fetches the prices directly from the Silo protocol.

https://devdocs.silo.finance/smart-contracts-overview/core-protocol/silo#state

```solidity
//@note in any case i assume that it is not correct to retrieve the data directly, use the state function instead. Could be manipulated
uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));
depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));
uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));
```

The TVL could be manipulated by simply sending tokens.

Function state from the Silo should be used instead

---

# L - Instead of calculating the fee via _quote we hardcode the params. → MessagingFee(address(this).balance, 0)

In the updateTVL in the LzHelperSender instead of sending the correct amount of fees, the contract send all of the his balance, which could lead to the problems if the LayerZero channel  would be stuck.

LayerZero clearly defines that it is recommend to calculate the exact amount of gas that should be sent during the tx.

> To estimate how much gas a message will cost to be sent and received, you will need to implement a `quote` function to return an estimate from the Endpoint contract to use as a recommended `msg.value`.
> 

MessagingFee uses all the balance instead of the correctly calculated msg.value.

```solidity
_lzSend(
            lzChainId, 
            data, 
            messageSetting, 
            //@audit quoteLayerZeroFee should be used, because the wrongfees always send.!
            MessagingFee(address(this).balance, 0), 
            payable(address(this))
```

Such attitude imposes the bridging risks. Message congestion’s could happen and it would take too long to wait for the tx execution. In the meantime the address(connector).balance would be 0 since we don’t receive the refund yet, and it will prevent from updatingTVL if it would be necessary. Overall, we heavily rely on the LayerZero and in case on small trouble on their side our contract would be non-working.

Implement the quote function right before the _lzSend , to calculate the exact msg.value that will be passed into the MessagingFee. Don’t send all the balance.

---

# L - During the withdrawWeiFromDefaultAccount in the Dolomite contract,  AccountBalanceHelper.BalanceCheckFlag is set to None, which could cause an unintended behaviours

Firstly, i would like to mention that 2 month ago the Dolomite was hacked, that’s why i highly recommend to cautiously review whether you should interact with this protocol. At least some time should be taken before the contract will go through the multiple audits.

Secondly, AccountBalanceHelper.BalanceCheckFlag is set to None. BalanceCheckFlag Checks that either BOTH, FROM, or TO accounts do not have negative balances. 

When the position is closed or opened Flag used to check if `_fromAccountNumber`, `_toAccountNumber`, or both accounts can go negative after the transfer settles. Setting the flag to `BalanceCheckFlag.None=3` results in neither account being checked.
# **Proof of Concept**

An example: you have 1 ETH and 1000 USDC supplied.
You decide to withdraw 1500 USDC. This puts your position in a +1 ETH state and -500 USDC debt. Your ETH is now collateralizing your debt and is subject to liquidation if you go under water 

Consequently, the manager could accidentally put the Connector position in the borrow state.
It's noted that in web applications or dApps, there is a risk of data being out of sync due to various factors like quick submissions, slow internet connections, etc. The withdrawal flags help mitigate this risk by ensuring alignment between the user's intention and the application's state.
# **Impact**

Withdrawing more than your supplied balance (to a negative number) will put you in a borrowed state according to the docs.
# **Recommendation**

Change the NONE to the BOTH.

https://docs.dolomite.io/developer-documentation/depositing-or-withdrawing

# L - Prisma connector uses the function, which was hacked in March 2024

# **Vulnerability Detail**

The Prisma connector uses the vulnerable function, and the contracts that utilized this function lost their funds in the March 2024. `setDelegateApproval`

https://hackmd.io/@PrismaRisk/PostMortem0328

I highly recommend to evaluate precisely whether it worth to interact with the protocol now. Be sure that the protocol gone through multiple audits before integrating it. Instead, the funds are at risks.

# L - In the GearBox it’s recommend to utilise function to quote the balances, otherwise the position can't be opened

# **Vulnerability Detail**

The position in the GearBox couldn’t be opened, if the total quotas for the target assets is at limit. The GearBox connector doesn’t check for it before opening the position.
# **Proof of Concept**

https://dev.gearbox.fi/credit/open
# **Impact**

Position can't be opened and the function will revert.
# **Recommendation**

Check the quote of the assets and ensure that it is not at the limit as stated in the GearBox documentation.

https://dev.gearbox.fi/credit/open

# L - LI_FI_GENERIC_SWAP_SELECTOR could be changed in the new versions, but it is constant and cannot be changed!

# **Vulnerability Detail**

In the LifiImplementation LI_FI_GENERIC_SWAP_SELECTOR is set to constant. Lifi works through the diamond proxies, it means that any time in the future the new version of the implementation contract could be release. So, implement the selector as constant is dangerous because in the future LiFi upgrade, the function selector could be changed, thus the verifySwapData function would always revert.
# **Impact**

If the Lifi Upgrade will happen and the selector will be changes, the verifySwapData would always revert and become non-functional.
# **Recommendation**

Don’t make LI_FI_GENERIC_SWAP_SELECTOR constant, and create the function that would allow to reset the function selector.