---
title: "getfeeformessage"
slug: "rpc-solana-getfeeformessage"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:42 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const message = {
  // Message content goes here...
}
const res = await tatum.rpc.getFeeForMessage(message)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getFeeForMessage` method is used to estimate the transaction fee for a given message. This is very useful when you are preparing to send a transaction and you want to estimate the transaction cost. This can be used in situations where you need to validate whether a user has enough funds to cover the transaction fee or to provide an estimate of the cost to the user.

### Parameters

- `message`(string, required): Base-64 encoded Message for which the fee should be estimated.
  - Example: "`AQABAgIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEBAQAA`"
- `options` (object, optional): Configuration object containing the following fields:
  - `commitment` (string, optional): Specifies the confirmation level of data to be fetched.
    - Values: `finalized` `confirmed` `processed`
  - `minContextSlot` (number, optional): The minimum slot that the request can be evaluated at
    - Example: `1000`

### Return Object

The result will be a JSON object with `value` equal to Fee corresponding to the message at the specified blockhash

### JSON-RPC Request Example

```json
{
  "id":1,
  "jsonrpc":"2.0",
  "method":"getFeeForMessage",
  "params":[
    "AQABAgIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEBAQAA",
    {
      "commitment":"processed"
    }
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": { "context": { "slot": 5068 }, "value": 5000 },
  "id": 1
}
```
