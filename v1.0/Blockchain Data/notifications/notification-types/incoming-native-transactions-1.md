---
title: "Incoming native transactions"
slug: "incoming-native-transactions-1"
excerpt: "Stay on Top of Your Transactions with INCOMING_NATIVE_TX Notifications"
hidden: false
createdAt: "Thu Mar 07 2024 14:00:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:02:21 GMT+0000 (Coordinated Universal Time)"
---
In the world of blockchain, staying updated with incoming transactions is crucial for ensuring smooth operations and an optimal user experience. Tatum's INCOMING\_NATIVE\_TX notification type is designed to help you do just that – by sending webhook notifications every time there's an incoming native balance update on a monitored address.

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "INCOMING_NATIVE_TX",
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
    
    const subscription = await tatum.notification.subscribe.incomingNativeTx({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all incoming ETH transactions on ${monitoredAddress}`)
})()
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "amount": "0.0001",
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "counterAddress": "0x0229338ee05154a406945899fb8c7bef36eb9220",
  "subscriptionType": "INCOMING_NATIVE_TX",
  "blockNumber": 3553920,
  "txId": "0x21c78973a2d47b1910d79b8586c55d13c732dfb41883ee5af4318dafc66a0db9",
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
| Bitcoin             | Network.BITCOIN             | Network.BITCOIN_TESTNET                                              |
| Litecoin            | Network.LITECOIN            | Network.LITECOIN_TESTNET                                             |
| Dogecoin            | Network.DOGECOIN            | Network.DOGECOIN_TESTNET                                             |
| Celo                | Network.CELO                | Network.CELO_ALFAJORES                                               |
| Klaytn              | Network.KLAYTN              | Network.KLATN_BAOBAB                                                 |
| Solana              | Network.SOLANA              | Network.SOLANA_DEVNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |
| Tezos               | Network.TEZOS               | Network.TEZOS_TESTNET                                                |
| XRP                 | Network.XRP                 | Network.XRP_TESTNET                                                  |
