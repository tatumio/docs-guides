---
title: "Get the contractaddress or tokenaddress from a transaction hash"
slug: "getting-the-contractaddress-or-tokenaddress-from-a-transaction-hash"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Mon Feb 12 2024 12:21:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 07:26:39 GMT+0000 (Coordinated Universal Time)"
---
When you deploy a Smart Contract, you get as a response a transaction hash.

### Example response

```json JSON
{
    "txId": "0x532cb74e9b5388a6ae46cf6d68e38f3ed28738c80949726b2b8b641bad58783f"
}
```

To get the `contractAddress`, you can use [the following REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-utils#operation/SCGetContractAddress).

### Example request (Polygon - testnet)

```curl
curl --location 'https://api.tatum.io/v3/blockchain/sc/address/MATIC/0x532cb74e9b5388a6ae46cf6d68e38f3ed28738c80949726b2b8b641bad58783f' \
--header 'x-api-key: {API_KEY}'
//response:
{"contractAddress":"0x5775f95675e23062e3e4a0683f03f22f012df7ce"}
```
