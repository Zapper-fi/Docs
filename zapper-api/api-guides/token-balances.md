---
description: Get an account's Token balances
---

# Token Balances

## Overview

Ensure you have read the [Zapper API ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The token balances endpoint returns an an account's token balances, including contextual information about each token for which the account has a balance.

The `img` property returns the path for the image associated with an asset. For example, this is the path for the ETH image:  `https://zapper.fi/images/networks/ethereum/0xfc1e690f61efd961294b3e1ce3313fbd8aa4f85d.png`

{% api-method method="get" host="https://api.zapper.fi" path="/v1/protocols/tokens/balances" %}
{% api-method-summary %}
Get User Token Balances
{% endapi-method-summary %}

{% api-method-description %}
Returns supported token balances 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="protocol" type="string" required=true %}
The specific protocol to retrieve balances for. In this case **tokens**.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="addresses\[\]" type="array" required=true %}
Array of addresses to query for balance
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from vault-stats endpoint
{% endapi-method-response-example-description %}

```
{
  "0x4c5...": {
    "products": [
      {
        "label": "Tokens",
        "assets": [
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x111111111117dc0aa78b770fa6a738034120c302",
            "symbol": "1INCH",
            "decimals": 18,
            "label": "1INCH",
            "img": "networks/ethereum/0x111111111117dc0aa78b770fa6a738034120c302.png",
            "hide": false,
            "canExchange": false,
            "price": 2.31,
            "balance": 163.70649844792575,
            "balanceRaw": "163706498447925745505",
            "balanceUSD": 378.1620114147085
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xfc1e690f61efd961294b3e1ce3313fbd8aa4f85d",
            "symbol": "aDAI",
            "decimals": 18,
            "label": "aDAI",
            "img": "networks/ethereum/0xfc1e690f61efd961294b3e1ce3313fbd8aa4f85d.png",
            "hide": true,
            "canExchange": false,
            "price": 1,
            "balance": 5.261462092496711,
            "balanceRaw": "5261462092496710734",
            "balanceUSD": 5.261462092496711
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x028171bca77440897b824ca71d1c56cac55b68a3",
            "symbol": "aDAI(v2)",
            "decimals": 18,
            "label": "aDAI(v2)",
            "img": "networks/ethereum/0x028171bca77440897b824ca71d1c56cac55b68a3.png",
            "hide": true,
            "canExchange": false,
            "price": 1,
            "balance": 28.344636483486713,
            "balanceRaw": "28344636483486713708",
            "balanceUSD": 28.344636483486713
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x94d863173ee77439e4292284ff13fad54b3ba182",
            "symbol": "ADEL",
            "decimals": 18,
            "label": "ADEL",
            "img": "networks/ethereum/0x94d863173ee77439e4292284ff13fad54b3ba182.png",
            "hide": false,
            "canExchange": false,
            "price": 0.055492,
            "balance": 16.096597114486205,
            "balanceRaw": "16096597114486205404",
            "balanceUSD": 0.8932323670770684
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x06af07097c9eeb7fd685c692751d5c66db49c215",
            "symbol": "CHAI",
            "decimals": 18,
            "label": "CHAI",
            "img": "networks/ethereum/0x06af07097c9eeb7fd685c692751d5c66db49c215.png",
            "hide": false,
            "canExchange": false,
            "price": 0.939578,
            "balance": 0.95,
            "balanceRaw": "950000000000000000",
            "balanceUSD": 0.8925991
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x0000000000000000000000000000000000000000",
            "symbol": "ETH",
            "decimals": 18,
            "label": "ETH",
            "img": "networks/ethereum/0x0000000000000000000000000000000000000000.png",
            "hide": false,
            "canExchange": false,
            "price": 2115.89,
            "balance": 0.3068941009354365,
            "balanceRaw": "306894100935436523",
            "balanceUSD": 649.3541592282808
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x0954906da0bf32d5479e25f46056d22f08464cab",
            "symbol": "INDEX",
            "decimals": 18,
            "label": "INDEX",
            "img": "networks/ethereum/0x0954906da0bf32d5479e25f46056d22f08464cab.png",
            "hide": false,
            "canExchange": false,
            "price": 25.25,
            "balance": 0.0356169747715949,
            "balanceRaw": "35616974771594899",
            "balanceUSD": 0.8993286129827712
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc12d1c73ee7dc3615ba4e37e4abfdbddfa38907e",
            "symbol": "KICK",
            "decimals": 8,
            "label": "KICK",
            "img": "networks/ethereum/0xc12d1c73ee7dc3615ba4e37e4abfdbddfa38907e.png",
            "hide": true,
            "canExchange": false,
            "price": 0.00015928,
            "balance": 888888,
            "balanceRaw": "88888800000000",
            "balanceUSD": 141.58208064000002
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x8207c1ffc5b6804f6024322ccf34f29c3541ae26",
            "symbol": "OGN",
            "decimals": 18,
            "label": "OGN",
            "img": "networks/ethereum/0x8207c1ffc5b6804f6024322ccf34f29c3541ae26.png",
            "hide": false,
            "canExchange": false,
            "price": 0.562499,
            "balance": 84.2790322915849,
            "balanceRaw": "84279032291584903316",
            "balanceUSD": 47.406871384984214
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x016bf078abcacb987f0589a6d3beadd4316922b0",
            "symbol": "RSPT",
            "decimals": 18,
            "label": "RSPT",
            "img": "networks/ethereum/0x016bf078abcacb987f0589a6d3beadd4316922b0.png",
            "hide": true,
            "canExchange": false,
            "price": 1,
            "balance": 22.583815247840153,
            "balanceRaw": "22583815247840151582",
            "balanceUSD": 22.583815247840153
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc011a73ee8576fb46f5e1c5751ca3b9fe0af2a6f",
            "symbol": "SNX",
            "decimals": 18,
            "label": "SNX",
            "img": "networks/ethereum/0xc011a73ee8576fb46f5e1c5751ca3b9fe0af2a6f.png",
            "hide": true,
            "canExchange": true,
            "price": 11.59,
            "balance": 1.7454545008953846,
            "balanceRaw": "1745454500895384479",
            "balanceUSD": 20.229817665377507
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x57ab1ec28d129707052df4df418d58a2d46d5f51",
            "symbol": "sUSD",
            "decimals": 18,
            "label": "sUSD",
            "img": "networks/ethereum/0x57ab1ec28d129707052df4df418d58a2d46d5f51.png",
            "hide": true,
            "canExchange": true,
            "price": 1,
            "balance": 9.57158463623644,
            "balanceRaw": "9571584636236439516",
            "balanceUSD": 9.57158463623644
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x6b3595068778dd592e39a122f4f5a5cf09c90fe2",
            "symbol": "SUSHI",
            "decimals": 18,
            "label": "SUSHI",
            "img": "networks/ethereum/0x6b3595068778dd592e39a122f4f5a5cf09c90fe2.png",
            "hide": false,
            "canExchange": false,
            "price": 9.14,
            "balance": 0.11955758515172142,
            "balanceRaw": "119557585151721426",
            "balanceUSD": 1.0927563282867339
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc7283b66eb1eb5fb86327f08e1b5816b0720212b",
            "symbol": "TRIBE",
            "decimals": 18,
            "label": "TRIBE",
            "img": "networks/ethereum/0xc7283b66eb1eb5fb86327f08e1b5816b0720212b.png",
            "hide": false,
            "canExchange": false,
            "price": 0.8806782832571027,
            "balance": 18.473662456065284,
            "balanceRaw": "18473662456065283997",
            "balanceUSD": 16.269353337278766
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
            "symbol": "USDC",
            "decimals": 6,
            "label": "USDC",
            "img": "networks/ethereum/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48.png",
            "hide": false,
            "canExchange": false,
            "price": 1,
            "balance": 5.83847,
            "balanceRaw": "5838470",
            "balanceUSD": 5.83847
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x49e833337ece7afe375e44f4e3e8481029218e5c",
            "symbol": "VALUE",
            "decimals": 18,
            "label": "VALUE",
            "img": "networks/ethereum/0x49e833337ece7afe375e44f4e3e8481029218e5c.png",
            "hide": false,
            "canExchange": false,
            "price": 1.38,
            "balance": 1.172452121629855,
            "balanceRaw": "1172452121629854933",
            "balanceUSD": 1.6179839278491996
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
            "symbol": "WETH",
            "decimals": 18,
            "label": "WETH",
            "img": "networks/ethereum/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
            "hide": false,
            "canExchange": false,
            "price": 2110.45,
            "balance": 0.00228556661504051,
            "balanceRaw": "2285566615040510",
            "balanceUSD": 4.823574062712244
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x0bc529c00c6401aef6d220be8c6ea1667f6ad93e",
            "symbol": "YFI",
            "decimals": 18,
            "label": "YFI",
            "img": "networks/ethereum/0x0bc529c00c6401aef6d220be8c6ea1667f6ad93e.png",
            "hide": false,
            "canExchange": false,
            "price": 32448,
            "balance": 0.0001,
            "balanceRaw": "100000000000000",
            "balanceUSD": 3.2448
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x837010619aeb2ae24141605afc8f66577f6fb2e7",
            "symbol": "zHEGIC",
            "decimals": 18,
            "label": "zHEGIC",
            "img": "networks/ethereum/0x837010619aeb2ae24141605afc8f66577f6fb2e7.png",
            "hide": false,
            "canExchange": false,
            "price": 0.12899,
            "balance": 0.13794102610655187,
            "balanceRaw": "137941026106551864",
            "balanceUSD": 0.017793012957484124
          }
        ],
        "meta": []
      }
    ],
    "meta": [
      {
        "label": "Total",
        "value": 1338.0863295425552,
        "type": "dollar"
      },
      {
        "label": "Assets",
        "value": 1338.0863295425552,
        "type": "dollar"
      },
      {
        "label": "Debt",
        "value": 0,
        "type": "dollar"
      }
    ]
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error response from vault-stats endpoint
{% endapi-method-response-example-description %}

```
{
  "statusCode": 400,
  "message": [
    "A helpful error message"
  ],
  "error": "Bad Request"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



