---
title: "Check if the wallet owns a specific NFT"
slug: "check-if-the-wallet-owns-a-specific-nft"
excerpt: "This function checks if a wallet own's any or a specific nft from a collection, you can pass collection address, wallet address & tokenId as an option parameter."
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Thu Feb 22 2024 13:07:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:42:04 GMT+0000 (Coordinated Universal Time)"
---
# Check if the wallet owns a specific NFT

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/bGQOjoQ",
  "href": "https://codepen.io/tatum-devrel/embed/bGQOjoQ",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


# Overview

In the rapidly growing world of non-fungible tokens (NFTs), verifying the ownership of a particular NFT is crucial for creators, collectors, and traders alike. This guide introduces you to the operation of checking if a wallet owns a specific NFT, providing an efficient way to confirm the possession of unique digital assets. By leveraging this functionality, you can ensure the accuracy and authenticity of your NFT holdings, make well-informed decisions about buying, selling, or holding NFTs, and navigate the dynamic NFT landscape with greater confidence. Ultimately, this operation empowers you to manage your digital assets more effectively, fostering transparency and trust in your NFT transactions.

# How to get the owner of the NFT on the Ethereum network

Use the TatumSDK (`@tatumcom/js`) to check, if the wallet is the owner.

```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const isOwner = await tatum.nft.checkNftOwner({
      tokenAddress: "0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d", // replace with your collection
      tokenId: "1",
      owner: "0x46efbaedc92067e6d60e84ed6395099723252496" // owner wallet
    });
    console.log(isOwner);
  } catch (error) {
    console.error("Error checking NFT owner:", error);
  }
})();


// Expected outcome
// true
```
```typescript Typescript
// yarn add @tatumio/tatum  
import {TatumSDK, Network, Ethereum} from '@tatumio/tatum'

const tatum = await TatumSDK.init\<Ethereum>({network: Network.ETHEREUM})

const isOwner: boolean = await tatum.nft.checkNftOwner({  
  tokenAddress: '0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d', // replace with your collection  
<strong>  tokenId: '1',  
</strong>  owner: '0x46efbaedc92067e6d60e84ed6395099723252496' // owner wallet  
})

console.log(isOwner)
```
```curl cURL
curl --location --request GET 'https://api.tatum.io/v4/data/owners/address?tokenAddress=0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d&tokenId=1&chain=ethereum&address=0x46efbaedc92067e6d60e84ed6395099723252496'
```

# Expected Response

```json5
true
```

## Request interface

```typescript
interface GetTokenOwner {
  /**
   * Token ID
   */
  tokenId: string
  /**
   * Token contract address
   */
  tokenAddress: string
   /**
   * Owner address of the NFT token
   */
  owner: string
}
```

## Response interface

```typescript
interface ResponseDto<boolean> {
  /**
   * Actual payload of the response - true or false result
   */
  data: boolean
  /**
   * Status of the response
   */
  status: Status
  /**
   * In case of ERROR status, this field contains the error message and detailed description
   */
  error?: ErrorWithMessage
}
```

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "h-1": "Supoprt",
    "0-0": "Ethereum / Ethereum Sepolia  \n  \nBNB Smart Chain / BNB Smart Chain Testnet  \n  \nCelo / Celo Alfajores  \n  \nPolygon / Polygon Mumbai",
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
