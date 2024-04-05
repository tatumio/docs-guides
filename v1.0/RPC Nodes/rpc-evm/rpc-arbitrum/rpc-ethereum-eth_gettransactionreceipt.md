---
title: "eth_getTransactionReceipt"
slug: "rpc-arbitrum-eth_gettransactionreceipt"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 10:52:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:03:46 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getTransactionReceipt` is an Ethereum JSON-RPC method that retrieves the transaction receipt of a given transaction hash. This method is particularly useful when you need to obtain detailed information about a transaction's execution, such as its status (success or failure), gas usage, and logs (events). Common use cases include checking the status of a transaction after it has been mined or inspecting the events emitted by a smart contract during a specific transaction.

## Parameters

This method requires a single parameter:

- `transactionHash`:  The hash of the transaction for which you want to obtain the receipt.
  - Example: "0x2a4811309750a84058d2fd1bd8dd534bf3a34039ff1b34e29f23a92dfb06449d"

## Returns

The method returns an object containing the following fields:

| Name              | Description                                                                                               |
| :---------------- | :-------------------------------------------------------------------------------------------------------- |
| transactionHash   | The hash of the transaction.                                                                              |
| transactionIndex  | The transaction's index position in the block.                                                            |
| blockHash         | The hash of the block where this transaction was mined.                                                   |
| blockNumber       | The block number where this transaction was mined.                                                        |
| from              | The address of the sender.                                                                                |
| to                | The address of the receiver. `null `when it's a contract creation transaction.                            |
| cumulativeGasUsed | The total amount of gas used when this transaction was executed in the block.                             |
| gasUsed           | The amount of gas used by this specific transaction alone.                                                |
| contractAddress   | The address of the contract created, if the transaction was a contract creation. Otherwise, `null`.       |
| logs              | An array of log objects, which were emitted during the transaction.                                       |
| logsBloom         | A 256-byte bloom filter, which is a compressed representation of the logs emitted during the transaction. |
| status            | The status of the transaction's execution. `"0x1"` indicates success, while `"0x0" `indicates failure.    |

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getTransactionReceipt",
  "params": [
    "0x2a4811309750a84058d2fd1bd8dd534bf3a34039ff1b34e29f23a92dfb06449d"
  ]
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const tx = await tatum.rpc.getTransactionReceipt('0x2a4811309750a84058d2fd1bd8dd534bf3a34039ff1b34e29f23a92dfb06449d')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
