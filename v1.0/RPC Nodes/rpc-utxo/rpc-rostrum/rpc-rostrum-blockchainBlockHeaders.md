---
title: "blockchainBlockHeaders"
slug: "rpc-rostrum-blockchainBlockHeaders"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee9ea8e770036f3c937"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, block headers, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.block.headers` method retrieves a contiguous sequence of block headers from the main chain, starting at a specified height. This function is crucial for applications that need to verify block headers without downloading full block data.

## Parameters

| Name         | Type    | Required | Description                                                        |
| ------------ | ------- | -------- | ------------------------------------------------------------------ |
| start_height | integer | Yes      | The height of the first header in the range to retrieve.           |
| count        | integer | Yes      | The number of headers to retrieve.                                 |
| cp_height    | integer | No       | Optional checkpoint height for header verification.                |

## Returns

The response includes a sequence of block headers and, optionally, proof of their inclusion in the blockchain:

| Field   | Description                                                                               |
| ------- | ----------------------------------------------------------------------------------------- |
| count   | The number of headers returned, which can be less than requested if the end of the chain is reached. |
| hex     | A single string containing the binary headers concatenated together as hexadecimal.       |
| max     | The maximum number of headers the server will return in a single request.                 |
| root    | (Optional) The merkle root of all blockchain headers up to cp_height, if cp_height is non-zero. |
| branch  | (Optional) The merkle branch linking the last returned header to the root.                |

## Example Result

Depending on the `cp_height` value, the response might include a simple list of headers or it could provide a merkle proof of inclusion up to the specified checkpoint height:

Without `cp_height` or `cp_height` is 0:

```json
{
  "count": 2,
  "hex": "010...299",
  "max": 2016
}


## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.block.headers",
    "params": [1000, 10, 0],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const headersInfo = await tatum.rpc.getBlockHeaders({
  startHeight: 1000,
  count: 10,
  cpHeight: 0
});

console.log(headersInfo);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
