---
title: "getLedgerStateDelta"
slug: "rpc-algorand-getLedgerStateDelta"
excerpt: "Algorand RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, AlgorandAlgod, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Algorand
const tatum = await TatumSDK.init<AlgorandAlgod>({ network: Network.ALGORAND_ALGOD });

// Define the input parameters in a single object
const params = {
    round: 12345,    // Specify the round for which the deltas are desired (number).
    format: 'json'   // Optional: Configures whether the response object is JSON or MessagePack encoded. If not provided, defaults to JSON (enum: json, msgpack).
};

// Retrieve ledger deltas for the specified round
const ledgerStateDelta = await tatum.rpc.getLedgerStateDelta(params);

// Log the ledger deltas
console.log('Ledger State Delta:', ledgerStateDelta);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getLedgerStateDelta` method allows you to retrieve the ledger deltas for a specific round in the Algorand network.

### Example Use Cases

1. **Ledger Analysis**: Developers can use this method to retrieve the ledger deltas for a specific round and analyze the changes in the Algorand ledger.

### Request Parameters

The `getLedgerStateDelta` method requires the following parameters:

- `round` (number, required): Specify the round for which the deltas are desired.
- `format` (enum: json, msgpack, optional): Configures whether the response object is JSON or MessagePack encoded. If not provided, it defaults to JSON.

### Return Object

The method returns an object representing the ledger deltas for the specified round in the Algorand network.

Please note that the structure and contents of the returned object may vary depending on the Algorand network and RPC version.