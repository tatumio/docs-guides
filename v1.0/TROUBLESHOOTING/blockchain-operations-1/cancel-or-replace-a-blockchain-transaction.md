---
title: "Cancel or Replace a blockchain transaction"
slug: "cancel-or-replace-a-blockchain-transaction"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Mon Jan 29 2024 10:11:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 08:42:10 GMT+0000 (Coordinated Universal Time)"
---
In some cases, you may want to cancel or replace a transaction.

- **Cancel**: for EVM chains (like Ethereum), it may be possible to replace a pending transaction in the mempool via another one with value zero (0) to your own address. UTXO transactions can't be "canceled".
- **Replace**: for UTXO chains (like Bitcoin), it may be possible to increase the fee of a pending transaction via [RBF](https://tatumdocs.readme.io/docs/bitcoin-replace-by-fee-and-stuck-transactions-in-the-mempool) (if enabled) or via [CPFP](https://tatumdocs.readme.io/docs/bitcoin-cpfp-and-stuck-transactions-in-the-mempool). For EVM chains, it may be possible to replace a pending transaction.

## Cancelling a transaction

EVM chains allow a bit of a trick to cancel a pending (unconfirmed) transaction in the mempool:

1. Verify the transaction you want to cancel is not confirmed yet and is still pending in the mempool. Check an Explorer.
2. Verify the nonce value of the unconfirmed transaction you want to cancel.
3. Create a new transaction where the sender and receiver blockchain address is the same with a zero (0) amount. Use the same nonce value you got from step 2 and put a much higher fee.
4. Broadcast this transaction. Ideally, the miners will prioritize this new transaction over the original due to a higher fee. 
5. If all worked well, your new transaction will get confirmed first and the original will be dropped due to invalid.

## Replacing a transaction

UTXO chains may allow [RBF](https://tatumdocs.readme.io/docs/bitcoin-replace-by-fee-and-stuck-transactions-in-the-mempool) or in some cases [CPFP](https://tatumdocs.readme.io/docs/bitcoin-cpfp-and-stuck-transactions-in-the-mempool) on pending (unconfirmed) transactions.

EVM chains may allow replacing a transaction using the same method as if you were to cancel it:

1. Verify the transaction you want to cancel is not confirmed yet and is still pending in the mempool. Check an Explorer.
2. Verify the nonce value of the unconfirmed transaction you want to replace.
3. Create a new transaction where the receiver blockchain address may or may not be the same as in the original to replace. Use the same nonce value you got from step 2 and put a much higher fee.
4. Broadcast this transaction. Ideally, the miners will prioritize this new transaction over the original due to a higher fee.
5. If all works well, your new transaction will get confirmed first and the original will be dropped due to invalid.

## Good to know

- Incorrectly executed transactions may result in the loss of funds.
- Blockchain transactions, once confirmed, are irreversible. There's no guarantee of success in canceling or replacing them.
