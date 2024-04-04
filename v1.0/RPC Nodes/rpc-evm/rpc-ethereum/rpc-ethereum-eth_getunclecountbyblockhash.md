---
title: "eth_getUncleCountByBlockHash"
slug: "rpc-ethereum-eth_getunclecountbyblockhash"
excerpt: "Ethereum RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 10:58:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:03:55 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getUncleCountByBlockHash` method is an Ethereum JSON-RPC method that returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the Ethereum network and to analyse the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralisation of the Ethereum network. The inclusion of uncles helps prevent centralisation and ensures the mining process remains competitive.

## Parameters

The `eth_getUncleCountByBlockHash` method takes one parameter:

- `blockHash`: The hash of the block for which you want to get the uncle count.
  - Example: "0x827d30e914a3adeefabb9d53f70da87e6e0ed3d02a72e7d9ae9bfd1bf123c7a3"

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
  "method": "eth_getUncleCountByBlockHash",
  "params": [
    "0x827d30e914a3adeefabb9d53f70da87e6e0ed3d02a72e7d9ae9bfd1bf123c7a3"
  ]
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.getUncleCountByBlockHash('0x827d30e914a3adeefabb9d53f70da87e6e0ed3d02a72e7d9ae9bfd1bf123c7a3')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
