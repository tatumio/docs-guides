---
title: "getmempooldescendants"
slug: "rpc-btc-getmempooldescendants"
excerpt: "Bitcoin RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:45:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:55:59 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getmempooldescendants` RPC method allows you to retrieve information about the descendant transactions of a specified transaction in the memory pool. This method is useful for understanding the relationships between unconfirmed transactions and the possible effects of their confirmation on the overall transaction fees and network congestion.

## Parameters

- `txid`: The transaction ID of the transaction for which you want to get its descendants.
- `verbose`: If set to `true`, detailed information about each descendant transaction will be returned, otherwise only the transaction IDs will be returned.

## Returns

The return object depends on the `verbose` parameter:

If `verbose` is `false`, the return object is an array of strings, each representing the transaction ID of a descendant.

If `verbose` is `true`, the return object is a JSON object, where the keys are the transaction IDs of the descendants, and the values are JSON objects containing detailed information about the descendants.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getmempooldescendants",
  "params": [
    "3b3c3bc559deddb0991e1fe9fb6d9f10c1c4a0dab4a18c12e8566b37ad4f06e4"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getMempoolDescendants("3b3c3bc559deddb0991e1fe9fb6d9f10c1c4a0dab4a18c12e8566b37ad4f06e4")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
