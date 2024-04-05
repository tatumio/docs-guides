---
title: "abcInfo"
slug: "rpc-bnb-beacon-abcInfo"
excerpt: "Bnb Beacon RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]


### How to use it

```typescript
// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Using the 'abciInfo' method to get information about the ABCI (Application Blockchain Interface) application
const abciInfoData = await tatum.rpc.abciInfo();

console.log(abciInfoData);

// Destroying the Tatum SDK instance. This is necessary to stop any background jobs that the SDK may have started.
await tatum.destroy();
```

### Overview

The `abciInfo` method is utilized to retrieve information about the BNB Beacon Chain application.

### Return Object

The `abciInfo` method typically returns an object containing the details about the application. While the exact structure might vary, the return object may include the following fields:

- `version` (string): The version of the application.
- `lastBlockHeight` (string number): The height of the last block processed.
- `lastBlockAppHash` (string number): The hash of the last block processed.

(Note: The exact fields in the return object might vary based on the BNB Beacon Chain's implementation and version.)