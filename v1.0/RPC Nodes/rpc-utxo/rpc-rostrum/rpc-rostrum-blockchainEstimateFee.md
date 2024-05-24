---
title: "blockchainEstimateFee"
slug: "rpc-rostrum-blockchainEstimateFee"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee9ea8e770036f3c937"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, estimate fee, transaction fee, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.estimatefee` method provides an estimation of the transaction fee per kilobyte needed for a transaction to be included in a block within a specified number of blocks. This is useful for applications that need to dynamically calculate transaction fees based on current network conditions.

## Parameters

| Name    | Type    | Required | Description                                                      |
| ------- | ------- | -------- | ---------------------------------------------------------------- |
| number  | integer | Yes      | The number of blocks within which the transaction should confirm. |

## Returns

The method returns the estimated fee in coin units per kilobyte. If the server cannot estimate the fee due to insufficient data, it returns -1.

| Field   | Description                                                                      |
| ------- | -------------------------------------------------------------------------------- |
| fee     | The estimated transaction fee per kilobyte or -1 if an estimate cannot be made.  |

## Example Result

```json
0.00101079
```

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.estimatefee",
    "params": [2],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const feeEstimate = await tatum.rpc.estimateFee(2);

console.log('Estimated Fee:', feeEstimate);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```