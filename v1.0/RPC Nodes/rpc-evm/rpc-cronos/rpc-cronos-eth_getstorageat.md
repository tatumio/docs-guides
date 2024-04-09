---
title: "eth_getstorageat"
slug: "rpc-cronos-eth_getstorageat"
excerpt: "Cronos RPC"
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:39 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cronos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Cronos>({network: Network.CRONOS})

const response = await tatum.rpc.getStorageAt('0x523D6F30C4aaca133DAAD97eE2A0C48235bfF137', '0x0')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_getStorageAt` is an JSON-RPC method that allows you to query the storage value of a contract at a given position. It can be used to inspect the internal state of a smart contract. This method is particularly useful for developers, auditors, and analysts who want to examine contract storage values for various purposes, such as debugging, verifying contract behavior, or analyzing data.

### Parameters

`eth_getStorageAt` accepts three parameters:

1. **`address`**: The address of the contract you want to query.
   - Example: `"0x523D6F30C4aaca133DAAD97eE2A0C48235bfF137"`
2. **`position`**: The storage position (slot) you want to query.
   - Example: `"0x0"`
3. **`blockParameter`**: The block number, block hash, or one of the string literals (`"earliest"`, `"latest"` or `"pending"`), representing the point in the blockchain to query the storage value.
   - Example: `"latest"`

### Return Object

The return object is a single string value, representing the storage value at the given position in the contract.

- `result`: The storage value in a 32-byte (64 character) hexadecimal format.
