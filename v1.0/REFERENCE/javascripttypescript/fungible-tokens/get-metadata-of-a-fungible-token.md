---
title: "Get metadata of a fungible token"
slug: "get-metadata-of-a-fungible-token"
excerpt: ""
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Thu Feb 22 2024 13:40:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:46:34 GMT+0000 (Coordinated Universal Time)"
---
Fungible tokens can carry associated metadata, which is a set of data that provides information about the token's properties. Although each token is indistinguishable in value, metadata can specify attributes such as the token's name, symbol, or total supply. In the realm of cryptocurrencies, metadata is often used to create a clearer understanding of the token's purpose or functionality. For instance, a utility token's metadata might detail the specific service or access it provides within its platform. Similarly, a governance token's metadata could illustrate the voting rights or privileges it conveys in a Decentralised Autonomous Organisation (DAO). Thus, metadata provides essential context, enhancing the fungible tokens' usability in diverse scenarios.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/BaGvOoe",
  "href": "https://codepen.io/tatum-devrel/embed/BaGvOoe",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


# How to show the metadata of a fungible token on the Ethereum network

Use the TatumSDK (`@tatumio/tatum`) to get the token metadata.

```typescript
// yarn add @tatumio/tatum
import { TatumSDK, Network, Ethereum, ResponseDto, TokenMetadata } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const response: ResponseDto<TokenMetadata> = await tatum.token.getTokenMetadata({
        tokenAddress: '0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48',
      })

console.log(response.data)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const result = await tatum.token.getTokenMetadata({
        tokenAddress: '0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48',
      })
      
    console.log(result.data);
  } catch (error) {
    console.error("Error fetching token metadata:", error);
  }
})();
```
```curl
curl --location --request GET 'https://api.tatum.io/v4/data/tokens?tokenAddress=0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48&chain=ethereum'
```

# Expected Response

```json
{
  "symbol":"USDC",
  "name":"USD Coin",
  "supply":"26667389920178985",
  "decimals":6,
  "type":"fungible",
  "cap":"undefined"
}
```

# Request interface

```typescript
interface TokenAddress {
  /**
   * Token contract address
   */
  tokenAddress: string
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

interface TokenMetadata {
  /**
   * Symbol of the fungible token.
   */
  symbol: string
  /**
   * Full name of the fungible token
   */
  name: string
  /**
   * Total supply of the fungible token.
   */
  supply: string
  /**
   * Number of decimal places for the fungible token.
   */
  decimals: number
  /**
   * Type of the token - fungible
   */
  type: string
  /**
   * Maximum supply cap of the fungible token.
   */
  cap: string
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
