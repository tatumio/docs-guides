---
title: "eth_getunclecountbyblocknumber"
slug: "rpc-haqq-eth_getunclecountbyblocknumber"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const result = await tatum.rpc.getUncleCountByBlockNumber(7687453)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getUncleCountByBlockHash` method is an Haqq JSON-RPC method that returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the Haqq network and to analyze the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralization of the Haqq network. The inclusion of uncles helps prevent centralization and ensures the mining process remains competitive.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Lukas-Kotol/pen/wvQOGYg?editors=1111",
  "href": "https://codepen.io/Lukas-Kotol/pen/wvQOGYg?editors=1111",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `eth_getUncleCountByBlockHash` method takes one parameter:

- `blockNumber`: The number of the block for which you want to get the uncle count.
  - Example value: 7687453

### Return Object

The return object for this method is a hex-encoded integer representing the number of uncles in the specified block.

- Example value: `"0x1"` (1 uncle)

### JSON-RPC Request and Response Examples

Here is an example JSON-RPC request and response for the `eth_getUncleCountByBlockNumber` method:

**Request:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getUncleCountByBlockNumber",
  "params": [
    7687453
  ]
}
```

**Response:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x1"
}
```

In this example, the JSON-RPC request asks for the number of uncles in the block with the specified hash. The response indicates that there is one uncle in the block.

\\
