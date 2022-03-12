## An Introduction to ERC-20 Tokens

## What is a Token?
Tokens are a type of asset. Tokens can be held for their monetary value or sold and staked to earn interest.  Tokens, unlike coins, do not have their own blockchain. Instead, they function on the blockchains of other coins, such as Ethereum. Examples of tokens are Uniswap, Chainlink, and Polygon.

## What is ERC-20?
“ERC” stands for “Ethereum Request for Comments”, which is an official protocol used to propose improvements to the Ethereum network, while “20” is the unique ID number used to identify the proposal. It is a programming standard that is utilized on the Ethereum network. This technical standard specifies a set of rules and actions that an Ethereum token or smart contract must adhere to, as well as the processes required to implement them. It's probably easiest to think of ERC20 as a collection of fundamental rules and functions that any new coin produced on the Ethereum network must adhere to. These rules cover how tokens can be exchanged, how transactions are approved, how users can access token data, and the overall supply of tokens. The protocol is required to ensure compatibility among the numerous tokens generated on Ethereum. Hence, ERC-20 tokens are tokens designed and created following the ERC-20 standards to be used solely on the Ethereum platform. Examples of ERC-20 tokens are Shiba Inu (SHIB), Tether (ERC20-USDT), Maker (MKR), etc. 

## History of ERC-20?
ERC20 was designed in 2015 by Ethereum developers on behalf of the Ethereum community as a whole, and it was officially recognized in September 2017. 1 To build this type of standard for Ethereum, a developer or group of developers must submit an Ethereum Improvement Proposal (EIP), which outlines the new functionality as well as its specific protocols and standards.

## Functionality for ERC-20 tokens
ERC-20 defines a number of functionalities/rules that a token must be able to implement. Some functionalities are mandatory, while others are optional. The mandatory functionalities include:
- TotalSupply: offers data on the overall token supply.
- BalanceOf: returns the owner's account balance.
- Transfer: sends a specific number of tokens to a specified address.
- TransferFrom: does a given number of token transfers from a specified address.
- Approve: allow a spender to withdraw a set number of tokens from a specified account.
- Allowance: returns a set number of tokens from a spender to the owner

The optional functionalities and rules include: 
- Token Name: the name of the token, for example, Shiba Inu (SHIB).
- Symbol: Symbol of token, for example, SHIB
- Decimal (up to 18)


## Issues with ERC-20
Many people in the development community believe that ERC-20 is limited or defective in one or more ways. As a result, various alternative token standards have been proposed since the inception of ERC-20. These include ERC-223, which tries to address a problem with the ERC-20 approval and transfer parts.

ERC-621 is another option that has the same fundamental capabilities as ERC-20 but also adds the ability to increase or decrease the overall token supply. On the other hand, allows ERC-827 token holder to approve the use of tokens by a third party. To some extent, each of these new protocol proposals is based on ERC-20.
