---
title: "klay_blocknumber"
slug: "rpc-klaytn-klay_blocknumber"
excerpt: "Klaytn RPC"
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const latestBlock = await tatum.rpc.blockNumber()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `klay_blockNumber` method returns the number of the most recent block on the blockchain. This method is commonly used to track the current state of the network, monitor for new blocks, or fetch historical data.

Use cases for `klay_blockNumber` include:

- Synchronising a local copy of the blockchain with the network
- Checking the status of a transaction by comparing its block number to the current block number
- Determining the current network state for smart contract interactions\\

### Parameters

The `klay_blockNumber` method does not require any parameters.

### Return Object

The `klay_blockNumber` method returns a single field:

- **`blockNumber`**: The number of the most recent block on the blockchain. The value is returned as a hexadecimal string.

### JSON-RPC Request Example

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "klay_blockNumber",
  "params": []
}
```

### JSON-RPC Response Example

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x4b7" // 1207
}
```
