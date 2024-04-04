---
title: "getchaintips"
slug: "rpc-btc-getchaintips"
excerpt: "Bitcoin RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Tue Mar 26 2024 13:12:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:55:24 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getchaintips` is a Bitcoin RPC method that returns information about all known tips in the block tree. This method is useful for identifying and analyzing potential forks or alternative chains in the Bitcoin network. It can be used to monitor the health and status of the network or to investigate discrepancies in blockchain data.

## Returns

The return object is an array of JSON objects, with each object representing a chain tip. The fields in each object are:

[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Description",
    "0-0": "height",
    "0-1": "The height of the chain tip in the block chain.",
    "1-0": "hash",
    "1-1": "The hash of the block corresponding to the chain tip.",
    "2-0": "branchlen",
    "2-1": "The length of the branch connected to the main chain.",
    "3-0": "status",
    "3-1": "The status of the chain tip, which can be one of the following values:  \n`active`: The tip is part of the main chain.  \n`valid-fork`: The tip is part of a valid but inactive fork  \n`valid-headers`: The tip is part of a valid fork but with incomplete block data.  \n`headers-only`: The tip is a fork with valid headers but incomplete block data and an invalid parent block.  \n`invalid`: The tip is part of an invalid fork.  \n`unknown`: The tip has an unknown validation state."
  },
  "cols": 2,
  "rows": 4,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getchaintips",
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getChainTips()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
