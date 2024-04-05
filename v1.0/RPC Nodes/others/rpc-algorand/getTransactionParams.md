---
title: "getTransactionParams"
slug: "rpc-algorand-getTransactionParams"
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

// Retrieve transaction parameters for constructing a new transaction
const transactionParams = await tatum.rpc.getTransactionParams();

// Log the transaction parameters
console.log('Transaction Parameters:', transactionParams);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getTransactionParams` method allows you to retrieve the parameters that help a client construct a new transaction in Algorand.

### Example Use Cases

1. **Transaction Construction**: Developers can use this method to get the necessary parameters required for constructing a new transaction in Algorand.

### Request Parameters

The `getTransactionParams` method does not require any parameters.

### Return Object

The method returns an object representing the parameters that help a client construct a new transaction in Algorand. The returned object includes the following properties:

- `consensus-version` (string): Indicates the consensus protocol version as of LastRound.
- `fee` (integer): The suggested transaction fee. The fee is in units of micro-Algos per byte. The fee may fall to zero but transactions must still have a fee of at least MinTxnFee for the current network protocol.
- `genesis-hash` (string): The hash of the genesis block.
- `genesis-id` (string): An ID listed in the genesis block.
- `last-round` (integer): Indicates the last round seen.
- `min-fee` (integer): The minimum transaction fee (not per byte) required for the transaction to validate for the current network protocol.

Please note that the structure of the returned object may change in different Algorand RPC versions.