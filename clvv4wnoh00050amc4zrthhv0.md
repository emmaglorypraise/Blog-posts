---
title: "How To Integrate INTMAX Wallet In Your dApp Using Intmax-walletsdk"
datePublished: Mon May 06 2024 15:46:32 GMT+0000 (Coordinated Universal Time)
cuid: clvv4wnoh00050amc4zrthhv0
slug: how-to-integrate-intmax-wallet-in-your-dapp-using-intmax-walletsdk
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1712977647954/3e0644df-02d6-4db9-b4f7-86be4cd4aca0.png
tags: tech, web3, wallet

---

Decentralized applications (dApps) are at the forefront of the blockchain revolution because they are the window into the web3 world. The importance of DApps cannot be overstated, as they represent the bridge between the traditional web and the decentralized web, where users have control over their data and interactions.

One of the critical components of DApps is the wallet connector, which facilitates the interaction between the DApp and the user's wallet. This connection is essential for authenticating users and ensuring transactions are securely executed on the blockchain.

However, the current landscape of DApp/Wallet connectors faces challenges, as connecting to web wallets has been a hassle. This complexity arises from the variety of wallet types and the intricacies of establishing a secure and seamless connection between DApps and user wallets. To address this issue `intmax-walletsdk` was created. `intmax-walletsdk` is built to enable direct communication and connection between web-based wallets and dApps, leveraging the power of EIP1193-like interactions to enhance user experiences across the blockchain ecosystem. This SDK allows you to easily connect your web3 dApp to any web wallet. By simplifying the integration process, `intmax-walletsdk` not only makes it easier for both wallet and dapps developers to build but also enhances the user experience by providing a more straightforward and secure method for wallet authentication and interaction.

In this article, we will delve into the process of building a simple dApp for conducting decentralized sports voting, using Vite, React, TypeScript, and `intmax-walletsdk`  for wallet authentication and connection. This DApp will demonstrate the simplicity of integrating the INTMAX Wallet into a DApp. By following the steps outlined in this guide, we aim to show that building a DApp and connecting it to the INTMAX Wallet doesn't have to be hard and is, in fact, very simple.

## **Prerequisites**

* Node.js 18.0+
    
* Familiarity with the command line interface.
    

## **Building the dApp**

### **Step 1: Setting Up the Project**

We start by creating a new React project with Vite and TypeScript, ensuring that we have a solid foundation for our application. This is done by running the following commands in the terminal:

```bash
npm create vite@latest my-voting-dapp -- --template react-ts
cd my-voting-dapp
npm install
npm run dev
```

This command creates a new React project named `my-voting-dapp`

### **Step 2: Integrating Wallet Authentication**

To enhance our dApp's functionality, we integrate a wallet SDK, specifically `intmax-walletsdk`, which enables users to connect their INTMAX wallets and cast their votes. This step is crucial for authenticating users and ensuring that each wallet can only vote once, thereby maintaining the integrity of the voting process. This is done by running this command in the terminal:

```bash
npm install intmax-walletsdk
```

### **Step 3: Creating the Voting Component**

The core of our dApp is the voting component, where users can select their favorite club and submit their votes. This component is designed with simplicity in mind, featuring a straightforward interface that allows users to easily interact with the dApp.

Create a component folder in the `src` directory of your project. and then create a new file named `Voting.tsx` inside. Copy and paste the provided code for the `Voting` component into this file. This component will include options for users to select their favorite club and a button to submit their vote.

```typescript
// src/components/Voting.tsx

import { useState } from 'react';

const Voting = () => {
  const [selectedClub, setSelectedClub] = useState('');
  const [voteCounts, setVoteCounts] = useState<Record<string, number>>({ ClubA: 0, ClubB: 0, ClubC: 0 });
  const [accounts, setAccounts] = useState<string[]>([]);
  const [result, setResult] = useState<string>("");
  const [votedAddresses, setVotedAddresses] = useState<string[]>([]);

  const truncateAddress = (address) => {
    return address.length > 8 ? `${address.substring(0, 8)}...` : address;
  };

  return (
    <div className="flex flex-col items-center min-h-screen bg-gray-100">
      <div className="w-full bg-blue-500 p-4 flex justify-between items-center sticky top-0 z-10">
        <h1 className="text-2xl font-bold text-white">Sports Voting </h1>
        <button
          onClick={handleConnect}
          className="bg-white hover:bg-gray-200 text-black font-bold py-2 px-4 rounded"
        >
          {accounts.length > 0 ? `Connected: ${truncateAddress(accounts[0])}` : 'Connect Wallet'}
        </button>
      </div>

      <div className='flex flex-col justify-center items-center mb-[60px] mt-[100px]'>
        <h1 className="text-4xl font-bold mb-8 px-1">Vote for Your Favorite Club</h1>

        <div className="flex flex-col space-y-1 sm:flex-row sm:space-x-4">
          {['Club A', 'Club B', 'Club C'].map(club => (
            <div
              key={club}
              className={`relative p-4 w-[200px] h-[200px] hover:border-blue-500 group`}
              onClick={() => {
                setSelectedClub(club);
                handleSignMessage(club);
              }}
            >
              <img
                src={`/assets/${club.toLowerCase().replace(' ', '')}.png`}
                alt={club}
                className="absolute inset-0 w-full h-full object-cover bg-black"
              />
              <div
                className={`absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity`}
              >
                <p className="text-white text-center ">Vote for {club}</p>
              </div>
            </div>
          ))}
        </div>

        <div className="flex flex-col space-y-0 sm:flex-row sm:space-x-4 mt-8">
          {['Club A', 'Club B', 'Club C'].map(club => (
            <div key={club}>
              <p className="text-center">{club} Votes: {voteCounts[club]}</p>
            </div>
          ))}
        </div>

        <div className='flex flex-col justify-center items-center mt-[70px]'>
          <h1 className="text-4xl font-bold mb-4">How to Vote</h1>
          <div className="bg-white p-6 rounded shadow">
            <h2 className="text-2xl font-bold mb-4">Steps to Connect and Vote:</h2>
            <ol className="list-decimal list-inside">
              <li className="mb-2">Click on the "Connect Wallet" button.</li>
              <li className="mb-2">Login to your INTMAX Wallet.</li>
              <li className="mb-2">Connect your wallet to the DApp.</li>
              <li className="mb-2">Choose your favorite club from the options.</li>
              <li className="mb-2">Click on the club to cast your vote.</li>
            </ol>
          </div>
        </div>
      </div>

    </div>
  );
};

export default Voting;
```

Import the Voting component in App.tsx with the code below:

```typescript
// App.tsx
import Voting from './components/Voting'

function App() {

  return (
    <>
      <div>
        <Voting/>
      </div>
    </>
  )
}

export default App
```

### **Step 4: Connecting to the INTMAX Wallet**

Connecting our dApp to INTMAX Wallet is a seamless process, thanks to the `intmax-walletsdk` library.

First, you need to import the `intmaxDappClient` from the `intmax-walletsdk/dapp` package. This client will be responsible for handling the connection and authentication process with the INTMAX Wallet.

```typescript
// src/components/Voting.tsx

import { ethereumProvider, intmaxDappClient } from "intmax-walletsdk/dapp";
```

Next, configure the `intmaxDappClient` by setting up the necessary parameters. These parameters include the name of your DApp, the URL of the wallet you wish to connect to, the metadata of your DApp, and a provider.

```typescript
// src/components/Voting.tsx

const DEFAULT_WALLET_URL = "https://wallet.intmax.io";
const DEFAULT_DAPP_ICON = `${window.location.origin}/vite.svg` as string;
const DAPP_METADATA = {
  name: "INTMAX Dapp Example",
  description: "This is a simple example of how to use the sdk dapp client.",
  icons: [DEFAULT_DAPP_ICON],
};

const createsdk = (walletUrl: string) => {
  return intmaxDappClient({
    wallet: { url: walletUrl, name: "INTMAX Wallet", window: { mode: "popup" } },
    metadata: DAPP_METADATA,
    providers: { eip155: ethereumProvider() },
  });
};

const sdk = createsdk(DEFAULT_WALLET_URL);
```

The `createsdk` function initializes the INTMAX Wallet SDK with the default wallet URL and metadata.

Next, we create a `handleConnect` function. Inside the `handleConnect` function, we use the SDK to request accounts from INTMAX Wallet. We then save the account in the React state to be used in the dapp. When the "Connect Wallet" button is clicked, it triggers the `handleConnect` function.

```typescript
// src/components/Voting.tsx

const handleConnect = async () => {
    const ethereum = sdk.provider("eip155");
    await ethereum.request({ method: "eth_requestAccounts", params: [] });
    const accounts = (await ethereum.request({ method: "eth_accounts", params: [] })) as string[];
    setAccounts(accounts);
  };
```

Next, we create a `handleSignMessage` function which signs a message with the user's account to cast a vote for the selected club. The selected club is passed to this function when a user clicks on it. After signing the message, the vote count for the selected club is incremented.

```typescript
// src/components/Voting.tsx
const handleSignMessage = async (club: string) => {
    if (accounts.length === 0) await handleConnect();
    const ethereum = sdk.provider("eip155");
    const _accounts = (await ethereum.request({ method: "eth_accounts", params: [] })) as string[];
    const currentAccount = _accounts[0];

    if (votedAddresses.includes(currentAccount)) {
     alert("You have already voted.");
     return;
    }

    const result = await ethereum.request({ method: "eth_sign", params: [currentAccount, "Vote " + club] });

    setResult(result as string);
    setVoteCounts(prev => ({ ...prev, [club]: (prev[club] || 0) + 1 }));
    setVotedAddresses(prev => [...prev, currentAccount]);
  };
```

### **Step 5: Styling**

Feel free to add your styles to customize the appearance of the DApp. To install Tailwind as used in this project, follow this guide on their official website [here](https://tailwindcss.com/docs/guides/vite). For the exact code, check the Github repo [here](https://github.com/emmaglorypraise/Sports-Voting-Demo/).

### **Step 6: Running the DApp**

Start the development server by running:

```bash
npm run dev
```

Open your browser and navigate to `http://localhost:5172` to view the voting DApp.

That's it! Your dApp should look like this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713036318469/7e7554da-4a5f-4f35-9f76-ed12214437e9.png align="center")

You've successfully built a simple voting DApp using React, Vite, Typescript, and the INTMAX Wallet SDK, allowing users to vote for their favorite sports club by connecting to their INTMAX Wallet. To get the full code, please check the GitHub repo [here](https://github.com/emmaglorypraise/Sports-Voting-Demo/).

## **Conclusion**

Building a decentralized voting platform (dApp) and integrating the INTMAX Wallet is a straightforward process that doesn't require extensive knowledge of blockchain technology. The steps outlined in this article provide a clear pathway for developers to create a functional app that allows users to vote securely and transparently.

The simplicity of this process underscores the potential of blockchain technology to revolutionize the way we interact with digital platforms. By making it easy to build and connect dApps to the blockchain, we open up new possibilities for innovation and user engagement. As the blockchain ecosystem continues to grow, we can expect to see more sophisticated dApps being developed, further showcasing the power and versatility of decentralized applications.

## **Quick Links**

* Learn more about Intmax-walletsdk: [https://intmax-wallet.gitbook.io/intmax-walletsdk](https://intmax-wallet.gitbook.io/intmax-walletsdk)
    
* Live demo: [sports-voting-demo.vercel.app](https://sports-voting-demo.vercel.app/)
    
* Full code in Github Rep: [emmaglorypraise/Sports-Voting-Demo (github.com)](https://github.com/emmaglorypraise/Sports-Voting-Demo/)