---
title: "Supported types and blockchain networks"
slug: "supported-types-and-blockchain-networks"
excerpt: ""
category: 65c0c716d716fe0040919d8b
hidden: false
createdAt: "Fri Mar 01 2024 07:37:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 01 2024 08:09:35 GMT+0000 (Coordinated Universal Time)"
---
# Types of notifications you can monitor

Tatum supports various types of notifications on a chain, which are designed to cover a wide range of blockchain events. These are the notifications types we offer:

## Incoming Transaction Notifications 📭

- **Incoming Native Transactions:** This notification is triggered when an address you are subscribed to, receives some Native Token from any address.
- **Incoming Internal Transactions:** This notification is triggered when an address you are subscribed to, receives an Internal transaction (such as transfer an asset by a smart contract).
- **Incoming Fungible Transactions:** This notification is triggered when an address you are subscribed to, receives a Fungible token from any address.
- **Incoming NFT Transactions:** This notification is triggered when an address you are subscribed to, receives a Non Fungible Token (NFT's) from any address.
- **Incoming MultiToken Transactions:** This notification is triggered when an address you are subscribed to, receives MultiToken from any address.

## Outgoing Transaction Notifications ✈️

- **Outgoing Native Transactions:** This notification is triggered when an address you are subscribed to, sends some Native Token to any address.
- **Outgoing Internal Transactions:** This notification is triggered when an smart contract address you are subscribed to, sends assets to another address (Internal transaction).
- **Outgoing Fungible Transactions:** This notification is triggered when an address you are subscribed to, send's Fungible tokens to any address.
- **Outgoing NFT Transactions:** This notification is triggered when an address you are subscribed to, sends a Non Fungible Token (NFT's) to any address.
- **Outgoing MultiToken Transaction:** This notification is triggered when an address you are subscribed to, sends a MultiToken to any address.
- **Outgoing Failed Transactions: **This notification is triggered when an address you are subscribed to, initiates any transaction but it failed due to any reason.

## Special Abstraction Notifications 🔔

- **Address Events: **This notification is triggered when a user either receives or sends any token to any address on blockchain.
- **Paid Fee:** This notification is triggered when a fee is paid as part of a transaction involving a specific address.
- **Failed Transactions in a Block :** This notification is triggered when a block containing failed transactions is detected. This notification can be useful for monitoring and analysing failed transactions within specific blocks.
- **Contract Address Log Event :** This notification allows you to monitor specific custom log events of a smart contract.

These notification types allow users to monitor a wide range of events on the blockchain, enabling them to build responsive and efficient applications.

# Blockchain protocols you can work with

> 📘 Every type of notification has its own guide, where all the supported blockchain for that type is mentioned.

Each of the notification types provided by Tatum can be used across various blockchains, depending on the blockchain family. These families include

1. **UTXO (Unspent Transaction Output) chains:**
   1. Bitcoin
   2. Litecoin
   3. Dogecoin
   4. Bitcoin Cash
2. **EVM (Ethereum Virtual Machine) chains:**
   1. Ethereum
   2. Binance Smart Chain
   3. Polygon
   4. Chilliz
   5. Celo
   6. Klaytn
   7. Flare
3. **Other Blockchains:**
   1. Solana
   2. XRP
   3. Tron

By offering compatibility with different blockchain families, Tatum ensures that users can effectively monitor and respond to a diverse range of events, irrespective of the underlying blockchain technology
