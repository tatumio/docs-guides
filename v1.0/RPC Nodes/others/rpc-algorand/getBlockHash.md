---
title: "getBlockHash"
slug: "rpc-algorand-getBlockHash"
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
    round: 12345,  // Specify the round from which you want to fetch block hash information (integer).
};

// Get the block hash for the specified round
const blockHash = await tatum.rpc.getBlockHash(params);

// Log the block hash
console.log('Block Hash:', blockHash);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getBlockHash` method allows you to fetch the block hash information for a specific block on the Algorand blockchain.

### Example Use Cases

1. **Retrieve Block Hash**: Developers can use this method to fetch the block hash for a specific block on the Algorand blockchain.

### Request Parameters

The `getBlockHash` method requires the following parameter:

- `round` (integer, required): Specify the round from which you want to fetch block hash information.

### Return Object

The method returns an object representing the block hash of the specified round on the Algorand blockchain.

Please note that the structure of the returned object may change in different Algorand RPC versions.