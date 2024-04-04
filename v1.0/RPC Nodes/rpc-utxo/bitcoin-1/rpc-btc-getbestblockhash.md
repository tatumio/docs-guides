---
title: "getbestblockhash"
slug: "rpc-btc-getbestblockhash"
excerpt: "Bitcoin RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:41:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:06:23 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getbestblockhash `method is part of the Bitcoin JSON-RPC API, which is used to interact with a Bitcoin node. This method specifically returns the hash of the tip block in the most-work fully-validated chain. The tip block is the most recent block in the longest chain that the node has fully validated. This method is useful for applications that need to know the current state of the blockchain, such as wallets or block explorers.

## Parameters

The method does not accept any parameters, which means it is straightforward to use. It simply returns the hash of the best block, represented as a hexadecimal string. This hash can then be used with other methods to retrieve more information about the block, such as its height, transactions, or confirmations.

## Returns

This method outputs a string representing serialized data for a block hash, encoded in hexadecimal format.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getbestblockhash"
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getBestBlockHash()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
