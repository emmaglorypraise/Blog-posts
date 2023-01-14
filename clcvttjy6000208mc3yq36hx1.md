# Vulnerability #2 - Reentrancy in Solidity

Reentrancy is a form of vulnerability that can happen in Solidity contracts when an external contract has the ability to call the main smart contract function repeatedly in order to drain its funds before the original call has ended.

A reentrancy attack continually removes money from a smart contract and transfers it to an unapproved contract until all the money in the contract is gone. The attack usually takes place within the blockchain's execution cycle.

Millions of dollars have been lost to reentrancy attacks affecting blockchain systems and DAOs. The DAO hack, [Lendf.me](http://Lendf.me), and Cream Finance are a few well-known examples of reentrancy attacks that exploited vulnerabilities in blockchain systems.

How does Reenterancy vulnerability happen?

Consider this contract:

```solidity
// SPDX-License-Identifier: MIT
    
    pragma solidity 0.8.0;
    contract SimpleBank {
      mapping (address => uint) credit;
        
      function deposit(address _to) payable public{
        require(msg.value > 0, "Add amount to deposite");
        credit[_to] += msg.value;
      }
        
      function withdraw(address _to) public{
            uint256 acctBalance = credit[msg.sender];
            (bool sent, bytes memory data) = _to.call{value: acctBalance}("");
            require(sent, "Failed to send Ether");
            credit[msg.sender]-=acctBalance;
        
      }  
      function checkBalance(address _account) public view returns(uint) {
           return  credit[_account];
      }
    }
```

Users can deposit money into this contract (using the deposit() function) and withdraw money from it (using the withdraw() function). The withdraw() function transfers the money to the caller's address and subtracts the requested sum from the contract's balance.

Unfortunately, this contract is vulnerable to reentrancy attacks. A malicious contract made by an attacker could make repeated calls to "withdraw()" before the initial call has finished. This malicious contract can generate an instance of the SimpleBank contract and call the SimpleBank contract's "withdraw()" function.

The fallback function may contain a function that repeatedly calls the withdraw function when a condition is met. The "withdraw()" function keeps executing if there is money in the contract until it is exhausted. The require() statement in the withdraw() method won't be activated as a result, allowing the attacker to withdraw more money than they are authorized to.

# Prevention

The caller's balance must be set to zero before making an external call (transferring ether out) in order for the balance to remain zero even when there is a callback after the first call has ended. This will fix the vulnerability. Here is an illustration of how to write the contract in a safer manner:

```solidity
// SPDX-License-Identifier: MIT
    
    pragma solidity 0.8.0;
    contract SimpleBank {
      mapping (address => uint) credit;
        
      function donate(address _to) payable public{
        require(msg.value > 0, "Add amount to donate");
        credit[_to] += msg.value;
      }
        
      function withdraw(address _to) public{
            uint256 acctBalance = credit[msg.sender];
            require(acctBalance > 0, "Low balance");
            credit[msg.sender] = 0;
            (bool sent, bytes memory data) = _to.call{value: acctBalance}("");
            require(sent, "Failed to send Ether");
      }  
    
      function checkBalance(address _account) public view returns(uint) {
           return  credit[_account];
      }
    }
```

We can use a Reentrancy Guard or mutex (mutual exclusion) pattern to stop several calls from occurring simultaneously, which will increase the contract's security. For instance:

```solidity
  // SPDX-License-Identifier: MIT
    
    pragma solidity 0.8.0;
    contract SimpleBank {
      mapping (address => uint) credit;
      bool entered;
    
      modifier customReentrancyGuard() {
            require(!entered);
            entered = true;
            _;
            entered = false;
        }
        
      function donate(address _to) payable public{
        require(msg.value > 0, "Add amount to donate");
        credit[_to] += msg.value;
      }
        
      function withdraw(address _to) public customReentrancyGuard {
            uint256 acctBalance = credit[msg.sender];
            require(acctBalance > 0, "Low balance");
            credit[msg.sender] = 0;
            (bool sent, bytes memory data) = _to.call{value: acctBalance}("");
            require(sent, "Failed to send Ether");
      }  
    
      function checkBalance(address _account) public view returns(uint) {
           return  credit[_account];
      }
    }
```

A reentrancy guard has been added to this code to thwart attackers who might attempt to repeatedly call the "withdraw" function. The "isEntered" boolean, which is used by the reentrancy guard, prevents the function from being invoked when it is true.

To prevent any errors, we may alternatively use OpenZeppelin's ReentrancyGuard. We also set the caller's balance to zero before transferring Ether to further protect the contract from vulnerabilities. This is done to update the contract's status before making calls to the outside world. This is known as the Checks-Effects-Interactions pattern.

As a result, we have successfully corrected a contract that had been exposed to reentry attacks.

# Conclusion

In summary, to prevent a reentrancy attack on your smart contract, you may do the following:

* Using the Checks-Effects-Interactions pattern by setting the caller's balance to zero before transferring Ether
    
* Using a Reentrancy Guard or mutex (mutual exclusion) pattern to stop several calls from occurring simultaneously or
    
* Using a Reenterancy guard library like OpenZeppelin's ReentrancyGuard
    

I sincerely hope that this article has assisted you in preventing reentrancy vulnerability in future smart contracts you write.

Thanks for reading and till I come your way again,

Adios!