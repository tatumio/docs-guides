---
title: "Get current rates for multiple crypto assets at once"
slug: "get-current-rates-for-multiple-crypto-assets-at-once"
excerpt: "This endpoint allows you to obtain current exchange rates between fiat/crypto or fiat/fiat."
hidden: false
createdAt: "Thu Feb 22 2024 13:49:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 12:17:36 GMT+0000 (Coordinated Universal Time)"
---
The `getExchangeRates()` method in our API provides a powerful solution similar to the "Get current rate" method. It enables you to obtain current exchange rate information, along with timestamps and the source of the data. 

One notable feature of this method is the ability to request multiple exchange pairs simultaneously. This means you can retrieve exchange rates for various cryptocurrencies all in one API call, saving time and reducing complexity.

# How to use it

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/xxQmQgV",
  "href": "https://codepen.io/tatum-devrel/embed/xxQmQgV",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]


## Request Interface

```typescript
// array of
export class RateBatchDto {
  // fiat
  basePair: Fiat

  // crypto currency/fiat
  currency: Fiat | Currency

  // used to identify pair in batch calls
  batchId?: string
}
```

## Response interface

```typescript
// array of
export class Rate {
  // used to identify pair in batch calls
  batchId?: string

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
