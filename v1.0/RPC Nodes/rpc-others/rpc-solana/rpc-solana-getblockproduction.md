---
title: "getblockproduction"
slug: "rpc-solana-getblockproduction"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getBlockProduction()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getBlockProduction` method provides information about the recent block production from the current or previous epoch. This can be used to monitor the performance and activity of validators on the Solana network.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/QWJoKde?editors=1011",
  "href": "https://codepen.io/tatum-devrel/pen/QWJoKde?editors=1011",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `options` (object, optional): This object can contain the following fields:
  - `commitment`(string, optional): Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`
  - `identity` (string, optional): Only return results for this validator identity (base-58 encoded).
  - `range` (object, optional): Slot range to return block production for.
    - `firstSlot` (number): First slot to return block production information for (inclusive).
    - `lastSlot` (number, optional): Last slot to return block production information for (inclusive).

### Return Object

The result will be a JSON object with value equal to object with the following fields:

- `byIdentity` (object): A dictionary of validator identities, as base-58 encoded strings. The value is a two-element array containing the number of leader slots and the number of blocks produced.
- `range` (object): Block production slot range with fields `firstSlot` and `lastSlot` indicating the first and last slot of block production information respectively.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0", 
  "id": 1,
  "method": "getBlockProduction"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "context": {
      "slot": 9887
    },
    "value": {
      "byIdentity": {
        "85iYT5RuzRTDgjyRa3cP8SYhM2j21fj7NhfJ3peu1DPr": [9888, 9886]
      },
      "range": {
        "firstSlot": 0,
        "lastSlot": 9887
      }
    }
  },
  "id": 1
}
```
