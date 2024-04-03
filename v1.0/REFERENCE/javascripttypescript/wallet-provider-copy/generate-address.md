---
title: "Generate Address"
slug: "generate-address"
excerpt: ""
hidden: false
createdAt: "Fri Mar 15 2024 13:31:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:32:01 GMT+0000 (Coordinated Universal Time)"
---
Generating an address is about creating a public address where others can send you funds. It's like an account number in the blockchain world.

You can generate an address with both Mnemonic or Xpub

```typescript
// Import the necessary library and initialize the SDK
import { EvmWalletProvider } from '@tatumio/evm-wallet-provider';
import { TatumSDK, Network, Ethereum } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM,
     configureWalletProviders: [
         EvmWalletProvider,
     ]});

// Generate address from mnemonic or xpub
const addressFromMnemonic = await tatumSdk.walletProvider
.use(EvmWalletProvider).generateAddressFromMnemonic(mnemonic, 0);
const addressFromXpub = await tatumSdk.walletProvider
.use(EvmWalletProvider).generateAddressFromXpub(xpubDetails.xpub, 0);

// This will print the generated address from mnemonic
console.log(addressFromMnemonic);
// This will print the generated address from xpub
console.log(addressFromXpub);

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
    const addressFromMnemonic = await tatumSdk.walletProvider
    .use(EvmWalletProvider).generateAddressFromMnemonic(mnemonic, 0);
    const addressFromXpub = await tatumSdk.walletProvider
    .use(EvmWalletProvider).generateAddressFromXpub(xpubDetails.xpub, 0);
    console.log(addressFromMnemonic);
    console.log(addressFromXpub);
  } catch (error) {
    console.error("Error generating address:", error);
  }
})();

await tatum.destroy()
```
