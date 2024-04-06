---
title: "numUnconfirmedTxs"
slug: "rpc-bnb-beacon-numunconfirmedtxs"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

```typescript
// Importing Tatum SDK for BNB Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for BNB Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Retrieve the number of unconfirmed transactions
const numUnconfirmedTxs = await tatum.rpc.numUnconfirmedTxs();
console.log(numUnconfirmedTxs);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `numUnconfirmedTxs` method is used to retrieve the number of unconfirmed transactions in the BNB Beacon Chain.

### Parameters

This method does not require any parameters.

### Return Object

The method returns a Promise that resolves to a JSON-RPC response containing the following fields:

- `n_txs` (string): The number of unconfirmed transactions. Example: `0`
- `total` (string): The total value associated with unconfirmed transactions. Example: `0`
- `total_bytes` (string): The total size in bytes of unconfirmed transactions. Example: `0`

(Note: The exact fields in the return object might vary based on the BNB Beacon Chain's implementation and version.)
