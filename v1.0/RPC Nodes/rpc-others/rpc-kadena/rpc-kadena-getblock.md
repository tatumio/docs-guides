---
title: "getBlock"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getblock"
category: "6620f7e31ea673003624a8ce"
hidden: false
metadata:
  image: []
  keywords: "kadena, get block, block"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/block` endpoint allows for retrieving a collection of blocks from a specified Kadena chain in ascending order that satisfies various query parameters. This comprehensive retrieval includes all blocks within the chain database, encompassing even orphaned blocks. This functionality is pivotal for developers requiring detailed insights into the chain's history and state for debugging and analytical purposes.

## Parameters

| Name        | Type    | Required | Description                                            |
| ----------- | ------- | -------- | ------------------------------------------------------ |
| apiVersion  | string  | Yes      | Version of Kadena API "0.0"                            |
| nodeVersion | enum    | Yes      | "test-singleton" "development" "mainnet01" "testnet04" |
| chain       | string  | Yes      | The specific chain ID from which to retrieve blocks.   |
| limit       | number | No       | The maximum number of blocks to return.                |
| next        | string  | No       | A cursor for pagination to fetch subsequent blocks.    |
| minheight   | number | No       | The minimum block height to include in the results.    |
| maxheight   | number | No       | The maximum block height to include in the results.    |

## Returns

| Name  | Description                                                                                            |
| ----- | ------------------------------------------------------------------------------------------------------ |
| next  | The cursor for the next page of blocks.                                                                |
| items | An array of blocks, each including details such as the block header, transactions, and their outcomes. |
| limit | The maximum number of blocks returned in this response.                                                |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/block?limit={limit}&next={next}&minheight={minheight}&maxheight={maxheight}' \
--header 'Content-Type: application/json'
```
```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum =
  (await TatumSDK.init) < Kadena > { network: Network.KADENA_MAINNET };

const blocks = await tatum.kadena.getBlock({
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

console.log(blocks);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
