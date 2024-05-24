---
title: "blockchainHeadersTip"
slug: "rpc-rostrum-blockchainHeadersTip"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee9ea8e770036f3c937"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, latest block header, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.headers.tip` method retrieves the latest block header, known as the tip of the blockchain, for the Bitcoin Cash network via Rostrum Electrum. This method provides a snapshot of the most recent block header without subscribing to continuous header updates.

## Returns

The method returns a dictionary with the latest block header information:

| Field  | Description                                         |
| ------ | --------------------------------------------------- |
| hex    | The block header as a hexadecimal string.           |
| height | The height of the block, represented as an integer. |

## Example Result

```json
{
  "hex": "0000...8ce804c4",
  "height": 520481
}

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.headers.tip",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const tipHeader = await tatum.rpc.getHeadersTip();

console.log(tipHeader);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
