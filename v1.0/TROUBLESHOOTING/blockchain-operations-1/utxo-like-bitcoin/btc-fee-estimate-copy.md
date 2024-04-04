---
title: "BCASH - Fee Estimate"
slug: "btc-fee-estimate-copy"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 22:15:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:18:32 GMT+0000 (Coordinated Universal Time)"
---
Bitcoin Cash (BCH) is a UTXO-based chain, where the Fee estimate for a transaction fee comes from two main parameters:

- Approximate fee per kilobyte
- Transaction size

## BTC Fee Estimate Formula

**Estimated Fee** == "`approximate fee per kilobyte`" x "`transaction size`"

### Calculating the approximate fee per kilobyte

To estimate the fee for a BCH transaction, you can use the RPC API cURL `estimatefee` method:

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/BCH' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "jsonrpc": "1.0",
    "id":"1",
    "method": "estimatefee",
    "params": []
}'
//response:
{
    "result": 0.00001,  // This is the value you are looking for
    "error": null,
    "id": "1"
}
```

> 📘 More information at [the following link](https://docs.bitcoincashnode.org/doc/json-rpc/estimatefee/).

### Calculating the Transaction Size

**Transaction Size (in bytes) = (Number of Inputs x 148) + (Number of Outputs x 34) + 10**

- **Number of Inputs**: The number of transaction inputs (unspent transaction outputs or UTXOs) that your transaction is spending.
- **Number of Outputs**: The number of transaction outputs, including the recipient's address and any change addresses.
- **10 bytes**: A fixed overhead for the transaction header.

**Let's break it down:**

- **Number of Inputs x 148 bytes**: Each input typically takes 148 bytes. This includes the previous transaction's reference (36 bytes) plus a scriptSig (typically 110 bytes) for unlocking the UTXO and some additional bytes for metadata.
- **Number of Outputs x 34 bytes**: Each output typically takes 34 bytes. This includes 8 bytes for the amount in satoshis, 1 byte for the OP_RETURN code (if used), and 25 bytes for the recipient's public key or address.

## Example BCH transaction

- Number of Inputs = 2
- Number of Outputs = 2

### Using the formula:

1. Transaction Size (in bytes) = (2 x 148) + (2 x 34) + 10
2. Transaction Size (in bytes) = 296 + 68 + 10
3. Transaction Size (in bytes) = 374 bytes

So, the transaction size in this example is 374 bytes.
