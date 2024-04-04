---
title: "gettxoutproof"
slug: "rpc-btc-gettxoutproof"
excerpt: "Bitcoin RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:34:41 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:55:41 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `gettxoutproof` RPC method returns a hex-encoded proof that the specified transaction(s) were included in a block. This method can be used to provide proof of inclusion for one or more transactions in the blockchain.

## Parameters

- `txids`: An array of transaction IDs to create a proof for.
  - txids: ["c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2"]
- `blockhash`: The hash of the block that contains the transactions. If not provided, the method will search for the transactions in the most recent blocks.
  - Example: "00000000000000000004c6125026f00b76e7b762e645a0b0b7ecfa7a7dafdba2"

## Returns

`hex`: The hex-encoded proof of the transaction(s) inclusion in the block.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "gettxoutproof",
  "params": [["c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2"], "00000000000000000004c6125026f00b76e7b762e645a0b0b7ecfa7a7dafdba2"],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getTxOutProof(["c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2"], "00000000000000000004c6125026f00b76e7b762e645a0b0b7ecfa7a7dafdba2")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
