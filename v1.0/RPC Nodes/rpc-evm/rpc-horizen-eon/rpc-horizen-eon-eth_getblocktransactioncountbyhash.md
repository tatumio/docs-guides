---
title: "eth_getblocktransactioncountbyhash"
slug: "rpc-horizen-eon-eth_getblocktransactioncountbyhash"
excerpt: "Horizen Eon  RPC"
hidden: false
metadata: 
  description: "Horizen Eon RPC"
  image: []
  keywords: "horizen-eon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:44 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, HorizenEon, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<HorizenEon>({network: Network.HORIZEN_EON})

const response = await tatum.rpc.getBlockTransactionCountByHash('0xb0ddfcdcc375afce9f365458c5035ca4aaf99f9fe8699522193e16a8718615b6')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_getBlockTransactionCountByHash` is a RPC method used to fetch the number of transactions in a block by the block's hash. It is useful when you want to know the total number of transactions included in a specific block and don't want to retrieve the entire block data. This method can be used in various scenarios, such as monitoring the network activity or estimating transaction confirmation times.

### Parameters

This method requires a single parameter:

- **`blockHash`**: The hash of the target block for which the transaction count will be retrieved. It should be a valid 32-byte hex string.

Example of the parameter:

- `blockHash`: `"0xb0ddfcdcc375afce9f365458c5035ca4aaf99f9fe8699522193e16a8718615b6"`

### Return

The method returns a single value:

- `transactionCount`: The total number of transactions included in the specified block. It is returned as a hexadecimal value.

### Examples

#### JSON-RPC request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getBlockTransactionCountByHash",
  "params": [
    "0xb0ddfcdcc375afce9f365458c5035ca4aaf99f9fe8699522193e16a8718615b6"
  ]
}
```

#### JSON-RPC response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0xa"
}
```

In this example, the block with the hash `"0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"` has a total of 10 transactions (indicated by the hexadecimal value `"0xa"`).
