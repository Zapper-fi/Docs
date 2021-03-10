---
description: Retrieve yearn vault data from the Data API
---

# Get Yearn Vault Stats

## Overview

Ensure you have read the [Zapper API ](../zapper-api.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The yearn vault stats endpoint returns contextual data for all of Zapper's supported yVaults. The returned data includes information such as each yVault's address, liquidity, total supply, USD price, underlying tokens, and more. This endpoint is useful to query statistics about the vaults in yearn's ecosystem or to use the returned data \(like the address property\) as parameters in the Transactions API as shown [here](yearn-zap-in.md#zap-in)

{% api-method method="get" host="https://api.zapper.fi/v1/vault-stats/yearn?api\_key=" path="api\_key" %}
{% api-method-summary %}
Get yearn Vault Stats
{% endapi-method-summary %}

{% api-method-description %}
Returns vault stats data for yearn Vaults.
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
    "address": "0x5533ed0a3b83f70c3c4a1f69ef5546d3d4713e44",
    "contractAddress": "0x5533ed0a3b83f70c3c4a1f69ef5546d3d4713e44",
    "tokenAddress": "0x5533ed0a3b83f70c3c4a1f69ef5546d3d4713e44",
    "symbol": "crvSUSD Vault",
    "label": "crvSUSD Vault",
    "value": "crvSUSD Vault",
    "isAave": false,
    "isCurve": true,
    "pricePerToken": 1.048763587843297,
    "liquidity": 21678402.62753494,
    "supply": 20670437.912623316,
    "protocol": "yearn",
    "protocolDisplay": "Yearn",
    "protocolSymbol": "YFI",
    "decimals": 18,
    "isBlocked": false,
    "canDeposit": true,
    "pricePerShare": 1.0104455587208072,
    "version": "v1",
    "tokens": [
      {
        "label": "sUSD Curve",
        "value": "sUSD",
        "protocol": "curve",
        "protocolDisplay": "Curve",
        "protocolSymbol": "CRV",
        "decimals": 18,
        "address": "0xFCBa3E75865d2d561BE8D220616520c171F12851",
        "tokenAddress": "0xc25a3a3b969415c80451098fa907ec722572917f",
        "exchangeAddress": "0xa5407eae9ba41422680e2e00537571bcc53efbfd",
        "contractAddress": "0xFCBa3E75865d2d561BE8D220616520c171F12851",
        "depositAddress": "0xFCBa3E75865d2d561BE8D220616520c171F12851",
        "liquidity": 174414609.5248811,
        "pricePerToken": 1.0379219135477216,
        "volume": 42375366.28463072,
        "feeVolume": 16950.14651385229,
        "fee": 0.0004,
        "volliq": 0.2429576650721204,
        "isBlocked": false,
        "isBtc": false,
        "isMetaPool": false,
        "tokens": [
          {
            "symbol": "sUSD",
            "address": "0x57ab1ec28d129707052df4df418d58a2d46d5f51",
            "decimals": 18,
            "price": 1.01,
            "reserve": 28500032.395438664,
            "reserveUSD": 28785032.719393052
          },
          {
            "symbol": "DAI",
            "address": "0x6b175474e89094c44da98b954eedeac495271d0f",
            "decimals": 18,
            "price": 1,
            "reserve": 47748788.94028079,
            "reserveUSD": 47748788.94028079
          },
          {
            "symbol": "USDC",
            "address": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
            "decimals": 6,
            "price": 0.999263,
            "reserve": 48172234.364747,
            "reserveUSD": 48136731.42802019
          },
          {
            "symbol": "USDT",
            "address": "0xdac17f958d2ee523a2206206994597c13d831ec7",
            "decimals": 6,
            "price": 1,
            "reserve": 49669301.824872,
            "reserveUSD": 49669301.824872
          }
        ],
        "supply": 168042130.384081,
        "dailyROI": 0.00009718306602884817,
        "weeklyROI": 0.0006802814622019371,
        "yearlyROI": 0.03537463603450073,
        "symbol": "sUSD Curve"
      }
    ]
  },
  {Subsequent vaults...},
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



