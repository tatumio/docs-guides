---
title: "VA - Error XPUB not compatible"
slug: "va-error-xpub-not-compatible"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 22:31:55 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:31:55 GMT+0000 (Coordinated Universal Time)"
---
When you create a virtual account based on a cryptocurrency (for example, BTC or ETH), you usually need to provide the extended public key (xpub) of the blockchain wallet that will be connected to the account.

However, this is not true for all wallets. When that happens, you will get an error looking as follows:

```json JSON
{
    “statusCode”: 403,
    “errorCode”: “account.xpub.incompatible”,
    “message”: “Xpub not compatible with account currency.”
}
```

## Good to know

- Not all blockchains provide xpub for wallets, or Tatum may not support wallets on some blockchains. In those cases, use the wallet address or the account address instead. In the case of Solana as well as a few others, you need to use the address you got from [Generated Wallet](https://apidoc.tatum.io/tag/Solana/#operation/SolanaGenerateWallet).
- Adding XPUB to the VA does not connect any specific blockchain address to the account. XPUB is a generator of addresses, not an address by itself. Find the REST API endpoint reference at [the following link](https://apidoc.tatum.io/tag/Account/#operation/createAccount).
