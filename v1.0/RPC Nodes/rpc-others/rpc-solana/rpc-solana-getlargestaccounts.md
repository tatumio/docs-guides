---
title: "getlargestaccounts"
slug: "rpc-solana-getlargestaccounts"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:00 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getLargestAccounts()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getLargestAccounts` method returns the 20 largest accounts by lamport balance. This method may cache results for up to two hours.

### Parameters

- `options` (object, optional): A configuration object containing:
  - `commitment`(string, optional): Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`
  - `filter` (string, optional): Filters the results by account type. Possible values are `circulating` or `nonCirculating`.

### Return Object

The result field will be an `RpcResponse` JSON object with a `value` field equal to an array of objects, each containing:

- `address`: Base-58 encoded address of the account.
- `lamports`: Number of lamports in the account.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getLargestAccounts"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "context": {
      "slot": 54
    },
    "value": [
      {
        "lamports": 999974,
        "address": "99P8ZgtJYe1buSK8JXkvpLh8xPsCFuLYhz9hQFNw93WJ"
      },
      {
        "lamports": 42,
        "address": "uPwWLo16MVehpyWqsLkK3Ka8nLowWvAHbBChqv2FZeL"
      },
      // ...additional accounts...
    ]
  },
  "id": 1
}
```
