---
description: Add liquidity to Curve pools & start generating fees on stable-coins.
---

# Curve

![](../../.gitbook/assets/group-280.png)

{% tabs %}
{% tab title="Overview" %}
{% hint style="info" %}
### Uses a hybrid of a constant sum and constant product, and arrives at quite a complex function below:
{% endhint %}

![](../../.gitbook/assets/image%20%281%29.png)

Where **x** is the reserves for each asset, **n** is the number of assets, **D** is an _invariant_ that represents the value in the reserve, and **A** is the “amplification coefficient”, which is a _tunable constant_ that provides an effect similar to leverage and influences the range of asset prices that will be profitable for liquidity providers \(i.e. the higher the asset volatility, the higher **A** should be\).

This function acts as a **constant sum** when the portfolio is balanced and shifts towards a **constant product** as the portfolio becomes more imbalanced. In effect, the function looks like a “zoomed-in hyperbola”.

![](../../.gitbook/assets/image%20%283%29.png)
{% endtab %}

{% tab title="How it works" %}
![sUSD Curve Pooling Illustration](../../.gitbook/assets/ezgif.com-gif-maker-1.gif)

1. _**Connect**_ your digital wallet.

   _No wallet?_ [_**Get one.**_](https://metamask.io/)_\*\*\*\*_

2. Navigate to the [**Invest**](https://www.zapper.fi/#/invest) tab.
3. Type in _**Curve**_ in the filter & click _**Invest**_ next to sUSD CRV Pool.
4.  ****Enter how much you want to invest in _**ETH or ERC20s** \(fiat coming soon\). Token balances show up in the drop-down if you have any available. ****_
5. Select gas setting for your transaction and click _**confirm**_. 

   _When Metamask or your wallet provider prompts you, click confirm again._ 

{% hint style="info" %}
**Note:** Curve pooling options will be included in [**Multipooling** ](../multipooling.md)soon. For now, you are able to submit 2 separate transactions if you would like to add liquidity to both Curve and Uniswap pool.
{% endhint %}
{% endtab %}
{% endtabs %}





