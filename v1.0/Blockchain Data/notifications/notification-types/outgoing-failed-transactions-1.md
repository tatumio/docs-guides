---
title: "Outgoing failed transactions"
slug: "outgoing-failed-transactions-1"
excerpt: "Stay Ahead of Failed Transactions with OUTGOING_FAILED_TX Notifications"
category: 65e9ba6715ec3b004bc82075
hidden: false
createdAt: "Thu Mar 07 2024 14:26:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:26:00 GMT+0000 (Coordinated Universal Time)"
---
In the fast-paced world of blockchain, keeping track of failed transactions is crucial for maintaining a secure and efficient platform. Tatum's OUTGOING_FAILED_TX notification type provides an invaluable tool to help you stay informed about transactions from monitored addresses that fail to be included in a block.

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "OUTGOING_FAILED_TX",
    "attr": {
      "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
      "chain": "ETH",
      "url": "https://<YOUR_WEBHOOK_URL>"
    }
  }'
```
```typescript
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

(async () => {
    const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})
    
    const monitoredAddress = '0xF64E82131BE01618487Da5142fc9d289cbb60E9d'
    
    const subscription = await tatum.notification.subscribe.outgoingFailedTx({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all outgoing failed transactions on ${monitoredAddress}`)
})()
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "amount": "0.001",
  "blockNumber": 2913059,
  "counterAddress": "0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990",
  "txId": "0x062d236ccc044f68194a04008e98c3823271dc26160a4db9ae9303f9ecfc7bf6",
  "chain": "ethereum-mainnet",
  "subscriptionType": "OUTGOING_FAILED_TX",
  "currency": "ETH"
}
```

# Which blockchain networks are supported?

| Blockchain          | Mainnet                       | Testnet                                                              |
| ------------------- | ----------------------------- | -------------------------------------------------------------------- |
| Ethereum            | Network.ETHEREUM              | Network.ETHEREUM_SEPOLIA, Network.ETHEREUM_HOLESKY                   |
| Polygon             | Network.POLYGON               | Network.POLYGON_MUMBAI                                               |
| Binance Smart Chain | Network.BINANCE\_SMART\_CHAIN | Network.BINANCE_SMART_CHAIN_TESTNET                                  |
| Flare               | Network.FLARE                 | Network.FLARE_COSTON, Network.FLARE_COSTON_2, Network.FLARE_SONGBIRD |
| Celo                | Network.CELO                  | Network.CELO_ALFAJORES                                               |
| Klaytn              | Network.KLAYTN                | Network.KLATN_BAOBAB                                                 |
| Tezos               | Network.TEZOS                 | Network.TEZOS_TESTNET                                                |
| XRP                 | Network.XRP                   | Network.XRP_TESTNET                                                  |

# Why Use OUTGOING_FAILED_TX Notifications?

OUTGOING_FAILED_TX notifications offer an effective way to monitor failed transactions in real-time. By focusing on transactions that fail to be included in a block, this notification type delivers several key benefits:

## Real-time Monitoring

Stay informed about failed transactions as they occur. OUTGOING_FAILED_TX notifications provide real-time updates, allowing you to react promptly to important events and ensuring your application or platform always has the latest information.

## Proactive Problem Solving

OUTGOING_FAILED_TX notifications help you identify and address the reasons behind failed transactions, such as insufficient gas fees, incorrect contract addresses, or network congestion. By proactively resolving these issues, you can minimize disruptions and maintain a smooth-running platform.
