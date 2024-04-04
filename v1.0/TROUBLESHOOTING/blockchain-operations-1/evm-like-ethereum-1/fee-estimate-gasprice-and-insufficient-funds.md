---
title: "Fee Estimate, GasPrice and Insufficient funds Error"
slug: "fee-estimate-gasprice-and-insufficient-funds"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 25 2024 11:04:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 11:05:14 GMT+0000 (Coordinated Universal Time)"
---
When building a transaction over EVM chains (like Ethereum), a common pitfall in using manual fees is adding `gasPrice` in `Wei` instead of `Gwei`. When this happens, you will likely get an error looking as follows:

```json
ERROR: {
  statusCode: 403,
  errorCode: 'eth.tx.preparation',
  message: 'Transaction preparation failure.',
  cause: 'Insufficient funds send transaction from account ####### -> available balance is 1800000000000000, required balance is 7.233615778886385e+23'
}

```

## Fee Estimate

Tatum Fee estimates endpoints return values in `Wei`.

- Estimate the fee for an Ethereum transaction - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-fees#operation/EthEstimateGas)
- Estimate the fee for multiple Ethereum transactions - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Blockchain-fees#operation/EthEstimateGasBatch)

### Example ETH Fee Estimate:

```json cURL
curl --location 'https://api.tatum.io/v3/ethereum/gas' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "from": "0xBF5c7e33a316cf7D86eBF4014bCf798c6962####",
    "to": "0xce864aaec47f07ee8ba7e60a37ff141298f7####",
    "amount": "0.018"
}'
//response:
{
    "gasLimit": "21000",
    "gasPrice": "43698096524", //The unit hereis in Wei!
    "estimations": {
        "safe": "43698096524",
        "standard": "43698096524",
        "fast": "43698096524",
        "baseFee": "43914769922"
    }
}
```

## Sending Ethereum with manual fees

When building an Ethereum transaction, if you want to input the transaction fee manually, make sure the `gasPrice` is in `Gwei`. 

> 📘 1 Gwei (Giga-wei) is equal to 1,000,000,000 Wei. Therefore, to convert Wei to Gwei, you have to divide the amount in Wei by 1,000,000,000. Alternatively, you may use an online conversion such as [eth-converter.com](https://eth-converter.com/)

### Example ETH transaction with Manual Fees:

```json cURL
curl --location 'https://api.tatum.io/v3/ethereum/transaction' \
--header 'Content-Type: application/json' \
--header 'x-api-key: ##Mainnet_API_KEY' \
--data '{
    "to": "0xd2c4b6434410e4af062ee3c280327c8ece11####",
    "currency": "ETH",
    "amount": "0.0017",
    "fromPrivateKey": "****",
    "fee": {
        "gasLimit": "21000",
        "gasPrice": "44" //unit in Gwei! -> Estimate returned "fast": "43698096524",
    }
}'
```
