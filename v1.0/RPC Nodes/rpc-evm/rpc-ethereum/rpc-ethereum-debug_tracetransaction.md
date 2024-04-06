---
title: "debug_traceTransaction"
slug: "rpc-ethereum-debug_tracetransaction"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "Ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 10:40:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 08:01:07 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


## Overview

`debug_traceTransaction` RPC method is utilized to trace the execution of a transaction on the Ethereum blockchain. This method is highly beneficial for debugging purposes, as it furnishes comprehensive details regarding the transaction's execution. These details include the type of call, the involved addresses, the transferred value, the gas consumption, the input and output data, any encountered errors, and reasons for reverts if applicable. Moreover, it can enumerate sub-calls made during the transaction's execution.

## Parameters

### 1.Transaction Hash (required)

A string representing the hash of the transaction you want to trace.

### 2.tracer (required)

An object that specifies the tracer to use for the transaction trace, one of the following:

| Name           | Type   | Required | Description                                                                                          |
| :------------- | :----- | :------- | :--------------------------------------------------------------------------------------------------- |
| callTracer     | string | Yes      | Tracks all call frames generated during a transaction, including those at depth 0.                   |
| prestateTracer | string | Yes      | Replays the transaction and monitors every aspect of the state that occurred throughout the process. |

### tracerConfig:

An object that allows specifying configurations for the tracer:

| Name        | Type    | Required | Description                                                                     |
| :---------- | :------ | :------- | :------------------------------------------------------------------------------ |
| onlyTopCall | boolean | Yes      | A boolean indicating whether to trace only the top-level call or all sub-calls. |

### 3.timeout

A string specifying the timeout for the trace operation. It's optional.

### Additional Configuration Parameters

`disableStorage` — when activated, it blocks the tracking of storage alterations made by the transaction under review, thus diminishing the resources needed for analysis. By default, `debug_traceTransaction` tracks both memory and storage changes, yet storage tracing can be notably demanding on resources, especially with sizable transactions.

`disableStack` — when enabled, it skips tracing of stack changes made by the transaction being analyzed.

`disableMemory` — when set to true, it halts the tracing of memory alterations carried out by the transaction under examination, thereby diminishing the necessary resources.

`disableReturnData` — when enabled, it disables the method from tracing the return data of a transaction. Tracing this return data can impose significant demands on resources, as it entails extensive time and processing power.

## Returns

`traceTransaction`response:

| Name         | Description                                                   |
| :----------- | :------------------------------------------------------------ |
| type         | The type of the call.                                         |
| from         | The address from which the transaction is sent.               |
| to           | The address to which the transaction is directed.             |
| value        | The integer value sent with the transaction.                  |
| gas          | The integer value of the gas used.                            |
| input        | The data given as input to the transaction.                   |
| output       | The data returned as output from the transaction.             |
| error        | The type of error encountered during the transaction, if any. |
| revertReason | The Solidity revert reason, if any.                           |
| calls        | A list of sub-calls made during the transaction's execution.  |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "debug_traceTransaction",
    "params": [
        "0x9e63085271890a141297039b3b711913699f1ee4db1acb667ad7ce304772036b",
        {
            "tracer": "callTracer"
        }
    ],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```javascript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.debugTraceTransaction('0x920d562e886a0c7c1f07ecee2ee5557f72d3056b205f8811c57e2615a3b6adb0', {
  tracer: 'callTracer',
  tracerConfig: {
      onlyTopCall: true,
      timeout: '5s',
  }
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
