---
title: "getProtocols"
slug: "rpc-tezos-getprotocols"
excerpt: "Tezos RPC"
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `getProtocols` method retrieves a list of protocol hashes for the Tezos blockchain. These protocol hashes represent different versions of the Tezos protocol that have been used or are available on the blockchain.

### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Tezos, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Tezos
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Call the getProtocols method to retrieve a list of protocol hashes
const protocols = await tatum.rpc.getProtocols();

// Log the list of protocol hashes
console.log('Protocols:', protocols);

// Always destroy the Tatum SDK instance when done to stop any background processes
tatum.destroy();
```

### Example Use Cases

1. **Protocol Version Information:**  
   Developers can use this method to obtain a list of protocol hashes to understand the available protocol versions on the Tezos network.

2. **Historical Analysis:**  
   Researchers and analysts can use this method to gather historical data on protocol versions used in the Tezos blockchain.

### Request Parameters

This method does not require any specific request parameters.

### Return Object

The `getProtocols` method returns an array of protocol hashes. Each protocol hash is represented as a string.

(Note: The exact fields in the return object might vary based on the Tezos blockchain's implementation and version.)
