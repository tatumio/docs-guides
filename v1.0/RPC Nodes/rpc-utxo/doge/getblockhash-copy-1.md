---
title: "getblock"
slug: "getblockhash-copy-1"
excerpt: ""
category: 65a9112c408e3a004ae466df
hidden: true
createdAt: "Wed Mar 27 2024 07:26:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 27 2024 07:44:28 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblock` is a Dogecoin RPC method that returns information about a specified block. This method is useful for obtaining block details such as the hash, height, transactions, and other metadata. It can be used for various purposes, including validating transactions, monitoring the blockchain, and analyzing the network.

## Parameters

- `hashOrHeight`: The hash or height of the block to be retrieved.
  - Example: "0000000000000000000ef0e1f703b56f2b0d6724e4eeccf00e4f8d55b9c3c3f6e"
- `verbose`: true for a json object, false for the hex encoded data

## Returns

The returned object varies depending on the verbosity parameter:

If `verbosity` is `0`, the return object is a hex-encoded string of the serialized block.

If `verbosity` is `1` or `2`, the return object is a JSON object containing the following fields:

| Name              | Description                                                                                                          |
| :---------------- | :------------------------------------------------------------------------------------------------------------------- |
| hash              | The hash of the block.                                                                                               |
| confirmations     | The number of confirmations for the block.                                                                           |
| strippedsize      | The block size without witness data.                                                                                 |
| size              | The block size.                                                                                                      |
| weight            | The block weight.                                                                                                    |
| height            | The block height.                                                                                                    |
| version           | The block version.                                                                                                   |
| versionHex        | The block version as a hex string.                                                                                   |
| merkleroot        | The Merkle root of the transactions in the block.                                                                    |
| tx                | An array of transaction identifiers (if `verbosity` is `1`) or detailed transaction objects (if `verbosity` is `2`). |
| time              | The block time in UNIX timestamp format.                                                                             |
| mediantime        | The median block time of the previous 11 blocks.                                                                     |
| nonce             | The block nonce.                                                                                                     |
| bits              | The block difficulty target as a hex string.                                                                         |
| difficulty        | The block difficulty.                                                                                                |
| chainwork         | The total work in the blockchain up to this block.                                                                   |
| nTx               | The number of transactions in the block.                                                                             |
| previousblockhash | The hash of the previous block.                                                                                      |
| nextblockhash     | The hash of the next block (if available).                                                                           |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getblock",
  "params": [
    "000000000000000000013d0a85b72c591500abe074a7f9175c596a194f67b82d",
    1
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBlock('000000000000000000013d0a85b72c591500abe074a7f9175c596a194f67b82d')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
