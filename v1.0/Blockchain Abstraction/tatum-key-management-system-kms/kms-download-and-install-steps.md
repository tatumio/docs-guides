---
title: "Download and Install KMS"
slug: "kms-download-and-install-steps"
excerpt: ""
hidden: false
createdAt: "Sun Feb 11 2024 15:34:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 11:15:16 GMT+0000 (Coordinated Universal Time)"
---
# Download KMS

- **macOS**: Natively or via [Docker](https://hub.docker.com/repository/docker/tatumio/tatum-kms)
- **Unix**: Natively or via [Docker](https://hub.docker.com/repository/docker/tatumio/tatum-kms)
- **Ms Windows**: `Only` via [Docker](https://hub.docker.com/repository/docker/tatumio/tatum-kms)

> 📘 We recommend that you run KMS from the [Docker image](https://hub.docker.com/repository/docker/tatumio/tatum-kms) regardless of the operating system used.

> 🚧 Tatum KMS should be installed in the Deny-From-All environment to meet the highest security standards.

# Install KMS

## From npm

1. Install KMS globally:
   ```Text CLI
   npm i -g @tatumio/tatum-kms
   //or
   yarn global add @tatumio/tatum-kms
   ```
2. Use `.env `file to configure Tatum KMS
   1. via `--env-file=/path/to/.env`
      ```Text CLI
       tatum-kms --env-file=/path/to/.env getaddress 11111111-1111-1111-1111-111111111111 0
      ```
   2. via environment variables directly
      ```Text CLI
      TATUM_API_KEY=XXXXX-YOUR-API-KEY tatum-kms --help
      ```
   3. via predefined environment vars on global level
      ```Text CLI
      export TATUM_API_KEY=XXXXX-YOUR-API-KEY  
      tatum-kms --help
      ```
      > 🚧 IMPORTANT! NodeJS >=14 and npm@6 are required. KMS does not work on npm@7.

## From Docker

1. Pull the `tatum-kms` image:
   ```Text CLI
   docker pull tatumio/tatum-kms
   ```
2. Navigate to the home directory:
   ```Text CLI
   cd $HOME
   ```
3. Use pre-created `.env` file to configure Tatum KMS via `--env-file .env`
4. Map the Docker volume to the local storage (your home folder).
   1. For more details, refer to the [Docker user documentation](https://docs.docker.com/storage/volumes/).
   2. Once you have mapped the Docker volume, KMS is ready to be run as a Docker container.

To interactively communicate with KMS and run various [KMS commands](https://github.com/tatumio/tatum-kms?tab=readme-ov-file#kms-commands), use the `docker run` command:

```Text CLI
docker run -it --env-file .env -v $HOME:/root/.tatumrc tatumio/tatum-kms --help
docker run -it --env-file .env -v $HOME:/root/.tatumrc tatumio/tatum-kms generatemanagedwallet BTC
docker run -it --env-file .env -v $HOME:/root/.tatumrc tatumio/tatum-kms storemanagedprivatekey BTC

//NOTE: You can shorten the command syntax and use it as follows:
docker run ${COMMON_PARAMS} tatumio/tatum-kms generatemanagedwallet BTC
//where COMMON_PARAMS can be exported as all the flags necessary for running the container.
```

# Good to know

1. It is possible to store private keys locally or using an external service:
   1. [Azure Key Vault](https://azure.microsoft.com/en-us/services/key-vault/)
   2. [VGS](https://www.verygoodsecurity.com/)
   3. [AWS Secrets Management](https://aws.amazon.com/secrets-manager/)
2. After you generate and store the wallets you want to work with, enable daemon mode. Daemon mode periodically checks for pending transactions to sign.
3. Every pending transaction has a `signatureId`. When a pending transaction matches a stored wallet, it is signed locally and sent to the blockchain. Your wallet data are stored only in memory.

> 📘 KMS supports the 4 eye control mechanism, where pending transactions are controlled in Tatum and the customer system. By default, KMS checks for the pending transactions every 5 seconds using the following [REST API call](https://apidoc.tatum.io/tag/Key-Management-System/#operation/GetPendingTransactionsToSign).
