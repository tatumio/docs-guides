---
title: "parseTransaction"
slug: "rpc-cosmos-parsetransaction"
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

The `parseTransaction` method allows you to parse either an unsigned or signed transaction and retrieve detailed information about its contents. This function is crucial for validating transaction details before submitting them to the Cosmos network.

## Request Parameters

| Name                    | Type                               | Required | Description                                                     |
| ----------------------- | ---------------------------------- | -------- | --------------------------------------------------------------- |
| `networkIdentifier`     | object                             | Yes      | Identifies the Cosmos blockchain and network details.           |
| `blockchain`            | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                  |
| `network`               | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.      |
| `subNetworkIdentifier`  | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                         |
| `network`               | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                      |
| `metadata`              | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                       |
| `signed`                | boolean                            | Yes      | Indicates whether the transaction is signed.                    |
| `transaction`           | string                             | Yes      | The transaction blob (either unsigned or signed).               |

## Returns

| Field                    | Description                                       |
| ------------------------ | ------------------------------------------------- |
| `parsedTransaction`      | The details of the parsed transaction.            |

## Example Result

```json
{
  "parsedTransaction": {
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
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/parse' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "network_identifier": {
    "blockchain": "cosmos",
    "network": "cosmos-mainnet"
  },
  "signed": true,
  "transaction": "TRANSACTION_BLOB"
}'
```
```typescript
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

const transactionDetails = await cosmos.rpc.parseTransaction({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet"
  },
  signed: true,
  transaction: "TRANSACTION_BLOB"
});

console.log("Parsed Transaction Details:", transactionDetails);

await cosmos.destroy();
```