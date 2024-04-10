---
title: "decodescript"
slug: "rpc-dogecoin-decodescript"
excerpt: "Dogecoin RPC"
hidden: false
metadata: 
  description: "Dogecoin RPC"
  image: []
  keywords: "dogecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Dogecoin>({network: Network.DOGECOIN})

const result = await tatum.rpc.decodeScript("3044022070cc08500b2203b6ebe7c8285295bc1914a9d252504416e1cde4de4a7dc6c3c8022079af2be6db34efcf147e86a4cbf61cf9995106e5b5e95270d47c40b082052c8501")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `decodescript` RPC method decodes a serialized (hex-encoded) script and provides information about the script in a human-readable format. This method is useful for inspecting scripts for debugging purposes or for understanding their structure.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Martin-Zemanek/pen/dyQrvdm",
  "href": "https://codepen.io/Martin-Zemanek/pen/dyQrvdm",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `hex_string`: (string, required) The serialized script in hex format.

### Return Object

An object containing the decoded script information:

- `asm`: (string) The assembly representation of the script.
- `hex`: (string) The hex-encoded script.
- `type`: (string) The type of the script (e.g., 'pubkeyhash', 'multisig').
- `reqSigs`: (numeric, optional) The required number of signatures if the script is a multisig script.
- `addresses`: (array, optional) An array of Litecoin addresses associated with the script if applicable.
- `p2sh`: (string, optional) The P2SH address for this script if applicable.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "decodescript",
  "params": ["3044022070cc08500b2203b6ebe7c8285295bc1914a9d252504416e1cde4de4a7dc6c3c8022079af2be6db34efcf147e86a4cbf61cf9995106e5b5e95270d47c40b082052c8501"],
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": {
        "asm": "44022070cc08500b2203b6ebe7c8285295bc1914a9d252504416e1cde4de4a7dc6c3c8022079af2be6db34efcf147e86 OP_MAX OP_UNKNOWN OP_UNKNOWN [error]",
        "desc": "raw(3044022070cc08500b2203b6ebe7c8285295bc1914a9d252504416e1cde4de4a7dc6c3c8022079af2be6db34efcf147e86a4cbf61cf9995106e5b5e95270d47c40b082052c8501)#3x5hf724",
        "type": "nonstandard"
    },
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
