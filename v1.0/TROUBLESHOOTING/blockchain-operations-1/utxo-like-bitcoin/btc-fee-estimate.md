---
title: "BTC - Fee Estimate"
slug: "btc-fee-estimate"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 22:11:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:14:14 GMT+0000 (Coordinated Universal Time)"
---
Bitcoin (BTC) is a UTXO-based chain, where the Fee estimate for a transaction fee comes from two main parameters:

- Approximate fee per kilobyte
- Transaction size

## BTC Fee Estimate Formula

**Estimated Fee** == "`approximate fee per kilobyte`" x "`transaction size`"

### Calculating the approximate fee per kilobyte

To estimate the fee for a BTC transaction, you can use the Tatum endpoint for BTC "fee estimate"

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/fee/BTC' \
--header 'x-api-key: {API_KEY}' \
--data ''
//response:
{
    "fast": 13.5, // Satoshis per byte == 0.0135 satoshis per kilobyte.
    "medium": 5,
    "slow": 4,
    "block": 813488, //last used to calculate fee from
    "time": "2023-10-23T12:14:42.817Z" // last time when calculation was executed
}
```

> 📘 More information at [the following link](https://apidoc.tatum.io/tag/Blockchain-fees/#operation/getBlockchainFee).

There's also the option to make a cURL RPC node request:

```Text cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/BTC/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "jsonrpc":"1.0",
    "id":"curltext",
    "method":"estimatesmartfee",
    "params":[2] // specifies the target confirmation time in blocks.
//response:
{
    "result": {
        "feerate": 0.00001, // Satoshis per Kilobyte
        "blocks": 2
    },
    "error": null,
    "id": "curltext"
}
```

### Calculating the Transaction Size

**Transaction Size (in bytes) = (Number of Inputs x 148) + (Number of Outputs x 34) + 10**

- **Number of Inputs**: The number of transaction inputs (unspent transaction outputs or UTXOs) that your transaction is spending.
- **Number of Outputs**: The number of transaction outputs, including the recipient's address and any change addresses.
- **10 bytes**: A fixed overhead for the transaction header.

**Let's break it down:**

- **Number of Inputs x 148 bytes**: Each input typically takes 148 bytes. This includes the previous transaction's reference (36 bytes) plus a scriptSig (typically 110 bytes) for unlocking the UTXO and some additional bytes for metadata.
- **Number of Outputs x 34 bytes**: Each output typically takes 34 bytes. This includes 8 bytes for the amount in satoshis, 1 byte for the OP_RETURN code (if used), and 25 bytes for the recipient's public key or address.

## Example BTC transaction

- Number of Inputs = 2
- Number of Outputs = 2

### Using the formula:

1. Transaction Size (in bytes) = (2 x 148) + (2 x 34) + 10
2. Transaction Size (in bytes) = 296 + 68 + 10
3. Transaction Size (in bytes) = 374 bytes

So, the transaction size in this example is 374 bytes.
