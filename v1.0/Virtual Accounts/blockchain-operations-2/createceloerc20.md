---
title: "Register a new Celo ERC-20-equivalent token in the virtual account"
slug: "createceloerc20"
excerpt: "<p><b>This method is deprecated.<br/>Use <a href=\"#operation/registerErc20Token\">this method</a> instead.</b></p><br/>\n<h4>2 credits per API call.</h4>\n<p>First step to create new ERC-20 token with given supply on Celo blockchain with support of Tatum's private ledger.<br/>\n<br/>\n<br/>\nThis method only creates Tatum Private ledger virtual currency with predefined parameters. It will not generate any blockchain smart contract.<br/>\nThe whole supply of ERC-20 token is stored in the customer's newly created account. Then it is possible to create new Tatum accounts with ERC-20 token name as account's currency.<br/>\nNewly created account is frozen until the specific ERC-20 smart contract address is linked with the Tatum virtual currency, representing the token.<br/>\nOrder of the steps to create ERC-20 smart contract with Tatum private ledger support:\n<ol>\n<li><a href=\"#operation/registerErc20Token\">Register Celo ERC-20 token</a> - creates a virtual currency within Tatum</li>\n<li><a href=\"#operation/CeloDeployErc20\">Deploy Celo ERC-20 smart contract</a> - create new ERC-20 smart contract on the blockchain</li>\n<li><a href=\"#operation/storeTokenAddress\">Store Celo ERC-20 smart contract address</a> - link newly created ERC-20 smart contract address with Tatum virtual currency - this operation enables frozen account and enables ledger synchronization for ERC-20 Tatum accounts</li>\n</ol>\nThere is a helper method <a href=\"#operation/CeloDeployErc20Ledger\">Deploy Celo ERC-20 Smart Contract to Blockchain and Ledger</a>, which wraps first 2 steps into 1 method.<br/>\nAddress on the blockchain, where all initial supply will be transferred, can be defined via the address or xpub and derivationIndex. When xpub is present, the account connected to this virtualCurrency will be set as the account's xpub.\n</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:15 GMT+0000 (Coordinated Universal Time)"
---