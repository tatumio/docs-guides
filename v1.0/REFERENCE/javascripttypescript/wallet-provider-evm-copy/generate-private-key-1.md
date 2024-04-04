---
title: "Generate Private Key"
slug: "generate-private-key-1"
excerpt: "Generate private key from Mnemonic"
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Fri Mar 15 2024 14:15:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:15:18 GMT+0000 (Coordinated Universal Time)"
---
Creating a private key is creating a unique and secret key that belongs to you. This key is crucial for accessing and controlling your funds.

```typescript
// Import the necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network, Tron } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Tron>({network: Network.TRON,
     configureWalletProviders: [
         TronWalletProvider,
     ]});

// Generate private key from mnemonic
const privateKey = await tatumSdk.walletProvider.use(TronWalletProvider)
.generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

await tatum.destroy()

```
```javascript
// Import the necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network, Tron } from '@tatumio/tatum';

// Initialize the SDK for Tron
const tatumSdk = await TatumSDK.init({
  network: Network.TRON,
  configureWalletProviders: [TronWalletProvider]
});

// Generate private key from mnemonic
const privateKey = await tatumSdk.walletProvider
  .use(TronWalletProvider)
  .generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

await tatum.destroy()

```
