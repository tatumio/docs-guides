---
title: "Paid Fee"
slug: "paid-fee-1"
excerpt: "Stay Informed About Transaction Fees with PAID_FEE Notifications"
category: 65c0c716d716fe0040919d8b
hidden: false
createdAt: "Thu Mar 07 2024 14:16:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:26:04 GMT+0000 (Coordinated Universal Time)"
---
In the complex world of blockchain, keeping track of transaction fees is crucial for maintaining a transparent and efficient platform. Tatum's PAID\_FEE notification type provides a valuable tool to help you stay informed about fees paid as part of transactions involving a specific address.

# How to do it?

```curl curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "PAID_FEE",
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
    
    const subscription = await tatum.notification.subscribe.paidFee({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all paid fees on ${monitoredAddress}`)
})()
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "amount": "0.000031500000168",
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "subscriptionType": "PAID_FEE",
  "blockNumber": 2913059,
  "txId": "0x062d236ccc044f68194a04008e98c3823271dc26160a4db9ae9303f9ecfc7bf6",
  "mempool": false
}
```

# Which blockchain networks are supported?

| Blockchain          | Mainnet                     | Testnet                                                              |
| ------------------- | --------------------------- | -------------------------------------------------------------------- |
| Ethereum            | Network.ETHEREUM            | Network.ETHEREUM_SEPOLIA, Network.ETHEREUM_HOLESKY                   |
| Polygon             | Network.POLYGON             | Network.POLYGON_MUMBAI                                               |
| Binance Smart Chain | Network.BINANCE_SMART_CHAIN | Network.BINANCE_SMART_CHAIN_TESTNET                                  |
| Flare               | Network.FLARE               | Network.FLARE_COSTON, Network.FLARE_COSTON_2, Network.FLARE_SONGBIRD |
| Celo                | Network.CELO                | Network.CELO_ALFAJORES                                               |
| Klaytn              | Network.KLAYTN              | Network.KLATN_BAOBAB                                                 |
| XRP                 | Network.XRP                 | Network.XRP_TESTNET                                                  |
| Tezos               | Network.Tezos               | Network.TEZOS_TESTNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |

# Why Use PAID_FEE Notifications?

PAID_FEE notifications offer an effective way to monitor transaction fees in real-time. By focusing on fees paid in transactions involving a specific address, this notification type delivers several key benefits:

#### Real-time Monitoring

Stay informed about transaction fees as they occur. PAID_FEE notifications provide real-time updates, allowing you to react promptly to important events and ensuring your application or platform always has the latest information.

#### Enhanced Transparency

Receiving real-time notifications about transaction fees helps you maintain a transparent and accountable platform. Users can clearly see the fees associated with their transactions, fostering trust in your service and promoting a fair ecosystem.

#### Proactive Fee Management

PAID_FEE notifications help you identify and address potential issues related to transaction fees, such as underpayment or overpayment. By proactively resolving these issues, you can minimize disruptions and maintain a smooth-running platform.
