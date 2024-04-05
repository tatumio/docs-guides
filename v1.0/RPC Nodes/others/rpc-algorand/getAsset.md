---
title: "getAsset"
slug: "rpc-algorand-getAsset"
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
import { TatumSDK, AlgorandIndexer, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK
const tatum = await TatumSDK.init<AlgorandIndexer>({ network: Network.ALGORAND_INDEXER });

// Define the input parameters as a dictionary object
const params = {
    assetId: 123,               // Specify the asset ID (number) for which you want to lookup asset information.
    includeAll: true            // Optional: Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application localstates (boolean).
};

// Lookup asset information
const assetInfo = await tatum.rpc.getAsset(params);

// Log the asset information
console.log('Asset Information:', assetInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAsset` method allows you to lookup information for a specific asset.

### Example Use Cases

1. **Asset Lookup**: Developers can use this method to retrieve detailed information about a specific asset.

### Request Parameters

The `getAsset` method requires the following parameters, all included in the `params` dictionary object:

- `assetId` (number, required): Specify the asset ID for which you want to lookup asset information.
- `includeAll` (boolean, optional): Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application localstates (boolean).

### Return Object

The method returns an object representing the detailed information of the specified asset, including its properties. 

Please note that the structure of the returned object may change in different RPC versions.