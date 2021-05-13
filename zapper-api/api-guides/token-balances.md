---
description: Get an account's Token balances
---

# Token Balances

## Overview

Ensure you have read the [Zapper API ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Data API.

The token balances endpoint returns an an account's token balances, including contextual information about each token for which the account has a balance.

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
  "0xfc7...": {
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
            "img": "1INCH-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 5.62,
            "balance": 54.40218481141585,
            "balanceRaw": "54402184811415852872",
            "balanceUSD": 305.7402786401571
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x7fc66500c84a76ad7e9c93437bfc5ac33e2ddae9",
            "symbol": "AAVE",
            "decimals": 18,
            "label": "AAVE",
            "img": "AAVE-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 525.9,
            "balance": 1,
            "balanceRaw": "1000000000000000000",
            "balanceUSD": 525.9
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xba100000625a3754423978a60c9317c58a424e3d",
            "symbol": "BAL",
            "decimals": 18,
            "label": "BAL",
            "img": "BAL-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 62.11,
            "balance": 3.63005206,
            "balanceRaw": "3630052060000000000",
            "balanceUSD": 225.46253344660002
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x1f573d6fb3f13d689ff844b4ce37794d79a7ff1c",
            "symbol": "BNT",
            "decimals": 18,
            "label": "BNT",
            "img": "BNT-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 7.32,
            "balance": 35,
            "balanceRaw": "35000000000000000000",
            "balanceUSD": 256.2
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xba9d4199fab4f26efe3551d490e3821486f135ba",
            "symbol": "CHSB",
            "decimals": 8,
            "label": "CHSB",
            "img": "CHSB-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 1.1,
            "balance": 50,
            "balanceRaw": "5000000000",
            "balanceUSD": 55.00000000000001
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc00e94cb662c3520282e6f5717214004a7f26888",
            "symbol": "COMP",
            "decimals": 18,
            "label": "COMP",
            "img": "COMP-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 784.71,
            "balance": 1,
            "balanceRaw": "1000000000000000000",
            "balanceUSD": 784.71
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xd533a949740bb3306d119cc777fa900ba034cd52",
            "symbol": "CRV",
            "decimals": 18,
            "label": "CRV",
            "img": "CRV-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 3.53,
            "balance": 30.00570108,
            "balanceRaw": "30005701080000000000",
            "balanceUSD": 105.9201248124
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x41e5560054824ea6b0732e656e3ad64e20e94e45",
            "symbol": "CVC",
            "decimals": 8,
            "label": "CVC",
            "img": "CVC-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.472485,
            "balance": 150,
            "balanceRaw": "15000000000",
            "balanceUSD": 70.87275
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x0abdace70d3790235af448c88547603b945604ea",
            "symbol": "DNT",
            "decimals": 18,
            "label": "DNT",
            "img": "DNT-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.264907,
            "balance": 150,
            "balanceRaw": "150000000000000000000",
            "balanceUSD": 39.73605
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xf629cbd94d3791c9250152bd8dfbdf380e2a3b9c",
            "symbol": "ENJ",
            "decimals": 18,
            "label": "ENJ",
            "img": "ENJ-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 2.09,
            "balance": 135.30438154,
            "balanceRaw": "135304381540000000000",
            "balanceUSD": 282.7861574186
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x0000000000000000000000000000000000000000",
            "symbol": "ETH",
            "decimals": 18,
            "label": "ETH",
            "img": "ETH-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 3856.24,
            "balance": 0.3501952193403428,
            "balanceRaw": "350195219340342784",
            "balanceUSD": 1350.4368126290035
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc944e90c64b2c07662a292be6244bdf05cda44a7",
            "symbol": "GRT",
            "decimals": 18,
            "label": "GRT",
            "img": "GRT-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 1.31,
            "balance": 100,
            "balanceRaw": "100000000000000000000",
            "balanceUSD": 131
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc12d1c73ee7dc3615ba4e37e4abfdbddfa38907e",
            "symbol": "KICK",
            "decimals": 8,
            "label": "KICK",
            "img": "KICK-icon.png",
            "hide": true,
            "canExchange": false,
            "price": 0.00014619,
            "balance": 888888,
            "balanceRaw": "88888800000000",
            "balanceUSD": 129.94653672
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xdd974d5c2e2928dea5f71b9825b8b646686bd200",
            "symbol": "KNC",
            "decimals": 18,
            "label": "KNC",
            "img": "KNC-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 3.02,
            "balance": 119.72021789,
            "balanceRaw": "119720217890000000000",
            "balanceUSD": 361.5550580278
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xbbbbca6a901c926f240b89eacb641d8aec7aeafd",
            "symbol": "LRC",
            "decimals": 18,
            "label": "LRC",
            "img": "LRC-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.625299,
            "balance": 100,
            "balanceRaw": "100000000000000000000",
            "balanceUSD": 62.529900000000005
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x7d1afa7b718fb893db30a3abc0cfc608aacfebb0",
            "symbol": "MATIC",
            "decimals": 18,
            "label": "MATIC",
            "img": "MATIC-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 1.13,
            "balance": 291.4890657892496,
            "balanceRaw": "291489065789249583970",
            "balanceUSD": 329.38264434185203
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x4fe83213d56308330ec302a8bd641f1d0113a4cc",
            "symbol": "NU",
            "decimals": 18,
            "label": "NU",
            "img": "NU-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.39907,
            "balance": 100,
            "balanceRaw": "100000000000000000000",
            "balanceUSD": 39.907
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x4575f41308ec1483f3d399aa9a2826d74da13deb",
            "symbol": "OXT",
            "decimals": 18,
            "label": "OXT",
            "img": "OXT-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.568457,
            "balance": 0.82345767,
            "balanceRaw": "823457670000000000",
            "balanceUSD": 0.46810027671519
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x0cec1a9154ff802e7934fc916ed7ca50bde6844e",
            "symbol": "POOL",
            "decimals": 18,
            "label": "POOL",
            "img": "POOL-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 17.44,
            "balance": 4.474802,
            "balanceRaw": "4474802000000000000",
            "balanceUSD": 78.04054688000001
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x408e41876cccdc0f92210600ef50372656052a38",
            "symbol": "REN",
            "decimals": 18,
            "label": "REN",
            "img": "REN-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.828405,
            "balance": 150,
            "balanceRaw": "150000000000000000000",
            "balanceUSD": 124.26074999999999
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc011a73ee8576fb46f5e1c5751ca3b9fe0af2a6f",
            "symbol": "SNX",
            "decimals": 18,
            "label": "SNX",
            "img": "SNX-icon.png",
            "hide": true,
            "canExchange": true,
            "price": 20.26,
            "balance": 33.49875183,
            "balanceRaw": "33498751830000000000",
            "balanceUSD": 678.6847120758001
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x6b3595068778dd592e39a122f4f5a5cf09c90fe2",
            "symbol": "SUSHI",
            "decimals": 18,
            "label": "SUSHI",
            "img": "SUSHI-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 15.27,
            "balance": 15.99418393,
            "balanceRaw": "15994183930000000000",
            "balanceUSD": 244.2311886111
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0x1f9840a85d5af5bf1d1762f925bdaddc4201f984",
            "symbol": "UNI",
            "decimals": 18,
            "label": "UNI",
            "img": "UNI-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 37.94,
            "balance": 7.19792974,
            "balanceRaw": "7197929740000000000",
            "balanceUSD": 273.0894543356
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
            "symbol": "USDC",
            "decimals": 6,
            "label": "USDC",
            "img": "USDC-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 0.996868,
            "balance": 25,
            "balanceRaw": "25000000",
            "balanceUSD": 24.921699999999998
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xe41d2489571d322189246dafa5ebde1f4699f498",
            "symbol": "ZRX",
            "decimals": 18,
            "label": "ZRX",
            "img": "ZRX-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 1.7,
            "balance": 75,
            "balanceRaw": "75000000000000000000",
            "balanceUSD": 127.5
          },
          {
            "type": "wallet",
            "category": "wallet",
            "address": "0xc5bddf9843308380375a611c18b50fb9341f502a",
            "symbol": "yveCRV-DAO",
            "decimals": 18,
            "label": "yveCRV-DAO",
            "img": "yveCRV-DAO-icon.png",
            "hide": false,
            "canExchange": false,
            "price": 3.01,
            "balance": 100,
            "balanceRaw": "100000000000000000000",
            "balanceUSD": 301
          }
        ],
        "meta": []
      }
    ],
    "meta": [
      {
        "label": "Total",
        "value": 6909.282298215629,
        "type": "dollar"
      },
      {
        "label": "Assets",
        "value": 6909.282298215629,
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



