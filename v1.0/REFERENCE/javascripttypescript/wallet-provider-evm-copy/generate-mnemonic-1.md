---
title: "Generate Mnemonic"
slug: "generate-mnemonic-1"
excerpt: ""
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Fri Mar 15 2024 14:13:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:13:48 GMT+0000 (Coordinated Universal Time)"
---
Generating a mnemonic means creating a special phrase that will be the foundation for your wallet. This phrase is like a master key from which all your wallet addresses and their private keys can be generated. It's a crucial step for ensuring the security and recoverability of your wallet.

The Tron Wallet Provider submodule helps in generating a mnemonic easily. This mnemonic phrase, also known as a seed phrase, is vital for creating and recovering wallets on Tron.

```typescript
// Import necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network, Tron } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Tron>({network: Network.TRON,
     configureWalletProviders: [
         TronWalletProvider,
     ]});

// Generate mnemonic using the Tron Wallet Provider submodule
const mnemonic = tatumSdk.walletProvider.use(TronWalletProvider)
.generateMnemonic();

console.log(mnemonic);  // This will print the generated mnemonic

await tatum.destroy()
```
```javascript
// Import necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network, Tron } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init({network: Network.TRON,
     configureWalletProviders: [
         TronWalletProvider,
     ]});

// Generate mnemonic using the Tron Wallet Provider submodule
const mnemonic = tatumSdk.walletProvider.use(TronWalletProvider)
.generateMnemonic();

console.log(mnemonic);  // This will print the generated mnemonic

await tatum.destroy()
```
