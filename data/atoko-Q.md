## Low Risk Findings

| Number        | issue           | Instances  |
| ------------- |:-------------:| -----:|
| [L-01] | Lack of Batch ID in Transaction Execution | 1 |
| [L-02] | Low level calls to account with no code will not fail      |   2 |
| [L-03] | Prevent gas griefing attacks that’s possible with custom address.call      |  2 |
| [L-04] | Missing check for address existence   |  2 |
| [L-05] | Missing Check for Duplicate Trusted Tokens    |  1 |
| [L-06] | Unhandled chainlink revert    |  1 |
| [L-07] | check to ensure size of array is equal     |  1 |


## [L-01] : Lack of Batch ID in Transaction Execution

The absence of a batch ID in the execute function for transaction execution can lead to potential issues in tracking, sequencing, and auditing transactions, especially when multiple transactions are executed simultaneously or in rapid succession.  It allows you to group multiple transactions together under a single identifier, making it easier to manage and track them collectively. This is particularly useful in systems where multiple actions need to be performed

POC

When multiple transactions are executed, there may be ambiguity in the order of execution, which can lead to unexpected behavior or conflicts.
Lack of a batch ID makes it difficult to ensure that transactions are processed in the correct order, potentially causing discrepancies in state changes.

recommendation

Modify the execute function to include a batchId parameter, which uniquely identifies each group of transactions executed together.

```javascript
function execute(
    uint256 batchId, // Introduce batchId
    address destination,
    bytes calldata data,
    uint256 gasLimit,
    address executor,
    bytes32[] memory sigR,
    bytes32[] memory sigS,
    uint8[] memory sigV,
    uint256 deadline
```

***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L84


## [L-02] : Low level calls to account with no code will not fail 

Low level calls to account with no code will not fail

Low level calls `(i.e. address.call(...))` to account with no code will silently succeed without reverting or throwing any error. Quoting the reference for the CALL opcode in evm.codes:

Creates a new sub context and execute the code of the given account, then resumes the current one. Note that an account with no code will return success as true.

***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L116

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L685


## [L-03] : Prevent gas griefing attacks that’s possible with custom address.call 

Whenever the returned bytes data is not required, using the .call() function with non TRUSTED addresses opens the transaction to unnecessary gas griefing by return huge bytes data.

Note that this:

```javascript
 (bool success,) = destination.call{ gas: gasLimit }(data);
        require(success, "Transaction execution reverted.");

```
So in both cases, the bytes data is returned and copied to memory. Malicious target address can return huge bytes data to cause gas grief to the sender. 

Impact:
Malicious target address can gas grief the sender making the sender waste more gas than necessary.

Recommendation:
Short term: When returned data is not required, use a low level call:

```javascript
(bool success, ) = destination.call{ gas: gasLimit }(data);
if (!success) {
    assembly {
        revert(0, 0)
    }
}
```
Long Term: Consider using https://github.com/nomad-xyz/ExcessivelySafeCall

***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L116

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L685

## [L-04] : Missing check for address existence 

The target address in the execute(...) function was not checked for address existence before making a .call(...) to it.

According to Solidity docs:

The low-level functions call, delegatecall and staticcall return true as their >first return value if the account called is non-existent, as part of the design of >the EVM. Account existence must be checked prior to calling if needed.

Source: https://docs.soliditylang.org/en/latest/control-structures.html#error-handling-assert-require-revert-and-exceptions

Impact
If target address does not exist, the boolean return value from .call(...) will return true when infact the asset was not transferred.

Recommendation:
Implement contract existence check before address.call().

(bool success,) = destination.call{ gas: gasLimit }(data);
        require(success, "Transaction execution reverted.");


***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L116

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L685

## [L-05] : Missing Check for Duplicate Trusted Tokens 

The current implementation of the updateConnectorTrustedTokens function allows tokens to be added to the list of trusted tokens multiple times without any validation. This can lead to inconsistencies and potential vulnerabilities in the system.

Proof of Concept (PoC):
Consider the following scenario:

Token A is added to the list of trusted tokens.
Due to a bug or oversight, Token A is added again to the list of trusted tokens.
In this scenario, Token A will be considered trusted twice, which could cause unexpected behavior or vulnerabilities in the system.

Recommendation:
Implement a check in the updateConnectorTrustedTokens function to ensure that a token is not added to the list of trusted tokens if it is already trusted. This can be achieved by checking whether the token is already marked as trusted before setting its trusted status.

```javascript
for (uint256 i = 0; i < _tokens.length; i++) {
        // Validate token 
        require(!vault.connectors[_connectorAddress].trustedTokens[_tokens[i]], "Token already trusted");
        
        // Update trusted status
        vault.connectors[_connectorAddress].trustedTokens[_tokens[i]] = trusted;

        // Emit event
        emit ConnectorTrustedTokenUpdated(vaultId, _connectorAddress, _tokens[i], trusted);
    }
```

Adding this check will prevent duplicate trusted tokens, ensuring consistency and reducing the potential for vulnerabilities in the system.


## [L-06] : Unhandled chainlink revert 

Call to `latestRoundData` could potentially revert and make it impossible to query any prices. Feeds cannot be changed after they are configured so this would result in a permanent denial of service.

Proof of Concept
Chainlink's multisigs can immediately block access to price feeds at will. Therefore, to prevent denial of service scenarios, it is recommended to query Chainlink price feeds using a defensive approach with Solidity’s try/catch structure. In this way, if the call to the price feed fails, the caller contract is still in control and can handle any errors safely and explicitly.

```javascript
(, price,, updatedAt,) = source.latestRoundData();

```

Recommended Mitigation Steps
Surround the call to latestRoundData() with try/catch instead of calling it directly. In a scenario where the call reverts, the catch block can be used to call a fallback oracle or handle the error in any other suitable way.

***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L123


## [L-07] : check to ensure size of array is equal 

The `addConnector` function allows the addition of new connectors to a vault by specifying an array of connector addresses. However, there is currently no check to ensure that the arrays of connector addresses and their corresponding enabled status are of the same length. This oversight could lead to inconsistencies in the addition of connectors, potentially affecting the functionality and security of the vault.

```javascript
 function addConnector(uint256 vaultId, address[] calldata _connectorAddresses, bool[] calldata _enableds) are equial
        external
        onlyVaultMaintainer(vaultId)
        vaultExists(vaultId)
    {
        Vault storage vault = vaults[vaultId];
        for (uint256 i = 0; i < _connectorAddresses.length; i++) {
            vault.connectors[_connectorAddresses[i]].enabled = _enableds[i];
            emit ConnectorAdded(vaultId, _connectorAddresses[i]);
        }
    }
```

Proof of Concept (POC):
Suppose the _connectorAddresses array has a different length than the _enableds array. In that case, the function will execute without any errors, resulting in some connectors being added without their enabled status being correctly set. This inconsistency could lead to unexpected behavior or vulnerabilities in the system.

Recommendation:
To address this issue and ensure consistency in connector addition, it's essential to enforce a check to ensure that the arrays of connector addresses and their corresponding enabled status have the same length. 


## Non-Critical Findings

| Number        | issue           | Instances  |
| ------------- |:-------------:| -----:|
| [NC-01] | Activate the Optimizer | 1 |
| [NC-02] | Navigating new frontiers in transaction fairness    |   1 |
| [NC-03] | Avoid hardcoding values     |  1 |
| [NC-04] | Private function with embedded modifier reduces contract size      |  2 |
| [NC-05] | unchecked arithmetic in for loops     |  1 |





## [NC-01] : Activate the Optimizer

Before deploying your contract, activate the optimizer when compiling using “solc —optimize —bin sourceFile.sol”. By default, the optimizer will optimize the contract assuming it is called 200 times across its lifetime. If you want the initial contract deployment to be cheaper and the later function executions to be more expensive, set it to “ —optimize-runs=1”. Conversely, if you expect many transactions and do not care for higher deployment cost and output size, set “—optimize-runs” to a high number.

module.exports = {
solidity: {
version: "0.8.24",
settings: {
optimizer: {
  enabled: true,
  runs: 1000,
},
},
},
};
Please visit this site for further information:

https://docs.soliditylang.org/en/v0.5.4/using-the-compiler.html#using-the-commandline-compiler

Here’s one example of instance on opcode comparison that delineates the gas saving mechanism:

for !=0 before optimization
PUSH1 0x00
DUP2
EQ
ISZERO
PUSH1 [cont offset]
JUMPI
after optimization
DUP1
PUSH1 [revert offset]
JUMPI
Disclaimer: There have been several bugs with security implications related to optimizations. For this reason, Solidity compiler optimizations are disabled by default, and it is unclear how many contracts in the wild actually use them. Therefore, it is unclear how well they are being tested and exercised. High-severity security issues due to optimization bugs have occurred in the past.


## [NC-02] : Navigating new frontiers in transaction fairness

Navigating new frontiers in transaction fairness
As Layer 2, like Arbitrum or Base, considers moving towards a more decentralized sequencer model, the platform faces the challenge of maintaining its current mitigation of frontrunning risks inherent in a “first come, first served” system.

The transition could reintroduce vulnerabilities to transaction ordering manipulation, demanding innovative solutions to uphold transaction fairness. Strategies such as commit-reveal schemes, submarine sends, Fair Sequencing Services (FSS), decentralized MEV mitigation techniques, and the incorporation of time-locks and randomness could play pivotal roles. These measures aim to preserve the integrity of transaction sequencing, ensuring that the L2’s evolution towards decentralization enhances its ecosystem without compromising the security and fairness that are crucial for user trust and platform reliability.


## [NC-03] : Avoid hardcoding values 

bytes32 totalHash = keccak256(abi.encodePacked("\x19\x01", _domainSeparatorV4(), txInputHash));

***instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L102


## [NC-04] :  function with embedded modifier reduces contract size

Consider having the logic of a modifier embedded through a private function to reduce contract size if need be. A private visibility that is more efficient on function calls than the internal visibility is adopted because the modifier will only be making this call inside the contract.

***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L201

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L207


## [NC-05] : unchecked arithmetic in for loops 

using unchecked arithmetic in for loops is handled in solc compiler 0.8.22 onwards

***Instances***

https://github.com/code-423n4/2024-04-noya/blob/main/contracts/governance/Keepers.sol#L108

