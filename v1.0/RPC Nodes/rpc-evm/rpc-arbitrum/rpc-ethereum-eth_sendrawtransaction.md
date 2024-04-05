---
title: "eth_sendRawTransaction"
slug: "rpc-arbitrum-eth_sendrawtransaction"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 08:12:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:04:39 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The`eth_sendRawTransaction`  RPC method is used to facilitate the transmission of a signed and serialized Ethereum transaction onto the network. This approach proves invaluable when seeking complete oversight of the signing procedure, especially when employing hardware wallets, cold storage solutions, or custom signing libraries. Its versatility shines through in multiple scenarios, including Ether transfers, smart contract interactions, and contract deployments.

## Parameters

`Transaction data`: This is a required parameter. It is a hex string that represents the signed transaction data. This data must be prepared and signed offline or through a wallet before being sent to the network.

## Returns

The response from the `eth_sendRawTransaction` method is a JSON object containing the following fields:

| Name    | Description                                                                                                        |
| :------ | :----------------------------------------------------------------------------------------------------------------- |
| jsonrpc | A string indicating the version of the JSON-RPC protocol. It should be "2.0".                                      |
| id      | A number that identifies the request. This should match the id value in the request.                               |
| result  | The transaction hash of the sent transaction. If the transaction is not yet available, this will be the zero hash. |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_sendRawTransaction",
  "params": [
    "0xf86d8201...94a7bc"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const gasPrice = await tatum.rpc.sendRawTransaction('0x0000.......')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
