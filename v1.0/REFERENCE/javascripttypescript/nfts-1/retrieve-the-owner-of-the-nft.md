---
title: "Retrieve the owner of the NFT"
slug: "retrieve-the-owner-of-the-nft"
excerpt: ""
hidden: false
createdAt: "Thu Feb 22 2024 13:07:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:21:01 GMT+0000 (Coordinated Universal Time)"
---
In the rapidly evolving world of non-fungible tokens (NFTs), it is essential for creators, collectors, and traders to have the ability to verify the ownership of individual NFTs. This guide introduces you to the operation of retrieving the owner of a specific NFT, providing you with the necessary information to confirm the current holder of the unique digital asset. By leveraging this functionality, you can ensure the authenticity and provenance of the NFT, make informed decisions about buying, selling, or holding it, and navigate the dynamic NFT market with confidence. Ultimately, this operation enables you to manage your digital assets more effectively and maintain the integrity of your NFT transactions.

# How to get the owner of the NFT on the Ethereum network

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto, NftTransaction} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const owner: ResponseDto<string[]> = await tatum.nft.getNftOwner({
  tokenAddress: '0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d', // replace with your collection
  tokenId: '1'
})

console.log(owner.data)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const txs = await tatum.nft.getNftOwner({
      tokenAddress: "0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d", // replace with your collection
      tokenId: "1"
    });
    console.log(txs.data);
  } catch (error) {
    console.error("Error fetching NFT owner:", error);
  }
})();
```
```curl
curl 
     --location 
     --request GET 'https://api.tatum.io/v4/data/owners?tokenAddress=0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d&tokenId=1&chain=ethereum'
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/rNQorxB",
  "href": "https://codepen.io/tatum-devrel/embed/rNQorxB",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


# Expected Response

```json5
[
 "0x46efbaedc92067e6d60e84ed6395099723252496"
]
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
   * Optional page size. If not specified, the default page size is used, which is 10.
   */
  pageSize?: number
  /**
   * Optional page number. If not specified, the first page is returned.
   */
  page?: number
}
```

## Response interface

```typescript
interface ResponseDto<string[]> {
  /**
   * Actual payload of the response - list of the owner address
   */
  data: string[]
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
