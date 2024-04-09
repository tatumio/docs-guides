---
title: "txpool_inspect"
slug: "rpc-cronos-txpool_inspect"
excerpt: "Cronos RPC"
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cronos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Cronos>({network: Network.CRONOS})

const inspect = await tatum.rpc.txPoolInspect()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `txpool_inspect` method is a JSON-RPC method used to inspect the current transaction pool of a running node. The method allows you to view all pending transactions and their details, including transaction hashes, gas prices, and transaction data. This method is useful for developers who want to monitor the status of pending transactions or debug transaction-related issues.

### Parameters

The `txpool_inspect` method takes one optional parameter:

- **`include`**: A string specifying the type of transactions to include in the response. Possible values are **`pending`** (default) and **`queued`**.

### Return Object

The `txpool_inspect` method returns an object with the following fields:

- **`pending`**: An array of transaction objects, with textual data
- **`queued`**: An array of transaction objects, with textual data
