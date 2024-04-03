---
title: "BNB - BEP2 and BEP20 Token Transfers"
slug: "bnb-bep2-and-bep20-token-transfers"
excerpt: ""
hidden: false
createdAt: "Sun Feb 25 2024 11:48:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 11:48:18 GMT+0000 (Coordinated Universal Time)"
---
It's possible to transfer NBN BEP2 and BEP20 tokens with Tatum:

### v3 REST API endpoints:

- [Send BEP2 over BNB](https://apidoc.tatum.io/tag/BNB-Beacon-Chain/#operation/BnbBlockchainTransfer)
- [Send BEP20 over BSC](https://apidoc.tatum.io/tag/BNB-Smart-Chain/#operation/BscBlockchainTransfer)
  - Alternative: [Send BEP20 token via compatible ERC-20](https://apidoc.tatum.io/tag/Fungible-Tokens-(ERC-20-or-compatible)/#operation/Erc20Transfer) method, where **Request Body Schema** is `ChainTransferBscBep20` and chain is BSC
