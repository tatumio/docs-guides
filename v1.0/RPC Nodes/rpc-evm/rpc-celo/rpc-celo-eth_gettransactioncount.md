---
title: "eth_gettransactioncount"
slug: "rpc-celo-eth_gettransactioncount"
excerpt: "Celo RPC"
hidden: false
metadata: 
  description: "Celo RPC"
  image: []
  keywords: "celo, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:34 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Celo, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Celo>({network: Network.CELO})

const result = await tatum.rpc.getTransactionCount('0x30ff20cb4A783B5bB97d0aF2e86d08c6B996D7d2', 'latest')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getTransactionCount` method is an JSON-RPC method that retrieves the number of transactions sent from a given address. It is a useful method for developers who need to keep track of an account's nonce value to avoid transaction collisions or incorrect order of execution. The nonce value is essential for ensuring transaction uniqueness and preventing replay attacks.

Use cases for this method include:

- Determining the nonce value for a new transaction to be sent from a specific address
- Monitoring the number of transactions sent by an address to observe its activity
- Troubleshooting transaction issues and verifying if a transaction was submitted successfully

### Parameters

The `eth_getTransactionCount` method accepts two parameters:

1. **`address`** - The address whose transaction count will be retrieved.
   - Example: `"0x30ff20cb4A783B5bB97d0aF2e86d08c6B996D7d2"`
2. **`blockParameter`** - A string indicating the block number or block state to consider when retrieving the transaction count.
   - Possible values: `"earliest"`, `"latest"`, `"pending"`, or a specific block number in hexadecimal format
   - Example: `"latest"`

### Return Object

The method returns a single value:

- **`transactionCount`** - A hexadecimal representation of the number of transactions sent from the specified address.
  - Example: `"0x1e"`

### JSON-RPC Request and Response Examples

_Request_:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getTransactionCount",
  "params": [
    "0x30ff20cb4A783B5bB97d0aF2e86d08c6B996D7d2",
    "latest"
  ]
}
```

_Response_:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1e"
}
```
