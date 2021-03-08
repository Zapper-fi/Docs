---
description: Get an account's Curve balances
---

# Curve User Balances

## Overview

Ensure you have read the [Zapper API ](../zapper-api.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The Curve balances endpoint returns an account's balance data for all of Zapper's supported Curve pools. The returned data includes raw, USD, and underlying token balances of an account, in addition to contextual information about each pool for which the account has a balance. This endpoint is useful to query account balances for pools in Curve's ecosystem.

{% api-method method="get" host="https://api.zapper.fi/v1/balances/curve?api\_key=" path="api\_key" %}
{% api-method-summary %}
Get Curve Balances
{% endapi-method-summary %}

{% api-method-description %}
Returns balance data for Curve pools
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="addresses\[\]" type="string" required=false %}
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
[
  {
    "0x0f3d8...": [
      {
        "label": "Y",
        "value": "Y",
        "protocol": "curve",
        "protocolDisplay": "Curve",
        "protocolSymbol": "Curve",
        "decimals": 18,
        "address": "0x45f783cce6b7ff23b2ab2d70e416cdb7d6055f51",
        "tokenAddress": "0xdf5e0e81dff6faf3a7e52ba697820c5e32d806a8",
        "exchangeAddress": "0xbBC81d23Ea2c3ec7e56D39296F0cbB648873a5d3",
        "contractAddress": "0xbBC81d23Ea2c3ec7e56D39296F0cbB648873a5d3",
        "depositAddress": "0xbBC81d23Ea2c3ec7e56D39296F0cbB648873a5d3",
        "liquidity": 109173781.18907443,
        "pricePerToken": 1.0870200143431872,
        "volume": 11876799.256408438,
        "feeVolume": 4750.719702563376,
        "fee": 0.0004,
        "volliq": 0.10878801784688034,
        "isBlocked": false,
        "isBtc": false,
        "tokens": [
          {
            "symbol": "DAI",
            "underlyingSymbol": "DAI",
            "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
            "underlyingAddress": "0x6b175474e89094c44da98b954eedeac495271d0f",
            "decimals": 18,
            "price": 1,
            "reserve": 18742274.19950344,
            "reserveUSD": 18742274.19950344,
            "balance": 25.422828781434415,
            "balanceUSD": 25.422828781434415
          },
          {
            "symbol": "USDC",
            "underlyingSymbol": "USDC",
            "address": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
            "underlyingAddress": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
            "decimals": 6,
            "price": 1,
            "reserve": 23075557.40143123,
            "reserveUSD": 23075557.40143123,
            "balance": 31.300680942352795,
            "balanceUSD": 31.300680942352795
          },
          {
            "symbol": "USDT",
            "underlyingSymbol": "USDT",
            "address": "0xdac17f958d2ee523a2206206994597c13d831ec7",
            "underlyingAddress": "0xdac17f958d2ee523a2206206994597c13d831ec7",
            "decimals": 6,
            "price": 1,
            "reserve": 28059478.218709864,
            "reserveUSD": 28059478.218709864,
            "balance": 38.06108601642104,
            "balanceUSD": 38.06108601642104
          },
          {
            "symbol": "TUSD",
            "underlyingSymbol": "TUSD",
            "address": "0x0000000000085d4780b73119b644ae5ecd22b376",
            "underlyingAddress": "0x0000000000085d4780b73119b644ae5ecd22b376",
            "decimals": 18,
            "price": 1,
            "reserve": 39309247.53250009,
            "reserveUSD": 39309247.53250009,
            "balance": 53.32075813789182,
            "balanceUSD": 53.32075813789182
          }
        ],
        "supply": 100434012.02234603,
        "dailyROI": 0.00004351520713875214,
        "weeklyROI": 0.00030460644997126496,
        "yearlyROI": 0.01583953539850578,
        "symbol": "Y",
        "name": "Y",
        "gaugeAddress": "0xfa712ee4788c042e2b7bb55e6cb8ec569c4530c1",
        "proxyAddress": "0xbBC81d23Ea2c3ec7e56D39296F0cbB648873a5d3",
        "share": 0.0000013564431141503612,
        "balance": 136.23302403420587,
        "balanceRaw": "136233024034205869544",
        "balanceUSD": 148.10535387810006
      }
    ]
  }
  {Subsequent Balances...},
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



