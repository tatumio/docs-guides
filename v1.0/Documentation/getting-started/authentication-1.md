---
title: "Authentication"
slug: "authentication-1"
excerpt: ""
category: 65a8e44fccf94800381cd6f6
hidden: false
createdAt: "Fri Feb 09 2024 08:39:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 13:34:46 GMT+0000 (Coordinated Universal Time)"
---
When using the Tatum API or SDK, you authenticate yourself with an API key. Access our services securely by authenticating with your Tatum account through available methods listed below, ensuring a secure and personalized experience. While it is possible to connect without authentication, please note that this approach provides limited access and functionalities.

To obtain the API key, [create a Tatum account](https://dashboard.tatum.io/signup). Once you are signed into the Dashboard, you are automatically assigned the Free plan.

The API key represents your pricing plan and defines how many API calls you can make per second and what the total number of API calls per month is available for you.

# Auth API Keys: Mainnet vs Testnet

When you sign up in the [Tatum.io Dashboard](https://dashboard.tatum.io/login), you'll get one development (Testnet) Auth API key and one for production (Mainnet) API key. You can create more API keys as you need them.

- **Mainnet** stands for "main network". This is where your production app will run.
- **Testnet** stands for "testing network". In most cases, has the same features and characteristics as the mainnet. The Testnet blockchain is completely isolated from the Mainnet blockchain. It doesn't have the same data, and it doesn't guarantee data persistence. On the other hand, all operations on the Testnet are free. This makes Testnet a great environment for developing and testing apps.

> 🚧 All **Mainnet** transactions are final. If you send assets like BTC to the wrong address over Testnet it's fine since Testnet assets hold no value. However, if this happens in Mainnet, you'll lose real money!

# X-API-Key

```curl
curl --location 'https://02-dallas-022-01.rpc.tatum.io'
--header 'Content-Type: application/json' 
--user 'x-api-key:<YOUR-API-KEY>' 
--data '{
    "jsonrpc":"2.0",
    "method":"web3_clientVersion",
    "params":[],
    "id":1
}'
```
```typescript
const tatum = await TatumSDK.init<Ethereum>({
  network: Network.ETHEREUM,
  apiKey: {
   v3: 'YOUR_API_KEY_V3',
   v4: 'YOUR_API_KEY_V4'
})
```

## X-API-Key as a part of URL

```curl
curl --location 'https://x-api-key:<YOUR-API-KEY>@02-dallas-022-01.rpc.tatum.io'
--header 'Content-Type: application/json' 
--data '{
    "jsonrpc":"2.0",
    "method":"web3_clientVersion",
    "params":[],
    "id":1
}'
```

# Auth Bearer

```curl
curl --location 'https://02-dallas-022-01.rpc.tatum.io' 
--header 'Content-Type: application/json' 
--header 'Authorization: bearer <YOUR-API-KEY>' 
--data '{
    "jsonrpc":"2.0",
    "method":"web3_clientVersion",
    "params":[],
    "id":1
}'
```

# Basic Auth (with base64 encoding)

Please use following base64 format: x-api-key:<YOUR-API-KEY>

```curl
curl --location 'https://02-dallas-022-01.rpc.tatum.io' 
--header 'Content-Type: application/json' 
--header 'Authorization: Basic eC1...S0x' 
--data '{
    "jsonrpc":"2.0",
    "method":"web3_clientVersion",
    "params":[],
    "id":67
}'
```

# API Key in the SDK

```typescript
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({
    network: Network.ETHEREUM, 
    apiKey: { v4: 'YOU-API-KEY'}
    }
)
```
