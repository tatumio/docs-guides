---
title: "getBlockHeaderByHash"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getblockheaderbyhash"
category: "65c5e93c623cad004b45d505"
hidden: false
metadata:
  description: "Retrieve a block header by hash in Kadena blockchain."
  image: []
  keywords: "Kadena, blockheader, hash"
  robots: "index"
createdAt: "Tue Apr 12 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 12 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/header/{blockHash}` endpoint allows querying a block header by its hash. This is useful for developers looking to verify blocks or inspect block attributes without the need for the entire block's data.

## Parameters

| Name        | Type   | Required | Description                                              |
| ----------- | ------ | -------- | -------------------------------------------------------- |
| apiVersion  | string | Yes      | Version of Kadena API "0.0"                              |
| nodeVersion | enum   | Yes      | "test-singleton" "development" "mainnet01" "testnet04"   |
| chain       | string | Yes      | The specific chain ID from which to retrieve the header. |
| blockHash   | string | Yes      | The hash of the block whose header is being requested.   |

## Returns

A successful call to this endpoint returns the requested block header. The header can be returned in various formats, including JSON, base64 encoded, or binary.

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/header/{blockHash}' \
--header 'Content-Type: application/json'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const blockHeader = await tatum.kadena.getBlockHeaderByHash({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  blockHash: "your_block_hash_here",
});

console.log(blockHeader);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
