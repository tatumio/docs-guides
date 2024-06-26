---
title: "getinflationreward"
slug: "rpc-solana-getinflationreward"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:38 GMT+0000 (Coordinated Universal Time)"
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

const addresses = ["Address1", "Address2", "Address3"]
const config = {
    epoch: 2
}

const res = await tatum.rpc.getInflationReward(addresses, config)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getInflationReward` method returns the inflation or staking reward for a list of addresses for a particular epoch on the Solana blockchain.

### Parameters

- An array of addresses (array of strings, optional): These are the addresses to query, as base-58 encoded strings.
- A configuration object (optional): This object can contain the following fields:
  - `commitment` (string, optional): Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`
  - `epoch` (number, optional): An epoch for which the reward occurs. If omitted, the previous epoch will be used.
  - `minContextSlot` (number, optional): The minimum slot that the request can be evaluated at.

### Return Object

The method returns a JSON array where each object represents the reward details for the corresponding address in the input array. Each object has the following fields:

- `epoch`: The epoch for which the reward occurred.
- `effectiveSlot`: The slot in which the rewards are effective.
- `amount`: The reward amount in lamports.
- `postBalance`: The post-balance of the account in lamports.
- `commission` : The vote account commission when the reward was credited.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getInflationReward",
  "params": [
    [
      "6dmNQ5jwLeLk5REvio1JcMshcbvkYMwy26sJ8pbkvStu",
      "BGsqMegLpV6n6Ve146sSX2dTjUMj3M92HnU8BbNRMhF2"
    ],
    {"epoch": 2}
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": [
    {
      "amount": 2500,
      "effectiveSlot": 224,
      "epoch": 2,
      "postBalance": 499999442500
    },
    null
  ],
  "id": 1
}
```
