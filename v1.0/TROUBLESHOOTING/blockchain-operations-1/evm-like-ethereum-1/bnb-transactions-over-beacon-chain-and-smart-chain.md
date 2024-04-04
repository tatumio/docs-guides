---
title: "BNB - Transactions over Beacon Chain and Smart Chain"
slug: "bnb-transactions-over-beacon-chain-and-smart-chain"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 25 2024 11:56:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 11:56:05 GMT+0000 (Coordinated Universal Time)"
---
Binance has two types of chains:

1. BNB Beacon Chain
2. BSC Smart Chain.

> 📘 BNB is the native asset of both chains.

## BNB Smart Chain (BSC) - BEP20

- In the Tatum v3 REST API, we call its currency with the symbol "`BSC`".
- BSC chain supports smart contracts and decentralized applications (DApps) since it's EVM compatible.
- BSC chain addresses follow the EVM address format. BSC chain addresses start with the prefix `0x`
- [BSC Explorer](https://bscscan.com/)
- [BSC chain API documentation link](https://apidoc.tatum.io/tag/BNB-Smart-Chain/)
- v3 REST API endpoint to make a BSC transfer: "`/v3/bsc/transaction`"

## BNB Beacon Chain (BNB) - BEP2

- In the Tatum v3 REST API, we call its currency with the symbol "`BNB`".
- The BNB chain is standalone, not EVM-compatible.
- BNB chain addresses start with the prefix `bnb`
- [BNB Explorer](https://explorer.bnbchain.org/)
- [BNB chain v3 REST API documentation link](https://apidoc.tatum.io/tag/BNB-Beacon-Chain/)
- v3 REST API endpoint to make a BNB transfer: "`/v3/bnb/transaction`"
