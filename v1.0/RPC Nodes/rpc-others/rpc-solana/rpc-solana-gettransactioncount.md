---
title: "gettransactioncount"
slug: "rpc-solana-gettransactioncount"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getTransactionCount()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getTransactionCount` method retrieves the current transaction count from the ledger. This can be used to track the number of transactions processed by the network.

{% embed url="<https://codepen.io/tatum-devrel/pen/jOQJroJ?editors=1111"> %}

### Parameters

- `options` (object, optional): Configuration object containing the following fields:
  - `commitment` (string, optional): Specifies the confirmation level of data to be fetched.
    - Values: `finalized` `confirmed` `processed`
  - `minContextSlot`: (number, optional) The minimum slot that the request can be evaluated at.
    - Example: `5`

### Return Object

The method returns a number indicating the current transaction count from the ledger.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getTransactionCount",
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 268,
  "id": 1
}
```
