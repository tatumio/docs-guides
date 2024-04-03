---
title: "debug_traceCall"
slug: "rpc-ethereum-debug_tracecall"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "Ethereum, rpc"
  robots: "index"
createdAt: "Thu Mar 07 2024 09:21:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:41:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

## Overview

`debug_traceCall` is an Ethereum RPC method that allows you to execute a given call (message), tracing the steps of its execution. This can be helpful for developers and auditors who want to inspect and analyze the internal operations and state changes of a contract call without modifying the blockchain state. This method can assist in debugging and identifying potential issues with contract execution, as well as understanding how gas is consumed during the execution of a call.

## Parameters

### 1. Transaction call object (required)

`object` - The eth_call data

| Name     | Type    | Required | Description                                                                                                                                                                    |
| :------- | :------ | :------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from     | string  | no       | The address the transaction is sent from                                                                                                                                       |
| to       | string  | yes      | The address the transaction is directed to                                                                                                                                     |
| gas      | integer | no       | The integer of the gas provided for the transaction execution. Although eth_call consumes zero gas, this parameter may still be needed by some executions.                     |
| gasPrice | integer | no       | The integer of the gasPrice used for each paid gas                                                                                                                             |
| value    | integer | no       | The integer of the value sent with this transaction                                                                                                                            |
| data     | string  | no       | The hash of the method signature and encoded parameters. Additional information is available at [Ethereum Contract ABI](https://docs.soliditylang.org/en/v0.7.0/abi-spec.html) |

### 2. Block parameter (required)

- hexadecimal block number
- block hash
- The `Tag` "latest", "earliest", "pending", "safe" or "finalized" "Safe" and "finalized" are only available on Ethereum and Arbitrum One chain. [Ethereum documentation](https://ethereum.org/en/developers/docs/apis/json-rpc/#default-block).

### 3. Trace type (optional)

- ` The type of tracer` - String - It might be `callTracer` or `prestateTracer`
  - `callTracer` - The calltracer keeps track of all call frames, including depth 0 calls, that are made during a transaction.
  - `prestateTracer` - The prestateTracer replays the transaction and tracks every part of state that occured during the transaction.
- `tracerConfig` - The object to specify the configurations of the tracer
  - `onlyTopCall` - When set to true, this will only trace the primary (top-level) call and not any sub-calls. It eliminates the additional processing for each call frame.

#### Additional configuration parameters

- `disableStorage` — when enabled, it prevents tracing of storage changes made by the transaction being analyzed, which can reduce the resource requirements of the analysis. By default, debug_traceTransaction traces both memory and storage changes, but storage tracing can be particularly resource-intensive, especially for large transactions.
- `disableStack` — when enabled, it skips tracing of stack changes made by the transaction being analyzed.
- `disableMemory` — when true, it stops tracing of memory changes made by the transaction being analyzed, reducing resource requirements.
- `disableReturnData` — when true, it prevents the method from tracing the return data of a transaction. This return data tracing can be very demanding on resources, as it requires a lot of time and processing power.
- `timeout` (default: 5s) — allows to customize the method's timeout period for JavaScript-based tracing calls.

> 🚧 When using a tracer type , `disableMemory`, `disableStorage`, `disableStack`, or `disableReturnData` will not have any effect. When no tracer is selected, the response defaults to [Struct/opcode logger](https://geth.ethereum.org/docs/developers/evm-tracing/built-in-tracers#structopcode-logger).

## Returns

`callTracer` response:

| Name              | Description                                                                                               |
| :---------------- | :-------------------------------------------------------------------------------------------------------- |
| type of the call  | Type of the call                                                                                          |
| from              | The transaction sender.                                                                                   |
| to                | The address of the transaction recipient.                                                                 |
| gas               | The gas included in the transaction by the sender.                                                        |
| transaction value | The actual value per gas deducted from the sender's account.                                              |
| gasUsed           | The total used gas by the call. Encoded as hexadecimal.                                                   |
| input             | The optional input data sent with the transaction, usually used to interact with smart contracts.         |
| output            | The return value of the call, encoded as a hexadecimal string.                                            |
| error             | An error message in case the execution failed.                                                            |
| calls             | A list of sub-calls made by the contract during the call, each represented as a nested call frame object. |
| revertReason      | The reason why the transaction was reverted, returned by the smart contract if any.                       |

`prestateTracer` response

- `smart contract address` — The address of the smart contract associated with the result.
  - `balance` — The balance of the contract, expressed in wei and encoded as a hexadecimal string.
  - `code` — The bytecode of the contract, encoded as a hexadecimal string.
  - `nonce` — The nonce of the account associated with the contract, represented as an unsigned integer.
  - `storage` — A map of key-value pairs representing the storage slots of the contract. The keys and values are both encoded as hexadecimal strings.

`Struct/opcode` response

- `The transaction trace object:`
- `failed` - Successful or failed
- `gas` - The total consumed gas in the transaction
- `returnValue` - The return value of the executed contract call
- `structLogs` - The trace result of each step:
  - `pc` - The current index in bytecode.
  - `op` - The name of current executing operation.
  - `gas` - The available gas in the execution.
  - `gasCost` - The gas cost of the operation.
  - `depth` - The number of levels of calling functions.
  - `stack` - An array of values in the current stack.
  - `storage` - The mapping of the current storage.
  - `refund` - The total of current refund value.
  - `error` - The error of the execution.
  - `memory` - An array of values in the current memory.

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method":"debug_traceCall",
    "params":[{
        "to":"0x742d35Cc6634C0532925a3b844Bc454e4438f44e"
        },
        "latest"
    ],
    "id":1,
    "jsonrpc":"2.0"
}'
```
```javascript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.debugTraceCall({
      "from": "0xa7d9ddbe1f17865597fbd27ec712455208b6b76d",
      "to": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "gas": "0x76c0",
      "gasPrice": "0x9184e72a000",
      "value": "0x9184e72a",
      "data": "0x606060..."
    },
    "0x1b4",
    {
  tracer: 'callTracer',
  tracerConfig: {
      onlyTopCall: true,
      timeout: '5s',
  }
}
)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
