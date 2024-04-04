---
title: "Generate Address"
slug: "generate-address-2"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 14:22:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:22:35 GMT+0000 (Coordinated Universal Time)"
---
Generating an address is about creating a public address where others can send you funds. It's like an account number in the blockchain world.

You can generate an address with private key.

```typescript
// Import the necessary library and initialize the SDK
import { TezosWalletProvider } from '@tatumio/tezos-wallet-provider';
import { TatumSDK, Network, Tezos } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Tezos>({network: Network.TEZOS,
     configureWalletProviders: [TezosWalletProvider],
});

// Generate Address from Private Key
const address = await tatumSdk.walletProvider
  .use(TezosWalletProvider)
  .generateAddressFromPrivateKey(privateKey);

console.log(address);  // This will print the generated address


await tatum.destroy()

```
```javascript
// Import the necessary library and initialize the SDK
import { TezosWalletProvider } from '@tatumio/tezos-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init({network: Network.TEZOS,
     configureWalletProviders: [TezosWalletProvider],
});

// Generate Address from Private Key
const address = await tatumSdk.walletProvider
  .use(TezosWalletProvider)
  .generateAddressFromPrivateKey(privateKey);

console.log(address);  // This will print the generated address

await tatum.destroy();

```
