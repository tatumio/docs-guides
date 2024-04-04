---
title: "Get all NFTs the wallet holds"
slug: "get-all-nfts-the-wallet-holds"
excerpt: "This function helps you to fetch all the NFT's a wallet holds, all you have to do is pass the address to the function parameter and chain while initialising the sdk."
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Thu Feb 22 2024 13:01:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:13:42 GMT+0000 (Coordinated Universal Time)"
---
# Get all NFTs the wallet holds

The world of non-fungible tokens (NFTs) has witnessed exponential growth, attracting artists, collectors, and investors alike. As users accumulate various NFTs across multiple blockchain networks, it becomes crucial to manage and track their digital collections. This guide introduces you to the operation of obtaining all NFTs associated with a particular address, offering you a comprehensive snapshot of your NFT holdings. By leveraging this functionality, you can effectively monitor your NFT collection, verify ownership, and assess the value of your digital assets. Ultimately, this operation empowers you to take full control of your unique digital assets and manage them with greater ease and efficiency.

# How to get NFTs on a wallet in the Ethereum network

Use the TatumSDK (`@tatumio/tatum`) to get a balance of the wallet.

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto, NftAddressBalance} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const balance: ResponseDto<NftAddressBalance[]> = await tatum.nft.getBalance({
  addresses: ['0x727EA45B2EB6abb2badD3dC7106d146E0Dc0450d'], // replace with your address
})

console.log(balance.data)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const balance = await tatum.nft.getBalance({
      addresses: ['0x727EA45B2EB6abb2badD3dC7106d146E0Dc0450d'], // replace with your address
    });
    console.log(balance.data);
  } catch (error) {
    console.error("Error fetching NFT balance:", error);
  }
})();
```
```curl
curl 
     --location 
     --request GET 'https://api.tatum.io/v4/data/balances?chain=ethereum&addresses=0x727EA45B2EB6abb2badD3dC7106d146E0Dc0450d'
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/oNQJyJb",
  "href": "https://codepen.io/tatum-devrel/embed/oNQJyJb",
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
    "balance": "2
    ",
    "chain": "ethereum-mainnet",
    "lastUpdatedBlockNumber": 14086122,
    "metadata": {
        "description": "# ***\"Sometimes I swear I can see .... | Joey Camacho ]*",
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

## Request interface

{% code overflow="wrap" lineNumbers="true" %}

```typescript
interface AddressBalanceDetails {
  /**
   * List of addresses to check.
   */
  addresses: string[]
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

interface NftAddressBalance {
  /**
   * Balance of the address.
   */
  balance: string
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
  /**
   * Block number of the last balance update.
   */
  lastUpdatedBlock: number
}
```

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "h-1": "Support",
    "0-0": "Ethereum / Ethereum Sepolia  \n  \nBNB Smart Chain / BNB Smart Chain Testnet  \n  \nCelo / Celo Alfajores  \n  \nPolygon / Polygon Mumbai",
    "0-1": "Multiple addresses per 1 invocation  \nNFTs (BAYC,...)<br>ERC-1155 Tokens"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]
