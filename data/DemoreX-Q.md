# [NC-01] Deposit and Withdraw queue is limited

> contracts/accountingManager/AccountingManager.sol:200-219 
> contracts/accountingManager/AccountingManager.sol:304-316


Deposit() and Withdraw() functions increment the last field of depositQueue/withdrawQueue object. There is no function to manage last index of the queue. Therefore, it will be increasing continously. Nobody can deposit or withdraw their funds after the max value of uint256. The max value of uint256 has 78 decimals which is extremely large for overflowing and this is why this finding is at not-critical level.

## Proof of Concept Test Function

```solidity
function testFail_OverflowQueue() public {

        // Set queue numbers to max
        // Set function is written for only testing purposes
        vm.startPrank(owner);
        accountingManager.setFirstMiddleLast(type(uint256).max, type(uint256).max, type(uint256).max);
        (uint first, uint middle, uint last, uint tokenAmountWaitingForDeposit) = accountingManager.depositQueue();
        console.log("Set up queue numbers to max");
        console.log("Queue First: %d", first);
        console.log("Queue Middle: %d", middle);
        console.log("Queue Last: %d", last);
        vm.stopPrank();

        // Set up address
        vm.deal(alice, 10 ether);
        _dealWhale(baseToken, address(alice), address(0xf89d7b9c864f589bbF53a82105107622B35EaA40), 11e6);
        vm.startPrank(alice);
        console.log("Balance of Alice before deposit: %d", IERC20(baseToken).balanceOf(address(alice)));
        
        // Set up allowance
        console.log("Giving allowance to accounting manager");
        IERC20(baseToken).approve(address(accountingManager), 11e6);
        
        // Try deposit
        vm.expectRevert();
        accountingManager.deposit(alice, 11e6, alice);
        console.log("Balance of Alice after deposit: %d", IERC20(baseToken).balanceOf(address(alice))); // If this line prints same amount of USDC, it means deposit doesn't work at this point.
        vm.stopPrank();
}
```

## Log results

```terminal
Set up queue numbers to max
Queue First: 115792089237316195423570985008687907853269984665640564039457584007913129639935
Queue Middle: 115792089237316195423570985008687907853269984665640564039457584007913129639935
Queue Last: 115792089237316195423570985008687907853269984665640564039457584007913129639935
Balance of Alice before deposit: 11000000
Giving allowance to accounting manager
Balance of Alice after deposit: 11000000
```

## Normal Deposit Process

```solidity
function test_Deposit() public {

        vm.startPrank(owner);
        (uint first, uint middle, uint last, uint tokenAmountWaitingForDeposit) = accountingManager.depositQueue();
        console.log("Queue First: %d", first);
        console.log("Queue Middle: %d", middle);
        console.log("Queue Last: %d", last);
        vm.stopPrank();

        // Set up address
        vm.deal(alice, 10 ether);
        _dealWhale(baseToken, address(alice), address(0xf89d7b9c864f589bbF53a82105107622B35EaA40), 11e6);
        vm.startPrank(alice);
        console.log("Balance of Alice before deposit: %d", IERC20(baseToken).balanceOf(address(alice)));
        
        // Set up allowance
        console.log("Giving allowance to accounting manager");
        IERC20(baseToken).approve(address(accountingManager), 11e6);
        
        // Try deposit
        accountingManager.deposit(alice, 11e6, alice);
        console.log("Balance of Alice after deposit: %d", IERC20(baseToken).balanceOf(address(alice)));
        vm.stopPrank();
}
```

## Log results

```terminal
Queue First: 0
Queue Middle: 0
Queue Last: 0
Balance of Alice before deposit: 11000000
Giving allowance to accounting manager
Balance of Alice after deposit: 0
```

# NC-02 Slippage tolerance can be set higher than %100

> https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L57C2-L74C6

```solidity
    function setGeneralSlippageTolerance(uint256 _slippageTolerance) external onlyMaintainerOrEmergency {
        genericSlippageTolerance = _slippageTolerance;
        emit SetSlippageTolerance(address(0), address(0), _slippageTolerance);
    }

    /**
     * @notice function responsible for setting the slippage tolerance for a specific pair
     * @param _inputToken address of the input token
     * @param _outputToken address of the output token
     * @param _slippageTolerance uint256 value of the slippage tolerance
     */
    function setSlippageTolerance(address _inputToken, address _outputToken, uint256 _slippageTolerance)
        external
        onlyMaintainerOrEmergency
    {
        slippageTolerance[_inputToken][_outputToken] = _slippageTolerance;
        emit SetSlippageTolerance(_inputToken, _outputToken, _slippageTolerance);
}
```

## Description

The %100 variable defined as 1e6 in the contract, but the above functions can set slippage higher than %100 because it doesn't check the value to be set.