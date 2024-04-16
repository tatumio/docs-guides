---
title: "getBlockBranches"
slug: "rpc-kadena-getblockbranches"
excerpt: "Kadena RPC"
hidden: false
metadata:
  description: "Retrieve blocks from branches in the Kadena blockchain."
  image: []
  keywords: "Kadena, block branches, getBlockBranches"
  robots: "index"
createdAt: "Fri Apr 12 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 12 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/block/branch` endpoint retrieves a page of blocks from branches of the blockchain in descending order. This includes blocks that are ancestors of the block in the set of upper bounds and are not ancestors of any block in the set of lower bounds.

## Parameters

| Name        | Type    | Required | Description                                                 |
| ----------- | ------- | -------- | ----------------------------------------------------------- |
| apiVersion  | string  | Yes      | Version of Kadena API "0.0"                                 |
| nodeVersion | enum    | Yes      | "test-singleton" "development" "mainnet01" "testnet04"      |
| chain       | string  | Yes      | The specific chain ID for which to retrieve block branches. |
| limit       | integer | No       | The maximum number of blocks to return.                     |
| next        | string  | No       | A cursor for pagination to fetch subsequent blocks.         |
| minheight   | integer | No       | The minimum block height to include in the results.         |
| maxheight   | integer | No       | The maximum block height to include in the results.         |

## Request Body

| Field | Type  | Description                                                                                                                |
| ----- | ----- | -------------------------------------------------------------------------------------------------------------------------- |
| lower | array | Blocks are not returned if they are predecessors of any block with a hash from this array.                                 |
| upper | array | Returned blocks are predecessors of a block with a hash from this array. This includes blocks with hashes from this array. |

## Returns

A successful call to this endpoint returns a JSON object containing the following fields:

| Field | Description                                                                |
| ----- | -------------------------------------------------------------------------- |
| next  | The cursor for the next page of block branches.                            |
| items | An array of JSON encoded blocks, detailing the branches in the blockchain. |
| limit | The maximum number of blocks returned in this response.                    |

## Request Example

```curl
curl --location --request POST 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/block/branch?limit={limit}&next={next}&minheight={minheight}&maxheight={maxheight}' \
--header 'Content-Type: application/json' \
--data-raw '{
"lower": ["RClyuyZAacwvPpmLXKbTwrIRXWeUSjiNhJVP2esH8KM"],
"upper": ["QxGCAz5AY1Y41nh1yWtgqhKhZ9pPiPRagFdIKNqBH74"],
}'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const blockBranches = await tatum.kadena.getBlockBranches({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  lower: ["RClyuyZAacwvPpmLXKbTwrIRXWeUSjiNhJVP2esH8KM"],
  upper: ["QxGCAz5AY1Y41nh1yWtgqhKhZ9pPiPRagFdIKNqBH74"],
  limit: 2,
});

console.log(blockBranches);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
