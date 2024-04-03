---
title: "TRON - \"tron.tx.expired\" Error"
slug: "tron-error-trontxexpired"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 12:53:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 12:25:04 GMT+0000 (Coordinated Universal Time)"
---
When working with the TRON blockchain, you may encounter the "`tron.tx.expired`" error, indicating that the transaction has expired and cannot be broadcast after a specific timestamp.

The error occurs when a transaction is not broadcast within the specified expiration time:

- **The default TRON transaction expiration time is 60 seconds**.
- If the period between transaction creation and broadcast exceeds 60 seconds, the transaction is considered expired.

Example error:

```json JSON
"response": {
    "statusCode": 403,
    "errorCode": "tron.tx.expired",
    "message": "Transaction expired and cannot be broadcast after 1705324314000."
}
```

> 📘 Additional information is available at [the following link](https://developers.tron.network/docs/faq#12-broadcast-response-code).

## Good to know

- KMS users need to be mindful of their configuration to check pending transactions at a rate below 60 seconds.
