---
title: "getbestblockhash"
slug: "getbestblockhash-1"
excerpt: ""
category: 65a9112c408e3a004ae466df
hidden: false
createdAt: "Wed Mar 06 2024 10:41:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 06 2024 10:41:39 GMT+0000 (Coordinated Universal Time)"
---
How to use it  
// yarn add @tatumio/tatum  
​  
import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'  
​  
const tatum = await TatumSDK.init<Dogecoin>({network: DOGECOIN})  
​  
const result = await tatum.rpc.getBestBlockHash()  
​  
await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs  
Overview  
getbestblockhash is a Dogecoin RPC method that returns the hash of the best (tip) block in the longest blockchain. This method is useful for obtaining the latest block hash, which can be used to fetch block details or confirmations for transactions.  
Parameters  
This method does not have any parameters.  
Return Object  
The returned object is a string containing the hash of the best block.  
JSON Examples  
Request example:  
{  
  "id": 1,  
  "jsonrpc": "2.0",  
  "method": "getbestblockhash"  
}  
Response example:  
{  
  "id": 1,  
  "result": "0000000000000000000ef0e1f703b56f2b0d6724e4eeccf00e4f8d55b9c3c3f6e",  
  "error": null  
}
