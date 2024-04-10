---
title: "getepochschedule"
slug: "rpc-solana-getepochschedule"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getEpochSchedule()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getEpochSchedule` method returns the epoch schedule information from this cluster's genesis config. This includes the maximum number of slots in each epoch, the number of slots before the beginning of an epoch to calculate a leader schedule for that epoch, whether epochs start short and grow, the first normal-length epoch, and the first normal slot. This data can be useful for planning and understanding the progression of epochs in the Solana network.

{% embed url="<https://codepen.io/Night-Shift-Dev/pen/XWyKMyP"> %}  
Try this Feature  
{% endembed %}

### Parameters

None

### Return Object

The result field will be an object with the following fields:

- `slotsPerEpoch`: The maximum number of slots in each epoch.
- `leaderScheduleSlotOffset`: The number of slots before beginning of an epoch to calculate a leader schedule for that epoch.
- `warmup`: Whether epochs start short and grow.
- `firstNormalEpoch`: The first normal-length epoch, log2(slotsPerEpoch) - log2(MINIMUM\_SLOTS\_PER\_EPOCH).
- `firstNormalSlot`: MINIMUM\_SLOTS\_PER\_EPOCH \* (2.pow(firstNormalEpoch) - 1).

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id":1,
  "method":"getEpochSchedule"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "firstNormalEpoch": 8,
    "firstNormalSlot": 8160,
    "leaderScheduleSlotOffset": 8192,
    "slotsPerEpoch": 8192,
    "warmup": true
  },
  "id": 1
}
```
