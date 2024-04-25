---
title: "blockchainRelayFee"
slug: "rpc-rostrum-blockchainRelayFee"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, relay fee, transaction fee, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.relayfee` method queries the minimum transaction fee required for a low-priority transaction to be accepted into the daemon's memory pool. This fee is crucial for users who need to minimize transaction costs while ensuring their transaction is processed.

## Returns

The method returns the minimum relay fee required in whole coin units (e.g., BTC, not satoshis for Bitcoin) as a floating-point number.

| Field | Description                           |
| ----- | ------------------------------------- |
| fee   | The minimum relay fee in coin units.  |

### Example Results

```json
1e-05
```

```json
0.0
```

## Request Example

```curl /cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.relayfee",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const relayFee = await tatum.rpc.getRelayFee();

console.log('Relay Fee:', relayFee);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```