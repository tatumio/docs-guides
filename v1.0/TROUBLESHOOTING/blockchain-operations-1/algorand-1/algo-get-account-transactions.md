---
title: "Algo - Get Account Transactions"
slug: "algo-get-account-transactions"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Mon Feb 12 2024 12:13:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 12 2024 12:15:25 GMT+0000 (Coordinated Universal Time)"
---
Getting all Account transactions in from an Algorand address is possible via an RPC node request.

### Example request

```curl cURL
curl --location --request GET 'https://api.tatum.io/v3/blockchain/node/ALGO/v2/accounts/MLD3LCNGOK2SXAVNUYMW3WVG5LBN4Z5HFARB3VLMZCENFW############/transactions?nodeType=INDEXER' \
--header 'x-api-key: {API_KEY}'
//Response:
{
    "current-round": 26834617,
    "next-token": "0DOZAQAAAAAMAAAA",
    "transactions": [
        {
            "asset-transfer-transaction": {
                "amount": 0,
                "asset-id": 27165954,
                "close-amount": 0,
                "receiver": "MLD3LCNGOK2SXAVNUYMW3WVG5LBN4Z5HFARB3VLMZCENFW############"
            },
            "close-rewards": 0,
            "closing-amount": 0,
            "confirmed-round": 26834571,
            "fee": 1000,
            "first-valid": 26834569,
...
```

## Good to Know

- Algorand RPC node method `/v2/accounts/{account-id}/transactions` looks up account transactions, returning newest to oldest.
- This request requires a redirect to the `INDEXER` node via `?nodeType=INDEXER`
