---
title: "debug_traceBlockByHash"
slug: "rpc-ethereum-debug_traceblockbyhash"
excerpt: "Ethereum RPC"
hidden: false
metadata:
  image: []
  keywords: "Ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 13:51:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---

[block:html]
{
"html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n <h5>Archive Method</h5>\n <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]

## Overview

`debug_traceBlockByHash`method allows developers to trace the execution of transactions within a block specified by its hash. This method is particularly useful for debugging purposes, as it provides detailed information about the execution of each transaction within the block, including the type of call, the addresses involved, the value transferred, the gas used, the input data, the output data, and any sub-calls made during the transaction.

## Parameters

### 1.blockHash (required)

A string representing the hash of the block to be traced.

### 2.tracer (required)

An object that specifies the tracer to use for the transaction trace, one of the following:

| Name           | Type   | Required | Description                                                                                          |
| :------------- | :----- | :------- | :--------------------------------------------------------------------------------------------------- |
| callTracer     | string | Yes      | Tracks all call frames generated during a transaction, including those at depth 0.                   |
| prestateTracer | string | Yes      | Replays the transaction and monitors every aspect of the state that occurred throughout the process. |

### tracerConfig

An object that allows specifying configurations for the tracer:

| Name        | Type    | Required | Description                                                                     |
| :---------- | :------ | :------- | :------------------------------------------------------------------------------ |
| onlyTopCall | boolean | Yes      | A boolean indicating whether to trace only the top-level call or all sub-calls. |

## Returns

`callTracer` response

| Name              | Description                                                                                                                |
| :---------------- | :------------------------------------------------------------------------------------------------------------------------- |
| type of the call  | The type of the call.                                                                                                      |
| from              | The address from which the transaction is sent.                                                                            |
| to                | The address to which the transaction is directed.                                                                          |
| gas               | The integer value of the gas used.                                                                                         |
| transaction value | The specific amount deducted from the sender's account per unit of gas consumed.                                           |
| gasUsed           | The total gas consumed during the call, represented in hexadecimal format.                                                 |
| input             | The input data accompanying the transaction, optionally provided, typically utilised for interacting with smart contracts. |
| output            | The data returned as output from the transaction.                                                                          |
| error             | The type of error encountered during the transaction, if any.                                                              |
| revertReason      | The Solidity revert reason, if any.                                                                                        |
| calls             | A list of sub-calls made during the transaction's execution.                                                               |

`prestateTracer` response

| Name                   | Description                                                                                                               |
| :--------------------- | :------------------------------------------------------------------------------------------------------------------------ |
| smart contract address | The smart contract address linked to the outcome.                                                                         |
| balance                | The balance of the contract , shown in hexadecimal format, and measured in wei.                                           |
| code                   | The contract's bytecode encoded as a hexadecimal string                                                                   |
| nonce                  | The account's nonce connected to the contract, shown as a unsigned integer                                                |
| storage                | A collection of pairs showing the storage slots of the contract, with both keys and values encoded in hexadecimal format. |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "debug_traceBlockByHash",
    "params": [
        "0x97b49e43632ac70c46b4003434058b18db0ad809617bd29f3448d46ca9085576",
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

import { TatumSDK, Ethereum, Network } from "@tatumio/tatum";

const tatum = (await TatumSDK.init) < Ethereum > { network: Network.ETHEREUM };

const result = await tatum.rpc.debugTraceBlockByHash(
  "0x3c4523b7e8c21e3d68f1c3af3d18e8a87c0d43e35b2c1b7f8f4e87e4d4db9c82",
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
