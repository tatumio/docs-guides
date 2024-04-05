---
title: "getversion"
slug: "rpc-solana-getversion"
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

const res = await tatum.rpc.getVersion()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getVersion` method is used to retrieve the current Solana version running on the node. This information can be useful for troubleshooting, compatibility checks, or for understanding the node's capabilities based on its version.

{% embed url="https://codepen.io/tatum-devrel/pen/vYQPXVV" %}

### Parameters

This method does not require any parameters.

### Return Object

The result field will be a JSON object with the following fields:

* `solana-core`: The software version of `solana-core`.
* `feature-set`: The unique identifier of the current software's feature set.

### JSON-RPC Request Example

```json
jsonCopy code{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getVersion"
}
```

### JSON-RPC Response Example

```json
jsonCopy code{
  "jsonrpc": "2.0",
  "result": {
    "solana-core": "1.15.0"
  },
  "id": 1
}
```
