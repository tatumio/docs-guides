---
title: "getblockhash"
slug: "rpc-litecoin-getblockhash"
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

const result = await tatum.rpc.getBlockHash(587123)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getblockhash` is a Litecoin RPC method that returns the block hash for a specified block height in the local best blockchain. This method is useful for obtaining the hash of a specific block, which can then be used to query for more detailed information about that block using other RPC methods, such as `getblock`.

{% embed url="<https://codepen.io/tatum-devrel/pen/jOQJWPj"> %}

### Parameters

- `height`: The height of the block for which the hash is requested. This is an integer parameter.

  Example: `587123`

### Return Object

The return object is a string representing the hash of the block at the specified height.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getblockhash",
  "params": [587123],
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": "0000000000000000001b4fedbfb3672963c37f965686c2bf6350e32e77f9941f",
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
