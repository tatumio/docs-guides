---
title: "estimatesmartfee"
slug: "rpc-litecoin-estimatesmartfee"
excerpt: "Litecoin RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Litecoin RPC"
  image: []
  keywords: "litecoin, rpc"
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

import { TatumSDK, Litecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Litecoin>({network: Network.LITECOIN})

const result = await tatum.rpc.estimateSmartFee(20)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `estimatesmartfee` method provides an estimated fee rate (in BTC/kB) for a transaction to be confirmed within a certain number of blocks. The estimation is based on recent transactions in the Litecoin network.

This method can be useful for users or applications trying to decide on an appropriate fee for their transactions, based on the desired confirmation speed.

{% embed url="https://codepen.io/tatum-devrel/pen/NWEJxLW" %}

### Parameters

The `estimatesmartfee` method accepts the following parameters:

* `conf_target`: An integer representing the number of blocks within which the transaction should be confirmed.
* `estimate_mode` _(optional)_: A string that determines the estimation mode. Possible values are "UNSET", "ECONOMICAL", and "CONSERVATIVE". Default is "CONSERVATIVE".

### Return Object

The `estimatesmartfee` method returns an object containing the following fields:

* `feerate`: A decimal number representing the estimated fee rate/kB.
* `blocks`: An integer representing the number of blocks within which the transaction is expected to be confirmed.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "jsonrpc": "2.0",
  "method": "estimatesmartfee",
  "params": [20],
  "id": 1
}
```
{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "result": {
        "feerate": 0.00017258,
        "blocks": 20
    },
    "error": null,
    "id": 1
}
```
{% endcode %}

\
