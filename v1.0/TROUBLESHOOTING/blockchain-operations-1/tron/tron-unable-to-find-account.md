---
title: "TRON - Unable to find account"
slug: "tron-unable-to-find-account"
excerpt: ""
hidden: false
createdAt: "Tue Feb 06 2024 17:27:30 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 06 2024 17:28:28 GMT+0000 (Coordinated Universal Time)"
---
You may encounter the following error `tron.account.not.found` when you try to get the balance from a TRON address that has some tokens, like for example USDT. Getting this error, or similar, is related to an "`inactive account"`. 

> 📘 The affected TRON blockchain address requires getting a deposit of TRX or TRC-10 to activate the address on the TRON network. Additional information is available via TRON documentation at [the following link](https://developers.tron.network/docs/account#account-activation).

### Error Example:

```json cURL
{
    "statusCode": 403,
    "errorCode": "tron.account.not.found",
    "message": "No such account for address: <address>"
}
```

## How to activate the address

- Send any amount of TRX or TRC-10 tokens from an existing account to the new account.
- Call Java-tron's [wallet/createaccount] API to create a transaction from an existing account, then sign the transaction and broadcast it to the TRON network.
