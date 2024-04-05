---
title: "broadcastTxCommit"
slug: "rpc-bnb-beacon-broadcastTxCommit"
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

// Defining the signed transaction string to broadcast
const signedTx = 'SIGNED_TRANSACTION_STRING';  // Replace with your signed transaction string

// Broadcasting the transaction and waiting for commit
const commitResponse = await tatum.rpc.broadcastTxCommit({ tx: signedTx });
console.log(commitResponse);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `broadcastTxCommit` method is used to broadcast a signed transaction to the BNB beacon chain and wait for it to be included in a block (commit). This method provides information about the committed transaction, including its status, block height, and other relevant data.

### Parameters

- `tx` (string, required): The signed transaction string that you want to broadcast.

### Return Object

The method returns a response containing information about the committed transaction. The response includes the following fields:

- `height` (string): The block height at which the transaction was included.
  - Example: `7734637`
  
- `hash` (string): The hash of the committed transaction.
  - Example: `008EA3C57B15E34B045F69DCEB2A5589B979B2B58BA282C15DF2AEA8B441AB6B`

- `check_tx` (object): Additional information related to the check transaction phase.
  - Example: `{ }`

- `deliver_tx` (object): Additional information related to the deliver transaction phase.

(Note: The exact structure of the response may vary based on the BNB beacon chain's implementation and version.)