---
description: Get Zapper's current gas prices
---

# Gas Price

## Overview

The prices endpoint returns Zapper's current Ethereum, BSC, and Polygon/Matic network gas prices

{% api-method method="get" host="http://api.zapper.fi/v1/gas-price" path=" " %}
{% api-method-summary %}
Get Gas Prices
{% endapi-method-summary %}

{% api-method-description %}
Returns the standard, fast, and instant gas price in GWEI.   
  
To convert to WEI multiply response values by 10 \*\* 9  
  
`network` can be one of `ethereum`,`binance-smart-chain`, `polygon`. Returns `ethereum` network gas prices if left blank.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="network" type="string" required=false %}
Network to get gas prices for
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Gas prices successfully retrieved.
{% endapi-method-response-example-description %}

```
{
  "standard": 75,
  "fast": 84.000001459,
  "instant": 90
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Error response from gas-price endpoint
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



