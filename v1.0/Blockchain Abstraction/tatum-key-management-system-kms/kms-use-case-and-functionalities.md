---
title: "Use Case and Functionalities"
slug: "kms-use-case-and-functionalities"
excerpt: ""
hidden: false
createdAt: "Sun Feb 11 2024 15:52:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:16:54 GMT+0000 (Coordinated Universal Time)"
---
# How does KMS Work?

KMS runs locally on your server and provides security for generating wallets, addresses, private keys, and signing transactions securely. KMS stores all your mnemonics and private keys in a wallet storage file. This storage file is an AEC encrypted file, for which only you know the encryption key.

Every wallet stored inside your KMS instance has a unique identifier, called signatureId. This signatureId is used in communication with Tatum API and represents the wallet used by the specific operation. When you generate and store all the wallets you want to work with, you then enable the daemon mode in the KMS. This daemon mode periodically checks for pending transactions to sign.

**Summary:**

- When you generate a wallet with KMS, it creates a signature ID that is used in place of the wallet’s mnemonic.
- When you generate a private key to an address, it creates a signature ID to be used in place of the private key.
- When you send API requests to Tatum you only have to remember to replace two fields:
  - `mnemonic` -> `signatureId` (of the wallet’s mnemonic phrase) - It's best to keep track of the "index"
  - `fromPrivateKey` -> `signatureId` (of the private key)

## There are the following options for how Tatum handles private keys to blockchain addresses:

- Sending private keys/mnemonic seeds to Tatum's REST API directly - This is not recommended in the production environment, and it should be used in a testnet only. Tatum never stores any private keys or mnemonic seeds.
- **Using Tatum libraries** to create wallets and sign transactions locally on a backend - [JavaScript](https://github.com/tatumio/tatum-js) 
- **Using Tatum KMS**, an external tool to securely generate and store private keys and use them to sign transactions locally. This is the safest and recommended way of working with private keys.

# KMS Operation Modes

## KMS provides two modes of operation:

- **CLI mode**: used to generate wallets or private keys, typically for the initial setup and one-time operations.
- **Daemon mode**: periodically pulls pending transactions from the Tatum API, signs transactions locally, and broadcasts the transactions to the blockchain.

## KMS works with three types of signature IDs:

- **Private key-based** signature IDs  
  When a private key is required to sign an operation, you must replace `privateKey` with `signatureId` matching the signature ID of the mnemonic.
- **mnemonic-based** signature IDs (intended for Virtual Accounts)  
  When a mnemonic is required to sign an operation, you must replace the `mnemonic` with the `signatureId` matching the signature ID of the mnemonic.
- **mnemonic && index** based signature IDs  
  When a mnemonic && index are required to sign an operation, you must replace the `mnemonic` with the `signatureId` matching the signature ID of the mnemonic as well its index.

## PrivateKey and Mnemonic caveats - storage limits

- **Mnemonic-based**: You could assign one (1) `signatureId` per mnemonic. To support this setup, we'd suggest building a database to store your customers' data, including but not limited to their associated IDs, KMS signature IDs, and the related index matching with their address/PrivateKey within the mnemonic in KMS.  
  With a limit of 25.000 mnemonics per API Key in KMS, where each mnemonic can contain up to 2^32 addresses, you could safely store and sign operations for **25K x 2^32 distinctive addresses/customers**.
- Private Key-based: You could assign one (1) `signatureId` per each individual PrivateKey. With a limit of 25.000 Private Keys per API Key in KMS, you could safely store and sign operations for **25K distinctive addresses/customers**.

> 📘 Each API key assigned to KMS supports up to 25.000 signatureId. You can reuse a seed/mnemonic for different chains. However, each chain requires a distinctive signatureId.

# KMS Functions

- Get a list of pending transactions to sign - [v3 REST API endpoint](https://apidoc.tatum.io/tag/Key-Management-System/#operation/GetPendingTransactionsToSign)
- Complete pending transactions to sign- [v3 REST API endpoint](https://apidoc.tatum.io/tag/Key-Management-System/#operation/CompletePendingSignature)
- Delete transactions waiting to be signed- [v3 REST API endpoint](https://apidoc.tatum.io/tag/Key-Management-System/#operation/DeletePendingTransactionToSign)
