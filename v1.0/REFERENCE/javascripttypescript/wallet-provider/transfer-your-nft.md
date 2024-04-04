---
title: "Transfer your NFT"
slug: "transfer-your-nft"
excerpt: ""
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Fri Mar 15 2024 12:59:34 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 12:59:44 GMT+0000 (Coordinated Universal Time)"
---
An NFT, or Non-Fungible Token, is a unique digital asset that represents ownership or proof of authenticity for a specific item, like a piece of digital artwork, a collectible, or even a virtual property. Transferring an NFT means changing the ownership of that digital item from one person to another.

Imagine you have a one-of-a-kind digital trading card that you'd like to give to a friend. To do this, you would initiate a transfer, which is similar to handing over a physical item to someone else. In the digital world, this transfer process is recorded on a blockchain, a secure and transparent digital ledger that keeps track of every transaction made.

When you transfer an NFT, you're essentially updating the blockchain record to show that your friend is now the new owner of the digital trading card. Once the transfer is complete, your friend has full control over the NFT and can choose to keep it, sell it, or trade it with others. This process ensures that ownership is securely and transparently tracked, preventing counterfeiting or unauthorized duplication of the digital item.

> 📘 Hint
> 
> MetaMask is designed as a browser extension to provide a user-friendly interface and secure key management for interacting with dApps and web services. Connecting from Node.js is not supported because MetaMask focuses on end-user interactions within web browsers, while Node.js is a server-side JavaScript runtime typically used for backend development.

# How to perform an NFT transfer with MetaMask from your browser-based application

Use the TatumSDK (`@tatumcom/js`) to prepare, sign and broadcast the transaction using MetaMask.

> 📘 Hint
> 
> You will leverage the WalletProvider submodule, which includes multiple browser-based wallet extensions. MetaMask is just one of them.

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, MetaMask} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

//This is the BoredApeYachtClub NFT token address
const BAYC = '0xBC4CA0EdA7647A8aB7C2061c2E118A18a936f13D'

const txId: string = await tatum.walletProvider.use(MetaMask).transferNft('0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263', '123', BAYC)

console.log(txId)

// We have prepared a transfer of NFT BAYC#123 from your default connected MetaMask account to the recipient - 0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network, MetaMask } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    //This is the BoredApeYachtClub NFT token address
    const BAYC = '0xBC4CA0EdA7647A8aB7C2061c2E118A18a936f13D'
    
    const txId = await tatum.walletProvider.use(MetaMask).transferNft('0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263', '123', BAYC);
    console.log(txId);
  } catch (error) {
    console.error("Error signing a transaction using MetaMask:", error);
  }
})();

// We have prepared a transfer of NFT BAYC#123 from your default connected MetaMask account to the recipient - 0x4675C7e5BaAFBFFbca748158bEcBA61ef3b0a263
// Result is a transaction IF of a broadcasted transaction
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Martin-Zemanek/embed/QWJEBJW",
  "href": "https://codepen.io/Martin-Zemanek/embed/QWJEBJW",
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
- **`tokenId`** - string, token ID to be sent, always in a token currency like USDT
  - Example: `"1.5"`
- **`tokenAddress`** - string, token address of a NFT collection you want to transfer
  - Example: `"0xdAC17F958D2ee523a2206206994597C13D831ec7"`

## Response

- **txId** - string, transaction hash of signed and broadcasted transaction
  - Example: `"0xdb1e03f4cea29265f031bfc0514b07c15a5fc5e5cc2fd47f7d9a54c74f5c5637"`
