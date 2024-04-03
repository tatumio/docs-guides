---
title: "Outgoing native transactions"
slug: "outgoing-native-transactions-1"
excerpt: "Master Your Outgoing Transactions with OUTGOING_NATIVE_TX Notifications"
hidden: false
createdAt: "Thu Mar 07 2024 14:06:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:06:06 GMT+0000 (Coordinated Universal Time)"
---
Monitoring outgoing transactions is essential for maintaining a secure and efficient blockchain platform. Tatum's OUTGOING_NATIVE_TX notification type offers a powerful solution to help you stay informed about outgoing native balance updates on a monitored address, simplifying your operations and enhancing user experience.

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "OUTGOING_NATIVE_TX",
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
    
    const subscription = await tatum.notification.subscribe.outgoingNativeTx({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all outgoing ETH transactions on ${monitoredAddress}`)
})()
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
  "subscriptionType": "OUTGOING_NATIVE_TX",
  "blockNumber": 3553968,
  "txId": "0xac4b590e7668ca2adfd7cceef398d9859de23e61e1a46cfa9f79ac29a1ddc541",
  "mempool": false
}
```

### Which blockchain networks are supported?

| Blockchain          | Mainnet                     | Testnet                                                              |
| ------------------- | --------------------------- | -------------------------------------------------------------------- |
| Ethereum            | Network.ETHEREUM            | Network.ETHEREUM_SEPOLIA, Network.ETHEREUM_HOLESKY                   |
| Polygon             | Network.POLYGON             | Network.POLYGON_MUMBAI                                               |
| Binance Smart Chain | Network.BINANCE_SMART_CHAIN | Network.BINANCE_SMART_CHAIN_TESTNET                                  |
| Flare               | Network.FLARE               | Network.FLARE_COSTON, Network.FLARE_COSTON_2, Network.FLARE_SONGBIRD |
| Bitcoin             | Network.BITCOIN             | Network.BITCOIN_TESTNET                                              |
| Litecoin            | Network.LITECOIN            | Network.LITECOIN_TESTNET                                             |
| Celo                | Network.CELO                | Network.CELO_ALFAJORES                                               |
| Klaytn              | Network.KLAYTN              | Network.KLATN_BAOBAB                                                 |
| Solana              | Network.SOLANA              | Network.SOLANA_DEVNET                                                |
| Tezos               | Network.TEZOS               | Network.TEZOS_TESTNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |
| XRP                 | Network.XRP                 | Network.XRP_TESTNET                                                  |
