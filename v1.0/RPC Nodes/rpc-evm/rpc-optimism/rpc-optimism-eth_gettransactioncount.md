---
title: "eth_gettransactioncount"
slug: "rpc-optimism-eth_gettransactioncount"
excerpt: "Optimism RPC"
hidden: false
metadata: 
  description: "Optimism RPC"
  image: []
  keywords: "optimism, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Optimism, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Optimism>({network: Network.OPTIMISM})

const result = await tatum.rpc.getTransactionCount('0x365a2dabcdb56f4f595c3af088b8975c26331448', 'latest')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getTransactionCount` method is method that retrieves the number of transactions sent from a given address. It is a useful method for developers who need to keep track of an account's nonce value to avoid transaction collisions or incorrect order of execution. The nonce value is essential for ensuring transaction uniqueness and preventing replay attacks.

Use cases for this method include:

- Determining the nonce value for a new transaction to be sent from a specific address
- Monitoring the number of transactions sent by an address to observe its activity
- Troubleshooting transaction issues and verifying if a transaction was submitted successfully

### Parameters

The `eth_getTransactionCount` method accepts two parameters:

1. **`address`** - The address whose transaction count will be retrieved.
   - Example: `"0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
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
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
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
