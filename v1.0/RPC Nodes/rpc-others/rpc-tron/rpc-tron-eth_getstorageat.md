---
title: "eth_getstorageat"
slug: "rpc-tron-eth_getstorageat"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

// Initialize the SDK for the TRON network
const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const response = await tatum.rpc.getStorageAt('0xa41d19F4258a388c639B7CcD938FCE3fb7D05e86', '0x0')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_getStorageAt` is an JSON-RPC method that allows you to query the storage value of a contract at a given position. It can be used to inspect the internal state of a smart contract. This method is particularly useful for developers, auditors, and analysts who want to examine contract storage values for various purposes, such as debugging, verifying contract behavior, or analyzing data.

### Parameters

`eth_getStorageAt` accepts three parameters:

1. **`address`**: The address of the contract you want to query.
   - Example: `"0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
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
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
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
