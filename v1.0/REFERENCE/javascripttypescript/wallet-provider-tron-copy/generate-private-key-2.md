---
title: "Generate Private Key"
slug: "generate-private-key-2"
excerpt: "Generate private key from Mnemonic"
hidden: false
createdAt: "Fri Mar 15 2024 14:21:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:21:41 GMT+0000 (Coordinated Universal Time)"
---
Creating a private key is creating a unique and secret key that belongs to you. This key is crucial for accessing and controlling your funds.

```typescript
// Import the necessary library and initialize the SDK
import { TezosWalletProvider } from '@tatumio/tezos-wallet-provider';
import { TatumSDK, Network, Tezos } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Tezos>({network: Network.TEZOS,
     configureWalletProviders: [TezosWalletProvider],
});

// Generate Private Key from Mnemonic
const privateKey = await tatumSdk.walletProvider
  .use(TezosWalletProvider)
  .generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

await tatum.destroy();
```
```javascript
// Import the necessary library and initialize the SDK
import { TezosWalletProvider } from '@tatumio/tezos-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init({network: Network.TEZOS,
     configureWalletProviders: [TezosWalletProvider],
});

// Generate Private Key from Mnemonic
const privateKey = await tatumSdk.walletProvider
  .use(TezosWalletProvider)
  .generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

await tatum.destroy();
```
