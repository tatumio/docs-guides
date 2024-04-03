---
title: "API Key is now a required parameter for Faucets"
slug: "api-key-is-now-a-required-parameter-for-faucets"
type: "improved"
createdAt: "Fri Nov 24 2023 11:26:00 GMT+0000 (Coordinated Universal Time)"
hidden: true
---
To ensure that the faucet service is not abused we have updated the fund function in the Faucets submodule to require a testnet key, which can be acquired for free in our [dashboard](https://dashboard.tatum.io/).

```coffeescript JavaScript
import { TatumSDK, Network, Ethereum } from '@tatumio/tatum'

// What changed
const tatum = await TatumSDK.init<Ethereum>({
  network: Network.ETHEREUM_SEPOLIA,
  // Include this line to have api key.
  apiKey: { v4: 'YOUR-API-KEY'}
})
```