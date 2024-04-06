---
title: "getdifficulty"
slug: "rpc-btc-getdifficulty"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:03:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 07:57:18 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getdifficulty` is a Bitcoin RPC method that returns the current mining difficulty. The mining difficulty is a measure of how difficult it is to find a new block compared to the easiest it can ever be. This method can be used to monitor the mining difficulty, which adjusts every 2016 blocks to maintain a consistent block creation rate of approximately 10 minutes per block.

## Returns

A return object is a floating-point number that represents the current mining difficulty.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getdifficulty",
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getDifficulty()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
