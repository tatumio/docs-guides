---
title: "Withdrawing Assets: Introduction"
slug: "withdrawing-assets-from-virtual-accounts"
excerpt: ""
category: 65a8e44fccf94800381cd6f8
hidden: false
createdAt: "Tue Feb 06 2024 16:32:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 07:42:10 GMT+0000 (Coordinated Universal Time)"
---
Setting up Virtual Accounts is similar for all the supported blockchains. 

However, withdrawing funds from a Virtual Account works differently depending on what blockchain the Virtual Account is created for.

## UTXO (like Bitcoin) blockchains

On UTXO-based blockchains such as Bitcoin, Bitcoin Cash, Dogecoin, and Litecoin, withdrawing funds from Virtual Accounts is "easier" when **the Virtual Accounts are associated with the same extended public key (xpub)**. 

This way, all the deposit addresses that you generate for those virtual accounts are associated with the same xpub, and you do not have to track all UTXO transactions. During the withdrawal, all the deposit addresses are automatically scanned for incoming deposits that are then used as a source of the withdrawal transaction.

**BTC Example:**

To withdraw funds from BTC Virtual Accounts associated with the same xpub, you can use [the following v3 REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-operations/#operation/BtcTransfer) for sending the funds from a BTC-based Virtual Account to the blockchain.

## EVM (like Ethereum) blockchains

On EVM-compatible blockchains such as Ethereum, BNB Smart Chain, Celo, and so on, you can choose from the following approaches to withdrawals:

- Withdraw assets from each blockchain deposit address separately. (**NOT recommended**)
- Centralize assets across all deposit addresses into a "Master Exchange blockchain address" and withdraw from there. (**Recommended**)

## BNB Beacon Chain, Stellar, and XRPL

On BNB Beacon Chain, Stellar, and XRPL, one deposit address is used and customers are identified by blockchain-specific parameters such as `memo`, `message`, and `DestinationTag`, accordingly.
