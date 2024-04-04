---
title: "Transfer fungible tokens like USDT"
slug: "transfer-fungible-tokens-like-usdt"
excerpt: ""
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Fri Mar 15 2024 13:10:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:11:02 GMT+0000 (Coordinated Universal Time)"
---
Preparing a transaction for signing via MetaMask means creating a transaction object containing essential details, such as the sender's address, recipient's address, amount to be sent, and gas fees. This transaction object is then presented to MetaMask, which securely signs the transaction using the user's private key, ensuring the transaction's authenticity and integrity before it's broadcasted to the Ethereum network.

> 📘 Hint
> 
> MetaMask is designed as a browser extension to provide a user-friendly interface and secure key management for interacting with dApps and web services. Connecting from Node.js is not supported because MetaMask focuses on end-user interactions within web browsers, while Node.js is a server-side JavaScript runtime typically used for backend development.

# How to perform a USDT transaction with MetaMask from your browser-based application

Use the TatumSDK (`@tatumcom/js`) to prepare, sign and broadcast the transaction using MetaMask.

> 📘 Hint
> 
> You will leverage the WalletProvider submodule, which includes multiple browser-based wallet extensions. MetaMask is just one of them.

```typescript
// yarn add @tatumcom/js
import {TatumSDK, Network, Ethereum, MetaMask} from '@tatumcom/js'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

//This is the USDT token address
const USDT = '0xdAC17F958D2ee523a2206206994597C13D831ec7'

const txId: string = await tatum.walletProvider.use(MetaMask).transferErc20('0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263', '1.5', USDT)

console.log(txId)

// We have prepared a transfer of 1.5 USDT from your default connected MetaMask account to the recipient of 0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263
```
```javascript
// Install with: npm install @tatumcom/js
const { TatumSDK, Network, MetaMask } = require("@tatumcom/js");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    //This is the USDT token address
    const USDT = '0xdAC17F958D2ee523a2206206994597C13D831ec7'
    
    const txId = await tatum.walletProvider.use(MetaMask).transferErc20('0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263', '1.5', USDT);
    console.log(txId);
  } catch (error) {
    console.error("Error signing a transaction using MetaMask:", error);
  }
})();

// We have prepared a transfer of 1.5 USDT from your default connected MetaMask account to the recipient of 0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Martin-Zemanek/embed/bGQeQaZ",
  "href": "https://codepen.io/Martin-Zemanek/embed/bGQeQaZ",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


## Request parameters

- **`recipient`** - string, recipient of your transaction
  - Example: `"0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263"`
- **`amount`** - string, amount to be sent, always in a token currency like USDT
  - Example: `"1.5"`
- **`tokenAddress`** - string, token address of a token you want to transfer
  - Example: `"0xdAC17F958D2ee523a2206206994597C13D831ec7"`

## Response

- **txId** - string, transaction hash of signed and broadcasted transaction
  - Example: `"0xdb1e03f4cea29265f031bfc0514b07c15a5fc5e5cc2fd47f7d9a54c74f5c5637"`
