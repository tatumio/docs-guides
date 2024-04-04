---
title: "Generate Xpub"
slug: "generate-xpub-1"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 14:14:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:14:30 GMT+0000 (Coordinated Universal Time)"
---
Generating an extended public key (xpub) is a way to allow the creation of public addresses without exposing the corresponding private keys. It's an important function for maintaining security while still being able to receive funds.

You can generate Xpub with or without mnemonic.

```typescript
// Import the necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network, Ethereum } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Tron>({network: Network.TRON,
     configureWalletProviders: [
         TronWalletProvider,
     ]});

// Generate xpub using the generated mnemonic
const xpubDetails = await tatumSdk.walletProvider.use(TronWalletProvider)
.generateXpub(mnemonic)


console.log(xpubDetails.xpub);  // This will print the generated xpub

await tatum.destroy()
```
```javascript
// Import the necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

// Initialize the SDK for Tron
const tatumSdk = await TatumSDK.init({
  network: Network.TRON,
  configureWalletProviders: [TronWalletProvider]
});

// Generate xpub using the generated mnemonic
const xpubDetails = await tatumSdk.walletProvider
  .use(TronWalletProvider)
  .generateXpub(mnemonic);

console.log(xpubDetails.xpub);  // This will print the generated xpub

await tatum.destroy();

```
