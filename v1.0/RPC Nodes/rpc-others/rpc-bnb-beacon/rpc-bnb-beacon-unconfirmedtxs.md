---
title: "unconfirmedTxs"
slug: "rpc-bnb-beacon-unconfirmedtxs"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:37 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

```typescript
// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Define the limit for unconfirmed transactions
const limit = { limit : '10' }; 

// Retrieve unconfirmed transactions
const unconfirmedTxs = await tatum.rpc.unconfirmedTxs(limit);
console.log(unconfirmedTxs);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `unconfirmedTxs` method is used to retrieve unconfirmed transactions from the BNB Beacon Chain.

### Parameters

- `limit` (string, optional): The maximum number of unconfirmed transactions to retrieve.

### Return Object (Required)

- `n_txs` (number): The number of unconfirmed transactions.
- `total` (number): The total value associated with unconfirmed transactions.
- `total_bytes` (number): The total size in bytes of unconfirmed transactions.
- `txs` (array): An array of unconfirmed transaction objects.

(Note: The exact structure of the transaction objects and response may vary based on the BNB beacon chain's implementation and version.)
