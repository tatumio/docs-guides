---
title: "getblockheight"
slug: "rpc-solana-getblockheight"
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



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getBlockHeight()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getBlockHeight` method returns the current block height of the node. Block height refers to the number of blocks preceding the current one in the blockchain.

This method is beneficial for understanding the current status of the blockchain, as it provides the most recent block number processed by the node. It can be used for monitoring the progress of the blockchain, troubleshooting node synchronisation issues, and determining the confirmation status of a transaction by comparing its block number with the current block height.

{% embed url="<https://codepen.io/tatum-devrel/pen/ZEmPppb?editors=1111"> %}

### Parameters

`options` (object, optional): This object can contain the following fields:

- `commitment`(string, optional): Specifies the level of commitment to apply when fetching data.
  - Values: `finalized` `confirmed` `processed`
- `minContextSlot` (number, optional): This field can be used to specify the minimum slot that the request can be evaluated at.

### Return Object

The method returns a single number, representing the current block height.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id":1,
  "method":"getBlockHeight"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 1233,
  "id": 1
}
```
