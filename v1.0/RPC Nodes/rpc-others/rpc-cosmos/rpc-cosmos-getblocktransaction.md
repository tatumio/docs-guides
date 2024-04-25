---
title: "getBlockTransaction"
slug: "rpc-cosmos-getblocktransaction"
category: "6620f7e31ea673003624a8cc"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Cosmos RPC"
  image: []
  keywords: "cosmos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `getBlockTransaction` method is used to retrieve detailed information about a specific transaction within a Cosmos block, utilizing the transaction's unique identifier and the block's identifier.

## Description

Retrieve a specific transaction by its identifier from a Cosmos block. This request needs to specify the block by its hash or index and the transaction by its hash. If the transaction is found within the specified block, its details are returned.

## Request Parameters

| Name                    | Type                               | Required | Description                                                     |
| ----------------------- | ---------------------------------- | -------- | --------------------------------------------------------------- |
| `networkIdentifier`     | object                             | Yes      | Identifies the Cosmos blockchain and network details.           |
| `blockchain`            | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "cosmos".                  |
| `network`               | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.      |
| `subNetworkIdentifier`  | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                         |
| `network`               | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                      |
| `metadata`              | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                       |
| `blockIdentifier`       | object                             | Yes      | The identifier of the block to fetch. Can be by hash or height. |
| `index`                 | number (from blockIdentifier)      | No       | The height of the block (optional if hash is provided).         |
| `hash`                  | string (from blockIdentifier)      | No       | The hash of the block (optional if index is provided).          |
| `transactionIdentifier` | object                             | Yes      | Identifies the transaction within the specified block.          |
| `hash`                  | string                             | Yes      | The hash of the transaction.                                    |

## Returns

| Field                    | Description                                       |
| ------------------------ | ------------------------------------------------- |
| `transaction`            | The details of the requested transaction.         |
| `transaction_identifier` | The unique identifier of the transaction.         |
| `operations`             | A list of operations involved in the transaction. |

## Example Result

```json
{
  "transaction": {
    "transaction_identifier": {
      "hash": "TRANSACTION_HASH"
    },
    "operations": [
      {
        "operation_identifier": {
          "index": 0
        },
        "type": "TRANSFER",
        "status": "SUCCESS",
        "account": {
          "address": "cosmos1..."
        },
        "amount": {
          "value": "-1000",
          "currency": {
            "symbol": "ATOM",
            "decimals": 6
          }
        }
      }
    ]
  }
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/block/transaction' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "network_identifier": {
    "blockchain": "cosmos",
    "network": "mainnet"
  },
  "block_identifier": {
    "hash": "0x1f2cc6c5027d2f201a5453ad1119574d2aed23a392654742ac3c78783c071f85"
  },
  "transaction_identifier": {
    "hash": "TRANSACTION_HASH"
  }
}
```
```typescript
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

const transactionDetails = await tatum.rpc.getBlockTransaction({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
  blockIdentifier: {
    index: 19865674,
  },
  transactionIdentifier: {
    hash: "TRANSACTION_HASH",
  },
});

console.log("Transaction Details:", transactionDetails);

await tatum.destroy();
```
