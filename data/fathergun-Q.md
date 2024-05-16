```solidity
      for (uint256 i = 0; i < usingTokens.length; i++) {
                if (!isTokenTrusted(vaultId, usingTokens[i], calculatorConnector)) {
                    revert TokenNotTrusted(usingTokens[i]);
                }
            }


```

Is the calldata checked？if not, then I want to pass the wrong calldata in some connector, so it's easy to bypass the ”if“ here.
In addition, it may be difficult for users to pass in the correct calldata, is there a suitable front-end script to help users choose?




```solidity
function _getUnderlyingTokens(uint256 id, bytes memory data) public view override returns (address[] memory) {
        (address tokenA, address tokenB) = abi.decode(data, (address, address));
        address[] memory tokens = new address[](2);
        tokens[0] = tokenA;
        tokens[1] = tokenB;
        return tokens;
    }
```

For example, if there is no calldata detection, I can pass in calldata encoded by two identical token addresses, and eventually I will get an array of tokens composed of two identical addresses as the return value. If istrusted has false tokens at this time, I can pass in callData encoded by two identical token addresses. Then you can avoid being passed in, thus bypassing the ”if“ check





