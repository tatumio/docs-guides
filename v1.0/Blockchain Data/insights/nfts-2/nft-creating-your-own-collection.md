---
title: "Creating a NFT Collection"
slug: "nft-creating-your-own-collection"
excerpt: ""
category: 65c0c716d716fe0040919d8b
hidden: true
createdAt: "Sat Feb 17 2024 13:34:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 13:22:32 GMT+0000 (Coordinated Universal Time)"
---
To mint an NFT, first you need a Collection to which said NFT must belong. To create your own NFT Collection, you have to deploy your own SmartContract. Tatum makes these steps easy.

## Creating an NFT Collection

1. Select the network you want the NFTs to exist.
2. Have ready an address with its `privatekey` with native assets. Required to pay for the SmartContract deployment.
3. Pick on a "`name`" and "`symbol`" for your collection.
4. Deploy the NFT SmartContract to get your Collection.
5. (Optional) Add a Tatum minter address
   1. If a Minter address is added to the Collection SmartContract, Tatum pays on your behalf. _Your account will be charged accordingly._

### Example request to create a new NFT Collection (CELO Testnet)

**Step_1:** Deploy the NFT SmartContract to create a collection

- v3 REST API endpoint - [Deploy an NFT Smart Contract](https://apidoc.tatum.io/tag/NFT-(ERC-721-or-compatible)#operation/NftDeployErc721)

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/nft/deploy' \
--header 'x-api-key: {API_KEY}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chain": "CELO",
    "name": "NFT on Celo Test Collection",
    "symbol": "NCTC",
    "fromPrivateKey": "####",
    "feeCurrency": "CELO"
}'

//Response
{
    "txId": "0xa3ed3b9d2686dad28e93bbad6df37fc38430ecd8c0b49aceef787d33a9a6edcd"
}
```

> 📘 Find the transaction in [Celo Alfajores Explorer](https://explorer.celo.org/alfajores/tx/0xa3ed3b9d2686dad28e93bbad6df37fc38430ecd8c0b49aceef787d33a9a6edcd).

**Step_2:** Retrieve the "SmartContract - address"

- v3 REST API endpoint - [Get the SC from a transaction hash](https://apidoc.tatum.io/tag/Blockchain-utils#operation/SCGetContractAddress)

```json cURL
curl --location --request GET 'https://api.tatum.io/v3/blockchain/sc/address/CELO/0xa6e0f4f1571dd5f50af126f173f0ff62ee8dd9d9aa7d708843c4b8058d347be5' \
--header 'x-api-key: {API_KEY}'
//Response
{
    "contractAddress": "0x0935a78C8a268c8ED0590E5A8d4409f7604Bed1A"
}
```

**Step_3:** (optional) Adding Tatum as a Minter

- v3 REST API endpoint - [Add an address as Minter](https://apidoc.tatum.io/tag/NFT-(ERC-721-or-compatible)#operation/NftAddMinter)

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/nft/mint/add' \
--header 'x-api-key: {API_KEY}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "chain": "CELO",
    "contractAddress": "0x0935a78C8a268c8ED0590E5A8d4409f7604Bed1A",
    "minter": "0xBC2eBA680EE50d685cc4Fe65f102AA70AfB27D3F",
    "fromPrivateKey": "#####"
}'
//Response
{
    "txId": "0x04e159bd515c917efcfbb88f819b513fb7c5d54aef70c26aaa285e7b987c1aae"
}
```

### Tatum Minter role addresses

| Environment | Chain                                         | Address                                        |
| :---------- | :-------------------------------------------- | :--------------------------------------------- |
| **Mainnet** | BSC, Celo, Ethereum, Harmony, Klaytn, Polygon | **0x49678AAB11E001eb3cB2cBD9aA96b36DC2461A94** |
| Testnet     | BSC                                           | 0xc16ae5e8c985b906935a0cadf4e24f0400531883     |
| Testnet     | Celo                                          | 0xBC2eBA680EE50d685cc4Fe65f102AA70AfB27D3F     |
| Testnet     | Ethereum                                      | 0x53e8577C4347C365E4e0DA5B57A589cB6f2AB848     |
| Testnet     | Harmony                                       | 0x8906f62d40293ddca77fdf6714c3f63265deddf0     |
| Testnet     | Polygon                                       | 0x542b9ac4945a3836fd12ad98acbc76a0c8b743f5     |

> 📘 Adding a Minter Address into an NFT Collection SmartContract is non-reversible. The cost of each use in crypto is charged to the account in credits.
