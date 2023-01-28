# Vulnerability #7 - Tx.origin Vulnerability

## What is Tx.origin?

In Solidity, Tx.origin is a global variable that returns the address of the account that originated the transaction. In other words, it is the address of the account that sent the original transaction that led to the execution of the current smart contract.

However, in some circumstances, an attacker may be able to impersonate the `tx.origin` address, giving them access to a contract's functions and data without authorization.

The use of a malicious smart contract also referred to as a "proxy contract," that stands between the original caller and the target contract is one common technique of exploiting this vulnerability. Before calling the target contract, the proxy contract can be used to change the `tx.origin` address, giving the attacker access that they are not entitled to. Here is a demonstration of how this vulnerability might be used to access certain functions in a basic Solidity contract that checks the `tx.origin` address:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.0;

contract MyContract {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    function doSomething() view public {
        require(msg.sender == tx.origin, "Unauthorized access");
        // do something
    }
}
```

The contract in the above example has a function called doSomething that is only accessible by the account that initiated the transaction. To make it appear as though the original transaction was sent by the attacker's account, an attacker can change the `tx.origin` address before to the call if they create a proxy contract that calls doSomething. Here is a modified contract that substitutes address(this).caller for `tx.origin`:

```solidity
// SPDX-License-Identifier: MIT 
pragma solidity 0.8.0;  

contract MyContract {     
address public owner;      

constructor() {         
owner = msg.sender;     
}      

function doSomething() view public {         
require(msg.sender == address(this), "Unauthorized access");         // do something     
} 
}
```

This updated example still requires the caller address to be checked before granting access to the doSomething method, but it does so using `address(this).caller` rather than `tx.origin`. Because the contract is validating the caller address rather than the origin address, even if an attacker develops a proxy contract and changes the `tx.origin` address, they will not be able to get unauthorized access to the doSomething function.

### Prevention

Avoid using the `tx.origin` address in your contracts; instead, use `msg.sender` or address(this). Additionally, you should use `address(this).caller` or `address(this).origin` rather than `tx.origin` as a condition to carry out an action.

Also, Utilizing libraries like Ownable from OpenZeppelin, which offers a safe and user-friendly solution, is another method to avoid this type of vulnerability. It's crucial to pay attention to how addresses are used in smart contracts and to use the correct variable when determining authorization.

I hope you remember this when you write your next smart contract.

I'll see you in the next one.

Adios!