---
title: "getBlockHashBranches"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getblockhashbranches"
category: "65c5e93c623cad004b45d505"
hidden: false
metadata:
  description: "Retrieve block hash branches in Kadena blockchain."
  image: []
  keywords: "Kadena, blockhash, getBlockHashBranches"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/hash/branch` endpoint retrieves a page of block hashes from branches of the blockchain in **descending** order. This method returns only blocks that are ancestors of some block in the set of upper bounds and are not ancestors of any block in the set of lower bounds.

## Parameters

| Name        | Type    | Required | Description                                                      |
| ----------- | ------- | -------- | ---------------------------------------------------------------- |
| apiVersion  | string  | Yes      | Version of Kadena API "0.0"                                      |
| nodeVersion | enum    | Yes      | "test-singleton" "development" "mainnet01" "testnet04"           |
| chain       | string  | Yes      | The specific chain ID for which to retrieve block hash branches. |
| limit       | integer | No       | The maximum number of block hashes to return.                    |
| next        | string  | No       | A cursor for pagination to fetch subsequent block hashes.        |
| minheight   | integer | No       | The minimum block height to include in the results.              |
| maxheight   | integer | No       | The maximum block height to include in the results.              |

## Request Body

| Field | Type  | Description                                                                                                                                            |
| ----- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| lower | array | An array of block hashes. No block hashes are returned that are predecessors of any block with a hash from this array.                                 |
| upper | array | An array of block hashes. Returned block hashes are predecessors of a block with a hash from this array, including blocks with hashes from this array. |

## Returns

A successful call to the `/chain/{chain}/hash/branch` endpoint returns a JSON object containing the following fields:

| Field | Description                                                         |
| ----- | ------------------------------------------------------------------- |
| next  | The cursor for the next page of block hashes.                       |
| items | An array of block hashes, detailing the branches in the blockchain. |
| limit | The maximum number of block hashes returned in this response.       |

## Request Example

```curl
curl --location --request POST 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/hash/branch?limit={limit}&next={next}&minheight={minheight}&maxheight={maxheight}' \
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

const blockHashBranches = await tatum.kadena.getBlockHashBranches({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
    chain: "0", // Example chain ID
  },
  lower: ["RClyuyZAacwvPpmLXKbTwrIRXWeUSjiNhJVP2esH8KM"],
  upper: ["QxGCAz5AY1Y41nh1yWtgqhKhZ9pPiPRagFdIKNqBH74"],
});

console.log(blockHashBranches);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
