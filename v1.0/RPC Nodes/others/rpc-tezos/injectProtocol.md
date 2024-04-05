---
title: "injectProtocol"
slug: "rpc-tezos-injectProtocol"
excerpt: "Tezos RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Tezos RPC"
  image: []
  keywords: "tezos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

```typescript code example
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Tezos, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK for Tezos
const tatum = await TatumSDK.init<Tezos>({ network: Network.TEZOS });

// Define the protocol information as an object
const protocolInfo = {
    expected_env_version: 'YOUR_ENV_VERSION',  // Replace with the expected environment version
    components: [
        {
            name: 'COMPONENT_NAME',           // Replace with the component name
            interface: 'COMPONENT_INTERFACE', // Replace with the component interface
            implementation: 'COMPONENT_IMPL'  // Replace with the component implementation
        }
    ]
    async: false  // Optional: Set to 'true' for asynchronous injection
};

// Inject a protocol into the node
const protocolId = await tatum.rpc.injectProtocol(protocolInfo);

// Log the protocol ID
console.log('Protocol ID:', protocolId);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `injectProtocol` method allows you to inject a protocol into the Tezos node. It returns the ID of the injected protocol. By default, the RPC waits for the protocol to be validated before returning. However, setting `async` to 'true' makes the function return immediately.

### Example Use Cases

1. **Protocol Upgrade:**
   Developers can use this method to inject protocol upgrades and improvements into the Tezos network.

2. **Network Maintenance:**
   Validators and administrators can inject protocol updates to perform network maintenance and ensure the stability and security of the blockchain.

### Request Parameters

The `injectProtocol` method accepts the following parameter:

- `expected_env_version` (string, required): 
  The expected environment version of the protocol.

- `components` (array of objects, required): 
  An array of components that make up the protocol. Each component should include:
  - `name` (string): The name of the component.
  - `interface` (string): The interface of the component.
  - `implementation` (string): The implementation of the component.

- `async` (boolean, optional): 
  Set to 'true' to receive an asynchronous response. Default is 'false'.

### Return Object

The `injectProtocol` method returns an object containing the ID of the injected protocol:

- `protocolId` (string): 
  A Tezos protocol ID in Base58Check-encoded format.

(Note: The exact fields in the return object might vary based on the Tezos blockchain's implementation and version.)