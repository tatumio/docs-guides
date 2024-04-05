---
title: "getTransaction"
slug: "rpc-algorand-getTransaction"
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
import { TatumSDK, AlgorandIndexer, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK
const tatum = await TatumSDK.init<AlgorandIndexer>({ network: Network.ALGORAND_INDEXER });

// Define the input parameters as a dictionary object
const txId = { txId : 'TRANSACTION_ID'}; // Specify the transaction ID you want to lookup (string).

// Lookup a single transaction by its ID
const transaction = await tatum.rpc.getTransactionById(txId);

// Log the transaction information
console.log('Transaction Information:', transaction);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getTransactionById` method allows you to lookup a single transaction by its unique transaction ID.

### Request Parameters

The method requires the following parameter:

- `txId` (string, required): Specify the transaction ID you want to lookup.

### Return Object

The method returns information about the specified transaction, including details such as the transaction's ID, sender address, receiver address, transaction type, amount, and more.

Please note that the structure of the returned object may change in different RPC versions.