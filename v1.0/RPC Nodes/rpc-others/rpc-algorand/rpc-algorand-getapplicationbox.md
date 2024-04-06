---
title: "getApplicationBox"
slug: "rpc-algorand-getapplicationbox"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
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
    applicationId: 123,     // Specify the application ID (number) for which you want to get the box information.
    name: 'int:1234'        // Specify the box name in goal-arg form (string).
};

// Get the box information for the Algorand application
const boxInfo = await tatum.rpc.getApplicationBox(params);

// Log the box information
console.log('Algorand Application Box Information:', boxInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getApplicationBox` method allows you to get box information for a given Algorand application.

### Example Use Cases

1. **Box Information**: Developers can use this method to retrieve base64 encoded box name and value for a specific box within an Algorand application.

### Request Parameters

The `getApplicationBox` method requires the following parameters:

- `applicationId` (number, required): Specify the application ID for which you want to get the box information.
- `name` (string, required): Specify the box name in goal-arg form, such as 'int:1234', 'b64:A==', 'str:hello', or 'addr:XYZ...'.

### Return Object

The method returns an object representing the base64 encoded box name and value for the specified box within the Algorand application. 

Please note that the structure of the returned object may change in different Algorand RPC versions.
