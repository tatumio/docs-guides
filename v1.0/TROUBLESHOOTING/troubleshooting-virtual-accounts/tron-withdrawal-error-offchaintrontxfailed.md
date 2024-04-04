---
title: "VA - TRON withdrawal error: offchain.tron.tx.failed"
slug: "tron-withdrawal-error-offchaintrontxfailed"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Thu Feb 08 2024 20:16:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:27:32 GMT+0000 (Coordinated Universal Time)"
---
When attempting to make a withdrawal from a TRON-based Virtual Account, holding TRX, TRC-10, or TRC-20 (like USDT), you may face the following error or similar:

```json JSON
 {
     "statusCode": 403,
     "errorCode": "offchain.tron.tx.failed",
     "message": "Unable to prepare transaction.",
     "cause": "class org.tron.core.exception.ContractValidateException : Validate TransferContract error, no OwnerAccount."
 }
```

## Steps to troubleshoot

- Make sure the address has been activated. This means that it holds some TRX - This is a TRON network requirement.
- Make sure the Private key used to sign the transaction matches the deposit address from the sender's Virtual Account.
- Make sure there's enough balance in the address, be TRX, or in the case of TRC-10 or TRC-20, additional TRX to pay for the fees.
