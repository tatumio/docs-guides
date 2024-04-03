---
title: "Get all fungible tokens the wallet holds"
slug: "get-all-fungible-tokens-the-wallet-holds"
excerpt: "This function helps you to fetch all the fungible tokens a wallet holds, all   you have to do is pass the address to the function parameter and chain while initialising the SDK."
hidden: false
createdAt: "Thu Feb 22 2024 13:39:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:36:30 GMT+0000 (Coordinated Universal Time)"
---
The "Get all fungible tokens the wallet holds" function is designed to retrieve information about all the fungible tokens stored in a specific wallet. By providing the wallet address as a parameter and initialising the software development kit (SDK) with the appropriate blockchain, this function enables users to fetch data regarding the fungible tokens associated with that particular wallet.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/gOQZjjj",
  "provider": "codepen.io",
  "href": "https://codepen.io/tatum-devrel/embed/gOQZjjj",
  "typeOfEmbed": "iframe",
  "height": "500px",
  "width": "100%",
  "iframe": true
}
[/block]


# How to get fungible tokens on a wallet in the Ethereum network

Use the TatumSDK (`@tatumio/tatum`) to get a balance of the wallet.

```typescript
// yarn add @tatumio/tatum
import { TatumSDK, Network, Ethereum, ResponseDto, FungibleTokenBalance } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM })

const balance: ResponseDto<FungibleTokenBalance[]> = await     tatum.token.getBalance({
   addresses: ['0x78E851C35326c9296485E9720D85CB3Bd153b428'], // replace with your address
 })

console.log(balance.data)
```
```javascript
// Install with: npm install @tatumio/tatum
const { TatumSDK, Network } = require("@tatumio/tatum");

(async () => {
  try {
    const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
    const balance = await tatum.token.getBalance({ addresses: ['0x78E851C35326c9296485E9720D85CB3Bd153b428'], // replace with your address
    });
    console.log(balance.data);
  } catch (error) {
    console.error("Error fetching balances of fungible tokens:", error);
  }
})();
```
```curl
curl --location --request GET 'https://api.tatum.io/v4/data/balances?chain=ethereum&addresses=0x78E851C35326c9296485E9720D85CB3Bd153b428&tokenTypes=fungible'
```

# Expected Response

```json
[
  {
    chain: 'ethereum-mainnet',
    tokenAddress: '0xd110bb8a24b100c37af7310416e685af807c1f10',
    type: 'fungible',
    lastUpdatedBlockNumber: 8167878,
    address: '0x78e851c35326c9296485e9720d85cb3bd153b428',
    balance: '0.0006'
  },
  {
    chain: 'ethereum-mainnet',
    tokenAddress: '0x1fcdce58959f536621d76f5b7ffb955baa5a672f',
    type: 'fungible',
    lastUpdatedBlockNumber: 8348276,
    address: '0x78e851c35326c9296485e9720d85cb3bd153b428',
    balance: '1'
  },
  {
    chain: 'ethereum-mainnet',
    tokenAddress: '0x558ec3152e2eb2174905cd19aea4e34a23de9ad6',
    type: 'fungible',
    lastUpdatedBlockNumber: 12136720,
    address: '0x78e851c35326c9296485e9720d85cb3bd153b428',
    balance: '201.752'
  }
]
```

# Request interface

```typescript
interface AddressBalanceDetails {
  /**
   * List of addresses to check.
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

interface FungibleTokenBalance {
  /**
   * Blockchain network
   */
  chain: string
  /**
   * Token contract address
   */
  tokenAddress: string
  /**
   * Token type, default 'fungible' (ERC-20).
   */
  type: 'fungible'

  /**
   * Block number of the last balance update.
   */
  lastUpdatedBlockNumber: number

  /**
   * Address
   */
  address: string

  /**
   * Balance of the address.
   */
  balance: string
}
```

# Supported blockchain networks

[block:parameters]
{
  "data": {
    "h-0": "Network",
    "h-1": "Support",
    "0-0": "Ethereum / Ethereum Sepolia  \nBNB Smart Chain / BNB Smart Chain Testnet  \nCelo / Celo Alfajores  \nPolygon / Polygon Mumbai",
    "0-1": "Multiple addresses per 1 invocation"
  },
  "cols": 2,
  "rows": 1,
  "align": [
    null,
    null
  ]
}
[/block]
