# Smart Contract Interface

## ETH Mainnet

| Contract | Description | Address ||
| :--- | :--- | :--- | :--- |
| Curve to Curve Pipe | Pipe liquidity among Curve pools | [0x83c32BF929F80e404ff30Ede7333271460b13cd9](https://etherscan.io/address/0x83c32BF929F80e404ff30Ede7333271460b13cd9) |  
| Unipool-Curve Pipe | Pipe liquidity from Uniswap to Curve pools or from Curve pools to Uniswap pools | [0x66895417881B1d77Ca71bd9e5Ba1E729f3Aa44D3](https://etherscan.io/address/0x66895417881B1d77Ca71bd9e5Ba1E729f3Aa44D3) | 
| Unipool-Unipool Pipe | Pipe liquidity among Curve pools | [0xaecCd58001D52B4b931FD6FD5bF87D4F911100B7](https://etherscan.io/address/0xaecCd58001D52B4b931FD6FD5bF87D4F911100B7) | 
| Curve Remove Liquidity | Remove liquidity from Curve. Recieve ETH or Stablecoin | [0x983dd5dc5a99ec27bb850b865ca99407b38722bf](https://etherscan.io/address/0x983dd5dc5a99ec27bb850b865ca99407b38722bf) | 

## Usage example (Curve to Curve Pipe)

```
import Web3 from "web3";

// A copy of the contract ABI is required
  import curveCurvePipeABI from "../curveCurvePipe.json";
  import ERC20ABI from "../ERC20.json"
  const web3 = new Web3(provider.wallet.provider);
  const address = provider.address;
  const curveCurvePipeAddress = '0x66895417881B1d77Ca71bd9e5Ba1E729f3Aa44D3';
  const curveCurvePipeContract = new web3.eth.Contract(curveCurvePipeABI, curveCurvePipeAddress);
  const crvTokenContract = new web3.eth.Contract(ERC20ABI, fromCurveTokenAddress);
  const balance = await getTokenBalance(web3, address, fromCurveTokenAddress);
  let valueToSend;
  if (+value >= formatDecimals(web3.utils.fromWei(balance), 6)) valueToSend = balance;
  else valueToSend = (value * 10 ** 18).toFixed(0);
  const tx = await curveCurvePipeContract.methods.Curve2Curve(
    address,
    fromCurveExchangeAddress,
    valueToSend,
    toTokenAddress
  );
  const allowance = await getAllowance(web3, fromCurveTokenAddress, address, curveCurvePipeAddress);
  if (allowance < value) {
    const approvalAmount = '100000000000000000000';
    let approveTx = await crvTokenContract.methods.approve(
      curveCurvePipeAddress,
      web3.utils.toWei(approvalAmount, 'ether')
    );
    approveTx
      .send({
        from: address,
        gasPrice,
      })
      .on('transactionHash', async (txHash) => {
        await sendTransaction(address, 0, tx, gasPrice, 2000000); // Rely on nonce for tx ordering to avoid waiting for approval to confirm
      });
  } else await sendTransaction(address, 0, tx, gasPrice); // Contract already has approval, gas estimates will not fail
};
```


