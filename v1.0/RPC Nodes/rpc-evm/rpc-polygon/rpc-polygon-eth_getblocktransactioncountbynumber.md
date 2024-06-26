---
title: "eth_getblocktransactioncountbynumber"
slug: "rpc-polygon-eth_getblocktransactioncountbynumber"
excerpt: "Polygon RPC"
hidden: false
metadata: 
  description: "Polygon RPC"
  image: []
  keywords: "polygon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:39 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Polygon, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Polygon>({network: Network.POLYGON})

const response = await tatum.rpc.getBlockTransactionCountByNumber(47766249)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getBlockTransactionCountByNumber` Polygon JSON-RPC method allows you to retrieve the number of transactions in a specified block. This method is particularly useful when you need to analyse the transaction activity of a specific block. You can use it to gain insights into network usage, analyse the impact of specific events on the Polygon network, or monitor transaction congestion in certain blocks.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/gOQqZKy",
  "href": "https://codepen.io/tatum-devrel/pen/gOQqZKy",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

1. **`blockNumber`**: The block number for which the transaction count should be retrieved. It should be a hex-encoded value representing the block number.
   - Example: 47766249

### Return Object

The returned object is a hex-encoded value representing the number of transactions in the specified block.

- Example: `"0xa"` (10 transactions)

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getBlockTransactionCountByNumber",
  "params": [47766249]
}
```

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x33"
}
```

\\
