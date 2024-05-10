# Unnecessary token approval when withdrawing collateral 

## Links

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SNXConnector.sol#L45-L48

## Details

There is a futile token approval when withdrawing collateral. 

```solidity

    function withdraw(address _token, uint256 _amount, uint128 _accountId) public onlyManager {
        // Deposit
        _approveOperations(_token, address(SNXCoreProxy), _amount);
```

Consider removing it.


# 