---
title: "Nonce - What is it and optional use"
slug: "nonce-what-is-it-and-optional-use"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Tue Feb 06 2024 17:43:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 06:59:50 GMT+0000 (Coordinated Universal Time)"
---
In blockchain technology, the `nonce` is a transaction counter that helps to prevent double-spending and replay attacks on a blockchain network. This value is attached to each Ethereum and EVM-compatible chain sender address.

Ethereum and other EVM-compatible blockchains require the `nonce` value for each transaction to ensure that the same transaction is not executed twice and that no one can replay a previously sent transaction.

With Tatum, when the `nonce` is not specified when making a transaction on Ethereum and other EVM-compatible chains, our Engine automatically adds it based on the sender's address.

> 📘 The Tatum engine has a delay when automatically calculating the nonce. Users with a high transaction broadcast volume should use a manual nonce value. Otherwise, errors about "replacement transaction" will be common.

## Finding the nonce value

### v3 REST API

You can get the current nonce value for their Ethereum sender address by making an API call.

- Endpoint: <https://apidoc.tatum.io/tag/Ethereum#operation/EthGetTransactionCount>

**Example:**

```json cURL
curl --location 'https://api.tatum.io/v3/ethereum/transaction/count/0x271ebc3C939Db4d0######' \
--header 'x-api-key: {Mainnet_API_KEY}'
//response:
4887 // Current nonce value in decimals
```

### RPC node request

You can also get the current nonce value using an Ethereum node's RPC call.

**Example:**

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ETH/' \
--header 'x-api-key: {Mainnet_API_KEY}' \
--header 'Content-Type: application/json' \
--data '{
    "jsonrpc":"2.0",
    "method":"eth_getTransactionCount",
    "params":[
        "0x271ebc3C939Db4d0######'",
        "latest"
        ],
    "id":1
    }'
//response:
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x1316" //needs conversion to decimal
}
```

## Nonce value and dropped transactions

### Single transaction

If a transaction with nonce value X is dropped or doesn't get included in a block, the nonce value for that account doesn't increase. The nonce is only increased once a transaction is successfully included in a block.

### Multiple transactions

If you try to send multiple transactions at the same time, each transaction must have `nonce+1,` `nonce+2`, `nonce+3`, `nonce+4`, etc. If for some reason the transaction with `nonce+2` gets dropped (low gas price, network congestion, etc.), the transactions with values `nonce+3` and `nonce+4` will be stuck in the mempool and won't be mined until the transaction with `nonce+2` is mined. 

To solve this, you would need to re-send the transaction with `nonce+2` with enough gas for it to be mined. Once the transaction with `nonce+2` would be mined, any subsequent transactions with higher nonce value should be able to be mined too.
