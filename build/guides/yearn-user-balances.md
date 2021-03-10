# Yearn User Balances

## Overview

Ensure you have read the [Zapper API ](../zapper-api.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The Yearn balances endpoint returns an account's balance data for all of Zapper's supported Yearn vaults. The returned data includes raw, USD, and underlying token balances of an account, in addition to contextual information about each vault for which the account has a balance. This endpoint is useful to query account balances for pools in Yearns ecosystem.

{% api-method method="get" host="https://api.zapper.fi/v1/balances/yearn?api\_key=" path="api\_key" %}
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

{% endapi-method-response-example-description %}

```
{
  "0x3b2c...": [
    {
      "address": "0xe1237aa7f535b0cc33fd973d66cbf830354d16c7",
      "decimals": 18,
      "tokenAddress": "0xe1237aa7f535b0cc33fd973d66cbf830354d16c7",
      "contractAddress": "0xe1237aa7f535b0cc33fd973d66cbf830354d16c7",
      "symbol": "WETH Vault",
      "label": "WETH Vault",
      "img": "WETH-icon.png",
      "protocolDisplay": "Yearn",
      "protocolSymbol": "YFI",
      "protocolImg": "YFI-icon.png",
      "protocol": "yearn",
      "balance": 4.940696916986185,
      "balanceRaw": "4940696916986184768",
      "balanceUSD": 9029.47776013852,
      "pricePerShare": 1.0139375178377805,
      "pricePerToken": 1827.5716790267077,
      "isVault": true,
      "isBlocked": false,
      "canDeposit": true,
      "version": "v1"
    },
  ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
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

