---
title: "eth_getblocktransactioncountbynumber"
slug: "rpc-base-eth_getblocktransactioncountbynumber"
excerpt: "Base RPC"
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const response = await tatum.rpc.getBlockTransactionCountByNumber("0xb2ef82");

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getBlockTransactionCountByNumber` method allows you to retrieve the number of transactions in a specified block. This method is particularly useful when you need to analyze the transaction activity of a specific block. You can use it to gain insights into network usage, analyze the impact of specific events on the network, or monitor transaction congestion in certain blocks.

### Parameters

1. **`blockNumber`**: The block number for which the transaction count should be retrieved. It should be a hex-encoded value representing the block number.
   - Example: block number "0xb2e214"

### Return Object

The return object is a hex-encoded value representing the number of transactions in the specified block.

- Example: 17884144 (10 transactions)

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x86"
}
```
