---
title: "getstakeactivation"
slug: "rpc-solana-getstakeactivation"
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



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const pubkey = "CYRJWqiSjLitBAcRxPvWpgX3s5TvmN2SuRY3eEYypFvT"
const config = {
    epoch: 4
}

const res = await tatum.rpc.getStakeActivation(pubkey, config)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getStakeActivation` method returns epoch activation information for a stake account on the Solana blockchain.

### Parameters

This method takes the following parameters:

- A string (required): This is the pubkey of the stake account to query, as a base-58 encoded string.
  - Example: `"CYRJWqiSjLitBAcRxPvWpgX3s5TvmN2SuRY3eEYypFvT"`
- A configuration object (optional): This object can contain the following fields:
  - `commitment` (string, optional): Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`
  - `minContextSlot` (number, optional): The minimum slot that the request can be evaluated at.
  - `epoch` (number, optional): The epoch for which to calculate activation details. If this parameter is not provided, it defaults to the current epoch.

### Return Object

The method returns a JSON object that includes the following fields:

- `state`: The activation state of the stake account. This can be 'active', 'inactive', 'activating', or 'deactivating'.
- `active`: The stake that is active during the epoch.
- `inactive`: The stake that is inactive during the epoch.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getStakeActivation",
  "params": [
    "CYRJWqiSjLitBAcRxPvWpgX3s5TvmN2SuRY3eEYypFvT",
    {
      "epoch": 4
    }
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "active": 124429280,
    "inactive": 73287840,
    "state": "activating"
  },
  "id": 1
}
```
