---
title: "getblockhash"
slug: "getblock-copy-1"
excerpt: ""
hidden: true
createdAt: "Wed Mar 27 2024 07:23:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 27 2024 07:30:11 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblockhash` is a Dogecoin RPC method that returns the block hash for a specified block height in the local best blockchain. This method is useful for obtaining the hash of a specific block, which can then be used to query for more detailed information about that block using other RPC methods, such as `getblock`.

## Parameters

- `height`: The height of the block for which the hash is requested. This is an integer parameter.
  - Example: `587123`

## Returns

The return object is a string representing the hash of the block at the specified height.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getblockhash",
  "params": [587123],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Dogecoin>({network: Network.DOGECOIN})

const result = await tatum.rpc.getBlockHash(587123)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
