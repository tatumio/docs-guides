---
title: "gettokensupply"
slug: "rpc-solana-gettokensupply"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const tokenMintPubkey = "3wyAj7Rt1TWVPZVteFJPLa26JmLvdb1CAKEFZm3NY75E"

const res = await tatum.rpc.getTokenSupply(tokenMintPubkey, config)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getTokenSupply` method returns the total supply of a specific SPL (Solana Program Library) Token in the network.

This method is especially useful for token issuers or traders who want to keep track of the total token supply for market analysis or supply management.

Another use case for this method is for financial services applications or DeFi protocols, where it is important to know the total supply of a token to calculate various financial metrics such as market capitalisation or liquidity.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/rNQRMxx",
  "href": "https://codepen.io/tatum-devrel/pen/rNQRMxx",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

This method takes the following parameters:

- `pubkey` (string, required): A string that represents the Pubkey of the token Mint to query.
- `options` (object, optional): This object can contain the following fields:
  - `commitment` (string, optional): Specifies the level of commitment to apply when fetching data.
    - Values: `finalized` `confirmed` `processed`

### Return Object

The result will be an RpcResponse JSON object with `value` equal to a JSON object containing:

- `amount`: The raw total token supply without decimals, a string representation of u64.
- `decimals`: The number of base 10 digits to the right of the decimal place.
- `uiAmount`: The total token supply, using mint-prescribed decimals. Note: This field is deprecated.
- `uiAmountString`: The total token supply as a string, using mint-prescribed decimals.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0", 
  "id": 1,
  "method": "getTokenSupply",
  "params": [
    "3wyAj7Rt1TWVPZVteFJPLa26JmLvdb1CAKEFZm3NY75E"
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "context": {
      "slot": 1114
    },
    "value": {
      "amount": "100000",
      "decimals": 2,
      "uiAmount": 1000,
      "uiAmountString": "1000"
    }
  },
  "id": 1
}
```
