---
title: "fee"
slug: "rpc-xrp-fee"
excerpt: "XRP RPC"
hidden: false
metadata: 
  description: "XRP RPC"
  image: []
  keywords: "xrp, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Xrp, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Xrp>({network: Network.XRP})

const res = await tatum.fee()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

### Overview

The `fee` method reports the current state of the open-ledger requirements for the transaction cost. This method requires the FeeEscalation amendment to be enabled. It was introduced in `rippled` version 0.31.0 and updated for public use in version 0.32.0.

The `fee` method is useful for gaining insight into the current transaction costs and the state of the ledger and transaction queue. It can be used by unprivileged users to understand the fees associated with transactions at a particular point in time.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/RwqOqdK",
  "href": "https://codepen.io/tatum-devrel/pen/RwqOqdK",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `fee` method does not take any parameters.

### Return Object

The `fee` method returns an object with the following fields:

- `current_ledger_size`: Number of transactions provisionally included in the in-progress ledger.
- `current_queue_size`: Number of transactions currently queued for the next ledger.
- `drops`: Object with various information about the transaction cost, in drops of XRP.
  - `base_fee`: The transaction cost required for a reference transaction to be included in a ledger under minimum load, represented in drops of XRP.
  - `median_fee`: An approximation of the median transaction cost among transactions included in the previous validated ledger, represented in drops of XRP.
  - `minimum_fee`: The minimum transaction cost for a reference transaction to be queued for a later ledger, represented in drops of XRP.
  - `open_ledger_fee`: The minimum transaction cost that a reference transaction must pay to be included in the current open ledger, represented in drops of XRP.
- `expected_ledger_size`: The approximate number of transactions expected to be included in the current ledger.
- `ledger_current_index`: The Ledger Index of the current open ledger these stats describe.
- `levels`: Object with various information about the transaction cost, in fee levels.
  - `median_level`: The median transaction cost among transactions in the previous validated ledger, represented in fee levels.
  - `minimum_level`: The minimum transaction cost required to be queued for a future ledger, represented in fee levels.
  - `open_ledger_level`: The minimum transaction cost required to be included in the current open ledger, represented in fee levels.
  - `reference_level`: The equivalent of the minimum transaction cost, represented in fee levels.
- `max_queue_size`: The maximum number of transactions that the transaction queue can currently hold.

### JSON-RPC Request Example

```json
{
    "method": "fee",
    "params": [{}]
}
```

### JSON-RPC Response Example

```json
{
    "result": {
        "current_ledger_size": "56",
        "current_queue_size": "11",
        "drops": {
            "base_fee": "10",
            "median_fee": "10000",
            "minimum_fee": "10",
            "open_ledger_fee": "2653937"
        },
        "expected_ledger_size": "55",
        "ledger_current_index": 26575101,
        "levels": {
            "median_level": "256000",
            "minimum_level": "256",
            "open_ledger_level": "67940792",
            "reference_level": "256"
        },
        "max_queue_size": "1100",
        "status": "success"
    }


}
```
