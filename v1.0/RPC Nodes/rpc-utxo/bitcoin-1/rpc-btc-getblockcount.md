---
title: "getblockcount"
slug: "rpc-btc-getblockcount"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  description: "Bitcoin RPC"
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Tue Mar 26 2024 12:10:23 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 07:56:47 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getblockcount` is a Bitcoin RPC method that returns the number of blocks in the local best blockchain. This method is useful for obtaining the current height of the blockchain, which can be used for various purposes, such as monitoring the blockchain, determining the number of confirmations for a transaction, or assessing the progress of the blockchain's growth.

## Returns

The returned object is an integer representing the number of blocks in the local best blockchain.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getblockcount"
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBlockCount()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
