---
title: "serverBanner"
slug: "serverBanner"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, server banner, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `server.banner` method retrieves the server's banner message. This is typically used to display server-specific messages or announcements to users.

## Parameters

No parameters are required for this method.

## Returns

Upon a successful request, the server responds with its current banner message. The response's `result` field contains a string with the banner message.

## Example Result

```json
{
  "banner": "Welcome to Rostrum Electrum Server! Stay up to date with the latest Bitcoin Cash news at our site."
}
```

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "server.banner",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<RostrumElectrum>({ network: Network.ROSTRUM_MAINNET });

const serverBanner = await tatum.rpc.getServerBanner();

console.log(serverBanner);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
