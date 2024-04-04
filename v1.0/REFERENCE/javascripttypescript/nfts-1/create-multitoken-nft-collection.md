---
title: "Create MultiToken NFT Collection"
slug: "create-multitoken-nft-collection"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Thu Feb 22 2024 13:06:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:47:51 GMT+0000 (Coordinated Universal Time)"
---
ERC-1155 is a standard for smart contracts on the Ethereum blockchain, which encompasses the functionality of both ERC-20 (fungible tokens, like cryptocurrencies) and ERC-721 (non-fungible tokens, or NFTs) within a single smart contract. This makes it a MultiToken standard.

In the ERC-1155 standard, each token is identified by an ID. What makes this different from ERC-721 (where each token also has a unique ID) is that tokens of the same ID in ERC-1155 are interchangeable, just like ERC-20 tokens. This allows for both fungible and non-fungible tokens to be represented within a single contract.

# Use Cases for ERC-1155 MultiToken Collections

1. **Video Games**: ERC-1155 tokens can represent a wide variety of assets within a game, such as fungible resources (like in-game currency or consumable items) and non-fungible unique items (like a special character or a limited edition weapon). This can all be done within a single, smart contract.
2. **DeFi Platforms**: A single ERC-1155 contract can manage a variety of tokens, such as governance tokens (fungible) and insurance contracts or loan receipts (non-fungible).
3. **Art and Collectibles**: Just like with ERC-721, artists can mint their artworks as NFTs with ERC-1155. However, with ERC-1155 they can also issue fungible tokens, such as prints or copies, alongside the unique piece.
4. **Real World Assets**: ERC-1155 tokens can represent ownership in real world assets, such as real estate or commodities. The fungible tokens can represent a divisible interest in an asset, while non-fungible tokens can represent unique assets.

By using the Tatum SDK to create an ERC-1155 MultiToken collection, you're able to manage a complex economy of both fungible and non-fungible tokens with ease. Whether you're developing an intricate in-game economy or creating a platform with diverse types of assets, ERC-1155 offers a versatile solution for digital ownership and trade.

# How to show create MultiToken NFT Collection (ERC-1155 type) on the Ethereum network

Use the TatumSDK (`@tatumio/tatum`) to get a transaction history of the wallet.

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const tx: ResponseDto<{txId: string}> = await tatum.nft.createMultiTokenNftCollection({
  owner: '0x727ea45b2eb6abb2badd3dc7106d146e0dc0450d', // replace with your address
})

console.log(tx.data.txId)
// 0x8e564406701caab6258501c794f5c1eece380f673be99b561d626c3d8d81b202

// you can get created collection address using this RPC call
const collectionAddress = await tatum.rpc.getContractAddress(tx.data.txId)
console.log(collectionAddress)
// 0x876977006988ce590e219f576077459a49c7318a
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const txs = await tatum.nft.createMultiTokenNftCollection({
      owner: '0x727ea45b2eb6abb2badd3dc7106d146e0dc0450d', // replace with your address
    });
    console.log(txs.data.txId);
    // 0x8e564406701caab6258501c794f5c1eece380f673be99b561d626c3d8d81b202
    
    const collectionAddress = await tatum.rpc.getContractAddress(tx.data.txId);
    console.log(collectionAddress);
    // 0x876977006988ce590e219f576077459a49c7318a
  } catch (error) {
    console.error("Error creating NFT collection:", error);
  }
})();
```
```curl
curl --location --request POST 'https://api.tatum.io/v4/contract/deploy' \
--header 'Content-Type: application/json' \
--data-raw '{
    "contractType": "multitoken",
    "chain": "ethereum-sepolia",
    "owner": "0x727ea45b2eb6abb2badd3dc7106d146e0dc0450d"
}'
```

## Request interface

```typescript
export interface CreateMultiTokenNftCollection {
  /**
   * Address of the NFT collection owner
   */
  owner: string
  /**
   * Address of the NFT collection minter, this is optional and defaults to the owner address
   */
  minter?: string
  /**
   * Optional base URI, which will be prepended to the token URI. If not specified, the token should be minted with the URI
   */
  baseURI?: string
}
```

## Response interface

```typescript
interface ResponseDto<{txId: string}> {
  /**
   * Actual payload of the response
   */
  data: {txId: string}
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
    "0-1": "NFTs (BAYC,...) ERC-1155 Tokens"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    "left",
    "left"
  ]
}
[/block]
