# Smart Contract Interface

## ETH Mainnet

| Contract | Description | Address | ABI |
| :--- | :--- | :--- | :--- |
| Unipool Remove Liquidity | Remove liquidity from Uniswap | [0x4316e3aD83ca2Cf0ea5e3b25e3DE2fA7F93cfE9c](https://etherscan.io/address/0x4316e3ad83ca2cf0ea5e3b25e3de2fa7f93cfe9c) | [ABI](https://gist.github.com/suhailgme/bbf5da6474c26c1d3f43838b2a835f56) |
| Unipool Add Liquidity With ETH | Add liquidity to Uniswap | [0x97402249515994Cc0D22092D3375033Ad0ea438A](https://etherscan.io/address/0x97402249515994cc0d22092d3375033ad0ea438a) | [ABI](https://gist.github.com/suhailgme/7ad05d8d1ee633973a427f923caea940) |
| Unipool Add Liquidity With ERC20 | Add liquidity to Uniswap | [0x4f026054B9C934D92cD2db344ea1ae193A22067d](https://etherscan.io/address/0x4f026054b9c934d92cd2db344ea1ae193a22067d) | [ABI](https://gist.github.com/suhailgme/6aab72c8fdb37492e2207ac11483dc34) |
| LLP General | Add Liquidity to Uniswap, Leverage Long 2X | [0x705637f340667EE03EfDa280C8F054976A5DBAF6](https://etherscan.io/address/0x705637f340667ee03efda280c8f054976a5dbaf6) | [ABI](https://gist.github.com/suhailgme/2aa2953d0edfe655064927bbe69cd6d0) |

## Usage

Our contract interface uses the function 'LetsInvest\(\)' for all Zap Ins.

**Zapping In to the sETH Unipool With ETH**

```
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



