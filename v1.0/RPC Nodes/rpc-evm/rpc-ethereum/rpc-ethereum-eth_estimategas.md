---
title: "eth_estimateGas"
slug: "rpc-ethereum-eth_estimategas"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 07:00:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:04:13 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`eth_estimateGas` method in Ethereum's JSON-RPC API is used to estimate the amount of gas that would be required to execute a transaction without actually sending it. This method is particularly useful for determining the appropriate gas limit for a transaction before it is submitted to the network, helping to avoid out-of-gas errors and ensuring that transactions are processed efficiently.

## Parameters

`eth_estimateGas` method accepts a single parameter, which is an object containing the details of the transaction you wish to estimate. The object can include the following fields:

| Name      | Type   | Required | Description                                                                                             |
| :-------- | :----- | :------- | :------------------------------------------------------------------------------------------------------ |
| from      | String | Yes      | The address that the transaction is sent from.                                                          |
| to        | String | Yes      | The address the transaction is sent to.                                                                 |
| gas       | String | No       | The maximum amount of gas provided for the transaction.                                                 |
| gasPrice  | String | No       | The price of gas in wei.                                                                                |
| value     | String | No       | The amount of ether to send in the transaction, in wei.                                                 |
| data      | String | No       | The data payload of the transaction, typically used for contract function calls or contract deployment. |
| nonce     | String | No       | A fake nonce to set for the account before executing the call.                                          |
| code      | String | No       | The code to be executed.                                                                                |
| state     | String | No       | The state to be used for the execution.                                                                 |
| stateDiff | String | No       | The state diff to be used for the execution                                                             |

## Returns

The response from the `eth_estimateGas` method is a single value representing the estimated amount of gas that would be used by the transaction. This value is returned as a hexadecimal string.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/API_KEY/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_estimateGas",
  "params": [
    {
      "from": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "to": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "value": "0xde0b6b3a7640000",
      "data": "0x606060"
    }
  ]
}'

```
```javascript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const estimate = await tatum.rpc.estimateGas({
      "from": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "to": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "value": "0xde0b6b3a7640000",
      "data": "0x606060"
    })
    
await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
