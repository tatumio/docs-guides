---
title: "eth_getBlockTransactionCountByNumber"
slug: "rpc-ethereum-eth_getblocktransactioncountbynumber"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 07:26:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getBlockTransactionCountByNumber` Ethereum JSON-RPC method allows you to retrieve the number of transactions in a specified block. This method is particularly useful when you need to analyze the transaction activity of a specific block. You can use it to gain insights into network usage, analyze the impact of specific events on the Ethereum network, or monitor transaction congestion in certain blocks.

## Parameters

This method requires a single parameter:

**blockNumber**: The block number for which the transaction count should be retrieved. It should be a hex-encoded value representing the block number.

- Example: block number 0x110E3F0 (17884144)

## Returns

The return object is a hex-encoded value representing the number of transactions in the specified block.

- Example:  0x86 (134 transactions)

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getBlockTransactionCountByNumber",
  "params": ["0x110E3F0"]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const response = await tatum.rpc.getBlockTransactionCountByNumber(17884144)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
