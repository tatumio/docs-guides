---
title: "VA - Withdrawals to Blockchain Troubleshooting"
slug: "withdrawals-to-blockchain-troubleshooting"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 14:53:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:27:05 GMT+0000 (Coordinated Universal Time)"
---
When attempting to transfer assets from a Virtual Account deposit address(es) to a blockchain address, the operation may fail. This can be caused by:

- Insufficient on-chain assets.
- Incorrect `PrivateKey`, `mnenonic` && `index` or `mnemonic` && `xpub`
- Insufficient blockchain fees/gas.
- `Blocked` amounts on the Virtual Account making its balance appear as a negative.
- Stuck withdrawals `inProgress`. Unconfirmed or dropped blockchain transaction.
- A blockchain transaction failed but the Virtual Account flagged it as `Done`, creating a balance desync.

## Troubleshooting Withdrawals

1. [Get account by ID](https://apidoc.tatum.io/tag/Account/#operation/getAccountByAccountId): confirm currency, VA balance, and more.
2. If you are using `index` && `mnemonic`/`signatureId`, make sure the index matches the address/`PrivateKey`.
   1. [Get all deposit addresses for a Virtual Account](https://apidoc.tatum.io/tag/Blockchain-addresses/#operation/getAllDepositAddresses): Find all linked blockchain addresses to the Virtual Account as well as confirm their `derivationKey` / `index`
   2. Off-chain Transfers from a Virtual Account to Blockchain require the proper use of a combination of `mnemonic`, `xpub`, `index`, and `PrivateKey` via a match dictated by the **REQUEST BODY SCHEMA**
3. If you are setting up manual fees in the transaction, **ensure it's sufficient** for the tx to be accepted by the blockchain.
   1. Tatum provides fee estimate for a few chains: [VA Specific for BTC, LTC and DOGE](https://apidoc.tatum.io/tag/Virtual-account-blockchain-fees#operation/offchainEstimateFee) as well as for [other chains](https://apidoc.tatum.io/tag/Blockchain-fees#operation/EstimateFeeBlockchain)
4. Check the Virtual Account balance via: [Get account balance](https://apidoc.tatum.io/tag/Account/#operation/getAccountBalance) - Where:
   1. `accountBalance`: All assets on the account, both available and blocked
   2. `availableBalance`: The account balance minus the blocked assets; use the available balance to determine how much a customer can send or withdraw from their virtual account
5. Check for any `blocked` amounts via: [Get blocked amounts in an account](https://apidoc.tatum.io/tag/Account/#operation/getBlockAmount)
   1. You may unblock the balance in the Virtual Account via: [Delete a blocked amount in an account](https://apidoc.tatum.io/tag/Account/#operation/deleteBlockAmount) OR [Delete all blocked amounts in an account](https://apidoc.tatum.io/tag/Account/#operation/deleteAllBlockAmount)
6. Check for any withdrawals `inProgress` via: [Get Withdrawals](https://apidoc.tatum.io/tag/Withdrawal/#operation/GetWithdrawals)
   1. You may find all related transactions of a Virtual Account via: [Find transactions for account](https://apidoc.tatum.io/tag/Transaction/#operation/getTransactionsByAccountId)
   2. You should [Complete a Withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/completeWithdrawal) if the transaction has been confirmed OR [Cancel the withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/cancelInProgressWithdrawal) if it failed.
7. Check for any withdrawals that may have **failed** in the blockchain but still got marked as `Done` via: [Get Withdrawals](https://apidoc.tatum.io/tag/Withdrawal/#operation/GetWithdrawals)
   1. You may find all related transactions of a Virtual Account via: [Find transactions for account](https://apidoc.tatum.io/tag/Transaction/#operation/getTransactionsByAccountId)
   2. You should [Cancel the withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/cancelInProgressWithdrawal)
