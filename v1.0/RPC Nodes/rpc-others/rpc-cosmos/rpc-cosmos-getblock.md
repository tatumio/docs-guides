---
title: "getBlock"
slug: "rpc-cosmos-getblock"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Retrieve a block in the Cosmos blockchain by Block Identifier."
  image: []
  keywords: "cosmos, rosetta, blockchain, block"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `getBlock` endpoint is designed to fetch a block from the Cosmos blockchain using a specific Block Identifier. This can be done either by the block's hash or by its height. If transactions are available, they are included directly in the response; otherwise, Transaction Identifiers are provided for subsequent fetches.

## Description

Retrieve a block by its Block Identifier. If transactions are included in the response, they are part of the returned Block object. If the transactions are not included, an array of Transaction Identifiers is returned for further fetches. Requests by block hash must be idempotent, always returning the same block contents for the same hash. Requests by block height do not have this restriction due to the possibility of chain reorganizations.

## Request Parameters

| Name                   | Type                               | Required | Description                                                     |
| ---------------------- | ---------------------------------- | -------- | --------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.           |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                  |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.      |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                         |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                      |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                       |
| `blockIdentifier`      | object                             | Yes      | The identifier of the block to fetch. Can be by hash or height. |
| `index`                | number (from blockIdentifier)      | No       | The height of the block (optional if hash is provided).         |
| `hash`                 | string (from blockIdentifier)      | No       | The hash of the block (optional if index is provided).          |

## Returns

| Field                     | Description                                                     |
| ------------------------- | --------------------------------------------------------------- |
| `block_identifier`        | Information about the current block, including index and hash.  |
| `index`                   | The index (height) of the block.                                |
| `hash`                    | The hash of the block.                                          |
| `parent_block_identifier` | Information about the parent block, including index and hash.   |
| `index`                   | The index (height) of the parent block.                         |
| `hash`                    | The hash of the parent block.                                   |
| `timestamp`               | The timestamp at which the block was proposed, in milliseconds. |
| `transactions`            | An array of transactions included in the block.                 |
| `transaction_identifier`  | Identifier for each transaction within the block.               |
| `hash`                    | The hash of the transaction.                                    |
| `operations`              | An array detailing operations within each transaction.          |

Each transaction detail is further broken down into identifiers and operations, providing a comprehensive breakdown of the block's contents.

## Example Result

```json
{
  "block": {
    "block_identifier": {
      "index": 19865674,
      "hash": "9035A963AA5A28729F0BA316801E901A4E8B1500B2E28301FA296C2D61816F53"
    },
    "parent_block_identifier": {
      "index": 19865673,
      "hash": "200CF85D862597295BB6D6E34888F94849B729C6D7AC688749ADCA387A57E9CD"
    },
    "timestamp": 1712310176442,
    "transactions": [
      {
        "transaction_identifier": {
          "hash": "txHash123456"
        },
        "operations": [
          // List of operations
        ]
      }
    ]
  }
}
```
## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/block' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "network_identifier": {
    "blockchain": "cosmos",
    "network": "mainnet"
  },
  "block_identifier": {
    "hash": "9035A963AA5A28729F0BA316801E901A4E8B1500B2E28301FA296C2D61816F53"
  }
}
```
```typescript
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({
  network: Network.COSMOS_MAINNET,
});

const blockInfo = await tatum.rpc.getBlock({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
  block_identifier: {
    hash: "abcdef1234567890abcdef1234567890abcdef1234567890abcdef1234567890", // Optional if you know the block hash
  },
});

console.log("Block Information:", blockInfo);

await tatum.destroy();
```
