---
title: "createNetworkTransaction"
slug: "rpc-cosmos-createnetworktransaction"
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

The `createNetworkTransaction` method allows you to create a network-specific transaction from an unsigned transaction and an array of provided signatures. The signed transaction returned from this method will be sent to the `submitTransaction` endpoint by the caller.

## Parameters

| Name                   | Type                               | Required | Description                                                                        |
| ---------------------- | ---------------------------------- | -------- | ---------------------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.                              |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                                     |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.                         |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                                            |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                                         |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                                          |
| `unsignedTransaction`  | string                             | Yes      | Contains the unsigned transaction blob.                                            |
| `signatures`           | array                              | Yes      | An array of signature objects.                                                     |
| `signing_payload`      | object (from signatures)           | Yes      | The payload that was signed.                                                       |
| `address`              | string (from signing_payload)      | No       | [DEPRECATED] Network-specific address of the account that should sign the payload. |
| `accountIdentifier`    | object (from signing_payload)      | No       | Contains information about the account.                                            |
| `address`              | string (from accountIdentifier)    | Yes      | The Cosmos account address associated with the operation.                          |
| `sub_account`          | object (from accountIdentifier)    | No       | Optional sub-account object.                                                       |
| `address`              | string (from sub_account)          | Yes      | The sub-account address.                                                           |
| `metadata`             | object (from sub_account)          | No       | Metadata for the sub-account.                                                      |
| `metadata`             | object (from accountIdentifier)    | No       | Metadata for the account.                                                          |
| `hex_bytes`            | string (from signing_payload)      | Yes      | Hex-encoded string of the payload bytes.                                           |
| `signatureType`        | string (from signing_payload)      | No       | Signature type (e.g., "ecdsa", "ed25519").                                         |
| `publicKey`            | object (from signatures)           | Yes      | Contains the public key.                                                           |
| `hexBytes`             | string (from publicKey)            | Yes      | Hexadecimal representation of the public key.                                      |
| `curveType`            | string (from publicKey)            | Yes      | The cryptographic curve type of the public key (e.g., "secp256k1").                |
| `signatureType`        | string (from signatures)           | Yes      | The type of signature (e.g., "ecdsa", "ed25519").                                  |
| `hexBytes`             | string (from signatures)           | Yes      | Hex-encoded signature.                                                             |

## Returns

| Field               | Type   | Description                                                                 |
| ------------------- | ------ | --------------------------------------------------------------------------- |
| `signedTransaction` | string | A string that represents the fully signed transaction ready for submission. |

## Example Result

```json
{
  "signedTransaction": "0x..."
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/combine' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "mainnet"
    },
    "unsignedTransaction": "YOUR_UNSIGNED_TRANSACTION",
    "signatures": [
      {
        "signing_payload": {
            "hex_bytes": "HEX_ENCODED_PAYLOAD_BYTES"
        },
        "publicKey": {
            "hexBytes": "PUBLIC_KEY_HEX",
            "curveType": "secp256k1"
        },
        "signatureType": "ecdsa",
        "hexBytes": "SIGNATURE_HEX"
      }
    ]
}'
```
```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Cosmos
const cosmos = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

// Define the input parameters with only required fields
const params = {
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
  unsignedTransaction: "YOUR_UNSIGNED_TRANSACTION",
  signatures: [
    {
      signing_payload: {
        hexBytes: "PAYLOAD_HEX", // Hex-encoded payload bytes.
      },
      publicKeys: [
        {
          hexBytes: "PUBLIC_KEY_HEX", // Hexadecimal representation of the public key.
          curveType: "secp256k1", // Curve type (secp256k1, secp256k1_bip340, secp256r1, edwards25519, tweedle, pallas).
        },
      ],
      signatureType: "ecdsa", // Signature type (ecdsa, ecdsa_recovery, ed25519, schnorr_1, schnorr_bip340, schnorr_poseidon).
      hexBytes: "SIGNATURE_HEX", // Hex-encoded signature.
    },
  ],
};

// Create network transaction from signatures
const networkTransaction = await tatum.rpc.createNetworkTransaction(params);

// Log the network transaction
console.log("Network Transaction:", networkTransaction);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```
