---
title: "Get balances of addresses"
slug: "getbalancesold"
excerpt: "<p><b>50 credits per API call</b></p>\n<p>Get balances of fungible tokens (ERC-20), NFTs (ERC-721 and ERC-1155) or multitokens (ERC-1155 only) for a specific wallet address on the following blockchains:</p>\n<ul>\n<li>Celo - celo / celo-testnet</li>\n<li>Ethereum - ethereum / ethereum-sepolia</li>\n<li>BNB (Binance) Smart Chain - bsc / bsc-testnet</li>\n<li>Polygon - polygon / polygon-mumbai</li>\n<li>Tezos - tezos-mainnet</li>\n<li>Horizen EON - eon-mainnet</li>\n<li>Chiliz - chiliz-mainnet</li>\n</ul>\n<p>To get started:</p>\n<ul>\n<li>Provide a chain name and comma-separated list of addresses. Our API will return balances of each token along with further information such as its type, id, and more.</li>\n<li>Aside from relevant information about each token and its balance, the response also contains metadata (they can, however, be excluded by setting <code>excludeMetadata</code> to <code>true</code>).</li>\n<li>If not specified, the API returns balances for all supported types of tokens (fungible tokens, nft, multitokens), but you can also choose to filter specific <code>tokenTypes</code>.</li>\n<li>For Tezos blockchain, the API returns balance of any tokens including native token (XTZ) for specified wallet addresses. Following query parameters won't have any effect on filtering data <code>excludeMetadata</code>.</li>\n</ul>"
category: 65e9ba6715ec3b004bc82075
hidden: false
createdAt: "Mon Feb 05 2024 13:24:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 13:24:50 GMT+0000 (Coordinated Universal Time)"
---
