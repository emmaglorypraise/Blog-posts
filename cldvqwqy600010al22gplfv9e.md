# EIP 1559 - Fee market change

EIP 1559, or Ethereum Improvement Proposal 1559, is a change to the Ethereum network that seeks to improve its scalability, optimize the previous transaction fee market, lower the high transaction fees that users must pay, and enhance the user experience. On August 5, 2021, the proposal went live on the Ethereum network after being introduced in 2019.

## Introduction

For the past few years, EIP 1559 has been a hot topic in the Ethereum community, with developers, investors, and consumers all interested in how it turns out. The plan was developed as a remedy for the scalability and fee problems that have dogged the Ethereum network ever since it was created.

The previous fee market on the Ethereum network was adopted from the transaction fee mechanism first proposed by Bitcoin.

Simply put, this mechanism is a first-price auction where

(i) each user bids a transaction fee associated with the transaction,

(ii) the miner chooses which transactions to include in the block, and

(iii) the miner gets all the transaction fees that users bid in the block.

However, first-price auctions may require users to either overpay transaction fees or have a long waiting time. In particular, in periods of high demand, transaction fees can be volatile, making it difficult for users to make the right bid. If we overbid, we end up overpaying. If we bid low, we may experience a long waiting time.

Due to the high fees associated with this system during periods of increased demand, it is now challenging for users to perform transactions on the network.

EIP 1559's key feature is the introduction of a new adaptable and effective fee system that would alter how transaction fees are calculated and paid on the Ethereum network, where the costs are automatically determined by the network rather than by specific users or miners. This approach aids in reducing the exorbitant prices and protracted confirmation times that frequently happen during times of heavy network demand.

## How it works

Instead of an auction-based system, EIP 1559 would introduce a base fee that would be burned, meaning it would be permanently removed from circulation. Users would be able to estimate how much they would have to spend to transact on the network thanks to the base fee's dynamic adjustment based on network usage.

Users may also choose to bid on two extra parameters, the max priority fee per gas ("tip") and the max fee per gas ("cap"), in their transactions in addition to the base charge that is required. Users tip miners to prioritize their transactions using priority fees. The max fees that users will be required to pay include both base fees and priority fees. As a result, the gas price can be calculated as

**min(base fee + max priority fee, max fee)**

The user will receive a refund for any difference between the maximum fee and the total of the base fee and priority fee.

So the priority fee is paid to the miners while the base fee is burned. Prior to EIP-1559, miners earned all the gas fees in a block. Hence, with the implementation of EIP-1559, tips are effectively required because miners may mine empty blocks since they do not earn the base fee.

Following EIP 1559, the total transaction fee is determined using the following formula:

***Total transaction fee = gas units (limit) x (base fee + tip)***

Let's analyze the formula above:

* **Gas units,** or gas limits, are defined in appendix “G” of the Ethereum yellow paper.
    
* The **base fee** is the minimum price per unit of gas for inclusion in the current block. Moreover, the network calculates the base fee according to the current demand for block space.
    
* The **priority fee** (tip) is there for users to give their transactions priority. Moreover, it is also part of the fee that rewards miners.
    

Think of the experience of using a cleaning service app on your phone to help you understand the base fee and priority fee. With this app, you can order laundry services. Regardless of which staff member picks up your items, the pricing for laundry service remains the same (the base fee in EIP-1559). Imagine for a moment that you could add a tip to your order before requesting the laundry service. A staff member will be motivated to pick up your laundry ahead of other possible customers who aren't leaving a tip if your tip is higher than what others are currently offering.

Similar to your ETH transactions, you can set a tip for miners (referred to as the "staff member" in the example above) to include your transaction in the next block (referred to as the "laundry pick up" in the example above). A higher tip increases the likelihood that your transaction will be included in the next block and be completed.

## Advantages of EIP 1559

EIP 1559 has several benefits, one of which is a decrease in the erratic nature of transaction fees on the Ethereum network. Users would no longer need to compete for block space and pay expensive prices during times of high demand because the base fee would be adjusted dynamically based on network usage.

Additional advantages of EIP 1559 include the following:

* Predictable fees: EIP-1559 made it possible for users to estimate fees more easily, despite the fact that it does not really lower the transaction fee level.
    
* Increased network efficiency: By managing network demand and preventing congestion, the base fee method helps to increase network efficiency. Lower costs and increased network efficiency are two ways that EIP 1559 seeks to improve the Ethereum user experience.
    
* Better user experience: With lower costs and increased network efficiency are two ways that EIP 1559 seeks to improve the Ethereum user experience.
    

This would improve user access to and use of the Ethereum network, particularly for individuals who are unable to afford the hefty transaction costs.

## Disadvantages of EIP 1559

EIP 1559, however, has downsides as well. The proposal's potential impact on the amount of revenue Ethereum miners make is one of the primary issues. For miners, the Ethereum network's present fee market mechanism provides a sizable amount of cash; the introduction of a base charge that is burned would mean a decrease in this revenue.

As a result, the network might have fewer miners, which would make it less secure and more vulnerable to attacks.

EIP 1559 implementation can be technically difficult, requiring collaboration and agreement across Ethereum ecosystem players.

To address these challenges, the Ethereum community is working to ensure that the implementation of EIP 1559 is as smooth and seamless as possible, through continued collaboration and communication among stakeholders.

## Conclusion

EIP 1559 is a modification to the Ethereum network that intends to increase its scalability and lower the high transaction fees that users must pay. The proposal includes a new fee mechanism that would alter how transaction costs are calculated and paid on the network, improving user access and usability. EIP 1559 marks a significant advancement for the Ethereum ecosystem with its adaptable and effective fee market mechanism, enhancing network performance and lowering user costs. To learn more about EIP 1559, visit the EIP proposal document [here](https://eips.ethereum.org/EIPS/eip-1559) or join the Ethereum community forums.