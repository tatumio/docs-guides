---
title: "Create a fungible token"
slug: "create-a-fungible-token"
excerpt: ""
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Thu Feb 22 2024 13:41:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:49:07 GMT+0000 (Coordinated Universal Time)"
---
Creating a fungible token involves defining the parameters of the token, such as its name, symbol, and total supply, within a smart contract on a blockchain network like Ethereum. The distinguishing feature of fungible tokens, created using standards like ERC-20 or BEP-20, is their interchangeability. Each token is identical to the others in its set, meaning they can be exchanged on a one-for-one basis. This is in contrast to non-fungible tokens (NFTs), which are unique and not interchangeable, with each NFT representing a distinct asset or value.

# How to create a fungible token on the Ethereum Sepolia network

Use the TatumSDK (`@tatumio/tatum`) to create the token.

```typescript
// yarn add @tatumio/tatum
import { TatumSDK, Network, Ethereum, ResponseDto, TokenMetadata } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.token.createNewFungibleToken({
        name: 'Test Token',
        symbol: 'MY_TKN',
        initialHolder: '0x48fa1676cfd0dfa23a71829c4c6d56874a88fa48', 
        initialSupply: '1000000',
        owner: '0x48fa1676cfd0dfa23a71829c4c6d56874a88fa48',
      })

console.log(result)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM_SEPOLIA });
    const result = await tatum.token.createNewFungibleToken({
        name: 'Test Token',
        symbol: 'MY_TKN',
        initialHolder: '0x48fa1676cfd0dfa23a71829c4c6d56874a88fa48', 
        initialSupply: '1000000',
        owner: '0x48fa1676cfd0dfa23a71829c4c6d56874a88fa48',
      })
      
    console.log(result.data);
  } catch (error) {
    console.error("Error fetching token metadata:", error);
  }
})();
```
```curl
curl --location --request POST 'https://api.tatum.io/v4/contract/deploy?type=testnet' -H "Content-Type: application/json" -d '{"chain":"ethereum-sepolia","contractType":"fungible","name":"Test Token","symbol":"MY_TKN","initialHolder":"0x48fa1676cfd0dfa23a71829c4c6d56874a88fa48","initialSupply":"1000000","owner":"0x48fa1676cfd0dfa23a71829c4c6d56874a88fa48"}'  
```

# Expected Response

```json
{ 
    "txId":"0x6f0ef980ee7c5289d10c8ee8cb5e1763ae72074d20424e2c3258f703c4ee7fba" 
}
```

# Use cases of fungible tokens include:

- **Native Tokens for Platforms/Projects:** For example, Binance Coin (BNB) is the native token of Binance, serving both as a cryptocurrency and a utility token within the platform. It's used for transaction fees, participating in new token sales, and more.
- **Stablecoins:** Tokens like USDT and USDC are examples of stablecoins, designed to maintain a stable value by being pegged to a reserve of assets, typically a fiat currency like USD. This provides stability in the volatile crypto markets.
- **Governance Tokens:** Governance tokens, such as Maker (MKR), grant voting rights within a Decentralized Autonomous Organization (DAO). Holders of these tokens can vote on key aspects of the project, influencing its direction and policies.
- **Reward Tokens:** Certain protocols, like Compound, use fungible tokens (in this case, COMP) as rewards to incentivise user engagement and participation within the platform. These tokens can also grant voting rights, enhancing the protocol's decentralised governance.

# Request interface

```typescript
interface CreateFungibleToken {
  /**
   * Address of the fungible token owner
   */
  owner: string
  /**
   * Optional. Address of the fungible token minter, it defaults to the owner address
   */
  minter?: string
  /**
   * Optional. Address of the fungible token pauser, it defaults to the owner address
   */
  pauser?: string
  /**
   * Name of fungible token
   */
  name: string
  /**
   * Symbol of fungible token
   */
  symbol: string
  /**
   * Initial supply of fungible token
   */
  initialSupply: string
  /**
   * Initial holder of fungible token
   */
  initialHolder: string
  /**
   * Optional. Number of decimal places for the fungible token, it defaults to 18
   */
  decimals?: string
}
```

# Response interface

```typescript
interface ResponseDto<T> {
  /**
   * Actual payload of the response
   */
  data: T
  /**
   * Status of the response
   */
  status: Status
  /**
   * In case of ERROR status, this field contains the error message and detailed description
   */
  error?: ErrorWithMessage
}

interface TxIdResponse {
  /**
   * Id of the transaction
   */
  txId: string
}
```

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "0-0": "Ethereum / Ethereum Sepolia  \nBNB Smart Chain / BNB Smart Chain Testnet  \nCelo / Celo Alfajores  \nPolygon / Polygon Mumbai"
  },
  "cols": 1,
  "rows": 1,
  "align": [
    null
  ]
}
[/block]
