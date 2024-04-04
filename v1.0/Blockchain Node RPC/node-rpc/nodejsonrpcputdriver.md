---
title: "Connect to the blockchain node through an RPC driver"
slug: "nodejsonrpcputdriver"
excerpt: "<p><b>2 credits per RPC method in an API call</b></p>\n<p>Connect directly to the blockchain node provided by Tatum.</p>\n<p>The <code>PUT</code> method is used. The API endpoint URL acts as an HTTP-based RPC driver.</p>\n<p>In the request body, provide valid Web3 RPC method content, for example:</p>\n<pre>\n{\n  \"jsonrpc\": \"2.0\",\n  \"id\": 1,\n  \"method\": \"method_name\",\n  \"params\": []\n}\n</pre>\n<p>For the blockchains using the JSON-RPC 2.0 specification, you can submit multiple RPC methods in one API call:</p>\n<pre>\n[\n  {\n    \"jsonrpc\": \"2.0\",\n    \"id\": 1,\n    \"method\": \"method_1_name\",\n    \"params\": []\n  },\n  {\n    \"jsonrpc\": \"2.0\",\n    \"id\": 2,\n    \"method\": \"method_2_name\",\n    \"params\": []\n  },\n  ...\n]\n</pre>\n<p>This API is supported for the following blockchains:</p>\n<ul>\n  <li><a href=\"https://developer.algorand.org/docs/rest-apis/restendpoints/\" target=\"_blank\">Algorand</a></li>\n  <li><a href=\"https://docs.bnbchain.org/docs/beaconchain/develop/api-reference/node-rpc#5-rpc-endpoint-list\" target=\"_blank\">BNB Beacon Chain</a></li>\n  <li><a href=\"https://docs.elrond.com/sdk-and-tools/rest-api/nodes/\" target=\"_blank\">Elrond</a></li>\n  <li><a href=\"https://developers.stellar.org/api\" target=\"_blank\">Stellar</a></li>\n</ul>"
category: 65c0c794d329e30077a0638c
hidden: false
createdAt: "Mon Feb 05 2024 11:33:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:33:42 GMT+0000 (Coordinated Universal Time)"
---
