---
title: "getBlockHeaderBranches"
slug: "rpc-kadena-getblockheaderbranches"
category: "6620f7e31ea673003624a8ce"
excerpt: "Retrieve Block Header Branches for a Specific Blockchain Chain"
hidden: false
metadata:
  image: []
  keywords: "blockchain, block header, branches, header branches"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/chain/{chain}/header/branch` endpoint allows retrieval of a page of block headers from branches of the blockchain in descending order. It provides headers that are ancestors of any block in the set of upper bounds and are not ancestors of any block in the set of lower bounds.

## Parameters

| Name        | Type    | Required | Description                                                      |
| ----------- | ------- | -------- | ---------------------------------------------------------------- |
| apiVersion  | string  | Yes      | Version of Kadena API "0.0"                                |
| nodeVersion | enum    | Yes      | "test-singleton" "development" "mainnet01" "testnet04"     |
| chain       | string  | Yes      | The specific chain ID from which to retrieve block hashes. |
| limit       | number | No       | The maximum number of block headers to return.                    |
| next        | string  | No       | A cursor for pagination to fetch subsequent block headers.        |
| minheight   | number | No       | The minimum block height to include in the results.               |
| maxheight   | number | No       | The maximum block height to include in the results.               |

## Request Body

| Field | Type  | Description                                                                                                                                            |
| ----- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| lower | array | An array of block hashes. No blocks are returned that are predecessors of any block with a hash from this array.                                      |
| upper | array | An array of block hashes. Returned block headers are predecessors of a block with a hash from this array. This includes blocks with hashes from this array. |

## Returns

A successful call to this endpoint returns a JSON object containing the following fields:

| Field | Description                                                         |
| ----- | ------------------------------------------------------------------- |
| next  | The cursor for the next page of block headers.                      |
| items | An array of block headers, detailing the branches in the blockchain. |
| limit | The maximum number of block headers returned in this response.      |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/chain/{chain}/header/branch' \
--header 'Content-Type: application/json' \
--data-raw '{
    "lower": ["example_lower_hash"],
    "upper": ["example_upper_hash"]
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Blockchain } from "@tatumio/tatum";

const sdk = await TatumSDK.init<Blockchain>({ network: Network.BLOCKCHAIN_MAINNET });

const headerBranches = await sdk.rpc.getBlockHeaderBranches({
  chain: 0,
  lower: ["example_lower_hash"],
  upper: ["example_upper_hash"]
});

console.log(headerBranches);

await sdk.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
