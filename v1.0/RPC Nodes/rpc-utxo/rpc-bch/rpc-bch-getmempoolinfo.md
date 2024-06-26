---
title: "getmempoolinfo"
slug: "rpc-bch-getmempoolinfo"
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

const result = await tatum.rpc.getMempoolInfo()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getmempoolinfo` RPC method allows you to retrieve general information about the current memory pool. This method is useful for monitoring the state of the memory pool, such as its size, the total transaction fees, and the minimum fee rate required for transactions to be included in the next block.

### Parameters

This method does not require any parameters.

### Return Object

The return object will be an object containing general information about the current memory pool.

**Fields**

- `size`: (numeric) The number of transactions in the memory pool.
- `bytes`: (numeric) The total size of all transactions in the memory pool, in bytes.
- `usage`: (numeric) The total memory usage of the memory pool, in bytes.
- `maxmempool`: (numeric) The maximum memory usage of the memory pool, in bytes.
- `mempoolminfee`: (numeric) The minimum fee rate required for transactions to be included in the memory pool.
- `minrelaytxfee`: (numeric) The minimum fee rate required for transactions to be relayed across the network.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getmempoolinfo",
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": {
        "loaded": true,
        "size": 28338,
        "bytes": 11367166,
        "usage": 63671920,
        "total_fee": 0.73841041,
        "maxmempool": 4000000000,
        "mempoolminfee": 0.00001,
        "minrelaytxfee": 0.00001,
        "incrementalrelayfee": 0.00001,
        "unbroadcastcount": 0,
        "fullrbf": false
    },
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
