## AddLiquidity need some require checks


* It was observed that Publisher is allowed to create a addLiquidity token with zero token . This can lead to user fund Transfer to address zero 



https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L178-L186


## Recommended Mitigation Steps

 check _balance value not equal to zero

    function addLiquidity(address[] memory tokens, uint256[] memory amounts, bytes memory data)
        require(balance != 0, "ZERO_BALANCE");
		...
    }

