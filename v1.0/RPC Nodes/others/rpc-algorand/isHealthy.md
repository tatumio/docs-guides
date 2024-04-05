---
title: "isHealthy"
slug: "rpc-algorand-isHealthy"
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

// Retrieve health check status for the Algorand node
const isHealthy = await tatum.rpc.isHealthy();

// Log the health check status
console.log('Algorand Health Check:', isHealthy);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `isHealthy` method allows you to check the health of the Algorand node.

### Example Use Cases

1. **Health Monitoring**: Developers can use this method to regularly monitor the health status of the Algorand node and ensure that it is functioning properly.

### Request Parameters

The `isHealthy` method does not require any parameters.

### Return Object

The method returns an empty object with a response code indicating the health status of the Algorand node.
