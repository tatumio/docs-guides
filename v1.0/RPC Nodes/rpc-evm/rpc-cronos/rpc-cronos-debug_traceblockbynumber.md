---
title: "debug_traceblockbynumber"
slug: "rpc-cronos-debug_traceblockbynumber"
excerpt: "Cronos RPC"
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 11:57:01 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cronos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Cronos>({network: Network.CRONOS})

const result = await tatum.rpc.debugTraceBlockByNumber(12863491)

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
  - Example: `"12863491"` or `"latest"`
- `options`  as `tracerConfig`(optional): An object containing configuration options for the tracer.
  - `tracer` (required): The tracer to use, in this case, `"callTracer"`.
  - `timeout` (required): The maximum amount of time the tracer is allowed to run, in seconds or as a string (e.g. "10s"). Default is "5s".
  - Example: `tracerConfig: { onlyTopCall: true, timeout: '10', }`

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
