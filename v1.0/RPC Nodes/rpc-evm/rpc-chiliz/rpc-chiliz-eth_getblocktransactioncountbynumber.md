---
title: "eth_getblocktransactioncountbynumber"
slug: "rpc-chiliz-eth_getblocktransactioncountbynumber"
excerpt: "Chiliz RPC"
hidden: false
metadata: 
  description: "Chiliz RPC"
  image: []
  keywords: "chiliz, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Chiliz, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Chiliz>({network: Network.CHILIZ})

const response = await tatum.rpc.getBlockTransactionCountByNumber('0x65B9AB')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getBlockTransactionCountByNumber` JSON-RPC method allows you to retrieve the number of transactions in a specified block. This method is particularly useful when you need to analyze the transaction activity of a specific block. You can use it to gain insights into network usage, analyze the impact of specific events on the network, or monitor transaction congestion in certain blocks.

### Parameters

1. **`blockNumber`**: The block number for which the transaction count should be retrieved. It should be a hex-encoded value representing the block number.
   - Example: 371156

### Return Object

The return object is a hex-encoded value representing the number of transactions in the specified block.

- Example: `"0x1"` (1 transactions)

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getBlockTransactionCountByNumber",
  "params": [371156]
}
```

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1"
}
```

\\
