---
title: "getbestblockhash"
slug: "rpc-litecoin-getbestblockhash"
excerpt: "Litecoin RPC"
hidden: false
metadata: 
  description: "Litecoin RPC"
  image: []
  keywords: "litecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 14:43:58 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Litecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Litecoin>({network: Network.LITECOIN})

const result = await tatum.rpc.getBestBlockHash()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getbestblockhash` is a Litecoin RPC method that returns the hash of the best (tip) block in the longest blockchain. This method is useful for obtaining the latest block hash, which can be used to fetch block details or confirmations for transactions.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/vYQPLOd",
  "href": "https://codepen.io/tatum-devrel/pen/vYQPLOd",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

This method does not have any parameters.

### Return Object

The returned object is a string containing the hash of the best block.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getbestblockhash"
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "result": "0000000000000000000ef0e1f703b56f2b0d6724e4eeccf00e4f8d55b9c3c3f6e",
  "error": null
}
```

{% endcode %}

\\
