---
title: "Get all NFTs in the NFT collection"
slug: "get-all-nfts-in-the-nft-collection"
excerpt: ""
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Thu Feb 22 2024 13:03:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 12:52:14 GMT+0000 (Coordinated Universal Time)"
---
As the non-fungible token (NFT) market continues to flourish, creators, collectors, and traders need efficient ways to manage and explore their digital collections. This guide introduces you to the operation of retrieving all NFTs in a specific collection, providing a comprehensive view of the unique digital assets grouped together. By leveraging this functionality, you can easily navigate and analyze your NFT collection, gain insights into the themes and trends within your portfolio, and make informed decisions about buying, selling, or holding specific NFTs. Ultimately, this operation enables you to better understand your digital assets, streamlines your NFT management, and empowers you to engage with the NFT market more effectively.

### How to get NFTs of a collection in the Ethereum network

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto, NftTokenDetail} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const nfts: ResponseDto<NftTokenDetail[]> = await tatum.nft.getNftsInCollection({
  collectionAddress: '0xBC4CA0EdA7647A8aB7C2061c2E118A18a936f13D', // replace with your collection
})

console.log(nfts.data)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const nfts = await tatum.nft.getNftsInCollection({
  collectionAddress: '0xBC4CA0EdA7647A8aB7C2061c2E118A18a936f13D', // replace with your collection
    });
    console.log(nfts.data);
  } catch (error) {
    console.error("Error fetching NFT collection:", error);
  }
})();
```
```curl
curl 
    --location 
    --request GET
    'https://api.tatum.io/v4/data/collections?collectionAddresses=0xBC4CA0EdA7647A8aB7C2061c2E118A18a936f13D&chain=ethereum'
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/eYQbKxX",
  "href": "https://codepen.io/tatum-devrel/embed/eYQbKxX",
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
    {
    "address": "0x727ea45b2eb6abb2badd3dc7106d146e0dc0450d",
    "balance": "2",
    "chain": "ethereum-mainnet",
    "lastUpdatedBlockNumber": 14086122,
    "metadata": {
        "description": "# ***\"Sometimes I swear I can see a glimmer of the Sun through all the layers of chaos. It's probably just wishful thinking. There's a lot of that here.\" — Renn Dialos, Alexandria Research Node 557***\n### **1 / 71492 Jupiter DAO Tokens**\n\nThis token represents proportional ownership over Jupiter. Together with other Jupiter DAO Token holders, its owner is able to actively build and govern the planet into its own unique environment.\n\n*Jupiter represents 10.4% of the total voting power for MetaHero Universe's United Planets DAO.*\n\n*[ Token Design by: TheVirtunaut, Odious, Raw & Rendered | Joey Camacho ]*",
        "external_url": "https://punkscomic.com",
        "image": "ipfs://QmS21WhH94jBnYompXHD1SxS6Gw2bY8E81sTYRktWrYa7a/JUPITER.mp4",
        "name": "MetaHero Universe: Jupiter DAO Token"
    },
    "metadataURI": "ipfs://QmR9PokA9rnKKUF1uLtZyHYEhExqQU1Z7t8AbovMBxND4U/5",
    "tokenAddress": "0x7deb7bce4d360ebe68278dee6054b882aa62d19c",
    "tokenId": "5",
    "type": "multitoken"
    }
]
```

# Request interface

```typescript
interface GetCollection {
  /**
   * Collection contract address
   */
  collectionAddress: string
  /**
   * Optional flag to exclude metadata from the response. In this case, only token IDs are returned. Defaults to false.
   */
  excludeMetadata?: boolean
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
interface ResponseDto<T> {
  /**
   * Actual payload of the response
   */
  data: T
  /**
   * Status of the response
   */
  status: Status
  /**
   * In case of ERROR status, this field contains the error message and detailed description
   */
  error?: ErrorWithMessage
}

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
    "0-1": "Multiple addresses per 1 invocation<br>NFTs (BAYC,...)"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]
