# Deposit and Withdraw queue is limited

> contracts/accountingManager/AccountingManager.sol:200-219 
> contracts/accountingManager/AccountingManager.sol:304-316


Deposit() and Withdraw() functions increment the last field of depositQueue object. There is no function to manage last index of the queue. Therefore, it will be increasing continously. Nobody can deposit or withdraw their funds after the max value of uint256. The max value of uint256 has 78 decimals which is extremely large for overflowing and this is why this finding is at not-critical level.

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
        console.log("Balance of Alice after deposit: %d", IERC20(baseToken).balanceOf(address(alice)));
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
