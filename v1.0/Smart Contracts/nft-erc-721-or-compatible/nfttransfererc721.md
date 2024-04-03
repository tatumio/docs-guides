---
title: "Transfer an NFT"
slug: "nfttransfererc721"
excerpt: "<p><b>100 credits per API call on Flow<br/>\n2 credits per API call on the other blockchains</b></p>\n<p>Transfer an NFT from the smart contract (the <code>contractAddress</code> parameter in the request body) to the specified blockchain address (the <code>to</code> parameter in the request body).</p>\n<p>In one API call, you can transfer only one NFT.</p>\n<p>This API is supported for the following blockchains:</p>\n<ul>\n<li>Algorand</li>\n<li>BNB Smart Chain</li>\n<li>Celo</li>\n<li>Ethereum</li>\n<li>Flow</li>\n<li>Harmony</li>\n<li>Klaytn</li>\n<li>KuCoin Community Chain</li>\n<li>Polygon</li>\n<li>Solana</li>\n<li>TRON</li>\n<li>Tezos</li>\n<li>Horizen Eon</li>\n</ul>\n<p>For Ethereum, Celo, and BNB Smart Chain, transferring NFTs invokes the <code>safeTransfer()</code> method.</p>\n<p><b>Transferring NFTs on Algorand</b></p>\n<ul>\n<li>On Algorand, the recipient has to agree in advance to receive your NFT because Algorand charges users for storing NFTs on their addresses, and an Algorand blockchain address by default does not receive NFTs unless explicitly agreed. Before transferring an NFT, make sure that the recipient <a href=\"https://apidoc.tatum.io/tag/Algorand#operation/AlgorandBlockchainReceiveAsset\" target=\"_blank\">has agreed to receive the NFT</a> to their address.</li>\n<li>If you want to transfer an NFT that <a href=\"#operation/NftMintErc721\">was minted using NFT Express</a>, use the <code>transferNftAlgoExpress</code> schema of the request body.<br /><b>NOTE:</b> On the <b>mainnet</b>, Tatum covers your transaction fees for the NFT transfer and pays for them from its own blockchain address. Then, the fee amount paid by Tatum is converted to the number of credits, and these credits are deducted from the monthly credit allowance of your paid pricing plan. On the <b>testnet</b>, only one credit is deducted from the monthly credit allowance for transaction fee.</li>\n</ul>\n<p><b>Transferring NFTs on Solana</b><br/>\nIf you want to transfer an NFT that <a href=\"#operation/NftMintErc721\">was minted using NFT Express</a>, use the <code>transferNftSolana</code> or <code>transferNftSolanaKMS</code> schema of the request body. In the request body:\n<ul>\n<li>Set the <code>from</code> parameter to the address that you used in the <code>to</code> parameter in the request body of the minting call.</li>\n<li>Set the <code>to</code> parameter to the recipient's address.</li>\n<li>Set the <code>contractAddress</code> parameter to the address from the <code>nftAddress</code> parameter returned in the response body of the minting call.</li>\n<li>Set the <code>fromPrivateKey</code>/<code>signatureId</code> parameter to the private key/signature ID of the blockchain address that you specified in the <code>from</code> parameter.</li>\n</ul>\n<p><b>Signing a transaction</b><br/>\nWhen transferring an NFT, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>\n<p><b>NOTE:</b> This does not apply to transferring NFTs that were minted on Algorand using NFT Express (see earlier in this section).</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:36:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:36:29 GMT+0000 (Coordinated Universal Time)"
---