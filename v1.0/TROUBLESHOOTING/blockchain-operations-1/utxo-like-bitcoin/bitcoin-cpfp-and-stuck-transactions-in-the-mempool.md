---
title: "BTC - CPFP and stuck transactions in the mempool"
slug: "bitcoin-cpfp-and-stuck-transactions-in-the-mempool"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Mon Jan 29 2024 10:22:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Feb 09 2024 08:48:24 GMT+0000 (Coordinated Universal Time)"
---
If your Bitcoin transaction is stuck, and you're the recipient, you can clear it using CPFP (child-pays-for-parent). This is an alternative to the sender's ability to do so with RBF when this has not been enabled in a transaction stuck in the mempool.

## How does Child-Pays-for-Parent (CPFP) work?

The idea of CPFP is that you "own" the privateKey of a recipient address of a transaction that hasn't been confirmed in a block yet and you want to use that coin ASAP. To achieve this, you will include that unconfirmed transaction in a new transaction and you will pay a high enough fee to encourage a miner to include both the original (parent) transaction and the new (child) transaction in a block. As a result, the parent and child transactions will clear simultaneously.

> 📘 CPFP is just an incentive scheme that can be used for transaction selection by miners. There might be reasons that the child can't be selected to be put into a block, and this will prevent the parent UTXO from ever being put into a block.

## Spending unconfirmed UTXOs

1. Check Transaction Status: Use a blockchain explorer or wallet software to monitor the status of your original transaction. Make sure it is still unconfirmed and stuck. See [BTC mempool explorer](https://mempool.space/).
2. Find the `vout` of the unconfirmed transaction. Example:

```json JSON
"vout": \[  
 {  
   "value": 0.01000000,  
   "n": 0,  
   "scriptPubKey": {  
     "asm": "OP_HASH160 f079f77f2ef0ef1187093379d128ec28d0b4bf76 OP_EQUAL",  
     "hex": "a914f079f77f2ef0ef1187093379d128ec28d0b4bf7687",  
     "reqSigs": 1,  
     "type": "scripthash",  
     "addresses": [  
       "2NFAkGiwnp8wvCodRBx3smJwxncuG3hndn5"  
     ]  
   }  
 },
```

3. Find in the `vout` the object the one that matches your address. (Here, it's the only one.) The `n` value is your `vout`.
4. Create a raw transaction using your unconfirmed transaction as input.
5. Double the transaction fees (or more).

> 📘 More information about CPFP is available at [the following link](https://github.com/BlockchainCommons/Learning-Bitcoin-from-the-Command-Line/blob/master/05_3_Funding_a_Transaction_with_CPFP.md).

## Good to know

To accelerate a CPFP transaction, you will have to estimate a fee high enough to get both parent and child transactions processed. The Tatum JS SDK has a public extension facilitating the estimate - [CPFP Fee Estimator](https://www.npmjs.com/package/@tatumio/cpfp-fee-estimator).
