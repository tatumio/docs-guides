---
title: "eth_getUncleCountByBlockNumber"
slug: "rpc-ethereum-eth_getunclecountbyblocknumber"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 11:01:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:04:05 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getUncleCountByBlockHash` method is an Ethereum JSON-RPC method that returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the Ethereum network and to analyse the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralisation of the Ethereum network. The inclusion of uncles helps prevent centralisation and ensures the mining process remains competitive.

## Parameters

The ` eth_getUncleCountByBlockHash` method takes one parameter:

- `blockNumber`: The number of the block for which you want to get the uncle count.
  - Example value: 15537345

## Returns

The return object for this method is a hex-encoded integer representing the number of uncles in the specified block.

- Example value: "0x1" (1 uncle)

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getUncleCountByBlockNumber",
  "params": [
    "0xED14C1"
  ]
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.getUncleCountByBlockNumber(15537345)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
