---
title: "getApplicationBoxes"
slug: "rpc-algorand-getapplicationboxes"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:44 GMT+0000 (Coordinated Universal Time)"
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
    applicationId: 123,  // Specify the application ID (number) for which you want to get box names.
    limit: 100,          // Optional: Maximum number of results to return (number).
    next: 'NEXT_TOKEN'   // Optional: The next page of results. Use the next token provided by the previous results (string).
};

// Get the box names for the Algorand application
const boxNames = await tatum.rpc.getApplicationBoxes(params);

// Log the box names
console.log('Algorand Application Box Names:', boxNames);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getApplicationBoxes` method allows you to get box names for a given Algorand application.

### Example Use Cases

1. **Box Names**: Developers can use this method to retrieve the box names of an Algorand application sorted lexicographically.

### Request Parameters

The `getApplicationBoxes` method requires the following parameters:

- `applicationId` (number, required): Specify the application ID for which you want to get box names.
- `limit` (number, optional): Maximum number of results to return.
- `next` (string, optional): The next page of results. Use the next token provided by the previous results.

### Return Object

The method returns an array of box names for the specified Algorand application, sorted lexicographically. 

Please note that the structure of the returned object may change in different Algorand RPC versions.
