---
title: "getAccountAssetInfo"
slug: "rpc-algorand-getaccountassetinfo"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
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
    address: 'ALGORAND_ACCOUNT_ADDRESS',  // Specify the Algorand account address for which you want to retrieve asset information.
    assetId: 123,                         // Specify the asset ID for which you want to retrieve information.
    format: 'json'                        // Optional: Configures whether the response object is JSON or MessagePack encoded. Defaults to JSON.
};

// Retrieve asset information for the Algorand account
const assetInformation = await tatum.rpc.getAccountAssetInformation(params);

// Log the asset information
console.log('Algorand Account Asset Information:', assetInformation);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountAssetInformation` method allows you to retrieve asset holding and asset parameters (if applicable) for a specific asset ID and account address.

### Example Use Cases

1. **Asset Holdings**: Developers can use this method to retrieve the asset holdings of a specific Algorand account, including information about the asset and its parameters.

### Request Parameters

The `getAccountAssetInformation` method requires the following parameters:

- `address` (string, required): Specify the Algorand account address for which you want to retrieve asset information.
- `assetId` (number, required): Specify the asset ID for which you want to retrieve information.
- `format` (enum: json, msgpack, optional): Configures whether the response object is JSON or MessagePack encoded. Defaults to JSON.

### Return Object

The method returns an object representing the asset holding and asset parameters (if applicable) for the specified asset ID and account address.

Please note that the structure of the returned object may change in different Algorand RPC versions.
