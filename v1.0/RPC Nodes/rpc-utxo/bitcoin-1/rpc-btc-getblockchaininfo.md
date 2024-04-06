---
title: "getblockchaininfo"
slug: "rpc-btc-getblockchaininfo"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Tue Mar 26 2024 12:36:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblockchaininfo`  is a Bitcoin RPC method that provides general information about the current state of the blockchain. This method is useful for obtaining an overview of the blockchain, including the best block hash, chain height, difficulty, and network protocol version. It can be used for various purposes, such as monitoring the blockchain, tracking network upgrades, and assessing the current mining difficulty.

## Returns

The return object is a JSON object containing the following fields:

| Name                 | Description                                                                                       |
| :------------------- | :------------------------------------------------------------------------------------------------ |
| chain                | The current network name (e.g., "main", "test", or "regtest").                                    |
| blocks               | The number of blocks in the local best block chain.                                               |
| headers              | The number of headers the local node has validated.                                               |
| bestblockhash        | The hash of the best (tip) block.                                                                 |
| difficulty           | The current mining difficulty.                                                                    |
| mediantime           | The median block time of the last 11 blocks in UNIX timestamp format.                             |
| verificationprogress | The estimate of the verification progress of the local node as a percentage.                      |
| initialblockdownload | A boolean indicating whether the node is in the initial block download mode.                      |
| chainwork            | The total work in the blockchain up to the best block.                                            |
| size_on_disk         | The estimated size of the block and undo files on disk.                                           |
| pruned               | A boolean indicating whether the block chain is pruned.                                           |
| pruneheight          | The lowest-height complete block stored if the node is pruned (only present if `pruned` is true). |
| softforks            | An array of objects, each containing information about a softfork.                                |
| bip9_softforks       | An object containing the status of BIP9 softforks in the blockchain.                              |
| warnings             | Any network and blockchain warnings.                                                              |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getblockchaininfo"
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBlockChainInfo()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
