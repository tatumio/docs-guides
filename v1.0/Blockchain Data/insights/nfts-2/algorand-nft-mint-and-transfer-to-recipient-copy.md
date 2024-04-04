---
title: "Solana - NFT Mint and Transfer to Recipient"
slug: "algorand-nft-mint-and-transfer-to-recipient-copy"
excerpt: ""
category: 65c0c716d716fe0040919d8b
hidden: true
createdAt: "Sun Feb 25 2024 12:03:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 13:22:32 GMT+0000 (Coordinated Universal Time)"
---
NFTs over Solana work a bit differently than other EVM (like Ethereum) chains.

With most EVM chains, you need to deploy a smart contract from which you will mint NFTs. However, Solana uses the [Metaplex Protocol](https://www.metaplex.com/) — a smart contract and metadata standard for creating and working with NFTs. Tatum’s API endpoints leverage the Metaplex protocol, and as a result, you do not need to deploy your own smart contract to mint NFTs.

Usually, the JSON metadata scheme that points to the metadata included in your NFT must be stored on IPFS. However, on Solana, this metadata is stored on the blockchain itself, so you do not need to create a JSON metadata scheme and upload it to IPFS. All you need to do is include a URL that points to the metadata in the uri field of the Mint NFT API call below.

## NFT Mint Example - Solana

[v3 REST API endpoint](https://apidoc.tatum.io/tag/NFT-(ERC-721-or-compatible)#operation/NftMintErc721) where available Request Body Schema:

- MintNftExpressSolana
- MintNftSolana
- MintNftSolana

Most of the parameters are the same as other EVM chains. However, the royalty information in the metadata section has a couple of key differences:

- The total percentage royalty of each transaction to be paid out to the creators is entered in the `sellerFeeBasisPoints` field of the Mint NFT endpoint. For example, if the `sellerFeeBasisPoints` value is “1000”, this means 10% of the purchase price of the NFT will be transferred to creators each time it is sold. To disable the royalty for the NFT completely, set `sellerFeeBasisPoints` to 0.
- The `share` field contains the different percentages of the total `sellerFeeBasisPoints` to be divided among the creators. If there are 2 creators, one with a `share` value of “30” and one with a share value of “70”, 30% and 70% of the total `sellerFeeBasisPoints` royalty will be paid to each respective creator.

### Request Example:

```json cURL
curl --location --request POST 'https://api.tatum.io/v3/nft/mint/' \
--header 'x-api-key: {API_KEY}' \
--header 'Content-Type: application/json' \
--data-raw '{
   "from": "FykfMwA9WNShzPJbbb9DNXsfgDgS3XZzWiFgrVXfWoPJ",
   "chain": "SOL",
   "fromPrivateKey": "####",
   "to": "FykfMwA9WNShzPJbbb9DNXsfgDgS3XZzWiFgrVXfWoPJ",
   "metadata": {
       "name": "Tatum API",
       "symbol": "TAPI",
       "sellerFeeBasisPoints": 10,
       "uri": "ipfs://bafybeidi7xixphrxar6humruz4mn6ul7nzmres7j4triakpfabiezll4ti",
       "creators": [
           {
               "address": "FykfMwA9WNShzPJbbb9DNXsfgDgS3XZzWiFgrVXfWoPJ",
               "verified": true,
               "share": 100
           }
       ]
   }
}'
```

**Parameters:**

| Name                 | Description                                                                                                                                                                                               |
| :------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| from                 | The address of the creator of the NFT from which the gas fees will be paid                                                                                                                                |
| chain                | The blockchain on which the NFT is being minted (in this case, “SOL”)                                                                                                                                     |
| fromPrivateKey       | The private key of the address from which the NFT is being minted                                                                                                                                         |
| to                   | The recipient address to which the NFT will be minted                                                                                                                                                     |
| metadata             | The data included in the NFT, including the royalty payment information to each co-creator                                                                                                                |
| name                 | The name of the NFT                                                                                                                                                                                       |
| symbol               | The symbol of the NFT                                                                                                                                                                                     |
| sellerFeeBasisPoints | The total percentage of the sale price to be paid out to co-creators based on their individual share (see below)                                                                                          |
| uri                  | The location of the metadata (image, video file, audio file, etc.). Usually, metadata json schemes are stored on IPFS. However, on Solana, the metadata scheme is stored on the Solana blockchain itself. |
| creators             | Information about each co-creator who will receive a percentage royalty share each time the NFT is sold address - the account address of the creator                                                      |
| verified             | whether or not the account has been verified                                                                                                                                                              |
| share                | the percentage share of the total `sellerFeeBasisPoints` percentage designated above to be paid out to each individual creator                                                                            |

### Response Example:

```json cURL
{
    "txId": "5GAwhRcMR7h5Dx71KCQax4CAcCFA6FcrVE5fwNedq7wXDYS1qpZaGd4Bj2zh8dCUfAz7fqVSXhdZzXRigsNoTZsb",
    "nftAddress": "7dQWANaodDyttJNz3seaXoAe6VA8cLpPV1bM4cPGuNhG",
    "nftAccountAddress": "3z2bPwKzfTAFDKPNKTM4vvffBSDvcBvkuRJeME5iALs3"
}
```

**Parameters:**

| Name              | Description                                                                                                                                                                                                                                                                                                                                                                                                                        |
| :---------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| txId              | The transaction ID. This ID can be used to get information about the transaction using the Get transaction endpoint or within the Solana Explorer.                                                                                                                                                                                                                                                                                 |
| nftAddress        | The address of the NFT on the blockchain. This is the address that is used to transfer the NFT below in the contractAddress field of the Transfer NFT API endpoint.                                                                                                                                                                                                                                                                |
| nftAccountAddress | The address of the account that owns the NFT. This address is owned by the recipient address, and a new `nftAccountAddress` is created each time a new NFT is minted. The private key of the `nftAccountAddress` is the same as the private key of the account address it is owned by. Each time an NFT is transferred on Solana, a new `nftAccountAddress` is created to receive the token under the recipient’s account address. |

## NFT Transfer Example - Solana

The way the Solana blockchain works with minting and transferring NFTs uses `nftAccountAddresses`. For practical use of Tatum’s API, this makes very little difference, but it is important to know that for transferring NFTs, the `nftAddress` of the NFT is used, NOT the `nftAccountAddress`.

### Request Example:

```json cURL
curl --request POST \
  --url https://api.tatum.io/v3/nft/transaction \
  --header 'content-type: application/json' \
  --header 'x-api-key: {API_KEY}' \
  --data '{
      "chain": "SOL",
      "from": "FykfMwA9WNShzPJbbb9DNXsfgDgS3XZzWiFgrVXfWoPJ",
      "to": "FykfMwA9WNShzPJbbb9DNXsfgDgS3XZzWiFgrVXfWoPJ",
      "contractAddress": "7dQWANaodDyttJNz3seaXoAe6VA8cLpPV1bM4cPGuNhG",
      "fromPrivateKey": "####"
}'
```

**Parameters:**

| Name            | Description                                                                                               |
| :-------------- | :-------------------------------------------------------------------------------------------------------- |
| chain           | The chain on which you are transferring the NFT (in this case, “SOL”) from - the sender’s account address |
| to              | The recipient’s account address                                                                           |
| ContractAddress | The address of the NFT from the nftAddress field in the response to the Mint NFT call above.              |
| fromPrivateKey  | The private key of the sender’s address                                                                   |

### Response Example:

```json cURL
{
    "txId": "c83f8818db43d9ba4accfe454aa44fc33123d47a4f89d47b314d6748eb0e9bc9"
}
```
