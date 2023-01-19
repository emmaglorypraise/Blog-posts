# Vulnerability #4 - Floating Pragma Vulnerability

In the previous article, we talked about outdated Solidity compiler versions and their vulnerabilities. Floating pragma vulnerabilities are related to it because it still has to do with the Solidity compiler version.

What then is Floating pragma?

Floating pragma is a \`pragma\` statement in a Solidity contract that does not specify a specific version of the compiler but rather a range of compiler versions that can be used for compilation. For example:

```bash
pragma solidity ^0.4.0; //Compiles with versions between 0.4.0 and latest version
pragma solidity >=0.4.0 < 0.8.0;  //Compiles with all versions between 0.4.0 and 0.8.0
pragma solidity >0.4.13 <0.8.0; 
pragma solidity 0.4.24 - 0.5.2;
```

Developers should stay away from using floating pragmas. Different pragma versions being used in test and mainnet may pose unidentified security issues.

# Prevention

To mitigate the risk of vulnerabilities caused by floating pragmas, it is important to specify a specific version of Solidity in the \`pragma\` statement of your contract. For example:

```bash
pragma solidity 0.8.0;
```

This will make sure that your contract is created using a particular version of Solidity and that it makes use of any newly added language features or bug patches. Additionally, it will prevent the contract from being built using an outdated compiler that might not support specific language features.

To make sure you are constantly utilizing the most recent version of Solidity, it is also a good idea to frequently review and update the "pragma" statement in your contracts. This will make it easier to guarantee that your contracts are safe and devoid of flaws brought on by floating pragmas.

# Conclusion

Finally, by enabling the usage of many compiler versions on a single contract, floating pragmas can lead to vulnerabilities in Solidity contracts. In order to reduce this risk, it's crucial to choose a specific version of Solidity in the contract's "pragma" declaration and to frequently examine and update this statement to guarantee that you're always utilizing the most recent compiler.

Thanks for reading and till I come your way again,

Adios!