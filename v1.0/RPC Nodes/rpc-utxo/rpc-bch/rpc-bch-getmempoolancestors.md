---
title: "getmempoolancestors"
slug: "rpc-bch-getmempoolancestors"
category: "6620f7e31ea673003624a8ce"
excerpt: "BCH RPC"
hidden: false
metadata: 
  description: "BCH RPC"
  image: []
  keywords: "bch, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:07 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, BitcoinCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BitcoinCash>({network: Network.BITCOIN_CASH})

const result = await tatum.rpc.getMempoolAncestors("3b3c3bc559deddb0991e1fe9fb6d9f10c1c4a0dab4a18c12e8566b37ad4f06e4")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getmempoolancestors` is a method that returns information about the ancestors of a transaction in the memory pool. This method can be used to analyze the dependency relationships between unconfirmed transactions and to investigate potential transaction issues, such as chains of unconfirmed transactions or transactions that depend on others with a low fee.

### Parameters

- `txid`: The transaction ID (string, required) of the transaction for which you want to retrieve the ancestors.
- `verbose`: Whether to return a JSON object with detailed information about the ancestors (bool, optional, default = false). If `false`, only the transaction IDs of the ancestors are returned.

### Return Object

The return object depends on the `verbose` parameter:

- If `verbose` is `false`, the return object is an array of strings, each representing the transaction ID of an ancestor.
- If `verbose` is `true`, the return object is a JSON object, where the keys are the transaction IDs of the ancestors, and the values are JSON objects containing detailed information about the ancestors.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getmempoolancestors",
  "params": [
    "3b3c3bc559deddb0991e1fe9fb6d9f10c1c4a0dab4a18c12e8566b37ad4f06e4"
  ]
}

```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "result": [
    "1d1c1bc9a9a7d7b0990e0e1f1b5b5a5a5c5b5a5a5a5a5a5a5a5a5a5a5a5a5a5a"
  ]
}

```

{% endcode %}

\\
