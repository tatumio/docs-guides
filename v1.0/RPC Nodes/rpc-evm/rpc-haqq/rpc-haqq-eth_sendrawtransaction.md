---
title: "eth_sendrawtransaction"
slug: "rpc-haqq-eth_sendrawtransaction"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const gasPrice = await tatum.rpc.sendRawTransaction('0x0000.......')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_sendRawTransaction` RPC method is used to send a signed and serialized Haqq transaction to the network. This method is particularly useful when you want to have full control over the signing process, e.g., when using hardware wallets, cold storage, or custom signing libraries. It can be utilized in various use cases, such as transferring ISLM, interacting with smart contracts, or deploying new contracts.

### Parameters

The method accepts a single parameter:

- **`data`**: The signed and serialized transaction data as a hexadecimal string.

### Return Value

The method returns a single value:

- `transactionHash`: The hash of the submitted transaction as a hexadecimal string, e.g., `"0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b"`.

### JSON-RPC Request Example

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_sendRawTransaction",
  "params": [
    "0xf86d8201...94a7bc"
  ]
}
```

### JSON-RPC Response Example

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b"
}
```

\\
