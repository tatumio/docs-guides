---
title: "get_required_keys"
slug: "rpc-eos-get_required_keys"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_required_keys` method returns the required keys that are needed to sign a transaction. This feature is extremely valuable for users and developers aiming to ensure secure and accurate transaction signatures, thus maintaining the integrity of transactions within the EOS blockchain.

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getRequiredKeys({
  transaction: { /* Transaction Object. See request params below. */ },
  availableKeys: ["EOS..."]
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Example use cases:

1. **Secure Transaction Signing:**  
   Users and developers can use the `get_required_keys` method to identify the specific keys required to sign a transaction, enhancing the security and accuracy of the signing process and avoiding unauthorized or faulty transactions.

2. **Blockchain Interaction:**  
   This method is crucial for interactions and operations on the EOS blockchain where transactions are involved, ensuring that only the correct keys are utilized to sign the transactions, maintaining the validity and authenticity of the transactions.

3. **Smart Contract Interaction:**  
   Developers interacting with smart contracts on the EOS blockchain can leverage this method to determine the appropriate keys to sign transactions related to smart contract execution, thereby maintaining the correctness and reliability of contract interactions.

### Request Parameters

The `getRequiredKeys` method mandates the following parameters in the request body:

- `transaction` (object, required): Represents the transaction that is set to be signed. 
  - `expiration`: (string, required) - A date and time indicating when the transaction expires.
  - `refBlockNum`: (number, required) - The reference block number.
  - `refBlockPrefix`: (number, required) - The reference block prefix.
  - `maxNetUsageWords`: (string | number, required) - The maximum net usage words.
  - `maxCpuUsageMs`: (string | number, required) - The maximum CPU usage in milliseconds.
  - `delaySec`: (number, required) - The delay in seconds.
  - `contextFreeActions`: (Array of Action, required) - Context-free actions.
    - `account`: (string, required) - EOSIO account name.
    - `name`: (string, required) - Name of the action.
    - `authorization`: (Array of objects, required)
      - `actor`: (string, required) - EOSIO account name that is the actor.
      - `permission`: (string, required) - Permission level for the actor.
    - `data`: (object, required)
    - `hexData`: (string, required) - Hexadecimal representation of the data for the action.
  - `actions` (Array of objects, required)
    - `account`: (string, required) - EOSIO account name.
    - `name`: (string, required) - Name of the action.
    - `authorization` (Array of objects, required)
      - `actor`: (string, required) - EOSIO account name that is the actor.
      - `permission`: (string, required) - Permission level for the actor.
    - `data`: (object, required)
    - `hexData`: (string, required) - Hexadecimal representation of the data for the action.
- `availableKeys` (array of strings, required): Represents the available public keys.

### Return Object

The `get_required_keys` method typically returns an object containing the keys that are required to sign the transaction.

### JSON-RPC Request Example

```json
{
  "transaction": { /* Transaction Object */ },
  "available_keys": ["EOS..."]
}
```

## JSON-RPC Response Example

```json
{
  "required_keys": ["EOS..."]
}
```
