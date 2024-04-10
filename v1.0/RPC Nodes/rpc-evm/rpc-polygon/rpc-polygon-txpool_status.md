---
title: "txpool_status"
slug: "rpc-polygon-txpool_status"
excerpt: "Polygon RPC"
hidden: false
metadata: 
  description: "Polygon RPC"
  image: []
  keywords: "polygon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:35 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Polygon, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Polygon>({network: Network.POLYGON})

const status = await tatum.rpc.txPoolStatus()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `txpool_status` method returns statistics about the current state of the transaction pool. The transaction pool is a queue of pending transactions waiting to be included in the next block by miners.

This method can be useful for monitoring the health of the Polygon network and analysing the behavior of the miners. It can also be used to estimate the time it will take for a transaction to be processed, as well as to determine the gas price necessary to ensure prompt inclusion of a transaction in the next block.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/bGQzOyV",
  "href": "https://codepen.io/tatum-devrel/pen/bGQzOyV",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

This method does not take any parameters.

### Return Object

The `txpool_status` method returns an object with the following fields:

- **`pending`**: Number of pending transactions in the pool
- **`queued`**: Number of queued transactions in the pool

### Example Request

```json
{
  "jsonrpc":"2.0",
  "method":"txpool_status",
  "params":[],
  "id":1
}
```

### Example Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "pending": 4,
    "queued": 10
  }
}
```

In this example response, there are currently 4 pending transactions and 10 queued transactions waiting to be processed by miners.
