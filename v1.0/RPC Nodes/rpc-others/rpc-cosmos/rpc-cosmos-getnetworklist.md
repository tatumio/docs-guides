---
title: "getNetworkList"
slug: "rpc-cosmos-getnetworklist"
category: "6620f7e31ea673003624a8cc"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "List all networks supported by the Cosmos Rosetta interface."
  image: []
  keywords: "cosmos, rpc, network list"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:42 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `getNetworkList` method fetches a list of all networks available through the Cosmos Rosetta API, allowing clients to discover the various blockchain networks they can interact with.

## Parameters

| Name       | Type   | Required | Description                     |
| ---------- | ------ | -------- | ------------------------------- |
| `metadata` | object | No       | Optional metadata if applicable |

## Returns

The method returns a comprehensive list of all supported networks, including essential network-specific information.

| Field                | Description                                                          |
| -------------------- | -------------------------------------------------------------------- |
| `network_identifier` | Identifier for each network, including blockchain and network names. |
| `blockchain`         | The blockchain name for the network, e.g., "cosmos".                 |
| `network`            | The specific network name, e.g., "mainnet".                          |

## Example Result

```json
{
  "network_identifiers": [
    {
      "blockchain": "cosmos",
      "network": "mainnet"
    }
  ]
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/network/list' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{}
```
```typescript
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({
  network: Network.COSMOS_ROSETTA,
});

const networkList = await tatum.rpc.getNetworkList();

console.log("Network List:", networkList);

await tatum.destroy();
```
