---
title: "getrecentprioritizationfees"
slug: "rpc-solana-getrecentprioritizationfees"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
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

const accounts = ['CxELquR1gPP8wHe33gZ4QxqGB3sZ9RSwsJ2KshVewkFY']

const res = await tatum.rpc.getRecentPrioritizationFees(accounts)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getRecentPrioritizationFees` method returns a list of prioritization fees from recent blocks. This method can be used to determine the fees required to prioritize transactions for faster processing.

{% embed url="<https://codepen.io/Night-Shift-Dev/pen/oNQLZJr"> %}

### Parameters

- `accountAddresses` (array, optional): An array of account addresses (up to a maximum of 128 addresses), as base-58 encoded strings.

  **Note**: If this parameter is provided, the response will reflect a fee to land a transaction locking all of the provided accounts as writable.

### Return Object

The result is an array of objects with the following fields:

- `slot`: The slot in which the fee was observed.
- `prioritizationFee`: The per-compute-unit fee paid by at least one successfully landed transaction, specified in increments of 0.000001 lamports.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0", 
  "id": 1,
  "method": "getRecentPrioritizationFees",
  "params": [
    ["CxELquR1gPP8wHe33gZ4QxqGB3sZ9RSwsJ2KshVewkFY"]
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": [
    {
      "slot": 348125,
      "prioritizationFee": 0
    },
    {
      "slot": 348126,
      "prioritizationFee": 1000
    },
    {
      "slot": 348127,
      "prioritizationFee": 500
    },
    {
      "slot": 348128,
      "prioritizationFee": 0
    },
    {
      "slot": 348129,
      "prioritizationFee": 1234
    }
  ],
  "id": 1
}
```
