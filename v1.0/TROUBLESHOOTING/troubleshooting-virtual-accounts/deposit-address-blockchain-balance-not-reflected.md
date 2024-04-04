---
title: "VA - Deposit address blockchain balance not reflected"
slug: "deposit-address-blockchain-balance-not-reflected"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Thu Feb 08 2024 19:54:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:27:10 GMT+0000 (Coordinated Universal Time)"
---
When adding a blockchain address as a deposit address into a Virtual Account, it is expected that said address contains no balance or assets.

If a blockchain address with existing assets is added as a deposit address into a Virtual Account, those pre-existing assets won't be considered by the Virtual Account.

To update a Virtual Account balance based on a blockchain operation, said operation needs to happen after the address has been attached to the Virtual Account.

## Good to know

- The time required for a blockchain transaction to get confirmed varies from chain to chain and chain load.
- The Virtual Account balance is updated with **confirmed blockchain transaction**, with an additional delay of approximately 1 minute.
