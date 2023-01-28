# Vulnerability #5 - Frontrunning Vulnerability

The distributed ledger of the blockchain does not instantaneously update with new transactions. They are gathered into blocks and only added to the ledger as a part of these blocks. A malicious node can view the transaction, determine its purpose, and create its own malicious request (transaction) based on the observed transaction before it is included in a block because the transaction is visible to the nodes as it is propagated to the network. Usually, the transaction fees are used to decide the order in which transactions are put to blocks. Blockchain users can determine their own costs, while most blockchains have a minimum charge.

This implies that a user has the option to pay for priority, by putting a higher fee on a transaction. This means that the miners have control over the order in which transactions execute and can mix early transactions with their late ones without broadcasting them. This could occur as a result of them trying to maximize their profits by adding transactions to blocks based on fees rather than the order in which they are received.

The scenario described above is the procedure that takes place during frontrunning.

## So what does "frontrunning" actually mean?

Decentralized systems, such as blockchain networks, are susceptible to frontrunning. It refers to the action of one party trying to acquire an unfair advantage over another by foreseeing what will happen next and using that knowledge to their own advantage.

For example, when a person sees a significant trade being made on a decentralized exchange, they may engage in frontrunning by swiftly buying or selling the same asset before the original trade can be completed. While the initial trade itself might not be profitable, this enables the frontrunning party to profit from the price change it generated.

To explain this more, consider a simple auction contract written in Solidity as an illustration:

```solidity
// SPDX-License-Identifier: MIT
    pragma solidity 0.8.0;
    contract Auction {
        address public owner;
        uint public highestBid;
        address public highestBidder;
        constructor()  {
            owner = msg.sender;
        }
        function bid(uint _bid) public payable {
            require(_bid > highestBid);
            require(msg.value == _bid);
            require(highestBidder != msg.sender);
            if (highestBidder != address(0)) {
                payable(highestBidder).transfer(highestBid);
            }
            highestBid = _bid;
            highestBidder = msg.sender;
        }
        function endAuction() public {
            require(msg.sender == owner);
            payable(owner).transfer(highestBid);
        }
    }
```

```solidity
// SPDX-License-Identifier: MIT 
pragma solidity 0.8.0; 
contract Auction { 

address public owner; 

uint public highestBid; 

address public highestBidder; 

constructor() { 
owner = msg.sender; 
} 

function bid(uint _bid) public payable { 
require(_bid > highestBid); 
require(msg.value == _bid); 
require(highestBidder != msg.sender); 

if (highestBidder != address(0)) { payable(highestBidder).transfer(highestBid); 
} 

highestBid = _bid; 
highestBidder = msg.sender; 

} 

function endAuction() public { 
require(msg.sender == owner); 
payable(owner).transfer(highestBid); 
} 
}
```

Users can bid in this simple auction of this contract. The bid() function allows users to make new bids as long as they are higher than the highest bid currently being accepted and they are not already the highest bidder. The `endAuction()` function enables the contract's owner to call off the auction and collect the winning bid. This contract is susceptible to frontrunning, unfortunately.

Think about the following example:

\- Lucy submits a bid for the auction contract at 100 ETH.

\- Before Lucy's first bid can be completed, Robert notices this bid and swiftly submits a greater bid of 110 ETH.

\- Robert becomes the new highest bidder because the auction contract processes his higher bid first.

\- Although Lucy's initial bid is processed, it is rejected since it is now less than the top bid.

In this case, Robert was able to foresee Lucy's conduct and use it to his advantage, thus outbidding her.

One method for resolving this issue is to implement a commit-reveal method in the bid function. A commit-reveal scheme can be implemented in an auction contract to prevent front running by requiring bidders to first "commit" to their bid by submitting a hash of their bid, rather than the actual bid itself. This hash is then stored in the contract, along with the bidder's address and the auction item ID. When the auction ends, bidders are then required to "reveal" their actual bid by submitting it to the contract.

The contract can then verify that the revealed bid matches the hash that was previously stored. If it does, the bid is accepted, and the auction process can continue. If it does not, the bid is rejected, and the auction continues without it.

This commit-reveal process helps to prevent front-running because it makes it difficult for other bidders or third parties to see the actual bids being made in the auction. Without this visibility, it is difficult for them to adjust their own bids in real-time to try and outbid the original bidder.

As an illustration of how a commit-reveal method might be used in the auction contract, consider the following:

```solidity
pragma solidity ^0.8.0;     
contract Auction {     
     
// Data structure to store bid information         
struct Bid {   address bidder;             
uint itemId;             
uint value;             
bytes32 hash;             
bool revealed;         
}         

// Mapping to store all bids         
mapping(bytes32 => Bid) public bids;  
       
// Function to allow bidders to commit to their bid         
function commitBid(uint itemId, uint value) public {             

// Generate the hash of the bid             
bytes32 hash = keccak256(abi.encodePacked(itemId, value));             

// Store the bid information in the contract             
bids[hash] = Bid({ bidder: msg.sender,                 
itemId: itemId,                 
value: value,                 
hash: hash,                 
revealed: false             
});         
}         

// Function to allow bidders to reveal their bid         
function revealBid(uint itemId, uint value) public {             
// Look up the bid information for the given hash             
Bid storage bid = bids[keccak256(abi.encodePacked(itemId, value))];

// Verify that the bid has not already been revealed 
require(!bid.revealed, "Bid has already been revealed");             // Verify that the caller is the bidder associated with this bid

require(bid.bidder == msg.sender, "Sender is not the bidder associated with this bid");             
// Set the revealed flag to true             
bid.revealed = true;         
}     
}
```

## Conclusion

Paying transaction fees that are always high enough that front-running is no longer lucrative is the simplest method for avoiding it. To prevent front-running, nevertheless, this is an expensive and unsustainable approach. Since front-running is a widespread problem on open blockchains like Ethereum. The ideal remedy is to take away the benefit of front-running, mostly by downplaying the significance of transaction sequencing or time.

For instance, it would be preferable to use batch auctions in markets (this also protects against high-frequency trading concerns). The second option is to limit price slippage by defining a maximum or minimum allowed price range on a deal in order to reduce the expense of front-running. Utilizing a pre-commit strategy—"I'm going to provide the specifics later"—is an additional option.

Thanks for reading!

See you at the next one.

Adios!