---
title: "getPendingTransactions"
slug: "rpc-algorand-getpendingtransactions"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
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
    max: 10,          // Optional: Truncated number of transactions to display. If max=0, returns all pending txns (number).
    format: 'json',   // Optional: Configures whether the response object is JSON or MessagePack encoded (enum: json, msgpack).
};

// Retrieve the list of pending transactions
const pendingTransactions = await tatum.rpc.getPendingTransactions(params);

// Log the pending transactions
console.log('Pending Transactions:', pendingTransactions);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getPendingTransactions` method allows you to retrieve the list of unconfirmed transactions currently in the transaction pool.

### Example Use Cases

1. **Monitor Pending Transactions**: Developers can use this method to monitor and retrieve information about pending transactions in the transaction pool.

### Request Parameters

The `getPendingTransactions` method requires the following parameters:

- `max` (number, optional): Truncated number of transactions to display. If max = 0, returns all pending transactions.
- `format` (enum: json, msgpack, optional): Configures whether the response object is JSON or MessagePack encoded. If not provided, defaults to JSON.

### Return Object

The method returns a potentially truncated list of transactions currently in the node's transaction pool. This includes an array of signed transaction objects as they were submitted, along with the total number of transactions in the pool. 

You can compute whether or not the list is truncated if the number of elements in the `top-transactions` array is fewer than `total-transactions`. 

Please note that the structure of the returned object may vary depending on the Algorand RPC version.
