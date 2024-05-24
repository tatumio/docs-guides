---
title: "getNetworkStatus"
slug: "rpc-cosmos-getnetworkstatus"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Retrieve current operational status and other relevant details about the Cosmos network."
  image: []
  keywords: "cosmos, rpc, network status"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `getNetworkStatus` method provides real-time information about the operational status of the Cosmos network. This includes the current network conditions, recent blocks, and any network events.

## Request Parameters

| Name                   | Type                               | Required | Description                                                     |
| ---------------------- | ---------------------------------- | -------- | --------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.           |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                  |
| `network`              | string (from networkIdentifier)    | Yes      | The network name, e.g., "cosmos-mainnet".                       |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                         |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                      |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                       |
| `metadata`             | object                             | No       | Optional metadata providing additional context for the request. |

## Returns

The response provides comprehensive details about the network's current state, essential for developers monitoring network health or preparing for network-wide events.

| Field                      | Description                                            |
| -------------------------- | ------------------------------------------------------ |
| `current_block_identifier` | The identifier of the most recently confirmed block.   |
| `current_block_timestamp`  | Timestamp of the latest block in Unix milliseconds.    |
| `genesis_block_identifier` | The identifier of the network's genesis block.         |
| `peers`                    | List of active peers with which the node is connected. |

## Example Result

The response returns detailed information about the current state of the network including the most recent block, the genesis block, the oldest block available due to pruning, synchronization status, and the active peers connected to the node.

```json
{
  "current_block_identifier": {
    "index": 5200568,
    "hash": "9035A963AA5A28729F0BA316801E901A4E8B1500B2E28301FA296C2D61816F53"
  },
  "current_block_timestamp": 1618355642000,
  "genesis_block_identifier": {
    "index": 1,
    "hash": "34EC9C1A9AB4092CF4B14B4C8107410E70FDDC09AB7B10877B167872E6F24ECC"
  },
  "oldest_block_identifier": {
    "index": 500,
    "hash": "4F2A8B7B5E6233851C8756AE12F4759881F2B5DE9F9B44F6A6F5EA5ABD3FCD82"
  },
  "sync_status": {
    "synced": true,
    "synced_through": {
      "index": 5200000,
      "hash": "C2D61816F538B1500B2E28301FA296C2D61816F53A963AA5A28729F0BA316801"
    }
  },
  "peers": [
    {
      "peer_id": "cosmos1fl48vsnmsdzcv85q5d2q4z5ajdha8yu34mf0eh",
      "metadata": {
        "client_version": "v0.34.7"
      }
    },
    {
      "peer_id": "cosmos1ql48hskj328lsv8zp6u6lqwdr8083gg9xlvnrz",
      "metadata": {
        "client_version": "v0.34.9"
      }
    }
  ]
}
```

This structured response ensures that clients can accurately assess the node’s view of the blockchain, whether the node is up-to-date with the blockchain, the oldest data available for querying due to state pruning, and the current peers connected to the network for data propagation and consensus.

## Request Example
```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/network/status' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "network_identifier": {
    "blockchain": "cosmos",
    "network": "mainnet"
  }
}'
```
```typescript
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({
  network: Network.COSMOS_MAINNET,
});

const networkStatus = await tatum.rpc.getNetworkStatus({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "cosmos-mainnet",
  },
});

console.log("Cosmos Network Status:", networkStatus);

await tatum.destroy();
```
