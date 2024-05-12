Prisma connector is not updating the registry for the collateral token after adding liquidity when calling `addColl`.

```
function testInvaidUpdateRegistry_addColl() public {
    IStakeNTroveZap troveZap = IStakeNTroveZap(ULTRA_StakeNTroveZap);
    uint256 maxFee = 12_500_000_000_000_000;

    uint256 WETHamount = 100e18;
    _dealERC20(WETH, address(connector), WETHamount);

    bytes32 WETHpositionId = registry.calculatePositionId(address(accountingManager), 0, abi.encode(WETH));
    bytes memory WETHpositionData = abi.encode(address(connector));

    vm.startPrank(owner);

    connector.updateTokenInRegistry(WETH);

    assertEq(registry.getHoldingPositionIndex(vaultId, WETHpositionId, address(connector), WETHpositionData), 1);
    assertEq(IERC20(WETH).balanceOf(address(connector)), WETHamount);

    connector.approveZap(troveZap, ULTRA_weeth_troveManager, true);
    connector.openTrove(troveZap, ULTRA_weeth_troveManager, maxFee, WETHamount / 2, 2000e18);

    assertEq(registry.getHoldingPositionIndex(vaultId, WETHpositionId, address(connector), WETHpositionData), 1);
    assertEq(IERC20(WETH).balanceOf(address(connector)), WETHamount / 2);

    connector.addColl(troveZap, ULTRA_weeth_troveManager, WETHamount / 2);

    // WETH position still exists in the registry even though the connector WETH balance is 0
    assertEq(registry.getHoldingPositionIndex(vaultId, WETHpositionId, address(connector), WETHpositionData), 1);
    assertEq(IERC20(WETH).balanceOf(address(connector)), 0);
}
```
