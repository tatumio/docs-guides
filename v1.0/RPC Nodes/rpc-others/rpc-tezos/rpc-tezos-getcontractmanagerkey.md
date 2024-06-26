---
title: "getContractManagerKey"
slug: "rpc-tezos-getcontractmanagerkey"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Tezos, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Tezos
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Define the input parameters as a dictionary object
const params = {
    contractId: 'YOUR_CONTRACT_ID',     // Specify the contract ID
    chainId: 'YOUR_CHAIN_ID',           // Specify the chain ID (Network identifier)
    blockId: 'YOUR_BLOCK_ID'            // Optional: Specify the block ID if needed
};

// Retrieve the manager key of the implicit contract
const managerKey = await tatum.rpc.getContractManagerKey(params);

// Log the manager key
console.log(`Manager Key of Contract ${params.contractId}:`, managerKey);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getContractManagerKey` method is used to access the manager of an implicit contract in the Tezos blockchain. The manager key represents the entity responsible for managing the contract's operations.

### Example Use Cases:

1. **Contract Analysis:** Developers and auditors can use this method to retrieve the manager key of an implicit contract, providing insights into the contract's ownership and management.

2. **Contract Interaction:** Users may use this method to verify the manager's public key of a contract to ensure the validity of transactions.

### Request Parameters

The `getContractManagerKey` method requires the following parameters, all included in the `params` dictionary object:

- `contractId` (string, required): A contract identifier encoded in b58check, representing the implicit contract for which you want to access the manager key.
- `chainId` (string, required): The network identifier (chain ID) for the Tezos blockchain.
- `blockId` (string, required): The unique identifier (hash) of the block.

### Return Object

The method returns an object representing the manager key of the implicit contract. The manager key is a nullable field, and it can be one of the following:

- If a manager key exists, it is represented as a Tezos public key hash (Base58Check-encoded).

- If there is no manager key, the response is nullable, indicating that no manager key is associated with the contract.

Users can use this information to verify the ownership and management of the contract.
