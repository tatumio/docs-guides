---
title: "Bid for an asset at the NFT auction"
slug: "bidonauction"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Bid for an asset listed on the NFT auction.</p>\n<p>You can buy the asset either for the native blockchain assets (for example, ETH, BSC, and so on) or for the fungible tokens of the blockchain.</p>\n<ul>\n<li>If you want to pay for the asset with the <b>native assets</b>, send the required amount of the assets with the API call.</li>\n<li>If you want to pay with the <b>fungible tokens</b>, <a href=\"https://apidoc.tatum.io/tag/Fungible-Tokens-(ERC-20-or-compatible)#operation/Erc20Approve\" target=\"_blank\">allow the auction smart contract to access your tokens</a> before bidding for the asset. When you make the API call, the auction smart contract will deduct the required amount of the tokens from the smart contract where you hold the tokens.</li>\n</ul>\n<p>After you have purchased the asset, it is in a pending state until <a href=\"#operation/SettleAuction\" target=\"_blank\">the auction is settled</a>. Settling the auction means that the asset is transferred to the buyer, the amount is transferred to the seller, and the fee is transferred to the fee recipient of the auction.</p>\n<p>For the complete information about how the bidding/purchase process at an auction works, see the API for <a href=\"#operation/GenerateAuction\" target=\"_blank\">creating an NFT auction</a>.</p>\n<p>This API is supported for the following blockchains:</p>\n<ul>\n<li>BNB Smart Chain</li>\n<li>Celo</li>\n<li>Ethereum</li>\n<li>Harmony</li>\n<li>Klaytn</li>\n<li>Polygon</li>\n</ul>\n<p><b>The \"execution reverted\" message</b><br/>\nWhen making this API call, you may get the following message:<br/>\n<code>Although one or more Error Occurred [execution reverted] Contract Execution Completed</code><br/>\nThis message is a result of the auction version check and has no impact on completing the API call. You can safely ignore it.</p>\n<p><b>Signing a transaction</b><br/>\nWhen bidding for an asset at the NFT auction, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:36:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:36:28 GMT+0000 (Coordinated Universal Time)"
---