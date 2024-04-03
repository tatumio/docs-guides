---
title: "getblockhash"
slug: "rpc-btc-getblockhash"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Mon Mar 25 2024 13:04:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:06:42 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblockhash` method is part of the Bitcoin JSON-RPC API, which is used to interact with the Bitcoin blockchain. This method is specifically designed to return the hash of a block given its height in the blockchain. The height is a numeric value that represents the position of the block in the blockchain, starting from 0 for the genesis block.

## Parameters

- `height`: This is a required parameter. It is a numeric value that specifies the height index of the block in the blockchain. The height index is used to identify a block uniquely within the blockchain.

## Returns

- `result`: The method returns the hash of the block corresponding to the provided height. This hash is a unique identifier for the block in the Bitcoin blockchain.
- `error`: If there is an error in processing the request, the method will return an error message detailing the issue.

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

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBlockHash(587123)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
