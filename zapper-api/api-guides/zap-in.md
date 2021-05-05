---
description: Construct a Zap In Transaction (yEarn Vaults V1 or V2)
---

# Zap In

## Video Summary

{% embed url="https://www.youtube.com/watch?v=VkyD17Benx8" %}

Ensure you have read the [Zapper API ](../api-getting-started.md)section for a brief overview of the API types and to acquire an API key. This guide uses the Zapper Transactions API. While this guide shows Zapping In for a Yearn vault, the process for Zapping In for other sources is very similar.

## Yearn Zap In Overview

The yVault Zap In adds liquidity to V1 and V2 Vaults. The latest currently deployed yVault Zap In can be found [here](../../zapper-smart-contracts/smart-contracts.md). The Zap accepts ETH or any Arbitrary ERC20 token and converts it into the appropriate input type for the Vault. Any token swaps that are required are done so in a manner such that the output is maximized with as little slippage as possible. This is done via intelligent pathing to ensure that the exchange is routed optimally, leveraging PMMs if necessary. In addition, if the input type for the vault is an LP token \(e.g. a Curve LP\), the Zap will also acquire the required LPs via an underlying Zap before adding liquidity into the Vault and returning the proceeds to the sender.

## Check Zap Allowance

Before Zapping In, check that the Zap contract has approval to spend the tokens you are sending. If ETH is being Zapped in, this step can be skipped as it does not require approval to transfer to the Zap contract. 

{% api-method method="get" host="https://api.zapper.fi/v1/zap-in/yearn/approval-state?api\_key=" path="API\_KEY" %}
{% api-method-summary %}
Get Approval State
{% endapi-method-summary %}

{% api-method-description %}
This endpoint checks if the Zap has approval to interact with the `ownerAddress`' tokens. If `isApproved` is false, the Zap \(i.e. the `spenderAddress`\) has less than the `amount` property in allowance and will require an approval transaction before proceeding. The amount property represents the total balance of the `tokenAddress` held by the `ownerAddress`
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the token to sell
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the seller
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful response from approval-state endpoint
{% endapi-method-response-example-description %}

```
{
    "spenderAddress": "0xb832cc0e8ed40ae42eddc63d9d07ebaf022994e8",
    "tokenAddress": "0x77777feddddffc19ff86db637967013e6c6a116c",
    "ownerAddress": "0x2a4...",
    "allowance": "0",
    "amount": "8339681156599282002",
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

If `isApprove` is false and the `sellToken` is not ETH, this endpoint can be used to assemble an approval transaction. This transaction will grant the yVault Zap In contract \(i.e. the `spenderAddress` from the previous step\) an allowance, enabling it to transfer tokens from the `ownerAddress` to the Zap contract. This step is required in order for the Zap to proceed if it does not yet have an allowance.

{% api-method method="get" host="https://api.zapper.fi/v1/zap-in/yearn/approval-transaction?api\_key=" path="API\_KEY" %}
{% api-method-summary %}
Get Approval Transaction
{% endapi-method-summary %}

{% api-method-description %}
The allowance granted to the Zap is `79228162514.26` \(i.e. effectively infinite\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the token to sell
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the seller
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication token
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
    "to": "0x77777feddddffc19ff86db637967013e6c6a116c",
    "from": "0x2a4d...",
    "gasPrice": "97000001459"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Error response from approval-transaction endpoint
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

## Zap In

After the approval step has been completed \(or if the Zap has already been granted an allowance or ETH is the input\). This endpoint can be used to create a transaction for the Zap In. This is the value transaction, which if signed and broadcasted, will transfer funds from the `ownerAddress` to the Zap contract \(the `to` property in the response\). Subsequently, the proceeds from the Zap In will be sent to the ownerAddress \(e.g Yearn vault tokens\). If the transaction reverts, the sender will pay for the gas consumed, however, the tokens **will not** be deducted from the `ownerAddress`. 

The `slippagePercentage` encapsulates the entire atomic transaction and will cause the transaction to revert if it is exceeded. For example, if the slippagePercentage is 3% \(0.03\) and the Zap requires multiple swaps \(exchanges\), the transaction will revert if cumulative slippage exceeds 3%. This represents the _maximum_ acceptable slippage and does not imply that the Zap will actually _experience_ this much slippage upon execution.

The `poolAddress` represents the yVault to enter. This address can be obtained from Zapper's Data API as shown [here](vault-stats.md#overview)

The `gasPrice` recommended by Zapper is returned from [Zapper's Gas Price API](gas-price.md). Alternatively, you can choose to use any gas price you'd like. The `gasPrice` should be in `WEI`

{% api-method method="get" host="https://api.zapper.fi/v1/zap-in/yearn/transaction?api\_key=" path="API\_KEY" %}
{% api-method-summary %}
Get Zap In Transaction
{% endapi-method-summary %}

{% api-method-description %}
Recommended `slippagePercentage` is `0.01` to `0.03` \(i.e. 1-3%\).   
  
The `sellAmount` should be in the base units of the sell token. For example for 3.14159 Ether it should be `3.14159 / 10 ** 18 = 3141590000000000000`   
  
If Ether is being sent, the sellTokenAddress should be the zero address \(i.e. `0x0000000000000000000000000000000000000000`\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="affiliateAddress" type="string" required=false %}
Affiliate address for volume tracking
{% endapi-method-parameter %}

{% api-method-parameter name="slippagePercentage" type="string" required=true %}
Slippage percentage as a decimal value
{% endapi-method-parameter %}

{% api-method-parameter name="gasPrice" type="string" required=true %}
Gas price in wei
{% endapi-method-parameter %}

{% api-method-parameter name="poolAddress" type="string" required=true %}
yVault Address to enter
{% endapi-method-parameter %}

{% api-method-parameter name="sellTokenAddress" type="string" required=true %}
Address of the token to sell
{% endapi-method-parameter %}

{% api-method-parameter name="sellAmount" type="string" required=true %}
Amount to sell in base units of the sell token
{% endapi-method-parameter %}

{% api-method-parameter name="ownerAddress" type="string" required=true %}
Address of the seller
{% endapi-method-parameter %}

{% api-method-parameter name="api\_key" type="string" required=true %}
Authentication Token
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
    "value": "0x5b99b82a033ddb7",
    "sellTokenAddress": "0x0000000000000000000000000000000000000000",
    "sellTokenAmount": "412531826216918455",
    "buyTokenAddress": "0x19d3364a399d251e894ac732651be8b0e4e85001",
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

The transaction objects returned from the [Get Zap In Transaction](zap-in.md#get-zap-in-transaction) and [Get Approval Transaction](zap-in.md#get-approval-transaction) endpoints are ready to be consumed by web3 or ethers. After initializing these libraries with a provider capable of signing the transaction \(e.g. Metamask\), a user can sign and broadcast the transaction in the same familiar way that they interact with any other DeFi protocol. For more details see the web3 [documentation](https://web3js.readthedocs.io/en/v1.2.0/web3-eth.html#sendtransaction) on sending transactions.

### With smart contracts

To consume the transaction object in your smart contract, it must have a balance of the `sellTokenAddress`  representing the `sellAmount`. Therefore, because your smart contract holds this balance, it is also the `ownerAddress`.  When assembling the transaction in the [Get Zap In Transaction request](zap-in.md#get-zap-in-transaction), care should be taken to assemble it with these parameters in mind. 

A function in a smart contract that consumes a Zap In transaction might resemble this:

```text
// Zaps into a Yearn yVault with ETH or ERC20 Tokens using a Zapper Transaction Object
function ZapIn(
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
    payable // Must attach ETH equal to the `value` field from the API response.
    returns (uint256 yVaultTokensRec)
{
    // ...

    // Give the Zap an infinite allowance to spend this contract's `sellToken`.
    // Note that for some tokens (e.g., USDT, KNC), you must first reset any existing
    // allowance to 0 before being able to update it.
    require(sellToken.approve(ZapContract, uint256(-1)));
    // Check this contract's initial balance
    uint256 initialBalance = IERC20(buyToken).balanceOf(address(this));
    // Call the encoded Zap function call on the contract at `ZapContract`,
    // passing along any ETH attached to this function call for the Zap.
    (bool success,) = ZapContract.call{value: msg.value}(zapCallData);
    require(success, 'Zap In Failed');
    yVaultTokensRec = IERC20(buyToken).balanceOf(address(this)).sub(initialBalance);
    // ...
}
```

