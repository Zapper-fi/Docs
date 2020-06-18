# 🚰Piping

Pool pipes seamlessly **re-balance** liquidity between pools.

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fbb82a33a-11c8-4430-b857-d237161e9580_920x558.png)

### **How does it work?**

Let’s assume you’re providing liquidity in the sETH pool on Uniswap earning trading fees + SNX rewards. 

You noticed that Synthetix just started distributing SNX rewards to Curve sUSD liquidity providers as well.

To move some of your liquidity from Uniswap sETH Pool into Curve’s sUSD Pool, you would need to perform at least 4 on chain transactions:

1. **Remove liquidity from sETH pool on Uniswap**
2. **Use ETH portion to buy DAI** 
3. **Use sETH to buy USDC**
4. **Add DAI + USDC on Curve**

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F9f196300-3194-46f9-8d5e-e514482296b3_1600x1174.png)

**Uniswap V1 &lt;&gt; Curve Pipe cuts this down to one!**

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F823efe8b-7944-44e1-b0b7-f86e4a99d30c_1006x638.png)

### **Walk-through tutorial:**

> **STEP 1: Visit Zapper.fi & connect your wallet.**

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fe4b4288a-be02-4241-bd47-1d1ba1c64c6a_961x460.png)

> **STEP 2: View your liquidity pool balances & click ‘Rebalance’**

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F06bffb69-cdda-43e4-a85e-3db9f679ea34_1797x867.png)

> **STEP 3: Choose which platform and which pool within that platform you would like to move some or all of your current pool’s liquidity into.**

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F323eb0af-81be-42f1-b5f3-5e390d34cffd_1178x849.gif)

> **STEP 4: Click confirm once ready to initiate the transaction.**
>
> **Note: if this is your very first time interacting with pool pipes you will need to confirm an approval transaction at first so you will see 2 requests to confirm. Here’s a sample sETH-&gt;sUSD pool piping transaction: https://etherscan.io/tx/0xf3029af4efae7a82aff195f1f4a3961f0b2fb5c24af8806cb0bc31a80a54abbc**

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fc7dac56b-53d0-4d1e-a07d-1f434ff93a68_1557x633.png)

### **Available Pool Pipes:**

![](../.gitbook/assets/curve-curve-pool-pipe.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fa5d7e93b-e8c4-4429-8bc4-b46ec861f8ba_1902x2732.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F824a2c4f-525d-4ba3-b87b-4f5d72a364de_1902x2732.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F835d1422-d3b4-458c-b8a2-f50771c93da2_1902x2732.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fb4a6785e-da0d-4fe2-b2a8-eee19808ad68_1902x2732.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F184318bb-a4cd-497f-af22-6a82e86411f6_1902x1680.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fff76026b-24e8-456f-82bb-8dcfb0d7b886_1902x1564.png)

![](https://cdn.substack.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F0d7d0a21-2510-4659-a3a4-159ac190cbd9_1902x1564.png)

> **While some of these may seem similar, each pipe contains optimizations to help you re-balance your assets with the least slippage.**

### **When to ‘pipe’ aka rebalance?**

Rebalance trigger parameters will differ based on your investment goals and risk profile but in general could be based one of these:

* **Shifts in liquidity provisioning incentives.**
  * We saw this example with SNX shifting some incentives from sETH pool on Uniswap to sUSD pool on Curve.
* **Shifts in trading activity within liquidity pools.**
  * As other pools start catching traction, liquidity providers could capture extra yield moving some assets to those pools.
  * _**Example**_: let’s say you are currently providing liquidity in the DAI/ETH pool on Uniswap V1 which currently averages ~$750K in daily exchange volume with ~$5.5M total liquidity supplied. As you might already know, fees generated from exchanges are proportionally split between all the liquidity providers of that pool. So what you are really looking for are pools with the highest volume/liquidity ratio to generate the most fees per $ supplied. Doing a quick sort by Vol/Liq on Zapper’s Explore Opportunities table, we can see how USDC/ETH pool is a great alternative as the volume is higher while total liquidity supplied is roughly the same. Also, this pool pair retains your previous pool’s asset exposures \(ETH+STABLECOIN\). Keep in mind, some trading activity spikes might be temporary so it’s important to analyze longer time frames to get better average estimates.
* **General market shifts.**
  * As prices of underlying assets change, liquidity providers could diversify by reallocating liquidity between pegged and stable pools.
  * _**Example:**_ let’s say you are currently providing liquidity in the WETH/ETH pool on Uniswap \(aka ETH pegged pool\) and ETH price just doubled in the last 24 hours. You might anticipate some pull-back so you want to sell some of your ETH. But instead of simply selling, you could rebalance some of your liquidity straight into the highest yield generating stable pool on Curve. Now while you are waiting to ‘buy the dip’, your stablecoins are generating fees. To buy back in simply rebalance back into the WETH/ETH pool.
* **Pool yield optimizations.**
  * As any yield hacker knows, opportunities in DeFi need to be capitalized ASAP. With pool piping, it’s never been easier to move liquidity around the DeFi ecosystem. Each pool pipe is a general smart contracts so once a pipe is deployed between two underlying platforms, anyone is able to instantly move liquidity between ANY pools within those platforms. Builders could deploy their own auto-rebalancing logic which uses pool pipes to shift liquidity based on set logic.

