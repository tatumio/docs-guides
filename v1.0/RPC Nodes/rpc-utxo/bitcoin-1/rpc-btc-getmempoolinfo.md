---
title: "getmempoolinfo"
slug: "rpc-btc-getmempoolinfo"
excerpt: "Bitcoin RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:56:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:56:10 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getmempoolinfo` RPC method allows you to retrieve general information about the current memory pool. This method is useful for monitoring the state of the memory pool, such as its size, the total transaction fees, and the minimum fee rate required for transactions to be included in the next block.

## Parameters

This method does not require any parameters.

## Returns

The return object will be an object containing general information about the current memory pool.

| Name          | Description                                                                                   |
| :------------ | :-------------------------------------------------------------------------------------------- |
| size          | The number of transactions in the memory pool.                                                |
| bytes         | The total size of all transactions in the memory pool, in bytes.                              |
| usage         | The total memory usage of the memory pool, in bytes.                                          |
| maxmempool    | The maximum memory usage of the memory pool, in bytes.                                        |
| mempoolminfee | The minimum fee rate (in BTC/kB) required for transactions to be included in the memory pool. |
| minrelaytxfee | The minimum fee rate (in BTC/kB) required for transactions to be relayed across the network.  |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getmempoolinfo",
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getMempoolInfo()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
