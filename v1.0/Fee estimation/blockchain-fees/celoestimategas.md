---
title: "Estimate the fee for a Celo transaction"
slug: "celoestimategas"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Get an estimated gas price and the number of gas units needed for a Celo transaction. The gas price is obtained from <a href=\"https://explorer.bitquery.io/celo_rc1/gas\" target=\"_blank\">https://explorer.bitquery.io/celo_rc1/gas</a>.</p>\n<p style=\"border:4px solid DeepSkyBlue;\"><b>NOTE:</b> The estimated gas price is returned in <b>wei</b>. However, when <a href=\"https://apidoc.tatum.io/tag/Celo#operation/CeloBlockchainTransfer\" target=\"_blank\">making the transaction itself</a> and providing the custom fee, you have to provide the gas price in <b>Gwei</b>. Make sure to convert the estimated gas price from wei to Gwei before submitting your transaction.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:35:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:35:38 GMT+0000 (Coordinated Universal Time)"
---