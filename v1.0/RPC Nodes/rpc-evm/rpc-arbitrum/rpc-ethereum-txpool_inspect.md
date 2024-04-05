---
title: "txpool_inspect"
slug: "rpc-ethereum-txpool_inspect"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 18:15:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:59:57 GMT+0000 (Coordinated Universal Time)"
---
## Overview

 `txpool_inspect `method is part of the txpool namespace in Ethereum's JSON-RPC API, which provides access to several non-standard RPC methods to inspect the contents of the transaction pool. This method is specifically tailored for developers to quickly see the transactions in the pool and identify any potential issues. It is used to list a textual summary of all the transactions currently pending for inclusion in the next block(s), as well as the ones that are being scheduled for future execution only.

## Parameters

The `txpool_inspect` method does not require any parameters.

## Returns

The response from `txpool_inspect` is an object with two fields: pending and queued. Each of these fields is an associative array, where each entry maps an origin-address to a batch of scheduled transactions. These batches themselves are maps associating nonces with transactions summary strings:

| Name    | Description                                                                                                                                                                                                                                                                             |
| :------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pending | This field contains transactions that are currently pending for inclusion in the next block(s). Each entry in this field maps an origin-address to a batch of transactions. Each transaction batch is a map associating nonces with transactions summary strings.                       |
| queued  | This field contains transactions that are being scheduled for future execution. Similar to the pending field, each entry in this field maps an origin-address to a batch of transactions, with each transaction batch being a map associating nonces with transactions summary strings. |

The transactions summary strings provide details about each transaction, including the recipient address, the amount of ether being sent (in wei), and the gas price and gas limit (in gwei and gas units, respectively).

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "txpool_inspect",
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const inspect = await tatum.rpc.txPoolInspect()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
