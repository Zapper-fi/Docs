---
description: This section contains helpful guides for interacting with Zapper APIs.
---

# Guides

If you'd like to contribute a guide, please reach out to us on [Discord](https://discord.com/invite/5C4wxPr) or [Twitter](https://twitter.com/zapper_fi)

## Transactions API

Assembling a Zap transaction is simple to do with the Transactions API. Provide basic details like the token to sell, pool or vault to interact with, and token quantities to send and the API will assemble and return an easy to consume Zap transaction for you to use in apps or smart contracts. 

The same patterns shown in these guides can be applied to all of the [zaps](../smart-contracts.md) offered by Zapper

* The [Yearn Zap In guide](yearn-zap-in.md) demonstrates how to create an easy to consume transaction object for interacting with Zaps with web3 or in your smart contracts directly.
* The [Sushiswap Zap Out guide](create-uniswapv2-zap-out.md) goes over how to create and consume a transaction object to enable one click Zap Outs from Sushiswap into ETH or any arbitrary token

## Data API

### Pool/Vault Stats and Account Balances

The same patterns shown here can be used for any of Zapper's [supported platforms](https://zapper.fi/protocols).

* The Yearn [Vault Stats guide](yearn-vault-stats.md) shows you how to pull data from the Zapper Data API. Vault stats includes platforms whose deposits are used for automated farming strategies \(e.g. Yearn, Harvest, Pickle, etc.\)
* The [Sushiswap Pool Stats guide ](sushiswap-pool-stats.md)shows you how to get pool data from the Zapper Data API. Pool stats includes platforms whose deposits are pooled as liquidity for exchanges \(e.g. Sushiswap, Uniswap, Balancer, etc.\)
* Fetching user balances for Zapper's supported platforms is also possible. Check out the [Curve User Balances Guide](curve-user-balances.md) or the [Yearn User Balances guide](yearn-user-balances.md) for an examples.

### Tokens, Gas Prices, Misc

* The [Token Balances API](get-user-token-balances.md) returns a list of tokens for which the account has a balance.
* The [Prices API](get-supported-tokens-and-prices.md) returns an easy to consume list of Zapper's supported tokens and their USD prices.
* The [Gas Price API](get-gas-price.md) returns Zapper's current gas prices.



