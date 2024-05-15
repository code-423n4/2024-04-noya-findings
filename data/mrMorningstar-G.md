## In `MorphoBlueConnector::convertCToL` the `collateral` address is not used

## Code
https://github.com/code-423n4/2024-04-noya/blame/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L137-L139

```javascript
    function convertCToL(uint256 amount, address marketOracle, address collateral) public view returns (uint256) {
        return amount * IOracle(marketOracle).price() / ORACLE_PRICE_SCALE;
    }
```
In the `convertCToL` the `collateral` address parameter is sent but it is not used in function.

## Recommendation
Remove it to save gas and make code cleaner as it is not used.