---
title: "Withdrawing Assets"
slug: "withdrawing-assets"
excerpt: ""
hidden: false
createdAt: "Sat Jan 27 2024 18:34:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 08:41:55 GMT+0000 (Coordinated Universal Time)"
---
Setting up virtual accounts is similar for all the supported blockchains. 

However, withdrawing funds from a virtual account works differently depending on what blockchain the virtual account is created for.

## UTXO-based blockchains

On UTXO-based blockchains such as Bitcoin, Bitcoin Cash, Dogecoin, and Litecoin, withdrawing funds from virtual accounts is "easier" when **the virtual accounts are associated with the same extended public key (xpub)**. 

This way, all the deposit addresses that you generate for those virtual accounts are associated with the same xpub, and you do not have to track all UTXO transactions. During the withdrawal, all the deposit addresses are automatically scanned for incoming deposits that are then used as a source of the withdrawal transaction.

**BTC Example:**

To withdraw funds from BTC Virtual Accounts associated with the same xpub, you can use [the following v3 REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-operations/#operation/BtcTransfer) for sending the funds from a BTC-based Virtual Account to the blockchain.

## EVM-compatible blockchains

On EVM-compatible blockchains such as Ethereum, BNB Smart Chain, Celo, and so on, you can choose from the following approaches to withdrawals:

- Withdraw deposits from each deposit address separately. (NOT recommended)
- Collect all deposits on a separate blockchain address and withdraw them from this address. (Recommended)

## BNB Beacon Chain, Stellar, and XRPL

On BNB Beacon Chain, Stellar, and XRPL, one deposit address is used and customers are identified by blockchain-specific parameters such as `memo`, `message`, and `DestinationTag`, accordingly.
