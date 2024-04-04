---
title: "txpool_content"
slug: "rpc-ethereum-txpool_content"
excerpt: "Ethereum RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 16:51:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:59:48 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`txpool+content` is specifically designed to return all pending and queued transactions currently in the transaction pool. It's important to note that this method is supported only on Geth, which is a popular Ethereum client.

## Parameters

`txpool_content `method does not accept any parameters. This means you can call it without needing to provide any additional information to get the current state of the transaction pool.

## Returns

The response from the `txpool_content` method is an array of transaction objects. Each transaction object contains several fields that provide detailed information about the `pending` transaction:

| Name                 | Description                                                              |
| :------------------- | :----------------------------------------------------------------------- |
| address              | The address initiating the transaction.                                  |
| nonce                | The nonce of the sending address.                                        |
| blockHash            | The hash of the block where the transaction was included.                |
| blockNumber          | The number of the block where the transaction was included.              |
| from                 | The address of the sender.                                               |
| gas                  | The total amount of gas units used in the transaction.                   |
| gasPrice             | The price of gas for the transaction.                                    |
| maxFeePerGas         | The maximum fee per gas unit that the sender is willing to pay.          |
| maxPriorityFeePerGas | The maximum priority fee per gas unit that the sender is willing to pay. |
| hash                 | The hash of the transaction.                                             |
| input                | The encoded transaction input data.                                      |
| to                   | The address of the recipient.                                            |
| transactionIndex     | The index of the transaction within the block.                           |
| value                | The amount of Ether sent with the transaction.                           |
| type                 | The type of the transaction.                                             |
| accesslist           | The access list for the transaction.                                     |
| chainId              | The ID of the chain where the transaction is valid.                      |
| v                    | The ECDSA recovery id encoded as a hexadecimal format.                   |
| r                    | The ECDSA signature r.                                                   |
| s                    | The ECDSA signature s.                                                   |
| yParity              | Another value used for transaction signing                               |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "txpool_content",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const content = await tatum.rpc.txPoolContent()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
