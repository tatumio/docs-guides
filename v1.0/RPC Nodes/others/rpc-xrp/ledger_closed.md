---
title: "ledger_closed"
slug: "rpc-xrp-ledger_closed"
excerpt: "XRP RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "XRP RPC"
  image: []
  keywords: "xrp, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Xrp, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Xrp>({network: Network.XRP})

const res = await tatum.rpc.ledgerClosed()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

### Overview

The `ledger_closed` method is used to fetch the unique identifiers of the most recently closed ledger. Note that the ledger might not be validated and immutable yet, so use this method when you need information about the latest ledger and not necessarily the final state.

{% embed url="https://codepen.io/tatum-devrel/pen/MWzRPbb" %}

### Parameters

This method does not require any parameters.

### Return Object

The `ledger_closed` method returns an object with the following fields:

* `ledger_hash` (String): The unique hash of this ledger version, in hexadecimal.
* `ledger_index` (Unsigned Integer): The ledger index of this ledger version.

### JSON-RPC Request Example

Here's an example of the `ledger_closed` method request:

```json
{
   "id": 2,
   "command": "ledger_closed"
}
```

### JSON-RPC Response Example

Here's an example of a successful response:

```json
{
  "id": 1,
  "status": "success",
  "type": "response",
  "result": {
    "ledger_hash": "17ACB57A0F73B5160713E81FE72B2AC9F6064541004E272BD09F257D57C30C02",
    "ledger_index": 6643099
  }
}
```

In this response, `ledger_hash` is the unique identifier of the ledger, and `ledger_index` is the index number of this ledger version.
