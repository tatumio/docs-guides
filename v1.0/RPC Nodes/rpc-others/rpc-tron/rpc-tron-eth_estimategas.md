---
title: "eth_estimategas"
slug: "rpc-tron-eth_estimategas"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:46 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

// Initialize the SDK for the TRON network
const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const estimate = await tatum.rpc.estimateGas({
      "from": "0xa41d19F4258a388c639B7CcD938FCE3fb7D05e86",
      "to": "0xa41d19F4258a388c639B7CcD938FCE3fb7D05e87",
      "value": "0xde0b6b3a7640000",
      "data": "0x606060"
    })
    
 await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`eth_estimateGas` is an JSON-RPC method that estimates the amount of gas required to execute a given transaction. This method can be used to determine the gas cost before sending a transaction, allowing developers to better predict the gas fees and avoid issues like out-of-gas errors.

Use cases for `eth_estimateGas` include:

- Estimating gas costs for contract deployments
- Estimating gas costs for contract function calls
- Estimating gas costs for standard transfers

### Parameters

The `eth_estimateGas` method takes a single parameter, an object representing the transaction details. The fields in the transaction object include:

- **`from`** (optional, string): The address that the transaction is sent from.
  - Example: `"from": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
- **`to`** (optional, string): The address the transaction is sent to.
  - Example: `"to": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
- **`gas`** (optional, string): The maximum amount of gas provided for the transaction.
  - Example: `"gas": "0x76c0"`
- **`gasPrice`** (optional, string): The price of gas in wei.
  - Example: `"gasPrice": "0x9184e72a000"`
- **`value`** (optional, string): The amount of ZEN to send in the transaction, in wei.
  - Example: `"value": "0xde0b6b3a7640000"`
- **`data`** (optional, string): The data payload of the transaction, typically used for contract function calls or contract deployment.
  - Example: `"data": "0x606060..."`
- **`nonce`** (optional, string): The transaction count of the `from` address.
  - Example: `"nonce": "0x1"`

### Return Object

The return value of the `eth_estimateGas` method is a single field:

- `gasEstimate` (string): The estimated gas cost for the transaction, represented as a hexadecimal string.
  - Example: `"0x5208"`

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_estimateGas",
  "params": [
    {
      "from": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "to": "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
      "value": "0xde0b6b3a7640000",
      "data": "0x606060..."
    }
  ]
}
```

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x5208"
}
```
