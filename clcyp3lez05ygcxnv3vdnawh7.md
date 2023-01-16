# Vulnerability #3 - Outdated Compiler Version

Solidity-written smart contracts may be security vulnerable if their compilers are out of date. This article will look into the issue of outdated compiler versions and cover methods for reducing the likelihood that your smart contracts include vulnerabilities.

Newer versions of compilers can provide new language features that weren't there in the compiler's first release, which can lead to vulnerabilities. Take the following Solidity contract, for instance:

```solidity
pragma solidity ^0.4.24;
    contract MyContract {
        uint public balance;
    
        constructor() public {
            balance = 100;
        }
    
        function add(uint _value) public {
            balance += _value;
        }
    }
```

This contract specifies that it was written for Solidity version 0.4.24 or later using the `pragma` statement at the top of the file. If this contract is compiled using a newer version of Solidity that introduces a new language feature, such as the `emit` keyword, the contract will still be able to use this feature even though it was not available when the contract was written.

This can lead to unexpected behavior and potentially create vulnerabilities in the contract. For example, consider the modified version of the contract:

```solidity
pragma solidity ^0.4.24;
    contract MyContract {
        uint public balance;
    
        constructor() public {
            balance = 100;
        }
    
        function add(uint _value) public {
            balance += _value;
            emit NewBalance(balance);
        }
    
        event NewBalance(uint newBalance);
    }
```

We've added an event to this iteration of the contract that is called each time the add function is used. The emit keyword, which was absent in Solidity version 0.4.24, is used to emit this event. This contract will be allowed to utilize the emit keyword, and the event will be triggered as expected if it was compiled using a more recent version of Solidity. The emit keyword is not supported by older versions of Solidity; hence, the compiler will throw an error if the contract is compiled using one of those versions.

Let’s see another example:

```solidity
 pragma solidity 0.4.24;
    contract SimpleDAO {    
      function withdraw(uint amount) public {
        msg.sender.call.value(amount)());
    } 
    function withdraw(uint amount) public {
        if (credit[msg.sender]>= amount) {
          credit[msg.sender]-=amount;
          msg.sender.call.value(amount)();
        }
    }  
```

The code above would not throw an error when compiled because of the compiler version, but the format for performing a call has been changed in newer versions of Solidity: Using a higher compiler version, the code would be modified to:

```solidity
 // SPDX-License-Identifier: MIT
    pragma solidity 0.8.0;
    contract SimpleExample {
        
      function withdraw(uint amount) public { 
          msg.sender.call{value: amount}("");
      }  
    }
```

Solidity compiler version 0.8.0 now requires an SPDX declaration statement, and the syntax for performing a call has changed. Hopefully, you see one of the possible problems caused by using an outdated compiler version. Using an outdated compiler version can be challenging, especially if the current compiler version has bugs and issues that have been made public. When new versions of the compiler are published, these issues are typically fixed.

Using out-of-date compiler versions exposes your smart contract to attacks from malicious parties who take advantage of the corrected defects, which can cause a lot of problems.

It is crucial to make sure that your contracts are constantly compiled using the most recent version of Solidity in order to reduce the possibility of vulnerabilities brought on by out-of-date compiler versions.

```solidity
pragma solidity ^0.8.0;
```

By doing this, you can be sure that your contract is created with the most recent version of Solidity and that it will benefit from any newly added language features or enhancements and bug fixes.

To make sure you are always utilizing the most recent version of Solidity, it is also a good idea to periodically examine and update the pragma statement in your contracts. By doing this, you'll be able to protect your contracts from vulnerabilities brought on by out-of-date compiler versions.

In conclusion, outdated compiler versions can introduce vulnerabilities from fixed bugs and other issues made public. It can also introduce bugs from old language features that have been changed or from new language features that weren’t present when the contract was prepared, leading to vulnerabilities in Solidity contracts. It is highly recommended to use a recent stable version of the Solidity compiler.

Thanks for reading and till I come your way again,

Adios!