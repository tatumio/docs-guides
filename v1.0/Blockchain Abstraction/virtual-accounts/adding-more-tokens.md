---
title: "Adding more tokens"
slug: "adding-more-tokens"
excerpt: "Tatum Virtual Accounts can support any existing or new ERC-20 (or compatible) token which is not included out of the box. This guide explains how."
category: 65a8e44fccf94800381cd6f8
hidden: false
createdAt: "Tue Feb 06 2024 16:31:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 07:42:00 GMT+0000 (Coordinated Universal Time)"
---
Adding more ERC-20 (or compatible) tokens to your Virtual Account ledger can be done with a few steps. You will need to create a new Virtual Account and register a new Virtual Currency representing the token inside your ledger. 

To do so, there are a few parameters required like "`symbol`", "`supply`" (of a selected blockchain deposit address), "`digits`", "`name`" and "`tokenAddress`".

# Steps

The following guide was executed in the ETH-Testnet (Sepolia). All steps are also applicable to Mainnet.

**Example - key parameters:**

```json JSON
//Token to add in the Virtual Account ledger
"symbol": "TTOKEN",  
"decimals": 18,  
"description": "Tatum_Token", //The token "name" as seen in the blockchain
"TokenAddress":"0xCf15c60f66e49d3C41a98717eb0f40AcD764DD57",

//Blockchain deposit address - acting as the initial "token holder" for the Virtual Account 
"address": "0x7a8c2f6f3bd2dc45812e5daae0373eaef2e2dddd",
"supply": "50000", //At the time of linking the EOA to the VA, the address was holding 500000 tokens
```

> 📘 Token details are available in the Ethereum (Sepolia) chain at [the following link](https://sepolia.etherscan.io/token/0xCf15c60f66e49d3C41a98717eb0f40AcD764DD57).

## Step_1:

Create a new Virtual Account with the token details - v3 REST API endpoint:

- [EVM](https://apidoc.tatum.io/tag/Blockchain-operations#operation/registerErc20Token) - `/v3/offchain/token/:chain`
- [TRON](https://apidoc.tatum.io/tag/Blockchain-operations#operation/createTrc) - `/v3/offchain/tron/trc`

```json cURL
curl --location '<https://api.tatum.io/v3/offchain/token/ETH'>  
--header 'Content-Type: application/json'  
--header 'x-api-key: {testnet_API_KEY}'  
--data '{  
  "symbol": "TTOKEN",  
  "supply": "50000",  
  "decimals": 18,  
  "description": "Tatum_Token",  
  "basePair": "USD",  
  "address": "0x7a8c2f6f3bd2dc45812e5daae0373eaef2e2dddd",  
  "customer":{  
        "externalId": "EX_CUST_1"  
    }  
}'  
//response:  
{  
    "accountId": "646dfe380b4f44ca693f12b1",  
    "address": "0x7a8c2f6f3bd2dc45812e5daae0373eaef2e2dddd"  
}
```

**Payload details:**

- “`Symbol`”: must be the same as the token to add. Check the token SmartContract details
- “`Decimals`”: must be the same as the token to add. Check the token SmartContract details
- “`Supply`”: Considering we are adding a blockchain address with potentially existing funds as the Virtual account deposit address, for data consistency, it is best to match the amount available in the blockchain address at the time of this operation, so the Virtual Account off-chain balance will match with the amount of on-chain balance of the deposit address.
- “`Description`” is the name of the token. Check the token SmartContract details
- “`basePair`” by default 1:1. Virtual Account transactions value will be calculated according to this base pair.
- “`Address`”: the blockchain address where the on-chain "`supply`" is located. --> Acts as any other "deposit address" for a Virtual Account. Make sure this address holds as much coin as you set up in the "`supply`" param. **You are expected to control the PrivateKey of this address**
- "`externalId`": This optional parameter is intended for you to track the account on your DataBase.

## Step_2:

Verify that the Virtual Account has been created - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Account#operation/getAccountByAccountId).  
The status at this point should be “`frozen`” with “`availableBalance`” at zero (0).

```json cURL
curl --location 'https://api.tatum.io/v3/ledger/account/646dfe380b4f44ca693f12b1' \
--header 'x-api-key: {testnet_API_KEY}'
//response:
{
    "balance": {
        "accountBalance": "50000",
        "availableBalance": "0"
    },
    "active": true,
    "frozen": true,
    "currency": "TTOKEN",
    "xpub": null,
    "customerId": "63889d0395bfe9fd220ffdf0",
    "accountingCurrency": "USD",
    "id": "646dfe380b4f44ca693f12b1"
}
```

## Step_3:

Register the Token via the "`symbol`" and the "`tokenAddress`" in your Virtual Account ledger - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-operations#operation/storeTokenAddress):

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/offchain/token/TTOKEN/0xCf15c60f66e49d3C41a98717eb0f40AcD764DD57' \
--header 'x-api-key: {testnet_API_KEY}'
//response:
//204 No content
```

## Step_4:

Verify that the Virtual Account has been "unfrozen" - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Account/#operation/getAccountByAccountId):

```json cURL
curl --location 'https://api.tatum.io/v3/ledger/account/646dfe380b4f44ca693f12b1' \
--header 'x-api-key: {testnet_API_KEY}'
//response:
{
    "balance": {
        "accountBalance": "50000",
        "availableBalance": "50000" //This confirms the Virtual Account has been "unfrozen"
    },
    "active": true,
    "frozen": false, //This confirms the Virtual Account has been "unfrozen"
    "currency": "TTOKEN",
    "xpub": null,
    "customerId": "63889d0395bfe9fd220ffdf0",
    "accountingCurrency": "USD",
    "id": "646dfe380b4f44ca693f12b1"
}
```

## Step_5 (optional)

You may create any number of additional Virtual Accounts with the token you added - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Account/#operation/createAccount):

```json cURL

curl --location 'https://api.tatum.io/v3/ledger/account' \
--header 'x-api-key: {testnet_API_KEY}' \
--header 'Content-Type: application/json' \
--data '{
    "currency": "TTOKEN",
    "xpub": "xpub6EMcUVjBn8qrftjMxinPS34ebPPHATDPkYvmxhex9H8rmwE4dTaiW94c3rZzBbk55WFoSspYCyQRSkMmGzDjDdyJNUpqtwq1ZGCDC7dgtjC",
    "customer":{
        "externalId": "EX_CUST_2"
    }
}'
//response:
{
    "currency": "TTOKEN",
    "active": true,
    "balance": {
        "accountBalance": "0",
        "availableBalance": "0"
    },
    "frozen": false,
    "xpub": "xpub6EMcUVjBn8qrftjMxinPS34ebPPHATDPkYvmxhex9H8rmwE4dTaiW94c3rZzBbk55WFoSspYCyQRSkMmGzDjDdyJNUpqtwq1ZGCDC7dgtjC",
    "customerId": "638f4cfad2e6f3168bb11a40",
    "accountingCurrency": "EUR",
    "id": "646e040b0b4f44ca693f198e"
}


```

**Payload details:**

- "`currency`": Now we can use the symbol token we have added by following the previous steps.
- "`xpub`" comes from a new and unused mnemonic generated to use with Virtual Accounts.

## Step_6 (optional)

Following the creation of an additional Virtual Account in Step_5, we will generate a deposit address - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-addresses/#operation/generateDepositAddress): 

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/offchain/account/646e040b0b4f44ca693f198e/address' \
--header 'x-api-key: {testnet_API_KEY}'
//response:
{
    "xpub": "xpub6EMcUVjBn8qrftjMxinPS34ebPPHATDPkYvmxhex9H8rmwE4dTaiW94c3rZzBbk55WFoSspYCyQRSkMmGzDjDdyJNUpqtwq1ZGCDC7dgtjC",
    "derivationKey": 1,
    "address": "0xe29744c6de04d062e5785b2f35dc11e57610ab34",
    "currency": "TTOKEN"
}
```
