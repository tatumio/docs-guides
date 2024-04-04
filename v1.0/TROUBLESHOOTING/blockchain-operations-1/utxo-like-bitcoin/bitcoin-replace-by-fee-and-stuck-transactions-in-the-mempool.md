---
title: "BTC - RBF and stuck transactions in the mempool"
slug: "bitcoin-replace-by-fee-and-stuck-transactions-in-the-mempool"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Mon Jan 29 2024 11:06:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Feb 09 2024 08:48:40 GMT+0000 (Coordinated Universal Time)"
---
Bitcoin Replace-By-Fee (RBF) is a feature that allows you to replace a stuck or unconfirmed Bitcoin transaction in the mempool - a temporary storage area for pending transactions, with a new one that includes a higher transaction fee.

RBF is particularly useful during times of network congestion when transactions might take longer to get confirmed due to high demand.

## How Does Replace-By-Fee (RBF) Work?

When you broadcast a Bitcoin transaction, a transaction fee comes along with it to incentivize miners to include the transaction in the next block. 

However, if the network becomes congested, or if the initial fee is too low, the transaction might get stuck in the mempool. With RBF, you have the option to increase the transaction fee on an unconfirmed transaction, making it more attractive for miners to prioritize it.

## Replacing a Stuck Transaction using RBF

To replace a transaction that's stuck in the mempool using RBF, follow these steps:

1. **Check Transaction Status**: Use a blockchain explorer or wallet software to monitor the status of your original transaction. Make sure it is still unconfirmed and stuck.
2. **Confirm RBF is enabled**: Look for the RBF flag in the tx on a BTC mempool explorer.
3. **Create a Replacement Transaction**: Create a new transaction with the same inputs as the stuck transaction but with a higher fee. This is essentially a "double-spend" transaction but with a higher fee. The higher fee incentivizes miners to prioritize the new transaction.
4. **Broadcast the Replacement Transaction**: Once the replacement transaction is created, broadcast it to the Bitcoin network. Miners will see the higher fee and prioritize it.
5. **Wait for Confirmation**: Monitor the replacement transaction to see if it gets confirmed in a block. If miners prioritize the new transaction, it should confirm relatively quickly.

> 📘 Via Tatum, only transactions submitted through RPC calls can enable RBF. For additional information on RBF, check [the following guide.](https://github.com/BlockchainCommons/Learning-Bitcoin-from-the-Command-Line/blob/master/05_2_Resending_a_Transaction_with_RBF.md) Alternatively, see our CPFP article.
