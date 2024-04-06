---
title: "getdifficulty"
slug: "rpc-litecoin-getdifficulty"
excerpt: "Litecoin RPC"
hidden: false
metadata: 
  description: "Litecoin RPC"
  image: []
  keywords: "litecoin, rpc"
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

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Litecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Litecoin>({network: Network.LITECOIN})

const result = await tatum.rpc.getDifficulty()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`getdifficulty` is a Litecoin RPC method that returns the current mining difficulty. The mining difficulty is a measure of how difficult it is to find a new block compared to the easiest it can ever be. This method can be used to monitor the mining difficulty, which adjusts every 2016 blocks to maintain a consistent block creation rate of approximately 10 minutes per block.

{% embed url="<https://codepen.io/tatum-devrel/pen/qBQvbxp"> %}

### Parameters

This method does not require any parameters.

### Return Object

A return object is a floating-point number that represents the current mining difficulty.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getdifficulty",
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": 48712405953118.43,
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
