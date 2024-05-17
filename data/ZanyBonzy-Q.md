## 1. Uniswap library contracts in use are not optimized for ^0.8.0 solidity usage

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L85

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/OracleLibrary.sol#L2

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/FullMath.sol#L2

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/TickMath.sol#L2

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/hardhat.config.ts#L11

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L141-L143

### Impact

The contracts are being compiled with [solidity version: "0.8.20",](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/hardhat.config.ts#L11), from the configs.
```typescript
const config: any = {
  solidity: {
    version: "0.8.20",
    settings: {
      optimizer: {
        enabled: true,
        runs: 10,
      },
    },
  },
```
The protocol rolls its own forks of uniswap [libraries](https://github.com/code-423n4/2024-04-noya/tree/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap), including [FullMath](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/FullMath.sol) and [TickMath](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/TickMath.sol)

Now, for a bit of context, UniswapV3 contracts and libraries are compiled with solidity <0.8.0. This is because overflow behaviour is desired during its interactions, and solidity version less than 0.8.0 do not revert upon overflow, hence the contracts are usually compiled with a solidity version from 0.4.0 to <0.8.0 depending on the contract. From [FullMath](https://github.com/Uniswap/v3-core/blob/d8b1c635c275d2a9450bd6a78f3fa2484fef73eb/contracts/libraries/FullMath.sol#L2) library for example

```solidity
pragma solidity >=0.4.0 <0.8.0;
```
Now, making comparisons with Noya's [Fullmath](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/FullMath.sol#L2) library, the pragma is left without an upperbound, meaning it can be compiled with solidity 0.8.20 as pointed out in the config file.

```solidity
pragma solidity >=0.4.0;
```
The same can be observed in [TickMath](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/external/libraries/uniswap/TickMath.sol#L2),

```solidity
pragma solidity >=0.4.0;
```
A brief comparison of the Noya's and Uniswap's.

https://www.diffchecker.com/gF846X3p/
https://www.diffchecker.com/IF56XCRj/
Apart from minor differences in styling and the solidity version, the contracts remain more or less the same. Note also the absence of any `unchecked`.  

This is being pointed out because these contracts are in use in the codebase including Oraclelibrary.sol, LiquidityAmounts.sol. These contracts are in use in [UniswapValueOracle.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/oracles/UniswapValueOracle.sol#L82-L86) and [UniV3Connector.sol](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/UNIv3Connector.sol#L141-L143). 

```solidity
        if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(int32(period)) != 0)) {
            timeWeightedAverageTick--;
        }
        _amountOut = OracleLibrary.getQuoteAtTick(timeWeightedAverageTick, amountIn128, tokenIn, baseToken);
    }
```

```solidity
            (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
                sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity
            );
```

The impact of this is that the desired overflow behaviour that Uniswap math desires will never be achieved as the current code will revert on overflows when it should not, breaking the contracts' functionalities.

PS: Not sure the best severity level that applies to this, since these libraries are not in scope although are in use by in-scope contracts, but the judge can set one that he deems best.

### Recommended Mitigation Steps
I'd recommend directly interacting with uniswap libraries instead, as a safe option. If however, the protocol desires to deploy their own forks, a better fork will be the [Univ3 0.8 versions](https://github.com/Uniswap/v3-core/tree/0.8/contracts/libraries) which can be safely deployed with solidity > 0.8. Conversely, the arithmetic operations can also be wrapped in an unchecked block.

## 2. Redundant check in `rescue` function for `ETH`

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691

### Impact
Rescue function holds a check for address(0) token, i.e ETH. But the contract holds no payable or receive function and has no way to receive ETH, making the check redundant.

```solidity
    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { //only emergency manager
        if (token == address(0)) {
            (bool success,) = payable(msg.sender).call{ value: amount }(""); 
            require(success, "Transfer failed.");
        } else {
            IERC20(token).safeTransfer(msg.sender, amount); 
        }
        emit Rescue(msg.sender, token, amount);
    }
```

### Recommended Mitigation Steps
Consider removing the check, or introducing receive() payable function

***

## 3. Introduce a check that token being withdrawn is not `baseToken`

Links to affected code *

https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L683-L691

### Impact

The rescue function should prevent the withdrawer being able to withdraw the baseToken as this can be used maliciously to drain the contract.

```solidity
    function rescue(address token, uint256 amount) public onlyEmergency nonReentrant { 
        if (token == address(0)) {
            (bool success,) = payable(msg.sender).call{ value: amount }(""); 
            require(success, "Transfer failed.");
        } else {
            IERC20(token).safeTransfer(msg.sender, amount); 
        }
        emit Rescue(msg.sender, token, amount);
    }
```