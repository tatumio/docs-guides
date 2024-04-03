---
title: "Notifications - UTXO and ADDRESS_TRANSACTION"
slug: "notifications-utxo-and-address_transaction"
excerpt: ""
hidden: false
createdAt: "Sun Feb 11 2024 16:31:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 16:31:49 GMT+0000 (Coordinated Universal Time)"
---
The Notification type `ADDRESS_TRANSACTION`, when applicable to UTXO chains (like Bitcoin), provides a notification based on the address registered.

- `ADDRESS_TRANSACTION` informs you that the subscribed address was part of a transaction, be it with a negative or positive amount. 
- If you are looking for a detailed report of balances from all the addresses involved with the transaction as recipient and sender, you can do so via the endpoint [Get a transaction by its hash](https://apidoc.tatum.io/tag/Bitcoin/#operation/BtcGetRawTransaction).
