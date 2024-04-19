---
title: "blockchainBlockHeader"
slug: "blockchainBlockHeader"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, block header, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.block.header` method retrieves the block header at a specified height within the Bitcoin Cash blockchain via Rostrum Electrum. Optionally, it can also provide a merkle proof of the header's inclusion in the blockchain up to a specified checkpoint height (`cp_height`).

## Parameters

| Name      | Type    | Required | Description                                                       |
| --------- | ------- | -------- | ----------------------------------------------------------------- |
| height    | integer | Yes      | The height of the block.                                           |
| cp_height | integer | No       | Checkpoint height for the merkle proof, defaults to 0 (disabled). |

## Returns

Depending on the value of `cp_height`, the method returns either the raw block header as a hexadecimal string or a dictionary providing a merkle proof:

| Field   | Description                                                                         |
| ------- | ----------------------------------------------------------------------------------- |
| branch  | An array of hashes in the merkle branch leading up to the checkpoint root.          |
| header  | The raw block header as a hexadecimal string.                                       |
| root    | The merkle root of all blockchain headers up to and including `cp_height`.          |

## Example Result

If `cp_height` is 0:

```json
{
  "header": "00000020a....61723"
}

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.block.header",
    "params": [5, 0],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const headerInfo = await tatum.rpc.getBlockHeader({
  height: 5,
  cp_height: 0
});

console.log(headerInfo);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
