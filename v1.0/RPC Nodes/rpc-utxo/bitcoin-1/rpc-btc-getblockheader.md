---
title: "getblockheader"
slug: "rpc-btc-getblockheader"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Tue Mar 26 2024 12:49:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:55:10 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblockheader`  is a Bitcoin RPC method that returns information about a specified block header. This method is useful for obtaining a high-level view of a specific block, including its hash, previous block hash, merkle root, timestamp, difficulty target, and nonce, without having to fetch the entire block's contents.

## Parameters

- `blockhash`: The hash of the block for which the header information is requested. This is a string parameter.
  - Example: "0000000000000000000ef0e1f703b56f2b0d6724e4eeccf00e4f8d55b9c3c3f6e"
- `verbose`: A boolean parameter that specifies whether to return the header information in a JSON object (true) or as a serialized hex-encoded string (false). Default is true.
  - Example: `True`

## Returns

If `verbose` is set to true (default), the return object is a JSON object containing the following fields:

| Name              | Description                                                           |
| :---------------- | :-------------------------------------------------------------------- |
| hash              | The hash of the block.                                                |
| confirmations     | The number of confirmations for the block.                            |
| height            | The height of the block in the block chain.                           |
| version           | The block version.                                                    |
| versionHex        | The block version formatted as a hex string.                          |
| merkleroot        | The merkle root of the block.                                         |
| time              | The block timestamp in UNIX format.                                   |
| mediantime        | The median block time of the last 11 blocks in UNIX timestamp format. |
| nonce             | The nonce value for the block.                                        |
| bits              | The encoded difficulty target for the block.                          |
| difficulty        | The actual difficulty target for the block as a decimal number.       |
| chainwork         | The total work in the block chain up to this block.                   |
| nTx               | The number of transactions in the block.                              |
| previousblockhash | The hash of the previous block.                                       |
| nextblockhash     | The hash of the next block (only present if there is a next block).   |

If `verbose` is set to false, the return object is a serialized hex-encoded string of the block header.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getblockheader",
  "params": ["0000000000000000001b4fedbfb3672963c37f965686c2bf6350e32e77f9941f", true],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBlockHeader("0000000000000000001b4fedbfb3672963c37f965686c2bf6350e32e77f9941f", true)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
