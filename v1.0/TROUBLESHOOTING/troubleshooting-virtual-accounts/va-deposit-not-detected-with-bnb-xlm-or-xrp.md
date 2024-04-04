---
title: "VA - Deposit not detected with BNB, XLM or XRP"
slug: "va-deposit-not-detected-with-bnb-xlm-or-xrp"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 22:28:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:32:35 GMT+0000 (Coordinated Universal Time)"
---
When receiving deposits from external sources to a deposit address linked to a Virtual Account, the users are identified by unique identifiers specific to BNB, XLM, and XRP.

### The fields required to identify users for each blockchain are as follows:

- BNB - `memo`
- XLM - `message`
- XRP - `destinationTag`

> 📘 Required fields for BNB, XLM and XRP are made available when [Generating a deposit address](https://apidoc.tatum.io/tag/Blockchain-addresses/#operation/generateDepositAddress) for a Virtual Account.
