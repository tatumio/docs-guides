---
title: "gettxout"
slug: "rpc-btc-gettxout"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:07:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:55:35 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `gettxout` RPC method returns details about an unspent transaction output (UTXO). This method can be used to check if a specific transaction output is still unspent and obtain its details such as the value and scriptPubKey.

## Parameters

- `txid`: The transaction ID of the output.
  - Example: "a12345abcdef67890bcdef1234567890abcdef1234567890abcdef1234567890"
- `n`: The index of the output within the transaction (vout).
  - Example: `1`
- `include_mempool`: Whether to include the mempool. Set to false to only check for outputs confirmed in the blockchain.
  - Example: `True`

## Returns

The return object contains the following fields:

[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Description",
    "0-0": "bestblock",
    "0-1": "The hash of the block at the tip of the blockchain.",
    "1-0": "confirmations",
    "1-1": "The number of confirmations for the transaction. -1 if the transaction is not yet confirmed and in the mempool.",
    "2-0": "value",
    "2-1": "The value of the output in BTC.",
    "3-0": "scriptPubKey",
    "3-1": "Information about the output's scriptPubKey:  \n`asm`:  The assembly representation of the script.  \n`hex`: The hex representation of the script.  \n`type`: The type of the script (e.g., pubkeyhash, scripthash).  \n`addresses`: The Bitcoin addresses associated with this output.",
    "4-0": "coinbase",
    "4-1": "Whether the transaction is a coinbase transaction.",
    "5-0": "version",
    "5-1": "The transaction version.",
    "6-0": "height",
    "6-1": "The height of the block containing this output."
  },
  "cols": 2,
  "rows": 7,
  "align": [
    "left",
    "left"
  ]
}
[/block]


## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "gettxout",
  "params": ["c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2", 1],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getTxOut("c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2", 1)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
