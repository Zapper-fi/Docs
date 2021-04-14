---
description: Get an account's Curve balances
---

# Protocol Balances

## Overview

Ensure you have read the [Zapper API Overview ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API. In addition, you can directly test out the protocol balances endpoint [here](https://api.zapper.fi/api/static/index.html#/default/BalanceController_getProtocolBalances).

### Curve Balances

The Curve balances endpoint returns an account's balance data for all of Zapper's supported Curve pools. The returned data includes raw, USD, and underlying token balances of an account, in addition to contextual information about each pool for which the account has a balance. This endpoint is useful to query account balances for pools in Curve's ecosystem.

{% api-method method="get" host="https://api.zapper.fi" path="/v1/curve/balances?api\_key=api\_key" %}
{% api-method-summary %}
Get Curve Balances
{% endapi-method-summary %}

{% api-method-description %}
Returns balance data for Curve pools
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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
  "0x0f3d8...": 
   data: [
     {
       type: "pool",
       address: "0xeb16ae0052ed37f479f7fe63849198df1765a733",
       tokenAddress: "0x02d341ccb60faaf662bc0554d13778015d1b285c",
       decimals: 18,
       label: "sAAVE",
       symbol: "sAAVE",
       share: 0.000012077379020945607,
       supply: 15208456.306812523,
       tokens: [
         {
           decimals: 18,
           address: "0x6b175474e89094c44da98b954eedeac495271d0f",
           symbol: "DAI",
           balance: 126.3168534770324,
           balanceUSD: 126.3168534770324,
           reserve: 10458962.433650801,
           price: 1
         },
         {
           decimals: 18,
           address: "0x57ab1ec28d129707052df4df418d58a2d46d5f51",
           symbol: "sUSD",
           balance: 61.68571949330141,
           balanceUSD: 62.91943388316744,
           reserve: 5107541.908415795,
           price: 1.02
         }
       ],
       protocol: "curve",
       protocolSymbol: "Curve",
       protocolDisplay: "Curve",
       price: 1.033085387226444,
       balance: 183.67829114086547,
       balanceRaw: "183678291140865471191",
       balanceUSD: 189.23628736019984
     },
    ]
    meta: {
    totalUSD: 894.0880577705768
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

### Yearn Balances

The Yearn balances endpoint returns an account's balance data for all of Zapper's supported Yearn vaults. The returned data includes raw, USD, and underlying token balances of an account, in addition to contextual information about each vault for which the account has a balance. This endpoint is useful to query account balances for pools in Yearns ecosystem.

{% api-method method="get" host="https://api.zapper.fi" path="/v1/yearn/balances?api\_key=api\_key" %}
{% api-method-summary %}
Get Yearn Balances
{% endapi-method-summary %}

{% api-method-description %}
Returns balance data for specific addresses for Yearn vaults
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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

{% endapi-method-response-example-description %}

```
{
  "0x3b2c...": {
  data: [
    {
      type: "vault",
      address: "0xba2e7fed597fd0e3e70f5130bcdbbfe06bb94fe1",
      decimals: 18,
      tokenAddress: "0xba2e7fed597fd0e3e70f5130bcdbbfe06bb94fe1",
      contractAddress: "0xba2e7fed597fd0e3e70f5130bcdbbfe06bb94fe1",
      symbol: "YFI Vault",
      label: "YFI Vault",
      img: "YFI-icon.png",
      protocolDisplay: "Yearn",
      protocolSymbol: "YFI",
      protocolImg: "YFI-icon.png",
      protocol: "yearn",
      balance: 1.3044743275618431,
      balanceRaw: "1304474327561843174",
      balanceUSD: 60908.844755453116,
      price: 46692.252556089894,
      pricePerShare: 1.0151372414142512,
      canDeposit: true,
      tokens: [
        {
          address: "0x0bc529c00c6401aef6d220be8c6ea1667f6ad93e",
          symbol: "YFI",
          decimals: 18,
          img: "YFI-icon.png",
          balance: 1.3242204703768397,
          balanceUSD: 60908.844755453116
        }
      ]
    }
  ],
  meta: {
  totalUSD: 60908.844755453116
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    statusCode: 400,
    message: [
    "A helpful error message"
    ],
    error: "Bad Request"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

