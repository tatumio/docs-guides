---
title: "eth_estimategas"
slug: "rpc-base-eth_estimategas"
excerpt: "Base RPC"
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const estimate = await tatum.rpc.estimateGas({
  from: "0x73d28fEB113D3E24C94F813c383D18D94080c6C8",
  to: "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
  value: "0x1",
});

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_estimateGas` is an method that estimates the amount of gas required to execute a given transaction. This method can be used to determine the gas cost before sending a transaction, allowing developers to better predict the gas fees and avoid issues like out-of-gas errors.

Use cases for `eth_estimateGas` include:

- Estimating gas costs for contract deployments
- Estimating gas costs for contract function calls
- Estimating gas costs for standard ether transfers

### Parameters

The `eth_estimateGas` method takes a single parameter, an object representing the transaction details. The fields in the transaction object include:

- **`from`** (optional, string): The address that the transaction is sent from.
  - Example: `"from": "0x73d28fEB113D3E24C94F813c383D18D94080c6C8"`
- **`to`** (optional, string): The address the transaction is sent to.
  - Example: `"to": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
- **`gas`** (optional, string): The maximum amount of gas provided for the transaction.
  - Example: `"gas": "0x76c0"`
- **`gasPrice`** (optional, string): The price of gas in wei.
  - Example: `"gasPrice": "0x9184e72a000"`
- **`value`** (optional, string): The amount of ether to send in the transaction, in wei.
  - Example: `"value": "0xde0b6b3a7640000"`
- **`data`** (optional, string): The data payload of the transaction, typically used for contract function calls or contract deployment.
  - Example: `"data": "0x606060..."`
- **`nonce`** (optional, string): The transaction count of the `from` address.
  - Example: `"nonce": "0x1"`

### Return Object

The return value of the `eth_estimateGas` method is a single field:

- `gasEstimate` (string): The estimated gas cost for the transaction, represented as a hexadecimal string.
  - Example: `"0x5208"`

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x5208"
}
```
