---
title: "eth_getunclecountbyblockhash"
slug: "rpc-avalanche-eth_getunclecountbyblockhash"
excerpt: "Avalanche RPC"
hidden: false
metadata: 
  description: "Avalanche RPC"
  image: []
  keywords: "avalanche, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:37 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, AvalancheC, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<AvalancheC>({network: Network.AVALANCHE_C})

const result = await tatum.rpc.getUncleCountByBlockHash('0x17ba17556f9028fd9957920b01b0e133d7499915c864648e6554b38d3234c4c8')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getUncleCountByBlockHash` method is an JSON-RPC method that returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the network and to analyze the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralization of the network. The inclusion of uncles helps prevent centralization and ensures the mining process remains competitive.

### Parameters

The `eth_getUncleCountByBlockHash` method takes one parameter:

- `blockHash`: The hash of the block for which you want to get the uncle count.
  - Example value: `"0x17ba17556f9028fd9957920b01b0e133d7499915c864648e6554b38d3234c4c8"`

### Return Object

The return object for this method is a hex-encoded integer representing the number of uncles in the specified block.

- Example value: `"0x1"` (1 uncle)

### JSON-RPC Request and Response Examples

Here is an example JSON-RPC request and response for the `eth_getUncleCountByBlockHash` method:

**Request:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getUncleCountByBlockHash",
  "params": [
    "0x17ba17556f9028fd9957920b01b0e133d7499915c864648e6554b38d3234c4c8"
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
