---
title: "getAssetInformation"
slug: "rpc-algorand-getAssetInformation"
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
    assetId: 123,  // Specify the asset ID for which you want to retrieve information.
};

// Retrieve the asset information for the specified asset ID
const assetInfo = await tatum.rpc.getAssetInformation(params);

// Log the asset information
console.log('Asset Information:', assetInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAssetInformation` method allows you to retrieve asset information, including creator, name, total supply, and special addresses, for a specific asset ID.

### Example Use Cases

1. **Asset Details**: Developers can use this method to retrieve detailed information about a specific asset, including the address of the asset's creator, the name of the asset, the total supply of the asset, and any special addresses associated with the asset.

### Request Parameters

The `getAssetInformation` method requires the following parameter:

- `assetId` (integer, required): An asset identifier representing the asset for which you want to retrieve information.

### Return Object

The method returns an object representing the asset information for the specified asset ID. The returned object includes details such as the asset's creator, name, total supply, and special addresses.

Please note that the structure of the returned object may change in different Algorand RPC versions.