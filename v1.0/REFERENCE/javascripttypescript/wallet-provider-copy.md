---
title: "💻 Wallet Provider EVM"
slug: "wallet-provider-copy"
excerpt: ""
hidden: false
createdAt: "Fri Mar 15 2024 12:26:59 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 13:27:55 GMT+0000 (Coordinated Universal Time)"
---
The EVM Wallet Provider Submodule submodule helps you create wallets locally for EVM (Ethereum Virtual Machine) blockchains.The submodule comes with simple functions to create special phrases called mnemonics, extended public keys (xpubs), private keys, and addresses, as well as to handle transactions on EVM blockchains.

# Get Started

To get started using EVM Wallet Providers, you would need to install @tatumio/evm-wallet-provider along with the Tatum SDK.

```bash
npm install @tatumio/evm-wallet-provider
```

# What are the use cases EVM Wallet Provider Submodule helps with?

1. Mnemonic Generation: Generate mnemonics for seed phrases effortlessly, a foundational step for wallet creation and management. 
2. Extended Public Key (xpub) Creation: Create xpubs from mnemonics seamlessly, paving the way for deriving addresses and managing wallets. 
3. Private Key and Address Derivation: Derive private keys and addresses from mnemonics and xpubs efficiently, ensuring secure and organized wallet management. 
4. Transaction Signing and Broadcasting: Sign and broadcast transactions to EVM-based networks with ease, facilitating smooth interactions with the blockchain. 
5. Cross-Blockchain Development: With support for a multitude of EVM-based networks, extend your development horizons across various blockchain platforms including Ethereum, Binance Smart Chain, Polygon, and more. Secure dApp Development:

The EVM Wallet Provider submodule is an indispensable companion for developers striving to excel in the EVM blockchain ecosystem. Its extensive functionalities make it a reliable and potent toolkit for advanced wallet management and blockchain interaction.

# Supported Chains

[block:parameters]
{
  "data": {
    "h-0": "Blockchain",
    "h-1": "Mainnet",
    "h-2": "Testnet",
    "0-0": "Arbitrum",
    "0-1": "Network.ARBITRUM_NOVA  \nNetwork.ARBITRUM_ONE",
    "0-2": "Network.ARBITRUM_NOVA_TESTNET",
    "1-0": "Aurora",
    "1-1": "Network.AURORA",
    "1-2": "Network.AURORA_TESTNET",
    "2-0": "Avalanche",
    "2-1": "Network.AVALANCHE_C",
    "2-2": "Network.AVALANCHE_C_TESTNET",
    "3-0": "Binance Smart Chain",
    "3-1": "Network.BINANCE_SMART_CHAIN",
    "3-2": "Network.BINANCE_SMART_CHAIN_TESTNET",
    "4-0": "Celo",
    "4-1": "Network.CELO",
    "4-2": "Network.CELO_ALFAJORES",
    "5-0": "Chilliz",
    "5-1": "Network.CHILIZ",
    "5-2": "",
    "6-0": "Cronos",
    "6-1": "Network.CRONOS",
    "6-2": "Network.CRONOS_TESTNET",
    "7-0": "Ethereum",
    "7-1": "Network.ETHEREUM",
    "7-2": "Network.ETHEREUM_SEPOLIA  \nNetwork.ETHEREUM_GOERLI",
    "8-0": "Ethereum Classic",
    "8-1": "Network.ETHEREUM_CLASSIC",
    "8-2": "",
    "9-0": "Fantom",
    "9-1": "Network.FANTOM",
    "9-2": "Network.FANTOM_TESTNET",
    "10-0": "Flare",
    "10-1": "Network.FLARE",
    "10-2": "Network.FLARE_COSTON  \nNetwork.FLARE_COSTON_2  \nNetwork.FLARE_SONGBIRD",
    "11-0": "Gnosis",
    "11-1": "Network.GNOSIS",
    "11-2": "Network.GNOSIS_TESTNET",
    "12-0": "Harmony",
    "12-1": "Network.HARMONY_ONE_SHARD_0",
    "12-2": "Network.HARMONY_ONE_TESTNET_SHARD_0",
    "13-0": "Haqq",
    "13-1": "Network.HAQQ",
    "13-2": "Network.HAQQ_TESTNET",
    "14-0": "Horizen",
    "14-1": "Network.HORIZEN_EON",
    "14-2": "Network.HORIZEN_EON_GOBI",
    "15-0": "Klaytn",
    "15-1": "Network.KLAYTN",
    "15-2": "Network.KLAYTN_BAOBAB",
    "16-0": "KuCoin",
    "16-1": "Network.KUCOIN",
    "16-2": "Network.KUCOIN_TESTNET",
    "17-0": "Oasis",
    "17-1": "Network.OASIS",
    "17-2": "Network.OASIS_TESTNET",
    "18-0": "Optimism",
    "18-1": "Network.OPTIMISM",
    "18-2": "Network.OPTIMISM_TESTNET",
    "19-0": "Palm",
    "19-1": "Network.PALM",
    "19-2": "Network.PALM_TESTNET",
    "20-0": "Polygon",
    "20-1": "Network.POLYGON",
    "20-2": "Network.POLYGON_MUMBAI",
    "21-0": "VeChain",
    "21-1": "Network.VECHAIN",
    "21-2": "Network.VECHAIN_TESTNET",
    "22-0": "XDC",
    "22-1": "Network.XDC",
    "22-2": "Network.XDC_TESTNET"
  },
  "cols": 3,
  "rows": 23,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]
