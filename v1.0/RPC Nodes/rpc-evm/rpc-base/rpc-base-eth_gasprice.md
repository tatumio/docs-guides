---
title: "eth_gasprice"
slug: "rpc-base-eth_gasprice"
excerpt: "Base RPC"
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const gasPrice = await tatum.rpc.gasPrice();

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_gasPrice` method is used to estimate the average gas price required for transactions in the network. This method provides a suggestion for the gas price to be used in a transaction to increase the likelihood of it being mined and included in a block in a reasonable amount of time. The `eth_gasPrice` method is particularly useful for developers and users who want to create and send transactions, as it helps them estimate the appropriate gas price to ensure timely processing.

### Parameters

The `eth_gasPrice` method does not require any parameters.

### Return Value

The `eth_gasPrice` method returns a single value as a hexadecimal string:

- `gasPrice`: The estimated average gas price in wei. Example: `"0x4a817c800"`

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 73,
  "result": "0x92f96e98800"
}
```
