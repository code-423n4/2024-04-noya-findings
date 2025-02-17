---
sponsor: "NOYA"
slug: "2024-04-noya"
date: "2025-02-17"
title: "NOYA"
findings: "https://github.com/code-423n4/2024-04-noya-findings/issues"
contest: 368
---

# Overview

## About C4

Code4rena (C4) is an open organization consisting of security researchers, auditors, developers, and individuals with domain expertise in smart contracts.

A C4 audit is an event in which community participants, referred to as Wardens, review, audit, or analyze smart contract logic in exchange for a bounty provided by sponsoring projects.

During the audit outlined in this document, C4 conducted an analysis of the NOYA smart contract system written in Solidity. The audit took place between April 26—May 17 2024.

## Wardens

173 Wardens contributed reports to NOYA:

  1. [BenRai](https://code4rena.com/@BenRai)
  2. [0xAlix2](https://code4rena.com/@0xAlix2) ([a\_kalout](https://code4rena.com/@a_kalout) and [ali\_shehab](https://code4rena.com/@ali_shehab))
  3. [alexxander](https://code4rena.com/@alexxander)
  4. [Sentryx](https://code4rena.com/@Sentryx) ([flacko](https://code4rena.com/@flacko) and [Buggsy](https://code4rena.com/@Buggsy))
  5. [KYP](https://code4rena.com/@KYP) ([givn](https://code4rena.com/@givn) and [yotov721](https://code4rena.com/@yotov721))
  6. [pkqs90](https://code4rena.com/@pkqs90)
  7. [grearlake](https://code4rena.com/@grearlake)
  8. [iamandreiski](https://code4rena.com/@iamandreiski)
  9. [SeveritySquad](https://code4rena.com/@SeveritySquad) ([shealtielanz](https://code4rena.com/@shealtielanz) and [0xdice91](https://code4rena.com/@0xdice91))
  10. [joaovwfreire](https://code4rena.com/@joaovwfreire)
  11. [KupiaSec](https://code4rena.com/@KupiaSec)
  12. [said](https://code4rena.com/@said)
  13. [rbserver](https://code4rena.com/@rbserver)
  14. [MrPotatoMagic](https://code4rena.com/@MrPotatoMagic)
  15. [VAD37](https://code4rena.com/@VAD37)
  16. [SpicyMeatball](https://code4rena.com/@SpicyMeatball)
  17. [Bauchibred](https://code4rena.com/@Bauchibred)
  18. [ArsenLupin](https://code4rena.com/@ArsenLupin)
  19. [ladboy233](https://code4rena.com/@ladboy233)
  20. [ZanyBonzy](https://code4rena.com/@ZanyBonzy)
  21. [WinSec](https://code4rena.com/@WinSec) ([ni8mare](https://code4rena.com/@ni8mare), [0xanmol](https://code4rena.com/@0xanmol), and [0xweb3boy](https://code4rena.com/@0xweb3boy))
  22. [AlexCzm](https://code4rena.com/@AlexCzm)
  23. [SBSecurity](https://code4rena.com/@SBSecurity) ([Slavcheww](https://code4rena.com/@Slavcheww) and [Blckhv](https://code4rena.com/@Blckhv))
  24. [Weed0607](https://code4rena.com/@Weed0607)
  25. [oakcobalt](https://code4rena.com/@oakcobalt)
  26. [bigtone](https://code4rena.com/@bigtone)
  27. [Tigerfrake](https://code4rena.com/@Tigerfrake)
  28. [d3e4](https://code4rena.com/@d3e4)
  29. [DPS](https://code4rena.com/@DPS) ([yvuchev](https://code4rena.com/@yvuchev) and [0xJaeger](https://code4rena.com/@0xJaeger))
  30. [MSaptarshi](https://code4rena.com/@MSaptarshi)
  31. [Rhaydden](https://code4rena.com/@Rhaydden)
  32. [Inspex](https://code4rena.com/@Inspex) ([DeStinE21](https://code4rena.com/@DeStinE21), [ErbaZZ](https://code4rena.com/@ErbaZZ), [Rugsurely](https://code4rena.com/@Rugsurely), [doggo](https://code4rena.com/@doggo), [jokopoppo](https://code4rena.com/@jokopoppo), [mimic\_f](https://code4rena.com/@mimic_f), and [rxnnxchxi](https://code4rena.com/@rxnnxchxi))
  33. [TPSec](https://code4rena.com/@TPSec) ([PetarTolev](https://code4rena.com/@PetarTolev) and [Pataroff](https://code4rena.com/@Pataroff))
  34. [forgebyola](https://code4rena.com/@forgebyola)
  35. [hihen](https://code4rena.com/@hihen)
  36. [atoko](https://code4rena.com/@atoko)
  37. [Jorgect](https://code4rena.com/@Jorgect)
  38. [den-sosnowsky](https://code4rena.com/@den-sosnowsky)
  39. [dimulski](https://code4rena.com/@dimulski)
  40. [Zac](https://code4rena.com/@Zac)
  41. [cu5t0mpeo](https://code4rena.com/@cu5t0mpeo)
  42. [Kaysoft](https://code4rena.com/@Kaysoft)
  43. [jolah1](https://code4rena.com/@jolah1)
  44. [Autosaida](https://code4rena.com/@Autosaida)
  45. [alexfilippov314](https://code4rena.com/@alexfilippov314)
  46. [n1punp](https://code4rena.com/@n1punp)
  47. [Bigsam](https://code4rena.com/@Bigsam)
  48. [josephdara](https://code4rena.com/@josephdara)
  49. [eta](https://code4rena.com/@eta)
  50. [shaflow2](https://code4rena.com/@shaflow2)
  51. [btk](https://code4rena.com/@btk)
  52. [0xJoyBoy03](https://code4rena.com/@0xJoyBoy03)
  53. [falconhoof](https://code4rena.com/@falconhoof)
  54. [JanuaryPersimmon2024](https://code4rena.com/@JanuaryPersimmon2024)
  55. [ak1](https://code4rena.com/@ak1)
  56. [recursiveEth](https://code4rena.com/@recursiveEth)
  57. [Cryptor](https://code4rena.com/@Cryptor)
  58. [0xbeWater0given](https://code4rena.com/@0xbeWater0given)
  59. [cheatc0d3](https://code4rena.com/@cheatc0d3)
  60. [0xrex](https://code4rena.com/@0xrex)
  61. [bareli](https://code4rena.com/@bareli)
  62. [0xmystery](https://code4rena.com/@0xmystery)
  63. [Daniel526](https://code4rena.com/@Daniel526)
  64. [wangxx2026](https://code4rena.com/@wangxx2026)
  65. [shikhar229169](https://code4rena.com/@shikhar229169)
  66. [Centaur](https://code4rena.com/@Centaur) ([mazi\_xyz](https://code4rena.com/@mazi_xyz), [Mylifechangefast\_eth](https://code4rena.com/@Mylifechangefast_eth), [Aristos](https://code4rena.com/@Aristos), and [TheWeb3Mechanic](https://code4rena.com/@TheWeb3Mechanic))
  67. [Audinarey](https://code4rena.com/@Audinarey)
  68. [Evo](https://code4rena.com/@Evo)
  69. [0xDemon](https://code4rena.com/@0xDemon)
  70. [mrMorningstar](https://code4rena.com/@mrMorningstar)
  71. [Giorgio](https://code4rena.com/@Giorgio)
  72. [Aymen0909](https://code4rena.com/@Aymen0909)
  73. [ironsidesec](https://code4rena.com/@ironsidesec)
  74. [0xbepresent](https://code4rena.com/@0xbepresent)
  75. [JC](https://code4rena.com/@JC)
  76. [peanuts](https://code4rena.com/@peanuts)
  77. [d\_tony7470](https://code4rena.com/@d_tony7470)
  78. [0xblackskull](https://code4rena.com/@0xblackskull)
  79. [dimah7](https://code4rena.com/@dimah7)
  80. [rekxor](https://code4rena.com/@rekxor)
  81. [codeslide](https://code4rena.com/@codeslide)
  82. [FastChecker](https://code4rena.com/@FastChecker)
  83. [Stormreckson](https://code4rena.com/@Stormreckson)
  84. [0x486776](https://code4rena.com/@0x486776)
  85. [igbinosuneric](https://code4rena.com/@igbinosuneric)
  86. [tofunmi](https://code4rena.com/@tofunmi)
  87. [slvDev](https://code4rena.com/@slvDev)
  88. [Brenzee](https://code4rena.com/@Brenzee)
  89. [twcctop](https://code4rena.com/@twcctop)
  90. [Sparrow](https://code4rena.com/@Sparrow)
  91. [djanerch](https://code4rena.com/@djanerch)
  92. [mrjorystewartbaxter](https://code4rena.com/@mrjorystewartbaxter)
  93. [0xSecuri](https://code4rena.com/@0xSecuri)
  94. [DemoreX](https://code4rena.com/@DemoreX)
  95. [xg](https://code4rena.com/@xg)
  96. [Stefanov](https://code4rena.com/@Stefanov)
  97. [PENGUN](https://code4rena.com/@PENGUN)
  98. [Dup1337](https://code4rena.com/@Dup1337) ([sorrynotsorry](https://code4rena.com/@sorrynotsorry) and [deliriusz](https://code4rena.com/@deliriusz))
  99. [DanielArmstrong](https://code4rena.com/@DanielArmstrong)
  100. [valy001](https://code4rena.com/@valy001)
  101. [honey-k12](https://code4rena.com/@honey-k12)
  102. [pavankv](https://code4rena.com/@pavankv)
  103. [joicygiore](https://code4rena.com/@joicygiore)
  104. [John\_Femi](https://code4rena.com/@John_Femi)
  105. [petro\_1912](https://code4rena.com/@petro_1912)
  106. [Topmark](https://code4rena.com/@Topmark)
  107. [robertodf99](https://code4rena.com/@robertodf99)
  108. [0xmuxyz](https://code4rena.com/@0xmuxyz)
  109. [aariiif](https://code4rena.com/@aariiif)
  110. [fandonov](https://code4rena.com/@fandonov)
  111. [Pelz](https://code4rena.com/@Pelz)
  112. [bctester](https://code4rena.com/@bctester)
  113. [Hueber](https://code4rena.com/@Hueber)
  114. [LinKenji](https://code4rena.com/@LinKenji)
  115. [Draiakoo](https://code4rena.com/@Draiakoo)
  116. [codeislight](https://code4rena.com/@codeislight)
  117. [seeques](https://code4rena.com/@seeques)
  118. [biakia](https://code4rena.com/@biakia)
  119. [Vancelot](https://code4rena.com/@Vancelot)
  120. [0rpse](https://code4rena.com/@0rpse)
  121. [novamanbg](https://code4rena.com/@novamanbg)
  122. [steadyman](https://code4rena.com/@steadyman)
  123. [itsabinashb](https://code4rena.com/@itsabinashb)
  124. [Sancybars](https://code4rena.com/@Sancybars)
  125. [tchkvsky](https://code4rena.com/@tchkvsky)
  126. [HChang26](https://code4rena.com/@HChang26)
  127. [lightoasis](https://code4rena.com/@lightoasis)
  128. [cholakov](https://code4rena.com/@cholakov)
  129. [poslednaya](https://code4rena.com/@poslednaya)
  130. [Ocean\_Sky](https://code4rena.com/@Ocean_Sky)
  131. [havewemeetbefore](https://code4rena.com/@havewemeetbefore)
  132. [ZdravkoHr](https://code4rena.com/@ZdravkoHr)
  133. [ChaseTheLight](https://code4rena.com/@ChaseTheLight)
  134. [web3km](https://code4rena.com/@web3km)
  135. [MrCrowNFT](https://code4rena.com/@MrCrowNFT)
  136. [youleeyan](https://code4rena.com/@youleeyan)
  137. [unix515](https://code4rena.com/@unix515)
  138. [nnez](https://code4rena.com/@nnez)
  139. [kk](https://code4rena.com/@kk)
  140. [sh1v](https://code4rena.com/@sh1v)
  141. [eldenelder](https://code4rena.com/@eldenelder)
  142. [korok](https://code4rena.com/@korok)
  143. [Nikki](https://code4rena.com/@Nikki)
  144. [AvantGard](https://code4rena.com/@AvantGard)
  145. [gavfu](https://code4rena.com/@gavfu)
  146. [0xch](https://code4rena.com/@0xch)
  147. [Velislav4o](https://code4rena.com/@Velislav4o)
  148. [4rdiii](https://code4rena.com/@4rdiii)
  149. [0xBugSlayer](https://code4rena.com/@0xBugSlayer)
  150. [0xMosh](https://code4rena.com/@0xMosh)
  151. [lanrebayode77](https://code4rena.com/@lanrebayode77)
  152. [heedfxn](https://code4rena.com/@heedfxn)
  153. [BiasedMerc](https://code4rena.com/@BiasedMerc)
  154. [Ali-\_-Y](https://code4rena.com/@Ali-_-Y)

This audit was judged by [gzeon](https://code4rena.com/@gzeon).

Final report assembled by [liveactionllama](https://twitter.com/liveactionllama).

# Summary

The C4 analysis yielded an aggregated total of 86 unique vulnerabilities. Of these vulnerabilities, 23 received a risk rating in the category of HIGH severity and 63 received a risk rating in the category of MEDIUM severity.

Additionally, C4 analysis included 23 reports detailing issues with a risk rating of LOW severity or non-critical.

All of the issues presented here are linked back to their original finding.

# Scope

The code under review can be found within the [C4 NOYA repository](https://github.com/code-423n4/2024-04-noya), and is composed of 41 smart contracts written in the Solidity programming language and includes 3,999 lines of Solidity code.

# Severity Criteria

C4 assesses the severity of disclosed vulnerabilities based on three primary risk categories: high, medium, and low/non-critical.

High-level considerations for vulnerabilities span the following key areas when conducting assessments:

- Malicious Input Handling
- Escalation of privileges
- Arithmetic
- Gas use

For more information regarding the severity criteria referenced throughout the submission review process, please refer to the documentation provided on [the C4 website](https://code4rena.com), specifically our section on [Severity Categorization](https://docs.code4rena.com/awarding/judging-criteria/severity-categorization).

# High Risk Findings (23)

***Note: full discussions can be accessed by viewing each linked submission.***

## [[H-01] Value of asset token can be incorrect when usage of ETH/USD Chainlink oracle is needed](https://github.com/code-423n4/2024-04-noya-findings/issues/1509)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-noya-findings/issues/1509), also found by [SpicyMeatball](https://github.com/code-423n4/2024-04-noya-findings/issues/511)*

### Impact

There are tokens that have token/ETH but no token/USD Chainlink oracles currently in which these tokens have the in scope token behaviors described in <https://code4rena.com/audits/2024-04-noya> and should be supported by this protocol. To support these tokens, the ETH/USD Chainlink oracle can be used as a part of the route set by the following `NoyaValueOracle.updatePriceRoute` function for converting the token amount to ETH first and then converting the converted ETH amount to USD.

<https://github.com/code-423n4/2024-04-noya/blob/cc3854f634a72bd4a8b597021887088ca2d6d29f/contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L64>

```solidity
    function updatePriceRoute(address asset, address base, address[] calldata s) external onlyMaintainer {
        priceRoutes[asset][base] = s;
        emit UpdatedPriceRoute(asset, base, s);
    }
```

When converting the value of such token in ETH to USD, the following `ChainlinkOracleConnector.getValue` function would return `getValueFromChainlinkFeed(AggregatorV3Interface(primarySource), amount, getTokenDecimals(decimalsSource), isPrimaryInverse)`; because `amountIn` is in ETH's decimals that is 18 and `uintprice` and `sourceTokenUnit` are in USD's decimals that is 8 in the `getValueFromChainlinkFeed` function below, the value returned by the `ChainlinkOracleConnector.getValue` function is in ETH's decimals. Hence, when converting such token amount to ETH first and then to USD, the value of the corresponding token amount is in ETH's decimals instead of USD's decimals. In comparison, if the token/USD oracle could exist and be used for such token, the value of such token returned by `ChainlinkOracleConnector.getValue` function would be in USD's decimals instead of ETH's decimals. Thus, the value of such token is much higher when using the token/ETH and ETH/USD oracles indirectly comparing to using the token/USD oracle directly given if such token/USD oracle can become existent in the future. If such token/USD oracle does become existent and be used in the `ChainlinkOracleConnector` contract in the future, the value of such token amount calculated previously using the token/ETH and ETH/USD oracles indirectly would be incorrectly much higher than the value of the same token amount newly calculated using the token/USD oracle directly.

<https://github.com/code-423n4/2024-04-noya/blob/cc3854f634a72bd4a8b597021887088ca2d6d29f/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L89-L103>

```solidity
    function getValue(address asset, address baseToken, uint256 amount) public view returns (uint256) {
        if (asset == baseToken) {
            return amount;
        }

        (address primarySource, bool isPrimaryInverse) = getSourceOfAsset(asset, baseToken);
        if (primarySource == address(0)) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(asset, baseToken, primarySource);
        }
        address decimalsSource = isPrimaryInverse ? baseToken : asset;
        decimalsSource = decimalsSource == ETH || decimalsSource == USD ? primarySource : decimalsSource;
        return getValueFromChainlinkFeed(
            AggregatorV3Interface(primarySource), amount, getTokenDecimals(decimalsSource), isPrimaryInverse
        );
    }
```

<https://github.com/code-423n4/2024-04-noya/blob/cc3854f634a72bd4a8b597021887088ca2d6d29f/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L138-L141>

```solidity
    function getTokenDecimals(address token) public view returns (uint256) {
        uint256 decimals = IERC20Metadata(token).decimals();
        return 10 ** decimals;
    }
```

<https://github.com/code-423n4/2024-04-noya/blob/cc3854f634a72bd4a8b597021887088ca2d6d29f/contracts/helpers/valueOracle/oracles/ChainlinkOracleConnector.sol#L115-L135>

```solidity
    function getValueFromChainlinkFeed(
        AggregatorV3Interface source,
        uint256 amountIn,
        uint256 sourceTokenUnit,
        bool isInverse
    ) public view returns (uint256) {
        int256 price;
        uint256 updatedAt;
        (, price,, updatedAt,) = source.latestRoundData();
        uint256 uintprice = uint256(price);
        if (block.timestamp - updatedAt > chainlinkPriceAgeThreshold) {
            revert NoyaChainlinkOracle_DATA_OUT_OF_DATE();
        }
        if (price <= 0) {
            revert NoyaChainlinkOracle_PRICE_ORACLE_UNAVAILABLE(address(source), address(0), address(0));
        }
        if (isInverse) {
            return (amountIn * sourceTokenUnit) / uintprice;
        }
        return (amountIn * uintprice) / (sourceTokenUnit);
    }
```

### Proof of Concept

Please add the following test in `testFoundry\testOracle.sol`. This test will pass to demonstrate the described scenario.

```solidity
    function test_assetTokenValueIsIncorrectWhenETHUSDChainlinkOracleIsNeeded() public {
        // Some tokens do not have token/USD oracle so token/ETH and ETH/USD oracles need to be used.
        // Following code compares method using token/ETH and ETH/USD oracles indirectly to method using token/USD oracle directly.

        address ETH_USD_FEED = 0x5f4eC3Df9cbd43714FE2740f5E3616155c5b8419;

        vm.startPrank(owner);

        addTokenToChainlinkOracle(address(USDC), address(840), address(USDC_USD_FEED));
        addTokenToChainlinkOracle(address(USDC), address(0), address(USDC_ETH_FEED));
        addTokenToChainlinkOracle(address(0), address(840), address(ETH_USD_FEED));

        addTokenToNoyaOracle(address(USDC), address(chainlinkOracle));
        addTokenToNoyaOracle(address(0), address(chainlinkOracle));
        addTokenToNoyaOracle(address(840), address(chainlinkOracle));

        uint256 valueDirect = noyaOracle.getValue(address(USDC), address(840), 1e6);

        // when using USDC/USD oracle directly, 1e6 wei USDC is equivalent to 99998495 wei USD, which is in USD's decimals that is 8
        assertEq(valueDirect, 99998495);

        address[] memory assets = new address[](1);
        assets[0] = address(0);
        noyaOracle.updatePriceRoute(address(USDC), address(840), assets);

        uint256 valueIndirect = noyaOracle.getValue(address(USDC), address(840), 1e6);

        // when using USDC/ETH and ETH/USD oracles indirectly, 1e6 wei USDC is equivalent to 998152930103816659 wei USD, which is in ETH's decimals that is 18
        assertEq(valueIndirect, 998152930103816659);

        // value of 1e6 wei USDC is incorrectly much higher when using USDC/ETH and ETH/USD oracles indirectly comparing to using USDC/USD oracle directly
        assertEq(valueIndirect / valueDirect, 9981679525);

        vm.stopPrank();
    }
```

### Recommended Mitigation Steps

`getValueFromChainlinkFeed(AggregatorV3Interface(primarySource), amount, getTokenDecimals(decimalsSource), isPrimaryInverse)` returned by the `ChainlinkOracleConnector.getValue` function can be further divided by `10 ** 10` when `asset` is ETH, `baseToken` is USD, and `isPrimaryInverse` is false. This makes such return value be in USD's decimals that is 8.

**[gzeon (judge) increased severity to High and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1509#issuecomment-2189853100):**
 > I think I see the problem, when decimalsSource is ETH/USD it treats the decimal as source.decimal() because they are not real ERC20. It is usually fine because ETH oracles are 18 decimals and USD oracles are 8 decimals which is same as the expected value. However, when ETH/USD oracle is used the logic would always consider it as 8 decimal (because ETH/USD oracle as 8 decimal) but in fact it should be treated as 18 decimal if we want the ETH decimal, hence the result is off by 10 decimals.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1509#event-13323232610)**


***

## [[H-02] Base tokens like USDT, USDC having different decimals on different chains can have their TVL updated incorrectly](https://github.com/code-423n4/2024-04-noya-findings/issues/1438)
*Submitted by [MrPotatoMagic](https://github.com/code-423n4/2024-04-noya-findings/issues/1438), also found by [KupiaSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1358) and [Weed0607](https://github.com/code-423n4/2024-04-noya-findings/issues/1294)*

### Impact

Tokens like [USDT, USDC](https://bscscan.com/address/0x8ac76a51cc950d9822d68b83fe1ad97b32cd580d#readProxyContract#F3) on the BSC chain have 18 decimals while the "Base" blockchain which is being used as the root/base chain uses 6 decimals (see [here](https://basescan.org/token/0x833589fcd6edb6e08f4c7c32d4f71b54bda02913#readProxyContract)).

The issue is that when the TVL is updated on the base chain by sending a cross-chain message call from OmnichainManagerNormalChain.sol contract to OmnichainManagerBaseChain.sol contract, the TVL is recorded in the holding position with 18 decimals instead of scaling it down to 6 decimals.

Due to this, whenever the accounting manager retrieves the [TVL()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L627C1-L630C6) through function [totalAssets()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L592) (overriden from ERC4626), the TVLHelper contract would loop through all holding positions and sum them up in order to be used in vault operations like minting shares etc. This would be problematic since the tvl is 1e12 decimals more than the actual of 1e6. This breaks the accounting in the accounting manager contract.

### Proof of Concept

Here's the whole process:

1.  Manager calls function [updateTVLInfo()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerNormalChain.sol#L28) on the OmnichainManagerNormalChain.sol contract on the BSC chain.

*   On Line 29, it calls the getTVL() function that loops through all the holding positions for the base token and vaultId.
*   The value is returned (in 18 decimals since we're on BSC) and stored in `tvl` on Line 29.

Line 30 calls the updateTVL() function on the lzhelper contract, which sends the cross-chain message with the tvl update.

```solidity
File: OmnichainManagerNormalChain.sol
19:     function getTVL() public view returns (uint256) {
20:         (, address baseToken) = registry.getVaultAddresses(vaultId);
21:         return TVLHelper.getTVL(vaultId, registry, baseToken);
22:     }
23:     /**
24:      * Triggers an update of the vault's TVL information, sending the latest data to the base chain via the LZHelperSender contract.
25:      * This function is restricted to be called by managers only, ensuring that TVL updates are controlled and authorized.
26:      */
27: 
28:     function updateTVLInfo() external onlyManager {
29:         uint256 tvl = getTVL();
30:         LZHelperSender(lzHelper).updateTVL(vaultId, tvl, block.timestamp);
31:     }
```

2.  The call arrives on the base chain by LZ calling the [\_lzReceive()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/LZHelpers/LZHelperReceiver.sol#L65) function, which calls the [updateTVL()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/OmniChainHandler/OmnichainManagerBaseChain.sol#L32) function on the OmnichainManagerBaseChain.sol contract.

*   On Line 39, the `tvl` variable is stored as is with the 18 decimals incorrectly.

```solidity
File: OmnichainManagerBaseChain.sol
32:     function updateTVL(uint256 chainId, uint256 tvl, uint256 updateTime) external nonReentrant {
33:         if (msg.sender != lzHelper) revert IConnector_InvalidSender();
34:         
35:         registry.updateHoldingPostionWithTime(
36:             vaultId,
37:             registry.calculatePositionId(address(this), OMNICHAIN_POSITION_ID, abi.encode(chainId)),
38:             "",
39:             abi.encode(tvl),
40:             tvl <= DUST_LEVEL,
41:             updateTime
42:         );
43:     }
```

3.  Now when the [totalAssets()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L591) function in the accounting manager calls the [TVL()](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/accountingManager/AccountingManager.sol#L627) function, it loops through the holding positions in the TVLHelper contract and sums up the TVL incorrectly.

```solidity
    function getTVL(uint256 vaultId, PositionRegistry registry, address baseToken) public view returns (uint256) {
        uint256 totalTVL;
        uint256 totalDebt;
        HoldingPI[] memory positions = registry.getHoldingPositions(vaultId);
        for (uint256 i = 0; i < positions.length; i++) {
            if (positions[i].calculatorConnector == address(0)) {
                continue;
            }
            uint256 tvl = IConnector(positions[i].calculatorConnector).getPositionTVL(positions[i], baseToken);
            bool isPositionDebt = registry.isPositionDebt(vaultId, positions[i].positionId);
            if (isPositionDebt) {
                totalDebt += tvl;
            } else {
                totalTVL += tvl;
            }
        }
        if (totalTVL < totalDebt) {
            return 0;
        }
        return (totalTVL - totalDebt);
    }
```

Through this we observe how incorrect tvl is reported from the normal chain to the base chain, which hugely affects the value retrieved by function totalAssets() for ERC4626 vault operations.

### Recommended Mitigation Steps

Keep track of the decimals of tokens on other chains in a mapping. If they are more or less, consider scaling them once the tvl update is received on the base chain.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1438#event-12904795203):**
> Fix in commit 58537ef76afa048745f85a31cb7a0aa3eb6b300b.


***

## [[H-03] `NoyaValueOracle.getValue` returns an incorrect price when a multi-token route is used](https://github.com/code-423n4/2024-04-noya-findings/issues/1430)
*Submitted by [TPSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1430) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1430+is%3Aclosed) submitted by other wardens)*

The [NoyaValueOracle.getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L79) is used to convert the price of an `asset` to `baseToken`, using token routing when necessary.

If there is no oracle for two tokens, a route needs to be set up between them. This route can then be used to get a value using [NoyaValueOracle.getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L79).

However, there's a mistake in the [NoyaValueOracle.getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L79) function that makes it give the wrong price.

### Impact

The [NoyaValueOracle.getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L71-L79) will return incorrect prices for tokens when the configured [priceRoutes\[asset\]\[baseToken\].length](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/helpers/valueOracle/NoyaValueOracle.sol#L76C36-L76C65) is more than 1.

### Proof of Concept

To set a price path for a token pair, the maintainer should use [NoyaValueOracle.updatePriceRoute](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L61-L64).

For instance, for the `SOL` to `UNI` conversion. 1 `SOL` is roughly equal to 21 `UNI`, but there's no direct oracle. So, the maintainer sets a route `SOL` → `BNB` → `ETH` → `UNI`.

When [\_getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L93) tries to convert 100 `SOL` into `UNI`, it should first convert `SOL` → `BNB`, then `BNB` → `ETH`, and lastly `ETH` → `UNI`. But, what [\_getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L93) really does is to convert `SOL` → `BNB`, `SOL` → `ETH`, and `SOL` → `UNI`.

You can see this error in the [\_getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L89) function, where `asset` is used each time instead of `quotingToken`.

```diff
    function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
        internal
        view
        returns (uint256 value)
    {
        uint256 initialValue = amount;
        address quotingToken = asset;
        for (uint256 i = 0; i < sources.length; i++) {
>           initialValue = _getValue(asset, sources[i], initialValue);
            quotingToken = sources[i];
        }
        return _getValue(quotingToken, baseToken, initialValue);
    }
```

The first problem comes up if the `SOL` → `BNB`, `SOL` → `ETH`, and `SOL` → `UNI` oracles are not set up. This will cause a revert of [\_getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L95-L110).

```diff
    function _getValue(address quotingToken, address baseToken, uint256 amount) internal view returns (uint256) {
        INoyaValueOracle oracle = priceSource[quotingToken][baseToken];
        if (address(oracle) == address(0)) {
            oracle = priceSource[baseToken][quotingToken];
        }
        if (address(oracle) == address(0)) {
            oracle = defaultPriceSource[baseToken];
        }
        if (address(oracle) == address(0)) {
            oracle = defaultPriceSource[quotingToken];
        }
        if (address(oracle) == address(0)) {
>           revert NoyaOracle_PriceOracleUnavailable(quotingToken, baseToken);
        }
        return oracle.getValue(quotingToken, baseToken, amount);
    }
```

Even if we configure these oracles, the calculated value will still be incorrect.

Consider this example - the [\_getValue](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/valueOracle/NoyaValueOracle.sol#L81-L93) is called with the following parameters:

*   asset = SOL
*   baseToken = UNI
*   amount = 100
*   sources = \[BNB, ETH]

This will convert 100 `SOL` to `UNI`, using `BNB` and `ETH` as the route.

| Iteration | initialValue | quotingToken | asset | sources[i] | initialValue’   | quotingToken’ |
| --------- | ------------ | ------------ | ----- | ---------- | --------------- | ------------- |
| 1         | 100          | SOL          | SOL   | BNB        | 100SOL ≈ 25BNB  | BNB           |
| 2         | 25           | BNB          | SOL   | ETH        | 25BNB ≈ 1.25ETH | ETH           |

The result is calculated using `quotingToken` = ETH, `baseToken` = UNI, and the `initialValue` = 1.25, which returns 526.

However, the expected result should be 2094.

### Recommended Mitigation Steps

Replace `asset` with `quotingToken:`

```diff
    function _getValue(address asset, address baseToken, uint256 amount, address[] memory sources)
        internal
        view
        returns (uint256 value)
    {
        uint256 initialValue = amount;
        address quotingToken = asset;
        for (uint256 i = 0; i < sources.length; i++) {
-           initialValue = _getValue(asset, sources[i], initialValue);
+           initialValue = _getValue(quotingToken, sources[i], initialValue);
            quotingToken = sources[i];
        }
        return _getValue(quotingToken, baseToken, initialValue);
    }
```

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1430#event-12904802551):**
> Fix in commit 66d4104e83cc1b68ab117c78c4a92eafac86341c.


***

## [[H-04] `executeWithdraw` may be blocked if any of the users are blacklisted from the `baseToken`](https://github.com/code-423n4/2024-04-noya-findings/issues/1426)
*Submitted by [TPSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1426) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1426+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

<https://github.com/d-xo/weird-erc20#tokens-with-blocklists>

> Some tokens (e.g. `USDC`, `USDT`) have a contract level admin controlled address blocklist. If an address is blocked, then transfers to and from that address are forbidden.

> Malicious or compromised token owners can trap funds in a contract by adding the contract address to the blocklist. This could potentially be the result of regulatory action against the contract itself, against a single user of the contract (e.g. a Uniswap LP), or could also be a part of an extortion attempt against users of the blocked contract.

If a user whose address has been blocklisted is added to a `withdrawQueue` inside the `AccountingManager` contract, all other users that are in that same queue will not be able to withdraw, as the `executeWithdraw` function will revert when it tries to do [`baseToken.safeTransfer`](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L428) call on the blocklisted address.

### Impact

A user who has been blocklisted can be added to a `withdrawQueue` to DoS the call of the `executeWithdraw` function, effectively preventing all other user that are in that same queue from withdrawing, locking their assets inside the protocol.

### Proof of Concept

When `baseToken` has blocklisting functionality, and any user in the withdrawal queue is in the blocklist, it prevents all other users from making withdrawals.

*Place the following test in [testFoundry/BlacklistableTokenPOC.t.sol](https://github.com/code-423n4/2024-04-noya/tree/9c79b332eff82011dcfa1e8fd51bad805159d758/testFoundry) and run it with the command `forge test --mt testBlacklistableERC20`*

<details>

```solidity
// SPDX-License-Identifier: Apache-2.0
pragma solidity 0.8.20;

import "@openzeppelin/contracts-5.0/token/ERC20/utils/SafeERC20.sol";
import "@openzeppelin/contracts-5.0/token/ERC20/IERC20.sol";
import "@openzeppelin/contracts-5.0/token/ERC20/ERC20.sol";
import "./utils/testStarter.sol";
import "./utils/resources/OptimismAddresses.sol";
import { AaveConnector, BaseConnectorCP } from "contracts/connectors/AaveConnector.sol";

contract BlacklistERC20 is ERC20 {
    mapping(address => bool) private blacklisted;

    error AccountBlacklisted();

    constructor() ERC20("Blacklist ERC20", "BLT") {
        _mint(msg.sender, 100e18);
    }

    function addToBlacklist(address account) public  {
        blacklisted[account] = true;
    }

    function isBlacklisted(address account) public view returns (bool) {
        return blacklisted[account];
    }

    function _update(
        address from,
        address to,
        uint256 value
    ) internal override {
        if (isBlacklisted(from) || isBlacklisted(to)) revert AccountBlacklisted();
        super._update(from, to, value);
    }
}

contract BlacklistableTokenPOC is testStarter, OptimismAddresses  {
   using SafeERC20 for IERC20;

    AaveConnector connector;

    address charlie = makeAddr("charlie");

    address public constant USD = address(840);

    BlacklistERC20 token;

    function setUp() public {
        vm.label(alice, "alice");
        vm.label(bob, "bob");
        vm.label(charlie, "charlie");

        vm.startPrank(owner);
        token = new BlacklistERC20();

        deployEverythingNormal(address(token));

        connector = new AaveConnector(aavePool, USD, BaseConnectorCP(registry, 0, swapHandler, noyaOracle));
        addConnectorToRegistry(vaultId, address(connector));
        addTrustedTokens(vaultId, address(accountingManager), address(token));

        registry.addTrustedPosition(vaultId, connector.AAVE_POSITION_ID(), address(connector), true, false, "", "");
        registry.addTrustedPosition(vaultId, 0, address(accountingManager), false, false, abi.encode(address(token)), "");

        vm.stopPrank();
    }

    function testBlacklistableERC20() public {
        uint depositAmount = 10e18;

        // give tokens to the users
        vm.startPrank(owner);
        token.transfer(alice, depositAmount);
        token.transfer(bob, depositAmount);
        token.transfer(charlie, depositAmount);
        vm.stopPrank();

        // user's deposits
        vm.startPrank(alice);
        SafeERC20.forceApprove(IERC20(token), address(accountingManager), depositAmount);
        accountingManager.deposit(address(alice), depositAmount, address(0));
        vm.stopPrank();

        vm.startPrank(bob);
        SafeERC20.forceApprove(IERC20(token), address(accountingManager), depositAmount);
        accountingManager.deposit(address(bob), depositAmount, address(0));
        vm.stopPrank();

        vm.startPrank(charlie);
        SafeERC20.forceApprove(IERC20(token), address(accountingManager), depositAmount);
        accountingManager.deposit(address(charlie), depositAmount, address(0));
        vm.stopPrank();

        // manager execute deposits
        vm.startPrank(owner);
        accountingManager.calculateDepositShares(10);
        skip(accountingManager.depositWaitingTime());
        accountingManager.executeDeposit(10, address(connector), "");
        vm.stopPrank();

        // withdraw requests
        vm.startPrank(alice);
        accountingManager.withdraw(accountingManager.maxRedeem(alice), address(alice));
        vm.stopPrank();

        vm.startPrank(bob);
        accountingManager.withdraw(accountingManager.maxRedeem(bob), address(bob));
        vm.stopPrank();

        vm.startPrank(charlie);
        accountingManager.withdraw(accountingManager.maxRedeem(charlie), address(charlie));
        vm.stopPrank();

        // execute withdraw
        vm.startPrank(owner);
        accountingManager.calculateWithdrawShares(10);
        accountingManager.startCurrentWithdrawGroup();
        uint neededAssetsForWithdraw = accountingManager.neededAssetsForWithdraw();
        RetrieveData[] memory retrieveData = new RetrieveData[](1);
        retrieveData[0] = RetrieveData(
            neededAssetsForWithdraw,
            address(connector),
            abi.encode(neededAssetsForWithdraw, ""));
        accountingManager.retrieveTokensForWithdraw(retrieveData);
        skip(accountingManager.withdrawWaitingTime());
        accountingManager.fulfillCurrentWithdrawGroup();

        // @audit When one of the users is blacklisted from the baseToken, no one else can withdraw either
        token.addToBlacklist(alice);

        vm.expectRevert();
        accountingManager.executeWithdraw(10);
    }
}
```

</details>

### Recommended Mitigation Steps

Validate that the receiver is not blacklisted before making the `ERC20::safeTransfer` call, whenever the `baseToken` has a contract level admin controlled address blocklist (e.g. `USDC`, `USDT`).

```diff
function executeWithdraw(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
			...
        while (
            currentWithdrawGroup.lastId > firstTemp
                && withdrawQueue.queue[firstTemp].calculationTime + withdrawWaitingTime <= block.timestamp // @audit-info use withdrawRequest time
                && i < maxIterations
        ) {
            i += 1;
            WithdrawRequest memory data = withdrawQueue.queue[firstTemp];
            uint256 shares = data.shares;
            // calculate the base token amount that the user will receive based on the total available amount
            uint256 baseTokenAmount =
                data.amount * currentWithdrawGroup.totalABAmount / currentWithdrawGroup.totalCBAmountFullfilled;

            withdrawRequestsByAddress[data.owner] -= shares;

            _burn(data.owner, shares);

            processedBaseTokenAmount += data.amount;
            {
                uint256 feeAmount = baseTokenAmount * withdrawFee / FEE_PRECISION;
                withdrawFeeAmount += feeAmount;
                baseTokenAmount = baseTokenAmount - feeAmount;
            }

+           if (baseToken.isBlacklisted(data.receiver)) {
+	        continue;
+	    }

            baseToken.safeTransfer(data.receiver, baseTokenAmount);

            emit ExecuteWithdraw(
                firstTemp, data.owner, data.receiver, shares, data.amount, baseTokenAmount, block.timestamp
            );

            delete withdrawQueue.queue[firstTemp];
            firstTemp += 1;
        }
			...
    }
```

**[gzeon (judge) increased severity to High and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1426#issuecomment-2143851561):**
 > High risk because the DOS can cause other funds to be stuck. There are multiple ways to trigger the problem:
> 
> 1. Transfer to address(0)
> 2. Transfer of 0 amount
> 3. Blacklisted receiver
> 
> I consider these all to share the same root cause of the deposit and withdrawal queue being blocking.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1426#event-12904835039):**
 > Fix in commit c9e03316c7f30f5aebe88627fc296763f6105c31.


***

## [[H-05] Loss of funds in `PendleConnector.depositIntoMarket()`](https://github.com/code-423n4/2024-04-noya-findings/issues/1363)
*Submitted by [alexxander](https://github.com/code-423n4/2024-04-noya-findings/issues/1363)*

### Impact

`PendleConnector` contracts can lose out on funds when minting LP tokens.

### Proof of Concept

The `PendleMarketV3.mint()` function accepts as parameters `uint256 netSyDesire` and `uint256 netPtDesired` , which serve as upper bounds, where the Market will try and mint as many LP tokens as possible such that neither of the upper bound amounts are exceeded. The issue is that in `PendleConnector.depositIntoMarket`, the developers incorrectly assume a call to `PendleMarketV3.skim()` will return back any unused tokens that were sent. The `skim()` function sends the extra tokens to the Pendle treasury rather than the calling contract: [skim()](https://github.com/pendle-finance/pendle-core-v2-public/blob/e48767be54fd668c4ea693ac56d13186f2517e3d/contracts/core/Market/v3/PendleMarketV3.sol#L223-L229).

```solidity
    * @dev skim allows us to get the surplus tokens
    */
function depositIntoMarket(IPMarket market, uint256 SYamount, uint256 PTamount) external onlyManager nonReentrant {
    (IPStandardizedYield _SY, IPPrincipalToken _PT,) = IPMarket(market).readTokens();
    IERC20(address(_SY)).safeTransfer(address(market), SYamount);
    IERC20(address(_PT)).safeTransfer(address(market), PTamount);
    market.mint(address(this), SYamount, PTamount);
    market.skim();
    emit DepositIntoMarket(address(market), SYamount, PTamount);
}
```

### Recommended Mitigation Steps

Remove the call to `market.skim()` and integrate with `MarketMathCore.addLiquidity()` to pre-calculate the used `SY` and `PT` amounts which then can be supplied to `market.mint()`. This will ensure no tokens are lost.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1363#issuecomment-2126553627):**
 > True, needs to be fixed.
> 
> I don't think this one is a High severity because although the use-case of skim() function is incorrectly assumed, by putting correct inputs in the SY and PT amount, the contract is not going to lose any funds.

**[gzeon (judge) commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1363#issuecomment-2143605258):**
 > I think this is High risk due to MEV mentioned in [issue \#473](https://github.com/code-423n4/2024-04-noya-findings/issues/473), even if the UI handles SY and PT amount correctly, funds can still be stolen.


***

## [[H-06] Incomplete TVL Calculation in `AerodromeConnector::_getPositionTVL` Function](https://github.com/code-423n4/2024-04-noya-findings/issues/1360)
*Submitted by [KupiaSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1360), also found by [Weed0607](https://github.com/code-423n4/2024-04-noya-findings/issues/1301), pkqs90 ([1](https://github.com/code-423n4/2024-04-noya-findings/issues/1104), [2](https://github.com/code-423n4/2024-04-noya-findings/issues/1102)), [said](https://github.com/code-423n4/2024-04-noya-findings/issues/713), [Inspex](https://github.com/code-423n4/2024-04-noya-findings/issues/608), BenRai ([1](https://github.com/code-423n4/2024-04-noya-findings/issues/502), [2](https://github.com/code-423n4/2024-04-noya-findings/issues/499)), [Zac](https://github.com/code-423n4/2024-04-noya-findings/issues/436), and [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/123)*

### Impact

The [AerodromeConnector::stake](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L100) function allows to stake liquidity tokens to the gauge pool. However, the [AerodromeConnector::\_getPositionTVL](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L125) function, which is responsible for calculating the Total Value Locked (TVL), does not take into account the liquidity tokens deposited in the gauge pool. This oversight will result in an incorrect calculation of the TVL, which could negatively impact the overall functionality of the protocol that utilizes the TVL metric.

### Proof of Concept

The [AerodromeConnector::stake](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L100) function allows to deposit and stake liquidity tokens in the gauge pool.

```solidity
AerodromeConnector.sol
100: function stake(address pool, uint256 liquidity) public onlyManager nonReentrant {
101:         address gauge = voter.gauges(pool);
102:         IERC20(pool).forceApprove(address(gauge), liquidity);
103:         IGauge(gauge).deposit(liquidity, address(this));  // @audit-info this sends tokens to the gauge
104:     }
```

The implementation of the [Gauge::deposit](https://github.com/aerodrome-finance/contracts/blob/b934e7ae398ea6c251a4d5af2119776c06f1f23d/contracts/gauges/Gauge.sol#L151) is as follows:

```solidity
    function deposit(uint256 _amount, address _recipient) external {
        _depositFor(_amount, _recipient);
    }

    function _depositFor(uint256 _amount, address _recipient) internal nonReentrant {
        if (_amount == 0) revert ZeroAmount();
        if (!IVoter(voter).isAlive(address(this))) revert NotAlive();


        address sender = _msgSender();
        _updateRewards(_recipient);


        IERC20(stakingToken).safeTransferFrom(sender, address(this), _amount); // @audit-info liquidity tokens are sent to the gauge.
        totalSupply += _amount;
        balanceOf[_recipient] += _amount;


        emit Deposit(sender, _recipient, _amount);
    }
```

As evident from the preceding code snippet, when the `Gauge::deposit` function is invoked, staked liquidity tokens are sent to the gauge pool. However, the implementation of the [AerodromeConnector::\_getPositionTVL](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L125) function only accounts for the liquidity tokens held in the Aerodrome pool, and does not consider the tokens that have been staked in the gauge pool. This oversight in the [AerodromeConnector::\_getPositionTVL](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/AerodromeConnector.sol#L125) function will result in an incomplete calculation of the Total Value Locked (TVL).

```solidity
AerodromeConnector.sol
125: function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) { 
126:         PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
127:         (address pool) = abi.decode(pBP.data, (address));
128:         uint256 balance = IERC20(pool).balanceOf(address(this)); // @audit-issue only accounts the liquidity token balance at the aerodrome pool, does not include the gauge pool
129:         uint256 totalSupply = IERC20(pool).totalSupply();
130:         (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();
131:         uint256 amount0 = balance * reserve0 / totalSupply;
132:         uint256 amount1 = balance * reserve1 / totalSupply;
133:         return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1);
134:     }
```

As a result, the Total Value Locked (TVL) value calculated by the `AerodromeConnector::_getPositionTVL` function will be less than the actual value, as it does not account for the liquidity tokens staked in the gauge pool. This underestimation of the TVL could negatively impact the overall functionality of the protocol that relies on the TVL metric.

### Recommended Mitigation Steps

It is recommended to fix the `_getPositionTVL` function to take account liquidity tokens staked in the gauge pool as follows:

```diff
    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
        PositionBP memory pBP = registry.getPositionBP(vaultId, p.positionId);
        (address pool) = abi.decode(pBP.data, (address));
+       address gauge = voter.gauges(pool);
-       uint256 balance = IERC20(pool).balanceOf(address(this));
+       uint256 balance = IERC20(pool).balanceOf(address(this)) + IERC20(gauge).balanceOf(address(this));
        uint256 totalSupply = IERC20(pool).totalSupply();
        (uint256 reserve0, uint256 reserve1,) = IPool(pool).getReserves();
        uint256 amount0 = balance * reserve0 / totalSupply;
        uint256 amount1 = balance * reserve1 / totalSupply;
        return _getValue(IPool(pool).token0(), base, amount0) + _getValue(IPool(pool).token1(), base, amount1);
    }
```

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1360#issuecomment-2126556101):**
 > True, needs to be fixed.<br>
> But I think Medium severity not High, because it's not going to cause loss of funds in any way.

**[gzeon (judge) commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1360#issuecomment-2143825068):**
 > Finalizing as High Risk as TVL affects share calculation.


***

## [[H-07] `PendleConnector` incorrectly sends the redeemed `PT` tokens to the market](https://github.com/code-423n4/2024-04-noya-findings/issues/1339)
*Submitted by [alexxander](https://github.com/code-423n4/2024-04-noya-findings/issues/1339), also found by [ArsenLupin](https://github.com/code-423n4/2024-04-noya-findings/issues/1382), [WinSec](https://github.com/code-423n4/2024-04-noya-findings/issues/951), and [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/316)*

### Impact

Burning a Pendle LP will donate the `PT` tokens to the market instead of withdrawing them to the `PendleConnector` which leads to a loss of funds for the Connector. 

### Proof of Concept

The Pendle Market `burn()` function accepts as the first address parameter the receiver of the `SY` tokens and a second address parameter that is the receiver of the `PT` tokens. The issue is that in `PendleConnecotr.burnLP()`, the function `market.burn()`  selects the `market` as the receiver of the ` PT  ` tokens, where it should be the `PendleConnector` i.e., `address(this)`:

```solidity
function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {
	IERC20(address(market)).safeTransfer(address(market), amount);
	// @audit -> address(market) should be address(this)
	market.burn(address(this), address(market), amount);
	market.skim();
	emit BurnLP(address(market), amount);
}
```

```solidity
// PendleMarket.burn()
function burn(
	address receiverSy,
	address receiverPt,
	uint256 netLpToBurn
) external nonReentrant returns (uint256 netSyOut, uint256 netPtOut) {
```

### Recommended Mitigation Steps

```diff
    function burnLP(IPMarket market, uint256 amount) external onlyManager nonReentrant {
        IERC20(address(market)).safeTransfer(address(market), amount);
-       market.burn(address(this), address(market), amount);
+       market.burn(address(this), address(this), amount);
        market.skim();
        emit BurnLP(address(market), amount);
    }
```

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1339#event-12905779501)**


***

## [[H-08] A Vault can steal all funds from another Vault through the Registry's flash loan contract due to insufficient access control in `Connector.sendTokensToTrustedAddress()`](https://github.com/code-423n4/2024-04-noya-findings/issues/1327)
*Submitted by [alexxander](https://github.com/code-423n4/2024-04-noya-findings/issues/1327) (View multiple [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1327+is%3Aclosed+-label%3Aunsatisfactory) submitted by additional wardens)*

### Impact

The keeper of a Vault can steal all funds from another Vault.

### Proof of Concept

Noya Vaults are registered with the `Registry` contract where `Registry.addVault()` is used to add a particular Vault and specify the address of its `AccountingManager`, `maintainer`, `keeper`, etc. The `Registry` contract also has the state variable address `flashLoan` which is the address of a `BalancerFlashLoan` contract that is used by the Vaults to leverage flash loans. The issue is that in any Connector, the `BaseConnector.sendTokensToTrustedAddress()` function allows the `BalancerFlashLoan` contract to perform token transfers back to the `BalancerFlashLoan` contract - [code snippet](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/helpers/BaseConnector.sol#L98-L99). This allows for the following exploit:

*   Assume 2 Vaults with Ids: ID-1 and ID-2
*   Assume ID-1 has a Connector C-1
*   Assume ID-2 has a Connector C-2
*   Assume C-2 holds X amount of token Y
*   The keeper of ID-1 calls `BalancerFlashLoan.makeFlashloan()` [code snippet](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerFlashLoan.sol#L37-L44)
*   the `tokens` array holds the address of some token
*   the `amounts` array holds some amount of the token in `tokens`
*   `bytes userData` is packed as
    *   `uint256 vaultId = ID-1`
    *   `address receiver = C-1`
    *   `address[] destinantionConnector = [C-2, Y]`
    *   `bytes[] callingData =     [sendTokensToTrustedAddress(Y, X, address(0), ""),    transferTo(C1, X)]`
    *   `uint256[] gas = [enoughGas, enoughGas]`
*   `BalancerFlashLoan.receiveFlashLoan()` is called by Balancer
*   The `receiver` (`C-1`) get's the flash loan tokens
*   `destinationConnector[0].call{...}(callingData[0])`, which is the `BaseConnector.sendTokensToTrustedAddress()` call to `C-2`. The Connector `C-2` allows the execution since `msg.sender` is `registry.flashLoan()`. `C-2` sends X amount of tokens to `BalancerFlashLoan`.
*   `destinationConnector[1].call{...}(callingData[1])`, which is the `Y.transferTo()` call that will transfer the X amount of tokens from `BalancerFlashLoan` to `C-1`.
*   `C-1` returns the borrowed tokens and keeps the X amount of token Y

### Coded Proof of Concept

The aim of the POC is to showcase how one Vault can steal the funds from another Vault's `BaseConnector`. The test consists of 2 Vaults (ID-5 and ID-10).  In the beginning of the test
ID-5 receives and executes deposits that go into its `BaseConnector`. The keeper of ID-10 then leverages the `BalancerFlashLoan` contract to call `BaseConnector.sendTokensToTrustedAddress()` and after that to retrieve the funds into an arbitrary address.

*   Add the contents of the following gist in a solidity file under `/testsFoundry` - [gist with code](https://gist.github.com/alexxander77/fd48ea07b66e8e6896896467ba594cad)
*   Execute with `forge test --match-test testVaultIssue -vv --fork-url <mainnet rpc url>`

### Recommended Mitigation Steps

Function `BaseConnector.sendTokensToTrustedAddress()` should be able to check that the caller of `BalancerFlashLoan.makeFlashLoan()` is authorized to perform calls into the Connector.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1327#issuecomment-2147881870):**
 > Fixed in e1d9ac635b6cada731bdfc16d2a1b7b640360311 and 986d24df537bed29ebec7fc51ae2e6f442058cea.


***

## [[H-09] PrismaConnector are not able to claim surplus collateral in recovery mode](https://github.com/code-423n4/2024-04-noya-findings/issues/1306)
*Submitted by [grearlake](https://github.com/code-423n4/2024-04-noya-findings/issues/1306)*

From [prisma docs](https://docs.prismafinance.com/protocol-concepts/recovery-mode):

> While in Recovery Mode, if your vault’s Individual Collateral Ratio (ICR) falls below the GTCR, your vault can be liquidated (even if your vault's collateral ratio is above 110\%). To prevent this from happening, in both Normal and Recovery Mode, a user should maintain their collateral ratio over 150\%.
> 
> During Recovery Mode, the liquidation loss is capped at 110\% of a vault's collateral. Any residual amount, i.e. the collateral above 110\% (and below the Global Total Collateral Ratio or GTCR), can be recouped by the borrower who faced liquidation by claiming the surplus collateral.
> 
> This implies that a borrower will encounter the same liquidation "penalty" (20\%) in Recovery Mode as they would in Normal Mode if their vault undergoes liquidation.

Function `claimCollateral()` is used to claim surplusBalances [link](https://github.com/prisma-fi/prisma-contracts/blob/63f3d08d6d7ae9fc74855a489eeae080b72a3f46/contracts/core/TroveManager.sol#L835):

    function claimCollateral(address _receiver) external {
        uint256 claimableColl = surplusBalances[msg.sender];
        require(claimableColl > 0, "No collateral available to claim");

        surplusBalances[msg.sender] = 0;

        collateralToken.safeTransfer(_receiver, claimableColl);
    }

But in `PrismaConnector` contract, it does not have function to call `claimCollateral()` function, lead to surplusBalances is stucked forever.

### Impact

`surplusBalances` are not able to be claimed, funds is stuck.

### Recommended Mitigation Steps

Create function to call `claimCollateral()` function in prisma.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1306#event-12906038087)**


***

## [[H-10] `AccountingManager::resetMiddle` will not behave as expected](https://github.com/code-423n4/2024-04-noya-findings/issues/1224)
*Submitted by [Aymen0909](https://github.com/code-423n4/2024-04-noya-findings/issues/1224) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1224+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

<https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L461-L468><br>
<https://github.com/code-423n4/2024-04-noya/blob/main/contracts/accountingManager/AccountingManager.sol#L328-L354>

The `resetMiddle` function in the `AccountingManager` contract is designed to reset the middle index of either the deposit or withdraw queue. This function is crucial for managing the order and processing of transactions within these queues, particularly in scenarios where recalculations are necessary to ensure fairness and accuracy in the distribution of shares or handling of withdrawals.

The function will work as expected when resetting the deposit queue, but it will not work for the reset of the withdrawal queue and will cause wrong withdrawal amount accounting to occurs.

To understand the issue we must first see how the withdrawal queue middle is calculated. The middle index of the withdrawal queue is updated during the process of calculating the withdrawal shares. This occurs in the `calculateWithdrawShares` function, which is designed to process queued withdrawal requests and assign the corresponding amount of base tokens to each request based on the current share price.

For each withdrawal request in the queue that has not yet been processed, the function calculates the amount of base tokens equivalent to the shares requested for withdrawal. After processing the maximum allowed iterations or reaching the end of the queue, the function updates the official middle index of the withdrawal queue to the last processed index (middleTemp) and increments the total base token amount needed for the current withdraw group `currentWithdrawGroup.totalCBAmount` (remember this state as it will be important).

Here is the relevant part of the code that handles the updating of the middle index:

```solidity
function calculateWithdrawShares(uint256 maxIterations) public onlyManager nonReentrant whenNotPaused {
    uint256 middleTemp = withdrawQueue.middle;
    uint64 i = 0;

    ...

    while (withdrawQueue.last > middleTemp && i < maxIterations) {
        WithdrawRequest storage data = withdrawQueue.queue[middleTemp];
        uint256 assets = previewRedeem(data.shares);
        data.amount = assets;
        data.calculationTime = block.timestamp;
        emit CalculateWithdraw(middleTemp, data.owner, data.receiver, data.shares, assets, block.timestamp);
        middleTemp += 1;
        i += 1;
    }
    currentWithdrawGroup.totalCBAmount += assetsNeededForWithdraw;
    withdrawQueue.middle = middleTemp;
}
```

Now let's see how the `resetMiddle` function will cause an issue to occur in the withdrawal process:

```solidity
function resetMiddle(
    uint256 newMiddle,
    bool depositOrWithdraw
) public onlyManager {
    if (depositOrWithdraw) {
        emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw);

        if (
            newMiddle > depositQueue.middle ||
            newMiddle < depositQueue.first
        ) {
            revert NoyaAccounting_INVALID_AMOUNT();
        }
        depositQueue.middle = newMiddle;
    } else {
        emit ResetMiddle(
            newMiddle,
            withdrawQueue.middle,
            depositOrWithdraw
        );

        if (
            newMiddle > withdrawQueue.middle ||
            newMiddle < withdrawQueue.first ||
            currentWithdrawGroup.isStarted
        ) {
            revert NoyaAccounting_INVALID_AMOUNT();
        }
        withdrawQueue.middle = newMiddle;
        //@audit currentWithdrawGroup.totalCBAmount is not reset
    }
}
```

As it can be seen the function doesn't reset the value for current withdraw group `currentWithdrawGroup.totalCBAmount` which will keep its value from the previous calculation which is supposed to be wrong, and thus when later on the manager will call `calculateWithdrawShares` to calculate the withdrawal shares once again, `currentWithdrawGroup.totalCBAmount` will get incremented on the previously calculated amount which will result in a bigger base token amount needed for the withdrawal to be processed than what was supposed to be.

Thus the accounting for the current withdrawal group will be wrong. This issue will cause the following problems:

*   First it will force the protocol manager to withdraw more funds than intended from the connectors to reach the amount needed for withdrawal of current group represented by `currentWithdrawGroup.totalCBAmount` (which is wrong -bigger- in our case after the reset has occurred), this will result in  potential yield that could've been generated and thus a loss for funds for the protocol and its users.

*   The worst that can happen is if `currentWithdrawGroup.totalCBAmount` after being incremented twice for the same group (the first time and the second time after the reset call as it wasn't updated) is bigger that the current protocol TVL (which can happen especially in early days of the vault), in that case the protocol is unable to get necessary amount of funds to execute the withdrawal and the withdrawal process and funds will remain blocked until new deposit are made & executed.

### Impact

The `reset` function doesn't reset the withdrawal amount requested `currentWithdrawGroup.totalCBAmount` which will cause problems in the withdrawal process and result a loss of funds for the protocol and all other users.

### Recommended Mitigation

To address this issue, the `reset` function must reset the withdrawal amount requested `currentWithdrawGroup.totalCBAmount` (set back to 0), the function should be modified as follows:

```diff
function resetMiddle(
    uint256 newMiddle,
    bool depositOrWithdraw
) public onlyManager {
    if (depositOrWithdraw) {
        emit ResetMiddle(newMiddle, depositQueue.middle, depositOrWithdraw);

        if (
            newMiddle > depositQueue.middle ||
            newMiddle < depositQueue.first
        ) {
            revert NoyaAccounting_INVALID_AMOUNT();
        }
        depositQueue.middle = newMiddle;
    } else {
        emit ResetMiddle(
            newMiddle,
            withdrawQueue.middle,
            depositOrWithdraw
        );

        if (
            newMiddle > withdrawQueue.middle ||
            newMiddle < withdrawQueue.first ||
            currentWithdrawGroup.isStarted
        ) {
            revert NoyaAccounting_INVALID_AMOUNT();
        }
        withdrawQueue.middle = newMiddle;
++      currentWithdrawGroup.totalCBAmount = 0;
    }
}
```

**[gzeon (judge) increased severity to High](https://github.com/code-423n4/2024-04-noya-findings/issues/1224#issuecomment-2143978598)**

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1224#issuecomment-2147949222):**
 > Fixed in commit 962d297e937e82d95e20739078a61b00eea47643.<br>
> If we are resetting the withdrawal queue, we have to reset all withdrawals that are calculated so far. So we can safely set the `totalCBAmount` to 0.


***

## [[H-11] `SNXConnector.sol` TVL calculation is incorrect](https://github.com/code-423n4/2024-04-noya-findings/issues/1120)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1120) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1120+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

SNXConnector allows depositing collateral and minting SUSD.

There are two issues for TVL calculation code:

1.  It does not account for the debt occurred for minting SUSD
2.  `totalDeposited` already includes `totalAssigned`

Note that the minted SUSD tokens are already calculated into TVL by calling `_updateTokenInRegistry(usdToken);` while minting SUSD, so the debt part must be calculated as well.

```solidity
    function mintOrBurnSUSD(
        uint256 _amount,
        uint128 _accountId,
        uint128 poolId,
        address collateralType,
        bool mintOrBurn
    ) public onlyManager {
        // Mint or burn
        address usdToken = SNXCoreProxy.getUsdToken();
        if (mintOrBurn) {
            SNXCoreProxy.mintUsd(_accountId, poolId, collateralType, _amount);
        } else {
            _approveOperations(usdToken, address(SNXCoreProxy), _amount);
            SNXCoreProxy.burnUsd(_accountId, poolId, collateralType, _amount);
        }
        _updateTokenInRegistry(collateralType);
>       _updateTokenInRegistry(usdToken);
    }

    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
        (uint128 accountId, address collateralType) = abi.decode(p.data, (uint128, address));
        (uint256 totalDeposited, uint256 totalAssigned, uint256 totalLocked) =
            SNXCoreProxy.getAccountCollateral(accountId, collateralType);
>       tvl = _getValue(collateralType, base, totalDeposited + totalAssigned);
    }
```

We can find the implementation of `getAccountCollateral` here: <https://github.com/Synthetixio/synthetix-v3/blob/main/protocol/synthetix/contracts/storage/Account.sol#L101-L116>

```solidity
    function getCollateralTotals(
        Data storage self,
        address collateralType
    )
        internal
        view
        returns (uint256 totalDepositedD18, uint256 totalAssignedD18, uint256 totalLockedD18)
    {
        totalAssignedD18 = getAssignedCollateral(self, collateralType);
>       totalDepositedD18 =
>           totalAssignedD18 +
>           self.collaterals[collateralType].amountAvailableForDelegationD18;
        totalLockedD18 = self.collaterals[collateralType].getTotalLocked();

        return (totalDepositedD18, totalAssignedD18, totalLockedD18);
    }
```

### Recommended Mitigation Steps

The collateral calculation can just use `totalDeposited`.

However the debt calculation is a bit tricky. The closest API for fetching debt is using `updateAccountDebt` <https://github.com/Synthetixio/synthetix-v3/blob/main/protocol/synthetix/contracts/storage/Pool.sol#L366-L373>, but it is not a view function. Not really sure what the best solution here is.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1120#event-13146834833)**


***

## [[H-12] `Registry.sol#updateHoldingPosition` remove position logic is incorrect: should use `ownerConnector` instead of `calculatorConnector` when calculating `holdingPositionId`](https://github.com/code-423n4/2024-04-noya-findings/issues/1093)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1093), also found by [Autosaida](https://github.com/code-423n4/2024-04-noya-findings/issues/1241), [josephdara](https://github.com/code-423n4/2024-04-noya-findings/issues/1146), [den-sosnowsky](https://github.com/code-423n4/2024-04-noya-findings/issues/1055), [eta](https://github.com/code-423n4/2024-04-noya-findings/issues/711), [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/564), and [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/172)*

### Impact

When removing a `holdingPosition` that is not at the back of `holdingPositions` array, the `holdingPositionId` is incorrectly calculated. This will mess up the position index, and ultimately mess up TVL calculation.

### Description

When removing a position in `updateHoldingPosition`, if the index of the position is not the last, it will do a swap between the current index and the last index, and remove the last position in `holdingPositions` array. However, the issue is when updating `vault.isPositionUsed[holdingPositionId]` index, the `holdingPositionId` is not correct.

It should be using `vault.holdingPositions[positionIndex].ownerConnector` instead of `vault.holdingPositions[positionIndex].calculatorConnector`.

This would be an issue for most of the token-holding positions because the `calculateorConnector` is the `AccountingManager` while the `ownerConnector` is the connector's own address.

```solidity
    function updateHoldingPosition(
        uint256 vaultId,
        bytes32 _positionId,
        bytes calldata _data,
        bytes calldata additionalData,
        bool removePosition
    ) public vaultExists(vaultId) returns (uint256) {
        Vault storage vault = vaults[vaultId];
        if (!vault.connectors[msg.sender].enabled) revert UnauthorizedAccess();
        if (!vault.trustedPositionsBP[_positionId].isEnabled) revert InvalidPosition(_positionId);
        bytes32 holdingPositionId = keccak256(abi.encode(msg.sender, _positionId, _data));
        uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
        if (positionIndex == 0 && removePosition) return type(uint256).max;
        if (removePosition) {
            if (positionIndex < vault.holdingPositions.length - 1) {
                vault.holdingPositions[positionIndex] = vault.holdingPositions[vault.holdingPositions.length - 1];
                vault.isPositionUsed[keccak256(
                    abi.encode(
>                       vault.holdingPositions[positionIndex].calculatorConnector,
                        vault.holdingPositions[positionIndex].positionId,
                        vault.holdingPositions[positionIndex].data
                    )
                )] = positionIndex;
            }
            vault.holdingPositions.pop();
            vault.isPositionUsed[holdingPositionId] = 0;
            emit HoldingPositionUpdated(vaultId, _positionId, _data, additionalData, removePosition, positionIndex);
            return type(uint256).max;
        }
        return
            updateHoldingPosition(vault, vaultId, _positionId, _data, additionalData, positionIndex, holdingPositionId);
    }
```

### Proof of Concept

We will give an example of how this bug will mess up the position index and ultimately lead to incorrect TVL.

Add the following test code in `BaseConnector.t.sol`. It does the following:

1.  Create 3 connectors, with the order \[1, 2, 3] (with a dummy connector up front), and deal 10e6 USDC to each of them.
2.  Check that current TVL is 30e6.
3.  Move all USDC from connector 1 to 3. This should remove connector 1's position. The current position array is \[3, 2].
4.  Move all USDC from connector 3 to 2. This should remove connector 3's position. However, since the `positionIndex` is not correctly updated in step 3, the connector 3's `positionIndex` is still 3. This in `updateHoldingPosition()` will result in popping the position at the back (which is actually position 2).
5.  Check that current TVL is 0: because connector 2 is holding all the USDC but it has been popped out in step 4.

```solidity
    function testRemoveConnectorBug() public {
        vm.startPrank(owner);
        BaseConnector connector3;
        connector3 = new BaseConnector(BaseConnectorCP(registry, 0, swapHandler, noyaOracle));
        addConnectorToRegistry(vaultId, address(connector3));

        // Step 1: Deal 10e6 USDC tokens to all 3 connectors.
        uint256 amount = 10 * 1e6;
        _dealWhale(baseToken, address(connector), USDC_Whale, amount);
        _dealWhale(baseToken, address(connector2), USDC_Whale, amount);
        _dealWhale(baseToken, address(connector3), USDC_Whale, amount);
        vm.startPrank(owner);
        connector.updateTokenInRegistry(USDC);
        connector2.updateTokenInRegistry(USDC);
        connector3.updateTokenInRegistry(USDC);

        // Make sure the TVL is 30e6.
        uint tvl = accountingManager.TVL();
        assertEq(tvl, 30e6);

        // Step 2: Move all USDC from connector 1 to connector 3. TVL is still 30e6.
        address[] memory tokens = new address[](1);
        tokens[0] = USDC;
        uint256[] memory amounts = new uint256[](1);
        amounts[0] = amount;
        {
            connector.transferPositionToAnotherConnector(tokens, amounts, "", address(connector3));
            uint tvl = accountingManager.TVL();
            assertEq(tvl, 30e6);
        }

        // Step 3: Move all USDC from connector 3 to connector 2. TVL is now ZERO.
        {
            amounts[0] = 2 * amount;
            connector3.transferPositionToAnotherConnector(tokens, amounts, "", address(connector2));
            uint tvl = accountingManager.TVL();
            assertEq(tvl, 0);
        }
    }
```

### Tools Used

Foundry

### Recommended Mitigation Steps

Use `vault.holdingPositions[positionIndex].ownerConnector` to calculate holdingPositionId.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1093#issuecomment-2149748939):**
 > Fix in commit aef35f768753277552c65ffecf199ea73d0cd058.


***

## [[H-13] `BalancerConnector::_getPositionTVL` is calculated incorrectly  ](https://github.com/code-423n4/2024-04-noya-findings/issues/1033)
*Submitted by [SBSecurity](https://github.com/code-423n4/2024-04-noya-findings/issues/1033), also found by [ladboy233](https://github.com/code-423n4/2024-04-noya-findings/issues/1323), [DPS](https://github.com/code-423n4/2024-04-noya-findings/issues/879), [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/789), [Sentryx](https://github.com/code-423n4/2024-04-noya-findings/issues/650), and [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/196)*

### Impact

BalancerConnector misuses the weight of pool tokens, leading to decreased TVL of these positions.

### Proof of Concept

If we take a look at the balancer documentation and especially how the tokens are being valued, we can see that they are not using weight to determine the price of the `pool.tokens[pool.tokenIndex]`:

[BalancerDocs](https://docs.balancer.fi/reference/lp-tokens/valuing.html#directly-calculating-nav)

```solidity
(tokens, balances, lastChangeBlock) = vault.getPoolTokens(poolId);
prices = fetchPricesFromPriceProvider(tokens); //ex. CoinGecko
poolValueUsd = sum(balances[i]*price[i]);
bptPriceUsd = poolValueUsd/bpt.totalSupply();
```

As we can see they are directly calculate the balance by the price, which is not the case in `Noya`:

[BalancerConnector.sol#L162-L173](https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/BalancerConnector.sol#L162-L173)

```solidity
function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
    PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
    PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
    uint256 lpBalance = totalLpBalanceOf(pool);
    (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);
    uint256 _totalSupply = IERC20(pool.pool).totalSupply();

    uint256 _weight = pool.weights[pool.tokenIndex];

    uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]);
    return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);
} 
```

The reason why weight is not needed here is because the balances returned from `getPoolTokens` are already split by them. If we look at the DAI-USDC-USDT pool we will see that balances returned are already splitted and there is no need to be divided by their weights. *(Note: please see image in warden's [original submission](https://github.com/code-423n4/2024-04-noya-findings/issues/1033))*

But since Noya uses weights to divide the balance of the tokens, the result will be amount which is percentage weight, set in the `pool.weights[pool.tokenIndex]`, of the actual balance and TVL will be accounted much lower as it is in reality.

Example with USDT and values from [`BalancerConnector.t.sol`](https://github.com/code-423n4/2024-04-noya/blob/main/testFoundry/BalancerConnector.t.sol#L96-L125):

`return (((1e18 * 423099282190 * 991435857075096399976) / 333333333333333333) / 2596148431740844293012911818494888)`**≈ 0.484**

### Recommended Mitigation Steps

Do not use weights to evaluate the TVL of the position, instead just refactor the `_getPositionTVL`'s return with proper decimal scaling based on the asset used.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1033#issuecomment-2167905982)**


***

## [[H-14] `BalancerConnector` has incorrect implementation of totalSupply, positionTVL and total TVL will be invalid](https://github.com/code-423n4/2024-04-noya-findings/issues/1021)
*Submitted by [oakcobalt](https://github.com/code-423n4/2024-04-noya-findings/issues/1021), also found by [grearlake](https://github.com/code-423n4/2024-04-noya-findings/issues/1425), [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/1204), [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1106), [DPS](https://github.com/code-423n4/2024-04-noya-findings/issues/859), [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/811), [Sentryx](https://github.com/code-423n4/2024-04-noya-findings/issues/652), and [cu5t0mpeo](https://github.com/code-423n4/2024-04-noya-findings/issues/505)*

### Proof of Concept

In `BalancerConnector::_getPositionTVL`, when calculating connector held LP token ratio, `IERC20(pool.pool).totalSupply()` is called. This is an incorrect implementation.

In Balancer, totalSupply() is different from totalActualSupply(). Based on Balancer [doc](https://docs.balancer.fi/concepts/advanced/valuing-bpt/valuing-bpt.html#getactualsupply):

> getActualSupply: This is the most common/current function to call. getActualSupply is used by the most recent versions of Weighted and Stable Pools. It accounts for pre-minted BPT as well as due protocol fees.

> totalSupply: In general, totalSupply only makes sense to call for older "legacy" pools. The original Weighted and Stable Pools do not have pre-minted BPT, so they follow the typical convention of using totalSupply to account for issued pool shares.

In short, totalSupply will include pre-minted BPT(balancer pool tokens) and shouldn't be used when calculating user position value. [The pool's arithmetic behaves as if it didn't exist, and the BPT total supply is not a useful value](https://docs.balancer.fi/concepts/advanced/preminted-bpt.html#preminted-bpt).
`getAcutalSupply` should be used instead.

```solidity
//contracts/connectors/BalancerConnector.sol
    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256) {
        PositionBP memory PTI = registry.getPositionBP(vaultId, p.positionId);
        PoolInfo memory pool = abi.decode(PTI.additionalData, (PoolInfo));
        uint256 lpBalance = totalLpBalanceOf(pool);
        (, uint256[] memory _tokenBalances,) = IBalancerVault(balancerVault).getPoolTokens(pool.poolId);
|>      uint256 _totalSupply = IERC20(pool.pool).totalSupply();

        uint256 _weight = pool.weights[pool.tokenIndex];

        uint256 token1bal = valueOracle.getValue(pool.tokens[pool.tokenIndex], base, _tokenBalances[pool.tokenIndex]);
|>      return (((1e18 * token1bal * lpBalance) / _weight) / _totalSupply);
    }
```

(<https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/BalancerConnector.sol#L167>)

In addition, in BalancerConnecot.t.sol we can see the intention is to use weighted pools with pre-minted BPT([USDC-DAI-USDT Stable Pool](https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/testFoundry/utils/resources/MainnetAddresses.sol#L150)).<br>
Based on the [deployed pool contract](https://etherscan.io/address/0x79c58f70905F734641735BC61e45c19dD9Ad60bC#readContract), `totalSupply` is 2596148430608596515167161432296901 . `totalAcutalSupply` is 1036029413274776191102780.

### Recommended Mitigation Steps

Use `IERC20(pool.pool).totalActualSupply()` with compatible pools.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1021#issuecomment-2133829109):**
 > True, needs to be fixed. But not high severity I think.

**[gzeon (judge) commented](https://github.com/code-423n4/2024-04-noya-findings/issues/1021#issuecomment-2143832308):**
 > Considering as High Risk due to TVL impact share calculation.


***

## [[H-15] SiloConnector `_getPositionTVL` miscalculate the TVL position](https://github.com/code-423n4/2024-04-noya-findings/issues/938)
*Submitted by [AlexCzm](https://github.com/code-423n4/2024-04-noya-findings/issues/938), also found by [ArsenLupin](https://github.com/code-423n4/2024-04-noya-findings/issues/1391), [Sentryx](https://github.com/code-423n4/2024-04-noya-findings/issues/582), and [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/166)*

### Impact

`_getPositionTVL` from SiloConnector calculates  wrongly  the position's TVL thus affecting the share price at which shares are minted / redeemed from the protocol.

### Proof of Concept

Each connector implements a `_getPositionTVL` used to return the value of funds, in base token, its corresponding protocol holds.

This information is used by `AccountingManager` to calculate the total assets of the vault and used by 4626 standard to calculate the shares price.

The problem is that SiloConnector miscalculate the value sent to SiloConnector protocol.

```solidity
    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
        PositionBP memory bp = registry.getPositionBP(vaultId, p.positionId);
        (address siloToken) = abi.decode(bp.data, (address));
        ISilo silo = ISilo(siloRepository.getSilo(siloToken));
        (address[] memory assets, IBaseSilo.AssetStorage[] memory assetsS) = silo.getAssetsWithState();
        uint256 totalDepositAmount = 0;
        uint256 totalBAmount = 0;
        for (uint256 i = 0; i < assets.length; i++) {
            uint256 depositAmount = IERC20(assetsS[i].collateralToken).balanceOf(address(this));
            depositAmount += IERC20(assetsS[i].collateralOnlyToken).balanceOf(address(this));
            uint256 borrowAmount = IERC20(assetsS[i].debtToken).balanceOf(address(this));
            if (depositAmount == 0 && borrowAmount == 0) {
                continue;
            }
            uint256 price = _getValue(assets[i], base, 1e18);
            totalDepositAmount += depositAmount * price / 1e18;
            totalBAmount += borrowAmount * price / 1e18;
        }
        tvl = totalDepositAmount - totalBAmount;
    }
```

This function calls `silo.getAssetsWithState()` to get a list of assets and data associated with them. Then for each asset:

1.  calculates `depositAmount` as sum of 2 different token balances: `collateralToken` and `collateralOnlyToken`
2.  retrieve the `borrowAmount` as the balance of a 3rd token named `debtToken`.
3.  get the price of asset (eg. `assets[i]`) in 'base' token
4.  calculates and save the deposited and borrowed amounts

After all assetes have been looped over, the tvl is calculated as the difference between deposits and debt amounts:<br>
`tvl - totalDepositAmount - totalBAmount`

There are 2 problems here:

1.  `collateralToken` and `collateralOnlyToken` are 2 different tokens and protocol is summing them as if they represents amounts of the same token.
2.  protocol is multiplying the price of `assets[i]` by the amounts of shares and not the underlying token (which is `assets[i]`).

All 3 tokens ( `collateralToken`, `collateralOnlyToken` and `debtToken`) are share tokens with the same underlying asset but have different purposes and different exchange rate.

To help us creating a better picture of what each token represent we can [look](https://github.com/silo-finance/silo-core-v1/blob/e5d16f201ab2139829d45ed881532c936249d3a5/contracts/interfaces/IBaseSilo.sol#L11-L27) how `AssetStorage` struct looks like:

```solidity
    /// @dev Storage struct that holds all required data for a single token market
    struct AssetStorage {
        /// @dev Token that represents a share in totalDeposits of Silo
        IShareToken collateralToken;
        /// @dev Token that represents a share in collateralOnlyDeposits of Silo
        IShareToken collateralOnlyToken;
        /// @dev Token that represents a share in totalBorrowAmount of Silo
        IShareToken debtToken;

        /// @dev COLLATERAL: Amount of asset token that has been deposited to Silo with interest earned by depositors.
        /// It also includes token amount that has been borrowed.
        uint256 totalDeposits;
        /// @dev COLLATERAL ONLY: Amount of asset token that has been deposited to Silo that can be ONLY used
        /// as collateral. These deposits do NOT earn interest and CANNOT be borrowed.
        uint256 collateralOnlyDeposits;
        /// @dev DEBT: Amount of asset token that has been borrowed with accrued interest.
        uint256 totalBorrowAmount;
    }
```

To make an analogy, it is like summing peanuts amount with fruits amount and then multiplying it by the peanut butter jelly price.

### Recommended Mitigation Steps

In the for loop, after you got the share tokens balances with `balanceOf`:

*   convert all 3 share tokens balances to underlying token (eg. `underlyingTotalDeposits, underlyingCollateralOnlyDeposits, underlyingBorrowAmount`)
*   sum underlying deposits : `underlyingTotalDeposits =  underlyingTotalDeposits + underlyingCollateralOnlyDeposits`
*   get the price of the underlying asset
*   calculate the `totalDepositAmount` and `totalBAmount` using the calculated `underlyingTotalDeposits` and `underlyingBorrowAmount` and price.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/938#event-13147639616)**


***

## [[H-16] It is possible to open insolvent position in Silo connector, due to missing check in borrow function](https://github.com/code-423n4/2024-04-noya-findings/issues/926)
*Submitted by [KYP](https://github.com/code-423n4/2024-04-noya-findings/issues/926), also found by [KupiaSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1375), [Weed0607](https://github.com/code-423n4/2024-04-noya-findings/issues/1305), [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1121), [AlexCzm](https://github.com/code-423n4/2024-04-noya-findings/issues/999), [ladboy233](https://github.com/code-423n4/2024-04-noya-findings/issues/993), [Bigsam](https://github.com/code-423n4/2024-04-noya-findings/issues/736), BenRai ([1](https://github.com/code-423n4/2024-04-noya-findings/issues/224), [2](https://github.com/code-423n4/2024-04-noya-findings/issues/182)), [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/173), and [Tigerfrake](https://github.com/code-423n4/2024-04-noya-findings/issues/36)*

[SiloConnector](https://github.com/georgiIvanov/noya-audit/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/SiloConnector.sol#L85-L107)

NOYA uses Connectors to interact with different protocols - deposit, borrow, repay, withdraw. One of the protocols is Silo through the `SiloConnector`.

In the code snippet below the `borrow` and `repay` functions of the `SiloConnector` can be seen:

```javascript
    function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {
        ISilo silo = ISilo(siloRepository.getSilo(siloToken));
        silo.borrow(bToken, amount);
        emit Borrow(siloToken, bToken, amount);
    }

...

    function repay(address siloToken, address rToken, uint256 amount) external onlyManager nonReentrant {
        ISilo silo = ISilo(siloRepository.getSilo(siloToken));
        _approveOperations(rToken, address(silo), amount);
        silo.repay(rToken, amount);
        _updateTokenInRegistry(rToken);
        if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) {
            revert IConnector_LowHealthFactor(0);
        }
        emit Repay(siloToken, rToken, amount);
    }
```

As can be seen in the `repay()` function there is a solvency check that reverts the transaction if the repay amount does not make to position solvent again.

However, this check is missing in the `borrow()` function which allows for a position (in Silo) to be opened that is insolvent (according to the NOYA solvency check in `SolvencyV2`) from the start.

### Root Cause

Missing Validation

### Impact

Breaks protocol invariant of minimum health factor and also the position is easier to get liquidated.

### Proof of Concept

Add the following test to `SiloConnecctor.t.sol` and run with `forge test --mt test_borrowAndRepay -vv`.

```javascript
function test_borrowAndRepay() public {        
    // Get value of 1 WETH in USDC
    uint256 wethPrice = chainlinkOracle.getValue(address(WETH), address(840), 1 ether);
    console.log("weth price :", wethPrice); // 2903,25841858

    // Deal a bit more (15%) USDC than the amount of 2 ETH. Mul by 23 and div by 10 so we deposit 115% USDC per ETH - 23/2 ETH = 1.15
    uint256 _amount = wethPrice * 23 / 100 / 10; // Divide by 100 because oracle price is 8 dec and USDC is 6. 
    console.log("USDC deposited:", _amount);

    _dealWhale(baseToken, address(connector), USDC_Whale, _amount);

    vm.startPrank(address(owner));

    // siloToken, deposit token, amount, open position
    connector.deposit(USDC, USDC, _amount, true);

    // siloToken, borrow token, amount
    connector.borrow(USDC, WETH, 2e18); // borrow 2 WETH in exchange for ~7000 USDC as collateral

    // Get silo repository from connector
    ISiloRepository siloRepository1 = connector.siloRepository();

    // Get USDC silo from silo repository
    ISilo silo = ISilo(siloRepository1.getSilo(USDC));

    console.log("Is Solvent: %s ", SolvencyV2.isSolvent(silo, address(connector), connector.minimumHealthFactor()));

    // siloToken, repay token, amount
    connector.repay(USDC, WETH, 1e18);

    vm.stopPrank();
}
```

### Recommended Mitigation Steps

Add solvency check in the borrow function.

```diff
function borrow(address siloToken, address bToken, uint256 amount) external onlyManager nonReentrant {
    ISilo silo = ISilo(siloRepository.getSilo(siloToken));
    silo.borrow(bToken, amount);
+    if (!SolvencyV2.isSolvent(silo, address(this), minimumHealthFactor)) {
+        revert IConnector_LowHealthFactor(0);
+    }
    _updateTokenInRegistry(bToken);
    emit Borrow(siloToken, bToken, amount);
}
```

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/926#event-13147662586)**


***

## [[H-17] `PrismaConnector` can mint a position below the desired health factor](https://github.com/code-423n4/2024-04-noya-findings/issues/925)
*Submitted by [KYP](https://github.com/code-423n4/2024-04-noya-findings/issues/925)*

[PrismaConnector::adjustTrove](https://github.com/georgiIvanov/noya-audit/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/PrismaConnector.sol#L117-L120)

The `PrismaConnector` contract is responsible for minting ULTRA and managing the collateral backing it. When a trove is opened, collateral is put up and ULTRA minted to the `PrismaConnector`. The contract also allows to manage how much of the stablecoin is minted or repay some of it, to improve the collateral ratio (CR). Since collateral can be liquidated an additional check is made to ensure adjustment operations don't leave the trove insolvent:

```javascript
uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));
if (minimumHealthFactor > healthFactor) {
    revert IConnector_LowHealthFactor(healthFactor);
}
```

The issue lies in the fact that `getNominalICR` is used to get the health factor (aka CR) and the resulting value is always less than `minimumHealthFactor` (1.5e18). Unless an unreasonable amount of collateral is put up. Thus, `adjustTrove` becomes practically unusable to borrow or repay.

### Root Cause

Incorrect CR check in `PrismaConnector`.

### Impact

Adjusting trove in the `PrismaConnector` is broken. Once a trove is opened it can only be closed. In the worst case scenario, not enough ULTRA is initially minted to close the trove, thus getting back the collateral will become impossible.

### Proof of Concept

The following test demonstrates how adjusting the trove fails once it's opened.

Keep in mind that the only part that fails is the wrongly checked CR, actual interaction with Prisma works. Which means that the trove has enough collateral to adjust.

In `ITroveManager` add the following method:

<details>

```javascript
function getCurrentICR(address _borrower, uint256 _price) external view returns (uint256);
```

In `PrismaConnector.t.sol` add the following test and run with `forge test --mt testTroveHealthFactor -vvv`:

```javascript
function testTroveHealthFactor() public {
    uint256 amount = 2e18;                   // collateral
    uint256 ultraToMint = 2000e18;
    _dealERC20(WETH, address(connector), amount);

    uint256 wethPrice = chainlinkOracle.getValue(address(WETH), address(840), 1 ether);
    console.log("wethPrice   :", wethPrice); // 3037$ per WETH

    vm.startPrank(owner);

    connector.approveZap(IStakeNTroveZap(ULTRA_StakeNTroveZap), ULTRA_weeth_troveManager, true);
    connector.openTrove(
        IStakeNTroveZap(ULTRA_StakeNTroveZap), ULTRA_weeth_troveManager, 
        125e14,     // max fee
        amount,     // collateral
        ultraToMint // ULTRA to mint
    );

    ITroveManager tm = ITroveManager(ULTRA_weeth_troveManager);
    (uint256 coll1, uint256 debt1) = tm.getTroveCollAndDebt(address(connector));
    console.log("coll1       :", coll1);
    console.log("debt1       :", debt1);
    console.log("minHF       :", connector.minimumHealthFactor()); // 1.5
    
    uint256 connectorMinHF = connector.minimumHealthFactor();
    uint256 troveHF = tm.getCurrentICR(address(connector), wethPrice * 1e10);  // or coll1 * (wethPrice * 1e10) / debt1;
    console.log("troveHF     :", troveHF);

    assertGt(troveHF, connector.minimumHealthFactor()); // 2000 ULTRA is backed up by 2 WETH, so troveHF is well above 1.5

    // Next call fails, when it shouldn't; health factor of the trove is above connector.minimumHealthFactor()
    vm.expectRevert();
    // repay 1 ULTRA
    connector.adjustTrove( 
        IStakeNTroveZap(ULTRA_StakeNTroveZap), 
        ULTRA_weeth_troveManager, 
        125e14, // max fee
        0,      // collateral to withdraw
        1e18,   // repay amount
        false   // is repay 
    );

    // There should be enough collateral to borrow 1 ULTRA, but call fails
    vm.expectRevert();
    // borrow 1 ULTRA
    connector.adjustTrove( 
        IStakeNTroveZap(ULTRA_StakeNTroveZap), 
        ULTRA_weeth_troveManager, 
        125e14, // max fee
        0,      // collateral to withdraw
        1e18,   // borrow amount
        true   // is borrow 
    );
}
```

</details>

### Recommended Mitigation Steps

Check the price for one unit of the collateral token using `valueOracle`. Then, call `troveManager.getCurrentICR(address(this), collateralPrice)` to get the actual CR and compare it to the minimum.

```diff
    function adjustTrove(
        IStakeNTroveZap zapContract,
        address tm,
        uint256 mFee,
        uint256 wAmount,
        uint256 bAmount,
        bool isBorrowing
    ) public onlyManager nonReentrant {
        bytes32 positionId =
            registry.calculatePositionId(address(this), PRISMA_POSITION_ID, abi.encode(zapContract, tm));
        if (registry.getHoldingPositionIndex(vaultId, positionId, address(this), "") == 0) {
            revert IConnector_InvalidPosition(positionId);
        }
        IBorrowerOperations borrowerOps = zapContract.borrowerOps();
        if (bAmount > 0 && !isBorrowing) {
            _approveOperations(ITroveManager(tm).debtToken(), address(borrowerOps), bAmount);
        }
        borrowerOps.adjustTrove(tm, address(this), mFee, 0, wAmount, bAmount, isBorrowing, address(this), address(this));
        _updateTokenInRegistry(ITroveManager(tm).debtToken());
        // get health factor
-        uint256 healthFactor = ITroveManager(tm).getNominalICR(address(this));
+        uint256 collateralPrice = _getValue(ITroveManager(tm).collateralToken(), ChainlinkOracleConnector.USD(), 1);
+        uint256 healthFactor = ITroveManager(tm).getCurrentICR(address(this), collateralPrice);
        if (minimumHealthFactor > healthFactor) {
            revert IConnector_LowHealthFactor(healthFactor);
        }
        emit AdjustTrove(address(zapContract), tm, mFee, wAmount, bAmount, isBorrowing);
    }
```

If ULTRA is repaid - don't revert if the collateral ratio is below minimum. This will allow repaying ULTRA even when below threshold, which will enable the protocol to repay the debt even in the edge case where Prisma CR is ok, but connectors' CR is below minimum.

In `ITroveManager` add the following two functions:

```javascript
+    function getCurrentICR(address _borrower, uint256 _price) external view returns (uint256);
    
+    function collateralToken() external view returns (address);
```

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/925#event-12910185745)**


***

## [[H-18] In Dolomite, when opening a borrow position, the holding position in the Registry will never be updated due to the `removePosition` flag being set to true](https://github.com/code-423n4/2024-04-noya-findings/issues/886)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-04-noya-findings/issues/886) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-886+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

### Impact

Whenever some of the connectors opens or closes a position, it is updated in the registry.

Usually if/when a position is closed (all asset amount withdrawn / borrow position closed in its entirety, etc.), the holding position is updated with the flag `true` for `bool removePosition`.

In Dolomite, whenever we open a new borrow position, the flag is also set to `true` which means that the position should be removed, and again when closing the borrow position, the flag is also set to `true`.

This will lead to that position never being accounted for in the Registry.

### Proof of Concept

In Dolomite, whenever we want to open a borrow position, we can call the `openBorrowPosition()` function:

```
     function openBorrowPosition(uint256 marketId, uint256 _amountWei, uint256 accountId)
            public
            onlyManager
            nonReentrant
        {
            address token = dolomiteMargin.getMarketTokenAddress(marketId);

            if (!registry.isTokenTrusted(vaultId, token, address(this))) {
                revert IConnector_UntrustedToken(token);
            }
            // borrow
            borrowPositionProxy.openBorrowPosition(
                0, accountId, marketId, _amountWei, AccountBalanceHelper.BalanceCheckFlag.None
            );
            registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
            );
        }
```

As we can see, when calling the `registry.updateHoldingPosition` the `removePosition` flag is set to `true` (the last argument in the function call).

Usually this is done when we want to either close a position or we've emptied the market/pool (our balance/share is 0) and we're closing it, here is an example from the same connector Dolomite properly utilizing this in the `withdraw` function:

```
     function withdraw(uint256 marketId, uint256 _amount) public onlyManager nonReentrant {
            address token = dolomiteMargin.getMarketTokenAddress(marketId);
            depositWithdrawalProxy.withdrawWeiFromDefaultAccount(
                marketId, _amount, AccountBalanceHelper.BalanceCheckFlag.None
            );
            // Update token
            _updateTokenInRegistry(token);
            (uint256[] memory markets,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));
            if (markets.length == 0) {
                registry.updateHoldingPosition(
                    vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(0), "", true
                );
            }
        }
```

We can also see that when closing a borrow position in the same connector, the flag is also set to true:

```
     function closeBorrowPosition(uint256[] memory marketIds, uint256 accountId) public onlyManager nonReentrant {
            // repay
            borrowPositionProxy.closeBorrowPosition(accountId, 0, marketIds);
            registry.updateHoldingPosition(
                vaultId, registry.calculatePositionId(address(this), DOL_POSITION_ID, ""), abi.encode(accountId), "", true
            );
        }
```

Due to the following circuit-breaker check, the borrow position would never be updated as part of the `holdingPositions` array:

```
      if (positionIndex == 0 && removePosition) return type(uint256).max;
```

The `positionIndex` is based on the `isPositionUsed` mapping:

```
     bytes32 holdingPositionId = keccak256(abi.encode(msg.sender, _positionId, _data));
     uint256 positionIndex = vault.isPositionUsed[holdingPositionId];
```

Since that mapping value of the holdingPositionId would have never been initiated, due to the circuit-breaker check above returning type(uint256).max, it would be 0, thus interrupting the function flow.

If the flag hasn't been set to true, the function flow would continue to the end, calling the other `updateHoldingPosition` function, and updating the `isPositionUsed` mapping:

```
    return
                updateHoldingPosition(vault, vaultId, _positionId, _data, additionalData, positionIndex, holdingPositionId);
```

This position would have never been accounted for in the Registry, and if the strategy's actions are based on Registry data, it can fail to close the position in-time, possibly leading to liquidations and bad debt.

### Recommended Mitigation Steps

Set the `removePosition` flag on the `openBorrowPosition` when calling the `updateHoldingPosition` function to `false`.

**[gzeon (judge) increased severity to High and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/886#issuecomment-2156700977):**
 > Both open and close borrow are impacted.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/886#event-13147702845)**


***

## [[H-19] Numerous errors when calculating the TVL for the MorphoBlue connector](https://github.com/code-423n4/2024-04-noya-findings/issues/778)
*Submitted by [Zac](https://github.com/code-423n4/2024-04-noya-findings/issues/778) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-778+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

There are numerous issues when calculating the TVL for the MorphoBlue connector

1.  decimals are not considered in the function `convertCToL` this means that if the loanToken and collateralToken have a different number of decimals the TVL calculation will be wrong.

2.  borrowAmount is added rather than subtracted when calculating the TVL. This means that any borrowing will increase the TVL and any repaying will decrease the TVL

3.  When withdrawing the function `_updateTokenInRegistry` is only called for the collateralToken and not the loanToken. This means that if the loanToken is withdrawn the TVL will be less than it should be.

If the TVL is incorrect, users will recieve an incorrect number of shares when depositing and an incorrect number of base tokens when withdrawing. The below table shows the possible scenarios.

| User      |             TVL lower than expected             |                TVL higher than expected               |
| :-------- | :---------------------------------------------: | :---------------------------------------------------: |
| Deposits  | Recieves more shares than should be entitled to | Recieves fewer base tokens than should be entitled to |
| Withdraws | Recieves less shares than should be entitled to |  Recieves more base tokens than should be entitled to |

### Proof of Concept

The below test can be added to `MorphoBlue.t.sol`.

It shows each of the 3 points above causing the TVL calculation to be incorrect.

    function testSupplyBorrowRepayWithdraw() public {
        uint256 amount = 1000 * 1e6;
        uint256 amount_dai = 1000 * 1e18;
        console.log("----------- Test Deposit -----------");
        _dealWhale(baseToken, address(connector), USDC_Whale, amount);
        _dealERC20(DAI, address(connector), amount_dai);
        vm.startPrank(owner);

        assertEq(
            address(morphoBlueContract), address(connector.morphoBlue()), "MorphoBlue address is not set correctly"
        );

        connector.supply(amount, usdcDaiMarketId, true);
        uint256 tvl = accountingManager.TVL();
        console.log("TVL: %s", tvl); // tvl = 1000000000

        connector.supply(amount_dai, usdcDaiMarketId, false);
        tvl = accountingManager.TVL();
        console.log("TVL before borrow: %s", tvl); // tvl = 1000000000001000000000
        // NOTE: Due to DAI having a different number of decimals than USDC, the TVL increases by a very large amount
        // correct TVL = 2000000000

        connector.borrow(amount / 2, usdcDaiMarketId);
        tvl = accountingManager.TVL();
        console.log("TVL after borrow: %s", tvl); // 1000000000002000000000
        // NOTE: The TVL increases because the borrow is added instead of subtracted from the TVL

        connector.repay(amount / 2, usdcDaiMarketId);
        tvl = accountingManager.TVL();
        console.log("TVL after repay: %s", tvl); // 1000000000001000000000

        connector.withdraw(amount, usdcDaiMarketId, true);
        tvl = accountingManager.TVL();
        console.log("TVL after withdraw 1: %s", tvl); // 1000000000000000000000

        connector.withdraw(amount_dai, usdcDaiMarketId, false);
        tvl = accountingManager.TVL();
        console.log("TVL after withdraw 2: %s", tvl); // 999945369
        // NOTE: The TVL is half of what it should be because the withdraw function does not call _updateTokenInRegistry for the loanToken
        
        vm.stopPrank();
    }

### Tools Used

Manual Review, Foundry

### Recommended Mitigation Steps

Each of the 3 points above must be fixed individually for the TVL calculation to be correct. Each issue can be fixed as follows:

1.  For the function `convertCToL` the result should be divided by 10&ast;&ast;(collateralTokenDecimals) and multiplied by 10&ast;&ast;(loanTokenDecimals).
2.  The borrow amount should be subtracted rather than added in the `_getPositionTVL` function.
<https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L132>
3. call `_updateTokenInRegistry` for the loanToken in the `withdraw` function.
<https://github.com/code-423n4/2024-04-noya/blob/9c79b332eff82011dcfa1e8fd51bad805159d758/contracts/connectors/MorphoBlueConnector.sol#L58>

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/778#event-13159241177)**


***

## [[H-20] `_getPositionTVL` of `UNIv3Connector` wrongly assumes ownership of all liquidity of the provided ticks inside `positionManager`](https://github.com/code-423n4/2024-04-noya-findings/issues/708)
*Submitted by [said](https://github.com/code-423n4/2024-04-noya-findings/issues/708), also found by [SBSecurity](https://github.com/code-423n4/2024-04-noya-findings/issues/1030), [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/907), and [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/790)*

### Impact

When `_getPositionTVL` is called, it queries position information from the pool using the calculated key. However, it assumes that all liquidity within the provided ticks in the `positionManager` is owned by the connector.

### Proof of Concept

When `_getPositionTVL` is called, it calculate `key` by providing `positionManager`, `tL`, `tU`. Then used the key to get liquidity information inside the `pool`.

<https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/UNIv3Connector.sol#L136-L138>

```solidity
    function _getPositionTVL(HoldingPI memory p, address base) public view override returns (uint256 tvl) {
        PositionBP memory positionInfo = registry.getPositionBP(vaultId, p.positionId);
        uint256 tokenId = abi.decode(p.data, (uint256));
        (address token0, address token1) = abi.decode(positionInfo.data, (address, address));
        uint256 amount0;
        uint256 amount1;
        (int24 tL, int24 tU, uint24 fee) = abi.decode(p.additionalData, (int24, int24, uint24));
        {
            IUniswapV3Pool pool = IUniswapV3Pool(factory.getPool(token0, token1, fee));
>>>         bytes32 key = keccak256(abi.encodePacked(positionManager, tL, tU));

>>>         (uint128 liquidity,,, uint128 tokensOwed0, uint128 tokensOwed1) = pool.positions(key);

            (uint160 sqrtPriceX96,,,,,,) = pool.slot0();
            (amount0, amount1) = LiquidityAmounts.getAmountsForLiquidity(
                sqrtPriceX96, TickMath.getSqrtRatioAtTick(tL), TickMath.getSqrtRatioAtTick(tU), liquidity
            );
            amount0 += tokensOwed0;
            amount1 += tokensOwed1;
        }

        tvl += valueOracle.getValue(token0, base, amount0);
        tvl += valueOracle.getValue(token1, base, amount1);
    }
```

This assumption is incorrect as it presumes that all liquidity within the provided ticks is owned by Noya's UniV3 Connector. This leads to wrong `TVL` calculation within the protocol, potentially inflating the TVL beyond its actual value. Consequently, this could undermine the protocol's solvency by incorrectly inflating its perceived total assets.

### Recommended Mitigation Steps

User `positionsManager` `positions` getter instead to provide accurate liquidity owner by connector.

**[HadiEsna (NOYA) confirmed and commented](https://github.com/code-423n4/2024-04-noya-findings/issues/708#issuecomment-2133838093):**
 > True, needs to be fixed. Not High severity though in my opinion.


***

## [[H-21] Decreasing a position in PendleConnector will remove it even if there's still a stake at Penpie](https://github.com/code-423n4/2024-04-noya-findings/issues/677)
*Submitted by [Sentryx](https://github.com/code-423n4/2024-04-noya-findings/issues/677)*

<https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol#L303-L309><br>
<https://github.com/code-423n4/2024-04-noya/blob/main/contracts/connectors/PendleConnector.sol#L223-L231>

`decreasePosition()` will falsely remove the market as a holding position, ignoring the staked Pendle market LP tokens at Penpie and thus that stake won't be counted towards the TVL of the connector and the TVL of the AccountingManager the connector belongs to.

### Proof of Concept

The PendleConnector has a function `decreasePosition()` to redeem Pendle SY tokens in exchange for underlying tokens with which it effectively would remove its stake in a given Pendle market.

```solidity
    function decreasePosition(IPMarket market, uint256 _amount, bool closePosition) external onlyManager nonReentrant {
        (IPStandardizedYield SY,,) = market.readTokens();
        (, address _underlyingToken,) = SY.assetInfo();

        // redeems an amount of base tokens by burning SY
        IERC20(address(SY)).safeTransfer(address(SY), _amount);
        IPStandardizedYield(address(SY)).redeem(address(this), _amount, _underlyingToken, 1, true);
→       if (closePosition && isMarketEmpty(market)) {
            registry.updateHoldingPosition(
                vaultId,
                registry.calculatePositionId(address(this), PENDLE_POSITION_ID, abi.encode(market)),
                "",
                "",
                true
            );
        }
        emit DecreasePosition(address(market), _amount, closePosition);
    }
```

When the `closePosition` parameter is true, `isMarketEmpty()` would be called for the given market to check if the connector holds any of the 3 tokens composing it - Yield token (YT), Principal token (PT) and Standardized Yield token (SY).

```solidity
    function isMarketEmpty(IPMarket market) public view returns (bool) {
        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
        return (
            _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0
                && market.balanceOf(address(this)) == 0
        );
    }
```

The function however does not check if the connector still has a balance in the Penpie pool for this market (a stake), and that will allow the connector to remove its holding position for a market, effectively excluding its stake in the Penpie pool from the connector and the AccountingManager TVL.

### Recommended Mitigation Steps

In the `isMarketOpen()` function check for the connector's balance in the Penpie staking pool for this market.

```diff
diff --git a/contracts/connectors/PendleConnector.sol b/contracts/connectors/PendleConnector.sol
index 17607ee..e1b1208 100644
--- a/contracts/connectors/PendleConnector.sol
+++ b/contracts/connectors/PendleConnector.sol
@@ -304,7 +304,7 @@ contract PendleConnector is BaseConnector {
         (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(market).readTokens();
         return (
             _SY.balanceOf(address(this)) == 0 && _PT.balanceOf(address(this)) == 0 && _YT.balanceOf(address(this)) == 0
-                && market.balanceOf(address(this)) == 0
+                && market.balanceOf(address(this)) == 0 && pendleMarketDepositHelper.balance(market, address(this)) == 0
         );
     }
 

```

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/677#event-12910805143)**

**[gzeon (judge) increased severity to High](https://github.com/code-423n4/2024-04-noya-findings/issues/677#issuecomment-2156655837)**


***

## [[H-22] Invalid calculation of position TVL in Pendle connector](https://github.com/code-423n4/2024-04-noya-findings/issues/350)
*Submitted by [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/350)*

### Impact

Pendle connector allows protocol managers to deposit some underlying asset in return for some SY tokens, which can be used to mint PT and YT tokens. PT and YT can be deposited in markets and in return for LP tokens and some claimable rewards. These LP tokens should be considered when calculating the TVL of the position, to do this the protocol is using `getLpToAssetRate`, which from the [docs](https://docs.pendle.finance/Developers/Helpers/PendleRouterStatic#overview):

> `getLpToAssetRate`: Serves the same purpose, but in terms of SY's asset.

This means that it returns the price of LP in terms of the underlying asset (which is USDT in the below example); however, the protocol is using this function assuming that it returns the price of LP in terms of SY, through:

`SYAmount += lpBalance * IPMarket(market).getLpToAssetRate(10) / 1e18;`

The above also applies to `getPtToAssetRate`.

This will cause an inaccurate representation of the Connector's TVL affecting the whole protocol's TVL.

### Proof of Concept

    function testInvalidPendleTVL() public {
        (IPStandardizedYield _SY, IPPrincipalToken _PT, IPYieldToken _YT) = IPMarket(pendleUsdtMarket).readTokens();
        uint256 USDTamount = 100e6;

        _dealERC20(USDT, address(connector), USDTamount);

        vm.startPrank(owner);

        // Update tokens in registry
        connector.updateTokenInRegistry(USDT);

        // TVL is around 100 USDC
        // Connector holds 100 USDT
        assertEq(accountingManager.TVL() / 1e6, 99);
        assertEq(IERC20(USDT).balanceOf(address(connector)) / 1e6, 100);

        // Supply USDT to the market
        connector.supply(pendleUsdtMarket, USDTamount);

        // TVL is still around 100 USDC
        // Connector holds 0 USDT and around 100 SY
        assertEq(accountingManager.TVL() / 1e6, 99);
        assertEq(IERC20(USDT).balanceOf(address(connector)), 0);
        assertEq(_SY.balanceOf(address(connector)) / 1e6, 99);

        // Mint PT and YT
        connector.mintPTAndYT(pendleUsdtMarket, _SY.balanceOf(address(connector)) / 2);

        // TVL is still around 100 USDC
        // Connector holds 0 USDT, 49 PT, 49 YT and 49 SY
        assertEq(accountingManager.TVL() / 1e6, 100);
        assertEq(IERC20(USDT).balanceOf(address(connector)), 0);
        assertEq(_SY.balanceOf(address(connector)) / 1e6, 49);
        assertEq(_PT.balanceOf(address(connector)) / 1e6, 49);
        assertEq(_YT.balanceOf(address(connector)) / 1e6, 49);

        // Deposit SY and PT into the market
        connector.depositIntoMarket(
            IPMarket(pendleUsdtMarket), _SY.balanceOf(address(connector)), _PT.balanceOf(address(connector))
        );
        vm.roll(block.number + 20);
        vm.warp(block.timestamp + 1 hours);

        // TVL drops to 59 USDC - which is wrong because of the invalid TVL calculation
        // Connector holds 0 USDT, 49 YT, 29 LP, 0 SY and 0 PT
        assertEq(accountingManager.TVL() / 1e6, 59);
        assertEq(IERC20(_YT).balanceOf(address(connector)) / 1e6, 49);
        assertEq(IERC20(pendleUsdtMarket).balanceOf(address(connector)) / 1e6, 29);
        assertEq(_SY.balanceOf(address(connector)), 0);
        assertEq(_PT.balanceOf(address(connector)), 0);
    }

### Recommended Mitigation Steps

Refactor `PendleConnector::_getPositionTVL` to take into consideration that `getLpToAssetRate` and `getPtToAssetRate` calculate the price of LP in terms of the underlying asset and not SY.

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/350#event-12912880785)**

**[gzeon (judge) increased severity to High](https://github.com/code-423n4/2024-04-noya-findings/issues/350#issuecomment-2143856023)**


***

## [[H-23] Invalid handling of holding positions in `DolomiteConnector::transferBetweenAccounts`](https://github.com/code-423n4/2024-04-noya-findings/issues/153)
*Submitted by [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/153), also found by [bigtone](https://github.com/code-423n4/2024-04-noya-findings/issues/670) and [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/120)*

### Impact

In Dolomite protocol, `transferBetweenAccounts` transfers the collateral from 1 account to another under the same owner. So the owner of both accounts still owns these funds regardless of the account they're deposited in. In `DolomiteConnector`, when calling `transferBetweenAccounts` the protocol isn't updating the holding position of either account.

So when the manager moves the collateral to account ID 1 for example, the protocol doesn't know about the new holding position (which is the position related to account ID 1) and will remain calculating the TVL according to the old holding position (account Id 0), even if the whole amount of account 0 was moved to account 1.

This will cause an inaccurate representation of the Connector's TVL affecting the whole protocol's TVL.

### Proof of Concept

```
    function testDolomiteInvalidHoldingPositions_transferBetweenAccounts() public {
        uint256 marketId = 1;
        uint256 defaultAccountId = 0;
        uint256 accountId = 1;
        uint256 amount = 200e18;

        _dealERC20(DAI, address(connector), amount);

        vm.startPrank(owner);

        // Deposits 200 DAI to Dolomite
        connector.deposit(marketId, amount);

        // TVL is around 200 Base Tokens
        assertEq(accountingManager.TVL() / 1e6, 199);

        // Transfer collateral from account 0 to account 1
        connector.transferBetweenAccounts(accountId, marketId, amount, false);

        // TVL has dropped to 0
        assertEq(accountingManager.TVL(), 0);

        // Connector's account 0 has no markets (no collateral left)
        (uint256[] memory markets,,,) =
            IDolomiteMargin(dolomiteMargin).getAccountBalances(Info(address(connector), defaultAccountId));
        assertEq(markets.length, 0);

        // Connector's account 1 has 1 market (some collateral exists)
        (markets,,,) = IDolomiteMargin(dolomiteMargin).getAccountBalances(Info(address(connector), accountId));
        assertEq(markets.length, 1);
    }
```

### Recommended Mitigation Steps

Add the following at the bottom of `DolomiteConnector::transferBetweenAccounts`:

```
    (uint256[] memory markets0,,,) = dolomiteMargin.getAccountBalances(Info(address(this), 0));
    registry.updateHoldingPosition(
        vaultId,
        registry.calculatePositionId(address(this), DOL_POSITION_ID, ""),
        abi.encode(0),
        "",
        markets0.length == 0
    );

    (uint256[] memory markets1,,,) = dolomiteMargin.getAccountBalances(Info(address(this), accountId));
    registry.updateHoldingPosition(
        vaultId,
        registry.calculatePositionId(address(this), DOL_POSITION_ID, ""),
        abi.encode(accountId),
        "",
        markets1.length == 0
    );
```

This updates the holding positions of both accounts, by either setting or removing the position according to the open markets of each.

**[gzeon (judge) increased severity to High](https://github.com/code-423n4/2024-04-noya-findings/issues/153#issuecomment-2156685924)**

**[HadiEsna (NOYA) confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/153#event-13159494107)**


***

 
# Medium Risk Findings (63)

***Note: full content and discussions can be accessed by viewing each linked submission.***

### [[M-01] Contract does not earn any boosted position rewards in Maverick Connector](https://github.com/code-423n4/2024-04-noya-findings/issues/1561)
*Submitted by [MrPotatoMagic](https://github.com/code-423n4/2024-04-noya-findings/issues/1561), also found by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/1235)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1561#event-12898026136)


***

### [[M-02] Extra rewards are not updated in curve connector when harvestConvexRewards is called](https://github.com/code-423n4/2024-04-noya-findings/issues/1554)
*Submitted by [WinSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1554) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1554+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1554#event-13159514203)


***

### [[M-03] Noya is not compatible with tokens whose balance changes outside of transfers, causing funds to get stuck in the contract](https://github.com/code-423n4/2024-04-noya-findings/issues/1548)
*Submitted by [Audinarey](https://github.com/code-423n4/2024-04-noya-findings/issues/1548) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1548+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor disputed](https://github.com/code-423n4/2024-04-noya-findings/issues/1548#issuecomment-2125348281)


***

### [[M-04] `performanceFeeReceiver` cannot mint any performance fee shares even if TVL is dropped by only a very tiny amount](https://github.com/code-423n4/2024-04-noya-findings/issues/1532)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-noya-findings/issues/1532) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1532+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor disputed](https://github.com/code-423n4/2024-04-noya-findings/issues/1532#issuecomment-2126273561)


***

### [[M-05] `AccountingManager` contract's `previewDeposit`, `previewMint`, `previewWithdraw`, and `previewRedeem` functions are not compliant with EIP-4626 standard](https://github.com/code-423n4/2024-04-noya-findings/issues/1522)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-noya-findings/issues/1522) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1522+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1522#event-13159420450)


***

### [[M-06] `maxDeposit`, `maxMint`, `maxWithdraw`, and `maxRedeem` functions do not return 0 when they should](https://github.com/code-423n4/2024-04-noya-findings/issues/1517)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-noya-findings/issues/1517) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1517+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor acknowledged](https://github.com/code-423n4/2024-04-noya-findings/issues/1517#event-13159416259)


***

### [[M-07] Stale price can be used in `getValueFromChainlinkFeed` function](https://github.com/code-423n4/2024-04-noya-findings/issues/1501)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-noya-findings/issues/1501) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1501+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1501#event-12904454541)


***

### [[M-08] Lack of Slippage Controls in `retrieveTokensForWithdraw` Function](https://github.com/code-423n4/2024-04-noya-findings/issues/1490)
*Submitted by [cheatc0d3](https://github.com/code-423n4/2024-04-noya-findings/issues/1490) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1490+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1490#event-13160141075)


***

### [[M-09] Incorrect modifier condition](https://github.com/code-423n4/2024-04-noya-findings/issues/1488)
*Submitted by [sh1v](https://github.com/code-423n4/2024-04-noya-findings/issues/1488) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1488+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1488#event-12904462570)


***

### [[M-10] First depositor can make subsequent depositor lose all of her or his deposit](https://github.com/code-423n4/2024-04-noya-findings/issues/1473)
*Submitted by [rbserver](https://github.com/code-423n4/2024-04-noya-findings/issues/1473) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1473+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1473#event-13231342528)


***

### [[M-11] `Keepers` does not implement EIP712 correctly on multiple occasions](https://github.com/code-423n4/2024-04-noya-findings/issues/1428)
*Submitted by [TPSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1428) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1428+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1428#event-12904821280)


***

### [[M-12] Chainlink connector doesn’t check for the Min / Max prices returned](https://github.com/code-423n4/2024-04-noya-findings/issues/1415)
*Submitted by [ArsenLupin](https://github.com/code-423n4/2024-04-noya-findings/issues/1415) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1415+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1415#event-12905228048)


***

### [[M-13] Missing calls to `_updateTokenInRegistry` leads to incorrect state of tokens in registry](https://github.com/code-423n4/2024-04-noya-findings/issues/1404)
*Submitted by [honey-k12](https://github.com/code-423n4/2024-04-noya-findings/issues/1404) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1404+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1404#event-12905312020)


***

### [[M-14] In the BalancerConnector, unclaimed rewards are not included in the calculation of the connectors TVL](https://github.com/code-423n4/2024-04-noya-findings/issues/1402)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/1402) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1402+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1402#event-13160135493)


***

### [[M-15] ` PendleConnector::_getPositionTVL` will revert in the current implementation because there is no need to stake the LP tokens anymore ](https://github.com/code-423n4/2024-04-noya-findings/issues/1373)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/1373)*

**Status:** [Sponsor disputed](https://github.com/code-423n4/2024-04-noya-findings/issues/1373#event-13146669276)


***

### [[M-16] `borrowAndSupply()` and `withdraw()` of `FraxConnector` should not be blocked when `maxLTV` of the Frax pair is 0](https://github.com/code-423n4/2024-04-noya-findings/issues/1353)
*Submitted by [KupiaSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1353)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1353#event-13160134144)


***

### [[M-17] Incorrect Return Value in `CompoundConnector.getBorrowBalanceInBase()` Affecting TVL Calculation](https://github.com/code-423n4/2024-04-noya-findings/issues/1352)
*Submitted by [KupiaSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1352) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1352+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1352#event-13146686469)


***

### [[M-18] AccountingManager has no correct implementations of the core ERC-4626 functions `deposit`, `mint`, `withdraw` and `redeem`](https://github.com/code-423n4/2024-04-noya-findings/issues/1334)
*Submitted by [d3e4](https://github.com/code-423n4/2024-04-noya-findings/issues/1334) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1334+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1334#event-13146720244)


***

### [[M-19] Attacker can increase the length of `withdrawQueue` by withdrawing 0 amount of tokens frequently](https://github.com/code-423n4/2024-04-noya-findings/issues/1330)
*Submitted by [Weed0607](https://github.com/code-423n4/2024-04-noya-findings/issues/1330) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1330+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1330#event-12905774327)


***

### [[M-20] `totalAssets()`, and thus `convertToShares()` and `convertToAssets()`, may revert, in violation of ERC-4626](https://github.com/code-423n4/2024-04-noya-findings/issues/1329)
*Submitted by [d3e4](https://github.com/code-423n4/2024-04-noya-findings/issues/1329) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1329+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1329#event-13160123638)


***

### [[M-21] Lack of function to claim reward in `AaveConnector`](https://github.com/code-423n4/2024-04-noya-findings/issues/1321)
*Submitted by [grearlake](https://github.com/code-423n4/2024-04-noya-findings/issues/1321) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1321+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1321#event-13146736531)


***

### [[M-22] In the SNXV3Connector, unclaimed rewards are not included in the calculation of the connectors TVL](https://github.com/code-423n4/2024-04-noya-findings/issues/1319)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/1319)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1319#event-13146740937)


***

### [[M-23] The modifier `onlyExistingRoute` works incorrectly](https://github.com/code-423n4/2024-04-noya-findings/issues/1298)
*Submitted by [Weed0607](https://github.com/code-423n4/2024-04-noya-findings/issues/1298) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1298+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1298#event-12906167537)


***

### [[M-24] The total deposit amount limit in `AccountingManager.sol` can be bypassed](https://github.com/code-423n4/2024-04-noya-findings/issues/1288)
*Submitted by [alexxander](https://github.com/code-423n4/2024-04-noya-findings/issues/1288) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1288+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor acknowledged](https://github.com/code-423n4/2024-04-noya-findings/issues/1288#event-12906227133)


***

### [[M-25] Base tokens accumulated from withdraw fees can't be transferred to/from the NoyaFeeReceiver and will remain stuck](https://github.com/code-423n4/2024-04-noya-findings/issues/1287)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-04-noya-findings/issues/1287), also found by [SBSecurity](https://github.com/code-423n4/2024-04-noya-findings/issues/1020)*

**Status:** [Sponsor disputed](https://github.com/code-423n4/2024-04-noya-findings/issues/1287#event-13146757095)


***

### [[M-26] The `TVLHelper.sol#getTVL` function is DOSed by the `under collateralized connector`, and as a result, many parts of the protocol may be DOS](https://github.com/code-423n4/2024-04-noya-findings/issues/1286)
*Submitted by [FastChecker](https://github.com/code-423n4/2024-04-noya-findings/issues/1286) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1286+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor disputed](https://github.com/code-423n4/2024-04-noya-findings/issues/1286#event-12906268989)


***

### [[M-27] Withdrawals in AccountManager are prone to DOS attacks](https://github.com/code-423n4/2024-04-noya-findings/issues/1278)
*Submitted by [WinSec](https://github.com/code-423n4/2024-04-noya-findings/issues/1278) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1278+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1278#event-12906393558)


***

### [[M-28] LP tokens from Boosted Positions are not included in the TVL calculation of a position held by the MaverickConnector ](https://github.com/code-423n4/2024-04-noya-findings/issues/1263)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/1263) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1263+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1263#event-13146813780)


***

### [[M-29] `_getPositionTVL()` of The StargateConnector doesn't accoount for the total value locked](https://github.com/code-423n4/2024-04-noya-findings/issues/1236)
*Submitted by [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/1236) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1236+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1236#event-13160120059)


***

### [[M-30] CompoundConnector.sol misses unclaimed rewards in getPositionTVL, resulting in undervalued positionTVL/TVL](https://github.com/code-423n4/2024-04-noya-findings/issues/1228)
*Submitted by [oakcobalt](https://github.com/code-423n4/2024-04-noya-findings/issues/1228) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1228+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1228#event-13160174314)


***

### [[M-31] Improper price validation in CompoundConnector.sol will lead to stale prices being used](https://github.com/code-423n4/2024-04-noya-findings/issues/1177)
*Submitted by [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/1177) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1177+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1177#event-12948172725)


***

### [[M-32] `PrismaConnector.sol` should also check health factor in `openTrove()` function](https://github.com/code-423n4/2024-04-noya-findings/issues/1128)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1128), also found by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/207)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1128#event-13231311211)


***

### [[M-33] `FraxConnector.sol#repay` approved amount of tokens does NOT account for latest interest, which may cause DoS while repaying](https://github.com/code-423n4/2024-04-noya-findings/issues/1112)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1112)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1112#event-12906913215)


***

### [[M-34] `CurveConnector.sol#depositIntoConvexBooster` does not keep track of TVL if `stake == false`](https://github.com/code-423n4/2024-04-noya-findings/issues/1110)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1110), also found by [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/228)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1110#event-12906884317)


***

### [[M-35] `AccountingManager#totalWithdrawnAmount` should reflect tokens actually transferred to users, instead of expected transfers](https://github.com/code-423n4/2024-04-noya-findings/issues/1097)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1097) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1097+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1097#event-12907050614)


***

### [[M-36] `veMav` token in `MaverickConnector` does NOT have an existing oracle, so staking Mav would always lead to DoS for TVL calculation](https://github.com/code-423n4/2024-04-noya-findings/issues/1094)
*Submitted by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1094) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1094+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1094#event-12907067812)


***

### [[M-37] `PendleConnector.sol::supply` doesn't pass a valid slippance protection min](https://github.com/code-423n4/2024-04-noya-findings/issues/1018)
*Submitted by [JanuaryPersimmon2024](https://github.com/code-423n4/2024-04-noya-findings/issues/1018) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-1018+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/1018#event-12909642817)


***

### [[M-38] `PendlingConnector::depositIntoMarket()` `PendlingConnector::burnLP()` and  are missing slippage control parameters](https://github.com/code-423n4/2024-04-noya-findings/issues/991)
*Submitted by [ladboy233](https://github.com/code-423n4/2024-04-noya-findings/issues/991) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-991+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/991#event-12909151414)


***

### [[M-39] No function to claim the reward in `PancakeswapConnector`](https://github.com/code-423n4/2024-04-noya-findings/issues/976)
*Submitted by [ladboy233](https://github.com/code-423n4/2024-04-noya-findings/issues/976) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-976+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor disputed](https://github.com/code-423n4/2024-04-noya-findings/issues/976#event-13147627224)


***

### [[M-40] Dust donation might DOS all connectors to create new holding positions, by preventing removing existing holding positions](https://github.com/code-423n4/2024-04-noya-findings/issues/959)
*Submitted by [oakcobalt](https://github.com/code-423n4/2024-04-noya-findings/issues/959) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-959+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/959#event-12910099331)


***

### [[M-41] A malicious user can front-run Morpho repay with a small repay amount making the transaction revert for underflow, DoSing the repay](https://github.com/code-423n4/2024-04-noya-findings/issues/924)
*Submitted by [KYP](https://github.com/code-423n4/2024-04-noya-findings/issues/924)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/924#event-13147685466)


***

### [[M-42] Using the same heartbeat for multiple price feeds](https://github.com/code-423n4/2024-04-noya-findings/issues/917)
*Submitted by [KYP](https://github.com/code-423n4/2024-04-noya-findings/issues/917) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-917+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/917#event-12910191767)


***

### [[M-43] Registry deletes liquidity positions without verifying complete withdrawal](https://github.com/code-423n4/2024-04-noya-findings/issues/856)
*Submitted by [Tigerfrake](https://github.com/code-423n4/2024-04-noya-findings/issues/856), also found by [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/157)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/856#event-13147740083)


***

### [[M-44] `depositQueue.queue` in `AccountingManager` can be flooded causing a DoS](https://github.com/code-423n4/2024-04-noya-findings/issues/854)
*Submitted by [DPS](https://github.com/code-423n4/2024-04-noya-findings/issues/854) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-854+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/854#event-12910614561)


***

### [[M-45] `MorphoBlueConnector:withdraw` withdraws supplied tokens in a market order](https://github.com/code-423n4/2024-04-noya-findings/issues/830)
*Submitted by [joaovwfreire](https://github.com/code-423n4/2024-04-noya-findings/issues/830), also found by [joaovwfreire](https://github.com/code-423n4/2024-04-noya-findings/issues/831)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/830#event-13147772626)


***

### [[M-46] The watchers cannot perform their role and `can't` do anything to intervene during bridging as stated by the docs](https://github.com/code-423n4/2024-04-noya-findings/issues/799)
*Submitted by [SeveritySquad](https://github.com/code-423n4/2024-04-noya-findings/issues/799)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/799#event-12910674030)


***

### [[M-47] The health factor check in `PrismaConnector::adjustTrove` will always pass because the ICR in the Primsma protocol has 20 decimals](https://github.com/code-423n4/2024-04-noya-findings/issues/759)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/759), also found by [ArsenLupin](https://github.com/code-423n4/2024-04-noya-findings/issues/1408)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/759#event-13159458649)


***

### [[M-48] Camelot and Aerodrome Connector TVL susceptible to manipulation attack](https://github.com/code-423n4/2024-04-noya-findings/issues/720)
*Submitted by [said](https://github.com/code-423n4/2024-04-noya-findings/issues/720) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-720+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/720#event-12910431149)


***

### [[M-49] Lack of functionality for `claimFees` calls to the Aerodrome Pool causes the connector to lose its deserved fees](https://github.com/code-423n4/2024-04-noya-findings/issues/712)
*Submitted by [said](https://github.com/code-423n4/2024-04-noya-findings/issues/712), also found by [pkqs90](https://github.com/code-423n4/2024-04-noya-findings/issues/1103)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/712#event-12910407578)


***

### [[M-50] Due to missing health factor and hardcoded balance checks on Dolomite, a borrow position can be opened by withdrawing more than the supplied balance leading to possible unwanted liquidations](https://github.com/code-423n4/2024-04-noya-findings/issues/630)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-04-noya-findings/issues/630) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-630+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/630#event-13159281114)


***

### [[M-51] Balancer flashloan contract can be DOSed completely by sending 1 wei to it](https://github.com/code-423n4/2024-04-noya-findings/issues/602)
*Submitted by [Sentryx](https://github.com/code-423n4/2024-04-noya-findings/issues/602) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-602+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/602#event-12912429440)


***

### [[M-52] Some connectors prevent repayment of a borrow position if it doesn't leave the connector solvent or above `minimumHealthFactor`](https://github.com/code-423n4/2024-04-noya-findings/issues/581)
*Submitted by [Sentryx](https://github.com/code-423n4/2024-04-noya-findings/issues/581) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-581+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/581#event-12912617395)


***

### [[M-53] `setFees` doesn't collect previous fees before changing fee values](https://github.com/code-423n4/2024-04-noya-findings/issues/544)
*Submitted by [SpicyMeatball](https://github.com/code-423n4/2024-04-noya-findings/issues/544) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-544+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor acknowledged](https://github.com/code-423n4/2024-04-noya-findings/issues/544#event-12912705905)


***

### [[M-54] Maverick Connector uses ETH as liquidity for some of the Maverick pools, but NOYA isn't equipped to handle ETH in its vaults without handling conversion to/from WETH in the connector](https://github.com/code-423n4/2024-04-noya-findings/issues/536)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-04-noya-findings/issues/536)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/536#event-12912729944)


***

### [[M-55] In the `AerodromeConnector`, unclaimed rewards are not included in the calculation of the connectors TVL](https://github.com/code-423n4/2024-04-noya-findings/issues/495)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/495) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-495+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/495#event-13159283760)


***

### [[M-56] In the `Gearboxv3` connector the health factor of the account is never considered](https://github.com/code-423n4/2024-04-noya-findings/issues/445)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/445) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-445+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/445#event-13159288810)


***

### [[M-57] Burning sUSD in `SNXV3Connector:: mintOrBurnSUSD` will not work because the sUSD to burn are not deposited into the SNXV3 protocol](https://github.com/code-423n4/2024-04-noya-findings/issues/370)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/370)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/370#event-12948419581)


***

### [[M-58] `SNXV3Connector::_getPositionTVL` only works for collateral with 18 decimals](https://github.com/code-423n4/2024-04-noya-findings/issues/365)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/365)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/365#event-12948442810)


***

### [[M-59] If a curve pool which CurveConnector uses is killed, the vault manager can't close the position, leading to loss of funds](https://github.com/code-423n4/2024-04-noya-findings/issues/340)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-04-noya-findings/issues/340) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-340+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/340#event-12912951050)


***

### [[M-60] FullMath library is missing `unchecked` blocks, leading to DOS protocol's TVL and UniswapValueOracle](https://github.com/code-423n4/2024-04-noya-findings/issues/314)
*Submitted by [0xAlix2](https://github.com/code-423n4/2024-04-noya-findings/issues/314), also found by [ZanyBonzy](https://github.com/code-423n4/2024-04-noya-findings/issues/1183)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/314#event-13159301036)


***

### [[M-61] `lzSend()` forwards all of the contract balance as the native gas fee but the excess won't be always returned](https://github.com/code-423n4/2024-04-noya-findings/issues/276)
*Submitted by [iamandreiski](https://github.com/code-423n4/2024-04-noya-findings/issues/276)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/276#event-12948333811)


***

### [[M-62]  `CurveConnector` will be non-functional on Arbitrum & Polygon due to the improper integration with Convex Boosters on these chains](https://github.com/code-423n4/2024-04-noya-findings/issues/255)
*Submitted by [Bauchibred](https://github.com/code-423n4/2024-04-noya-findings/issues/255) (View additional [reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3Aduplicate-255+is%3Aclosed+-label%3Aunsatisfactory) submitted by other wardens)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/255#event-12948352357)


***

### [[M-63] The check when increasing the `minimumHelthFactor` in the `SiloConnector` is wrong because this variable is used differently in this connector](https://github.com/code-423n4/2024-04-noya-findings/issues/227)
*Submitted by [BenRai](https://github.com/code-423n4/2024-04-noya-findings/issues/227)*

**Status:** [Sponsor confirmed](https://github.com/code-423n4/2024-04-noya-findings/issues/227#event-13159466876)


***

# Low Risk and Non-Critical Issues

For this audit, [23 reports](https://github.com/code-423n4/2024-04-noya-findings/issues?q=is%3Aissue+label%3A%22QA+%28Quality+Assurance%29%22+-label%3Agrade-c) were submitted by wardens detailing low risk and non-critical issues. [This report](https://github.com/code-423n4/2024-04-noya-findings/issues/284) submitted by **Bauchibred** received the top score from the judge.


***

# Disclosures

C4 is an open organization governed by participants in the community.

C4 audits incentivize the discovery of exploits, vulnerabilities, and bugs in smart contracts. Security researchers are rewarded at an increasing rate for finding higher-risk issues. Audit submissions are judged by a knowledgeable security researcher and solidity developer and disclosed to sponsoring developers. C4 does not conduct formal verification regarding the provided code but instead provides final verification.

C4 does not provide any guarantee or warranty regarding the security of this project. All smart contract software should be used at the sole risk and responsibility of users.
