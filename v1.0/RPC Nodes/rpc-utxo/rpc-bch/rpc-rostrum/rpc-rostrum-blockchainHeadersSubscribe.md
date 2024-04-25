---
title: "blockchainHeadersSubscribe"
slug: "rpc-rostrum-blockchainHeadersSubscribe"
category: "6620f7e31ea673003624a8ce"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, block headers, subscribe, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.headers.subscribe` method allows clients to subscribe to new block headers as they are discovered on the network. This subscription is essential for applications that need real-time updates on blockchain changes without polling the server for the latest block.

## Subscription

Upon subscribing, the client immediately receives the current blockchain tip's header. Following this initial response, the client will receive updates whenever new blocks are found.

## Returns

The response and subsequent updates provide the header in a dictionary format:

| Field   | Description                                 |
| ------- | ------------------------------------------- |
| hex     | The block header as a hexadecimal string.   |
| height  | The height of the block header.             |

## Example Result

```json
{
  "height": 520481,
  "hex": "00000020890208a0ae3a3892aa047c5468725846577cfcd9b512b50000000000000000005dc2b02f2d297a9064ee103036c14d678f9afc7e3d9409cf53fd58b82e938e8ecbeca05a2d2103188ce804c4"
}
```

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.headers.subscribe",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const subscribeHeaders = await tatum.rpc.subscribeBlockHeaders();

subscribeHeaders.on('data', header => {
  console.log('New Block Header:', header);
});

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```

## Note

- **Chain Reorganisations:** Clients should handle potential blockchain reorganizations where the new chain tip may not directly extend the previous one. Clients must be prepared to identify the common ancestor and request any missing headers to maintain a consistent view of the chain state.
- **Multiple Subscriptions:** If a client attempts multiple subscriptions, only the first one is active; additional requests do not result in multiple sets of notifications.
