---
title: "getBlockHashes"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getblockhashes"
category: "6620f7e31ea673003624a8cc"
hidden: false
metadata:
  description: "Kadena RPC"
  image: []
  keywords: "kadena, blockhash, get block hashes"
  robots: "index"
createdAt: "Wed Mar 10 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 10 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/hash` endpoint retrieves a collection of block hashes from a specified Kadena chain in ascending order that satisfies various query parameters. This includes all block hashes within the chain database, even those of orphaned blocks. It is crucial for developers needing to track block creation or verify chain integrity.

## Parameters

| Name        | Type    | Required | Description                                                |
| ----------- | ------- | -------- | ---------------------------------------------------------- |
| apiVersion  | string  | Yes      | Version of Kadena API "0.0"                                |
| nodeVersion | enum    | Yes      | "test-singleton" "development" "mainnet01" "testnet04"     |
| chain       | string  | Yes      | The specific chain ID from which to retrieve block hashes. |
| limit       | number | No       | The maximum number of block hashes to return.              |
| next        | string  | No       | A cursor for pagination to fetch subsequent block hashes.  |
| minheight   | number | No       | The minimum block height to include in the results.        |
| maxheight   | number | No       | The maximum block height to include in the results.        |

## Returns

A successful call to the `/chain/{chain}/hash` endpoint returns a JSON object containing the following fields:

| Field | Description                                                    |
| ----- | -------------------------------------------------------------- |
| next  | The cursor for the next page of block hashes.                  |
| items | An array of block hashes, including hashes of orphaned blocks. |
| limit | The maximum number of block hashes returned in this response.  |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/hash?limit={limit}&next={next}&minheight={minheight}&maxheight={maxheight}' \
--header 'Content-Type: application/json'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const blockHashes = await tatum.kadena.getBlockHashes({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  limit: 2,
  next: "inclusive:o1S4NNFhKWg8T1HEkmDvsTH9Ut9l3_qHRpp00yRKZIk",
  minheight: 1000000,
  maxheight: 1000001,
});

console.log(blockHashes);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
