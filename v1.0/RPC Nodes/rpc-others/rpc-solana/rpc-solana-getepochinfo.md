---
title: "getepochinfo"
slug: "rpc-solana-getepochinfo"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:44 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getEpochInfo()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getEpochInfo` method returns information about the current epoch on the Solana network. This includes the current slot, block height, epoch number, slot index, the number of slots in this epoch, and the total number of transactions processed without error since genesis. This data can be essential for developers and operators of Solana nodes to understand the current state of the network and to track its progress over time.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/JjezRzL",
  "href": "https://codepen.io/tatum-devrel/pen/JjezRzL",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `options` (object, optional): A configuration object containing:
  - `commitment`(string, optional): Specifies the level of commitment to apply when fetching data.
  - `minContextSlot` (number, optional): The minimum slot that the request can be evaluated at.

### Return Object

The result field will be an object with the following fields:

- `absoluteSlot`: The current slot.
- `blockHeight`: The current block height.
- `epoch`: The current epoch.
- `slotIndex`: The current slot relative to the start of the current epoch.
- `slotsInEpoch`: The number of slots in this epoch.
- `transactionCount`: Total number of transactions processed without error since genesis.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id":1, 
  "method":"getEpochInfo"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "absoluteSlot": 166598,
    "blockHeight": 166500,
    "epoch": 27,
    "slotIndex": 2790,
    "slotsInEpoch": 8192,
    "transactionCount": 22661093
  },
  "id": 1
}
```
