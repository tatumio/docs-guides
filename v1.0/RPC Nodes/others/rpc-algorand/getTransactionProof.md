---
title: "getTransactionProof"
slug: "rpc-algorand-getTransactionProof"
excerpt: "Algorand RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, AlgorandAlgod, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Algorand
const tatum = await TatumSDK.init<AlgorandAlgod>({ network: Network.ALGORAND_ALGOD });

// Define the input parameters in a single object
const params = {
    round: ROUND_NUMBER,                   // Specify the round in which the transaction appears.
    txid: 'TRANSACTION_ID',                // Specify the transaction ID for which to generate a proof.
    format: 'json',                        // Optional: Configures whether the response object is JSON or MessagePack encoded. If not provided, defaults to JSON.
    hashtype: 'sha512_256'                  // Optional: The type of hash function used to create the proof, must be one of: sha512_256 or sha256.
};

// Generate a proof for a transaction in a block
const transactionProof = await tatum.rpc.getTransactionProof(params);

// Log the transaction proof
console.log('Transaction Proof:', transactionProof);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getTransactionProof` method allows you to get a proof for a transaction in a block.

### Example Use Cases

1. **Transaction Verification**: Developers can use this method to get a proof for a transaction in a block in order to verify the authenticity and integrity of the transaction.

### Request Parameters

The `getTransactionProof` method requires the following parameters:

- `round` (integer, required): Specify the round in which the transaction appears.
- `txid` (string, required): Specify the transaction ID for which to generate a proof.
- `hashtype` (enum: sha512_256, sha256, optional): The type of hash function used to create the proof, must be one of: sha512_256 or sha256.
- `format` (enum: json, msgpack, optional): Configures whether the response object is JSON or MessagePack encoded. If not provided, defaults to JSON.

### Return Object

The method returns an object representing the proof of the specified transaction in a block. The object includes the following properties:

- `hashtype` (string): The type of hash function used to create the proof, must be one of: sha512_256 or sha256.
- `idx` (integer): Index of the transaction in the block's payset.
- `proof` (string): Proof of transaction membership.
- `stibhash` (string): Hash of SignedTxnInBlock for verifying the proof.
- `treedepth` (integer): Represents the depth of the tree that is being proven, i.e. the number of edges from a leaf to the root.

Please note that the structure of the returned object may change in different Algorand RPC versions.