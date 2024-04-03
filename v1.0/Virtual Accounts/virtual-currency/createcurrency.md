---
title: "Create new virtual currency"
slug: "createcurrency"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Create new virtual currency with given supply stored in account. This will create Tatum internal virtual currency. Every virtual currency must be prefixed with <b>VC_</b>.</p>\n<p>Every virtual currency must be pegged to existing FIAT or supported cryptocurrency. 1 unit of virtual currency has then the same amount as 1 unit of the base currency it is pegged to. It is possible to set a custom base rate for the virtual currency. (baseRate = 2 => 1 VC unit = 2 basePair units)</p>\n<p>Tatum virtual currency acts as any other asset within Tatum. To create a fungible token, see the <a href=\"https://apidoc.tatum.io/tag/Fungible-Tokens-(ERC-20-or-compatible)#operation/Erc20Deploy\" target=\"_blank\">API for deploying a fungible token smart contract</a>.</p>\n<p>This operation returns the newly created Tatum Ledger account with an initial balance set to the virtual currency's total supply. Total supply can be changed in the future.</p>\n<p>Digital assets:</p>\n<ul>\n<li><b>USDC_MATIC</b> refers to contract <code>0x2791bca1f2de4661ed88a30c99a7a9449aa84174</code> on Polygon mainnet.</li>\n<li><b>USDC_MATIC_NATIVE</b> refers to contract <code>0x3c499c542cef5e3811e1192ce70d8cc03d5c3359</code> on Polygon mainnet.</li>\n</ul>"
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:13 GMT+0000 (Coordinated Universal Time)"
---
