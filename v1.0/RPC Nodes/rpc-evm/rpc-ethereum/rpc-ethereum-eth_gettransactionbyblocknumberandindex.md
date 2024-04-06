---
title: "eth_getTransactionByBlockNumberAndIndex"
slug: "rpc-ethereum-eth_gettransactionbyblocknumberandindex"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 08:43:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 07:56:49 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getTransactionByBlockHashAndIndex` is an Ethereum JSON-RPC method that allows you to fetch the transaction details based on the block hash and the index of the transaction within that block. This method can be useful when you want to retrieve transaction details for a specific transaction without knowing its transaction hash.

## Usecase

Use cases for this method may include:

- Inspecting transaction details for debugging purposes
- Gathering data for transaction analysis
- Fetching transaction information for specific blocks in a block explorer application

## Parameters

The `eth_getTransactionByBlockHashAndIndex` method accepts two parameters:

- `blockHash` (required): The hash of the block containing the transaction.
  - Example: 10123321
- `transactionIndex`: (required): The index of the transaction within the specified block. The index is a hexadecimal value.
  - Example: 0

## Returns

The method returns a JSON object containing the following fields:

| Name             | Description                                                                                  |
| :--------------- | :------------------------------------------------------------------------------------------- |
| hash             | The transaction hash as a 32-byte hex string.                                                |
| nonce            | The number of transactions made by the sender prior to this one.                             |
| blockHash        | The hash of the block in which this transaction is included.                                 |
| blockNumber      | The block number in which this transaction is included.                                      |
| transactionIndex | The index of the transaction within the block.                                               |
| from             | The address of the sender.                                                                   |
| to               | The address of the recipient. `null ` if the transaction is a contract creation transaction. |
| value            | The value transferred in wei.                                                                |
| gasPrice         | The gas price provided by the sender in wei.                                                 |
| gas              | The gas limit provided by the sender.                                                        |
| input            | The data sent along with the transaction.                                                    |

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "jsonrpc": "2.0",
    "id": 1,
    "method": "eth_getTransactionByBlockNumberAndIndex",
    "params": [
        10123321,
        0
    ]
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const tx = await tatum.rpc.getTransactionByBlockNumberAndIndex(10123321, 0)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
