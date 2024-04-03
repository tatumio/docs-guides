---
title: "Generate Xpub"
slug: "generate-xpub"
excerpt: ""
hidden: false
createdAt: "Fri Mar 15 2024 13:29:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:30:21 GMT+0000 (Coordinated Universal Time)"
---
Generating an extended public key (xpub) is a way to allow the creation of public addresses without exposing the corresponding private keys. It's an important function for maintaining security while still being able to receive funds.

You can generate Xpub with or without mnemonic.

```typescript
// Import the necessary library and initialize the SDK
import { EvmWalletProvider } from '@tatumio/evm-wallet-provider';
import { TatumSDK, Network, Ethereum } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM,
     configureWalletProviders: [
         EvmWalletProvider,
     ]});

// Generate xpub using the generated mnemonic
const xpubDetails = await tatumSdk.walletProvider.use(EvmWalletProvider)
.generateXpub(mnemonic);

console.log(xpubDetails.xpub);  // This will print the generated xpub

await tatum.destroy()
```
```javascript
// Install with: npm install @tatumio/evm-wallet-provider @tatumio/tatum
const { EvmWalletProvider } = require("@tatumio/evm-wallet-provider");
const { TatumSDK, Network, Ethereum } = require("@tatumio/tatum");

(async () => {
  try {
    const tatumSdk = await TatumSDK.init({ network: Network.ETHEREUM,
     configureWalletProviders: [
         EvmWalletProvider,
     ]});
    const xpubDetails = await tatumSdk.walletProvider.use(EvmWalletProvider).generateXpub(mnemonic);
    console.log(xpubDetails.xpub);
  } catch (error) {
    console.error("Error generating xpub:", error);
  }
})();

await tatum.destroy()
```
