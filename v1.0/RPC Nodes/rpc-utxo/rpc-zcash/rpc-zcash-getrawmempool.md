---
title: "getrawmempool"
slug: "rpc-zcash-getrawmempool"
excerpt: "Zcash RPC"
hidden: false
metadata: 
  description: "Zcash RPC"
  image: []
  keywords: "zcash, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 14:55:14 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, ZCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<ZCash>({network: Network.ZCASH})

const result = await tatum.rpc.getRawMemPool(true)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getrawmempool` RPC method provides information on the transactions currently in the memory pool. This method is useful for getting details about unconfirmed transactions that have not yet been included in a block.

### Parameters

- `verbose` (boolean, optional, default=false): Set to `true` to receive a detailed JSON object for each transaction in the memory pool. Set to `false` to receive a simple array of transaction IDs.

**Example**

- `verbose`: `true`

### Return Object

The return object will depend on the value of the `verbose` parameter.

- If `verbose` is set to `false`, the method will return an array of transaction IDs.
- If `verbose` is set to `true`, the method will return an object with transaction IDs as keys and detailed transaction information as values.

**Fields (when verbose is true)**

- `size`: (numeric) The transaction size in bytes.
- `fee`: (numeric) The transaction fee.
- `modifiedfee`: (numeric) The transaction fee with descendants.
- `time`: (numeric) The local time when the transaction entered the memory pool.
- `height`: (numeric) The block height when the transaction entered the memory pool.
- `descendantcount`: (numeric) The number of descendant transactions in the memory pool.
- `descendantsize`: (numeric) The total size of all descendant transactions in the memory pool, in bytes.
- `descendantfees`: (numeric) The total fees of all descendant transactions in the memory pool, in satoshis.
- `ancestorcount`: (numeric) The number of ancestor transactions in the memory pool.
- `ancestorsize`: (numeric) The total size of all ancestor transactions in the memory pool, in bytes.
- `ancestorfees`: (numeric) The total fees of all ancestor transactions in the memory pool, in satoshis.
- `wtxid`: (string) The transaction witness ID.
- `depends`: (array) An array of unconfirmed transactions that this transaction depends on.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getrawmempool",
  "params": [true],
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
"result": {
        "940352ce2be1f34f2a88ed32ba9bfcd01d4d8cbd68b79c88ce97115d1d8da8ce": {
            "vsize": 151,
            "weight": 602,
            "time": 1682395086,
            "height": 787063,
            "descendantcount": 1,
            "descendantsize": 151,
            "ancestorcount": 2,
            "ancestorsize": 1334,
            "wtxid": "a824488001981d130794c9982afb0aeab3cdef25b5b9505b50ded0724308e976",
            "fees": {
                "base": 0.00000307,
                "modified": 0.00000307,
                "ancestor": 0.00002679,
                "descendant": 0.00000307
            },
            "depends": [
                "e17275ca632c7083ce2f36415d4a52eda928901624e90f104c51696bc3338379"
            ],
            "spentby": [],
            "bip125-replaceable": true,
            "unbroadcast": false
        }
    },
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
