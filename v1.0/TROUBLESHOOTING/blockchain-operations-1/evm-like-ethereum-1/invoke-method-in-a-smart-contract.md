---
title: "Invoke method in a Smart Contract"
slug: "invoke-method-in-a-smart-contract"
excerpt: ""
hidden: false
createdAt: "Sun Feb 11 2024 20:44:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 20:44:37 GMT+0000 (Coordinated Universal Time)"
---
You can [invoke a method in a Smart Contract (SC)](https://apidoc.tatum.io/tag/Ethereum/#operation/EthBlockchainSmartContractInvocation) to read or write. This is done through the ABI (Application Binary Interface) method.

- **Read**: could be used to read the balance of a specific token on that smart contract.
- **Write**: could be used to do something like burning some of the total minted tokens when the contract was originally deployed.

## Disclaimer

Tatum ensures the endpoint "Invoke a method in an SC" works against the blockchain.

> 🚧 Troubleshooting issues in successfully invoking a method in an SC is out of the scope of Tatum's staff. Users may check the related SC code, and ABI documentation and reach out to the SC creator.

## How to invoke a Smart Contract

Example with a minted smart contract for ERC20 on BSC.

1. Deploy Smart Contract
   ```json cURL
   curl --location --request POST 'https://api.tatum.dev/v3/blockchain/token/deploy' \
   --header 'X-Api-Key: {API_KEY}' \
   --header 'Content-Type: application/json' \
   --data-raw '{
       "chain": "BSC",
       "symbol": "invoke_Token",
       "name": "invToken",
       "totalCap": "10000000",
       "supply": "10000000",
       "digits": 18,
       "address": "0x6b598e8be2629380c7dc0a95ca5b59923a136436",
       "fromPrivateKey": "0x200cc2960b8b75e1fe4cf461e6e02d1b9da869c7d46995709671232b228e6346"
   }'
   //Response
   {
       "txId": "0x86fe1d7f65c7c80a67ad85aeb5ec92df4b5cbabae82955da1bf3eb1fae1eb2cb"
   }
   ```
2. Get the SC address from the explorer. Example: [`0x3fc5facec56e5b40df4a8abcebf7873259e340b6`]
3. Click on the [Contract] tab:

   [block:image]{"images":[{"image":["https://files.readme.io/5ac2196-sc_code_1.png","",""],"align":"center"}]}[/block]

   [block:image]{"images":[{"image":["https://files.readme.io/cbf2ea6-sc_code_2.png","",""],"align":"center"}]}[/block]
4. On the "**Code Decompilation result**", grab the related info from decompiled code. If you know the type of SC, use its public ABI to figure out what the JSON body looks like for a specific method.
5. **READ** method example: `balanceOf` >> to get balance of that token.
   ```json cURL
   {
       "contractAddress": "0x3fc5facec56e5b40df4a8abcebf7873259e340b6",
       "methodName": "balanceOf",
       "methodABI": {
           "constant": true,
           "inputs": [
               {
                   "name": "owner",
                   "type": "address"
               }
           ],
           "name": "balanceOf",
           "outputs": [
               {
                   "name": "",
                   "type": "uint256"
               }
           ],
           "payable": false,
           "stateMutability": "view",
           "type": "function"
       },
       "params": [
           "{{address1}}"
       ]
   }
   //Response
   {
       "data": "10000000000000000000000000" >> which matches the original minted tokens
   }
   ```
6. **WRITE** method example: `burn` >> to decrease #original minted tokens
   ```json cURL
   {
       "contractAddress": "0x3fc5facec56e5b40df4a8abcebf7873259e340b6",
       "methodName": "burn",
       "methodABI": {
           "constant": false,
           "inputs": [
               {
                   "name": "to",
                   "type": "uint256"
               }
           ],
           "name": "burn",
           "outputs": [
               {
                   "name": "",
                   "type": "bool"
               }
           ],
           "payable": false,
           "stateMutability": "nonpayable",
           "type": "function"
       },
       "params": [
           10
       ],
       "fromPrivateKey": "{{pk1}}"
   }
   //Response
   {
       "txId": "0x1d77e9ed8a8ed84444f0b818f666c488eb6de77aef7329e324685cd2e84fd968"
   }
   ```

- Check in the Explorer to find burn transaction:

  [block:image]{"images":[{"image":["https://files.readme.io/cd23957-cs_invoke_burn.png","",""],"align":"center"}]}[/block]

## ERC-20 ABI Documentation

- [ERC-20 ABI](https://gist.github.com/veox/8800debbf56e24718f9f483e1e40c35c)
- [ERC-20 OpenZeppelin](https://docs.openzeppelin.com/contracts/2.x/api/token/erc20)

## About Smart Contract code format

Smart Contracts are applications inside the blockchain with an interaction interface, where ABI can be described with JSON.

For ERC-20 and using this interface, you can do some actions with it. Every entry of it shows the corresponding method available to call. The only difference compared to the usual method call in a programming language is that it has expanded definitions.

### Example:

```json cURL
{
        "constant": false,
        "inputs": [
            {
                "name": "_from",
                "type": "address"
            },
            {
                "name": "_to",
                "type": "address"
            },
            {
                "name": "_value",
                "type": "uint256"
            }
        ],
        "name": "transferFrom",
        "outputs": [
            {
                "name": "",
                "type": "bool"
            }
        ],
        "payable": false,
        "stateMutability": "nonpayable",
        "type": "function"
    },

//This is the same as this:
transferFrom(_from: address, _to: address, _value: uint256): bool
```

Other flags show if stateMutability is required (we may say tx on chain, for further reading - solidity state mutability), or if it is a constant of SC or more.
