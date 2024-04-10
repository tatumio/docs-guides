---
title: "eth_getstorageat"
slug: "rpc-polygon-eth_getstorageat"
excerpt: "Polygon RPC"
hidden: false
metadata: 
  description: "Polygon RPC"
  image: []
  keywords: "polygon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Polygon, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Polygon>({network: Network.POLYGON})

const response = await tatum.rpc.getStorageAt('0x0000000000000000000000000000000000001010', '0x0')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_getStorageAt` is a Polygon JSON-RPC method that allows you to query the storage value of a contract at a given position. It can be used to inspect the internal state of a smart contract. This method is particularly useful for developers, auditors, and analysts who want to examine contract storage values for various purposes, such as debugging, verifying contract behavior, or analyzing data.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Martin-Zemanek/pen/eYQYNzG",
  "href": "https://codepen.io/Martin-Zemanek/pen/eYQYNzG",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

`eth_getStorageAt` accepts three parameters:

1. **`address`**: The address of the contract you want to query.
   - Example: `"0x0000000000000000000000000000000000001010"`
2. **`position`**: The storage position (slot) you want to query.
   - Example: `"0x0"`
3. **`blockParameter`**: The block number, block hash, or one of the string literals (`"earliest"`, `"latest"` or `"pending"`), representing the point in the blockchain to query the storage value.
   - Example: `"latest"`

### Return Object

The return object is a single string value, representing the storage value at the given position in the contract.

- `result`: The storage value in a 32-byte (64 character) hexadecimal format.

### JSON-RPC Request Example

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getStorageAt",
  "params": [
    "0x0000000000000000000000000000000000001010",
    "0x0",
    "latest"
  ]
}
```

### JSON-RPC Response Example

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x0000000000000000000000000000000000000000000000000000000000000123"
}
```

\\
