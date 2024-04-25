---
title: "getBlockHeaders"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getblockheaders"
category: "6620f7e31ea673003624a8cc"
hidden: false
metadata:
  description: "Retrieve a collection of block headers from the Kadena blockchain."
  image: []
  keywords: "Kadena, block headers, getBlockHeaders"
  robots: "index"
createdAt: "Tue Apr 12 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 12 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/header` endpoint retrieves a page of block headers in ascending order that satisfies various query parameters. This includes headers of all blocks within the chain database, including those of orphaned blocks. The service is essential for developers needing detailed insights into the blockchain's history and state without needing full block data.

## Parameters

| Name        | Type    | Required | Description                                            |
| ----------- | ------- | -------- | ------------------------------------------------------ |
| apiVersion  | string  | Yes      | Version of Kadena API "0.0"                            |
| nodeVersion | enum    | Yes      | "test-singleton" "development" "mainnet01" "testnet04" |
| chain       | string  | Yes      | The specific chain ID from which to retrieve headers.  |
| limit       | number | No       | The maximum number of headers to return.               |
| next        | string  | No       | A cursor for pagination to fetch subsequent headers.   |
| minheight   | number | No       | The minimum block height to include in the results.    |
| maxheight   | number | No       | The maximum block height to include in the results.    |

## Returns

A successful call to this endpoint returns a JSON object containing the following fields:

| Field | Description                                                                                      |
| ----- | ------------------------------------------------------------------------------------------------ |
| next  | The cursor for the next page of block headers.                                                   |
| items | An array of base64 encoded or JSON formatted block headers, depending on the requested encoding. |
| limit | The maximum number of block headers returned in this response.                                   |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chain/{chain}/header?limit={limit}&next={next}&minheight={minheight}&maxheight={maxheight}' \
--header 'Content-Type: application/json'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const headers = await tatum.kadena.getBlockHeaders({
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

console.log(headers);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
