---
title: "Estimate the fee for multiple Ethereum transactions"
slug: "ethestimategasbatch"
excerpt: "<p><b>10 credits per API call + 10 credits per each gas estimation</b></p>\n<p>Get an estimated gas price and the number of gas units needed for multiple Ethereum transactions. The gas price is obtained from multiple sources and calculated based on the latest N blocks and the current mempool state.</p>\n<p>The estimations are returned in the same order as the transactions were submitted in the request.</p>\n<p>The <code>fast</code> gas price is used by default.</p>\n<p style=\"border:4px solid DeepSkyBlue;\"><b>NOTE:</b> The estimated gas price is returned in <b>wei</b>. However, when <a href=\"https://apidoc.tatum.io/tag/Ethereum#operation/EthBlockchainTransfer\" target=\"_blank\">making a transaction itself</a> and providing the custom fee, you have to provide the gas price in <b>Gwei</b>. Make sure to convert the estimated gas price from wei to Gwei before submitting your transaction.</p>\n</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:35:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:35:38 GMT+0000 (Coordinated Universal Time)"
---
