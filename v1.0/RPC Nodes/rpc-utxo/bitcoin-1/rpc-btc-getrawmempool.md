---
title: "getrawmempool"
slug: "rpc-btc-getrawmempool"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 07:01:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:56:16 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getrawmempool` RPC method provides information on the transactions currently in the memory pool. This method is useful for getting details about unconfirmed transactions that have not yet been included in a block.

## Parameters

`verbose`: Set to true to receive a detailed JSON object for each transaction in the memory pool. Set to false to receive a simple array of transaction IDs.

- Example: `verbose`: `true`

## Returns

The return object will depend on the value of the verbose parameter.

If `verbose` is set to `false`, the method will return an array of transaction IDs.

If `verbose` is set to `true`, the method will return an object with transaction IDs as keys and detailed transaction information as values.

Fields (when verbose is true): 

| Name            | Description                                                                    |
| :-------------- | :----------------------------------------------------------------------------- |
| size            | The transaction size in bytes.                                                 |
| fee             | The transaction fee in BTC.                                                    |
| modifiedfee     | The transaction fee with descendants in BTC.                                   |
| time            | The local time when the transaction entered the memory pool.                   |
| height          | The block height when the transaction entered the memory pool.                 |
| descendantcount | The number of descendant transactions in the memory pool.                      |
| descendantsize  | The total size of all descendant transactions in the memory pool, in bytes.    |
| descendantfees  | The total fees of all descendant transactions in the memory pool, in satoshis. |
| ancestorcount   | The number of ancestor transactions in the memory pool.                        |
| ancestorsize    | The total size of all ancestor transactions in the memory pool, in bytes.      |
| ancestorfees    | The total fees of all ancestor transactions in the memory pool, in satoshis.   |
| wtxid           | The transaction witness ID.                                                    |
| depends         | An array of unconfirmed transactions that this transaction depends on.         |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getrawmempool",
  "params": [true],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getRawMemPool(true)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
