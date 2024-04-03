---
title: "Algorand - NFT Mint and Transfer to Recipient"
slug: "algorand-nft-mint-and-transfer-to-recipient"
excerpt: ""
hidden: true
createdAt: "Sun Feb 25 2024 10:40:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 13:22:32 GMT+0000 (Coordinated Universal Time)"
---
NFTs over Algorand work a bit differently than other EVM (like Ethereum) chains.

Algorand charges users for storing NFTs on their addresses and an Algorand blockchain address by default does not receive NFTs unless the owner of the address explicitly agrees to receive an NFT.

### NFT Mint Example - Algorand

[v3 REST API endpoint](https://apidoc.tatum.io/tag/NFT-(ERC-721-or-compatible)#operation/NftMintErc721) where available Request Body Schema:

- MintNftExpressAlgorand
- MintNftAlgorand
- MintNftAlgorandKMS

In the following example, the `privatekey` and `contractaddress` are default set to Tatum’s pre-deployed smart contract with Tatum's private key. The gas fees are deducted as credits from the monthly credit allowance from the paid Tatum plan.

```json cURL
curl -i -X POST \
  https://api.tatum.io/v3/nft/mint \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {API_KEY}' \
  -d '{
    "chain": "ALGO",
    "url": "https://my_token_data.com",
    "name": "My Crazy NFT",
    "attr": {
      "assetUnit": "USDT",
      "clawback": "TMETT6BXL3QUH7AH5TS6IONU7LVTLKIGG54CFCNPMQXWGRIZFIESZBYWP4",
      "manager": "TMETT6BXL3QUH7AH5TS6IONU7LVTLKIGG54CFCNPMQXWGRIZFIESZBYWP4",
      "reserve": "TMETT6BXL3QUH7AH5TS6IONU7LVTLKIGG54CFCNPMQXWGRIZFIESZBYWP4",
      "freeze": "TMETT6BXL3QUH7AH5TS6IONU7LVTLKIGG54CFCNPMQXWGRIZFIESZBYWP4"
    }
  }'
```

### Parameters

| Name      | Description                                                                                                             |
| :-------- | :---------------------------------------------------------------------------------------------------------------------- |
| chain     | ALGO for Algorand in this specific case.                                                                                |
| url       | Metadata of the minted NFT. For details, see [the Ethereum site](https://eips.ethereum.org/EIPS/eip-721#specification). |
| name      | The name of the minted NFT.                                                                                             |
| attr      | Attributes                                                                                                              |
| assetUnit | The name of the minted NFT unit.                                                                                        |
| clawback  | The address of the clawback account.                                                                                    |
| manager   | The address of the reserve account.                                                                                     |
| freeze    | The address of the freeze account.                                                                                      |

## NFT Transfer Example - Algorand

An NFT that you mint on Algorand is automatically transferred to your blockchain address. After the NFT is minted, you have to transfer it to the recipient's address. 

The recipient has to agree in advance to receive your NFT (by default, Algorand charges users for storing NFTs on their addresses which, by default, does not receive NFTs unless agreed).

### Step_1 - The recipient agrees with the NFT reception

The recipient [agrees to receive the NFT](https://apidoc.tatum.io/tag/Algorand/#operation/AlgorandBlockchainReceiveAsset). **Recipient** enables accepting assets on an Algorand address using the mintNftExpressAlgorand schema:

**Request Example**:

```json cURL
curl -i -X POST \
  https://api.tatum.io/v3/algorand/asset/receive \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {API_KEY}' \
  -d '{
    "assetId": "116363571", //The NFT the recipient must agree to recieve.
    "fromPrivateKey": "####"
  }'
```

### Step_2 - The sender sends the NFT to the recipient

 You [transfer the NFT](https://preview.redoc.ly/tatum/develop/tag/NFT-(ERC-721-or-compatible)/#operation/NftTransferErc721) to the recipient's address using the `transferNftAlgoExpress` schema:

**Request Example:**

```json cURL
curl -i -X POST \
  https://api.tatum.io/v3/nft/transaction \
  -H 'Content-Type: application/json' \
  -H 'x-api-key: {API_KEY}' \
  -d '{
    "chain": "ALGO",
    "to": "TMETT6BXL3QUH7AH5TS6IONU7LVTLKIGG54CFCNPMQXWGRIZFIESZBYWP4",
    "contractAddress": "100000"
  }'
```
