---
title: "blockchainBlockGet"
slug: "rpc-rostrum-blockchainBlockGet"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, get block, full block, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.block.get` method allows retrieving a full block based on its hash or height within the Bitcoin Cash blockchain via Rostrum Electrum. This is particularly useful for obtaining detailed block information, including transactions within the block.

## Parameters

| Name           | Type            | Required | Description                                      |
| -------------- | --------------- | -------- | ------------------------------------------------ |
| height_or_hash | string or integer | Yes      | The block hash (hex string) or block height (integer). |

## Returns

This method returns the raw block data as a hexadecimal string:

| Field    | Description                                        |
| -------- | -------------------------------------------------- |
| blockHex | The full block data encoded as a hexadecimal string. |

## Example Result

```json
{
  "blockHex": "0100...abcd"
}

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.block.get",
    "params": ["00000000000000000176c6f9e3b8c23a5f9a07ae2b0f6cc6cc2d1b16869f97a3"],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const blockData = await tatum.rpc.getBlock("00000000000000000176c6f9e3b8c23a5f9a07ae2b0f6cc6cc2d1b16869f97a3");

console.log(blockData);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
