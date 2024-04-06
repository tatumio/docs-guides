---
title: "getAssets"
slug: "rpc-algorand-getassets"
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
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, AlgorandIndexer, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Algorand
const tatum = await TatumSDK.init<AlgorandIndexer>({ network: Network.ALGORAND_INDEXER });

// Define the input parameters in a single object
const params = {
    assetId: 123,                    // Optional: Asset ID (number).
    creator: 'CREATOR_ADDRESS',     // Optional: Filter assets with the given creator address (string).
    includeAll: true,               // Optional: Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application localstates (boolean).
    limit: 100,                     // Optional: Maximum number of results to return (number).
    name: 'ASSET_NAME',             // Optional: Filter assets with the given name (string).
    next: 'NEXT_PAGE_TOKEN',         // Optional: The next page of results. Use the next token provided by the previous results (string).
    unit: 'ASSET_UNIT'              // Optional: Filter assets with the given unit (string).
};

// Search for assets using the Algorand Indexer
const assets = await tatum.rpc.getAssets(params);

// Log the asset information
console.log('Algorand Assets:', assets);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAssets` method allows you to search for assets in the Algorand blockchain.

### Example Use Cases

1. **Asset Search**: Developers can use this method to search for assets with specific criteria, such as asset ID, creator address, name, or unit.

### Request Parameters

The `getAssets` method requires the following parameters:

- `assetId` (number, optional): Asset ID to filter assets by (number).
- `creator` (string, optional): Filter assets with the given creator address (string).
- `includeAll` (boolean, optional): Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application localstates (boolean).
- `limit` (number, optional): Maximum number of results to return (number).
- `name` (string, optional): Filter assets with the given name (string).
- `next` (string, optional): The next page of results. Use the next token provided by the previous results (string).
- `unit` (string, optional): Filter assets with the given unit (string).

### Return Object

The method returns an array of asset information that matches the specified criteria.

Please note that the structure of the returned object may change in different Algorand RPC versions.
