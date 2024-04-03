---
title: "getmempoolancestors"
slug: "rpc-btc-getmempoolancestors"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:41:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:55:52 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getmempoolancestors` is a Bitcoin RPC method that returns information about the ancestors of a transaction in the memory pool. This method can be used to analyze the dependency relationships between unconfirmed transactions and to investigate potential transaction issues, such as chains of unconfirmed transactions or transactions that depend on others with a low fee.

## Parameters

- `txid`: The transaction ID (string, required) of the transaction for which you want to retrieve the ancestors.
- `verbose`: Whether to return a JSON object with detailed information about the ancestors (bool, optional, default = false). If `false`, only the transaction IDs of the ancestors are returned.

## Returns

The return object depends on the `verbose` parameter:

If `verbose` is `false`, the return object is an array of strings, each representing the transaction ID of an ancestor.

If `verbose` is `true`, the return object is a JSON object, where the keys are the transaction IDs of the ancestors, and the values are JSON objects containing detailed information about the ancestors.

\## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getmempoolancestors",
  "params": [
    "3b3c3bc559deddb0991e1fe9fb6d9f10c1c4a0dab4a18c12e8566b37ad4f06e4"
  ]
}
'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getMempoolAncestors("3b3c3bc559deddb0991e1fe9fb6d9f10c1c4a0dab4a18c12e8566b37ad4f06e4")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
