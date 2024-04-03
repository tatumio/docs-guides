---
title: "Generate Address"
slug: "generate-address-1"
excerpt: "Generate Address from Mnemonic or an Xpub"
hidden: false
createdAt: "Fri Mar 15 2024 14:17:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:17:04 GMT+0000 (Coordinated Universal Time)"
---
These functions allow you to derive a wallet address from a mnemonic or an xpub using the `TronWalletProvider` from the Tatum SDK.

```typescript
// Import the necessary library and initialize the SDK
import { TronWalletProvider } from '@tatumio/tron-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

// Initialize the SDK for Tron
const tatumSdk = await TatumSDK.init<Tron>({
  network: Network.TRON,
  configureWalletProviders: [TronWalletProvider]
});

// Derive address from mnemonic
const addressFromMnemonic = await tatumSdk.walletProvider
  .use(TronWalletProvider)
  .generateAddressFromMnemonic(mnemonic, 0);

// Derive address from xpub
const addressFromXpub = await tatumSdk.walletProvider
  .use(TronWalletProvider)
  .generateAddressFromXpub(xpubDetails.xpub, 0);

// Output the derived addresses
console.log(addressFromMnemonic);  // Prints the address derived from mnemonic
console.log(addressFromXpub);  // Prints the address derived from xpub

await tatum.destroy();
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

// Derive address from mnemonic
const addressFromMnemonic = await tatumSdk.walletProvider
  .use(TronWalletProvider)
  .generateAddressFromMnemonic(mnemonic, 0);

// Derive address from xpub
const addressFromXpub = await tatumSdk.walletProvider
  .use(TronWalletProvider)
  .generateAddressFromXpub(xpubDetails.xpub, 0);

// Output the derived addresses
console.log(addressFromMnemonic);  // Prints the address derived from mnemonic
console.log(addressFromXpub);  // Prints the address derived from xpub

await tatum.destroy();
```
