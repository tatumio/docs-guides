---
title: "getblocks"
slug: "rpc-solana-getblocks"
excerpt: "Solana RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]


### How to Use It

{% code overflow="wrap" lineNumbers="true" %}
```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getBlocks(5,10)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getBlocks` method returns a list of confirmed blocks between two specified slots. This can be useful when needing to examine a specific range of blocks for transaction analysis, data verification, or other blockchain analysis tasks.

### Parameters

* `endSlot` (number, required): This is the upper limit of the slot range from which blocks are to be returned.
* `startSlot` (number, optional): This is the lower limit of the slot range. If not provided, the method will return blocks from the start of the blockchain to the `endSlot`. Note that `startSlot` must be no more than 500,000 blocks lower than the `end_slot`.
* `options` (object, optional): This object can contain the following fields:
  * `commitment`(string, optional): Specifies the level of commitment to apply when fetching data.
    * Values: `finalized` `confirmed` Note that `processed` is not supported.

### Return Object

The method returns an array of integers, each representing a confirmed block between `startSlot` and either `endSlot` (if provided) or the latest confirmed block, inclusive. The maximum range allowed is 500,000 slots.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getBlocks",
  "params": [5, 10]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": [5, 6, 7, 8, 9, 10],
  "id": 1
}
```
