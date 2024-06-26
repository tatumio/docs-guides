---
title: "debug_storagerangeat"
slug: "rpc-klaytn-debug_storagerangeat"
excerpt: "Klaytn RPC"
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:00 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const res = await tatum.rpc.debugStorageRangeAt(
   '0xcb632c914a18d838113f1e0cbf3ebc58e837c9497113c247001ecd52b212768e',
   1, '0x898f2afc07924f5a4f9612449e4c4f8eca527515', '0x0000000000000000000000000000000000000000000000000000000000000000', 1
)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`debug_storageRangeAt` is an RPC method that allows you to retrieve the contract storage range for a given block and address. This can be useful for developers and auditors who want to inspect the storage state of a specific contract at a particular point in time. This method can also help in debugging and identifying potential issues with contract storage, as well as understanding how storage evolves as transactions are executed.

### Parameters

The `debug_storageRangeAt` method accepts the following parameters:

- `blockHash`: The block hash for which the storage range should be retrieved. Example: `"0x3c4523b7e8c21e3d68f1c3af3d18e8a87c0d43e35b2c1b7f8f4e87e4d4db9c82"`
- `txIndex`: The transaction index within the specified block. Example: `1`
- `address`: The contract address for which the storage range should be retrieved. Example: `"0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
- `begin`: The beginning of the storage range. Example: `"0x0000000000000000000000000000000000000000000000000000000000000000"`
- `end`: The end of the storage range. Example: `1` (inclusive)

### Return Object

The `debug_storageRangeAt` method returns an object with the following fields:

- `storage`: An object that contains key-value pairs representing the contract storage, where the key is the storage slot and the value is the stored data. Example: `"0x00..01": "0x00..01"`
- `nextKey`: A key indicating the next storage slot if the requested range is too large, otherwise `null`. Example: `"0x00..02"` or `null`

{% hint style="info" %}  
This method is available only on the full archive node.  
{% endhint %}

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "debug_storageRangeAt",
  "params": [
    "0x3c4523b7e8c21e3d68f1c3af3d18e8a87c0d43e35b2c1b7f8f4e87e4d4db9c82",
    "0x1",
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
    "0x0000000000000000000000000000000000000000000000000000000000000000", 1
  ]
}
```

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "storage": {
      "0x0000000000000000000000000000000000000000000000000000000000000001": "0x0000000000000000000000000000000000000000000000000000000000000001",
      "0x0000000000000000000000000000000000000000000000000000000000000002": "0x0000000000000000000000000000000000000000000000000000000000000002"
    },
    "nextKey": "0x0000000000000000000000000000000000000000000000000000000000000065"
  }
}
```
