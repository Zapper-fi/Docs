# ⚡️🔏How to Zap directly from your Gnosis Safe

**Total value stored in all Gnosis Safe contracts recently crossed $1 billion🚀**

{% embed url="https://twitter.com/gnosisSafe/status/1297922743942307840?s=20" %}

It’s become the go to tool for teams to secure company crypto assets by requiring multiple signatures to manage funds. [Here’s a quick video tutorial on how to set up a wallet for your team with Gnosis.](gnosis.md)

Once signed in, their web app enables easy interactions with existing DeFi applications such as Aave, Balancer and Synthetix. [While Zapper is finalizing a direct integration within this ‘APPS’ section](https://github.com/Zapper-fi/GECO/blob/master/Proposals/Zapper.md), we wanted to share a tutorial on how you could interact with Zap contracts directly from your Gnosis Safe via their custom transaction builder.

![](../.gitbook/assets/image%20%2816%29.png)

 **At first, you need to decide which opportunity you would like to ‘Zap’ into and which asset you will be depositing with.**

You can find a list of available opportunities on [zapper.fi/invest](https://zapper.fi/invest) and a list of corresponding Zap contracts on [docs.zapper.fi/build/smart-contracts.](https://docs.zapper.fi/build/smart-contracts) Each generalized DeFi action has a dedicated Zap contract. For example, adding liquidity to any liquidity pool on Uniswap V2 using a single asset could be executed via a general Unipool Zap by calling the _ZapIn_ function with pre-filled parameters to specify which pool you are joining, with what asset, and where the liquidity pool token proceeds should be sent \(with this last one you could actually redirect the Zap proceeds to be sent to a third party if you want to\).

If you are using ETH as your deposit - you are able to call the contract function directly and make your deposit but if you are using ERC20 tokens \(DAI, LINK, SNX, YFI, etc.\), you will first need to approve the chosen Zap contract to use them.

**ADDING LIQUIDITY to the $YFI/$ETH POOL on UNISWAP V2 with $DAI:**

1. Look up $DAI token contract on Etherscan: 0x6b175474e89094c44da98b954eedeac495271d0f
2. Paste in DAI token contract address into Multisend transaction builder on Gnosis
3. Select Approve function
4. Look up Zap contract for adding liquidity to uniswap V2 pools address: 0x80C5e6908368CB9db503bA968d7ec5A565BFb389
5. Paste int Zap contract address under _usr\(address\)_
6. Enter how many DAI tokens you would like to approve the Zap contract for \(this means you will be able to Zap in up to this amount in DAI. Keep in mind its in wad so for 100 DAI you would enter _1000000000000000000_ 
7. _Click send Transaction_
8. _Now paste the Zap contract on top._
9. _Select ZapIn function_
10. For _\_toWhomToIssue \(address\):_ Enter wallet address where you want to send proceeds to \(usually this is your address\)
11. \_FromTokenContractAddress \(address\): Enter DAI contract address
12. For \_ToUnipoolToken0 \(address\): Enter YFI token contract 
    1. address
13. \_ToUnipoolToken1 \(address\): Enter WETH token contract address
14. For \_amount \(uint256\): Enter how many DAI you want to deposit
15. For \_minPoolTokens \(uint256\): Enter min \# of pool tokens you wish to receive otherwise transaction reverts in order to avoid slippage.

\*\*\*\*



