---
title: "VA - Withdrawal registered in ledger but failed in the blockchain"
slug: "withdrawal-registered-but-failed-in-the-blockchain"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 19:59:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:27:26 GMT+0000 (Coordinated Universal Time)"
---
Sometimes, a transaction from a Virtual Account to the blockchain will be internally processed decreasing the asset amount in the Virtual Account, but ultimately failing in the blockchain.

When this happens, additional transaction attempts with the affected `senderAccountId` could return an error looking as follows or similar:

```json JSON
{
    "statusCode": 403,
    "errorCode": "balance.insufficient",
    "message": "Insufficient balance for account ######### and payment amount 9. Sender balance is 0.2."
}
```

## Good to know

- A successful API call withdrawing assets from a VA that ultimately fails in the blockchain does not automatically revert the asset balance.
- To fix the affected Virtual Account balance on the`senderAccountId`, it is necessary to revert the operation via [Cancel Withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/cancelInProgressWithdrawal).
