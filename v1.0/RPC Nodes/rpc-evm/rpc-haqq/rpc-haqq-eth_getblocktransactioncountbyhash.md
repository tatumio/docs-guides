---
title: "eth_getblocktransactioncountbyhash"
slug: "rpc-haqq-eth_getblocktransactioncountbyhash"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:00 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ}

const response = await tatum.rpc.getBlockTransactionCountByHash('0xF07355D9A980F61915B53A74AFCDB89598E54EFCD9DF5A9935D16BC1DC4CFA8F')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_getBlockTransactionCountByHash` is an Haqq RPC method used to fetch the number of transactions in a block by the block's hash. It is useful when you want to know the total number of transactions included in a specific block and don't want to retrieve the entire block data. This method can be used in various scenarios, such as monitoring the network activity or estimating transaction confirmation times.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/wvQVbyY",
  "href": "https://codepen.io/tatum-devrel/pen/wvQVbyY",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

This method requires a single parameter:

- **`blockHash`**: The hash of the target block for which the transaction count will be retrieved. It should be a valid 32-byte hex string.

Example of the parameter:

- `blockHash`: `"0xF07355D9A980F61915B53A74AFCDB89598E54EFCD9DF5A9935D16BC1DC4CFA8F"`

### Return

The method returns a single value:

- `transactionCount`: The total number of transactions included in the specified block. It is returned as a hexadecimal value.

### Examples

#### JSON-RPC request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getBlockTransactionCountByHash",
  "params": [
    "0xF07355D9A980F61915B53A74AFCDB89598E54EFCD9DF5A9935D16BC1DC4CFA8F"
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

In this example, the block with the hash `"0xF07355D9A980F61915B53A74AFCDB89598E54EFCD9DF5A9935D16BC1DC4CFA8F"` has a total of 10 transactions (indicated by the hexadecimal value `"0xa"`).
