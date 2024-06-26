---
title: "getAccountAssets"
slug: "rpc-algorand-getaccountassets"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:36 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
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
    accountId: 'ALGORAND_ACCOUNT_ID', // Specify the Algorand account ID for which you want to retrieve asset holdings.
    assetId: 123,                     // Optional: Specify the asset ID (number) for filtering.
    includeAll: true,                 // Optional: Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application local states (boolean).
    limit: 100,                       // Optional: Maximum number of results to return (number).
    next: 'NEXT_PAGE_TOKEN'           // Optional: The next page of results. Use the next token provided by the previous results (string).
};

// Retrieve asset holdings for the Algorand account
const accountAssets = await tatum.rpc.getAccountAssets(params);

// Log the asset holdings information
console.log('Algorand Account Asset Holdings:', accountAssets);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountAssets` method allows you to retrieve the asset holdings of a specific Algorand account.

### Example Use Cases

1. **Asset Holdings**: Developers can use this method to retrieve the asset holdings of an Algorand account, including information about specific assets held by the account.

### Request Parameters

The `getAccountAssets` method requires the following parameters:

- `accountId` (string, required): Specify the Algorand account ID for which you want to retrieve asset holdings.
- `assetId` (number, optional): Specify the asset ID for filtering the results.
- `includeAll` (boolean, optional): Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application local states.
- `limit` (number, optional): Maximum number of results to return.
- `next` (string, optional): The next page of results. Use the next token provided by the previous results.

### Return Object

The method returns an object representing the asset holdings of the specified Algorand account, including information about specific assets and their quantities. 

Please note that the structure of the returned object may change in different Algorand RPC versions.
