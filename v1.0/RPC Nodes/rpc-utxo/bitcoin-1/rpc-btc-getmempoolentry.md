---
title: "getmempoolentry"
slug: "rpc-btc-getmempoolentry"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 06:49:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:05 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `getmempoolentry` RPC method allows you to retrieve information about a specific transaction in the memory pool. This method is useful for tracking the status of unconfirmed transactions and for gathering additional details about their current state.

## Parameters

- `txid`: The transaction ID of the transaction you want to retrieve information about.

## Returns

The return object will be an object containing information about the specified transaction.

| Name               | Description                                                                                      |
| :----------------- | :----------------------------------------------------------------------------------------------- |
| size               | The transaction size in bytes.                                                                   |
| fee                | The transaction fee in BTC.                                                                      |
| modifiedfee        | The transaction fee with fee deltas used for mining priority.                                    |
| time               | The local time the transaction entered the memory pool.                                          |
| height             | The block height when the transaction entered the memory pool.                                   |
| descendantcount    | The number of descendant transactions.                                                           |
| descendantsize     | he virtual transaction size of all descendant transactions combined.                             |
| descendantfees     | The total fees of all descendant transactions.                                                   |
| ancestorcount      | The number of ancestor transactions.                                                             |
| ancestorsize       | he virtual transaction size of all ancestor transactions combined.                               |
| ancestorfees       | The total fees of all ancestor transactions.                                                     |
| wtxid              | The witness transaction ID of the transaction.                                                   |
| depends            | An array containing the witness transaction IDs of the transactions this transaction depends on. |
| spentby            | An array containing the witness transaction IDs of the transactions that spend this transaction. |
| bip125-replaceable | Whether the transaction is BIP125 replaceable. Possible values are "yes", "no", or "unknown".    |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "getmempoolentry",
  "params": ["c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2"],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.getMempoolEntry("c7ad51e46a39d136adc2bb7536a236136cc206ab3c8dabcd4277d4cadcf674f2")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
