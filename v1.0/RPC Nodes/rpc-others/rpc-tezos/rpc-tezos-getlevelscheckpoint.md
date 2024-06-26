---
title: "getLevelsCheckpoint"
slug: "rpc-tezos-getlevelscheckpoint"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Tezos, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Tezos
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Fetch the checkpoint for a specific Tezos chain using the deprecated getLevelsCheckpoint method
const checkpoint = await tatum.rpc.getLevelsCheckpoint({
  chainId: 'main'  // Specify the Tezos chain ID (usually 'main' for mainnet)
});

console.log(`The checkpoint for the chain is:`, checkpoint);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

**DEPRECATED**: This method is deprecated. It is recommended to use `../levels/{checkpoint, savepoint, caboose, history_mode}` instead. The `getLevelsCheckpoint` method provides information about the current checkpoint for a specified chain in Tezos.

### Example use cases:

1. **Legacy System Support:**  
   While this method is deprecated, it may still be relevant for legacy systems or applications that have not transitioned to newer endpoints.
2. **Checkpoint Retrieval:**  
   Checkpoints are crucial for validating the blockchain's integrity. The method allows for quick retrieval of the current checkpoint for audit or validation purposes.

### Request Parameters

The `getLevelsCheckpoint` method requires:

- `chainId` (string, required):  
  The identifier of the Tezos chain from which the checkpoint information is being requested.

### Return Object

The `getLevelsCheckpoint` method returns an object containing details about the current checkpoint for the specified chain.
