---
title: "eth_chainid"
slug: "rpc-xinfin-eth_chainid"
excerpt: "Xinfin RPC"
hidden: false
metadata: 
  description: "Xinfin RPC"
  image: []
  keywords: "xinfin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, XinFin, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<XinFin>({ network: Network.XINFIN })

const id = await tatum.rpc.chainId()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_chainId` method is a method that allows developers to retrieve the currently configured chain ID of the network they are connected to. The chain ID is a unique identifier for different networks, such as Mainnet or various testnets.

This method is particularly useful when building applications that interact with multiple networks or need to verify the network to prevent replay attacks. By checking the chain ID, an application can ensure it is interacting with the intended network.

### Parameters

The `eth_chainId` method does not have any input parameters.

### Return Object

The return object contains a single field:

- **`chainId`**: The hexadecimal string representation of the chain ID.

### Example Request and Response

JSON-RPC request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_chainId",
  "params": []
}
```

JSON-RPC response:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0xa"
}
```
