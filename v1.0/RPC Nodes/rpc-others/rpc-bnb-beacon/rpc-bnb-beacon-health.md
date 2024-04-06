---
title: "health"
slug: "rpc-bnb-beacon-health"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

```typescript
// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Check the health status
const healthStatus = await tatum.rpc.health();
console.log(healthStatus);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `health` method is used to check the health status of the Beacon Chain.

### Parameters

This method does not require any parameters.

### Return Object (Required)

The method returns a Promise that resolves to a JSON-RPC response containing information about the health status of the Beacon Chain.

(Note: The exact structure of the transaction objects and response may vary based on the BNB beacon chain's implementation and version.)
