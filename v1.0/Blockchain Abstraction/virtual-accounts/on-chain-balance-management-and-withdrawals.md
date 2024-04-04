---
title: "On-chain Balance Management and Withdrawals"
slug: "on-chain-balance-management-and-withdrawals"
excerpt: ""
category: 65e9ba6715ec3b004bc82075
hidden: false
createdAt: "Thu Feb 08 2024 13:36:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 07:42:06 GMT+0000 (Coordinated Universal Time)"
---
## How Virtual Accounts balance works

At a high level, the Virtual Account balance is the combination of two separate asset balance sources:

- **On-chain**: From Blockchain deposit addresses
- **Off-chain**: From Virtual Account trading

> 🚧 Depending on Virtual Account trading activity, a blockchain deposit address attached to a Virtual Account may hold a lower or higher balance than what’s available on its Virtual Account.

## On-chain asset balance management

Handing transfers from Virtual Accounts to external blockchain addresses to your Exchange or Application, successfully and pain-free, requires thoughtful On-chain balance management.

Trading across Virtual Accounts means that your On-chain balance increasingly spreads across the blockchain deposit addresses of your Exchange or Application. If left unchecked, your On-chain balance will become increasingly hard to track.

### Virtual Accounts asset management can be handled in two ways:

- Spread Asset Management (UTXO **only** recommended)
- Centralized Asset Management (EVM recommended)

## Spread Asset Management (UTXO only recommended)

**For UTXO chains (like Bitcoin)**

It's possible to sign a transaction with XPUB and mnemonic. UTXOs under the XPUB will be checked automatically and a transaction will be built with a suitable XPUB with enough balance.

**For EVM chains (like Ethereum)**

You keep and maintain a complex database of all your Virtual Account balances and On-chain assets spread across all your blockchain deposit addresses.

At the time to handle transfers from Virtual Accounts to the blockchain, depending on the On-chain balance available within each deposit address of a specific Virtual Account, you may need to find additional deposit addresses within your database across your customers to amount enough On-chain balance to transfer out. 

This method can require several blockchain transfers with different endpoint types.

> 📘 Spread asset Management may offer a low cost in fees, applicable to UTXO chains. However, with EVM chains, it requires from you a complex database and back-end infrastructure to handle On-chain assets and withdrawals. Find the related article at the following link.

## Centralized Asset Management (EVM recommended)

You keep a relatively simple database of all your Virtual Accounts and you track On-chain deposits. 

After an incoming On-chain deposit from the blockchain to a deposit address of a Virtual Account, you transfer those On-chain assets to your Master Exchange address. Virtual Account withdrawals are handled via your Master Exchange Address.

> 📘 Centralized asset Management has a higher cost in terms of fees. However, it requires from you a relatively easy database and back-end infrastructure to handle On-chain assets and withdrawals. Find the related article at the following link.
