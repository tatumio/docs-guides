---
title: "getblocktime"
slug: "rpc-solana-getblocktime"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

{% code overflow="wrap" lineNumbers="true" %}

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getBlockTime(5)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `getBlockTime` method returns the estimated production time of a block. Each validator in the Solana network reports their UTC time to the ledger at regular intervals by intermittently adding a timestamp to a vote for a specific block. A requested block's time is then calculated from the stake-weighted mean of these vote timestamps recorded on the ledger in a set of recent blocks.

This method is useful in understanding when a particular block was produced, which is essential for various analysis and audit purposes.

{% embed url="<https://codepen.io/tatum-devrel/pen/bGQZwRy?editors=1111"> %}

### Parameters

- `blockNumber` (number, required): This is the number of the block for which you want to retrieve the production time. The block number is identified by its slot.

### Return Object

The method returns an integer or null:

- If the production time of the block is available, the method returns the estimated production time as a Unix timestamp (seconds since the Unix epoch).
- If the production time of the block is not available, the method returns null.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0", "id":1,
  "method": "getBlockTime",
  "params":[5]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 1574721591,
  "id": 1
}
```
