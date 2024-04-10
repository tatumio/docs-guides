---
title: "account_currencies"
slug: "rpc-xrp-account_currencies"
excerpt: "XRP RPC"
hidden: false
metadata: 
  description: "XRP RPC"
  image: []
  keywords: "xrp, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Xrp, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Xrp>({network: Network.XRP})

const res = await tatum.rpc.accountCurrencies('r9cZA1mLK5R5Am25ArfXFmqgNwjZgnfk59', {
  ledgerIndex: 'validated',
  strict: true
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

### Overview

The `accountCurrencies` method retrieves a list of currencies that an account can send or receive, based on its trust lines. This isn't a thoroughly confirmed list but can be used to populate user interfaces.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/gOQyjNx",
  "href": "https://codepen.io/tatum-devrel/pen/gOQyjNx",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The method accepts two parameters:

- `account` (**required**): A unique identifier for the account, most commonly the account's Address.
- `options` (**optional**): An object with the following properties:
  - `ledgerHash`: A 20-byte hex string for the ledger version to use.
  - `ledgerIndex`: The ledger index of the ledger to use, or a shortcut string to choose a ledger automatically.
  - `strict`: If true, then the `account` field only accepts a public key or XRP Ledger address. Otherwise, `account` can be a secret or passphrase (not recommended). The default is false.

### Return Object

The `accountCurrencies` method returns an object with following fields:

- `ledger_hash` (String - Hash): May be omitted. The identifying hash of the ledger version used to retrieve this data, as hex.
- `ledger_index` (Integer - Ledger Index): The ledger index of the ledger version used to retrieve this data.
- `receive_currencies` (Array of Strings): Array of Currency Codes for currencies that this account can receive.
- `send_currencies` (Array of Strings): Array of Currency Codes for currencies that this account can send.
- `validated` (Boolean): If true, this data comes from a validated ledger.\\

### JSON-RPC Request Example

Here's an example of how the JSON-RPC request might look like:

```json
{
  "command": "account_currencies",
  "account": "r9cZA1mLK5R5Am25ArfXFmqgNwjZgnfk59",
  "strict": true,
  "ledger_index": "validated"
}
```

### JSON-RPC Response Example

Here's an example of how the JSON-RPC response might look like:

```json
{
  "result": {
    "ledger_index": 11775844,
    "receive_currencies": ["BTC", "CNY", "DYM", "EUR", "JOE", "MXN", "USD", "015841551A748AD2C1F76FF6ECB0CCCD00000000"],
    "send_currencies": ["ASP", "BTC", "CHF", "CNY", "DYM", "EUR", "JOE", "JPY", "MXN", "USD"],
    "validated": true
  },
  "status": "success",
  "type": "response"
}
```
