# Troubleshooting

## Why are my tokens not showing in the Zapper Dashboard?
It's normally 1 of 2 reasons. We may not support the token and/or DeFi platform yet. It takes quite a bit of development work to properly support each new token and LP / yield farming / staking opportunity so it calculates your assets, LPs, and claimable assets. If you'd like to suggest we support your token and/or DeFi applications, go [here](https://features.zapper.fi/token-requests) to propose it or upvote an existing proposal.

Secondly, there's a chance you've staked (aka deposited) your token(s) into a yield farming opportunity and so you've transferred ownership of that token to another protocol we don't support yet. An example would be: "I'm an LP in Uniswap and I staked my LP token in a new yield farming application. I no longer see my Uniswap LP on my Zapper dashboard."


## My transaction has been pending on Etherscan for more than an hour. What's the deal and how do I fix this?
When you Zap liquidity, it normally requires multiple transactions (unless zapping ETH), which you'll be prompted to confirm. However, transactions on Ethereum compete to be confirmed through an auction-like process, bidding by gas price (shown as Gwei in your wallet). If the average bidding gas price is much higher than you selected under Speed before Confirming a Zap (see screenshot below) or when you modified the gas price in MetaMask, your transaction can get stuck. Sometimes, a Zap user can get unlucky choosing a gas price right as Ethereum gas prices skyrocket. It's a best practice and recommended to check gas prices at [ethgasstation.info](https://ethgasstation.info) before clicking Confirm.

Transactions submitted by an Ethereum address will processed sequentially. For example, if transaction #1 is stuck, transaction #2 will be stuck until #1 is confirmed on the blockchain. Here's a helpful video tutorial from DeFi Dad on how to fix a pending transaction (a.k.a un-stuck a stuck transaction).
