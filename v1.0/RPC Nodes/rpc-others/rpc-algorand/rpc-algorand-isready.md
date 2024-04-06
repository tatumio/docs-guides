---
title: "isReady"
slug: "rpc-algorand-isready"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 05 2024 16:02:40 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, AlgorandAlgod, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Algorand
const tatum = await TatumSDK.init<AlgorandAlgod>({ network: Network.ALGORAND_ALGOD });

// Retrieve the health status of the Algorand node
const readyStatus = await tatum.rpc.isReady();

// Log the health status
console.log('Algorand Node Ready:', readyStatus);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `isReady` method allows you to check the health status of the Algorand node and confirm if it is fully caught up.

### Example Use Cases

1. **Node Health Check**: Developers can use this method to check if the Algorand node is healthy and fully caught up, ensuring that it is ready to process requests.

### Request Parameters

The `isReady` method does not require any parameters.

### Return Object

The method returns a response indicating the health status of the Algorand node.

Please note that the structure of the returned object may change in different Algorand RPC versions.
