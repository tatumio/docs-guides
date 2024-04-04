---
title: "Notifications - XRP, KMS and failed transactions"
slug: "notifications-xrp-kms-and-failed-transactions"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 16:29:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 16:29:28 GMT+0000 (Coordinated Universal Time)"
---
XRP transactions can exhibit a discrepancy where a transaction seemingly fails yet becomes part of the blockchain due to the node's response structure. 

Understanding the distinct failure types and associated notifications is required for the accurate interpretation and handling of these scenarios within the XRP blockchain ecosystem

## Failure Types in XRP Transactions

XRP transactions encounter two distinctive failure types, leading to differing behaviors within the blockchain.

### Failure Type 1: Transaction Broadcast Failure

This type occurs when the transaction fails to broadcast to the network. It's characterized by the node's rejection of the transaction or a failure in the call to the node. Consequently, the transaction does not exist on the XRP blockchain.

### Failure Type 2: Transaction Execution Failure

This type occurs when the transaction is accepted and included in the blockchain despite encountering execution failures. This could result from issues such as smart contract (SC) call failures or other logic-related discrepancies.

## Understanding XRP Notifications and KMS

- `KMS_FAILED_TX` Notification will be triggered due to the error in broadcasting but inclusion in the chain.
- `ADDRESS_EVENT` Notification will also be triggered, despite the apparent failure indication, owing to XRP's design.

### KMS_FAILED_TX Notification

This notification triggers when the logic inside the user's Key Management System (KMS) fails to broadcast the transaction (Failure Type 1). It signifies the failure to initiate the transaction and generates an API call to register the failure. However, it's essential to note that this HTTP call might also fail, leaving a log within the user's KMS.

### KMS_COMPLETED_TX Notification

Triggered when the broadcast endpoint within the KMS receives a response from the node indicating a successful broadcast (Failure Type 2). Despite this success signal, Failure Type 2 issues can still arise, potentially leading to the transaction being dropped from the mempool and not included in the chain.

### ADDRESS_EVENT Notification and \_others_

This notification creates a nuanced situation. For XRP transactions, there exists a design peculiarity where the XRP node responds with an error message (e.g., "Insufficient XRP balance to send") but still includes the transaction in the chain.
