---
title: "klay_getunclecountbyblocknumber"
slug: "rpc-klaytn-klay_getunclecountbyblocknumber"
excerpt: "Klaytn RPC"
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const result = await tatum.rpc.getUncleCountByBlockNumber('0x80F8C7A')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `klay_getUncleCountByBlockHash` method is an JSON-RPC method that returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the network and to analyze the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralization of the network. The inclusion of uncles helps prevent centralization and ensures the mining process remains competitive.

### Parameters

The `klay_getUncleCountByBlockHash` method takes one parameter:

- `blockNumber`: The number of the block for which you want to get the uncle count.
  - Example value: `"0x12345"`

### Return Object

The return object for this method is a hex-encoded integer representing the number of uncles in the specified block.

- Example value: `"0x1"` (1 uncle)

### JSON-RPC Request and Response Examples

Here is an example JSON-RPC request and response for the `klay_getUncleCountByBlockNumber` method:

**Request:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "klay_getUncleCountByBlockNumber",
  "params": [
    "0x12345"
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
