---
title: "eth_maxpriorityfeepergas"
slug: "rpc-bsc-eth_maxpriorityfeepergas"
excerpt: "Bsc RPC"
hidden: false
metadata: 
  description: "Bsc RPC"
  image: []
  keywords: "bsc, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, BinanceSmartChain, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BinanceSmartChain>({network: Network.BINANCE_SMART_CHAIN})

const gasPrice = await tatum.rpc.maxPriorityFeePerGas()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_maxPriorityFeePerGas` RPC method is used to retrieve the maximum priority fee per gas set by the user for a transaction. This method can be used to determine the maximum fee that can be paid for a transaction to be included in a block quickly.

### Use case

This method is particularly useful when the user wants to ensure that a transaction is processed quickly, even in a congested network where transaction fees may fluctuate rapidly. By setting a high maximum priority fee per gas, the user can ensure that the transaction is processed as quickly as possible.

### Parameters

`None.`

## Return Object

- `maxPriorityFeePerGas` - The maximum priority fee per gas the user is willing to pay, in wei.

### JSON Examples

#### Request

```json
{
    "jsonrpc": "2.0",
    "method": "eth_maxPriorityFeePerGas",
    "params": [],
    "id": 1
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x3b9aca00"
}
```

\\
