---
description: Easily swap between assets through the API
---

# Exchange Assets

## Video Summary

{% embed url="https://www.youtube.com/watch?v=h\_GEw0ve60o" %}

## Check Exchange Price

Before exchanging to a different asset, you must first call the price endpoint to determine the price for swapping the assets and to obtain the exchange address in order to check approval state for the token. The **allowanceTarget** property returned is the contract address that the user must approve their tokens too.

{% hint style="info" %}
Note: The zero address is used as the token address for protocol native gas tokens i.e.

* `0x0000000000000000000000000000000000000000` swapping **ETH** on **Ethereum**
* `0x0000000000000000000000000000000000000000` swapping **BSC** on **Bianance SC**
{% endhint %}

{% api-method method="get" host="https://api.zapper.fi" path="/v1/exchange/price" %}
{% api-method-summary %}
Get Exchange Price
{% endapi-method-summary %}

{% api-method-description %}
Returns data about prices of a possible trade. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the token that is being sold
{% endapi-method-parameter %}

{% api-method-parameter name="buyTokenAddress" type="string" required=true %}
Address of the token that is being bought
{% endapi-method-parameter %}

{% api-method-parameter name="sellAmount" type="string" required=true %}
Amount to sell
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="number" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=false %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="slippagePercentage" type="number" %}
Slippage percentage as a decimal value
{% endapi-method-parameter %}

{% api-method-parameter name="network" type="string" %}
Network where the swap would be made
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from the exchange price endpoint
{% endapi-method-response-example-description %}

```
{
  "price": "1.0021",
  "guaranteedPrice": "0.992",
  "to": "0xdef1c0ded9bec7f1a1670819833240f027b25eff",
  "value": "0",
  "gas": "111000",
  "estimatedGas": "111000",
  "gasPrice": "1000000000",
  "protocolFee": "0",
  "minimumProtocolFee": "0",
  "buyTokenAddress": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
  "sellTokenAddress": "0x6b175474e89094c44da98b954eedeac495271d0f",
  "buyAmount": "10021",
  "sellAmount": "10000000000000000",
  "sources": [
    {
      "name": "Uniswap_V2",
      "proportion": "0"
    },
    {
      "name": "Eth2Dai",
      "proportion": "0"
    },
    {
      "name": "Kyber",
      "proportion": "0"
    },
    {
      "name": "SushiSwap",
      "proportion": "1"
    },
    {
      "name": "Shell",
      "proportion": "0"
    },
    {
      "name": "MultiHop",
      "proportion": "0"
    },
    {
      "name": "DODO",
      "proportion": "0"
    }
  ],
  "orders": [
    {
      "makerToken": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
      "takerToken": "0x6b175474e89094c44da98b954eedeac495271d0f",
      "makerAmount": "10021",
      "takerAmount": "10000000000000000",
      "fillData": {
        "tokenAddressPath": [
          "0x6b175474e89094c44da98b954eedeac495271d0f",
          "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48"
        ],
        "router": "0xd9e1ce17f2641f24ae83637ab66a2cca9c378b9f"
      },
      "source": "SushiSwap",
      "sourcePathId": "0xeea3991f20d566b823c5dca46125031e8bb0379a678c515e7280dac31b279d52",
      "type": 0
    }
  ],
  "allowanceTarget": "0xdef1c0ded9bec7f1a1670819833240f027b25eff",
  "sellTokenToEthRate": "2620.302848322808313341",
  "buyTokenToEthRate": "2624.980073"
}

```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error response for the exchange price endpoint
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

## Check Exchange Allowance

Before swapping assets, check that the exchange contract has approval to spend the tokens you are sending. 

{% hint style="info" %}
 If a **protocol native gas token** \(ETH on Ethereum or BSC on Binanance SC\) is being sold then this step can be skipped as it does not require approval to the exchange contract.
{% endhint %}

{% api-method method="get" host="https://api.zapper.fi" path="/v1/approval-state" %}
{% api-method-summary %}
Get Approval State
{% endapi-method-summary %}

{% api-method-description %}
Checks if the exchange contract has an approval amount associated with the `ownerAddress`. `isApproved` returns false if the `spenderAddress` has less than the `amount` response property. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="tokenAddress" type="string" required=true %}
Token contract address for approval 
{% endapi-method-parameter %}

{% api-method-parameter name="spenderAddress" type="string" required=true %}
Exchange contract address
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="string" required=false %}
A specific amount to approve
{% endapi-method-parameter %}

{% api-method-parameter name="network" type="string" required=false %}
Approval info for a specific network
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from the approval state endpoint
{% endapi-method-response-example-description %}

```
{
  "spenderAddress": "0xdef1c0ded9bec7f1a1670819833240f027b25eff",
  "tokenAddress": "0x6b175474e89094c44da98b954eedeac495271d0f",
  "ownerAddress": "0xfc759...",
  "allowance": "45228162514260000000000000000",
  "amount": "1000000000000",
  "isApproved": true
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
 Error response for approval state endpoint
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

## Set Allowance if Needed

If `isApprove` is false and the asset being sold is not a protocol native gas token, then this endpoint can be used to assemble an approval transaction. This transaction will grant the exchange contract \(i.e. the `spenderAddress` from the previous step\) an allowance, enabling it to transfer tokens from the `ownerAddress` to the exchange contract. This step is required in order for the exchange contract to proceed if it does not yet have an allowance.

{% api-method method="get" host="https://api.zapper.fi" path="/v1​/approval-transaction" %}
{% api-method-summary %}
Get Approval Transaction
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="tokenAddress" type="string" required=true %}
Token contract address for approval
{% endapi-method-parameter %}

{% api-method-parameter name="spenderAddress" type="string" required=true %}
Address of the exchange contract
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="string" required=false %}
A specific approval amount
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "data": "0x095ea7b3000000000000000000000000def1c0ded9bec7f1a1670819833240f027b25eff0000000000000000000000000000000000000000000000000000000000000000",
    "to": "0x6b175474e89094c44da98b954eedeac495271d0f",
    "from": "0xfc759...",
    "gasPrice": "100000000000"
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

## Exchange Asset Transaction

{% hint style="info" %}
This endpoint should only be used once the user has approved the contract address **and** is ready to submit a transaction.
{% endhint %}

{% api-method method="get" host="https://api.zapper.fi" path="/v1/exchange/quote" %}
{% api-method-summary %}
Get Exchange Quote
{% endapi-method-summary %}

{% api-method-description %}
Returns back both the price as well as data for submitting a trade transaction. **Should only be called for submitting a transaction.**
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the token that is being sold
{% endapi-method-parameter %}

{% api-method-parameter name="buyTokenAddress" type="string" required=true %}
Address of the token that is being bought
{% endapi-method-parameter %}

{% api-method-parameter name="sellAmount" type="string" required=true %}
Amount to sell
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=false %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="slippagePercentage" type="string" required=false %}
Slippage percentage as a decimal value
{% endapi-method-parameter %}

{% api-method-parameter name="network" type="string" required=false %}
Network where the swap would be made
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "price": "1.0021",
  "guaranteedPrice": "0.992",
  "to": "0xdef1c0ded9bec7f1a1670819833240f027b25eff",
  "data": "0xd9627aa40000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000000000000000000000002386f26fc1000000000000000000000000000000000000000000000000000000000000000026c0000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000020000000000000000000000006b175474e89094c44da98b954eedeac495271d0f000000000000000000000000a0b86991c6218b36c1d19d4a2e9eb0ce3606eb48869584cd0000000000000000000000003ce37278de6388532c3949ce4e886f365b14fb560000000000000000000000000000000000000000000000cb13248e36608843bc",
  "value": "0",
  "gas": "111000",
  "estimatedGas": "111000",
  "gasPrice": "1000000000",
  "protocolFee": "0",
  "minimumProtocolFee": "0",
  "buyTokenAddress": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
  "sellTokenAddress": "0x6b175474e89094c44da98b954eedeac495271d0f",
  "buyAmount": "10021",
  "sellAmount": "10000000000000000",
  "sources": [
    {
      "name": "Uniswap_V2",
      "proportion": "0"
    },
    {
      "name": "Eth2Dai",
      "proportion": "0"
    },
    {
      "name": "Kyber",
      "proportion": "0"
    },
    {
      "name": "SushiSwap",
      "proportion": "1"
    },
    {
      "name": "Shell",
      "proportion": "0"
    },
    {
      "name": "MultiHop",
      "proportion": "0"
    },
    {
      "name": "DODO",
      "proportion": "0"
    }
  ],
  "orders": [
    {
      "makerToken": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
      "takerToken": "0x6b175474e89094c44da98b954eedeac495271d0f",
      "makerAmount": "10021",
      "takerAmount": "10000000000000000",
      "fillData": {
        "tokenAddressPath": [
          "0x6b175474e89094c44da98b954eedeac495271d0f",
          "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48"
        ],
        "router": "0xd9e1ce17f2641f24ae83637ab66a2cca9c378b9f"
      },
      "source": "SushiSwap",
      "sourcePathId": "0xeea3991f20d566b823c5dca46125031e8bb0379a678c515e7280dac31b279d52",
      "type": 0
    }
  ],
  "allowanceTarget": "0xdef1c0ded9bec7f1a1670819833240f027b25eff",
  "sellTokenToEthRate": "2620.302848322808313341",
  "buyTokenToEthRate": "2624.980073"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Submit the Transaction

You can use parts from the quote response once you are ready to submit a transaction object like the one below which can be submitted to the blockchain via web3 or ethers.

```text
{
    "data": quote.data,
    "to": quote.to,
    "from": "0xfc759...",
    "gasPrice": quote.gasPrice
}
```

After initializing these libraries with a provider capable of signing the transaction \(e.g. Metamask\), a user can sign and broadcast the transaction in the same familiar way that they interact with any other DeFi protocol. For more details see the web3 [documentation](https://web3js.readthedocs.io/en/v1.2.0/web3-eth.html#sendtransaction) on sending transactions.

