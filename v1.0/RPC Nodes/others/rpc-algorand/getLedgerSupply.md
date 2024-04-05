---
title: "getLedgerSupply"
slug: "rpc-algorand-getLedgerSupply"
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

// Retrieve the current supply of MicroAlgos reported by the ledger
const supply = await tatum.rpc.getLedgerSupply();

// Log the current supply
console.log('Algorand Current Supply:', supply);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getLedgerSupply` method allows you to retrieve the current supply of MicroAlgos reported by the ledger.

### Example Use Cases

1. **Supply Information**: Developers can use this method to retrieve the current supply of MicroAlgos in the Algorand system.

### Request Parameters

The `getLedgerSupply` method does not require any parameters.

### Return Object

The method returns an object representing the current supply of MicroAlgos in the Algorand system.

Please note that the structure of the returned object may change in different Algorand RPC versions.