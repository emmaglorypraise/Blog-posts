## Quick Dive into Value Types In Solidity

Solidity is an object-oriented, high-level programming language used to build smart contracts. It is statically typed, which means that each variable's type must be stated; it also enables inheritance, libraries, and complex user-defined types, among other things.

Variables of the value type store their own data. Variables are duplicated wherever they appear in function parameters or assignment.

Solidity, like many other programming languages, provides two types of data: value types and reference types. In this tutorial, we will look at the different value types in Solidity.


- Integer: 

This data type is used to store integer values; the data types **int** and **uint** are used to declare signed and unsigned integers, respectively. The term **uint** refers to unsigned integers, which are non-negative numbers. **uint** is a shorthand for **uint256**. It comes in a variety of sizes, including uint8, which has a range of 0 to **2 **** 8 - 1**, and uint256, which has a range of 0 to **2 ****256 - 1**.

Let's look at few examples:
```
    uint8 public u8 = 10;
    uint public u256 = 500;
    uint public u = 1190; 
```

Note: The term "public" denotes that the variable can be accessible internally by the contract as well as viewed outside the contract.

Negative numbers are represented using **int** types. **int** is equivalent to **int256**. **Int**, like **uint**, has several sizes, such as **int256**, which runs from -2 **** 255 to **2 ** 255 - 1.

Example:
```
    int public i = -178; 
```


- Boolean: 

Booleans (bool) have two fixed values: true and false. All of the standard Boolean operators are supported by Solidity, including!= (inequality), == (equality),! (logical negation), && (logical conjunction, "and"), and || (logical disjunction, "or"). The boolean value is set to false by default.

Example:
```
    bool public isRequired = false;
```


- Fixed Point Numbers: 

Fixed-point refers to a method of representing fractional numbers (not integers). According to the Solidity documentation, These data types are not yet completely supported in Solidity. . However, fixed-point numbers can be declared, but cannot be assigned to or from. We have signed and unsigned fixed-point numbers, which are denoted by the keywords fixed and ufixed, respectively. These are also compatible with comparison operators such as =, ==,!=, >=, >. Also used for Arithmetic are +, -, unary -, *, /, and percent (modulo).


- Addresses

Address is a 20-byte number that represents the size of an Ethereum address. An address can be used to acquire the balance with the.balance method and to transfer the balance to another address with the.transfer method.

Addresses are classified into two types: address payable and address. These are nearly identical. The 'address' has a 20-byte value (the size of an Ethereum address) and cannot send 'Ether', however the 'address payable' has the same as an address but with the additional members 'transfer' and 'send' and can send 'Ether'.

These value data types will appear frequently when building smart contracts. I hope you found this article helpful.

Till I come your way again,

Adios!



