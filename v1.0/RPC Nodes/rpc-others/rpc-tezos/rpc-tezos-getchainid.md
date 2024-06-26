---
title: "getChainId"
slug: "rpc-tezos-getchainid"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
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

// Fetch the unique chain identifier for a specific Tezos chain using the getChainId method
const chainIdentifier = await tatum.rpc.getChainId({
  chainId: 'main'  // Specify the Tezos chain ID (usually 'main' for mainnet)
});

console.log(`The unique identifier for the chain is: ${chainIdentifier}`);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getChainId` method retrieves the unique identifier of a specified chain in Tezos.

### Example use cases:

1. **Chain Verification:**  
   To ensure that interactions and transactions are occurring on the intended Tezos chain, developers and users can validate the chain's unique identifier.

2. **Multi-chain Environments:**  
   In setups where multiple Tezos chains might be in use, this method can differentiate and identify each chain uniquely.

3. **Dynamic Chain Configuration:**  
   For applications that adapt to multiple chain environments, the method provides a way to fetch and set the active chain based on its identifier.

### Request Parameters

The `getChainId` method requires:

- `chainId` (string, required):  
  The identifier of the Tezos chain from which the unique chain identifier is being requested.

### Return Object

The `getChainId` method returns a string:

- The unique identifier of the specified chain.
