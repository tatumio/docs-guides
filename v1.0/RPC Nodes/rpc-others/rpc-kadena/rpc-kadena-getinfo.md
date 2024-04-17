---
title: "getinfo"
excerpt: "Kadena RPC"
hidden: false
metadata:
  description: "Kadena RPC"
  image: []
  keywords: "kadena, node, info"
  robots: "index"
createdAt: "Wed Apr 10 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 10 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/info` endpoint provides general information about a Kadena node and the chainweb version it is running. This endpoint is crucial for understanding the configuration and status of the node, including:

- The number of chains supported by the node.
- The API version of the node.
- The list of chains the node is part of.
- The node's version and its chainweb instance.
- The node's graph history, detailing the connectivity and relationships between different chains at various points in time.

This information is valuable for developers interacting with the Kadena blockchain, as it offers insights into the node's capabilities and network topology.

## Parameters

The `/info` method does not require any parameters, making it straightforward to retrieve the node's information.

## Returns

A successful call to the `/info` endpoint returns a JSON object containing the following fields:

| Field              | Description                                                                                        |
| ------------------ | -------------------------------------------------------------------------------------------------- |
| nodeNumberOfChains | The number of chains the node participates in.                                                     |
| nodeApiVersion     | The version of the node's API.                                                                     |
| nodeChains         | An array listing the chains the node is part of.                                                   |
| nodeVersion        | The version of the Kadena node.                                                                    |
| nodeGraphHistory   | A detailed account of the node's graph history, showing the connectivity between chains over time. |

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/chainweb/{apiVersion}/{nodeVersion}/info' \
--header 'Content-Type: application/json'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const nodeInfo = await tatum.kadena.getNodeInfo();

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
