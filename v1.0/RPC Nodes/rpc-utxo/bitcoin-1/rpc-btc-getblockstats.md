---
title: "getblockstats"
slug: "rpc-btc-getblockstats"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Tue Mar 26 2024 12:59:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 07:56:55 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblockstats` is a Bitcoin RPC method that returns various statistics about a specified block. This method is useful for obtaining detailed information about a block, including the number of transactions, transaction volume, fees, and other related data. The results can be used for data analysis, monitoring, and understanding the state of the Bitcoin network at a specific block height.

## Parameters

- `blockhash`: The hash of the block for which the header information is requested. This is a string parameter.
  - Example: "0000000000000000000ef0e1f703b56f2b0d6724e4eeccf00e4f8d55b9c3c3f6e"
- `verbose`: A boolean parameter that specifies whether to return the header information in a JSON object (true) or as a serialized hex-encoded string (false). Default is true.
  - Example: `True`
  - `hash_or_height`: The block hash or block height for which the statistics are requested. This parameter can be either a string (block hash) or an integer (block height).
    - Example (block hash): "`0000000000000000000f92fb968a8d1a2a9c2039e6e99f8c7a0ee3421a44a7d6`"
    - Example (block height): `685230`
  - `stats` (optional): An array of strings indicating the statistics to be included in the response. If not specified, all available statistics will be returned.
    - Example: ["txs", "avgfee"]

## Returns

The return object is a JSON object containing the requested statistics as key-value pairs. The available statistics are:

| Name           | Description                                                |
| :------------- | :--------------------------------------------------------- |
| avgfee         | The average transaction fee in satoshis.                   |
| avgfeerate     | The average fee rate in satoshis per virtual byte.         |
| avgtxsize      | The average transaction size in bytes.                     |
| blockhash      | The hash of the block.                                     |
| height         | The height of the block in the block chain.                |
| ins            | The total number of inputs in all transactions.            |
| maxfee         | The maximum transaction fee in satoshis.                   |
| maxfeerate     | The maximum fee rate in satoshis per virtual byte.         |
| maxtxsize      | The maximum transaction size in bytes.                     |
| medianfee      | The median transaction fee in satoshis.                    |
| mediantime     | The median time for the block in UNIX timestamp format.    |
| mediantxsize   | The median transaction size in bytes.                      |
| minfee         | The minimum transaction fee in satoshis.                   |
| minfeerate     | The minimum fee rate in satoshis per virtual byte.         |
| mintxsize      | The minimum transaction size in bytes.                     |
| outs           | The total number of outputs in all transactions.           |
| subsidy        | The block reward in satoshis.                              |
| swtotal_size   | The total size of all SegWit transactions in bytes.        |
| swtotal_weight | The total weight of all SegWit transactions.               |
| swtxs          | The total number of SegWit transactions.                   |
| time           | The block timestamp in UNIX format.                        |
| total_size     | The total size of all transactions in bytes.               |
| total_weight   | The total weight of all transactions.                      |
| totalfee       | The total transaction fees in satoshis.                    |
| txs            | The total number of transactions in the block.             |
| utxo_increase  | The increase in the number of unspent transaction outputs. |
| utxo_size_inc  | The increase in the size of the UTXO set.                  |

If `verbose` is set to false, the return object is a serialized hex-encoded string of the block header.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{{
  "jsonrpc": "2.0",
  "method": "getblockstats",
  "params": ["0000000000000000001b4fedbfb3672963c37f965686c2bf6350e32e77f9941f"],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBlockStats("0000000000000000001b4fedbfb3672963c37f965686c2bf6350e32e77f9941f")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
