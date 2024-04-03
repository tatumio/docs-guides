---
title: "Get Private Key, Address, and Mnemonic"
slug: "get-private-key-address-and-mnemonic"
excerpt: ""
hidden: false
createdAt: "Fri Mar 15 2024 14:23:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:23:38 GMT+0000 (Coordinated Universal Time)"
---
This function allows you to obtain the private key, address, and mnemonic using the `TezosWalletProvider` from the Tatum SDK.

```typescript
// Import necessary libraries
import { TezosWalletProvider } from '@tatumio/tezos-wallet-provider';
import { TatumSDK, Network, Tezos } from '@tatumio/tatum';

// Initialize the SDK for Tezos
const tatumSdk = await TatumSDK.init<Tezos>({network: Network.TEZOS,
     configureWalletProviders: [TezosWalletProvider],
});

// Get private key, address and mnemonic
const { privateKey, address, mnemonic } = await tatumSdk.walletProvider
  .use(TezosWalletProvider)
  .getWallet();

// Output the retrieved data
console.log(privateKey);  // Prints the private key
console.log(address);  // Prints the address
console.log(mnemonic);  // Prints the mnemonic
```
```javascript
// Import necessary libraries
import { TezosWalletProvider } from '@tatumio/tezos-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

// Initialize the SDK for Tezos
const tatumSdk = await TatumSDK.init({network: Network.TEZOS,
     configureWalletProviders: [
    { type: TezosWalletProvider, config: { rpcUrl: 'https://ghostnet.ecadinfra.com' } },
  ]
});

// Get private key, address and mnemonic
const { privateKey, address, mnemonic } = await tatumSdk.walletProvider
  .use(TezosWalletProvider)
  .getWallet();

// Output the retrieved data
console.log(privateKey);  // Prints the private key
console.log(address);  // Prints the address
console.log(mnemonic);  // Prints the mnemonic
```
