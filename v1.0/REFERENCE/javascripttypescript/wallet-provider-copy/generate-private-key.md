---
title: "Generate Private Key"
slug: "generate-private-key"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 13:30:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:31:13 GMT+0000 (Coordinated Universal Time)"
---
Creating a private key is creating a unique and secret key that belongs to you. This key is crucial for accessing and controlling your funds.

```typescript
// Import the necessary library and initialize the SDK
import { EvmWalletProvider } from '@tatumio/evm-wallet-provider';
import { TatumSDK, Network, Ethereum } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM,
     configureWalletProviders: [
         EvmWalletProvider,
     ]});

// Generate private key from mnemonic
const privateKey = await tatumSdk.walletProvider.use(EvmWalletProvider)
.generatePrivateKeyFromMnemonic(mnemonic, 0);

console.log(privateKey);  // This will print the generated private key

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
    const privateKey = await tatumSdk.walletProvider.use(EvmWalletProvider)
    .generatePrivateKeyFromMnemonic(mnemonic, 0);
    console.log(privateKey);
  } catch (error) {
    console.error("Error generating private key:", error);
  }
})();


await tatum.destroy()
```
