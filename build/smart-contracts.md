# 📄Smart Contracts

## Mainnet

| Contract | Description | Address | ABI |
| :--- | :--- | :--- | :--- |
| Uniswap V1 Add Liquidity With ETH | Add liquidity to any liquidity pool on Uniswap V1 using just ETH | [0x97402249515994Cc0D22092D3375033Ad0ea438A](https://etherscan.io/address/0x97402249515994cc0d22092d3375033ad0ea438a) | [ABI](https://gist.github.com/suhailgme/7ad05d8d1ee633973a427f923caea940) |
| Uniswap V2 Add Liquidity With ETH | Add liquidity to any liquidity pool on Uniswap V1 using just ETH | [0xEEE503B78e96F24c47c9AD8c287990e51697A99c](https://etherscan.io/address/0xEEE503B78e96F24c47c9AD8c287990e51697A99c) |  |
| Uniswap V1 Add Liquidity With ERC20 | Add liquidity to any liquidity pool on Uniswap V1 using any ERC20 token | [0x4f026054B9C934D92cD2db344ea1ae193A22067d](https://etherscan.io/address/0x4f026054b9c934d92cd2db344ea1ae193a22067d) | [ABI](https://gist.github.com/suhailgme/6aab72c8fdb37492e2207ac11483dc34) |
| Multi-Pool Uniswap | Add Liquidity Multiple Uniswap V1 Pools at the same time | [0x705637f340667EE03EfDa280C8F054976A5DBAF6](https://etherscan.io/address/0x7f1cd65679d73eb98fcebe8b61c13d3d68605717) |  |
| Uniswap V1 Remove Liquidity | Remove liquidity from any liquidity pool on Uniswap V1 & receive just ETH or any ERC20 | [0x2fba0b21a553f0f268293be7abb07a54fffd2b02](https://etherscan.io/address/0x2fba0b21a553f0f268293be7abb07a54fffd2b02) |  |
| Curve Add Liquidity with ETH or ERC20 | Add liquidity to sUSD, y, BUSD, or PAX pools on Curve using just ETH or just ERC20s | [0x924Cc11Fd506fcE3dAB461AA71a6bb823669EcE3](https://etherscan.io/address/0xc4ec123cd61d8ca3ea1ee413d5cb0a95de6d34cd) |  |
| Curve Remove Liquidity | Remove liquidity from any Curve pool & receive just ETH or any ERC20 | [0x983dd5dc5a99ec27bb850b865ca99407b38722bf](https://etherscan.io/address/0x983dd5dc5a99ec27bb850b865ca99407b38722bf) |  |
| Curve &lt;&gt; Curve Pool Pipe | Rebalance liquidity between liquidity pools on Curve | [0x83c32BF929F80e404ff30Ede7333271460b13cd9](https://etherscan.io/address/0x83c32BF929F80e404ff30Ede7333271460b13cd9) |  |
| Uniswap V1 &lt;&gt; Curve Pool Pipe | Rebalance liquidity between Uniswap V1 & Curve liquidity pools  | [0x66895417881B1d77Ca71bd9e5Ba1E729f3Aa44D3](https://etherscan.io/address/0x66895417881B1d77Ca71bd9e5Ba1E729f3Aa44D3) |  |
| Uniswap V1 &lt;&gt; Uniswap V1 Pool Pipe | Rebalance liquidity between Uniswap V1 liquidity pools  | [0xaecCd58001D52B4b931FD6FD5bF87D4F911100B7](https://etherscan.io/address/0xaecCd58001D52B4b931FD6FD5bF87D4F911100B7) |  |
| Uniswap V1 &lt;&gt; Uniswap V2 Pool Pipe | Rebalance liquidity between Uniswap V1+V2 liquidity pools | [0x6d313883c6db5ea58bdd5546f403f1fe27e92690](https://etherscan.io/address/0x6d313883c6db5ea58bdd5546f403f1fe27e92690) |  |

## Deprecated

| Contract | Description | Address | ABI |
| :--- | :--- | :--- | :--- |
| Uniswap V1 Add Liquidity With ETH | Add liquidity to any liquidity pool on Uniswap V1 using just ETH | [0x606563f8DC27F316b77F22d14D9Cd025B4F70469](https://etherscan.io/address/0x606563f8dc27f316b77f22d14d9cd025b4f70469) |  |
| Uniswap V1 Remove Liquidity | Remove liquidity from any liquidity pool on Uniswap V1 & receive just ETH or any ERC20 | [0x4316e3aD83ca2Cf0ea5e3b25e3DE2fA7F93cfE9c](https://etherscan.io/address/0x4316e3ad83ca2cf0ea5e3b25e3de2fa7f93cfe9c) |  |
| Uniswap V1 Add Liquidity With ERC20 | Add liquidity to any liquidity pool on Uniswap V1 using any ERC20 token | [0xF0cd9981F15695324763A06869d1c1DD90073C2A](https://etherscan.io/address/0xf0cd9981f15695324763a06869d1c1dd90073c2a) |  |

## Usage

Our contract interface uses the function 'LetsInvest\(\)' for all Zap Ins.

**Zapping In to the sETH Unipool With ETH**

```text
import Web3 from "web3";

// A copy of the contract ABI is required
import UniGenContract from "../UnipoolGeneralContract.json";
const UniGenAddress = "0x97402249515994Cc0D22092D3375033Ad0ea438A";
const sethAddress = "0x5e74C9036fb86BD7eCdcb084a0673EFc32eA31cb";

const zapInWithEth = (value) =>{
    const valueToSend = web3.utils.toWei((+value).toFixed(18), "ether");
    const provider = window.ethereum || window.web3.currentProvider;
    const [account] = await window.ethereum.enable();
    web3 = new Web3(provider);

    const contract = new web3.eth.Contract(UniGenContract, UniGenAddress);

    tx = await contract.methods.LetsInvest(
      sethAddress,
      account // Recipient address (currently user's address)
    );
    tx.send({
      from: account,
      valueToSend
    });
}
```

**Zapping In to the sETH Unipool With DAI**

```bash
import Web3 from "web3";

import erc20ZapABI from "./ERC20toUniPoolZapV1_GeneralABI"; // DeFiZap's ERC20 Zap In ABI
import daiTokenABI from "./daiTokenABI"; // ERC20 ABI

const erc20ZapAddress = "0xF0cd9981F15695324763A06869d1c1DD90073C2A";
const sethAddress = "0x5e74C9036fb86BD7eCdcb084a0673EFc32eA31cb";
const daiAddress = "0x6B175474E89094C44Da98b954EedeAC495271d0F";

const zapInWithERC20 = async value => {
  const provider = window.ethereum || window.web3.currentProvider;
  const [account] = await window.ethereum.enable();
  web3 = new Web3(provider);

  const valueToSend = web3.utils.toWei((+value).toFixed(18), "ether");
  // Instantiate ERC20 Zap In Contract
  const erc20ZapContract = new web3.eth.Contract(erc20ZapABI, erc20ZapAddress);
  // Instantiate DAI ERC20 Token Contract
  const daiContract = new web3.eth.Contract(daiTokenABI, daiAddress);
  // Check if the erc20ZapContract has approval to spend user's DAI, get approval if needed
  let allowance = await daiContract.methods
    .allowance(account, erc20ZapAddress)
    .call({ from: account });
  if (+allowance < valueToSend) {
    let approveTx = await contract.methods.approve(
      erc20ZapAddress,
      web3.utils.toWei("100000000000000000000", "ether")
    );
    approveTx
      .send({
        from: account
      })
      // After approval TX has been sent, create TX Object for ERC20 Zap in
      .on("transactionHash", async txHash => {
        let tx;
        tx = await erc20ZapContract.methods.LetsInvest(
          account,
          daiAddress,
          valueToSend,
          sethAddress
        );
        let gas = 900000; // Gas Estimation will fail due to pending approval TX
        tx.send({
          from: account,
          gas
        }).on("transactionHash", txHash => {
          console.log(txHash);
        });
      });
    // Approval for required DAI already exists, create TX object and send it with gas estimate
  } else {
    tx = await erc20ZapContract.methods.LetsInvest(
      account,
      daiAddress,
      valueToSend,
      sethAddress
    );
    const gas = await tx.estimateGas({
      from: account
    });
    tx.send({
      from: account,
      gas
    }).on("transactionHash", txHash => {
      console.log(txHash);
    });
  }
};
```

## Usage example \(Curve to Curve Pipe\)

### Swap 5 CRV tokens \(sUSD\) for y Curve tokens

```text
import Web3 from "web3";

// A copy of the contract ABI is required
  import curveCurvePipeABI from "../curveCurvePipe.json";
  import ERC20ABI from "../ERC20.json"

  const web3 = new Web3(provider.wallet.provider);
  const address = provider.address;
  const curveCurvePipeAddress = '0x66895417881B1d77Ca71bd9e5Ba1E729f3Aa44D3';
  const curveCurvePipeContract = new web3.eth.Contract(curveCurvePipeABI, curveCurvePipeAddress);
  const crvTokenContract = new web3.eth.Contract(ERC20ABI, fromCurveTokenAddress);
  const valueToSend = (5 * 10 ** 18).toFixed(0); //Sending 5 CRV tokens
  const tx = await curveCurvePipeContract.methods.Curve2Curve(
    address,
    "a5407eae9ba41422680e2e00537571bcc53efbfd", //sUSD curve pool
    valueToSend,
    "bbc81d23ea2c3ec7e56d39296f0cbb648873a5d3" //y Curve pool
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


