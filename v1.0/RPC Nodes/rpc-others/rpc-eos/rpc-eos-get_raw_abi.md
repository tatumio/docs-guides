---
title: "get_raw_abi"
slug: "rpc-eos-get_raw_abi"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_raw_abi` method is used to fetch the raw, serialized ABI (Application Binary Interface) for a specified account, providing essential details needed for interacting with smart contracts on the EOS network.

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const rawAbi = await tatum.rpc.getRawAbi({ accountName: 'b1' })

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Example use cases:

1. **Smart Contract Interaction:**  
   Developers or users may use the `get_raw_abi` method to obtain the raw ABI of a smart contract, essential for decoding binary data and enabling effective interaction with the contract.
2. **ABI Analysis and Verification:**  
   The method allows developers and analysts to study and analyze the ABI of a contract, verify its integrity, and understand its structure and methods by comparing the retrieved `abi_hash` with known hash values.
3. **Development and Debugging:**  
   This method is crucial for developers during the development and debugging phases, enabling quick access to and assessment of the ABI, ensuring alignment with the contract’s intended design and functionality.

### Request Parameters

The `getRawAbi` method has one parameter:

- `accountName` (string, required): The unique EOSIO account name of the smart contract whose ABI is to be retrieved.

### Return Object

The `get_raw_abi` method returns an object with the following parameters:

- `account_name` (string, required): The name of the account whose ABI was retrieved.
- `code_hash` (string, required): The hash of the smart contract code.
- `abi_hash` (string, required): The hash of the ABI of the smart contract.
- `abi` (string, required): The raw, serialized ABI data.

### JSON-RPC Request Example

```json
{
  "account_name": "b1"
}
```

### JSON-RPC Response Example

```json
{
    "account_name": "b1",
    "code_hash": "0000000000000000000000000000000000000000000000000000000000000000",
    "abi_hash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "abi": ""
}
```
