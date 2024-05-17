1. AccountingManager contract emits deposit event with data in a wrong order and wrong price
As there are off-chain actors like Keepers, events can have an important role for the protocol

Wrong events:
- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L242C1-L244C15
- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L274C13-L276C15

Problem: 
- not correct amount/shares arguments order in the event
- Not correct price formula for share `shares * 1e18 / data.amount` - should be `data.amount * 1e18 / shares`

Correct events structure described:
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/interface/Accounting/IAccountingManager.sol#L117C5-L123C7

2. `AccountingManager::executeDeposit` function reverts with a wrong error when a connector is active, but `processedBaseTokenAmount` is zero

It emits `NoyaAccounting_INVALID_CONNECTOR` while the connector is valid
https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L288C9-L296C10

3. Wrong Reset Fee event
- https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L496

currentProfit and storedProfitForFee should be in reverse