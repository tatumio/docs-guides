---
title: "get_raw_code_and_abi"
slug: "rpc-eos-get_raw_code_and_abi"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_raw_code_and_abi` method is used to retrieve both the raw code and the ABI (Application Binary Interface) for a contract, based on the account name. This is pivotal for developers who wish to interact with, decode, and understand the underlying code and interfaces of smart contracts deployed on the EOS blockchain.



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getRawCodeAndAbi({ accountName: 'eosio' })

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Example use cases:

1. **Understanding Smart Contracts:**  
   Developers can use the `get_raw_code_and_abi` method to gain insights into the raw code and ABI of smart contracts, enabling them to understand and interact with the contract's methods, state variables, and structures more effectively.

2. **Development and Debugging:**  
   This method is crucial for developers in the development and debugging phases, allowing for precise interaction and validation of the contract's code and interfaces, thereby facilitating a smoother development process.

3. **Enhanced Interaction with Smart Contracts:**  
   With the detailed insight provided by this method, developers can optimize their interaction with the smart contracts, making the development of decentralized applications more efficient and robust.

### Request Parameters

The `geRrawCodeAndAbi` method requires the following parameter in the request body:

- `accountName` (string, required): This can be `NamePrivileged`, `NameBasic`, `NameBid`, or `NameCatchAll`. It represents the name of the account for which the raw code and ABI are being requested.

### Return Object

Upon a successful request, the method returns an object containing the following details:

- `account_name` (string): Name of the account.
- `wasm` (string): The base64 encoded WebAssembly (WASM) code of the smart contract.
- `abi` (string): The base64 encoded ABI of the smart contract.

### JSON-RPC Request Example

```json
{
  "account_name": "eosio"
}
```

### JSON-RPC Response Example

```json
{
  "account_name": "eosio",
  "wasm": "base64EncodedWASM",
  "abi": "base64EncodedABI"
}
```
