---
title: "broadcastTxAsync"
slug: "rpc-bnb-beacon-broadcastTxAsync"
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

// Defining the transaction to broadcast
const signedTx = 'SIGNED_TRANSACTION_STRING';  // Replace with your signed transaction string

// Broadcasting the transaction asynchronously
const txResponse = await tatum.rpc.broadcastTxAsync({ tx: signedTx });
console.log(txResponse);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `broadcastTxAsync` method is used to broadcast a signed transaction to the BNB Beacon Chain asynchronously.

### Parameters

- `tx` (string, required): The signed transaction string that you want to broadcast.

### Return Object

The method returns a promise that resolves to a JSON-RPC response containing information about the broadcasted transaction. The response includes the following fields:

- `code` (string): The status code of the transaction.
  - Example: `0`

- `data` (string): Additional data related to the transaction.
  - Example: `7B226F726465725F6964223A22383133453439333946313536374232313937303446464332414434444635384244453031303837392D3438227D`

- `hash` (string): The hash of the broadcasted transaction.
  - Example: `008EA3C57B15E34B045F69DCEB2A5589B979B2B58BA282C15DF2AEA8B441AB6B`

- `log` (string): Transaction log information.
  - Example: `Msg 0:`

(Note: The exact response structure may vary depending on the BNB Beacon Chain's implementation and version.)
