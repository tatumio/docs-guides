---
title: "isblockhashvalid"
slug: "rpc-solana-isblockhashvalid"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network, Commitment } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const blockhash = 'J7rBdM6AecPDEZp8aPq5iPSNKVkU5Q76F3oAV4eW5wsW'
const options = {
  commitment: Commitment.Processed,
  minContextSlot: 5
} // optional

const res = await tatum.rpc.isBlockhashValid(blockhash, options)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `isBlockhashValid` method evaluates the validity of a specified blockhash. This can be used to confirm if a blockhash is still valid on the network.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/vYQPKoW",
  "href": "https://codepen.io/tatum-devrel/pen/vYQPKoW",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `blockhash`(string, required): The blockhash of the block to evaluate, as a base-58 encoded string.
  - Example: `'J7rBdM6AecPDEZp8aPq5iPSNKVkU5Q76F3oAV4eW5wsW'`
- `options`: (object, optional) Configuration object containing the following fields:
  - `commitment`: (string, optional) Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`
  - `minContextSlot`: (number, optional) The minimum slot that the request can be evaluated at.
    - Example: `5`

### Return Object

The return object contains a `bool` value indicating if the blockhash is still valid.

### JSON-RPC Request Example

```json
{
  "id": 45,
  "jsonrpc": "2.0",
  "method": "isBlockhashValid",
  "params": [
    "J7rBdM6AecPDEZp8aPq5iPSNKVkU5Q76F3oAV4eW5wsW", {"commitment":"processed"}
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "context": {
      "slot": 2483
    },
    "value": false
  },
  "id": 1
}
```
