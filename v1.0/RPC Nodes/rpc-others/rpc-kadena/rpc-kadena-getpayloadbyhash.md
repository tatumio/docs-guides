---
title: "getPayloadByHash"
excerpt: "getCurrentCut"
slug: "rpc-kadena-getpayloadbyhash"
category: "65c5e93c623cad004b45d505"
hidden: false
metadata:
  description: "Retrieve payload data for a specific block in the Kadena blockchain by payload hash."
  image: []
  keywords: "Kadena, block payload, getPayloadByHash"
  robots: "index"
createdAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/payload/{payloadHash}` endpoint retrieves the payload data of a block for the given payload hash. This is crucial for accessing detailed information about specific transactions and operations within a block without retrieving the entire block data.

## Parameters

| Name        | Type   | Required | Description                                            |
| ----------- | ------ | -------- | ------------------------------------------------------ |
| apiVersion  | string | Yes      | Version of Kadena API "0.0"                            |
| nodeVersion | enum   | Yes      | "test-singleton" "development" "mainnet01" "testnet04" |
| chain       | string | Yes      | The specific chain ID from which to retrieve data.     |
| payloadHash | string | Yes      | The hash of the payload to retrieve.                   |

## Returns

A successful call to this endpoint returns the payload data of the specified block, which includes:

| Field            | Description                                                       |
| ---------------- | ----------------------------------------------------------------- |
| transactions     | A list of transactions included in the block.                     |
| minerData        | Data about the miner who mined this block.                        |
| transactionsHash | A hash of the transactions included in the block.                 |
| outputsHash      | A hash of the outputs from the transactions.                      |
| payloadHash      | The hash of the payload itself, confirming the payload retrieved. |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/payload/{payloadHash}' \
--header 'Content-Type: application/json'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const payload = await tatum.kadena.getPayloadByHash({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  payloadHash: "your_payload_hash_here",
});

console.log(payload);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
