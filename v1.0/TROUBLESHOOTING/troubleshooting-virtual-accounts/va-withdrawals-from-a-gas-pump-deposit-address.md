---
title: "VA - Withdrawals from a Gas Pump deposit address"
slug: "va-withdrawals-from-a-gas-pump-deposit-address"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 22:33:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:35:12 GMT+0000 (Coordinated Universal Time)"
---
Gas Pump contract addresses can be attached to Virtual Accounts.

At the time to execute a withdrawal of a Gas Pump contract address attached to a Virtual Account, there are a few steps to follow, so the balance is updated on the Virtual Account.

## Withdrawal steps:

1. Check if a Gas Pump contract address has been activated on-chain - [V3 REST API endpoint](https://apidoc.tatum.io/tag/Gas-pump/#operation/GasPumpAddressesActivatedOrNot)
   1. If the Gas Pump contract address is not activated, do so - [V3 REST API endpoint](https://apidoc.tatum.io/tag/Gas-pump/#operation/ActivateGasPumpAddresses)
2. Create a withdrawal request to the Virtual Account - [V3 REST API endpoint](https://apidoc.tatum.io/tag/Withdrawal/#operation/storeWithdrawal)
3. Transfer the assets from the Gas Pump contract address - [V3 REST API endpoint](https://apidoc.tatum.io/tag/Gas-pump/#operation/TransferCustodialWallet)
4. Mark the withdrawal on the virtual account as completed - [V3 REST API endpoint](https://apidoc.tatum.io/tag/Withdrawal/#operation/completeWithdrawal)
