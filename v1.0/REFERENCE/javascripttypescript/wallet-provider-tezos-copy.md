---
title: "💻  Wallet Provider UTXO"
slug: "wallet-provider-tezos-copy"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 13:20:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:24:33 GMT+0000 (Coordinated Universal Time)"
---
UTXO Wallet Provider extends wallet capabilities for UTXO-based blockchains via Tatum SDK, facilitating:

- Mnemonic generation for seed phrases.
- xpub creation from mnemonics.
- Private key and address derivation from mnemonics and xpubs.
- Transaction signing and broadcasting to UTXO networks.

Utilizes well-regarded packages like bitcoinjs-lib, bitcore-lib, bip39, and bip32.

# Quick Start

## Installation

```javascript Install
npm install @tatumio/utxo-wallet-provider
```

```javascript
import { UtxoWalletProvider } from '@tatumio/utxo-wallet-provider';

const tatumSdk = await TatumSDK.init<Bitcoin>({
     network: Network.BITCOIN,
     configureWalletProviders: [
         UtxoWalletProvider,
     ]
 });
```

# Supported Networks

- Network.BITCOIN
- Network.DOGECOIN
- Network.LITECOIN
- Network.BITCOIN_TESTNET
- Network.DOGECOIN_TESTNET
- Network.LITECOIN_TESTNET

Remember to keep mnemonics, private keys, and other sensitive data secure. Avoid exposing them in client-side code or public repositories.
