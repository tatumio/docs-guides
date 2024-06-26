---
title: "getNodeStatus"
slug: "rpc-algorand-getnodestatus"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
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

// Retrieve the current node status
const nodeStatus = await tatum.rpc.getNodeStatus();

// Log the node status
console.log('Algorand Node Status:', nodeStatus);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getNodeStatus` method allows you to retrieve the current status of an Algorand node.

### Example Use Cases

1. **Check Node Status**: Developers can use this method to check the status of an Algorand node and get information about the node's catchup progress, last round seen, consensus version details, and more.

### Request Parameters

The `getNodeStatus` method does not require any parameters.

### Return Object

The method returns an object representing the current status of the Algorand node. The object contains information about the node's catchup progress, last round seen, consensus version details, and more. 

Please note that the structure of the returned object may change in different Algorand RPC versions.

```

 
```
