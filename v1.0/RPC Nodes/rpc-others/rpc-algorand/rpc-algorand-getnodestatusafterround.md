---
title: "getNodeStatusAfterRound"
slug: "rpc-algorand-getnodestatusafterround"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:07 GMT+0000 (Coordinated Universal Time)"
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

// Define the input parameters in a single object
const params = {
    round: 10000 // Specify the round to wait until returning status.
};

// Wait for a block to appear after the specified round and return the node's status at the time
const nodeStatus = await tatum.rpc.getNodeStatusAfterRound(params);

// Log the node status
console.log('Algorand Node Status:', nodeStatus);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getNodeStatusAfterRound` method allows you to wait for a block to appear after a specified round and returns the node's status at that time. 

### Example Use Cases

1. **Wait for Block**: Developers can use this method to wait for a specific round and retrieve the node's status when a block appears after that round.

### Request Parameters

The `getNodeStatusAfterRound` method requires the following parameter:

- `round` (integer, required): The round to wait until returning status.

### Return Object

The method returns an object representing the node's status at the time a block appears after the specified round. The object includes various properties that provide information about the node's status, such as catchpoints, catchup progress, last round seen, consensus version, and voting information.

Please note that the structure of the returned object may change in different Algorand RPC versions.
