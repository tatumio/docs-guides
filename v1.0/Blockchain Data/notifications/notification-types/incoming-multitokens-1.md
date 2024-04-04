---
title: "Incoming Multitokens"
slug: "incoming-multitokens-1"
excerpt: "Stay Informed on Multi-Token Transactions with INCOMING_MULTITOKEN_TX   Notifications"
category: 65c0c716d716fe0040919d8b
hidden: false
createdAt: "Thu Mar 07 2024 14:31:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 08 2024 17:26:14 GMT+0000 (Coordinated Universal Time)"
---
In the dynamic world of blockchain, keeping track of multi-token transactions is crucial for maintaining a secure and efficient platform. Tatum's INCOMING_MULTITOKEN_TX notification type offers a powerful solution to help you stay informed about incoming multi-token transactions (e.g., ERC-1155 transfers) involving a specific address.

A MultiToken (ERC-1155) could be likened to a series of limited edition art prints, where each print belongs to the same series but has its unique edition number. In this scenario, ERC-1155 tokens can represent both the series (fungible aspect) and the individual editions (non-fungible aspect) within a single smart contract, allowing for seamless management and transfer of value.

# How to do it?

```curl curl
curl -i -X POST   
</strong>  <https://api.tatum.io/v4/subscription?type=mainnet>   
  -H 'Content-Type: application/json'   
  -H 'x-api-key: <YOUR-API-KEY>'   
  -d '{  
    "type": "INCOMING_MULTITOKEN_TX",  
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
    
    const subscription = await tatum.notification.subscribe.incomingMultitokenTx({
        address: monitoredAddress,
        url: 'https://<YOUR_WEBHOOK_URL>' // replace with your handler URL
    })
    console.log(`Now you will be notified about all incoming MultiToken transactions on ${monitoredAddress}`)
})()
```

# What does the fired webhook look like?

The fired notification webhook you will receive in your webhook listener will have the following format.

```json
{
  "currency": "ETH",
  "chain": "ethereum-mainnet",
  "amount": "1",
  "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "counterAddress": "0x690B9A9E9aa1C9dB991C7721a92d351Db4FaC990",
  "subscriptionType": "INCOMING_MULTITOKEN_TX",
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
| Ethereum            | Network.ETHEREUM            | Network.ETHEREUM_SEPOLIA,  Network.ETHEREUM_HOLESKY                  |
| Polygon             | Network.POLYGON             | Network.POLYGON_MUMBAI                                               |
| Binance Smart Chain | Network.BINANCE_SMART_CHAIN | Network.BINANCE_SMART_CHAIN_TESTNET                                  |
| Flare               | Network.FLARE               | Network.FLARE_COSTON, Network.FLARE_COSTON_2, Network.FLARE_SONGBIRD |
| Celo                | Network.CELO                | Network.CELO_ALFAJORES                                               |
| Klaytn              | Network.KLAYTN              | Network.KLAYTN_BAOBAB                                                |
