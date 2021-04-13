---
description: >-
  Zaps = Smart Contracts combining multiple on-chain actions to make DeFi easy
  to use
---

# Smart Contracts

## Mainnet

{% tabs %}
{% tab title="Production" %}
These contracts are currently deployed on various EVM Mainnets and are used by [Zapper.fi](https://zapper.fi/) and other DeFi projects. The recommended way to interact with these contracts is via the [Transactions API](../zapper-api/api-guides/#transactions-api).

| Contract | Address | Version | Chain |
| :--- | :--- | :--- | :--- |
| Uniswap V2 Add | [0x5ACedBA6C402e2682D312a7b4982eda0Ccf2d2E3](https://etherscan.io/address/0x5ACedBA6C402e2682D312a7b4982eda0Ccf2d2E3) | 4.0 | Ethereum |
| Uniswap V2 Remove | [0x69090d6968B12b79CD403Ee33E871284dC7E92F6](https://etherscan.io/address/0x69090d6968b12b79cd403ee33e871284dc7e92f6) | 3.0.1 | Ethereum |
| Uniswap V2 Pool Pipe | [0xBdcd4Dcc79bA2C4088323ca94F443a05A23cA372](https://etherscan.io/address/0xBdcd4Dcc79bA2C4088323ca94F443a05A23cA372) | 1.1 | Ethereum |
| Uniswap V1 Remove | [0x5e6531d99e9099cb3936c048daf6ba0b3f79b9e2](https://etherscan.io/address/0x5e6531d99e9099cb3936c048daf6ba0b3f79b9e2) | 2.0 | Ethereum |
| Uniswap V2 to Balancer Pool Pipe | [0xA3149708cb9D9BD31CB5c8F5c107D94395B7bA64](https://etherscan.io/address/0xA3149708cb9D9BD31CB5c8F5c107D94395B7bA64) | 1.4 | Ethereum |
| Balancer Add | [0x7F249DBD212158e1ac449f0A37CA956C8186ac80](https://etherscan.io/address/0x7F249DBD212158e1ac449f0A37CA956C8186ac80) | 3.0 | Ethereum |
| Balancer Remove | [0x00d0f137b51692D0AC708bdE7b367a373865cFfe](https://etherscan.io/address/0x00d0f137b51692D0AC708bdE7b367a373865cFfe) | 2.2 | Ethereum |
| Curve Add | [0x77eD360E62cA6f2D1582F00da8B0b8489cA1e2E2](https://etherscan.io/address/0x77ed360e62ca6f2d1582f00da8b0b8489ca1e2e2) | 3.1 | Ethereum |
| Curve Remove | [0x47c964e8d93843ab0c185bdeab5cbf57b9ec613a](https://etherscan.io/address/0x47c964e8d93843ab0c185bdeab5cbf57b9ec613a) | 3.0.1 | Ethereum |
| Curve to Curve Pool Pipe | [0xB54dCe7f4Bd17DFebe4CB9742AE2D7d2886134d8](https://etherscan.io/address/0xB54dCe7f4Bd17DFebe4CB9742AE2D7d2886134d8) | 1.0 | Ethereum |
| Yearn yVault Add or Remove | [0xB0880df8420974ef1b040111e5e0e95f05F8fee1](https://etherscan.io/address/0xB0880df8420974ef1b040111e5e0e95f05F8fee1) | 1.5 | Ethereum |
| Yearn yVault Add | [0x462991D18666c578F787e9eC0A74Cd18D2971E5F](https://etherscan.io/address/0x462991d18666c578f787e9ec0a74cd18d2971e5f) | 2.0.1 | Ethereum |
| Sushiswap Add | [0xcff6eF0B9916682B37D80c19cFF8949bc1886bC2](https://etherscan.io/address/0xcff6eF0B9916682B37D80c19cFF8949bc1886bC2) | 3.0 | Ethereum |
| Sushiswap Remove | [0x3351be9654188571a3e32388DA582947928111Ce](https://etherscan.io/address/0x3351be9654188571a3e32388da582947928111ce) | 2.0 | Ethereum |
| Bancor Add | [0xa14EEefa753a166a5651bce7B84094f614Df0D05](https://etherscan.io/address/0xa14EEefa753a166a5651bce7B84094f614Df0D05) | 2.1 | Ethereum |
| Harvest Add | [0xab297faf67D486c8d03fBcD8F026feD0D71254B9](https://etherscan.io/address/0xab297faf67D486c8d03fBcD8F026feD0D71254B9) | 1.0 | Ethereum |
| PoolTogether Add | [0x2e61170a7dCab6438e403AA7A8A7143d39ED0A65](https://etherscan.io/address/0x2e61170a7dCab6438e403AA7A8A7143d39ED0A65) | 1.0 | Ethereum |
| Ethereum to Polygon Bridge | [0x1f0d1927498FBD4f9E8558704Ce5B658929527Ec](https://etherscan.io/address/0x1f0d1927498fbd4f9e8558704ce5b658929527ec) | 1.2 | Ethereum |
| Polygon to Ethereum Bridge | [0x5848E3A0eC02cEd206292ae6504E03c4aD97BF76](https://explorer-mainnet.maticvigil.com/address/0x5848E3A0eC02cEd206292ae6504E03c4aD97BF76/transactions) | 1.0 | Polygon\* |
| QuickSwap Add | [0x5CCb8c39bF68612C7997Cbc498ae55908D32d223](https://explorer-mainnet.maticvigil.com/address/0x5CCb8c39bF68612C7997Cbc498ae55908D32d223/transactions) | 1.0 | Polygon\* |
| PancakeSwap Add | [0xbA62b2E64A91623293a78B5244b3950fC0398deE](https://bscscan.com/address/0xbA62b2E64A91623293a78B5244b3950fC0398deE) | 2.0 | BSC\*\* |
| PancakeSwap Remove | [0x343E3a490c9251dC0eaA81Da146ba6ABe6C78b2d](https://bscscan.com/address/0x343e3a490c9251dc0eaa81da146ba6abe6c78b2d) | 1.0 | BSC\*\* |
| 1Inch Add | [0x5531b2eAA05D8b6fb855E15F1d21e6a3A3794B4d](https://etherscan.io/address/0x5531b2eAA05D8b6fb855E15F1d21e6a3A3794B4d#code) | 1.0 | Ethereum |
| Pickle Add | [0xc695f73c1862e050059367B2E64489E66c525983](https://etherscan.io/address/0xc695f73c1862e050059367b2e64489e66c525983) | 1.0 | Ethereum |
{% endtab %}

{% tab title="Deprecated" %}
Deprecated contracts are no longer in use by Zapper but are still available for use by the public as is. Contracts are deprecated due to improvements being made to the core logic, swap mechanics, or for gas efficiency purposes. You are encouraged to use the Zaps listed in Production instead of these.

| Contract | Address | Version | Chain |
| :--- | :--- | :--- | :--- |
| Zapper Swap | [0xacDF47C844Eff0Ecb218D8945e28A9A484aF8D07](https://etherscan.io/address/0xacDF47C844Eff0Ecb218D8945e28A9A484aF8D07) | 1.3 | Ethereum |
| Curve Add | [0x79c88866247a3626D45011662eFA093535554B34](https://etherscan.io/address/0x79c88866247a3626D45011662eFA093535554B34) | 2.0.1 | Ethereum |
| Curve Remove | [0xA3061Cf6aC1423c6F40917AD49602cBA187181Dc](https://etherscan.io/address/0xA3061Cf6aC1423c6F40917AD49602cBA187181Dc) | 2.1 | Ethereum |
| Uniswap V2 Add | [0xD3cF4e98e1e432B3d6Ae42AE406A78F2AC8293D0](https://etherscan.io/address/0xD3cF4e98e1e432B3d6Ae42AE406A78F2AC8293D0) | 3.0.1 | Ethereum |
| Uniswap V2 Remove | [0x79B6C6F8634ea477ED725eC23b7b6Fcb41F00E58](https://etherscan.io/address/0x79B6C6F8634ea477ED725eC23b7b6Fcb41F00E58) | 2.1 | Ethereum |
| Sushiswap Add | [0x91baf383abc0c332a69a73041c866f6761a90b3c](https://etherscan.io/address/0x91baf383abc0c332a69a73041c866f6761a90b3c) | 2.0.1 | Ethereum |
| Sushiswap Remove | [0xa4E4BeAA9d27EabB6a5E010565A21D93a723c7e1](https://etherscan.io/address/0xa4E4BeAA9d27EabB6a5E010565A21D93a723c7e1) | 1.1 | Ethereum |
| Uniswap V2 Remove | [0x05448acd708B78791d007Bc1e037EA6FE78283A6](https://etherscan.io/address/0x05448acd708B78791d007Bc1e037EA6FE78283A6) | 3.0 | Ethereum |
| Uniswap V2 Remove | [0x79B6C6F8634ea477ED725eC23b7b6Fcb41F00E58](https://etherscan.io/address/0x79B6C6F8634ea477ED725eC23b7b6Fcb41F00E58) | 2.1 | Ethereum |
| Curve Add | [0x75987EB3cB933E355474c5ffC4905ECB6061796b](https://etherscan.io/address/0x75987EB3cB933E355474c5ffC4905ECB6061796b) | 3.0 | Ethereum |
| Yearn Vault Add | [0xb832Cc0E8Ed40Ae42edDC63D9d07EbAF022994E8](https://etherscan.io/address/0xb832Cc0E8Ed40Ae42edDC63D9d07EbAF022994E8) | 2.0 | Ethereum |
| Pancakeswap Add | [0x775EE938186FddC13bD7C89D24820E1b0758F91D](https://bscscan.com/address/0x775ee938186fddc13bd7c89d24820e1b0758f91d#code) | 1.0 | BSC\*\* |
{% endtab %}
{% endtabs %}

Polygon\* = Matic  
BSC\*\* = Binance Smart Chain  




