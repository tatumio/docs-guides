---
title: "getNetworkList"
slug: "rpc-cardano-getnetworklist"
excerpt: "Cardano RPC"
hidden: false
metadata: 
  description: "Cardano RPC"
  image: []
  keywords: "cardano, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:42 GMT+0000 (Coordinated Universal Time)"
---



### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, CardanoRosetta, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Cardano
const tatum = await TatumSDK.init<CardanoRosetta>({ network: Network.CARDANO_ROSETTA });

// Optional metadata parameter
const params = metadata: {
                [key: string]: any,  // object (optional)
            }, 

// Call the `getNetworkList` method
const networkList = await tatum.rpc.getNetworkList(params);

// Log the network list
console.log('Network List:', networkList);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getNetworkList` method allows you to retrieve a list of available networks that the Rosetta server supports.

### Example Use Cases

1. **Supported Networks**: Developers can use this method to retrieve the list of networks supported by the Rosetta server.

### Request Parameters

The `getNetworkList` method has only optional metadata object.

- `metadata` (object, optional)

### Return Object

The method returns an object representing the list of available networks supported by the Rosetta server.

Structure and behavior of this method may vary with different versions of the Cardano service. Always refer to the documentation specific to the version you are using for the most accurate information.
