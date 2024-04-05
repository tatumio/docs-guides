---
title: "txpool_status"
slug: "rpc-ethereum-txpool_status"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, RPC"
  robots: "index"
createdAt: "Tue Mar 19 2024 18:34:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:00:07 GMT+0000 (Coordinated Universal Time)"
---
## Overview

 `txpool_status` method is part of the Ethereum JSON-RPC API, which is used to query the status of the transaction pool (mempool) on an Ethereum node. This method is particularly useful for developers and analysts who need to monitor the current state of pending and queued transactions in the Ethereum network.

## Parameters

`txpool_status` method does not require any parameters.

## Returns

`txpool_status` method returns an object containing two fields; pending and queued:

| Name    | Description                                                                                                                                                                                                           |
| :------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pending | This field indicates the number of transactions that are currently pending in the transaction pool. Pending transactions are those that have been broadcast to the network but have not yet been included in a block. |
| queued  | This field shows the number of transactions that are queued for future execution. These transactions are not yet ready to be included in a block but are waiting for their turn based on their gas price and nonce.   |

The method would return a JSON object with the current status of the transaction pool, including the number of pending and queued transactions.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "txpool_status",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```javascript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const status = await tatum.rpc.txPoolStatus()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
