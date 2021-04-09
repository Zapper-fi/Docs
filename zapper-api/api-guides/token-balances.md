---
description: Get an account's Token balances
---

# Token Balances

## Overview

Ensure you have read the [Zapper API ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The token balances endpoint returns an an account's token balances, including contextual information about each token for which the account has a balance.

{% api-method method="get" host="https://api.zapper.fi/v1/balances/tokens?addresses\[\]=address&api\_key=" path="api\_key" %}
{% api-method-summary %}
Get User Token Balances
{% endapi-method-summary %}

{% api-method-description %}
Returns Zapper's supported tokens
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
  "0x3b2...": [
    {
      "address": "0xba100000625a3754423978a60c9317c58a424e3d",
      "tokenAddress": "0xba100000625a3754423978a60c9317c58a424e3d",
      "decimals": 18,
      "img": "BAL-icon.png",
      "label": "BAL",
      "symbol": "BAL",
      "balance": 0.020191614617267317,
      "balanceRaw": "20191614617267316",
      "balanceUSD": 0.9411311573108296,
      "price": 46.61,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0xc00e94cb662c3520282e6f5717214004a7f26888",
      "tokenAddress": "0xc00e94cb662c3520282e6f5717214004a7f26888",
      "decimals": 18,
      "img": "COMP-icon.png",
      "label": "COMP",
      "symbol": "COMP",
      "balance": 0.10125296154657497,
      "balanceRaw": "101252961546574972",
      "balanceUSD": 47.01681269415209,
      "price": 464.35,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x0000000000000000000000000000000000000000",
      "tokenAddress": "0x0000000000000000000000000000000000000000",
      "decimals": 18,
      "img": "ETH-icon.png",
      "label": "ETH",
      "symbol": "ETH",
      "balance": 2.070389284731874,
      "balanceRaw": "2070389284731874038",
      "balanceUSD": 3765.1892493205387,
      "price": 1818.59,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x4e15361fd6b4bb609fa63c81a2be19d873717870",
      "tokenAddress": "0x4e15361fd6b4bb609fa63c81a2be19d873717870",
      "decimals": 18,
      "img": "FTM-icon.png",
      "label": "FTM",
      "symbol": "FTM",
      "balance": 20679.449388200468,
      "balanceRaw": "20679449388200468654641",
      "balanceUSD": 9035.327065040714,
      "price": 0.436923,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x429881672b9ae42b8eba0e26cd9c73711b891ca5",
      "tokenAddress": "0x429881672b9ae42b8eba0e26cd9c73711b891ca5",
      "decimals": 18,
      "img": "PICKLE-icon.png",
      "label": "PICKLE",
      "symbol": "PICKLE",
      "balance": 0.32549746636350163,
      "balanceRaw": "325497466363501653",
      "balanceUSD": 3.362388827534972,
      "price": 10.33,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x04fa0d235c4abf4bcf4787af4cf447de572ef828",
      "tokenAddress": "0x04fa0d235c4abf4bcf4787af4cf447de572ef828",
      "decimals": 18,
      "img": "UMA-icon.png",
      "label": "UMA",
      "symbol": "UMA",
      "balance": 10.536590952142477,
      "balanceRaw": "10536590952142476922",
      "balanceUSD": 251.61379193716235,
      "price": 23.88,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
      "tokenAddress": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
      "decimals": 18,
      "img": "WETH-icon.png",
      "label": "WETH",
      "symbol": "WETH",
      "balance": 3.9558141278189054,
      "balanceRaw": "3955814127818905530",
      "balanceUSD": 7184.945200357478,
      "price": 1816.3,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x45f24baeef268bb6d63aee5129015d69702bcdfa",
      "tokenAddress": "0x45f24baeef268bb6d63aee5129015d69702bcdfa",
      "decimals": 18,
      "img": "YFV-icon.png",
      "label": "YFV",
      "symbol": "YFV",
      "balance": 0.4107985906240419,
      "balanceRaw": "410798590624041889",
      "balanceUSD": 1.8527016437144288,
      "price": 4.51,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x67b66c99d3eb37fa76aa3ed1ff33e8e39f0b9c7a",
      "tokenAddress": "0x67b66c99d3eb37fa76aa3ed1ff33e8e39f0b9c7a",
      "decimals": 18,
      "img": "ibETHv1-icon.png",
      "label": "ibETHv1",
      "symbol": "ibETHv1",
      "balance": 2.975853996364994,
      "balanceRaw": "2975853996364994053",
      "balanceUSD": 5668.003202625356,
      "price": 1904.664412148184,
      "isStaked": false,
      "hide": true,
      "canExchange": false
    },
    {
      "address": "0x8798249c2e607446efb7ad49ec89dd1865ff4272",
      "tokenAddress": "0x8798249c2e607446efb7ad49ec89dd1865ff4272",
      "decimals": 18,
      "img": "xSUSHI-icon.png",
      "label": "xSUSHI",
      "symbol": "xSUSHI",
      "balance": 2484.572020189006,
      "balanceRaw": "2484572020189005888321",
      "balanceUSD": 53895.182852831174,
      "price": 21.691938255318224,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    },
    {
      "address": "0x837010619aeb2ae24141605afc8f66577f6fb2e7",
      "tokenAddress": "0x837010619aeb2ae24141605afc8f66577f6fb2e7",
      "decimals": 18,
      "img": "zHEGIC-icon.png",
      "label": "zHEGIC",
      "symbol": "zHEGIC",
      "balance": 225.75392231890183,
      "balanceRaw": "225753922318901839992",
      "balanceUSD": 59.59519767551067,
      "price": 0.263983,
      "isStaked": false,
      "hide": false,
      "canExchange": false
    }
  ]
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



