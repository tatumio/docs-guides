---
title: "getContractBalance"
slug: "rpc-tezos-getcontractbalance"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Importing Tatum SDK for Tezos blockchain
import { TatumSDK, Network, Tezos } from '@tatumio/tatum';

// Initializing SDK for Tezos blockchain
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Define your chain ID and contract address
const params = { 
    chainId: 'YOUR_CHAIN_ID',           // Specify the chain ID (Network identifier)
    blockId: 'YOUR_BLOCK_ID',           // Optional: Specify the block ID 
    contractId: 'YOUR_CONTRACT_ID'      // Specify the contract ID
};

// Fetching contract balance
const contractBalance = await tatum.rpc.getContractBalance(params);
console.log(contractBalance);

// Cleaning up resources used by Tatum SDK
await tatum.destroy();
```

### Overview

The `getContractBalance` method retrieves the balance of a specific smart contract on the Tezos blockchain.

### Parameters

- `chainId` (string, required): The ID of the chain where the smart contract is deployed.
- `blockId` (string, required): The unique identifier (hash) of the block.
- `contractAddress` (string, required): The address of the smart contract

### Return Object

The method returns an object containing the `balance` of the specified smart contract. The structure of the return object may include various fields depending on the contract's status and balance.

(Note: The exact fields in the return object might vary based on the Tezos blockchain's implementation and version.)
