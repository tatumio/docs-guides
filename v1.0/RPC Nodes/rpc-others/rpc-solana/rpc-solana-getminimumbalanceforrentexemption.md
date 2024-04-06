---
title: "getminimumbalanceforrentexemption"
slug: "rpc-solana-getminimumbalanceforrentexemption"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getMinimumBalanceForRentExemption(50)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `getMinimumBalanceForRentExemption` method returns the minimum balance required to make an account rent exempt. This is useful when setting up a new account or assessing the cost of maintaining an account in a rent-free state.

{% embed url="<https://codepen.io/tatum-devrel/pen/xxQBEMp"> %}

### Parameters

- `dataSize` (number, optional): The account's data length.
- `options` (object, optional): A configuration object containing:
  - `commitment`(string, optional): Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`

### Return Object

The result field will be a number indicating the minimum lamports required in the account to remain rent free.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getMinimumBalanceForRentExemption",
  "params": [50]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 500,
  "id": 1
}
```
