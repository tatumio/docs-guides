---
title: "eth_getTransactionByBlockHashAndIndex"
slug: "rpc-ethereum-eth_gettransactionbyblockhashandindex"
excerpt: "Ethereum RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 08:35:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:03:01 GMT+0000 (Coordinated Universal Time)"
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
  - Example: "0x742d35Cc6634C0532925a3b844Bc454e4438f44e"
- `transactionIndex`: (required): The index of the transaction within the specified block. The index is a hexadecimal value.
  - Example: "0x1"

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
    "method": "eth_getTransactionByBlockHashAndIndex",
    "params": [
        "0x2907402477167193008a0cbbaa8073278c48e8b97bf9ed1a2101f6ad2130dbaf",
        "0x1"
    ]
 }'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const tx = await tatum.rpc.getTransactionByBlockHashAndIndex('0x2907402477167193008a0cbbaa8073278c48e8b97bf9ed1a2101f6ad2130dbaf', 1)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
