---
title: "getAccountInfo"
slug: "rpc-algorand-getaccountinfo"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:00 GMT+0000 (Coordinated Universal Time)"
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
    address: 'ALGORAND_ADDRESS', // Specify the Algorand public key for which you want to retrieve account information.
    format: 'json',              // Optional: Configures whether the response object is JSON or MessagePack encoded (enum: json, msgpack).
    exclude: 'none'              // Optional: When set to 'all' will exclude asset holdings, application local state, created asset parameters, any created application parameters. Defaults to 'none' (enum: all, none).
};

// Retrieve account information for the Algorand account
const accountInfo = await tatum.rpc.getAccountInformation(params);

// Log the account information
console.log('Algorand Account Information:', accountInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountInformation` method allows you to retrieve the status, balance, and spendable amounts of a specific Algorand account.

### Example Use Cases

1. **Account Balance**: Developers can use this method to retrieve the balance and spendable amounts of an Algorand account.
2. **Account Status**: Users can check the status of their Algorand account, including the account public key and other related information.

### Request Parameters

The `getAccountInformation` method requires the following parameters:

- `address` (string, required): Specify the Algorand public key for which you want to retrieve account information.
- `format` (enum: json, msgpack, optional): Configures whether the response object is JSON or MessagePack encoded. If not provided, defaults to JSON.
- `exclude` (enum: all, none, optional): When set to 'all', it will exclude asset holdings, application local state, created asset parameters, and any created application parameters. Defaults to 'none'.

### Return Object

The method returns an object representing the account information of the specified Algorand account, including the account status, balance, and spendable amounts.

Please note that the structure of the returned object may change in different Algorand RPC versions.
