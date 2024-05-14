## [L-1] AccountingManager.sol is not ERC4626 compliant as stated in the contest page.

On the `EIP compliance checklist` on the contest page, it is stated that AccountingManager.sol is compliant with ERC4626. This in incorrect because a lot of difference from the `ERC4626` specifications. some of which are.

1. The `ERC4626` specifications's `deposit`, `mint`, `withdraw` and `redeem` functions on the AccountingManager.sol have been overridden and made to revert. These overriden functions are now replaced with another functions with different signature. 
```
File: AccountingManager.sol
function mint(uint256 shares, address receiver) public override returns (uint256) {
        revert NoyaAccounting_NOT_ALLOWED();
    }

    function withdraw(uint256 assets, address receiver, address owner) public override returns (uint256) {
        revert NoyaAccounting_NOT_ALLOWED();
    }

    function redeem(uint256 shares, address receiver, address shareOwner) public override returns (uint256) {
        revert NoyaAccounting_NOT_ALLOWED();
    }

    function deposit(uint256 assets, address receiver) public override returns (uint256) {
        revert NoyaAccounting_NOT_ALLOWED();
    }

```

2. The `ERC4626` [specifications's](https://eips.ethereum.org/EIPS/eip-4626#maxdeposit) `maxDeposit` function MUST return the maximum allowed asset deposit but the `maxDeposit` still returns `return type(uint256).max`  when infact there are `depositLimitPerTransaction` and `depositLimitTotalAmount` which are used to validate deposits but not returned when the `maxDeposit` function is called.

```
 function maxDeposit(address) public view virtual returns (uint256) {
        return type(uint256).max;
    }
```

3. Also according the `ERC4626` [spec](https://eips.ethereum.org/EIPS/eip-4626#events)
> `Deposit` event MUST be emitted when tokens are deposited into the Vault via the mint and deposit methods. 

However, `Deposit` event was not emitted when tokens are deposited instead a `RecordDeposit` event was emitted with different parameters from the spec's `Deposit` event


Impact: The AccountingManager.sol will not integrate with well ERC4626 interface like generic contracts that are built to work with ERC4626 contracts just like wallets integrate well with ERC20s.

Recommendation: If the main design is for the AccountingManager.sol to integrate well with the ERC4626 interface, consider making it comply to the ERC4626 specification.




