---
title: "serverVersion"
slug: "rpc-rostrum-serverVersion"
category: "6620f7e31ea673003624a8ce"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, server version, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `server.version` method allows a client to identify itself to the server and negotiate the protocol version. It is important that only the first `server.version` message is accepted by the server after connection establishment.

## Parameters

| Name              | Type   | Required | Description                                                                 |
| ----------------- | ------ | -------- | --------------------------------------------------------------------------- |
| client_name       | string | Yes      | A string identifying the connecting client software.                        |
| protocol_version  | mixed  | Yes      | An array [protocol_min, protocol_max] or a single string for equal values.  |

## Returns

Upon a successful request, the server responds with the negotiated protocol version and server information. The response's `result` field contains an array with two elements:

| Field       | Description                                           |
| ----------- | ----------------------------------------------------- |
| Server Name | The name and version of the Rostrum server.           |
| Protocol    | The negotiated protocol version between client and server. |

## Example response

```json
{
    "result": [
        "Rostrum 10.0.0",
        "1.4"
    ]
}
```
## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "server.version",
    "params": ["TatumClient", "1.4"],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<RostrumElectrum>({ network: Network.ROSTRUM_MAINNET });


const serverVersion = await tatum.rpc.getServerVersion({
  client_name: "TatumClient",
  protocol_version: "1.4"
});

console.log(serverVersion);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs

```

