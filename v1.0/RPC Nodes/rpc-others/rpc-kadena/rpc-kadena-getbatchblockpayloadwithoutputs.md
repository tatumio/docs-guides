---
title: "getBatchBlockPayloadWithOutputs"
excerpt: "Kadena RPC"
hidden: false
metadata:
  description: "Retrieve a batch of block payloads with outputs for specified payload hashes in the Kadena blockchain."
  image: []
  keywords: "Kadena, block payload, batch, outputs, getPayloadOutputsBatch"
  robots: "index"
createdAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/payload/outputs/batch` endpoint retrieves a batch of block payloads along with their outputs, given a set of payload hashes. This method enables efficient bulk data retrieval, particularly useful for applications requiring detailed information across multiple blocks.

## Parameters

| Name        | Type   | Required | Description                                                                     |
| ----------- | ------ | -------- | ------------------------------------------------------------------------------- |
| apiVersion  | string | Yes      | Version of Kadena API, e.g., "0.0"                                              |
| nodeVersion | enum   | Yes      | Node version, one of: "test-singleton", "development", "mainnet01", "testnet04" |
| chain       | string | Yes      | The specific chain ID from which to retrieve data.                              |

## Request Body

You should include an array of payload hashes for which payloads with outputs are to be retrieved:

```json
{
  "payloadHashes": ["hash1", "hash2", ...]
}
```

## Returns

A successful call to this endpoint returns an array of the requested block payloads with outputs. The results may be returned in any order.

| Field            | Description                                                        |
| ---------------- | ------------------------------------------------------------------ |
| transactions     | An array of transactions included in each payload.                 |
| outputs          | Detailed outputs of each transaction.                              |
| minerData        | Data about the miner who mined each block.                         |
| transactionsHash | A hash of the transactions included in each payload.               |
| outputsHash      | A hash of the outputs from the transactions in each payload.       |
| payloadHash      | The hash of each payload itself, confirming the payload retrieved. |

## Request Example

```curl
curl --location --request POST 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key})/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/payload/outputs/batch' \
--header 'Content-Type: application/json' \
--data-raw '{
"payloadHashes": ["hash1", "hash2"]
}'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const payloadOutputsBatch = await tatum.kadena.getPayloadOutputsBatch({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  payloadHashes: ["hash1", "hash2"],
});

console.log(payloadOutputsBatch);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
