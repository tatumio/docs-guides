---
title: "getAccount"
slug: "rpc-algorand-getaccount"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 05 2024 15:56:15 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


\\n

### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, AlgorandIndexer, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Algorand
const tatum = await TatumSDK.init<AlgorandIndexer>({ network: Network.ALGORAND_INDEXER });

// Define the input parameters as an object
const accountAddress = { address: 'ALGORAND_ACCOUNT_ADDRESS' }; // Replace with the Algorand account address you want to retrieve information for.

// Retrieve account information using the Algorand Indexer
const accountInfo = await tatum.rpc.getAccount(accountAddress);

// Log the account information
console.log('Algorand Account Information:', accountInfo);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccount` method allows you to retrieve detailed information about a specific Algorand account based on its account address.

### Example Use Cases

1. **Account Balance**: Developers can use this method to check the balance of a specific Algorand account by providing its address.

2. **Account Details**: Retrieve various details of an Algorand account, including its transactions, assets, and more, for further analysis.

### Request Parameters

The `getAccount` method requires the following parameter:

- `account-address` (string, required): The Algorand account address for which you want to retrieve account information.

### Return Object

The method returns an object representing the detailed information of the specified Algorand account, including various parameters. 

Please note that the structure of the returned object may change in different Algorand RPC versions.
