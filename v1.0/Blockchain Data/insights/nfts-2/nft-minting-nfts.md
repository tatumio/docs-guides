---
title: "Minting NFTs"
slug: "nft-minting-nfts"
excerpt: ""
category: 65c0c716d716fe0040919d8b
hidden: true
createdAt: "Sat Feb 17 2024 14:17:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 13:22:32 GMT+0000 (Coordinated Universal Time)"
---
To mint an NFT, first you need a Collection to which said NFT must belong. Once you have the Collection SmartContract, minting NFTs just takes a few steps.

## Minting an NFT

1. Select the network you want the NFTs to exist.
2. Have ready a Collection (SmartContract) for your NFT to belong.
3. Have ready an address with its `privatekey` with native assets. Required to pay for the minting.
   1. If a Minter address was added to the Collection SmartContract, Tatum pays on your behalf. _Your account will be charged accordingly._
4. Get ready the metadata JSON file.
5. Mint the NFT.

### Example request to mint an NFT (CELO Testnet)

**Step_1:** Upload the Image and the Metadata JSON file 

- v3 REST API endpoint - [Store data to IPFS](https://apidoc.tatum.io/tag/IPFS#operation/StoreIPFS)

```json cURL
//First upload the NFT image
curl --location --request POST 'https://api.tatum.io/v3/ipfs' \
--header 'x-api-key: {API_KEY}' \
--form 'file=@"/Users/{username}/Documents/tatum_nft_example.jpeg"'
//Response
{
    "ipfsHash": "bafkreif6ifegpj74w6biowzzbswqwvg6c5t6hhtwsrmpxhweg6yn7zxm7e"
}

//After that, create a JSON file and upload this new file
//File format:
//  {
//    "name": "Tatum NFT for Diagram example",
//    "description": "This is an NFT minted as an example.",
//    "image": "ipfs://bafkreif6ifegpj74w6biowzzbswqwvg6c5t6hhtwsrmpxhweg6yn7zxm7e"
//  }

curl --location --request POST 'https://api.tatum.io/v3/ipfs' \
--header 'x-api-key: {API_KEY}' \
--form 'file=@"/Users/{username}/Documents/Tatum_NFT_example.json"'
//Response
{
    "ipfsHash": "bafkreiebg3ugqtumak2ueyf2j2sbggt47hxjvbozkxbgyssebufmbgp3fa"
}
```

**Step_2:** Mint the NFT

- v3 REST API endpoint - [Mint an NFT](https://apidoc.tatum.io/tag/NFT-(ERC-721-or-compatible)#operation/NftMintErc721)

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/nft/mint/' \
--header 'x-api-key: {API_KEY}' \
--header 'Content-Type: application/json' \
--data-raw '{
"chain": "CELO",
"tokenId": "001",
"to": "0x40245fa66666508e4121f4400819eef4b08ac4bf",
"url": "ipfs://bafkreiebg3ugqtumak2ueyf2j2sbggt47hxjvbozkxbgyssebufmbgp3fa",
"contractAddress": "0x0935a78C8a268c8ED0590E5A8d4409f7604Bed1A",
"minter": "0xBC2eBA680EE50d685cc4Fe65f102AA70AfB27D3F", // If there's no "minter", PrivateKey must be used instead.
"feeCurrency": "CELO"
}'
//Resonse
{
    "txId": "0xd16536eea02ddffd2deee2db5e2c053ee429526758420477781082c7a5465aa7"
}
```

### Parameters

| Name            | Description                                                                                 |
| :-------------- | :------------------------------------------------------------------------------------------ |
| chain           | The network on which the NFT will be minted.                                                |
| contractAddress | The address of your NFT Collection/SmartContract.                                           |
| minter          | The address of the Tatum NFT minter that you have added as a minter to your smart contract. |
| to              | The blockchain address of the recipient to whom the NFT will be sent.                       |
| tokenId         | The identifier of the NTF that will be minted.                                              |
| url             | The URL of the metadata (image, audio, video, etc) to be included in the NFT.               |

> 📘 Find the transaction in [Celo Alfajores Explorer](https://explorer.celo.org/alfajores/tx/0xd16536eea02ddffd2deee2db5e2c053ee429526758420477781082c7a5465aa7).

### Tatum Minter role addresses

| Environment | Chain                                         | Address                                        |
| :---------- | :-------------------------------------------- | :--------------------------------------------- |
| **Mainnet** | BSC, Celo, Ethereum, Harmony, Klaytn, Polygon | **0x49678AAB11E001eb3cB2cBD9aA96b36DC2461A94** |
| Testnet     | BSC                                           | 0xc16ae5e8c985b906935a0cadf4e24f0400531883     |
| Testnet     | Celo                                          | 0xBC2eBA680EE50d685cc4Fe65f102AA70AfB27D3F     |
| Testnet     | Ethereum                                      | 0x53e8577C4347C365E4e0DA5B57A589cB6f2AB848     |
| Testnet     | Harmony                                       | 0x8906f62d40293ddca77fdf6714c3f63265deddf0     |
| Testnet     | Polygon                                       | 0x542b9ac4945a3836fd12ad98acbc76a0c8b743f5     |
