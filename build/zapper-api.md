---
description: API Reference
---

# Zapper API

## Zapper API

The Data and Transactions APIs are free for the community using a shared public use [API key](zapper-api.md#authentication). 

For any API related inquiries, please reach out to the team on [Twitter](https://twitter.com/zapper_fi) or [Discord](https://discordapp.com/invite/h6CGbuN).

If your project consumes the Zapper API, a mention that your app is "**Powered by Zapper**" with a backlink to [https://zapper.fi](https://zapper.fi/dashboard) would be appreciated!

### Data API

The Zapper Developer APIs provide the Ethereum community with accessible and consistent DeFi data for an ever increasing number of protocols. For a full list of supported protocols, see [https://zapper.fi/protocols](https://zapper.fi/protocols). Check out the [guides](guides/#data-api) section to see how to query account balances, pool stats, and more.

### Transactions API

The Zapper Transactions API is the easiest way for builders to interact directly with a wide range of DeFi protocols through Zapper. Get an easy to consume transaction for approving, adding, removing, and rebalancing liquidity through any of our [zaps](smart-contracts.md).

This API returns a transaction object which includes all of the contextual data needed to be consumed by [Web3](https://web3js.readthedocs.io/en/v1.2.0/web3-eth.html#sendtransaction), Ethers or other Smart Contracts. This enables anyone to assemble and execute a complex Zap including multi exchange hops and interacting with several DeFi protocols in a single atomic transaction. To learn more, check out the [guides](guides/) section.

## Authentication

The Zapper API uses [API Keys](https://swagger.io/docs/specification/authentication/api-keys/) to authenticate requests. Zapper has made available for public use the following API key `api_key=96e0cc51-a62e-42ca-acee-910ea7d2a241`

The API key must be provided as a query string by the client when making API calls.

## Swagger

The Swagger UI contains an overview of the available endpoints. Be creative and feel free to reach out to us with suggestions or to show us what you've built.

{% embed url="http://api.zapper.fi/api/static/index.html" %}

## 

