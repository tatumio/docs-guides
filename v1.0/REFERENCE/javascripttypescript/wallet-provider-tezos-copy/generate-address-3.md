---
title: "Generate Address"
slug: "generate-address-3"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 14:28:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:28:35 GMT+0000 (Coordinated Universal Time)"
---
Generating an address is about creating a public address where others can send you funds. It's like an account number in the blockchain world.

You can generate an address with both Mnemonic or Xpub

```typescript
// Import the necessary library and initialize the SDK
import { UtxoWalletProvider } from '@tatumio/utxo-wallet-provider';
import { TatumSDK, Network, Bitcoin } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN,
     configureWalletProviders: [
         UtxoWalletProvider,
     ]});

// Generate address from mnemonic or xpub
const addressFromMnemonic = await tatumSdk.walletProvider
.use(UtxoWalletProvider).generateAddressFromMnemonic(mnemonic, 0);
const addressFromXpub = await tatumSdk.walletProvider
.use(UtxoWalletProvider).generateAddressFromXpub(xpubDetails.xpub, 0);

// This will print the generated address from mnemonic
console.log(addressFromMnemonic);
// This will print the generated address from xpub
console.log(addressFromXpub);

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

// Generate address from mnemonic or xpub
const addressFromMnemonic = await tatumSdk.walletProvider
.use(UtxoWalletProvider).generateAddressFromMnemonic(mnemonic, 0);
const addressFromXpub = await tatumSdk.walletProvider
.use(UtxoWalletProvider).generateAddressFromXpub(xpubDetails.xpub, 0);

// This will print the generated address from mnemonic
console.log(addressFromMnemonic);
// This will print the generated address from xpub
console.log(addressFromXpub);

await tatum.destroy();

```
