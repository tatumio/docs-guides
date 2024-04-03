---
title: "Incoming NFTs"
slug: "incoming-nfts-1"
excerpt: "Stay Updated on Non-Fungible Token Transactions with INCOMING_NFT_TX Notifications"
hidden: false
createdAt: "Thu Mar 07 2024 14:38:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 14:39:00 GMT+0000 (Coordinated Universal Time)"
---
In the ever-expanding world of blockchain, keeping track of non-fungible token (NFT) transactions is crucial for maintaining a secure and efficient platform. Tatum's INCOMING_NFT_TX notification type offers a powerful solution to help you stay informed about incoming non-fungible token transactions (e.g., ERC-721 / SPL transfers) involving a specific address.

> 📘 Hint
> 
> A non-fungible token (NFT) is a unique digital asset that represents ownership of a one-of-a-kind item or piece of content, such as digital art, virtual real estate, or collectibles. Unlike fungible tokens, NFTs are not interchangeable and each NFT has a distinct value based on its rarity, provenance, and the demand for that specific token.
> 
> There are different NFT standards, most known are ERC-721 on EVM chains or SPL

# How to do it?

```curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: <YOUR-API-KEY>' \
  -d '{
    "type": "INCOMING_NFT_TX",
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
    
    const subscription = await tatum.notification.subscribe.incomingNftTx({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all incoming NFT transactions on ${monitoredAddress}`)
})()
```

> 📘 Hint
> 
> This notification will be fired no matter what kind of NFT is being transferred.

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "amount": "1", 
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d", 
  "counterAddress": "0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990",
  "subscriptionType": "INCOMING_NFT_TX",
  "blockNumber": 110827114, 
  "txId": "0xe118976ba31815f81301341b4e211825bce1393cac1c4215075177b0a6b98930", 
  "contractAddress": "0x7d3dda0430471fe460c07b1ecab35670ef4ce85b", 
  "tokenId": "1450000023306",
  "metadataURI": "https://touhao.bj.bcebos.com/nft/metadata/1450000023306.json"
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
| Klaytn              | Network.KLAYTN              | Network.KLAYTN_BAOBAB                                                |
| Solana              | Network.SOLANA              | Network.SOLANA_DEVNET                                                |
| Tezos               | Network.TEZOS               | Network.TEZOS_TESTNET                                                |
| Tron                | Network.TRON                | Network.TRON_SHASTA                                                  |
