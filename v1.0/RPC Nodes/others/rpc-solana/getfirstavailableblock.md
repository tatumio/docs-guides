---
title: "getfirstavailableblock"
slug: "rpc-solana-getfirstavailableblock"
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

const res = await tatum.rpc.getFirstAvailableBlock()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getFirstAvailableBlock` method returns the slot of the lowest confirmed block that has not been purged from the ledger. This method is useful when you want to start parsing the ledger from the oldest available data, or when you want to check how far back the data in your node goes. This can be critical in scenarios where historical block data is required for backtracking transactions or auditing purposes.

{% embed url="https://codepen.io/tatum-devrel/pen/MWzxjvK" %}

### Parameters

This method does not require any parameters.

### Return Object

The method returns an integer representing the slot of the oldest confirmed block that has not been purged from the ledger.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id":1,
  "method":"getFirstAvailableBlock"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 250000,
  "id": 1
}
```
