---
title: "getslotleaders"
slug: "rpc-solana-getslotleaders"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getSlotLeaders(100,10)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getSlotLeaders` method returns an array of the slot leaders for a given slot range. In the Solana network, a slot leader is responsible for producing blocks for the network during their assigned slot time. This method could be used to monitor the network's operation, for analysis of network activity, or to understand which nodes have been assigned to produce blocks in the upcoming slots.

### Parameters

- `startSlot` (number, optional)
- `limit` (number, optional): Integer between 1 and 5,000.

### Return Object

The method returns an array of strings that represents an array of Node identity public keys as base-58 encoded strings.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id": 1,
  "method": "getSlotLeaders",
  "params": [100, 10]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": [
    "ChorusmmK7i1AxXeiTtQgQZhQNiXYU84ULeaYF1EH15n",
    "ChorusmmK7i1AxXeiTtQgQZhQNiXYU84ULeaYF1EH15n",
    "ChorusmmK7i1AxXeiTtQgQZhQNiXYU84ULeaYF1EH15n",
    "ChorusmmK7i1AxXeiTtQgQZhQNiXYU84ULeaYF1EH15n",
    "Awes4Tr6TX8JDzEhCZY2QVNimT6iD1zWHzf1vNyGvpLM",
    "Awes4Tr6TX8JDzEhCZY2QVNimT6iD1zWHzf1vNyGvpLM",
    "Awes4Tr6TX8JDzEhCZY2QVNimT6iD1zWHzf1vNyGvpLM",
    "Awes4Tr6TX8JDzEhCZY2QVNimT6iD1zWHzf1vNyGvpLM",
    "DWvDTSh3qfn88UoQTEKRV2JnLt5jtJAVoiCo3ivtMwXP",
    "DWvDTSh3qfn88UoQTEKRV2JnLt5jtJAVoiCo3ivtMwXP"
  ],
  "id": 1
}
```
