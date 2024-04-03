---
title: "KMS - General FAQ"
slug: "kms-general-faq"
excerpt: ""
hidden: false
createdAt: "Sun Feb 25 2024 12:39:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 12:46:52 GMT+0000 (Coordinated Universal Time)"
---
Q. We are setting up development and pre-production configuration on a single server. Can we start KMS twice with separate paths?

**Example:**

```shell CLI
tatum-kms daemon --path=/path/to/wallet/store/directory/wallet.dat

:: Running KMS for dev as:
docker run -d --env-file .env -v $HOME:/root/.tatumrc tatumio/tatum-kms daemon --period 10 --chain=MATIC --testnet

:: Running KMS for Pre-production as:
docker run -d --env-file .env-pre-prod -v $HOME:/root/.tatumrc tatumio/tatum-kms daemon --period 10 --chain=MATIC --external-url={{URL}}
```

The differences are the .env  [.env for dev and .env-pre-prod for preproduction] files and where we are storing the wallets which is `wallet.dat` and `wallet-preProd.dat`.

A. Yes, with caveats. You can use a different name for your data, it is described in the KMS repo: <https://github.com/tatumio/tatum-kms>

```shell CLI
tatum-kms daemon --path=/path/to/wallet/store/directory/wallet.dat
```

If you start KMS twice, then each app uses its own config (i.e. mainnet/testnet) and "lives" in its own environment. Each of the apps should use its own API key, its own wallet.dat file  
The --env-file should work. There, you setup different API key (urls, passwords, ...) For different environments you need to add --path param as in example code, to separate wallet.dat files for the envs

***

Q. Can you give an example of the four-eyes principle in KMS Daemon? What parameters should we set and how should we do this?  
A.  This is just another API call where you validate If the tx could be signed on your end. 1 post rest API listener for you

***

Q. Where are the private keys stored?  
A. Inside `wallet.dat` file - encrypted in JSON file in KMS-specific format

***

Q. If we generate several wallets does it create several [wallet.dat]?  
A. No. All wallets are in one `wallet.dat` file

***

Q. Can we restore a Tatum wallet on a different server using backup wallet.dat and password?  
A. Yes

***

Q. Can we run two KMS setups in "daemon mode" from two isolated servers, but with the same [wallet.dat] file to have high availability and failover?  
A. Yes

***

Q. Can the KMS password be changed?  
A. For the time being, that's not possible.

***

Q. How can I set up KMS with AWS?  
A. If you were to set up KMS with AWS via “`TATUM_KMS_AWS_ACCESS_KEY_ID`” and "`TATUM_KMS_AWS_SECRET_ACCESS_KEY`” as AWS’s access key and secret key, they expire per session. Look up [AWS Long-Term Access Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html) and [AWS Managed Policy](https://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_available-policies.html). More information about AWS credentials is available at [the following link](https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html#iam-credentials).

***

Q. Can new Mnemonic phrases be generated in the KMS if the previous mnemonics are lost? If yes, are those previously generated Mnemonics still valid or invalid?  
A. Yes, that is possible. The old ones will still be valid.

***

Q. I am getting Error: 403 "Unable to broadcast transaction", "16: mandatory-script-verify-flag-failed..." What's wrong?  
A. Check the "signature id", if wrong causes the wrong privatekey under KMS in tx request.  
For BTC-based chains use key-based "signature id", for now. Mnemonic-based is currently under development. ETA soon.

***

Q. KMS running under Linux container, accessing Azure key vault to get the password. How can we make this work?  
A. Details are found at [the following link from Github](https://github.com/tatumio/tatum-kms/blob/1a567500bbd30774fbcf060b635744a2ef93ed10/src/index.ts#L103). Where: `if (flags.azure) {`

***

Q. I want to use TRON and TRC Tokens with KMS. How?  
A. TRON must be used for all TRX and trc20 transfers. It covers all tokens, native and TRC-10 and TRC-20.

***

Q. I sent a transaction with wrong data, so every time KMS on Daemon runs it will try to execute it but will keep failing. What can I do?  
A. Remove the unsuccessful TX via [the following v3 REST API endpoint](https://apidoc.tatum.io/tag/Key-Management-System/#operation/DeletePendingTransactionToSign).

***

Q. I want to work with KMS on PHP. Is that possible?  
A. Yes. Start KMS in Docker mode on a server and then you can the Tatum API in any language like PHP to do the transfers.

***

Q. How do I link KMS tx signature with Gas Pump?  
A. Check [the following article](https://docs-v3.tatum.io/gas-pump/pay-gas-fees-with-tatum-gas-pump).

***

Q. How can I export to file the wallet?  
A.` tatum-kms export --path=/pathtodirectory/wallet.dat`

***

Q. What is the cost for each KMS signature withdrawal?  
A. 2 credits per request and 2 credits for broadcasting, `4 in total`.
