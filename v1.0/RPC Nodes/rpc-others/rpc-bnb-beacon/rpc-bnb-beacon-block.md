---
title: "block"
slug: "rpc-bnb-beacon-block"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 05 2024 16:20:18 GMT+0000 (Coordinated Universal Time)"
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

// Defining the parameters for fetching a specific block from the blockchain
const blockParams = {
  height: YOUR_HEIGHT_VALUE
};

// Fetching the block data using the 'block' method and the defined parameters
const blockData = await tatum.rpc.block(blockParams);

console.log(blockData);

// Destroying the Tatum SDK instance to stop any background jobs and free up resources
await tatum.destroy();

```

### Overview

The `block` method is utilized to fetch block details for a specific height from the BNB Beacon Chain. Without specific block `height`, method returns last known block.

### Parameters

- `height` (string number, optional): The height of the block to be fetched. This is a optional parameter.

### Return Object

The `block` method returns an object containing the details of the block at the specified height. While the exact structure might vary, the return object may include fields like:

- `header` (object): Information about the block header.
- `transactions` (array): List of transactions within the block.
- `blockHash` (string): Hash of the block.
- ... and other details depending on the BNB Beacon Chain's implementation and version.

(Note: The exact fields in the return object might vary based on the BNB Beacon Chain's implementation and version.)
