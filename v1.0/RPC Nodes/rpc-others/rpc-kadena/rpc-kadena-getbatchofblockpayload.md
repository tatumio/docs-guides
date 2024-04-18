---
title: "getBatchOfBlockPayload"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getbatchofblockpayload"
category: "65c5e93c623cad004b45d505"
hidden: false
metadata:
  description: "Retrieve a batch of block payloads by hash in the Kadena blockchain."
  image: []
  keywords: "Kadena, block payload, getPayloadBatch"
  robots: "index"
createdAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/payload/batch` endpoint retrieves a batch of block payloads given a set of payload hashes. This allows for efficient bulk retrieval of block data, crucial for applications that need to process or verify multiple blocks at once.

## Parameters

| Name        | Type   | Required | Description                                            |
| ----------- | ------ | -------- | ------------------------------------------------------ |
| apiVersion  | string | Yes      | Version of Kadena API "0.0"                            |
| nodeVersion | enum   | Yes      | "test-singleton" "development" "mainnet01" "testnet04" |
| chain       | string | Yes      | The specific chain ID from which to retrieve data.     |

## Request Body

The request body should include an array of payload hashes for which payloads are to be retrieved:

```json
{
  "payloadHashes": ["hash1", "hash2", ...]
}
```

## Returns

A successful call to this endpoint returns an array of the requested block payloads. The payloads may be returned in any order.

| Field            | Description                                                       |
| ---------------- | ----------------------------------------------------------------- |
| transactions     | A list of transactions included in the block.                     |
| minerData        | Data about the miner who mined this block.                        |
| transactionsHash | A hash of the transactions included in the block.                 |
| outputsHash      | A hash of the outputs from the transactions.                      |
| payloadHash      | The hash of the payload itself, confirming the payload retrieved. |

## Request Example

```curl
curl --location --request POST 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/payload/batch' \
--header 'Content-Type: application/json' \
--data-raw '{
    "payloadHashes": ["RClyuyZAacwvPpmLXKbTwrIRXWeUSjiNhJVP2esH8KM", "QxGCAz5AY1Y41nh1yWtgqhKhZ9pPiPRagFdIKNqBH74"]
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const payloadBatch = await tatum.kadena.getPayloadBatch({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  payloadHashes: ["your_payload_hash_here1", "your_payload_hash_here2"],
});

console.log(payloadBatch);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
