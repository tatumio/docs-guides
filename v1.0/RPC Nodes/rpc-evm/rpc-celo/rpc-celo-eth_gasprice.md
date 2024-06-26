---
title: "eth_gasprice"
slug: "rpc-celo-eth_gasprice"
excerpt: "Celo RPC"
hidden: false
metadata: 
  description: "Celo RPC"
  image: []
  keywords: "celo, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:08:59 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Celo, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Celo>({network: Network.CELO})

const gasPrice = await tatum.rpc.gasPrice()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_gasPrice` method is an JSON-RPC method used to estimate the average gas price required for transactions in the network. This method provides a suggestion for the gas price to be used in a transaction to increase the likelihood of it being mined and included in a block in a reasonable amount of time. The `eth_gasPrice` method is particularly useful for developers and users who want to create and send transactions, as it helps them estimate the appropriate gas price to ensure timely processing.

### Parameters

The `eth_gasPrice` method does not require any parameters. 

### Return Value

The `eth_gasPrice` method returns a single value as a hexadecimal string:

- `gasPrice`: The estimated average gas price in wei. Example: `"0x4a817c800"`

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_gasPrice",
  "params": []
}
```

#### Response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x4a817c800"
}
```

By using the `eth_gasPrice` method, developers and users can estimate the appropriate gas price for their transactions, improving the overall user experience and ensuring that their transactions are processed in a timely manner.
