---
title: "Failed transactions in a block"
slug: "failed-transactions-in-a-block-1"
excerpt: "Stay Ahead of Failed Transactions with FAILED_TXS_PER_BLOCK Notifications"
hidden: false
createdAt: "Thu Mar 07 2024 14:28:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:28:59 GMT+0000 (Coordinated Universal Time)"
---
In the fast-paced world of blockchain, keeping track of failed transactions is crucial for maintaining a secure and efficient platform. Tatum's OUTGOING_FAILED_TX notification type provides an invaluable tool to help you stay informed about all transactions in a block that fail to be included in a block.

# How to do it?

```typescript
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

(async () => {
    const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})
    
    const subscription = await tatum.notification.subscribe.failedTxsPerBlock({
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all failed transactions`)
})()
```
```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "FAILED_TX_PER_BLOCK",
    "attr": {
      "chain": "ETH",
      "url": "https://<YOUR_WEBHOOK_URL>"
    }
  }'
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "amount": "0.001",
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "counterAddress": "0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990",
  "subscriptionType": "FAILED_TXS_PER_BLOCK"
  "blockNumber": 2913059,
  "txId": "0x062d236ccc044f68194a04008e98c3823271dc26160a4db9ae9303f9ecfc7bf6",
  "mempool": false
}
```

# Which blockchain networks are supported?

| Blockchain          | Mainnet                     | Testnet                                                              |
| ------------------- | --------------------------- | -------------------------------------------------------------------- |
| Ethereum            | Network.ETHEREUM            | Network.ETHEREUM_SEPOLIA, Network.ETHEREUM_FLARE                     |
| Polygon             | Network.POLYGON             | Network.POLYGON_MUMBAI                                               |
| Binance Smart Chain | Network.BINANCE_SMART_CHAIN | Network.BINANCE_SMART_CHAIN_TESTNET                                  |
| Flare               | Network.FLARE               | Network.FLARE_COSTON, Network.FLARE_COSTON_2, Network.FLARE_SONGBIRD |
| Celo                | Network.CELO                | Network.CELO_ALFAJORES                                               |
| Klaytn              | Network.KLAYTN              | Network.KLATN_BAOBAB                                                 |
| Solana              | Network.SOLANA              | Network.SOLANA_DEVNET                                                |
| Tezos               | Network.TEZOS               | Network.TEZOS_TESTNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |

# Why use FAILED_TXS_PER_BLOCK Notifications?

FAILED_TXS_PER_BLOCK notifications offer an effective way to monitor failed transactions in real-time. By focusing on transactions that fail to be included in a block, this notification type delivers several key benefits:

## Real-time Monitoring

Stay informed about failed transactions as they occur. FAILED_TXS_PER_BLOCK notifications provide real-time updates, allowing you to react promptly to important events and ensuring your application or platform always has the latest information.

## Proactive Problem Solving

FAILED_TXS_PER_BLOCK notifications help you identify and address the reasons behind failed transactions, such as insufficient gas fees, incorrect contract addresses, or network congestion. By proactively resolving these issues, you can minimize disruptions and maintain a smooth-running platform.
