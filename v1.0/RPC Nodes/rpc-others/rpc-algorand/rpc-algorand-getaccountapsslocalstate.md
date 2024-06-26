---
title: "getAccountApssLocalState"
slug: "rpc-algorand-getaccountapsslocalstate"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
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

// Define optional query parameters
const params = {
    accountId: 'ALGORAND_ACCOUNT_ID', // Replace with the Algorand account ID for which you want to retrieve local application state.
    applicationId: 123,       // Optional: Specify the application ID (number) for filtering.
    includeAll: true,        // Optional: Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application local states (boolean).
    limit: 100,              // Optional: Maximum number of results to return (number).
    next: 'NEXT_PAGE_TOKEN'  // Optional: The next page of results. Use the next token provided by the previous results (string).
};

// Retrieve local application state for the Algorand account
const appsLocalState = await tatum.rpc.getAccountAppsLocalState(params);

// Log the local application state information
console.log('Algorand Account Local Application State:', appsLocalState);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountAppsLocalState` method allows you to retrieve the local application state of a specific Algorand account.

### Example Use Cases

1. **Application State**: Developers can use this method to retrieve the local application state of an Algorand account, including information about its asset holdings and applications.

### Request Parameters

The `getAccountAppsLocalState` method requires the following parameters:

- `account-id` (string, required): The Algorand account ID for which you want to retrieve local application state.
- `application-id` (number, optional): Specify the application ID for filtering the results.
- `include-all` (boolean, optional): Include all items, including closed accounts, deleted applications, destroyed assets, opted-out asset holdings, and closed-out application local states.
- `limit` (number, optional): Maximum number of results to return.
- `next` (string, optional): The next page of results. Use the next token provided by the previous results.

### Return Object

The method returns an object representing the local application state of the specified Algorand account, including information about asset holdings and applications. 

Please note that the structure of the returned object may change in different Algorand RPC versions.
