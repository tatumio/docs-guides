---
title: "checkNodeHealth"
slug: "rpc-kadena-checknodehealth"
excerpt: "Kadena RPC"
hidden: false
metadata:
  image: []
  keywords: "kadena, node, health-check"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/health-check` endpoint is utilized to confirm the operational status of a Kadena chainweb-node, ensuring it is active, running, and able to respond to API requests. To evaluate the consensus state or the blockchain's current cut, it is advisable to use the `/cut` endpoint. This health check plays a vital role in the maintenance and reliability of blockchain applications by verifying the node's readiness.

## Parameters

The `/health-check` endpoint does not require any parameters, simplifying the process for developers to quickly ascertain the health of a Kadena node.

## Returns

A successful call to the `/health-check` endpoint yields a plain text response that indicates the node's health status:

- **200 OK**: "Health check OK." - This response signifies that the node is healthy and functional.

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/kadena-mainnet/{api_key}/health-check' \
--header 'Content-Type: application/json'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Kadena, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Kadena>({ network: Network.KADENA_MAINNET });

const healthStatus = await tatum.kadena.checkNodeHealth();

console.log(healthStatus); // Expected output: "Health check OK."

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
