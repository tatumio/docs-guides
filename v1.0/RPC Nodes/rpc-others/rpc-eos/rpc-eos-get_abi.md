---
title: "get_abi"
slug: "rpc-eos-get_abi"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_abi` method is utilized to retrieve the ABI (Application Binary Interface) associated with an EOS account. ABI is critical for encoding and decoding the data correctly to interact with the smart contracts deployed by the account.  
{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getAbi({ accountName: 'b1' })

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Example use cases:

1. **Smart Contract Interaction:**  
   Developers can use the `get_abi` method to obtain the ABI of a smart contract, enabling them to interact with the contract's methods and access its state variables and structures.

2. **Data Encoding and Decoding:**  
   The method is crucial for encoding the data sent to a smart contract and decoding the data received from it, facilitating seamless interaction with smart contracts deployed on the EOS blockchain.

3. **Contract Development and Testing:**  
   `get_abi` is invaluable for developers in the development and testing phases of smart contract deployment, allowing for accurate and efficient contract interaction and validation.

### Request Parameters

The `getAbi` method usually requires one parameter in the request body:

- `accountName` (string, required): The name of the EOS account whose ABI is being requested.

### Return Object

The `get_abi` method typically returns an object containing the ABI details including the version, types, structs, actions, tables, and more, of the requested account:

- `version` (string): The version of the ABI.
- `types` (array): An array containing the types used in the ABI.
- `structs` (array): An array of structures defined in the ABI.
- `actions` (array): The actions that are defined in the ABI.
- `tables` (array): The tables that are defined in the ABI.
- `ricardian_clauses` (array): The ricardian clauses defined in the ABI.
- `error_messages` (array): Possible error messages that are defined in the ABI.
- `abi_extensions` (array): Any extensions to the ABI.

### JSON-RPC Request Example

```json
{
  "account_name": "b1"
}
```

### JSON-RPC Response Example

```json
{
  "version": "eosio::abi/1.0",
  "types": [...],
  "structs": [...],
  "actions": [...],
  "tables": [...],
  "ricardian_clauses": [...],
  "error_messages": [...],
  "abi_extensions": [...]
}
```
