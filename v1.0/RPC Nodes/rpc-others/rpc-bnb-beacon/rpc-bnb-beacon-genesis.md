---
title: "genesis"
slug: "rpc-bnb-beacon-genesis"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
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

// Retrieve the genesis information
const genesisInfo = await tatum.rpc.genesis();
console.log(genesisInfo);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `genesis` method is used to retrieve the genesis information of the Beacon Chain.

### Parameters

This method does not require any parameters.

### Return Object (Required)

The method returns a Promise that resolves to a JSON-RPC response containing the following field:

- `genesis` (object): General information about the Beacon Chain genesis.

(Note: The exact fields in the return object might vary based on the BNB Beacon Chain's implementation and version.)
