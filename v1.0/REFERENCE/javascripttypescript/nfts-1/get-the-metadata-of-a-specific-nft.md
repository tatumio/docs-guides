---
title: "Get the metadata of a specific NFT"
slug: "get-the-metadata-of-a-specific-nft"
excerpt: ""
hidden: false
createdAt: "Thu Feb 22 2024 13:08:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:17:01 GMT+0000 (Coordinated Universal Time)"
---
As non-fungible tokens (NFTs) gain popularity in the digital asset space, it becomes increasingly important for creators, collectors, and traders to have access to detailed information about individual NFTs. This guide introduces you to the operation of retrieving the metadata of a specific NFT, providing valuable insights into the unique properties, characteristics, and history of the digital asset. By leveraging this functionality, you can better understand the provenance, rarity, and artistic attributes of the NFT, make well-informed decisions about buying, selling, or holding it, and navigate the dynamic NFT market with greater confidence. Ultimately, this operation allows you to manage your digital assets more effectively and fosters a deeper appreciation for the unique qualities of each NFT.

# How to get the metadata of the NFT on the Ethereum network

Use the TatumSDK (`@tatumio/tatum`) to get the metadata of the specific NFT.

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto, NftTokenDetail} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const metadata: ResponseDto<NftTokenDetail|null> = await tatum.nft.getNftMetadata({
  tokenAddress: '0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d', // replace with your collection
  tokenId: '1'
})

console.log(metadata.data)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const metadata = await tatum.nft.getNftMetadata({
      tokenAddress: "0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d", // replace with your collection
      tokenId: "1"
    });
    console.log(metadata.data);
  } catch (error) {
    console.error("Error getting NFT metadata:", error);
  }
})();
```
```curl
curl 
     --location 
     --request GET 'https://api.tatum.io/v4/data/metadata?chain=ethereum&tokenAddress=0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d&tokenIds=1'
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/XWyoBYd",
  "href": "https://codepen.io/tatum-devrel/embed/XWyoBYd",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


# Request interface

```typescript
interface GetNftMetadata {
  /**
   * Token ID
   */
  tokenId: string
  /**
   * Token contract address
   */
  tokenAddress: string
}
```

# Response interface

{% code overflow="wrap" lineNumbers="true" %}

```typescript
interface NftTokenDetail {
  /**
   * Blockchain network
   */
  chain: string
  /**
   * Token ID
   */
  tokenId: string
  /**
   * Token contract address
   */
  tokenAddress: string
  /**
   * Token type. Either 'nft' (ERC-721) or 'multitoken' (ERC-1155)
   */
  type: 'nft' | 'multitoken'
  /**
   * Token URI
   */
  metadataURI: string
  /**
   * Token metadata
   */
  metadata?: {
    name: string
    description: string
    image: string
    [metadataKey: string]: unknown
  }
}
```

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "h-1": "Support",
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
