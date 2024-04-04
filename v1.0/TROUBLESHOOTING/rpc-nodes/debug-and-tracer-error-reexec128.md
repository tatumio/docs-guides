---
title: "Debug and Tracer error: reexec=128"
slug: "debug-and-tracer-error-reexec128"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Thu Feb 08 2024 20:21:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2024 20:29:25 GMT+0000 (Coordinated Universal Time)"
---
Dbug and Tracer calls are **highly resource-consuming**. This means that they can take some extra time to return a response. Due to this, you may encounter errors like `reexec=128` on your Node RPC calls.

## Steps to troubleshoot

 Add the optional `timeout` parameter on your debug and tracer requests.

### Example Payloads

**Optimism:**

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/optimism-mainnet/{API_KEY}' \
--header 'Content-Type: application/json' \
--data '{
    "jsonrpc": "2.0",
    "method": "debug_traceBlockByNumber",
    "params": [
        "0x666c7f4",
        {
            "tracer": "callTracer",
            "timeout":"1m"
        }
    ],
  "id": 2
}'
```

**KLAY:**

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/arb-one-mainnet/{API_KEY}' \
--header 'Content-Type: application/json' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "debug_traceBlockByNumber",
  "params": [
    "0xa1e86ab",
    {
      "tracer": "callTracer",
      "timeout": "10s"
    }
  ]
}'
```

> 📘 You can find additional information at [the following link](https://pkg.go.dev/time#ParseDuration).
