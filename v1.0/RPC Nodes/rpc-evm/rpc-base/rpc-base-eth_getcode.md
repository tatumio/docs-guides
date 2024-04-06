---
title: "eth_getcode"
slug: "rpc-base-eth_getcode"
excerpt: "Base RPC"
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---



### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const code = await tatum.rpc.getCode(
  "0x833589fcd6edb6e08f4c7c32d4f71b54bda02913"
);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

The `eth_getCode` method is which allows users to interact with the blockchain. This method is specifically used to retrieve the contract code (bytecode) of an account at a specific block number. It is helpful when developers need to examine the bytecode of a deployed contract or validate that the contract code on the blockchain matches the intended code.

Use cases for this method could include:

- Debugging a smart contract
- Verifying the integrity of a deployed contract
- Analyzing contract bytecode for security vulnerabilities

### Parameters

The `eth_getCode` method accepts two parameters:

1. **`address`** (string): The address of the contract whose bytecode you want to retrieve. This should be a 20-byte address, formatted as a hex string with a `0x` prefix.
   - Example: `"0x833589fcd6edb6e08f4c7c32d4f71b54bda02913"`
2. **`block`** (string): The block number at which you want to retrieve the contract code. This can be specified as a hex string or one of the following special keywords:
   - `"earliest"`: The first block in the blockchain
   - `"latest"`: The most recent block in the blockchain
   - `"pending"`: The upcoming block that is being mined
   - Example: `"0x1"` or `"latest"`

### Return Object

The `eth_getCode` method returns a string representing the contract bytecode. The returned value is a hex string with a `0x` prefix.

- If the account has contract code, the returned string will contain the bytecode.
- If the account is not a contract or does not exist, the returned string will be `0x`.

#### Response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x606060...code_here...3839"
}
```