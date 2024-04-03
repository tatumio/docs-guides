---
title: "Use Case and Functionalities"
slug: "use-case-and-functionalities"
excerpt: ""
hidden: false
createdAt: "Tue Feb 06 2024 16:29:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 07:41:46 GMT+0000 (Coordinated Universal Time)"
---
Virtual accounts allow you to build an off-chain exchange type of ledger parallel to the blockchain and bypass the slow and often congested transaction mechanism of the blockchain itself. 

If your customers want to send their crypto outside of your application, they can withdraw it from their virtual account to their blockchain deposit addresses.

> 🚧 This is intended as a self-custodial solution. You are expected to hold 1:1 asset liquidity between your off-chain ledger to your on-chain assets.

## No blockchain fees for off-chain transfers

Because transactions between virtual accounts do not happen on the blockchain, they do not incur blockchain transaction fees and happen instantly. This provides huge benefits for working with blockchains like Ethereum and Bitcoin, both of which have high transaction fees and slow transaction times.

## Grouping multiple Virtual Accounts

Multiple virtual accounts of different currencies can be grouped using a "customer ID". In this way, your customers can easily view the balances of all the currencies they hold with one API call, allowing you to build multi-currency wallets and various fintech applications.

## Deposit addresses and automatic balance updates

A virtual Account has at least one real blockchain address associated with it. This blockchain address is called “deposit address”.

You can either connect an existing blockchain address (or addresses) to the virtual account or generate a new blockchain address and associate it with the account. In either case, the blockchain address becomes a deposit address for this virtual account.

Virtual Accounts automatically scan associated deposit addresses for incoming transactions and update their own balances to reflect the assets received. Whenever any blockchain address connected to a Virtual Account receives an incoming transaction, the virtual account's balance will be updated to reflect the newly received funds.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/4633730-ledger_and_off_chain.webp",
        "",
        "Virtual Account and deposit addresses"
      ],
      "align": "center",
      "caption": "Virtual Account and deposit addresses"
    }
  ]
}
[/block]


If you transfer assets from one virtual account to the other one, the total balance of all virtual accounts does not change.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/bf416a9-va_transfers.webp",
        "",
        "Virtual Account off-chain transfers do not affect on-chain assets"
      ],
      "align": "center",
      "caption": "Virtual Account off-chain transfers do not affect on-chain assets"
    }
  ]
}
[/block]


## Single currency per Virtual Account

Each virtual account is in a single currency. This can be either a cryptocurrency or a virtual fiat currency.

Virtual accounts can be connected to blockchain addresses or represent virtual currencies that can be pegged to a fiat currency. Virtual accounts can be in Bitcoin or Ethereum, Euro or U.S. dollar. Using virtual currencies, you can use fiat and cryptocurrencies in the same way with the same API calls.

Although each virtual account contains a single currency, it can be connected to multiple blockchain addresses for that currency.

> 📘 Virtual accounts can only perform transactions with other virtual accounts of the same currency.

## Running in the background

When a customer transfers assets from their virtual account to a real blockchain address, they do not know where the assets are withdrawn from in the background.

Imagine that you have three customers with their custodial accounts: **A**, **B,** and **C**, and each of them has a virtual account connected to the customer’s blockchain address. 

The following scenario takes place:

1. **Customer_A** received 1 ETH.
2. **Customer_A** transfers this 1 ETH to **Customer_B**.
3. **Customer_B** receives 1 ETH and transfers it to **Customer_C**.
4. **Customer_C** receives 1 ETH and uses it to pay for something (in other words, transfers it to a blockchain address that is outside of your custodial application).

When **Customer_C** transfers 1 ETH to a blockchain address that is outside of your custodial application:

- On the **Virtual Account level**, the amount is deducted from **Customer_C**'s virtual account. -> This is what the customer sees.
- On the **Blockchain level**, the amount is deducted from **Customer_A**'s blockchain address because **Customer_A** is the one who owned that 1 ETH in the beginning. -> This is what you see as the owner of the custodial application.

> 📘 Tatum Virtual Accounts back-end take care of calculating the balance and tracking the assets.
