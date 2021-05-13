---
description: Get an account's Curve balances
---

# Protocol Balances

## Overview

Ensure you have read the [Zapper API Overview ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API. 

{% hint style="info" %}
You can directly test out the protocol balances endpoint [**here**](https://api.zapper.fi/api/static/index.html#/default/BalanceController_getProtocolBalances).
{% endhint %}

### Curve Balances

The Curve balances endpoint returns an account's balance data for all of Zapper's supported Curve pools. The returned data includes raw, USD, and underlying token balances of an account, in addition to contextual information about each pool for which the account has a balance. This endpoint is useful to query account balances for pools in Curve's ecosystem.

{% api-method method="get" host="https://api.zapper.fi" path="/v1/protocols/curve/balances" %}
{% api-method-summary %}
Get Curve Balances
{% endapi-method-summary %}

{% api-method-description %}
Returns balance data for Curve pools 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="protocol" type="string" required=true %}
The specific protocol to get balances for. In this case **Curve**
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="addresses\[\]" type="string" required=true %}
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
  "0xb1a...": {
    "products": [
      {
        "label": "Curve",
        "assets": [
          {
            "type": "pool",
            "category": "pool",
            "address": "0x3b3ac5386837dc563660fb6a0937dfaa5924333b",
            "decimals": 18,
            "label": "BUSD",
            "symbol": "BUSD",
            "share": 2.733268612429166e-7,
            "supply": 58686684.43771173,
            "tokens": [
              {
                "decimals": 18,
                "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
                "symbol": "DAI",
                "balance": 3.525232950015166,
                "balanceUSD": 3.4663439335851627,
                "reserve": 12897499.11144719,
                "price": 0.983295
              },
              {
                "decimals": 6,
                "address": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
                "symbol": "USDC",
                "balance": 4.698445147973828,
                "balanceUSD": 4.667660935364304,
                "reserve": 17189840.495765,
                "price": 0.993448
              },
              {
                "decimals": 6,
                "address": "0xdac17f958d2ee523a2206206994597c13d831ec7",
                "symbol": "USDT",
                "balance": 3.6609429114733385,
                "balanceUSD": 3.6235244139751694,
                "reserve": 13394010.727031,
                "price": 0.989779
              },
              {
                "decimals": 18,
                "address": "0x4fabb145d64652a948d72533023f6e7a623c7c53",
                "symbol": "BUSD",
                "balance": 4.784708349311653,
                "balanceUSD": 4.751459410992286,
                "reserve": 17505445.046834566,
                "price": 0.993051
              }
            ],
            "protocol": "curve",
            "protocolSymbol": "Curve",
            "protocolDisplay": "Curve",
            "price": 1.1000502438824038,
            "balance": 16.040647254113267,
            "balanceRaw": "16040647254113267158",
            "balanceUSD": 16.508988693916923
          },
          {
            "type": "pool",
            "category": "pool",
            "address": "0x02d341ccb60faaf662bc0554d13778015d1b285c",
            "decimals": 18,
            "label": "sAAVE",
            "symbol": "sAAVE",
            "share": 0.000008643510065527967,
            "supply": 21250428.326960705,
            "tokens": [
              {
                "decimals": 18,
                "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
                "symbol": "DAI",
                "balance": 145.6124501753291,
                "balanceUSD": 143.17999419515021,
                "reserve": 16846448.846755028,
                "price": 0.983295
              },
              {
                "decimals": 18,
                "address": "0x57ab1ec28d129707052df4df418d58a2d46d5f51",
                "symbol": "sUSD",
                "balance": 44.013938567751055,
                "balanceUSD": 44.454077953428566,
                "reserve": 5092137.133418445,
                "price": 1.01
              }
            ],
            "protocol": "curve",
            "protocolSymbol": "Curve",
            "protocolDisplay": "Curve",
            "price": 1.026851565402617,
            "balance": 183.67829114086547,
            "balanceRaw": "183678291140865471191",
            "balanceUSD": 187.63407214857878
          },
          {
            "type": "pool",
            "category": "pool",
            "address": "0xd2967f45c4f384deea880f807be904762a3dea07",
            "decimals": 18,
            "label": "GUSD",
            "symbol": "GUSD",
            "share": 0.0000074471106833135844,
            "supply": 87634608.23650196,
            "tokens": [
              {
                "decimals": 2,
                "address": "0x056fd409e1d7a124bd7017459dfea2f387b6d5cd",
                "symbol": "GUSD",
                "balance": 321.8520051985404,
                "balanceUSD": 311.16651862594887,
                "reserve": 43218372.72,
                "price": 0.9668
              },
              {
                "decimals": 18,
                "address": "0x6c3f90f043a72fa612cbac8115ee7e52bde6e490",
                "symbol": "3CRV",
                "balance": 335.94138837888687,
                "balanceUSD": 337.64913571022237,
                "reserve": 45110298.83463611,
                "price": 1.0050834681001242
              }
            ],
            "protocol": "curve",
            "protocolSymbol": "Curve",
            "protocolDisplay": "Curve",
            "price": 1.0020787702024336,
            "balance": 652.6246272260544,
            "balanceRaw": "652624627226054336269",
            "balanceUSD": 648.8156543361713
          }
        ],
        "meta": []
      }
    ],
    "meta": [
      {
        "label": "Total",
        "value": 852.958715178667,
        "type": "dollar"
      },
      {
        "label": "Assets",
        "value": 852.958715178667,
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

