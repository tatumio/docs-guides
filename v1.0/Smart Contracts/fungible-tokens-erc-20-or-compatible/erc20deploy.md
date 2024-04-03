---
title: "Deploy a fungible token smart contract"
slug: "erc20deploy"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Deploy a fungible token smart contract on the blockchain. In a deployed smart contract, you can mint and burn fungible tokens. The whole supply of fungible tokens (the <code>supply</code> parameter in the request body) will be transferred to the specified blockchain address (the <code>address</code> parameter in the request body).<br/>\nSmart contracts are standardized and audited.</p>\n<p>This API is supported for the following blockchains:</p>\n<ul>\n<li>Algorand</li>\n<li>BNB Smart Chain</li>\n<li>Celo</li>\n<li>Ethereum</li>\n<li>Harmony</li>\n<li>Klaytn</li>\n<li>KuCoin Community Chain</li>\n<li>Polygon</li>\n<li>Solana</li>\n<li>XinFin</li>\n</ul>\n<p>You can review the code of a deployed smart contract <a href=\"https://github.com/tatumio/tatum-middleware/blob/master/src/contracts/token.sol\" target=\"_blank\">here</a>.</p>\n<p><b>Signing a transaction</b><br/>\nWhen deploying a fungible token smart contract, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:36:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:36:29 GMT+0000 (Coordinated Universal Time)"
---