# Using Zaps

## Is it safe to Zap into all liquidity pools on Zapper?
We cannot provide financial advice, but we do our best to vet that Zaps lead users to smart contracts that are audited and developed by reputable DeFi teams. Please assume that there is always risk in zapping into any liquidity pool or yield farming opportunity via Zapper. Common risks to consider in the resulting exposure one can achieve through Zaps is smart contract risk (bugs), impermanent loss in LPs, liquidity crises in less liquid pools, admin risk, governance compromise risk, stablecoins de-pegging, tokenized BTC de-pegging, and systemic risk with how interwoven many DeFi apps and protocols are on Ethereum.

## Can I zap any token with a Zap?
Due to liquidity constraints with some tokens, ideally one is zapping one of the tokens in a liquidity pool. For such LPs, Zapper conveniently can split your liquidity provision into whatever proportion the LP calls for (ie 50/50 in Uniswap or maybe 80/20 in Balancer).
However, Zapper also magically can Zap a token not in the pool by swapping it first for a pool token. For example, in the ETH-DAI pool in Uniswap, one could zap in with USDC. Currently, we offer this convenience with more liquid tokens like ETH, DAI, USDC, USDT, and WBTC.

## Are there any fees besides standard Ethereum network transaction fees for using Zapper?
No, currently Zapper does not charge any fees besides the gas required to process your transaction on-chain. Zapper helps you save gas fees by bundling multiple DeFi actions into one transaction. 
