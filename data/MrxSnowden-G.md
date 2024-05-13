https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/SwapHandler/GenericSwapAndBridgeHandler.sol#L90-L120

## Summarize
The executeSwap function in the provided Solidity code does not explicitly manage gas limits for external calls, specifically to the performSwapAction function of the ISwapAndBridgeImplementation interface. This omission could lead to potential issues if performSwapAction involves complex operations or interactions with other contracts, potentially causing the transaction to fail due to running out of gas.
## Recommended Mitigation Steps
Explicit Gas Limit Management: Modify the executeSwap function to include an explicit gas limit for the external call to performSwapAction , you can pass the gas limit as a parameter to the function call. This approach requires changes to both the executeSwap function and the performSwapAction function (or wherever it's defined) to accept and handle the gas limit parameter. 

function executeSwap(SwapRequest memory _swapRequest, uint256 gasLimit)
    external
    payable
    onlyEligibleUser
    onlyExistingRoute(_swapRequest.routeId)
    nonReentrant
    returns (uint256 _amountOut)
{
    if (_swapRequest.amount == 0) revert InvalidAmount();
    RouteData memory swapImplInfo = routes[_swapRequest.routeId];
    if (swapImplInfo.isBridge) revert RouteNotAllowedForThisAction();

    if (_swapRequest.checkForSlippage && _swapRequest.minAmount == 0) {
        // set minAmount so that slippage can be checked
        uint256 _slippageTolerance = slippageTolerance[_swapRequest.inputToken][_swapRequest.outputToken];
        if (_slippageTolerance == 0) {
            _slippageTolerance = genericSlippageTolerance;
        }
        INoyaValueOracle _priceOracle = INoyaValueOracle(valueOracle);
        uint256 _outputTokenValue =
            _priceOracle.getValue(_swapRequest.inputToken, _swapRequest.outputToken, _swapRequest.amount);

        _swapRequest.minAmount = (((1e6 - _slippageTolerance) * _outputTokenValue) / 1e6);
    }

    // Pass the gas limit to the performSwapAction function
    _amountOut = ISwapAndBridgeImplementation(swapImplInfo.route).performSwapAction{gasLimit}(msg.sender, _swapRequest);

    emit ExecutionCompleted(
        _swapRequest.routeId, _swapRequest.amount, _amountOut, _swapRequest.inputToken, _swapRequest.outputToken
    );
}

##

// Inside the ISwapAndBridgeImplementation interface or its implementation
function performSwapAction(address sender, SwapRequest memory swapRequest, uint256 gasLimit)
    external
    returns (uint256 _amountOut)
{
    // Implementation details...
    
    // Use the gasLimit parameter for the external call
    // Example: _externalCallFunction{gasLimit}(...);
    
    // Return the amount out
    return _amountOut;
}