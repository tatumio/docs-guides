---
title: "Outgoing Tokens"
slug: "outgoing-tokens-1"
excerpt: "Stay on Top of Token Transactions with OUTGOING_FUNGIBLE_TX Notifications"
hidden: false
createdAt: "Thu Mar 07 2024 14:35:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:35:18 GMT+0000 (Coordinated Universal Time)"
---
In the dynamic world of blockchain, staying updated with fungible token transactions is vital for maintaining a secure and efficient platform. Tatum's `OUTGOING_FUNGIBLE_TX` notification type offers a powerful solution to help you track outgoing fungible token transactions (e.g., ERC-20 / SPL transfers) from a specific address.

> 📘 Hint
> 
> A fungible token is a type of digital asset that is interchangeable and holds the same value across all its individual units. Examples of fungible tokens include popular cryptocurrencies like Bitcoin (BTC) and Ether (ETH), as well as ERC-20 tokens like Chainlink (LINK) and USD Coin (USDC), which can be easily exchanged, divided, and combined without altering their overall worth.

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "OUTGOING_FUNGIBLE_TX",
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
    
    const subscription = await tatum.notification.subscribe.outgoingFungibleTx({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all outgoing token transactions on ${monitoredAddress}`)
})()
```

> 📘 Hint
> 
> This notification will be fired no matter what kind of Token leaves the monitored address.

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "amount": "1",
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "counterAddress": "0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990",
  "subscriptionType": "OUTGOING_FUNGIBLE_TX",
  "blockNumber": 2913059,
  "txId": "0x062d236ccc044f68194a04008e98c3823271dc26160a4db9ae9303f9ecfc7bf6",
  "contractAddress": "0x743e8b6cc1676adae0e3243b5c011f7139c26128"
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
| Solana              | Network.SOLANA              | Network.SOLANA_DEVNET                                                |
| Tezos               | Network.TEZOS               | Network.TEZOS_TESTNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |
