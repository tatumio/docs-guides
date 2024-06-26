---
title: "get_code"
slug: "rpc-eos-get_code"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_code` method returns an object containing the smart contract WASM code for a specified account on the EOS blockchain. This method is paramount for developers who are looking to analyze or understand the WASM code of deployed smart contracts, enabling an in-depth interaction and integration with the smart contracts.  


```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getCode({
  accountName: "eosio.token",
  codeAsWasm: 1
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Example use cases:

1. **Smart Contract Analysis:**  
   Developers use this method to retrieve and analyze the WASM code of smart contracts, allowing for comprehensive understanding and debugging of the contract logic.

2. **WASM Code Inspection:**  
   This method is vital for users and developers wishing to inspect the WASM code, ensuring the contract's integrity, functionality, and security.

3. **Enhanced Integration and Interaction:**  
   Retrieving the WASM code facilitates seamless integration and interaction with smart contracts, ensuring proper deployment, execution, and management of contracts on the EOS blockchain.

### Request Parameters

The `getCode` method requires the following parameters in the request body:

- `accountName` (string, required): The name of the account whose smart contract WASM code needs to be retrieved. Acceptable types are NamePrivileged, NameBasic, NameBid, and NameCatchAll.
- `codeAsWasm` (integer, required): This must be 1 (true).

### Return Object

The `get_code` method returns an object containing:

- `name` (string): The name of the account from which the WASM code was retrieved. Acceptable types are NamePrivileged, NameBasic, NameBid, and NameCatchAll.
- `code_hash` (string): A Sha256 hash representing the WASM code of the retrieved smart contract.
- `wast` (string): The WebAssembly text format representation of the smart contract.
- `wasm` (string): The WebAssembly binary representation of the smart contract.
- `abi` (object): The ABI (Application Binary Interface) of the smart contract, representing the binary representation of the contract's interface.

### JSON-RPC Request Example

```json
{
  "accountName": "eosio.token",
  "codeAsWasm": 1
}
```

### JSON-RPC Response Example

```json
{
  "name": "eosio.token",
  "code_hash": "a1b2c3d4e5f67890abcdef1234567890abcdef1234567890abcdef1234567890ab",
  "wast": "... (WAST string) ...",
  "wasm": "... (WASM binary string) ...",
  "abi": { ... (ABI object) ... }
}

```
