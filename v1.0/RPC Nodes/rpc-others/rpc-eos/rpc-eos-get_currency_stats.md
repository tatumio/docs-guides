---
title: "get_currency_stats"
slug: "rpc-eos-get_currency_stats"
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

The `get_currency_stats` method is utilized to retrieve the statistics for a specific currency on the EOS blockchain. By employing this method, users and developers can obtain crucial information about a currency, such as its supply, maximum supply, and issuer, thereby enabling in-depth analysis and insights into the currency's status and distribution.

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Eos, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Eos>({ network: Network.EOS })

const response = await tatum.rpc.getCurrencyStats({
  code: 'eosio.token',
  symbol: 'EOS'
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Example use cases:

1. **Token Analysis:**  
   Individuals and analysts can utilize the `get_currency_stats` method to gather comprehensive details about a token's supply and issuer, facilitating profound analysis and research on the token’s characteristics and distribution.

2. **Smart Contract Interaction:**  
   Developers can use this method to obtain necessary information about a token, which can aid in interacting efficiently with smart contracts that deal with tokens, for operations like transferring tokens or querying balances.

3. **Market Analysis:**  
   `get_currency_stats` is instrumental for acquiring essential details about a token, which are critical for performing market analysis. This enables users and potential investors to make informed and insightful decisions based on the available token data.

### Request Parameters

The `getCurrencyStats` method requires the following parameters in the request body:

- `code` (string, required): The contract that operates the token.
- `symbol` (string, required): The symbol of the token for which the statistics are being requested.

### Return Object

The `get_currency_stats` method typically returns an object containing the statistics of the requested currency. This object includes:

- `supply` (string): The total supply of the token in circulation.
- `max_supply` (string): The maximum supply of the token that can ever be created.
- `issuer` (string): The account name of the issuer of the token.

### JSON-RPC Request Example

```json
{
  "code": "eosio.token",
  "symbol": "EOS"
}
```

### JSON-RPC Response Example

```json
{
    "EOS": {
        "supply": "1168690795.8555 EOS",
        "max_supply": "10000000000.0000 EOS",
        "issuer": "eosio"
    }
}
```
