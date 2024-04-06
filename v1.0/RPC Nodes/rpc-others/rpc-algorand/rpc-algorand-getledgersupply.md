---
title: "getLedgerSupply"
slug: "rpc-algorand-getledgersupply"
excerpt: "Algorand RPC"
hidden: false
metadata: 
  description: "Algorand RPC"
  image: []
  keywords: "algorand, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



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
