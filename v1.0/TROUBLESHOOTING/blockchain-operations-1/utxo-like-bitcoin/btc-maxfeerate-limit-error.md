---
title: "BTC - Maxfeerate Limit Error"
slug: "btc-maxfeerate-limit-error"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 25 2024 10:13:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 10:13:24 GMT+0000 (Coordinated Universal Time)"
---
Tatum Bitcoin Nodes are set with a default `maxfeerate` limit of `0.10 BTC/kb`.

When attempting to broadcast a transaction with a higher fee than the limit, you may receive an error looking as follows:

```json JSON
data: {   
   statusCode: 403,
   errorCode: 'btc.blockchain.broadcast.error',
   message: 'Unable to broadcast transaction. Set lower fee or check change 
   address to be present',
   cause: 'max-fee-exceeded'
}
```

## Workaround

It is possible to bypass the `maxfeerate` limit via the RPC node call method `sendrawtransaction`, which submits a raw transaction (serialized, hex-encoded) to our Bitcoin nodes.

### Example RPC raw request

In the example, the `maxfeerate` parameter is set at `12.0 BTC/kb`, overriding the limit set on the node.

```json cURL
url --location 'https://api.tatum.io/v3/blockchain/node/BTC/{{apikey}}' \
--header 'Content-Type: application/json' \
--data '{
    "jsonrpc": "2.0",
    "id": "someid",
    "method": "sendrawtransaction",
    "params": [
       "020000000001016fa9e19f2d988a745df84c8bb51bbe5db1cd98c49778744f9d4d228f71f75a4a0100000000ffffffff0116f10000000000001600148683f923f0b610e029ecd00c1aecc4cdda0d012b0247304402201373c6eb3cba8f827e0f70eb8e5a6e8c12bd12d1fb4264f6c5e75045da625f390220732cb45c3fe489067d1f47dfa799a07277574ccec7ccfb6f4f9cc14314d58e6801210382fc753a96946caeed8e1350dd2eecd44622a47f1fb755c2004a934a1d71c8ed00000000",
        "12.0"
    ]
}'

```

> 📘 Additional information is available at [the followin link](https://developer.bitcoin.org/reference/rpc/sendrawtransaction.html#argument-2-maxfeerate).
