---
title: "Interacting with Smart Contracts Using INTMAX Wallet SDK and Ethers.js"
datePublished: Wed Sep 18 2024 23:47:57 GMT+0000 (Coordinated Universal Time)
cuid: cm18ijrwj001509la5yhebvro
slug: interacting-with-smart-contracts-using-intmax-wallet-sdk-and-ethersjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1726703170555/07cc33a9-4529-4cfe-ba8c-b8c9380af89f.png
tags: dapps, web3, smart-contracts, wallet, ethersjs, intmax

---

Smart contracts have revolutionized the way decentralized applications (DApps) operate by enabling automated, trustless agreements on the blockchain. To build robust DApps, developers often leverage powerful tools like **Ethers.js** and **INTMAX Wallet SDK**. In this tutorial, we'll walk you through how to install these libraries, connect to a smart contract, interact with it, and check the balance of an address using a practical example.

## **Prerequisites**

Before we begin, ensure you have the following:

* **Node.js and NPM** are installed on your machine.
    
* Frontend dApp built with **React.js/Vue.js/Angular**.
    
* Familiarity with **Ethereum** and **smart contracts**.
    

## **Installing Dependencies**

We'll need to install **Ethers.js** and **INTMAX Wallet SDK** to interact with the blockchain and manage wallet connections.

### 1\. Install INTMAX Wallet SDK

INTMAX Wallet SDK facilitates seamless wallet integration into your DApp.

```bash
npm install intmax-walletsdk
```

### 2\. Install Ethers.js

Ethers.js is a library for interacting with the Ethereum blockchain. It provides a simple and secure way to communicate with smart contracts.

```bash
npm install ethers
```

## **Connecting to INTMAX Wallet**

To interact with a smart contract, users need to connect their wallets. We'll use INTMAX Wallet SDK to handle wallet connections.

### Initialize the INTMAX DApp Client

First, set up the INTMAX DApp client with the necessary metadata, specifying the wallet URL and other details:

```typescript
import { intmaxDappClient, ethereumProvider } from "intmax-walletsdk/dapp";

const DEFAULT_WALLET_URL = "https://wallet.intmax.io";
const DEFAULT_DAPP_ICON = `${window.location.origin}/logo.png`; //directory of logo
const DAPP_METADATA = {
  name: "My Brand Name",
  description: "This is a simple example of how to use the SDK DApp client.",
  icons: [DEFAULT_DAPP_ICON],
};

const createSdk = (walletUrl) => {
  return intmaxDappClient({
    wallet: { url: walletUrl, name: "INTMAX Wallet", window: { mode: "popup" } },
    metadata: DAPP_METADATA,
    providers: { eip155: ethereumProvider() },
  });
};

const sdk = createSdk(DEFAULT_WALLET_URL);
```

### Handle Wallet Connection

Create a function to connect the user's wallet and retrieve their accounts:

```typescript
const handleConnect = async () => {
  const intmaxWalletProvider = sdk.provider("eip155:137"); // 137 is Polygon mainnet network
  await intmaxWalletProvider.request({ method: "eth_requestAccounts", params: [] });
  const accounts = await intmaxWalletProvider.request({ method: "eth_accounts", params: [] });
};
```

The `handleConnect` function requests account access from the user's wallet and updates the state with the connected accounts.

## **Interacting with the Smart Contract**

We'll use Ethers.js to interact with the smart contract. This includes reading data from the contract and sending transactions.

### Define the Smart Contract ABI and Address

First, define the ABI (Application Binary Interface) and the smart contract address. The ABI defines the smart contract's interface, and the contract address points to its location on the blockchain.

```typescript
import { ethers, Contract } from 'ethers';

const abi = [
  // ... (Your ABI here)
];

const contractAddress = "CONTRACT ADDRESS";
```

### Create a Contract Instance

Initialize the contract instance using Ethers.js:

```typescript
const currentAccount = accounts[0]; // connected wallet address from above
const provider = new ethers.JsonRpcProvider('https://polygon-mainnet.infura.io/v3/YOUR_INFURA_PROJECT_ID');
const signer = new JsonRpcSigner(provider, currentAccount);
const contract = new ethers.Contract(contractAddress, abi, signer);
```

## **Reading from Smart Contract**

In this section, we'll focus on reading data from the smart contract. Specifically, fetch vote counts for different clubs using the smart contract's `getClubVotes` function.

```typescript
const fetchVoteCounts = async () => {
          const votes = await contract.getClubVotes(clubId);
          console.log("Votes:", votes.toString());
}
```

The `getClubVotes` function from the smart contract is called for each club to retrieve the number of votes each club has received.

By using this approach, we can fetch data from the blockchain and display it to users.

## **Writing to Smart Contract**

Now, let’s explore how to interact with the smart contract by **writing** to it. Specifically, we’ll focus on casting a vote for a club using the `vote` function of the contract.

```typescript
const handleVote = async (club) => {
  // Connects with wallet account
  if (accounts.length === 0) await handleConnect();
  
  try {

    // Sending a transaction to vote for the selected club
    const result = await intmaxWalletProvider.request({
      method: "eth_sendTransaction",
      params: [{
        from: currentAccount,
        to: contractAddress,
        data: contract.interface.encodeFunctionData("vote", [clubId]),
        gasLimit: 300000,
      }]
    });

    // Check the new vote
    console.log("Result:", result);
  } catch (error) {
    console.error("Error voting:", error);
  }
};
```

The `handleVote` function interacts with the smart contract to cast a vote. Before any transaction can be made, the wallet must be connected using the `intmaxWalletProvider`. The `vote` function from the smart contract is invoked with the selected club’s ID, encoding the function call with `ethers` to create a transaction. The transaction is sent using the INTMAX wallet’s `eth_sendTransaction` method, ensuring the vote is cast on-chain. Remember that a contract instance was created above and is being used here including the provider and signer.

## **Checking Address Balance**

To check the balance of a specific address, use Ethers.js as follows:

```typescript
const checkAccountBalance = async () => {
  try {
    const balanceInWei = await provider.getBalance(currentAccount);
    const balance = ethers.formatEther(balanceWei);
    console.log("Balance in Polygon:", balance);
  } catch (error) {
    console.error("Error fetching balance:", error);
  }
};
```

We use `getBalance` to fetch the balance of the address on the Polygon network, converting the result from wei (the smallest unit) to ether. Note, that the balance gotten would be the balance of whatever native token of the selected network.

## **Complete Code Example**

Below is the complete React component integrating INTMAX Wallet SDK and Ethers.js to interact with a smart contract and check the balance of an address.

* [https://github.com/emmaglorypraise/Sports-Voting-Demo](https://github.com/emmaglorypraise/Sports-Voting-Demo/blob/main/src/components/Voting.tsx)
    

## **Conclusion**

In this tutorial, we demonstrated how to use **INTMAX Wallet SDK** and **Ethers.js** to interact with a smart contract by reading data and writing transactions. We explored how to:

* **Read** from the contract to check vote counts and to check address balances.
    
* **Write** to the contract by casting votes through a wallet interaction.
    

By following these steps, you can build more complex and feature-rich decentralized applications that leverage the power of blockchain technology.

Remember to replace placeholder values like `YOUR_INFURA_PROJECT_ID` and ensure your smart contract's ABI and addresses are correctly configured.

Happy coding!

## **Quick Links**

* Learn more about Intmax Wallet SDK: [**intmax-wallet.gitbook.io/intmax-walletsdk**](https://intmax-wallet.gitbook.io/intmax-walletsdk)
    
* Live demo: [https://sports-voting-demo.vercel.app/](https://sports-voting-demo.vercel.app/)
    
* Full code in Github Repo: [https://github.com/emmaglorypraise/Sports-Voting-Demo](https://github.com/emmaglorypraise/Sports-Voting-Demo)
    
* Reach out to me on [**Twitter**](https://twitter.com/emmaglorypraise) if you have any questions.