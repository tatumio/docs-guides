---
title: "constructionPreprocess"
slug: "rpc-cosmos-constructionpreprocess"
category: "6620f7e31ea673003624a8ce"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Cosmos RPC"
  image: []
  keywords: "cosmos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `constructionPreprocess` method is called prior to `constructionPayloads` to construct a request for any metadata that is needed for transaction construction. This method is used to fetch information such as account nonce. The `options` object returned from this method will be sent to the `constructionMetadata` endpoint **UNMODIFIED** by the caller in an offline execution environment. If your Construction API implementation has configuration options, they MUST be specified in the `constructionPreprocess` request in the `metadata` field.

## Parameters

| Name                   | Type                               | Required | Description                                                  |
| ---------------------- | ---------------------------------- | -------- | ------------------------------------------------------------ |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.        |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, set to `COSMOS` for Cosmos.       |
| `network`              | string (from networkIdentifier)    | Yes      | The network name for Cosmos.                                 |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier.                             |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                   |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                    |
| `operations`           | array                              | Yes      | Describes the operations associated with the transaction.    |
| `operation_identifier` | object (from operations)           | Yes      | Identifier for each operation.                               |
| `index`                | number (from operation_identifier) | Yes      | The index of the operation within the transaction.           |
| `network_index`        | number (from operation_identifier) | No       | Network-specific index of the operation.                     |
| `related_operations`   | array (from operations)            | No       | Operations related to the current operation.                 |
| `index`                | number (from related_operations)   | Yes      | Index of related operations.                                 |
| `network_index`        | number (from related_operations)   | No       | Network-specific index of related operations.                |
| `type`                 | string (from operations)           | Yes      | Type of operation (e.g., "TRANSFER").                        |
| `status`               | string (from operations)           | No       | Status of the operation (e.g., "SUCCESS").                   |
| `account`              | object (from operations)           | No       | Account details involved in the operation.                   |
| `address`              | string (from account)              | Yes      | Cosmos account address associated with the operation.        |
| `sub_account`          | object (from account)              | No       | Details of a sub-account, if applicable.                     |
| `metadata`             | object (from account)              | No       | Metadata for the account.                                    |
| `address`              | string (from sub_account)          | Yes      | Address of the sub-account.                                  |
| `metadata`             | object (from sub_account)          | No       | Metadata for the sub-account.                                |
| `amount`               | object (from operations)           | No       | Details of the amount involved in the operation.             |
| `value`                | string (from amount)               | Yes      | Transaction amount.                                          |
| `currency`             | object (from amount)               | Yes      | Currency details of the transaction.                         |
| `metadata`             | object (from amount)               | No       | Additional currency-related metadata.                        |
| `symbol`               | string (from currency)             | Yes      | Symbol of the currency used.                                 |
| `decimals`             | number (from currency)             | Yes      | Decimal places of the currency.                              |
| `metadata`             | object (from currency)             | No       | Additional currency-related metadata.                        |
| `coin_change`          | object (from operations)           | No       | Information about changes to coin states.                    |
| `coin_identifier`      | object (from coin_change)          | Yes      | Identifier for the coin involved in the change.              |
| `identifier`           | string (from coin_identifier)      | Yes      | Globally unique identifier of a Coin.                        |
| `coin_action`          | string (from coin_change)          | Yes      | Type of action performed on the coin (e.g., 'coin_created'). |
| `metadata`             | object (from operations)           | No       | Additional metadata for operations construction.             |
| `metadata`             | object                             | No       | Additional metadata for transaction construction.            |

## Returns

| Field     | Type   | Description                                    |
| --------- | ------ | ---------------------------------------------- |
| `options` | object | Object containing options for the transaction. |

## Example Result

```json
{
  "options": {
    "fee": "10000",
    "nonce": "3"
  }
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/preprocess' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "mainnet"
    },
    "operations": [
      {
        "operation_identifier": {
          "index": 1
        },
        "type": "TRANSFER",
      }
    ]
}'
```
```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, CosmosRosetta, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Cosmos
const tatum = await TatumSDK.init<CosmosRosetta>({
  network: Network.COSMOS_MAINNET,
});

// Define the input parameters with only required fields
const params = {
  networkIdentifier: {
    blockchain: "cosmos", // Specifies the blockchain
    network: "mainnet", // Specifies the network name
  },
  operations: [
    {
      operation_identifier: {
        index: 1, // Specifies the operation index (number)
      },
      type: "TRANSFER", // Specifies the operation type
    },
  ],
};

// Create a request to fetch metadata for transaction construction
const preprocessRequest = await tatum.rpc.constructionPreprocess(params);

// Log the preprocess request
console.log("Construction Preprocess Request:", preprocessRequest);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```
