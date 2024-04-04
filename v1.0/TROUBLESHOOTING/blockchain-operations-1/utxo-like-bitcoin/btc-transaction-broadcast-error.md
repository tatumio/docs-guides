---
title: "BTC - Transaction Broadcast Error"
slug: "btc-transaction-broadcast-error"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Thu Feb 08 2024 13:16:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2024 13:17:29 GMT+0000 (Coordinated Universal Time)"
---
When broadcasting a BTC transaction, you may encounter errors looking as follows:

```json JSON
{
    "statusCode": 403,
    "errorCode": "btc.blockchain.broadcast.error",
    "message": "Unable to broadcast transaction.",
    "cause": "Request failed with status code 500"
}
```

## How to troubleshoot

To troubleshoot, you will have to check how was the transaction made with "inputs", "outputs" and "amounts".

### Example request:

```json JSON
//Endpoint: "/v3/bitcoin/broadcast"
//Payload:
{
  "txData": "020000000001af4800000000000016001419619f650a88532d25fed24dc06aada4a0cb238d00000000",
  "signatureId": "654cf9d2ca22c5a2a9c###" // Tatum KMS related
}
```

Take the raw txData and use the Bitcoin RPC method `testmempoolaccept`.

**Example request:**

```json cURL
curl -X POST -H "Content-Type: application/json" -d '{
    "id": "1",
    "jsonrpc": "2.0",
    "method": "testmempoolaccept",
    "params": [
        [
            "020000000001af4800000000000016001419619f650a88532d25fed24dc06aada4a0cb238d00000000"
        ]
    ]
}'
//response:
{
    "jsonrpc": "2.0",
    "error": {
        "code": -32000,
        "message": "Server error"
    }
}
```

Based on the response, the transaction payload was built improperly and the blockchain refuses to accept it. In this case, it is best to review how you built your transaction based on inputs, outputs, and amounts.

## Good to know

1. You may decode the transaction using a reliable blockchain explorer, such as [BlockCypher](https://live.blockcypher.com/btc/decodetx/).
2. Analyze the decoded transaction to ensure its structure and content are correct.
