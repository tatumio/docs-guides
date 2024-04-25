---
title: "getCurrentCut"
excerpt: "Kadena RPC"
slug: "rpc-kadena-getcurrentcut"
category: "6620f7e31ea673003624a8cc"
hidden: false
metadata:
  description: "Kadena RPC"
  image: []
  keywords: "kadena, rpc"
  robots: "index"
createdAt: "Wed Apr 10 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 10 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/cut` endpoint in Kadena represents a distributed state of a chainweb. It references one block header for each chain, ensuring those blocks are pairwise concurrent. In Kadena, two blocks from different chains are considered concurrent if one is a direct dependency of the other or if they don't depend on each other at all. This method is crucial for:

- **State Monitoring**: Allows for the monitoring of the Kadena chainweb's state, facilitating the identification of the blockchain's health and activity.
- **Synchronization**: Essential for applications that require up-to-date synchronization with the Kadena chainweb's state.
- **Data Integrity**: Ensures that transactions and other blockchain interactions are based on the current and accurate state of the chainweb.

## Parameters

| Name        | Type   | Required | Description                                            |
| ----------- | ------ | -------- | ------------------------------------------------------ |
| apiVersion  | string | Yes      | Version of Kadena API "0.0"                            |
| nodeVersion | enum   | Yes      | "test-singleton" "development" "mainnet01" "testnet04" |
| maxHeight   | number | No       | Maximum cut height of the returned cut                 |

## Returns

A successful request to the `/cut` endpoint returns the current cut of the Kadena chainweb, including the following information:

| Field    | Description                                                                                  |
| -------- | -------------------------------------------------------------------------------------------- |
| origin   | The origin of the cut.                                                                       |
| height   | The height of the cut, indicating the latest state.                                          |
| weight   | The weight of the cut.                                                                       |
| hashes   | An object containing the height and hash of the latest block for each chain in the chainweb. |
| id       | The ID of the cut.                                                                           |
| instance | The instance of the Kadena network (e.g., mainnet01).                                        |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/cut' \
--header 'Content-Type: application/json' \
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const currentCut = await tatum.rpc.putCutNetworkPeerInfo({
  network: {
    apiVersion: "0.0",
    nodeVersion: "mainnet01",
  },
  maxHeight:
});

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
