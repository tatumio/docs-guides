---
title: "Solana - Indexing and Confirmation"
slug: "solana-indexing-and-confirmation"
excerpt: ""
hidden: false
createdAt: "Sun Feb 11 2024 22:45:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:49:13 GMT+0000 (Coordinated Universal Time)"
---
For preflight checks and transaction processing, Solana nodes choose which bank state to query based on a commitment requirement set by the client. The commitment describes how finalized a block is at that point in time. 

## Solana blocks - state in descending order of commitment

### Finalized

The node will query the most recent block confirmed by supermajority of the cluster as having reached maximum lockout, meaning **the cluster has recognized this block as finalized**.

### Confirmed

The node will query the most recent block that has been voted on by supermajority of the cluster.

- It incorporates votes from gossip and replay.
- It does not count votes on descendants of a block, only direct votes on that block.
- This confirmation level also upholds "optimistic confirmation" guarantees in release 1.3 and onwards.

### Processed

The node will query its most recent block. Note that the block may still be skipped by the cluster.

> 📘 It's recommended to query blocks with a "finalized" state. These should take about 2-3 minutes. More information is avaialble at [the following link](https://solana.com/docs/rpc/http#configuring-state-commitment).
