---
title: "Generate Private Key"
slug: "generate-private-key-3"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 14:27:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:27:52 GMT+0000 (Coordinated Universal Time)"
---
Creating a private key is creating a unique and secret key that belongs to you. This key is crucial for accessing and controlling your funds.

```typescript
// Import the necessary library and initialize the SDK
import { UtxoWalletProvider } from '@tatumio/utxo-wallet-provider';
import { TatumSDK, Network, Bitcoin } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN,
     configureWalletProviders: [
         UtxoWalletProvider,
     ]});

// Generate private key from mnemonic
const privateKey = await tatumSdk.walletProvider.use(UtxoWalletProvider)
.generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

await tatum.destroy();


```
```javascript
// Import the necessary library and initialize the SDK
import { UtxoWalletProvider } from '@tatumio/utxo-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init({network: Network.BITCOIN,
     configureWalletProviders: [
         UtxoWalletProvider,
     ]});

// Generate private key from mnemonic
const privateKey = await tatumSdk.walletProvider.use(UtxoWalletProvider)
.generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

await tatum.destroy();
```
