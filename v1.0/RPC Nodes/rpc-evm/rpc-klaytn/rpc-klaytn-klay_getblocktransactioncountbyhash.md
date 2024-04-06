---
title: "klay_getblocktransactioncountbyhash"
slug: "rpc-klaytn-klay_getblocktransactioncountbyhash"
excerpt: "Klaytn RPC"
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const response = await tatum.rpc.getBlockTransactionCountByHash('0xcb632c914a18d838113f1e0cbf3ebc58e837c9497113c247001ecd52b212768e')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`klay_getBlockTransactionCountByHash` is a RPC method used to fetch the number of transactions in a block by the block's hash. It is useful when you want to know the total number of transactions included in a specific block and don't want to retrieve the entire block data. This method can be used in various scenarios, such as monitoring the network activity or estimating transaction confirmation times.

### Parameters

This method requires a single parameter:

- **`blockHash`**: The hash of the target block for which the transaction count will be retrieved. It should be a valid 32-byte hex string.

Example of the parameter:

- `blockHash`: `"0xb0ddfcdcc375afce9f365458c5035ca4aaf99f9fe8699522193e16a8718615b6"`

### Return

The method returns a single value:

- `transactionCount`: The total number of transactions included in the specified block. It is returned as a hexadecimal value.

### Examples

#### JSON-RPC request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "klay_getBlockTransactionCountByHash",
  "params": [
    "0xb0ddfcdcc375afce9f365458c5035ca4aaf99f9fe8699522193e16a8718615b6"
  ]
}
```

#### JSON-RPC response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0xa"
}
```

In this example, the block with the hash `"0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"` has a total of 10 transactions (indicated by the hexadecimal value `"0xa"`).
