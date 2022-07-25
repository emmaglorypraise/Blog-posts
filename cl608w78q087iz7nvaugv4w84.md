## Ethereum 101

Ethereum, is a decentralized computing platform that is open source and available worldwide. Smart contracts are computer programs that run on and the system's state updates are synchronized and stored on a blockchain, and the execution resource costs are metered and constrained using its cryptocurrency Ether(ETH).

Ethereum is a deterministic but fundamentally unlimited state machine and It consists of a globally accessible singleton state and a virtual machine that updates that state.

Using the Ethereum platform, programmers can create robust, decentralized applications with integrated economic features. It not only offers high availability, auditability, transparency, and impartiality but also lessens or completely does away with censorship and some counterparty concerns.

A peer-to-peer network connecting participants, a Byzantine fault-tolerant consensus algorithm for synchronizing state updates (a proof-of-work blockchain), the use of cryptographic primitives like digital signatures and hashes, and a digital currency(ether) are just a few of the similarities between Ethereum and other open blockchains . The goal and design of Ethereum, however, are very different from those of the open blockchains that came before it, such as Bitcoin, in a number of important ways.

The components of the Ethereum Blockchain includes:

- #### P2P Network
The ÐΞVp2p. protocol is used by Ethereum, which runs on the Ethereum main network, and is accessible at TCP port 30303.
- #### Consensus rules
 The Yellow Paper, the standard specification, contains a specification of Ethereum's consensus rules 
- #### Transactions 
Network messages sent via the Ethereum network typically contain a sender, recipient, value, and data payload amongst other things.
- #### State machine 
The Ethereum Virtual Computer (EVM) is a stack-based virtual machine that runs bytecode (machine-language instructions) and processes Ethereum state changes. The "smart contracts" that run on the EVM are written in high-level languages (like Solidity) and compiled to bytecode.
- #### Data structures 
The state of Ethereum is kept locally on each node in the form of a database, which houses the system state and transactions in a serialized hashed data structure known as a Merkle Patricia Tree.
- #### Consensus algorithm 
To determine the longest chain and subsequently the current state, Ethereum adopts the Nakamoto Consensus model(Bitcoin’s consensus model), which uses sequential single-signature blocks that are weighted in importance by PoW(Proof of Work). But there are future plans to switch to the  PoS(Proof of Stake) weighted voting method(Casper).
- ####  Economic security 
Ethereum currently uses a PoW algorithm called Ethash, but will eventually be abandoned in favor of PoS(Proof of Stake) at some time in the future.
- #### Clients 
Ethereum has a number of compatible client software implementations, the most well-known of which is Go-Ethereum(Geth) and Parity.

Note: Ethereum is a Turing-complete system because it can read and write data to memory while running a stored program in a state machine called the Ethereum Virtual Machine.

The Ethereum Virtual Machine(EVM), an emulated computer, is used to run smart contracts, which are computer programs, and Ether is intended to be used to pay for their execution . 

Ether, often known as "ETH" or with the symbol Ξ(derived from the Greek letter "Xi," which resembles a stylised capital E), is the name of the money used by Ethereum.
Wei is the smallest unit of Ether. Wei (1 * 1018 or 1,000,000,000,000,000,000) is equal to one Ether.

Every Ethereum transaction needs to be validated by miners, who charge a fee for their services, a virtual currency called gas is used to pay the fees. As part of every transaction, you use ether to pay for the gas. it must be specifically defined for the purchase of gas, and there must be a reasonable gas price. The gas price changes depending on the type of transaction and other factors. The gas limit is set at the cost of sending a basic transaction, which is 21,000 gas units.  

After gas is purchased for the transaction, the computation is carried out, and any leftover gas is reimbursed to the transaction's sender. Gas permits Turing-complete computation while restricting the amount of resources that every program may utilize. 

Your entry point into the Ethereum network is an Ethereum wallet. It can create and broadcast transactions on your behalf, and it keeps your keys. In Ethereum, keys come in pairs consisting of a private (secret) key and a public key. 

A common misconception about Ethereum is that Ethereum wallets contain ether or tokens. Ethereum wallets contain keys, not ether or tokens. Wallets are like keychains containing pairs of private and public keys. Users sign transactions with the private keys, thereby proving they own the ether. The ether is stored on the blockchain.

## The Four Stages of Ethereum's Development
There are four stages in the creation of Ethereum, and each stage saw major changes. A stage may contain "hard forked" subreleases that modify functionality in a non-backwards compatible way.

A hard fork is a significant update or modification to a network protocol that renders transactions and blocks that were previously invalid valid or invalid. Two branches emerge from it, one that adheres to the old protocol and the other to the new one.

Token holders in the original Blockchain will also receive tokens in the new fork, but miners must decide which Blockchain to keep validating.

The four main development stages are codenamed Frontier, Homestead, Metropolis, and Serenity. 
- ### Frontier Stage(Block #0)
Due to the technical nature of the network's interaction interface, the original stage of the Ethereum project, which lasted from July 30, 2015, to March 2016, was primarily targeted at those with technical backgrounds. The interface for combining ethers, uploading, and running ether contracts, came in the form of a command line. Mining could be set up and started by miners. Ether could be traded on trade exchanges.
- ### Homestead Stage(Block #1,150,000)
In March 2016, Ethereum's second phase was released. Ethereum took a step further by providing numerous protocol upgrades to speed up network transactions. More blocks were activated during this phase, which also laid the groundwork for upcoming improvements.
- ### Metropolis Stage(Block #4,370,000)
The third Ethereum stage is called Metropolis. October 2017 saw the launch. The network will undergo modifications throughout the Metropolis stage, including as the addition of security updates and a higher level of smart contract automation. By releasing programs that do not require the local download of the complete blockchain, this phase will also make the platform simpler for the average user. There are two stages in Metropolis: 
- #### Byzantium.
The first phase of Metropolis, Byzantium, modifies the block reward and difficulty while providing low-level capabilities.
-  #### Constantinople / St. Petersburg(Block #7,280,000)
It was intended for Constantinople to be the continuation of Metropolis with comparable enhancements. A serious bug was found just before it was activated. As a result, the hard fork was delayed and given the new name St. Petersburg.
- ### Serenity Stage
The Serenity development stage of Ethereum is final stage of development. Serenity entails a fundamental restructure of the infrastructure, making Ethereum faster, more efficient, and easier to understand for newbies. There will also be a switch from the Proof of Work method to the Proof of Stake approach in an effort to save energy. It is presented as "Ethereum 2.0," the updated version of Ethereum.

I wish you would realize there is more to Ethereum. First off, Ethereum has other purposes outside serving as a payment network for cryptocurrencies. The Ethereum platform's utility currency, Ether, is used to pay for access to the Ethereum platform as the world computer, even though it is essential to and required for Ethereum to function. I would discuss further aspects of the Ethereum Blockchain in subsequent articles.

Till I come your way again,

Adios



