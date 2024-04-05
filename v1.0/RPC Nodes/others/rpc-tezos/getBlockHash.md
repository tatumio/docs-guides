---
title: "getBlockHash"
slug: "rpc-tezos-getBlockHash"
excerpt: "Tezos RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Tezos, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Tezos
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Define the chain ID and block ID (Replace placeholders with actual values)
const params = { 
    chainId: 'YOUR_CHAIN_ID',           // Specify the chain ID (Network identifier)
    blockId: 'YOUR_BLOCK_ID',           // Optional: Specify the block ID (hash)
};

// Fetch the hash of a specific block by its ID
const blockHash = await tatum.rpc.getBlockHash(params);

// Log the block hash
console.log('Block Hash:', blockHash);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getBlockHash` method allows you to retrieve the hash of a specific block within a Tezos chain. By providing the chain ID and block ID as parameters, you can access the unique hash associated with the chosen block.

### Example use cases:

1. **Block Identification:**
   Developers and applications can use this method to identify and reference a specific block on the Tezos blockchain using its hash.

2. **Transaction Verification:**
   When verifying transactions or interactions with smart contracts, you may need the block hash as part of the verification process.

3. **Historical Data Retrieval:**
   Researchers and analysts can retrieve block hashes for historical data analysis and record-keeping.

### Request Parameters

The `getBlockHash` method requires the following parameters:

- `chainId` (string, required): 
  The identifier of the Tezos chain from which to retrieve the block hash.

- `block` (string, required): 
  The unique identifier (hash) of the block for which you want to retrieve the hash.

### Return Object

The `getBlockHash` method returns a string representing the hash of the requested block.

(Note: The exact fields in the return object might vary based on the Tezos blockchain's implementation and version.)