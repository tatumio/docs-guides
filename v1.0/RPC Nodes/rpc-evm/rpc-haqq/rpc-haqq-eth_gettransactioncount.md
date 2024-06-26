---
title: "eth_gettransactioncount"
slug: "rpc-haqq-eth_gettransactioncount"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:36 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const result = await tatum.rpc.getTransactionCount('0x2eAd3B147fc20fB03fd25C71c1677E81714A9Eb5', 'latest')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_getTransactionCount` method is an Haqq JSON-RPC method that retrieves the number of transactions sent from a given address. It is a useful method for developers who need to keep track of an account's nonce value to avoid transaction collisions or incorrect order of execution. The nonce value is essential for ensuring transaction uniqueness and preventing replay attacks.

Use cases for this method include:

- Determining the nonce value for a new transaction to be sent from a specific address
- Monitoring the number of transactions sent by an address to observe its activity
- Troubleshooting transaction issues and verifying if a transaction was submitted successfully

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Jan-Musil-the-lessful/pen/RwqvOmO?editors=1111",
  "href": "https://codepen.io/Jan-Musil-the-lessful/pen/RwqvOmO?editors=1111",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `eth_getTransactionCount` method accepts two parameters:

1. **`address`** - The Haqq address whose transaction count will be retrieved.
   - Example: `"0x2eAd3B147fc20fB03fd25C71c1677E81714A9Eb5"`
2. **`blockParameter`** - A string indicating the block number or block state to consider when retrieving the transaction count.
   - Possible values: `"earliest"`, `"latest"`, `"pending"`, or a specific block number in hexadecimal format
   - Example: `"latest"`

### Return Object

The method returns a single value:

- **`transactionCount`** - A hexadecimal representation of the number of transactions sent from the specified address.
  - Example: `"0x1e"`

### JSON-RPC Request and Response Examples

_Request_:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getTransactionCount",
  "params": [
    "0x2eAd3B147fc20fB03fd25C71c1677E81714A9Eb5",
    "latest"
  ]
}
```

_Response_:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1e"
}
```
