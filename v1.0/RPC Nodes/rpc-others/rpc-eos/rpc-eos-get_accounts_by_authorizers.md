---
title: "get_accounts_by_authorizers"
slug: "rpc-eos-get_accounts_by_authorizers"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 05 2024 16:29:32 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_accounts_by_authorizers` method retrieves accounts associated with specific authorizers, serving as an essential tool for developers and users interested in understanding account access and control on the EOS blockchain.  
{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getAccountsByAuthorizers({
  accounts: ["eosio"]
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Example use cases:

1. **Account Access Analysis:**  
   Developers can utilize this method to discern which accounts have access through specific authorizers, fortifying access control and security management.

2. **Permission Management:**  
   Users managing multiple accounts can benefit from this method by identifying which accounts are controlled by specific authorizers, optimizing permission management processes.

3. **Enhanced Account Retrieval:**  
   This method facilitates the retrieval of accounts based on specific authorizers, fostering efficient data interaction and management on the EOS blockchain.

### Request Parameters

The `getAccountsByAuthorizers` method requires the following parameters in the request body:

- `keys` (array of strings): An array of public keys used to retrieve accounts.
- `accounts` (array of strings): An array of account names used to retrieve accounts.
  - `actor` (string, required): Name of the actor.
  - `permission` (string, required): Specifies the permission name.

### Return Object

The `get_accounts_by_authorizers` method typically returns an object containing:

- `accounts` (array of strings): An array of account names associated with the provided authorizers.

### JSON-RPC Request Example

```json
{
  "keys": ["EOS6MRy..."],
  "accounts": ["eosio"]
}
```

### JSON-RPC Reponse Example

```json
{
  "accounts": ["account1", "account2"]
}
```
