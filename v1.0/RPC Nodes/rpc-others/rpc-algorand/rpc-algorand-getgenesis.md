---
title: "getGenesis"
slug: "rpc-algorand-getgenesis"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:43 GMT+0000 (Coordinated Universal Time)"
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

// Retrieve the genesis information
const genesisInfo = await tatum.rpc.getGenesis();

// Log the genesis information
console.log('Algorand Genesis:', genesisInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getGenesis` method allows you to retrieve the entire genesis file in JSON format.

### Example Use Cases

1. **Genesis Information**: Developers can use this method to retrieve the genesis information of the Algorand network, including details about the network configuration.

### Request Parameters

The `getGenesis` method does not require any parameters.

### Return Object

The method returns a string representing the entire genesis file in JSON format.

Please note that the structure of the returned object may change in different Algorand RPC versions.
