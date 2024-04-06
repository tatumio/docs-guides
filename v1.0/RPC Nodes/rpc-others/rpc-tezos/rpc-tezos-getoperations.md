---
title: "getOperations"
slug: "rpc-tezos-getoperations"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Importing Tatum SDK for Tezos blockchain
import { TatumSDK, Network, Tezos } from '@tatumio/tatum';

// Initializing SDK for Tezos blockchain
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Define parameters for the query
const params = {
  chainId: 'YOUR_CHAIN_ID',
  blockId: 'YOUR_BLOCK_ID'
};

// Fetching the operations
const operations = await tatum.rpc.getOperations(params);
console.log(operations);

// Cleaning up resources used by Tatum SDK
await tatum.destroy();
```

### Overview

The `getOperations` method is used to retrieve a list of operations included in a specific block on the Tezos blockchain.

### Request Parameters

- `chainId` (string, required): The ID of the chain.
- `blockId` (string, required): The unique identifier (hash) of the block.

### Return Object

The method returns an array of operations from the specified block on the Tezos blockchain. Each operation is an object containing details about the operation.

(Note: The exact fields in the return object might vary based on the Tezos blockchain's implementation and version.)
