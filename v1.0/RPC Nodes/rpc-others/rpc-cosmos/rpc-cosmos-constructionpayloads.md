---
title: "constructionPayloads"
slug: "rpc-cosmos-constructionpayloads"
category: "6620f7e31ea673003624a8ce"
excerpt: "Rosetta API for Cosmos"
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

The `constructionPayloads` contains the network, a slice of operations, and arbitrary metadata that was returned by the call to `constructionMetadata`. Optionally, the request can also include an array of publicKeys associated with the AccountIdentifiers returned in `constructionPreprocess` response.

## Parameters

| Name                   | Type                               | Required | Description                                                                                             |
| ---------------------- | ---------------------------------- | -------- | ------------------------------------------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.                                                   |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The name of the blockchain, typically "Cosmos".                                                         |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.                                              |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier.                                                                        |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                                                              |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                                                               |
| `operations`           | array                              | Yes      | An array of operation objects, each representing a transaction component.                               |
| `operationIdentifier`  | object (from operations)           | Yes      | Identifier for the operation. Includes `index` and optionally `network_index`.                          |
| `index`                | number (from operationIdentifier)  | Yes      | The index of the operation within the transaction.                                                      |
| `network_index`        | number (from operationIdentifier)  | No       | Network-specific index of the operation.                                                                |
| `relatedOperations`    | array (from operations)            | No       | Operations related to the current operation.                                                            |
| `index`                | number (from relatedOperations)    | Yes      | Index of related operations.                                                                            |
| `network_index`        | number (from relatedOperations)    | No       | Network-specific index of related operations.                                                           |
| `type`                 | string (from operations)           | Yes      | The type of operation, e.g., "TRANSFER".                                                                |
| `status`               | string (from operations)           | No       | The status of the operation.                                                                            |
| `account`              | object (from operations)           | No       | The account involved in the operation. Includes `address`, and optionally `subAccount` and `metadata`.  |
| `address`              | string (from account)              | Yes      | The Cosmos account address associated with the operation.                                               |
| `subAccount`           | object (from account)              | No       | An optional sub-account object.                                                                         |
| `metadata`             | object (from account)              | No       | Metadata for the account.                                                                               |
| `address`              | string (from subAccount)           | Yes       | The sub-account address.                                                                                |
| `metadata`             | object (from subAccount)           | No       | An optional metadata object for the sub-account.                                                        |
| `amount`               | object (from operations)           | No       | The monetary amount involved in the operation. Includes `value`, `currency`, and optionally `metadata`. |
| `value`                | string (from amount)               | Yes      | The value of the transaction amount.                                                                    |
| `currency`             | object (from amount)               | Yes      | An object specifying the currency details. Includes `symbol`, `decimals`, and optionally `metadata`.    |
| `metadata`             | object (from amount)               | No       | Metadata object for the amount.                                                                         |
| `symbol`               | string (from currency)             | Yes      | The symbol or code of the currency.                                                                     |
| `decimals`             | number (from currency)             | Yes      | The number of decimal places for the currency.                                                          |
| `metadata`             | object (from currency)             | No       | Any additional information related to the currency itself, such as contract addresses.                  |
| `coin_change`          | object (from operations)           | No       | Information about changes to the coin state (e.g., created or spent).                                   |
| `coinIdentifier`       | object (from coin_change)          | Yes      | An object containing a coin identifier.                                                                 |
| `identifier`           | string (from coinIdentifier)       | Yes      | Identifier should be populated with a globally unique identifier of a Coin.                             |
| `coin_action`          | string (from coin_change)          | Yes      | CoinActions are different state changes that a Coin can undergo.                                        |
| `publicKeys`           | array                              | No       | List of public keys involved in authorizing the transaction.                                            |
| `hexBytes`             | string (from publicKeys)           | Yes      | Hexadecimal representation of the public key.                                                           |
| `curveType`            | string (from publicKeys)           | Yes      | The cryptographic curve type of the public key, e.g., "secp256k1".                                      |
| `metadata`             | object (from operations)           | No       | Additional information about the operation.                                                             |
| `metadata`             | object                             | No       | Optional metadata for transaction construction.                                                         |

## Returns

| Field                  | Type   | Description                                                         |
| ---------------------- | ------ | ------------------------------------------------------------------- |
| `unsigned_transaction` | string | A hexadecimal string representing the unsigned transaction data.    |
| `payloads`             | array  | An array of objects containing the information that must be signed. |

## Example Result

```json
{
  "unsigned_transaction": "0x...",
  "payloads": [
    {
      "address": "cosmos1...",
      "hex_bytes": "f2ca1bb6c7...",
      "signature_type": "ecdsa_recovery"
    }
  ]
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "mainnet"
    },
    "operations": [
      {
        "operationIdentifier": {
          "index": 1
        },
        "type": "TRANSFER",
      }
    ]
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

const params = {
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
  operations: [
    {
      operationIdentifier: {
        index: 1,
      },
      type: "TRANSFER",
    },
  ],
  publicKeys: [
    {
      hexBytes: "abc123...",
      curveType: "secp256k1",
    },
  ],
};

const constructionPayloads = await tatum.rpc.constructionPayloads(params);

console.log("Construction Payloads:", constructionPayloads);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
