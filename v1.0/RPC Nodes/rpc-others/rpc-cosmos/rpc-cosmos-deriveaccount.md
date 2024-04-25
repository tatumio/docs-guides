---
title: "deriveAccount"
slug: "rpc-cosmos-deriveaccount"
category: "6620f7e31ea673003624a8cc"
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

The `deriveAccount` method enables you to derive a Cosmos account identifier from a public key, facilitating the association of public keys with specific blockchain addresses.

## Parameters

| Name                   | Type                               | Required | Description                                                          |
| ---------------------- | ---------------------------------- | -------- | -------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.                |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                       |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.           |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                              |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                           |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                            |
| `publicKey`            | object                             | Yes      | Contains the public key information necessary to derive the account. |
| `hexBytes`             | string (from publicKey)            | Yes      | Hexadecimal representation of the public key.                        |
| `curveType`            | string (from publicKey)            | Yes      | The cryptographic curve type of the public key, e.g., "secp256k1".   |
| `metadata`             | object                             | No       | Optional metadata related to the derivation process.                 |

## Returns

| Field               | Type   | Description                                                                   |
| ------------------- | ------ | ----------------------------------------------------------------------------- |
| `accountIdentifier` | object | An object representing the derived account identifier for the Cosmos account. |

## Example Result

```json
{
  "accountIdentifier": "cosmos1..."
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/derive' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "cosmos-mainnet"
    },
    "publicKeys": {
        "hexBytes": "PUBLIC_KEY_HEX_BYTES",
        "curveType": "secp256k1"
    }
}'
```
```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Cosmos
const cosmos = await TatumSDK.init<Cosmos>({
  network: Network.COSMOS_MAINNET,
});

// Define the input parameters with only required fields
const params = {
  networkIdentifier: {
    blockchain: "COSMOS",
    network: "COSMOS_MAINNET",
  },
  publicKeys: {
    hexBytes: "PUBLIC_KEY_HEX_BYTES", // Hexadecimal representation of the public key.
    curveType: "secp256k1", // Cryptographic curve type.
  },
};

// Derive the Cosmos account identifier from the public key
const accountIdentifier = await tatum.rpc.deriveAccount(params);

// Log the derived account identifier
console.log("Account Identifier:", accountIdentifier);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```
