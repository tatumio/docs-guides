---
title: "Transaction Unconfirmed, Pending or Dropped"
slug: "unconfirmed-and-dropped-transactions"
excerpt: ""
hidden: false
createdAt: "Sat Feb 10 2024 10:48:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 10:20:22 GMT+0000 (Coordinated Universal Time)"
---
When a transaction is successfully broadcasted, you will get a transaction hash. At this stage, the transaction entered the mempool and remains "Pending", waiting for confirmation. 

Confirming a transaction can take from seconds, to minutes, to many hours. Factors such as the total network activity or congestion, hashrate, and transaction fees impact the time it takes for a transaction to get confirmed.

For example, the usual average confirmation time for a BTC transaction is about 10 minutes. However, if the Bitcoin network is congested, there may be a backlog of transactions in the Mempool awaiting verification. The same applies to any other network.

In most cases, your transactions will be confirmed. How long this takes depends on the chain network, based on how much fee was allocated and mempool congestion.

### Two things can happen to unconfirmed transactions in the mempool:

- The transaction is `confirmed`, eventually.
- The transaction is `dropped`. 

> 📘 Mempool: the "waiting room" for transactions that have not yet been validated by a miner and added to a next block on the blockchain.

## Get transaction by hash

### EVM (like Ethereum):

- `Unconfirmed` transactions return an `error`
- `Dropped` transactions return an `error`

**Example Error:**

```json cURL
curl --location 'https://api.tatum.io/v3/ethereum/transaction/0xb491a90c665ab8a3bcebb42cbc30ded73bf40eae40d45a365895a33595d347dc' \
--header 'x-api-key: {API_KEY}'
//response:
{
    "statusCode": 403,
    "errorCode": "eth.tx.not.found",
    "message": "Transaction 0xb491a90c665ab8a3bcebb42cbc30ded73bf40eae40d45a365895a33595d347dc not found. Possible not exists or is still pending.",
    "dashboardLog": "https://dashboard.tatum.io/logs?id=65###315a"
}
```

### UTXO (like Bitcoin)

- `Unconfirmed`: transactions return with the parameter `"blocknumber": null`
- `Dropped` transactions return an `error`

**Example of BTC transaction waiting in mempool**

```json cURL
curl --location 'https://api.tatum.io/v3/bitcoin/transaction/61749d00c59548b3b5c6f394a218a1c55b0f99020ca49cbec5c0a590c74ee89a' \
--header 'x-api-key: {API_KEY}'
//response:
{
    "blockNumber": null, //Since the transaction is unconfirmed, there can't be a "blockNumber"
    "fee": 4245,
    "hash": "61749d00c59548b3b5c6f394a218a1c55b0f99020ca49cbec5c0a590c74ee89a",
    "hex": "0200000000...
```

**Example of BTC transaction dropped**

```json cURL
curl --location 'https://api.tatum.io/v3/bitcoin/transaction/61749d00c59548b3c5c6f394a218a1c55b0f99020ca49cbec5c0a590c74ee89a' \
--header 'x-api-key: {API_KEY}'
//response:
{
    "statusCode": 403,
    "errorCode": "btc.tx.not.found",
    "message": "Transaction 61749d00c59548b3c5c6f394a218a1c55b0f99020ca49cbec5c0a590c74ee89a not found. Possible not exists or is still pending.",
    "dashboardLog": "https://dashboard.tatum.io/logs?id=65c75###22ae3d3"
}
```
