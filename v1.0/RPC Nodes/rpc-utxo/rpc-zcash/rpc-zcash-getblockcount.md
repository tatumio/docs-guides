---
title: "getblockcount"
slug: "rpc-zcash-getblockcount"
excerpt: "Zcash RPC"
hidden: false
metadata: 
  description: "Zcash RPC"
  image: []
  keywords: "zcash, rpc"
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
// yarn add @tatumio/tatum

import { TatumSDK, ZCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<ZCash>({network: Network.ZCASH})

const result = await tatum.rpc.getBlockCount()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getblockcount` is a method that returns the number of blocks in the local best blockchain. This method is useful for obtaining the current height of the blockchain, which can be used for various purposes, such as monitoring the blockchain, determining the number of confirmations for a transaction, or assessing the progress of the blockchain's growth.

### Parameters

This method does not have any parameters.

### Return Object

The returned object is an integer representing the number of blocks in the local best blockchain.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getblockcount"
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": 787067,
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
