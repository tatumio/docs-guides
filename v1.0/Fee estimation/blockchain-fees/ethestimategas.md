---
title: "Estimate the fee for an Ethereum transaction"
slug: "ethestimategas"
excerpt: "<p><b>10 credits per API call</b></p>\n<p>Get an estimated gas price and the number of gas units needed for an Ethereum transaction. The gas price is obtained from multiple sources and calculated based on the latest N blocks and the current mempool state.</p>\n<p>The <code>fast</code> gas price is used by default.</p>\n<p style=\"border:4px solid DeepSkyBlue;\"><b>NOTE:</b> The estimated gas price is returned in <b>wei</b>. However, when <a href=\"https://apidoc.tatum.io/tag/Ethereum#operation/EthBlockchainTransfer\" target=\"_blank\">making the transaction itself</a> and providing the custom fee, you have to provide the gas price in <b>Gwei</b>. Make sure to convert the estimated gas price from wei to Gwei before submitting your transaction.</p>"
category: 65c0c807b4d77e006316ec5c
hidden: false
createdAt: "Mon Feb 05 2024 11:35:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:35:38 GMT+0000 (Coordinated Universal Time)"
---
