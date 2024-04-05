---
title: "getinflationrate"
slug: "rpc-solana-getinflationrate"
excerpt: "Solana RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]


### How to Use It

{% code overflow="wrap" lineNumbers="true" %}
```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getInflationRate()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getInflationRate` method is used to retrieve the specific inflation values for the current epoch in the Solana blockchain.

{% embed url="https://codepen.io/tatum-devrel/pen/vYQPXOp" %}

### Parameters

No parameters are required for this method.

### Return Object

The method returns a JSON object with the following fields:

* `total`: Total inflation rate.
* `validator`: Inflation allocated to validators.
* `foundation`: Inflation allocated to the foundation.
* `epoch`: The epoch for which these values are valid.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getInflationRate"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "epoch": 100,
    "foundation": 0.001,
    "total": 0.149,
    "validator": 0.148
  },
  "id": 1
}
```
