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

![Source: https://medium.com/bollinger-investment-group/constant-function-market-makers-defis-zero-to-one-innovation-968f77022159](../../.gitbook/assets/image%20%283%29.png)

## Who's this for?

{% hint style="warning" %}
Risk-averse: prefer stable and predictable income.
{% endhint %}

{% hint style="danger" %}
Generally bearish on crypto markets for the time being.
{% endhint %}
{% endtab %}

{% tab title="Add Liquidity" %}
![sUSD Curve Pooling Illustration](../../.gitbook/assets/ezgif.com-gif-maker-1.gif)

1. _**Connect**_ your digital wallet.

   _No wallet?_ [_**Get one.**_](https://metamask.io/)_\*\*\*\*_

2. Navigate to the [**Invest**](https://www.zapper.fi/#/invest) tab.
3. Type in _**Curve**_ in the filter & click _**Add liquidity**_ next to the pool you would like to join.
4.  ****Enter how much liquidity you would like to add in _**ETH or ERC20s** \(fiat coming soon\). Token balances show up in the drop-down if you have them available. ****_
5. Confirm the transaction & you will receive Curve Pool Tokens \(CRV\) which are ERC20 tokens that track your liquidity provided to the protocol.

{% embed url="https://twitter.com/DeFi\_Dad/status/1275577623473618944?s=20" %}

{% hint style="info" %}
**Note:** Curve pooling options will be included in [**Multipooling** ](../multipooling.md)soon. For now, you are able to submit 2 separate transactions if you would like to add liquidity to both Curve and Uniswap pool.
{% endhint %}
{% endtab %}

{% tab title="Remove Liquidity" %}
![](../../.gitbook/assets/5eloy7hedn.gif)

1. **As usual start by selecting which pool you want to exit.**
2. **For output you are able to select ETH, sUSD, DAI, USDC, TUSD, USDT, or BUSD.**
3. **Confirm your transaction.**
{% endtab %}

{% tab title="Incentives" %}
## Add liquidity to [sUSD pool on Curve ](https://www.zapper.fi/invest)+ stake your pool tokens to receive $BAL + $SNX + future $CRV rewards.

![1. Type in &apos;sUSD&apos; to filter Curve sUSD pool.](../../.gitbook/assets/chrome_2psnreh6sm.png)

![2. Enter how much liquidity you would like to add.](../../.gitbook/assets/chrome_cv6vcbcdmd.png)

![3. Once you have sUSD Curve pool tokens, click stake. ](../../.gitbook/assets/chrome_sie91vu8re.png)

![4. Simply click confirm &amp; your pool tokens will start accruing rewards.](../../.gitbook/assets/chrome_rfuoy9hwuk.png)

![5. View your current staked assets. Claim rewards / unstake anytime.](../../.gitbook/assets/chrome_f25fz7cdxi.png)

![](../../.gitbook/assets/chrome_itroncqp9s.png)

## Add liquidity to [sBTC pool on Curve ](https://www.zapper.fi/invest)+ stake your pool tokens to receive $BAL + $SNX + $REN + future $CRV rewards.
{% endtab %}
{% endtabs %}

