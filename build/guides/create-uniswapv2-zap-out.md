---
description: Construct a Sushiswap LP Zap Out Transaction with the Transactions API
---

# Create a Zap Out \(Sushiswap\)

## Overview

Ensure you have read the [Zapper API ](../zapper-api.md)section for a brief overview of the API types and to acquire an API key. This Zap Out guide uses the Zapper Transactions API.

The Sushiswap Zap Out removes liquidity from Sushiswap pools. The latest currently deployed Sushiswap Zap Out can be found [here](../smart-contracts.md). The Zap accepts Sushiswap LP Tokens and converts them into ETH, any arbitrary ERC20 token, or the pair of underling tokens. Any swaps that are required are done so in a manner such that the output is maximized with as little slippage as possible. This is done via intelligent pathing to ensure that the exchange is routed optimally, leveraging PMMs if necessary.

{% hint style="info" %}
This guide is also applicable to Uniswap V2. Simply substitute references of`sushiswap` with`uniswap.`For example, in the [Get Zap Allowance](create-uniswapv2-zap-out.md#check-zap-allowance) request, `.../zap-out/sushiswap/approval-state/...` can be replaced with `.../zap-out/uniswap/approval-state/...`

\*For the [Get Zap Out Transaction](create-uniswapv2-zap-out.md#get-zap-out-transaction) query, replace`sushiswap`with`uniswap-v2`

\`\`
{% endhint %}

## Check Zap Allowance

Before Zapping Out, check that the Zap contract has approval to spend the LP tokens you are sending. 

{% api-method method="get" host="https://api.zapper.fi" path="/v1/zap-out/sushiswap/approval-state?api\_key=API\_KEY" %}
{% api-method-summary %}
Get Approval State
{% endapi-method-summary %}

{% api-method-description %}
This endpoint checks if the Zap has approval to interact with the `ownerAddress`' LP tokens. If `isApproved` is false, the Zap \(i.e. the `spenderAddress`\) has less than the `amount` property in allowance and will require an approval transaction before proceeding. The amount property represents the total LP balance of the `tokenAddress` held by the `ownerAddress`  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the LP token
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="network" type="string" required=false %}
Retrieve approval info for a specific network
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "spenderAddress": "0x69090d6968B12b79CD403Ee33E871284dC7E92F6",
    "tokenAddress": "0xa478c2975ab1ea89e8196811f51a7b7ade33eb11",
    "ownerAddress": "0x2a4...",
    "allowance": "0",
    "amount": "423802387456",
    "isApproved": false
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error response from approval-state endpoint
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

If `isApprove` is false, this endpoint can be used to assemble an approval transaction to submit to the Ethereum network for the LP token. This transaction will grant the Sushiswap Zap Out contract \(i.e. the `spenderAddress` from the previous step\) an allowance, enabling it to transfer tokens from the `ownerAddress` to the Zap contract. This step is required in order for the Zap to proceed if it does not yet have an allowance.

{% api-method method="get" host="https://api.zapper.fi" path="/v1/zap-out/sushiswap/approval-transaction?api\_key=API\_KEY" %}
{% api-method-summary %}
Get Approval Transaction
{% endapi-method-summary %}

{% api-method-description %}
The allowance granted to the Zap is `79228162514.26`\(i.e. effectively infinite\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the LP token
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="network" type="string" required=false %}
Retrieve approval transaction for a specific network
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from approval-transaction endpoint.
{% endapi-method-response-example-description %}

```
{
    "data": "0x095ea7b3000000...",
    "to": "0xa478c2975ab1ea89e8196811f51a7b7ade33eb11",
    "from": "0x2a4d...",
    "gasPrice": "97000001459"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error response from approval-transaction endpoint.
{% endapi-method-response-example-description %}

```
{
    statusCode: 400,
    message: [
    "A Helpful error messasge."
    ],
    error: "Bad Request"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Zap Out

After the approval step has been completed, this endpoint can be used to create a transaction for the Zap Out. This is the value transaction, which if signed and broadcasted, will transfer LP tokens from the `ownerAddress` to the Zap contract \(the `to` property in the response\). Subsequently, the proceeds of the Zap out \(i.e. ETH, tokens, or both\) will be transferred to the `ownerAddress`. If the transaction reverts, the sender will pay for the gas consumed, however, the LP tokens **will not** be deducted from the `ownerAddress`. 

The `slippagePercentage` encapsulates the entire atomic transaction and will cause the transaction to revert if it is exceeded. For example, if the slippagePercentage is 3% \(0.03\) and the Zap requires multiple swaps \(exchanges\), the transaction will revert if cumulative slippage exceeds 3%. This represents the _maximum_ acceptable slippage and does not imply that the Zap will actually _experience_ this much slippage upon execution.

The `poolAddress` represents the Sushiswap pool to exit from. This address can be obtained from Zapper's Data API as shown [here](sushiswap-pool-stats.md)

The `gasPrice` recommended by Zapper is returned from [Zapper's Gas Price API](get-gas-price.md). Alternatively, you can choose to use any gas price you'd like. The `gasPrice` should be in `WEI`

{% api-method method="get" host="https://api.zapper.fi" path="/v1/zap-out/sushiswap/transaction?api\_key=API\_KEY" %}
{% api-method-summary %}
Get Zap Out Transaction
{% endapi-method-summary %}

{% api-method-description %}
Recommended slippagePercentage is `0.01` to `0.03` \(i.e. 1-3%\).  
  
The sellAmount should be in the base units of the sell token. For example for 3.14159 Sushiswap LP tokens it should be `3.14159 / 10 ** 18 = 3141590000000000000`   
  
If Ether is being received, the `toTokenAddress` should be the zero address \(i.e. `0x0000000000000000000000000000000000000000`\)  
  
`shouldSellEntire` balance should always be set to `true`. This flag ensures that the transaction does not revert in cases where the reserves change significantly \(i.e. up to the `slippagePercentage`\) due to slow transaction confirmation times.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
{% endapi-method-parameter %}

{% api-method-parameter name="slippagePercentage" type="string" required=true %}
Slippage percentage as a decimal value
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="poolAddress" type="string" required=true %}
Address of the pool contract
{% endapi-method-parameter %}

{% api-method-parameter name="shouldSellEntireBalance" type="boolean" required=true %}
Flag to sell entire contract balance
{% endapi-method-parameter %}

{% api-method-parameter name="sellAmount" type="string" required=true %}
Amount to sell in base units of the LP token
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the owner
{% endapi-method-parameter %}

{% api-method-parameter name="toTokenAddress" type="string" required=true %}
Address of the token to receive
{% endapi-method-parameter %}

{% api-method-parameter name="network" type="string" required=false %}
Retrieve zap out transaction for a specific network
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from transaction endpoint
{% endapi-method-response-example-description %}

```
{
    "to": "0xb832cc0e8ed40ae42eddc63d9d07ebaf022994e8",
    "from": "0x2a4d...",
    "data": "0xbb0abba7000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000005b99b82a033ddb700000000000000000000000019d3364a399d251e894ac732651be8b0e4e85001000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002737641f7304d7d4e9000000000000000000000000def1c0ded9bec7f1a1670819833240f027b25eff000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000128d9627aa4000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000005b99b82a033ddb7000000000000000000000000000000000000000000000027eb0781bcc6ad968d00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000002000000000000000000000000eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee0000000000000000000000006b175474e89094c44da98b954eedeac495271d0f869584cd000000000000000000000000f4e386b070a18419b5d3af56699f8a438dd18e890000000000000000000000000000000000000000000000bd5d54886f60470580000000000000000000000000000000000000000000000000",
    "value": "0",
    "gasPrice": "153800000000",
    "gas": "316245"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error response from transaction endpoint
{% endapi-method-response-example-description %}

```
{
    statusCode: 400,
    message: [
    "A helpful error message."
    ],
    error: "Bad Request"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Send It!

### With Web3/Ethers

The transaction objects returned from the Get Zap Out Transaction and Get Approval Transaction endpoints are ready to be consumed by web3 or ethers. After initializing these libraries with a provider capable of signing the transaction \(e.g. Metamask\), a user can sign and broadcast the transaction in the same familiar way that they interact with any other DeFi protocol. For more details see the web3 [documentation](https://web3js.readthedocs.io/en/v1.2.0/web3-eth.html#sendtransaction) on sending transactions.

### With smart contracts

To consume the transaction object in your smart contract, it must have a balance of the `poolAddress`  \(i.e. pool tokens\) representing the `sellAmount`. Therefore, because your smart contract holds this balance, it is also the `ownerAddress`.  When assembling the transaction in the [Get Zap Out Transaction request](create-uniswapv2-zap-out.md#get-zap-out-transaction), care should be taken to assemble it with these parameters in mind. 

A function in a smart contract that consumes a Zap Out transaction might resemble this:

```text
// Zaps out of a Sushiswap pool into ETH or ERC20 Tokens or both using a Zapper Transaction Object
// The contract must have a fallback function to receive ETH proceeds from a Zap Out
function ZapOut(
    // The `sellTokenAddress` field from the API response.
    address sellToken,
    // The `buyTokenAddress` field from the API response.
    address buyToken,
    // The `to` field from the API response.
    address payable ZapContract,
    // The `data` field from the API response.
    bytes calldata zapCallData
)
    external
    onlyOwner
    returns (uint256 tokensRec)
{
    // ...

    // Give the Zap an infinite allowance to spend this contract's `sellToken`.
    require(sellToken.approve(ZapContract, uint256(-1)));
    // Check this contract's initial balance
    uint256 initialBalance = buyToken == address(0)
    ? address(this).balance
    : IERC20(buyToken).balanceOf(address(this));
    // Call the encoded Zap Out function call on the contract at `ZapContract`,
    (bool success,) = ZapContract.call(zapCallData);
    require(success, 'Zap Out Failed');
    uint256 finlBal = buyToken == address(0)
    ? address(this).balance
    : IERC20(buyToken).balanceOf(address(this));
    tokensRec = finlBal.sub(initialBalance);
    
    // ...
}
```

