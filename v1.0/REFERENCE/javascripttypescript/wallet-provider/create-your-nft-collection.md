---
title: "Create your NFT Collection"
slug: "create-your-nft-collection"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Fri Mar 15 2024 13:03:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:03:49 GMT+0000 (Coordinated Universal Time)"
---
MetaMask is a widely used Ethereum wallet that allows users to manage their Ether and ERC-20 tokens. It also provides an interface for interacting with decentralized applications (dApps) and smart contracts. With the growing popularity of non-fungible tokens (NFTs), you can now leverage MetaMask to create your very own NFT collection contract, opening up a world of opportunities and benefits.

# Why create an NFT collection contract?

NFTs represent unique digital assets that can't be exchanged on a one-to-one basis, differentiating them from other cryptocurrencies. Creating an NFT collection contract allows you to mint, trade, and showcase a series of unique digital items, such as art, collectibles, virtual real estate, or game items. These contracts facilitate the management of your NFT collection, defining rules for minting, transferring, and managing the ownership of your tokens.

> 📘 Info
> 
> MetaMask is designed as a browser extension to provide a user-friendly interface and secure key management for interacting with dApps and web services. Connecting from Node.js is not supported because MetaMask focuses on end-user interactions within web browsers, while Node.js is a server-side JavaScript runtime typically used for backend development.

# How to create your NFT collection with MetaMask from your browser-based application

Use the TatumSDK (`@tatumio/tatum`) to prepare, sign and broadcast the transaction using MetaMask.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/VwVqVKp",
  "href": "https://codepen.io/tatum-devrel/embed/VwVqVKp",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


> 📘 You will leverage the WalletProvider submodule, which includes multiple browser-based wallet extensions. MetaMask is just one of them.

```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network, MetaMask } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    // We have prepared a deploy transaction of ERC-721 contract from your default connected MetaMask account to the recipient
    // Result is a transaction IF of a broadcasted transaction
    const txId = await tatum.walletProvider.use(MetaMask).createNftCollection({
    name: 'Your Collection Name',
    symbol: 'Your Collection Symbol'});
    
    console.log(txId);
    
    // Once the transaction is included in a block, you can get the contract address of the newly created collection
    const contractAddress: string | null = await tatum.rpc.getContractAddress(txId)
    console.log(contractAddress)
  } catch (error) {
    console.error("Error signing a transaction using MetaMask:", error);
  }
})();
```
```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, MetaMask} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

// We have prepared a deploy transaction of ERC-721 contract from your default connected MetaMask account to the recipient
// Result is a transaction IF of a broadcasted transaction
const txId: string = await tatum.walletProvider.use(MetaMask).createNftCollection({
    name: 'Your Collection Name',
    symbol: 'Your Collection Symbol'})

console.log(txId)

// Once the transaction is included in a block, you can get the contract address of the newly created collection
const contractAddress: string | null = await tatum.rpc.getContractAddress(txId)
console.log(contractAddress)
```

## Request object parameters

```typescript
export interface CreateNftCollection {
  /**
   * Name of the token.
   */
  name: string
  /**
   * Symbol of the token.
   */
  symbol: string
  /**
   * base URI of the collection, defaults to empty string. Base URI is prepended to the token ID in the token URI.
   */
  baseURI?: string
  /**
   * (Optional) Address of the admin of the token. Defaults to the connected MetaMask account. Admin can add new minters and pausers.
   */
  author?: string
  /**
   * (Optional) Address of the minter of the token. Defaults to the connected MetaMask account. Minters can mint new tokens.
   */
  minter?: string
}

```

## Response

- **txId** - string, transaction hash of signed and broadcasted transaction
  - Example: `"0xdb1e03f4cea29265f031bfc0514b07c15a5fc5e5cc2fd47f7d9a54c74f5c5637"`

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "h-1": "Support",
    "0-0": "Ethereum / Ethereum Sepolia / Ethereum Goerli  \nBNB Smart Chain / BNB Smart Chain Testnet  \nCelo / Celo Alfajores  \nPolygon / Polygon Mumbai",
    "0-1": "NFTs (BAYC,...)  \nERC-1155 Tokens"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]
