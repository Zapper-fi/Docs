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

### Available Curve Pools:

* [sUSD \(beta\)](https://beta.curve.fi/)
* [Compound](https://compound.curve.fi/)
* [USDT](https://usdt.curve.fi/)
* [yCurve](https://y.curve.fi/)
* [BUSD](https://busd.curve.fi/)
{% endtab %}
{% endtabs %}





