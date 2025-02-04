# Creating a Token on XODE

<img src="https://drive.google.com/uc?export=view&id=1i88iInwVlXMoX2L8P2kLwFzGNuFVRra5"></img>

<div align="center">

[![Twitter URL](https://img.shields.io/badge/Twitter-gray?logo=x)](https://x.com/XodeNet)
[![Facebook URL](https://img.shields.io/badge/Facebook-gray?logo=facebook)](https://web.facebook.com/xodenet)
[![Discord](https://img.shields.io/badge/Discord-gray?logo=discord)](https://discord.gg/V6DETUY7Cy)
<br>
[![Certik Security Code Audit Rating](https://img.shields.io/badge/Certik_Security_Code_Audit-AA-green.svg)](https://skynet.certik.com/projects/xode-blockchain)
[![CoinMarketCap](https://img.shields.io/badge/CoinMarketCap-Listing-purple.svg)]([https://skynet.certik.com/projects/xode-blockchain](https://coinmarketcap.com/currencies/xode-blockchain/))
[![Kusama Parachain](https://img.shields.io/badge/Kusama_Parachain-3344-pink.svg)]([https://skynet.certik.com/projects/xode-blockchain](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpcnodea01.xode.net%2Fn7yoxCmcIrCF6VziCcDmYTwL8R03a%2Frpc#/explorer))

> Xode is a blockchain platform with its own on-chain governance that aims to bring game development and businesses to Web3 and Polkadot.

</div>

This guide explains how to create a token on the Polkadot network. Polkadot's architecture allows tokens to be created either as part of a custom parachain or as a smart contract on an EVM-compatible parachain like Moonbeam or Astar Network.

---

## Table of Contents
- [Introduction](#introduction)
- [Key Fields for Token Creation](#key-fields-for-token-creation)
- [Steps to Create a Token](#steps-to-create-a-token)
  - [Option 1: Using Moonbeam (EVM-Compatible Parachain)](#option-1-using-moonbeam-evm-compatible-parachain)
  - [Option 2: Creating a Custom Parachain](#option-2-creating-a-custom-parachain)
- [Example Smart Contract Code](#example-smart-contract-code)
- [Tools and Resources](#tools-and-resources)
- [Conclusion](#conclusion)

## Introduction
Creating a token in the Polkadot ecosystem provides flexibility with options like leveraging existing parachains or creating custom ones. This guide explores these methods, including key fields and steps to follow.

## Key Fields for Token Creation
- **Token Name**: The unique name of your token.
- **Symbol**: A short identifier for the token.
- **Total Supply**: The maximum supply of tokens that will exist.
- **Decimals**: The number of decimal places your token can be divided into.
- **Ownership and Permissions**: The ability to define who has control over minting, burning, or transferring tokens.

## Steps to Create a Token

### Option 1: Using Moonbeam (EVM-Compatible Parachain)
Moonbeam provides an easy way to create tokens in the Polkadot ecosystem using Ethereum-compatible smart contracts. It allows developers to deploy and interact with Solidity-based contracts.

1. **Install MetaMask** and connect it to the Moonbeam network.
2. **Deploy an ERC-20 token contract** using tools like Remix IDE or Hardhat.
3. Customize your token details (name, symbol, total supply) in the smart contract.
4. **Verify and publish your contract** on the Moonbeam block explorer.

### Option 2: Creating a Custom Parachain
For more advanced use cases, you can create a custom parachain within the Polkadot ecosystem. This approach allows for greater flexibility in tokenomics, governance, and other features.

1. **Set up a Substrate-based blockchain**: Use the Substrate framework to create a blockchain that integrates with Polkadot.
2. **Define your token's parameters**: Configure token name, supply, and other features within the runtime of your parachain.
3. **Deploy your parachain**: Use Polkadot's relay chain to deploy your custom parachain, making it interoperable with the entire Polkadot ecosystem.
4. **Customize governance and consensus** mechanisms to control how your token operates on the chain.

## Example Smart Contract Code
Below is an example of a basic ERC-20 smart contract in Solidity for deploying on Moonbeam.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    string public name = "MyToken";
    string public symbol = "MTK";
    uint8 public decimals = 18;
    uint public totalSupply = 1000000 * 10**uint(decimals);

    mapping (address => uint) public balanceOf;
    mapping (address => mapping (address => uint)) public allowance;

    event Transfer(address indexed from, address indexed to, uint value);
    event Approval(address indexed owner, address indexed spender, uint value);

    constructor() {
        balanceOf[msg.sender] = totalSupply;
    }

    function transfer(address to, uint value) public returns (bool success) {
        require(balanceOf[msg.sender] >= value, "Insufficient balance");
        balanceOf[msg.sender] -= value;
        balanceOf[to] += value;
        emit Transfer(msg.sender, to, value);
        return true;
    }

    function approve(address spender, uint value) public returns (bool success) {
        allowance[msg.sender][spender] = value;
        emit Approval(msg.sender, spender, value);
        return true;
    }

    function transferFrom(address from, address to, uint value) public returns (bool success) {
        require(balanceOf[from] >= value, "Insufficient balance");
        require(allowance[from][msg.sender] >= value, "Allowance exceeded");
        balanceOf[from] -= value;
        balanceOf[to] += value;
        allowance[from][msg.sender] -= value;
        emit Transfer(from, to, value);
        return true;
    }
}
