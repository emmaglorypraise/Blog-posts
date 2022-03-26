## Quick Dive into Reference Types In Solidity

In my previous article, I discussed Value types, which are one of Solidity's data types. In this tutorial, we'll look at the Reference type.

Because Reference type variables store the location of the data, they should be treated more cautiously than value types. They do not immediately share the data. Two separate variables can refer to the same location using reference type, and any change in one variable can affect the other. Several variables pointing to the same address can be used to modify the reference type value. It is critical to determine the data region memory, storage, or calldata location where the Reference type is stored.

The set location is significant for assignment semantics as well as data persistence. Assignments between 'storage' and 'memory' (or from 'calldata') always result in a separate copy. Assignments from 'memory' to 'memory' provide only references. Changes to one memory variable are reflected in all other memory variables that relate to the same data. Assignments from 'storage' to a local storage variable only return a reference. All other 'storage' assignments always copy. Assignments to state variables or members of local variables of storage struct type are examples of this case, even if the local variable itself is only a reference.

**Note:** 
 Local variables are declared within a function and are not stored on the blockchain; state variables are declared outside of a function and are stored on the blockchain; and global variables give information about the blockchain. The Ethereum Virtual Machine injects them during runtime. Global variables include transaction sender, block timestamp, and so forth.

Reference types in solidity are listed below: 


- ### Arrays: 

An array is a collection of variables of the same data type, each of which has a unique place known as an index. The requested variable can be retrieved by using the index location. At compilation time, arrays can be fixed or dynamic. T[k] is the combination of an array of fixed size k and element type T. T[] is the dynamically sized array.

Example: 
```
    uint[10] public myFixedArr;
```

Arrays have these members:

 - Length: The number of elements is dealt with by length. The length of storage arrays is fixed after they are built. It can, however, be dynamic and based on runtime settings. To adjust the size of dynamically sized arrays, the length is set.
 - Push: Adds an element to the end of a dynamic memory array and bytes (not a string). Newly inserted items are set to zero.
 - Pop: removes elements from the end of a dynamic array of storage and bytes (not strings).


```
    uint[] public arr;
    uint length = arr.length; // get the length of the array
    arr.push(i);  // Append to array 
    arr.pop();   // Remove last element from array
```


- ### Structs

Structs in Solidity enable the declaration of new types in the form of structs. Users of Solidity can construct and specify their own types in the form of structures. The structure is a collection of different types (which can contain both value types and reference types). There is one exception: a struct cannot contain a member of its own type since the size of the struct must be finite. This is not to say that struct cannot include struct; for example, struct A can contain struct B, but struct A cannot contain its own type struct A.

Example:
```
    struct student {
            string name;
            string subject;
            uint8 marks;
        }
```

- ### Mapping: 
Mapping is the most commonly used reference type, storing data as a key-value pair where the key can be any value type. It functions similarly to a hash table or dictionary in any other computer language, where data can be retrieved using a key. Solidity mappings can only have one data storage location. As a result, they are permitted for state variables.

Example: 
```
    mapping (address => uint) account;  
```
In this case, the address is used to store key information, while the uint type is used to store value information. The identifier is "account"; by utilizing identifier, we can access mapping later in our contract.

I am sure you are able to understand what Reference Types are and how to use them in Solidity now.

Till I come your way again,

Adios! 
