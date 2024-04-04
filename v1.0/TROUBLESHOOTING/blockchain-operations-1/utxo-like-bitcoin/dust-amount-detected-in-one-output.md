---
title: "Dust amount detected in one output"
slug: "dust-amount-detected-in-one-output"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Thu Feb 08 2024 13:17:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2024 13:21:11 GMT+0000 (Coordinated Universal Time)"
---
Dust refers to a small amount of coins within a UTXO transaction hash recipient address that is smaller than the gas fees required to transfer out. This makes said amount unspendable.

For UTXO-based chains like Bitcoin, Dogecoin, Litecoin and related, small amounts of UTXOs can accumulate (as the result of the change from earlier sent payments), which, combined with higher fees, may result in a portion of the balance impossible to spend.

## Why do I get a Dust Error?

If the amount of a UTXO is smaller than the partial fee needed to transfer out, that UTXO cannot be used (with the current fee level). If all UTXOs are Dust, nothing can be sent.

### Example:

A Bitcoin address contains 0.0087 BTC. In reality, consisting of x3 UTXOs of:

1. 0.0080
2. 0.0002
3. 0.0005

Considering a potential tx fee for each UTXO of 0.00055, the 0.0002 and 0.0005 amounts would be considered as Dust and thus, unspendable. Attempting to send 0.0087 would trigger a Dust UTXO error while attempting to send 0.0080 should get through.

> 📘 See Bitcoin code for Dust threshold via [`GetDustThreshold`] at [the following link](https://github.com/bitcoin-sv/bitcoin-sv/blob/v1.0.8/src/primitives/transaction.h#L189).
