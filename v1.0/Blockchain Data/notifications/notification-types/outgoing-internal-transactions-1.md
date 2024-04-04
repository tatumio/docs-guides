---
title: "Outgoing internal transactions"
slug: "outgoing-internal-transactions-1"
excerpt: "Enhance Your Smart Contract Monitoring with OUTGOING_INTERNAL_TX Notifications"
category: 65c0c716d716fe0040919d8b
hidden: false
createdAt: "Thu Mar 07 2024 14:18:23 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:18:24 GMT+0000 (Coordinated Universal Time)"
---
In the dynamic world of blockchain, staying updated with transactions involving smart contracts is essential for maintaining a secure and efficient platform. Tatum's OUTGOING_INTERNAL_TX notification type offers a powerful solution to help you track outgoing native balance updates on a monitored smart contract.

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "OUTGOING_INTERNAL_TX",
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
    
    const monitoredSmartContract = '0xF64E82131BE01618487Da5142fc9d289cbb60E9d'
    
    const subscription = await tatum.notification.subscribe.outgoingInternalTx({
        address: monitoredSmartContract,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all outgoing ETH transactions on ${monitoredSmartContract}`)
})()
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "txId": "0x062d236ccc044f68194a04008e98c3823271dc26160a4db9ae9303f9ecfc7bf6",
  "blockNumber": 2913059,
  "subscriptionType": "OUTGOING_INTERNAL_TX",
  "mempool": false,
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "counterAddress": "0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990",
  "amount": "0.001"
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
| Tezos               | Network.TEZOS               | Network.TEZOS_TESTNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |
