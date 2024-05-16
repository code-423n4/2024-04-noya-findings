
[Regitry.sol](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/Registry.sol)
```solidity
253      for (uint256 i = 0; i < usingTokens.length; i++) {
254             if (!isTokenTrusted(vaultId, usingTokens[i], 
255      calculatorConnector)) {
256                    revert TokenNotTrusted(usingTokens[i]);
257             }
258         }


```

Is the calldata checked？if not, then I want to pass the wrong calldata in some connector, so it's easy to bypass the ”if“ here.
In addition, it may be difficult for users to pass in the correct calldata, is there a suitable front-end script to help users choose?


[CamelotConnector](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/CamelotConnector.sol)

```solidity
99   function _getUnderlyingTokens(uint256 id, bytes memory data) public view 
100  override returns (address[] memory) {
101  (address tokenA, address tokenB) = abi.decode(data, (address,address));
102     address[] memory tokens = new address[](2);
103     tokens[0] = tokenA;
104     tokens[1] = tokenB;
105     return tokens;
106 }
```

For example, if there is no calldata detection, I can pass in calldata encoded by two identical token addresses, and eventually I will get an array of tokens composed of two identical addresses as the return value. If istrusted has false tokens at this time, I can pass in callData encoded by two identical token addresses. Then you can avoid being passed in, thus bypassing the ”if“ check





