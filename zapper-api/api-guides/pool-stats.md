---
description: Get Pool data for all of Zapper's supported Sushiswap Pools
---

# Pool Stats

## Overview

Ensure you have read the [Zapper API ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The Sushiswap pool stats endpoint returns contextual data for all of Zapper's supported Sushiswap pools. The returned data includes information such as each pool's address, liquidity, total supply, USD price, underlying tokens, and more. This endpoint is useful to query statistics about the pools in Sushiswap's ecosystem or to use the returned data \(like the address property\) as parameters in the Transactions API as shown [here](zap-in.md#zap-in).

{% api-method method="get" host="https://api.zapper.fi/v1/pool-stats/sushiswap?api\_key=" path="api\_key" %}
{% api-method-summary %}
Get Sushiswap Pool Stats
{% endapi-method-summary %}

{% api-method-description %}
Returns pool stats data for Sushiswap pools.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Whether the cake should be gluten-free or not.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from vault-stats endpoint
{% endapi-method-response-example-description %}

```
[
  {
    "address": "0xceff51756c56ceffca006cd410b03ffc46dd3a58",
    "decimals": 18,
    "value": "WBTC / ETH",
    "label": "WBTC / ETH",
    "symbol": "WBTC / ETH",
    "contractAddress": "0xceff51756c56ceffca006cd410b03ffc46dd3a58",
    "exchangeAddress": "0xceff51756c56ceffca006cd410b03ffc46dd3a58",
    "tokenAddress": "0xceff51756c56ceffca006cd410b03ffc46dd3a58",
    "tokens": [
      {
        "address": "0x2260fac5e5542a773aa44fbcfedf7c193bc2c599",
        "decimals": 8,
        "price": 50693,
        "reserve": 8741.42459664,
        "symbol": "WBTC",
        "hide": false,
        "hideFromExplore": false
      },
      {
        "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
        "decimals": 18,
        "price": 1662.01,
        "reserve": 265809.06835221,
        "symbol": "WETH",
        "hide": false,
        "hideFromExplore": false
      }
    ],
    "protocol": "sushiswap",
    "protocolSymbol": "SUSHI",
    "protocolDisplay": "SushiSwap",
    "liquidity": 884906366.769528,
    "volume": 39273930.86863661,
    "volumeChangePercentage": 0.009623654778511664,
    "volliq": 0.04438201864453917,
    "feeVolume": 117821.79260590982,
    "fee": 0.003,
    "dailyROI": 0.0001331460559336175,
    "weeklyROI": 0.0009320223915353224,
    "supply": 0.0202664809417539,
    "pricePerToken": 43663543232.43187,
    "price0": 50693,
    "price1": 1662.01,
    "isBlocked": false,
    "hideFromExplore": false,
    "yearlyROI": 0.04846516435983676
  },
]
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



