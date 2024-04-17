---
title: "getPayloadWithOutputs"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getblockpayloadwithoutputs"
category: "65c5e93c623cad004b45d505"
hidden: false
metadata:
  description: "Retrieve the block payload with outputs for a given payload hash in the Kadena blockchain."
  image: []
  keywords: "Kadena, block payload, outputs, getPayloadWithOutputs"
  robots: "index"
createdAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/payload/{payloadHash}/outputs` endpoint retrieves the payload data along with transaction outputs for a specified payload hash. This detailed view is beneficial for users needing comprehensive transactional data for specific blocks.

## Parameters

| Name        | Type   | Required | Description                                            |
| ----------- | ------ | -------- | ------------------------------------------------------ |
| apiVersion  | string | Yes      | Version of Kadena API "0.0"                            |
| nodeVersion | enum   | Yes      | "test-singleton" "development" "mainnet01" "testnet04" |
| chain       | string | Yes      | The specific chain ID from which to retrieve data.     |
| payloadHash | string | Yes      | The hash of the payload to retrieve.                   |

## Returns

A successful call to this endpoint returns the payload with transaction outputs for the specified block payload hash, which includes:

| Field            | Description                                                             |
| ---------------- | ----------------------------------------------------------------------- |
| transactions     | An array of transactions included in the block, with their output data. |
| minerData        | Data about the miner who mined this block.                              |
| transactionsHash | A hash of the transactions included in the block.                       |
| outputsHash      | A hash of the outputs from the transactions.                            |
| payloadHash      | The hash of the payload itself, confirming the payload retrieved.       |
| coinbase         | Coinbase transaction details, if applicable.                            |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/payload/{payloadHash}/outputs' \
--header 'Content-Type: application/json'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const payloadOutputs = await tatum.kadena.getPayloadWithOutputs({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  payloadHash: "your_payload_hash_here",
});

console.log(payloadOutputs);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
