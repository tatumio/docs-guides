---
title: "getContract"
slug: "rpc-tezos-getcontract"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
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
    blockId: 'YOUR_BLOCK_ID',           // Optional: Specify the block ID if needed
    normalizeTypes: false               // Optional: Set to true if you want to normalize types
};

// Access the complete status of a contract
const contractStatus = await tatum.rpc.getContract(params);

// Log the contract status
console.log(`Status of Contract ${params.contractId}:`, contractStatus);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getContract` method allows you to access the complete status of a contract in the Tezos blockchain. This includes information about the contract's balance, delegate, script, and counter.

### Example Use Cases:

1. **Contract Analysis:** Developers and auditors can use this method to retrieve detailed information about a specific contract, including its balance, delegate, script, and counter.

2. **Contract Interaction:** Users may want to examine the status of a contract to verify its current balance or delegate.

### Request Parameters

The `getContract` method requires the following parameters, all included in the `params` dictionary object:

- `contractId` (string, required): A contract identifier encoded in b58check, representing the contract for which you want to access the status.

- `chainId` (string, required): The network identifier (chain ID) for the Tezos blockchain.

- `blockId` (string, optional): The unique identifier (hash) of the block. This parameter is optional, and if not provided, the method will retrieve the status from the latest block.

- `normalizeTypes` (boolean, optional): Whether types should be normalized (annotations removed, combs flattened) or kept as they appeared in the original script. Set to `true` for normalization or `false` to keep original types.

### Return Object

The method returns an object representing the complete status of the specified contract, including the following properties:

- `balance` (positive big number): The balance of the contract, represented as a positive big number.

- `delegate` (public key hash): The delegate of the contract, represented as a Tezos public key hash (Base58Check-encoded).

- `script` (scripted contract): The script associated with the contract, represented as a scripted contract object.

- `counter` (positive big number): The counter of the contract, represented as a positive big number.

Users can utilize this information for various purposes, such as contract analysis and verification.
