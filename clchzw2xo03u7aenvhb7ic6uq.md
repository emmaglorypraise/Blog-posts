# Vulnerability #1 - Integer Overflow/Underflow in Solidity

In Solidity, integers are limited in size and can only hold a certain range of values. For example, an **uint8** (unsigned 8-bit integer) can hold values from 0 to 255. In other words, the largest number we can store is 11111111 in binary, or  (2^8 - 1 = 255) in decimal. If an operation is performed that results in a value outside of this range, it can cause an integer overflow or underflow.

For Solidity versions greater than or equal to (&gt;=) 0.8, Solidity's default behavior for overflows and underflows is to throw an error. For Solidity versions less than 0.8, integers overflow/underflow without any issues.

However, what exactly are integer overflows and underflows, and how are they prevented?

An integer overflow occurs when the result of an operation is larger than the maximum value that the integer can hold. For example:

```solidity

pragma solidity 0.6.0;

contract IntegerOverflow {
    uint8 public num;
    function setNumber(uint8 _num) public {
            num = _num;
    }
    function addToNumber(uint8 _num) public {
        num += _num;
    }
}
```

In this contract, if we set **x** to 255 and then call **addToNumber(1)**, the value of **x** will become 0 because of the integer overflow. If you add 1 to the binary number 11111111, it resets back to 00000000.

An integer underflow occurs when the result of an operation is smaller than the minimum value that the integer can hold. For example:

```solidity
pragma solidity 0.6.0;

contract IntegerUnderflow {

    uint8 public num;
    function setNumber(uint8 _num) public {
        num = _num;
    }
    function subtractFromNumber(uint8 _num) public {
        num -= _num;
    }

}
```

In this contract, if we set **x** to 0 and then call **subtractFromNumber(1)**, the value of **x** will become 255 because of the integer underflow.

**Prevention**

To prevent integer overflows and underflows, using a Solidity compiler that is at least version 0.8.0 is the simplest method. The compiler will automatically check for overflows and underflows in Solidity 0.8.

For example:

```solidity

// SPDX-License-Identifier: MIT

pragma solidity 0.8.0;

contract IntegerOverflowAndUnderflowPrevention {

    uint256 public num;
    function setNumber(uint256 _num) public {
            num = _num;
        }
    function addToNumber(uint256 _num) public {
            num += _num;
        }
        
    function subtractFromNumber(uint256 _num) public {
            num -= _num;
        }
}
```

You can alternatively use the SafeMath library from openZeppelin. The SafeMath library provides safe variations of functions that automatically handle overflow and underflow scenarios. Keep in mind that SafeMath only functions with uint256 and Solidity version 0.8.0.

The following contract, for instance, uses the SafeMath  library to securely add and subtract numbers from num:

```solidity

// SPDX-License-Identifier: MIT

pragma solidity 0.8.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeMath.sol";

contract IntegerOverflowAndUnderflowPrevention {
    using SafeMath for uint256;
    uint256 public num;
    function setNumber(uint256 _num) public {
        num = _num;
    }
    function addToNumber(uint256 _num) public {
        num = num.add(_num);
    }
    function subtractFromNumber(uint256 _num) public {
        num = num.sub(_num);
    }
}
```

Now, if we set **x** to 255 and call **addToNumber(1)**, or set **x** to 0 and call **subtractFromNumber(1)**, the contract will revert with an error message.

**Conclusion**

In Solidity smart contracts, integer overflows and underflows can produce unexpected and potentially unsafe behavior. It is important to use the SafeMath library or manually handle overflow/underflow conditions by using only Solidity version 0.8.0 and above to ensure the correctness and security of your contract.

I hope this article was helpful! See you at the next one!