---
title: "commit"
slug: "rpc-bnb-beacon-commit"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:00:04 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Defining the block height parameter for the query
const commitParams = {
  height: 'YOUR_HEIGHT_VALUE',  // e.g., "12345"
};

// Fetching commit information for the specified block height
const commitData = await tatum.rpc.commit(commitParams);
console.log(commitData);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `commit` method is used to retrieve the commit information of a specific block in the BNB Beacon Chain by providing the block height. If no height is provided, it will fetch commit information regarding the latest block.

### Parameters

- `height` (string, optional): The height of the block for which you want to retrieve commit information.

### Return Object

This method returns an object containing commit information for the specified block, including details like commit hash, precommit validators, and more. 

(Note: The exact fields in the return object might vary based on the BNB Beacon Chain's implementation and version.)
