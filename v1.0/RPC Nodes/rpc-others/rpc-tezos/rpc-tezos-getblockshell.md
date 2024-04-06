---
title: "getBlockShell"
slug: "rpc-tezos-getblockshell"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 05 2024 16:43:26 GMT+0000 (Coordinated Universal Time)"
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

// Define parameters for the query
const params = {
  chainId: 'YOUR_CHAIN_ID', // Required
  blockId: 'YOUR_BLOCK_ID' // Required
};

// Fetching the block header shell
const blockHeaderShell = await tatum.rpc.getBlockShell(params);
console.log(blockHeaderShell);

// Cleaning up resources used by Tatum SDK
await tatum.destroy();
```

### Overview

The `getBlockShell` method is used to retrieve the shell header of a specific block on the Tezos blockchain.

### Request Parameters

- `chainId` (string, required): The ID of the chain.
- `blockId` (string, required): The unique identifier (hash) of the block for which you want to retrieve the shell header.

### Return Object

The method returns an object representing the shell header of the specified block on the Tezos blockchain.

- `level` (integer): The level (block number) of the block, e.g., 4000000.
- `proto` (integer): The protocol version of the block, e.g., 17.
- `predecessor` (string): The hash of the block's predecessor, e.g., "BMR5RnbukbbDw3ZXN1RbKEPYg6aFvLQuCgxPBhRLg3vmdVLbLJv".
- `timestamp` (string): The timestamp of the block, e.g., "2023-08-05T07:23:15Z".
- `validation_pass` (integer): The number of validation passes, e.g., 4.
- `operations_hash` (string): The hash of the operations included in this block, e.g., "LLoaEA9PAMVP7HGpdb4nKLM8oyVnSMy5gJBEwyftjCsyk7EhnvSm7".
- `fitness` (array): An array of fitness values, e.g.,
- `context` (string): The context hash of the block, e.g., "CoW4EjrMzokDdz8v8qBPMXhrjStzuQU9bSGNFHsyej6mNkY89g7f".

(Note: The exact fields in the return object might vary based on the Tezos blockchain's implementation and version.)
