---
title: "constructionMetadata"
slug: "rpc-cosmos-constructionmetadata"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Rosetta API for Cosmos"
hidden: false
metadata:
  image: []
  keywords: "cosmos, construction metadata, Rosetta API"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `constructionMetadata` method retrieves metadata necessary to construct transactions for a specific network using the Rosetta API. This is particularly useful in environments where transactions need to be constructed offline or in secure environments.

## Parameters

| Name                   | Type                               | Required | Description                                                                                                                                                           |
| ---------------------- | ---------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.                                                                                                                 |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The name of the blockchain, typically "Cosmos".                                                                                                                       |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place (e.g., "mainnet" or "testnet").                                                                             |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier.                                                                                                                                      |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                                                                                                                            |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                                                                                                                             |
| `options`              | object                             | No       | Optional parameters for specifying the metadata required for different types of transactions. Can include various flags and values depending on the transaction type. |
| `publicKeys`           | array                              | No       | List of public keys involved in the transaction. Each object in the array contains `hexBytes` and `curveType`.                                                        |
| `hexBytes`             | string (from publicKey)            | Yes      | Hexadecimal representation of the public key.                                                                                                                         |
| `curveType`            | string (from publicKey)            | Yes      | Cryptographic curve associated with the public key (e.g., "secp256k1").                                                                                               |

## Returns

| Field      | Type   | Description                                                                                                         |
| ---------- | ------ | ------------------------------------------------------------------------------------------------------------------- |
| `metadata` | object | Contains necessary metadata for transaction construction including signers, sequence number, and recent block hash. |

## Example Result

```json
{
  "metadata": {
    "requiredSigners": [
      {
        "publicKey": "03fa...",
        "signatureType": "ecdsa_recovery"
      }
    ],
    "sequence": 45,
    "recentBlockHash": "abcd1234..."
  }
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/metadata' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "mainnet"
    }
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, CosmosRosetta, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<CosmosRosetta>({
  network: Network.COSMOS_ROSETTA,
});

const constructionMetadata = await tatum.rpc.constructionMetadata({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
});

console.log(constructionMetadata);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
