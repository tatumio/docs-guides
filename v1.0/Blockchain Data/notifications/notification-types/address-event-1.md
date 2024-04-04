---
title: "Address Event"
slug: "address-event-1"
excerpt: "Unlock the Power of ADDRESS_EVENT Notifications for Real-Time Balance Updates"
category: 65c0c716d716fe0040919d8b
hidden: false
createdAt: "Thu Mar 07 2024 13:48:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:21:03 GMT+0000 (Coordinated Universal Time)"
---
Monitoring blockchain addresses can be a challenging and resource-intensive task, especially when you need to track balance updates across multiple token types and currencies. However, with Tatum's ADDRESS\_EVENT notification type, you can stay up-to-date with real-time balance updates, allowing you to streamline your operations and enhance the user experience.

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "ADDRESS_EVENT",
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
    
    const subscription = await tatum.notification.subscribe.addressEvent({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all ETH transactions on ${monitoredAddress}`)
})()
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format depends on case whether the address you subscribed on is sending or receiving address.

**You subscribed to a sending address**

In this case you will get two notifications fired in your webhook listener:

1. Related to **`fee`** paid for transaction with defined `"type": "fee"`

```json
{
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "amount": "-0.000031500000168",
  "asset": "ETH",
  "blockNumber": 3553692,
  "txId": "0xde48b2572176eb3e1c4a2a9abe62c5552f778afcbba1ded8491a2ceb675a6390",
  "type": "fee",
  "chain": "ethereum-mainnet",
  "subscriptionType": "ADDRESS_EVENT"
}
```

2. Related to **`transaction`** itself with defined `"type": "native"` or "`fungible"` and etc.

```json
{
  "address": "0xfAF0F447715dEeDF6Dd79c2fd1F7966F0CC647A1",
  "amount": "0.001",
  "asset": "ETH",
  "blockNumber": 3553692,
  "counterAddress": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "txId": "0xde48b2572176eb3e1c4a2a9abe62c5552f778afcbba1ded8491a2ceb675a6390",
  "type": "native",
  "chain": "ethereum-mainnet",
  "subscriptionType": "ADDRESS_EVENT"
}
```

**You subscribed to a receiving address**

In this case you will get only one single notification fired in your webhook listener:

```json
{
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "amount": "0.0001",
  "asset": "ETH",
  "blockNumber": 3553815,
  "counterAddress": "0xfAF0F447715dEeDF6Dd79c2fd1F7966F0CC647A1",
  "txId": "0x24e3c8d20449958b53186feb1844a022b864cba67bbca792330b5ab71035b499",
  "type": "native",
  "chain": "ethereum-mainnet",
  "subscriptionType": "ADDRESS_EVENT"
}
```

# Which blockchain networks are supported?

[block:parameters]
{
  "data": {
    "h-0": "Blockchain",
    "h-1": "Mainnet",
    "h-2": "Testnet",
    "0-0": "**Ethereum**",
    "0-1": "API: ETH  \nSDK: Network.ETHEREUM",
    "0-2": "SDK: Network.ETHEREUM_SEPOLIA, Network.ETHEREUM_HOLESKY",
    "1-0": "**Polygon**",
    "1-1": "Network.POLYGON",
    "1-2": "Network.POLYGON_MUMBAI",
    "2-0": "**Binance Smart Chain**",
    "2-1": "Network.BINANCE_SMART_CHAIN",
    "2-2": "Network.BINANCE_SMART_CHAIN_TESTNET",
    "3-0": "**Flare**",
    "3-1": "Network.FLARE",
    "3-2": "Network.FLARE_COSTON, Network.FLARE_COSTON_2, Network.FLARE_SONGBIRD",
    "4-0": "**Bitcoin**",
    "4-1": "Network.BITCOIN",
    "4-2": "Network.BITCOIN_TESTNET",
    "5-0": "**Litecoin**",
    "5-1": "Network.LITECOIN",
    "5-2": "Network.LITECOIN_TESTNET",
    "6-0": "**Dogecoin**",
    "6-1": "Network.DOGECOIN",
    "6-2": "Network.DOGECOIN_TESTNET",
    "7-0": "**Bitcoin Cash**",
    "7-1": "Network.BITCOIN_CASH",
    "7-2": "Network.BITCOIN_CASH_TESTNET",
    "8-0": "**Celo**",
    "8-1": "Network.CELO",
    "8-2": "Network.CELO_ALFAJORES",
    "9-0": "**Klaytn**",
    "9-1": "Network.KLAYTN",
    "9-2": "Network.KLAYTN_BAOBAB",
    "10-0": "**Solana**",
    "10-1": "Network.SOLANA",
    "10-2": "Network.SOLANA_DEVNET",
    "11-0": "**Tron**",
    "11-1": "Network.TRON",
    "11-2": "Network.TRON_SHASTA",
    "12-0": "**XRP**",
    "12-1": "Network.XRP",
    "12-2": "Network.XRP_TESTNET",
    "13-0": "**Tezos**",
    "13-1": "Network.Tezos",
    "13-2": "Network.TEZOS_TESTNET"
  },
  "cols": 3,
  "rows": 14,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


# Why Use ADDRESS_EVENT Notifications?

The ADDRESS\_EVENT notification type delivers a webhook notification every time there is a balance update on a monitored address. This comprehensive notification system covers incoming and outgoing transactions for native currencies, as well as popular token standards like ERC-20, ERC-721, and ERC-1155. Moreover, it even tracks internal smart contract native transfers, ensuring a seamless monitoring experience across various blockchain activities.

Here are some key benefits of using ADDRESS_EVENT notifications:

### Real-time Monitoring

Stay informed about balance changes as they happen. ADDRESS\_EVENT notifications provide real-time updates, enabling you to react promptly to important events and ensuring that your application or platform always has the latest information.

### Simplified Tracking

With support for native currencies, as well as popular token standards like ERC-20, ERC-721, and ERC-1155, ADDRESS\_EVENT notifications simplify the process of tracking balance changes across multiple token types. This feature allows you to focus on building functionality around these events, rather than spending time and resources on parsing raw blockchain data.

### Enhanced Security

By receiving real-time notifications about balance changes, you can monitor your accounts or smart contracts for any suspicious activity. In case of unauthorized transactions or potential security risks, you can take immediate action to mitigate potential losses.

### Improved User Experience

Integrating ADDRESS\_EVENT notifications into your application or platform keeps your users informed about balance updates, enhancing their experience and fostering trust in your service. Timely information empowers users to make informed decisions and interact confidently with your platform.
