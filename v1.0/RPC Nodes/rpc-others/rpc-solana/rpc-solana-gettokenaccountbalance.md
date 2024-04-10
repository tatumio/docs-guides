---
title: "gettokenaccountbalance"
slug: "rpc-solana-gettokenaccountbalance"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:43 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getTokenAccountBalance('DhzDoryP2a4rMK2bcWwJxrE2uW6ir81ES8ZwJJPPpxDN')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getTokenAccountBalance` method provides the ability to fetch the current balance of a given SPL Token account. It is used when you want to know the amount of tokens held in a specific token account. The token account is specified by its public key.

{% embed url="<https://codepen.io/tatum-devrel/pen/KKrEzqq"> %}

### Parameters

This method accepts two parameters:

- `pubkey` (string, required): Pubkey of Token account to query, as base-58 encoded string
  - Example: `"DhzDoryP2a4rMK2bcWwJxrE2uW6ir81ES8ZwJJPPpxDN"`
- `options` (object, optional): Configuration object containing the following fields:
  - `commitment` (string, optional): Specifies the confirmation level of data to be fetched.
    - Values: `finalized` `confirmed` `processed`

### Return object

The `getTokenAccountBalance` method returns an object containing the following fields:

- `value`: An object containing:
  - `amount`: The raw balance without decimals, a string representation of number
  - `decimals`: Number of base 10 digits to the right of the decimal place
  - `uiAmount`: Number or null. The balance, using mint-prescribed decimals **DEPRECATED**
  - `uiAmountString`: The balance as a string, using mint-prescribed decimals

If `withContext` is set to true, the response will also include a `context` object:

- `context`: An object containing details about the context in which the data was fetched.
  - `slot`: The slot at which the data was fetched.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getTokenAccountBalance",
  "params": [
    "rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn",
    {
      "commitment": "finalized",
      "encoding": "base64"
    }
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "context": {
      "slot": 123456
    },
    "value": {
      "amount": "10000",
      "decimals": 6,
      "uiAmount": 0.01,
      "uiAmountString": "0.01"
    }
  }
}
```
