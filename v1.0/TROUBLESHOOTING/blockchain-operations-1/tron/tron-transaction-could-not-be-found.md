---
title: "TRON - Transaction could not be found"
slug: "tron-transaction-could-not-be-found"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Wed Jan 31 2024 11:45:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 08:36:15 GMT+0000 (Coordinated Universal Time)"
---
When broadcasting a TRON transaction to the blockchain, even if you get a transaction hash from Tatum, the transaction can be dropped from the TRON blockchain mempool.

If a successfully broadcasted transaction is reaching the TRON mempool, there can be many reasons for it to be dropped:

- `mempool size limit` could have been reached (low-priority transactions fall victim to mempool pruning first)
- The transaction could have reached the set mempool expiration time (Time-To-Live)
- Double-spending

Assuming the transaction is valid, if this issue happens to you only during certain periods during the day, it might be during higher traffic hours when fees get bloated. In this case, we recommend increasing the fee so that your transactions will be less likely to be dropped or timed out.
