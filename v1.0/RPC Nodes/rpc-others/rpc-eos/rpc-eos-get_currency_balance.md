---
title: "get_currency_balance"
slug: "rpc-eos-get_currency_balance"
excerpt: "Eos RPC"
hidden: false
metadata: 
  description: "Eos RPC"
  image: []
  keywords: "eos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### Overview

The `get_currency_balance` method is used to retrieve the balance of a specific currency/token for a given account on the EOS blockchain. This method is essential for users and developers who wish to query and manage account balances, ensuring accurate and up-to-date financial data.



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getCurrencyBalance({
  account: 'eosio',
  code: 'eosio.token',
  symbol: 'EOS'
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Example use cases:

1. **Balance Querying:**  
   Users and developers can utilize the `get_currency_balance` method to query the balances of specific currencies or tokens, enabling effective account management and financial planning.

2. **Financial Management:**  
   This method is pivotal for financial management in decentralized applications, allowing for the implementation of features related to balance checking, fund transfer validations, and more.

3. **Smart Contract Interaction:**  
   Developers can leverage this method to interact with token contracts to retrieve the balance of an account, facilitating the development of functionalities around token transactions and balance validations in dApps.

### Request Parameters

The `getCurrencyBalance` method requires the following parameters in the request body:

- `account` (string, required): The name of the account for which the balance is being requested.
- `code` (string, required): The smart contract that operates the currency.
- `symbol` (string, optional): The symbol of the currency/token. If not provided, the balances of all tokens available under the smart contract will be returned.

### Return Object

Upon a successful request, the method returns an array containing the balances of the specified currency/token for the given account:

- Each item in the array represents a balance in the format `"amount SYMBOL"` (e.g., `"100.0000 EOS"`).

### JSON-RPC Request Example

```json
{
  "account": "eosio",
  "code": "eosio.token",
  "symbol": "EOS"
}
```

### JSON-RPC Response Example

```json
[
    "1667.0290 EOS"
]
```
