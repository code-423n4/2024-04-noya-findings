## [L-1] No function to cancel your withdrawal request

#### Proof of Concept
There is no way for the user who requested a withdrawal to cancel it. Due to
various factors, such as unfavorable conditions, user may wish to cancel their withdrawal request and request it later.

#### Recommended Mitigation Steps
Implement a function that allows users to cancel their withdrawal request by
deleting their `WithdrawRequest` struct and returning them their `shares` back.

## [L-02] `Keeper::execute` address destination is not checked

#### Proof of Concept
`Keeper::execute` function does not check wether `destination` address contains code or not

#### Recommended Mitigation Steps
```diff
  function execute(
        address destination,
        bytes calldata data,
        uint256 gasLimit,
        address executor,
        bytes32[] memory sigR,
        bytes32[] memory sigS,
        uint8[] memory sigV,
        uint256 deadline
    ) public {
+       require(destination != address(0), "Does not contain any code");
       ...
    }
```