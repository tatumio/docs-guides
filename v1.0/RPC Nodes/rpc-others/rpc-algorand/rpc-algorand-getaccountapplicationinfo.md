---
title: "getAccountApplicationInfo"
slug: "rpc-algorand-getaccountapplicationinfo"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
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
    address: 'ALGORAND_PUBLIC_KEY', // Specify the Algorand account public key.
    applicationId: 12345,           // Specify the application identifier.
    format: 'json'                  // Optional: Configures whether the response object is JSON or MessagePack encoded (enum: json, msgpack).
};

// Retrieve account application information for the Algorand account
const accountApplicationInfo = await tatum.rpc.getAccountApplicationInfo(params);

// Log the account application information
console.log('Algorand Account Application Information:', accountApplicationInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountApplicationInfo` method allows you to retrieve the account's application local state and global state for a specific Algorand account and application ID.

### Example Use Cases

1. **Retrieve Application State**: Developers can use this method to retrieve the application state (local and global) for a specific Algorand account.

### Request Parameters

The `getAccountApplicationInfo` method requires the following parameters:

- `address` (string, required): An Algorand account public key.
- `applicationId` (number, required): An application identifier.
- `format` (enum: json, msgpack, optional): Configures whether the response object is JSON or MessagePack encoded.

### Return Object

The method returns an object representing the account's application local state and global state (if exists) for the specified Algorand account and application ID. 

Please note that the structure of the returned object may change in different Algorand RPC versions.
