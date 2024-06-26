---
title: "getbestblockhash"
slug: "rpc-dogecoin-getbestblockhash"
excerpt: "Dogecoin RPC"
hidden: false
metadata: 
  description: "Dogecoin RPC"
  image: []
  keywords: "dogecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:07 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Dogecoin>({network: DOGECOIN})

const result = await tatum.rpc.getBestBlockHash()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getbestblockhash` is a Dogecoin RPC method that returns the hash of the best (tip) block in the longest blockchain. This method is useful for obtaining the latest block hash, which can be used to fetch block details or confirmations for transactions.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Jan-Musil-the-lessful/pen/zYMbowj",
  "href": "https://codepen.io/Jan-Musil-the-lessful/pen/zYMbowj",
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
