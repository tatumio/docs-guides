---
title: "TRON - Troubleshooting Tapos check error"
slug: "tron-troubleshooting-tapos-check-error"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 22:23:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:25:34 GMT+0000 (Coordinated Universal Time)"
---
When utilizing the TRON network, you may encounter the error "`tron.blockchain.broadcast.error`" with the cause identified as "`Tapos check error.`"

The Tapos error check specifically points to an issue with the "`ref_block_hash`" parameter in the transaction payload.

> 📘 Additional information is available at [the following link](https://developers.tron.network/docs/faq#12-broadcast-response-code).

## Example Payload

```json JSON
"{\"visible\":false,\"txID\":\"d29228b006181447a75796953824fff1de55be30a964ffdba2a88ff####\",\"raw_data\":{\"contract\":[{\"parameter\":{\"value\":{\"data\":\"a9059cbb0000000000000000000000009f4e3eb9ae86450bd2ec4be7c88004d215b47b0900000000000000000000000000000000000000000000000000000000####\",\"owner_address\":\"4113c83df83b14e8ff33f9aa63c48e41d####\",\"contract_address\":\"#####\"},\"type_url\":\"#####\"},\"type\":\"TriggerSmartContract\"}],\"ref_block_bytes\":\"85c5\",\"ref_block_hash\":\"d06bf1458a2f###\",\"expiration\":1705324902000,\"fee_limit\":40000000,\"timestamp\":1705324843822},\"raw_data_hex\":\"0a0285c52208d06bf1458a2f760040f0eca3e######48913\",\"signature\":[\"58c2f618e1e888bdbca29e7f4243ccdb19216bfbd32a4b6f363d5242dfd7ffdb912d3af8e7c64399dcb72dcb3aac7c83c6cfa6f####\"]}"
```

The reference block specified by the "`ref_block_hash`" parameter needs to be on the same chain as the transaction. If these are not aligned, the Tapos check error may occur.

## Example Error

```json
{
  "statusCode": 403,
  "errorCode": "tron.blockchain.broadcast.error",
  "message": "Unable to broadcast transaction",
  "cause": "Tapos check error."
}
```
