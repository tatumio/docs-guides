---
title: "txpool_inspect"
slug: "rpc-cronos-txpool_inspect"
excerpt: "Cronos RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
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

import { TatumSDK, Cronos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Cronos>({network: Network.CRONOS})

const inspect = await tatum.rpc.txPoolInspect()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `txpool_inspect` method is a JSON-RPC method used to inspect the current transaction pool of a running node. The method allows you to view all pending transactions and their details, including transaction hashes, gas prices, and transaction data. This method is useful for developers who want to monitor the status of pending transactions or debug transaction-related issues.

### Parameters

The `txpool_inspect` method takes one optional parameter:

* **`include`**: A string specifying the type of transactions to include in the response. Possible values are **`pending`** (default) and **`queued`**.

### Return Object

The `txpool_inspect` method returns an object with the following fields:

* **`pending`**: An array of transaction objects, with textual data
* **`queued`**: An array of transaction objects, with textual data