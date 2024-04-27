# **Multiple gas optimization findings that will reduce gas costs significantly and improve code quality**   
------
  

## [GAS-1] Unused local variables that can be removed to optimize gas  
------
  
**Impact**  
Several contracts in-scope have numerous local variables that have not been used at all and can be removed to improve the code and to reduce unnecessary gas consumption. You can comment also comment out the variables and check their purpose to see if they are necessary.  
  
**PoC**  
>1. contracts/connectors/BalancerConnector.sol(#L117)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L117   
>2. contracts/connectors/BalancerFlashLoan.sol(#L69)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L69  
>3. contracts/connectors/UNIv3Connector.sol(#L129)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L129  
>4. contracts/connectors/PendleConnector.sol(#L79)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L79  
>5. contracts/connectors/PendleConnector.sol(#L98)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L98  
>6. contracts/connectors/PendleConnector.sol(#L153)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L153  
>7. contracts/connectors/PendleConnector.sol(#L170)    
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L170  
>8. contracts/connectors/PendleConnector.sol(#L188)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L188  
>9. contracts/connectors/PendleConnector.sol(#L190)    
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PendleConnector.sol#L190  
>10. contracts/connectors/SNXConnector.sol(#L123)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L123  
  
  
## [GAS-2] State mutability of functions can be restricted to `pure` or `view`  
------  
  
**Impact**  
Functions that can be restricted to `pure` should always be restricted to `pure` as you can call these functions without needing a transaction, without any gas cost and without confirmation delay. It will also prevent you from accidentally reading/writing contract state in functions where you don't want to.  
  
**PoC**  
>1. contracts/accountingManager/AccountingManager.sol:693  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L693  
>2. contracts/accountingManager/AccountingManager.sol(#L697)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L697  
>3. contracts/accountingManager/AccountingManager.sol(#L701)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L701  
>4. contracts/accountingManager/AccountingManager.sol(#L705)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L705   
>5. contracts/helpers/LZHelpers/LZHelperSender.sol(#L40)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperSender.sol#L40  
  
  
## [GAS-3] Unused function parameter has no purpose and ends up costing more gas  
------
  
**Impact**  
Unused function parameters lead to utilization of higher gas costs. This can be optimized by removal of such parameters or commenting them out. You can check again to see if they serve any purpose, if not, please remove them to save gas.  
  
**PoC**  
>1. contracts/helpers/ConnectorMock2.sol(#L27)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L27  
>2. contracts/helpers/ConnectorMock2.sol(#L40)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L40  
>3. contracts/helpers/ConnectorMock2.sol(#L71)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L71  
>4. contracts/helpers/ConnectorMock2.sol(#L75)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/ConnectorMock2.sol#L75  
>5. contracts/connectors/CamelotConnector.sol(#L99)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CamelotConnector.sol#L99  
>6. contracts/connectors/CompoundConnector.sol(#L134)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/CompoundConnector.sol#L134  
>7. contracts/connectors/FraxConnector.sol(#L142)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/FraxConnector.sol#L142  
>8. contracts/connectors/MaverickConnector.sol(#L161)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MaverickConnector.sol#L161  
>9. contracts/connectors/MorphoBlueConnector.sol(#L137)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L137  
>10. contracts/accountingManager/AccountingManager.sol:693  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L693  
>11. contracts/accountingManager/AccountingManager.sol(#L697)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L697  
>12. contracts/accountingManager/AccountingManager.sol(#L701)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L701  
>13. contracts/accountingManager/AccountingManager.sol(#L705)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L705  
>14. contracts/connectors/AerodromeConnector.sol(#L117)  
>https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L117  