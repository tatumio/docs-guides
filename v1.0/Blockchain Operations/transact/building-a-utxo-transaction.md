---
title: "Building a UTXO Transaction"
slug: "building-a-utxo-transaction"
excerpt: ""
category: 65e9ba02205d9900590782fe
hidden: true
createdAt: "Sun Feb 25 2024 07:40:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 13:20:30 GMT+0000 (Coordinated Universal Time)"
---
For UTXO chains (like Bitcoin, Litecoin, Doge, etc.), Tatum supports two methods to build a transaction.

- **fromAddress**
- **fromUTXO**

> 📘 Make sure there's x2 vout addresses or that you are using "fee" & "ChangeAddress".

## fromAddress

- Using a "standard" approach of x2 vout addresses

Let's say `address_1` contains 100BTC and you want to make a transfer from `address_1` to `address_2` of 10BTC.

The transaction would look as follows:

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/bitcoin/transaction' \
--header 'x-api-key: {API_KEY}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "fromAddress": [
        {
            "address": "address_1",
            "privateKey": "pk_address_1"
        }
    ],
    "to": [
        {
            "address": "address_1", //The rest of the coin gets defined to be sent back to the sender address.
            "value": 89.87654321 // Here you also consider the amount of "fee" you will allocate for the "miners"
        },
        {
            "address": "address_2", // where you want to transfer the 10BTC
            "value": 10
        }
    ]
  }'

// within the "to" IF you only have x1 address as destination and don't specify where the rest of the coins go, the blockchain considers that amount as the "fee" to be given to the miners!
```

## fromUTXO

- Using `fee` && `changeAddress`

Let's say `address_1` contains 100BTC and you want to make a transfer from `address_1` to `address_2` of 10BTC.

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/bitcoin/transaction' \
--header 'x-api-key: {API_KEY}' \
--header 'Content-Type: application/json' \
--data-raw '{
  "fromUTXO":[
      {
        "txHash":"######",
        "index":##, // the index of the "PublicAddress" within the "txHash"
        "privateKey":"pk_address_2"
      }
    ],
   "to": [ // this is an array, you can have multiple destinations
      {
        "address":"address_y", //main destination address
        "value":10
      }
    ],
  "changeAddress":"address_1", //where you sent the rest of "unspent" coin
  "fee":"0.87654321" // this fee is quite high for BTC or LTC, take it as an example.
}'
```

## Good to know

- BTC supports a maximum of eight (8) decimals.
- You may use FeeEstimate endpoints to figure out the amount to set up as the miner's fees.
