---
title: "getHashOfTransaction"
slug: "rpc-cosmos-gethashoftransaction"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Calculate the transaction hash for a signed transaction on the Cosmos blockchain."
  image: []
  keywords: "cosmos, rpc, transaction hash"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `getHashOfTransaction` method computes the hash for a signed transaction, providing a unique identifier used to track and verify transactions on the Cosmos network.

## Description

This method is essential for obtaining a transaction hash from a signed transaction blob. This hash serves as the transaction's unique identifier within the Cosmos blockchain, aiding in transaction verification and tracking.

## Request Parameters

| Name                   | Type                               | Required | Description                                                         |
| ---------------------- | ---------------------------------- | -------- | ------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.               |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                      |
| `network`              | string (from networkIdentifier)    | Yes      | The network name, e.g., "cosmos-mainnet".                           |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                             |
| `network`              | string (from subNetworkIdentifier) | Yes       | The name of the sub-network within Cosmos.                          |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                           |
| `signedTransaction`    | string                             | Yes      | The signed transaction blob for which the hash is to be calculated. |

## Returns

| Field             | Description                                                           |
| ----------------- | --------------------------------------------------------------------- |
| `transactionHash` | The hash of the signed transaction, serving as its unique identifier. |

## Example Result

```json
{
"transaction_hash": "0x2f23fd8cca835af21f3ac375bac601f97ead75f2e79143bdf71fe2c4be043e8f"
}
```
## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/hash' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "network_identifier": {
    "blockchain": "cosmos",
    "network": "mainnet"
  },
  "signedTransaction": "SIGNED_TRANSACTION_BLOB"
}
```
```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, CosmosRosetta, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Cosmos
const tatum = await TatumSDK.init<CosmosRosetta>({
  network: Network.COSMOS_ROSETTA,
});

// Define the input parameters in a single object
const hashRequest = {
  networkIdentifier: {
    blockchain: "COSMOS", // Specify the blockchain identifier ('COSMOS' for Cosmos).
    network: "NETWORK_NAME", // Specify the network name.
  },
  signedTransaction: "SIGNED_TRANSACTION", // Specify the signed transaction blob.
};

// Calculate the hash of the transaction
const transactionHash = await tatum.rpc.getHashOfTransaction(hashRequest);

// Log the transaction hash
console.log("Transaction Hash:", transactionHash);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```