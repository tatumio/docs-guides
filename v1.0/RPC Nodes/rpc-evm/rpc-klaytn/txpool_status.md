---
title: "txpool_status"
slug: "rpc-klaytn-txpool_status"
excerpt: "Klaytn RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

{% tabs %}
{% tab title="TypeScript/JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const status = await tatum.rpc.txPoolStatus()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `txpool_status` method returns statistics about the current state of the transaction pool. The transaction pool is a queue of pending transactions waiting to be included in the next block by miners.

This method can be useful for monitoring the health of the network and analyzing the behavior of the miners. It can also be used to estimate the time it will take for a transaction to be processed, as well as to determine the gas price necessary to ensure prompt inclusion of a transaction in the next block.

### Parameters

This method does not take any parameters.

### Return Object

The `txpool_status` method returns an object with the following fields:

* **`pending`**: Number of pending transactions in the pool
* **`queued`**: Number of queued transactions in the pool

### Example Request

```json
{
  "jsonrpc":"2.0",
  "method":"txpool_status",
  "params":[],
  "id":1
}
```

### Example Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "pending": 4,
    "queued": 10
  }
}
```

In this example response, there are currently 4 pending transactions and 10 queued transactions waiting to be processed by miners.
