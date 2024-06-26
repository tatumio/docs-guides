---
title: "debug_traceblockbyhash"
slug: "rpc-base-debug_traceblockbyhash"
excerpt: "Base RPC"
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:35 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const result = await tatum.rpc.debugTraceBlockByHash(
  "0x1141fda5c9d290557d3d0079f33423e2bc4ccba9b279d23dbc0884687cf36fe5",
  {
    tracer: "callTracer",
    tracerConfig: {
      onlyTopCall: true,
      timeout: "5s",
    },
  }
);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`debug_traceBlockByHash` is an RPC method that allows developers to trace all transactions within a block using a given tracer. This is particularly useful for analyzing the behavior of all transactions in a block, investigating potential issues, and understanding the flow of execution within smart contracts.

By using the `callTracer` tracer, developers can obtain more detailed information about the calls made during each transaction, including the input, output, and depth of the calls.

### Parameters

- `block_hash` (required): The hash of the block to be traced.
  - Example: `"0x1141fda5c9d290557d3d0079f33423e2bc4ccba9b279d23dbc0884687cf36fe5"`
- `options` (optional): An object containing configuration options for the tracer.
  - `tracer` (required, string): The tracer to use, in this case, `'callTracer'`.
  - `tracerConfig` (required, string): object containing `'timeout'` and `'onlyTopCall'` paramter
    - `timeout` (required, string): The maximum amount of time the tracer is allowed to run in seconds (e.g. "10s"). Default is "5s".
    - `onlyTopCall` (required, boolean): Setting this to true will only trace the main (top-level) call and none of the sub-calls. This avoids extra processing for each call frame if only the top-level call info is required (useful for getting revertReason).
  - Example: `{ tracer: 'callTracer', tracerConfig: { onlyTopCall: true, timeout: '5s', }}`

### Return Object

The return object is an array of objects, each representing the trace result of a transaction within the block. Each object contains the following fields:

- `from`: The address the transaction was sent from.
- `gas`: The gas provided for the transaction.
- `gasUsed`: The total gas used by the transaction.
- `to`: The address the transaction was sent to.
- `input`: The input data for the transaction.
- `output`: The output data from the transaction.
- `calls`: An array of objects, each representing a call made during the transaction. Each object contains:
  - `from`: The address the call was made from.
  - `gas`: The gas provided for the call.
  - `gasUsed`: The gas used by the call.
  - `to`: The address the call was made to.
  - `input`: The input data for the call.
  - `output`: The output data from the call.
  - `type`: The type of the call (e.g., "STATICCALL").

{% hint style="info" %}  
This method is available only on the full archive node.  
{% endhint %}

#### Response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": [
    {
      "result": {
        "from": "0x8894e0a0c962cb723c1976a4421c95949be2d4e3",
        "gas": "0x2d48c",
        "gasUsed": "0xc7ab",
        "to": "0x55d398326f99059ff775485246999027b3197955",
        "input": "0xa9059cbb0000000000000000000000003b9f33b3a9d382fa60283c555bde8f78855957be00000000000000000000000000000000000000000000000d4e7f4f79da7c0000",
        "output": "0x0000000000000000000000000000000000000000000000000000000000000001",
        "value": "0x0",
        "type": "CALL"
      }
    }
  ]
}
```
