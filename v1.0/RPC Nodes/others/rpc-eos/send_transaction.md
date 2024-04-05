---
title: "send_transaction"
slug: "rpc-eos-send_transaction"
excerpt: "Eos RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### Overview

The `send_transaction` method is designed to submit a transaction to the EOS blockchain. This method expects a transaction in JSON format and will attempt to apply it to the blockchain, enabling various blockchain interactions such as transferring tokens, invoking smart contracts, etc.
{% tabs %}
{% tab title="TypeScript/JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.sendTransaction({ 
  signatures: [/* array of signatures */], 
  compression: false, 
  packedContextFreeData: 'string', // json to hex
  packedTrx: 'string' // Transaction object json to hex
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}
### Example use cases:

1. **Transaction Submission:**
   Developers and users can utilize the `send_transaction` method to broadcast their transactions to the EOS network, enabling various blockchain interactions and operations.

2. **Smart Contract Interaction:**
   This method is crucial for invoking actions on smart contracts deployed on the EOS blockchain, allowing users to interact with decentralized applications.

3. **Token Transfer:**
   `send_transaction` is used for transferring EOS tokens or other tokens deployed on the EOS blockchain between accounts.

### Request Parameters

The `sendTransaction` method requires the following parameters in the request body:

- `signatures` (array of strings, required): Array of signatures required to authorize the transaction.
- `compression` (boolean): Compression used, usually false.
- `packedContextFreeData` (string): JSON converted to hex.
- `packedTrx` (string): Transaction object converted from JSON to hex.

### Return Object

The `send_transaction` method typically does not return any object but acknowledges with a 200 OK status upon a successful transaction broadcast.

### JSON-RPC Request Example

```json
{
  "signatures": ["SIG_K1_..."],
  "compression": false,
  "packed_context_free_data": "0x...",
  "packed_trx": "0x..."
}
```
### JSON-RPC Response Example

200 OK status implies successful broadcast, and typically no object is returned.