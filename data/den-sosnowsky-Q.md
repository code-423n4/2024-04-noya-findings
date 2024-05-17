AccountingManager contract emits event with data in a wrong order and wrong price
As there are off-chain actors like Keepers, events can have an important role for the protocol

Wrong events:
1. https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L242C1-L244C15
2.https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L274C13-L276C15

Problem: 
1. not correct amount/shares arguments order in the event
2. Not correct price formula for share `shares * 1e18 / data.amount` - should be `data.amount * 1e18 / shares`

Correct events structure described:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L117C5-L123C7
