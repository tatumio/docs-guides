---
title: "eth_call"
slug: "rpc-bsc-eth_call"
excerpt: "Bsc RPC"
hidden: false
metadata: 
  description: "Bsc RPC"
  image: []
  keywords: "bsc, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, BinanceSmartChain, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BinanceSmartChain>({network: Network.BINANCE_SMART_CHAIN})

const result = await tatum.rpc.call({
  "to": "0x8AC76a51cc950d9822D68b83fE1Ad97B32Cd580d", // Replace with the ERC-20 token contract address
  "data": "0x70a082310000000000000000000000008894E0a0c962CB723c1976a4421c95949bE2D4E3" // The function signature for balanceOf(address), followed by the address tokens
}, "latest")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

Executes a new message call immediately without creating a transaction on the block chain. Often used for executing read-only smart contract functions, for example the `balanceOf` for an ERC-20 contract.

Top 5 most commonly used use cases for `eth_call`:

1. **Retrieve Token Balance:** Check an ERC-20 token balance for an address.
2. **Query Contract State:** Get contract data, like a game score or auction status.
3. **Validate Inputs:** Pre-validate function inputs before sending a transaction.
4. **Price Oracles:** Fetch real-time price data for decentralized applications.
5. **Gas Estimation:** Estimate gas costs for future transactions.

### **Parameters**

1. `Object` - The transaction call object

- `from`: `DATA`, 20 Bytes - (optional) The address the transaction is sent from.
- `to`: `DATA`, 20 Bytes - The address the transaction is directed to.
- `gas`: `QUANTITY` - (optional) Integer of the gas provided for the transaction execution. eth\_call consumes zero gas, but this parameter may be needed by some executions.
- `gasPrice`: `QUANTITY` - (optional) Integer of the gasPrice used for each paid gas
- `value`: `QUANTITY` - (optional) Integer of the value sent with this transaction
- `data`: `DATA` - (optional) Hash of the method signature and encoded parameters. For details see [Ethereum Contract ABI in the Solidity documentation(opens in a new tab)](https://docs.soliditylang.org/en/latest/abi-spec.html)

2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`

### Return Object

`DATA` - the return value of executed contract.

### JSON Examples

#### Request

```json
{
    "jsonrpc":"2.0",
    "method":"eth_call",
        "params":[{
            "to": "0x8AC76a51cc950d9822D68b83fE1Ad97B32Cd580d", // Replace with the ERC-20 token contract address in this case USDC on Binance Smart Chain
            "data": "0x70a082310000000000000000000000008894E0a0c962CB723c1976a4421c95949bE2D4E3" // The function signature for balanceOf(address), followed by the address to query in this case holder of USDC tokens
        },"latest"],
    "id":1
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x0000000000000000000000000000000000000000002f798bddfae24274770b92"
}
```
