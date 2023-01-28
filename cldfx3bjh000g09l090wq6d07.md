# Vulnerability #6 - State Variable Default Visibility Vulnerability

Any unknown visibility type of a function was set to public visibility type in older versions of the Solidity compilers. However, in more current versions, visibility type of the function must be specified in order to avoid the compiler throwing an error.

This vulnerability can still be introduced by improper use of State Variable Default visibility. It is imperative to test for this vulnerability since deployed contracts are immutable. One improperly defined state variable visibility can create a vulnerability that could jeopardize the entire contract.

## What are state variables?

In Solidity, a smart contract's state variables are variables that may be accessed both from within the contract and from other contracts and applications. State variables have "public" visibility by default, allowing anyone on the Ethereum network to read and write to them.

However, if developers are not careful in how they use it, this default visibility may occasionally result in vulnerabilities. Malicious actors may, in particular, change or "spoof" the values of public state variables in order to take advantage of vulnerabilities in the contract.

The "uninitialized storage pointer" attack is an illustration of this sort of vulnerability. In this attack, a malicious actor can write to the storage location of an uninitialized pointer, possibly leading to contract failure or malfunction.

To demonstrate this vulnerability:

```solidity
// SPDX-License-Identifier: MIT
    pragma solidity 0.8.0;
    contract UninitializedPointer {
        
        uint public number;  // Public state variable to store a number
        
        function setNumber(uint _number) public {  
            number = _number;          // Function to set the number
        }
    }
```

Anyone may call the "setNumber" function to change the number because the "number" state variable in this contract is publicly readable and write. In order to take advantage of the contract in some way, a hostile actor may use this to call the function with a faked number value. It is best practice to make state variables private or internal by default and to only make them public if absolutely necessary in order to reduce this vulnerability. To accomplish this, simply substitute "private" or "internal" for the word "public" in the declaration of the state variable:

```solidity
// SPDX-License-Identifier: MIT     
pragma solidity 0.8.0;     
contract SecurePointer {                  

uint private number; // Public state variable to store a number 
                
function setNumber(uint _number) public {               
number = _number;          // Function to set the number         
}     
}
```

The "number" state variable is made private so that only the contract itself has access to it and can change it; it is not readable or modifiable by anybody else. This makes it more difficult for malicious actors to alter or falsify the value of the state variable. It's also crucial to carefully assess a contract's functions' visibility because publicly available functions are vulnerable to abuse by malicious people.

Take the following contract, for instance:

```solidity
// SPDX-License-Identifier: MIT     
pragma solidity 0.8.0;          
contract VulnerableContract {  
                
uint public balance;  // Public state variable to store a user's balance         

// Public function to transfer funds from the contract         
function transferFunds(address _to, uint _amount) public {             require(balance >= _amount, "Insufficient funds");             
balance -= _amount;            
_to.transfer(_amount);         
}     
}
```

Since the "transferFunds" function in this contract is publicly accessible, anyone can use it to withdraw money from the contract. The function might be called by a malicious actor with a spoof \_to address and a huge \_amount value, though, in an effort to drain the contract's balance.

It is best practice to make functions private or internal by default and to only make them public if absolutely necessary in order to reduce this vulnerability. Simply substituting the word "public" with "private" or "internal" will accomplish this.

## Conclusion

It is best practice to make state variables private or internal by default and to only make them public if absolutely necessary in order to reduce this vulnerability.

Thanks for reading, and I'll see you in the next one.

Adios!