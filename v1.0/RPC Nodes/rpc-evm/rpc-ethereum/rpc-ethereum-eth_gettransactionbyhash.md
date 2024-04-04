---
title: "eth_getTransactionByHash"
slug: "rpc-ethereum-eth_gettransactionbyhash"
excerpt: "Ethereum RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 08:47:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:03:29 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getTransactionByHash` is an Ethereum JSON-RPC method that allows you to query transaction details based on its hash. This method is useful when you want to retrieve information about a specific transaction, such as its sender, receiver, value, and more. Common use cases include tracking transaction status, monitoring incoming transactions, or analyzing historical transaction data.

## Parameters

The `eth_getTransactionByHash` method takes one parameter:

- `transactionHash`:  The hash of the transaction you want to retrieve. This should be a 32-byte hash string with a 0x prefix.
  - Example: 0x97696c2014695e851d85a344cbbc6ae8ab9d386de05cb0230fe50b91c044639b

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
  "method": "eth_getTransactionByHash",
  "params": ["0x97696c2014695e851d85a344cbbc6ae8ab9d386de05cb0230fe50b91c044639b"],
  "id": 1
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const tx = await tatum.rpc.getTransactionByHash('0x97696c2014695e851d85a344cbbc6ae8ab9d386de05cb0230fe50b91c044639b')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
