---
title: "Solana error: getProgramAccounts"
slug: "solana-error-getprogramaccounts"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 20:47:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2024 20:47:33 GMT+0000 (Coordinated Universal Time)"
---
When making a complex call to a Solana RPC Node with the method `getProgramAccounts`, you may get an error looking as follows:

```json JSON
{
 "jsonrpc":"2.0",
 "error":{
  "code":-32010,
  "message":"Tokenkeg####### excluded from account secondary indexes; 
  this RPC method unavailable for key"
 },
 "id":1
}
```

From Solana Github, this error appears if a program is excluded from the secondary indices. [`Tokenkeg...`] with lots of accounts can be excluded from [`getProgramAccounts`] by RPC nodes as a consequence.

> 📘 Additional information is available at [the following link](https://github.com/solana-labs/solana-program-library/issues/2547#issuecomment-1168004960).
