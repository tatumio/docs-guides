---
title: "debug_traceblockbynumber"
slug: "rpc-bsc-debug_traceblockbynumber"
excerpt: "Bsc RPC"
hidden: false
metadata: 
  description: "Bsc RPC"
  image: []
  keywords: "bsc, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:00 GMT+0000 (Coordinated Universal Time)"
---



### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, BinanceSmartChain, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BinanceSmartChain>({network: Network.BINANCE_SMART_CHAIN})

const result = await tatum.rpc.debugTraceBlockByNumber('0x1E3C299' , {
  tracer: 'callTracer',
  tracerConfig: {
      onlyTopCall: true,
      timeout: '5s',
  }
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`debug_traceBlockByNumber` is an RPC method that allows developers to trace all transactions within a block using a given tracer. This is particularly useful for analyzing the behavior of all transactions in a block, investigating potential issues, and understanding the flow of execution within smart contracts.

By using the `callTracer` tracer, developers can obtain more detailed information about the calls made during each transaction, including the input, output, and depth of the calls.

### Parameters

- `blockNumber` - `Quantity` or `String`
  - The block number of the block to trace.
  - Example: `"0x1"` or `"latest"`
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

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "debug_traceBlockByNumber",
  "params": [
    "latest",
    {
      "tracer": "callTracer",
      "timeout": "10s"
    }
  ]
}

```

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