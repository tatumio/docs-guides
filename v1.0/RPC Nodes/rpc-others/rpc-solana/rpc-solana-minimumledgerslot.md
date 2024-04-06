---
title: "minimumledgerslot"
slug: "rpc-solana-minimumledgerslot"
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

{% code overflow="wrap" lineNumbers="true" %}

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.minimumLedgerSlot()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `minimumLedgerSlot` method returns the lowest slot number that the node has information about in its ledger. This is useful when tracking the node's ledger history, such as for auditing, ledger analysis, or understanding the node's data retention policies.

Note: This value may change over time if the node is configured to purge older ledger data, meaning that older data may no longer be accessible.

{% embed url="<https://codepen.io/tatum-devrel/pen/QWJoKBw"> %}

### Parameters

This method does not require any parameters.

### Return Object

The method returns an integer that represents the minimum ledger slot number.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id":1,
  "method":"minimumLedgerSlot"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 1234,
  "id": 1
}
```
