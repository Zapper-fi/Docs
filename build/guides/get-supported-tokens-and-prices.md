---
description: Get a list of Zapper's supported tokens
---

# Get Supported Tokens and Prices

## Overview

Ensure you have read the [Zapper API ](../zapper-api.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The prices endpoint returns an array of Zapper's supported tokens and their associated USD price, decimals, address and symbol.

{% api-method method="get" host="https://api.zapper.fi/v1/prices?api\_key=" path="api\_key" %}
{% api-method-summary %}
Get Zapper Prices
{% endapi-method-summary %}

{% api-method-description %}
Returns Zapper's supported tokens
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
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
    "address": "0x68a118ef45063051eac49c7e647ce5ace48a68a5",
    "decimals": 18,
    "symbol": "$BASED",
    "price": 1.77
  },
  {
    "address": "0x9d47894f8becb68b9cf3428d256311affe8b068b",
    "decimals": 18,
    "symbol": "$ROPE",
    "price": 52.24
  },
  {
    "address": "0xb6ed7644c69416d67b522e20bc294a9a9b405b31",
    "decimals": 8,
    "symbol": "0XBTC",
    "price": 0.317657
  },
  {
    "address": "0x035df12e0f3ac6671126525f1015e47d79dfeddf",
    "decimals": 18,
    "symbol": "0XMR",
    "price": 0.056292
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



