---
title: "getblockhash"
slug: "rpc-bch-getblockhash"
category: "6620f7e31ea673003624a8ce"
excerpt: "BCH RPC"
hidden: false
metadata: 
  description: "BCH RPC"
  image: []
  keywords: "bch, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, BitcoinCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BitcoinCash>({network: Network.BITCOIN_CASH})

const result = await tatum.rpc.getBlockHash(587123)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getblockhash` is a method that returns the block hash for a specified block height in the local best blockchain. This method is useful for obtaining the hash of a specific block, which can then be used to query for more detailed information about that block using other RPC methods, such as `getblock`.

### Parameters

- `height`: The height of the block for which the hash is requested. This is an integer parameter.

  Example: `587123`

### Return Object

The return object is a string representing the hash of the block at the specified height.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getblockhash",
  "params": [587123],
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": "0000000000000000001b4fedbfb3672963c37f965686c2bf6350e32e77f9941f",
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
