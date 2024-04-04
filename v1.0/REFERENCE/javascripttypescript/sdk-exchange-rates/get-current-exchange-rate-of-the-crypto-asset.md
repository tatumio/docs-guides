---
title: "Get current exchange rate of the crypto asset"
slug: "get-current-exchange-rate-of-the-crypto-asset"
excerpt: "This endpoint allows you to obtain current exchange rate between fiat/crypto or fiat/fiat."
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Thu Feb 22 2024 13:48:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 12:15:40 GMT+0000 (Coordinated Universal Time)"
---
The `getExchangeRate()` method offers a seamless way to retrieve up-to-date exchange rate information for cryptocurrencies. By invoking this method, you can effortlessly access the current exchange rate, along with the corresponding timestamp and the reliable source of the data.

# How to use it

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const rate = await tatum.rates.getCurrentRate("BTC","EUR")
```

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/poQqQNB",
  "href": "https://codepen.io/tatum-devrel/embed/poQqQNB",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


# Request Interface

```typescript
export class RateBatchDto {
  // fiat
  basePair: Fiat

  // crypto currency/fiat
  currency: Fiat | Currency
}
```

# Response interface

```typescript
export class Rate {
  // crypto currency/fiat
  _id: Fiat | Currency

  // the amount of basePair that can be exchanged for 1 _id (crypto currency/fiat)
  value: string

  // fiat
  basePair: Fiat

  // timestamp of rate information from source
  timestamp: number

  // source of rate
  source: string
}
```

# Supported FIAT

See the full wide range of fiat currencies we support for the exchange  submodule on this page.

# Supported Crypto Currency

See the full wide range of crypto currencies we support for the exchange  submodule on this page.
