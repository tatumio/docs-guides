---
title: "getmempoolentry"
slug: "rpc-zcash-getmempoolentry"
excerpt: "Zcash RPC"
hidden: false
metadata: 
  description: "Zcash RPC"
  image: []
  keywords: "zcash, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 14:55:13 GMT+0000 (Coordinated Universal Time)"
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

const result = await tatum.rpc.getMempoolEntry("c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getmempoolentry` RPC method allows you to retrieve information about a specific transaction in the memory pool. This method is useful for tracking the status of unconfirmed transactions and for gathering additional details about their current state.

### Parameters

- `txid`: (string, required) The transaction ID of the transaction you want to retrieve information about.

### Return Object

The return object will be an object containing information about the specified transaction.

**Fields**

- `size`: (numeric) The transaction size in bytes.
- `fee`: (numeric) The transaction fee.
- `modifiedfee`: (numeric) The transaction fee with fee deltas used for mining priority.
- `time`: (numeric) The local time the transaction entered the memory pool.
- `height`: (numeric) The block height when the transaction entered the memory pool.
- `descendantcount`: (numeric) The number of descendant transactions.
- `descendantsize`: (numeric) The virtual transaction size of all descendant transactions combined.
- `descendantfees`: (numeric) The total fees of all descendant transactions.
- `ancestorcount`: (numeric) The number of ancestor transactions.
- `ancestorsize`: (numeric) The virtual transaction size of all ancestor transactions combined.
- `ancestorfees`: (numeric) The total fees of all ancestor transactions.
- `wtxid`: (string) The witness transaction ID of the transaction.
- `depends`: (array) An array containing the witness transaction IDs of the transactions this transaction depends on.
- `spentby`: (array) An array containing the witness transaction IDs of the transactions that spend this transaction.
- `bip125-replaceable`: (string) Whether the transaction is BIP125 replaceable. Possible values are "yes", "no", or "unknown".

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getmempoolentry",
  "params": ["c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2"],
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": {
        "vsize": 203,
        "weight": 809,
        "time": 1682502684,
        "height": 787068,
        "descendantcount": 1,
        "descendantsize": 203,
        "ancestorcount": 1,
        "ancestorsize": 203,
        "wtxid": "c00fc27056ad4305dc65a40a78381a6c923b4311a460ceccd81401016f5c8984",
        "fees": {
            "base": 0.00005481,
            "modified": 0.00005481,
            "ancestor": 0.00005481,
            "descendant": 0.00005481
        },
        "depends": [],
        "spentby": [],
        "bip125-replaceable": false,
        "unbroadcast": false
    },
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
