---
title: "Get all assets the wallet holds"
slug: "get-all-assets-the-wallet-holds"
excerpt: "This endpoint can help you fetch all the Assets a wallet holds including   native tokens, fungible tokens, non fungible tokens & multitokens."
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Thu Feb 22 2024 13:42:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:57:45 GMT+0000 (Coordinated Universal Time)"
---
[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/xxQmQxG",
  "href": "https://codepen.io/tatum-devrel/embed/xxQmQxG",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


Managing digital assets across various blockchain networks can be a challenging task. However, with TatumSDK, a powerful TypeScript library, developers can effortlessly retrieve wallet balances from multiple blockchains using a unified interface. This guide will demonstrate how to leverage TatumSDK's cross-chain capabilities to obtain wallet balances on Ethereum and Bitcoin, two popular, yet different blockchain networks. By following the steps outlined, you'll be able to streamline the development process and build applications that easily interact with multiple blockchains, saving time and reducing complexity.

# How to get a balance on Ethereum network

Use the TatumSDK (`@tatumio/tatum`) to get a balance of the wallet.

> 📘 Hint
> 
> TatumSDK wraps multiple different calls to the Tatum API together in 1 function, so we don't show here the curl example for using direct HTTP API calls. You can check the API documentation for specific operations, which are internally used inside the library.

```typescript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto, AddressBalance} from '@@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const balance: ResponseDto<AddressBalance[]> = await tatum.address.getBalance({
  addresses: ['0xF64E82131BE01618487Da5142fc9d289cbb60E9d'], // replace with your address
})

console.log(balance.data)
```
```javascript
// Install with: npm install @tatumio/tatum
import { TatumSDK, Network } from "@tatumio/tatum";

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const balance = await tatum.address.getBalance({
      addresses: ['0xF64E82131BE01618487Da5142fc9d289cbb60E9d'], // replace with your address
    });
    console.log(balance.data);
  } catch (error) {
    console.error("Error fetching wallet balance:", error);
  }
})();
```

## Expected Response

```json
[
    {
        asset: 'ETH',
        address: '0xF64E82131BE01618487Da5142fc9d289cbb60E9d',
        decimals: 18,
        balance: '0.001',
        type: 'native',
    }
]
```

# How to get a balance on the Bitcoin network

In order to get a balance of a Bitcoin address, you can use the same approach and reuse the same code.

```typescript
// yarn add @tatumcom/js
import {TatumSDK, Network, Bitcoin, ResponseDto, AddressBalance} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const balance: ResponseDto<AddressBalance[]> = await tatum.address.getBalance({
  addresses: ['bc1q7zw9ax8tm4jk2k2674u6lcd9fwjut8kqtvfeg8'], // replace with your address
})

console.log(balance.data)

// Expected outcome
// [{
//     asset: 'BTC',
//     address: 'bc1q7zw9ax8tm4jk2k2674u6lcd9fwjut8kqtvfeg8',
//     decimals: 8,
//     balance: '0.001',
//     type: 'native',
// }]
```
```javascript
// Install with: npm install @tatumcom/js
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.BITCOIN });
    const balance = await tatum.address.getBalance({
      addresses: ["bc1q7zw9ax8tm4jk2k2674u6lcd9fwjut8kqtvfeg8"], // replace with your address
    });
    console.log(balance.data);
  } catch (error) {
    console.error("Error fetching wallet balance:", error);
  }
})();

// Expected outcome
// [{
//     asset: 'BTC',
//     address: 'bc1q7zw9ax8tm4jk2k2674u6lcd9fwjut8kqtvfeg8',
//     decimals: 8,
//     balance: '0.001',
//     type: 'native',
// }]
```

You can see, that the same request and response is used for different blockchain networks.

## Request interface

```typescript
interface AddressBalanceDetails {
  /**
   * List of addresses to check. Some blockchain network supports only 1 address at a time
   */
  addresses: string[]
  /**
   * Optional page size. If not specified, the default page size is used, which is 10.
   */
  pageSize?: number
  /**
   * Optional page number. If not specified, the first page is returned.
   */
  page?: number
}
```

## Response interface

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

interface AddressBalance {
  /**
   * Blockchain address of the balance.
   */
  address: string
  /**
   * Asset of the balance. For native currencies, it's always present. For tokens, only when readable from the contract `symbol()` method.
   */
  asset?: string
  /**
   * Decimals of the asset. Valid for native and fungible tokens. For tokens, only when readable from the contract `decimals()` method.
   */
  decimals?: number
  /**
   * Balance of the address.
   */
  balance: string
  /**
   * Type of the balance.
   */
  type: 'native' | 'fungible' | 'nft' | 'mutlitoken'
  /**
   * Optional token contract address. Valid only for tokens (USDT, NFTs of any kind), not for native network balances (ETH, BTC).
   */
  tokenAddress?: string
  /**
   * Optional token ID. Valid only for non-fungible and semi-fungible tokens.
   */
  tokenId?: string
  /**
   * Block number of the last balance update.
   */
  lastUpdatedBlock?: number
}
```

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "h-1": "Support",
    "0-0": "Ethereum / Ethereum Sepolia  \nBNB Smart Chain / BNB Smart Chain Testnet  \nCelo / Celo Alfajores  \nPolygon / Polygon Mumbai  \nChilliz",
    "0-1": "Multiple addresses per 1 invocation  \nNative Assets  \nERC-20 Tokens (USDT, USDC,...)  \nNFTs (BAYC,...)  \nERC-1155 Tokens",
    "1-0": "Solana / Solana Devnet",
    "1-1": "Multiple addresses per 1 invocation  \nNative Assets (SOL)",
    "2-0": "XRP / XRP Testnet  \nBitcoin / Bitcoin Testnet  \nLitecoin / Litecoin Testnet  \nDogecoin / Dogecoin Testnet  \nCardano / Cardano Preprod",
    "2-1": "Native Assets  \nOnly 1 address per 1 invocation"
  },
  "cols": 2,
  "rows": 3,
  "align": [
    "left",
    "left"
  ]
}
[/block]
