## Public Queries

```json
{ 
  "jsonrpc": "3.0", 
  "method": "chain_queryInfo", 
  "params": ["{key}","{content}","encryp=none"], 
  "id": "1"
} 
```

**Key Description:**
- `pubTrustQuery` - Trust machine public information query
- `pubChainQuery` - Mainnet public information query

Public information queries do not require login.

------------------------------------------------------------------------------------------

#### Get Edge Trust Machine ID

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query current edge trust machine ID)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | op        |  required | string                  | edgeInfo - Query edge trust machine ID to add to the vacuum network node allowlist  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"ret":"0","err":"","content":{"edge_id":"..."}}`                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubTrustQuery","op=edgeInfo","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "edge_id": "16c079fb71bdb921002735db3f3ff37bdb7629cf7caec29a649dcc240b34c49c"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Entry Information Query

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query corresponding vacuum network node entry information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | op        |  required | string                  | entryInfo - Query entry information  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Entry information details                                           |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubTrustQuery","op=entryInfo","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "edge_id": "16c079fb71bdb921002735db3f3ff37bdb7629cf7caec29a649dcc240b34c49c",
>        "tmac_id": "66f560cd08ac831e4f7195a672cd5603e3d4ce578142c939d22062a4ee5c081b",
>        "tmac_entry": "fc7aab55f28388f035a9afc1e9cace3d7de52a12bf89511d759805e19e8faf11074dad1015ee681ebd956b63cdc3a9cb347a5fae6f79622d7ce5ba208d163fcc@103.123.5.10",
>        "tmac_auth_succ": true,
>        "auth_error": "",
>        "chain_id": "f2a61969b24a3cab29a88b107a0de169d348714fb564ea9e579c768422e49804",
>        "Chain_entry": "43f394edeff1fcb38c6f3368b85324803f4619c1208aa6cbfa7b7e5a06bfe8818d854ebbc11632d915ae4f1195694b963d01fca363a72394c337a2e7f9f0b61f@103.123.5.10",
>        "Chain_register": true
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Node Query

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query nearby nodes)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | op        |  required | string                  | nodes - Query nearby nodes  |
> | sliceno   |  required | int                     | Operating metaspace  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Node list                                                           |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=nodes&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Block List

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query recent block timestamps at specified height)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | nums      |  required | int                     | Number of blocks to list  |
> | number    |  required | string/int              | Specified header block height, "latest" represents the latest height  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Block list array                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryBlocks&nums=5&number=latest&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": [
>        {
>          "number": 178,
>          "miner": "0xca2fad5ae97e9c154f7a9b362e20531393dd81bf",
>          "tv": 1696318486264618700,
>          "txs": 95,
>          "size": 46156
>        },
>        {
>          "number": 177,
>          "miner": "0xca2fad5ae97e9c154f7a9b362e20531393dd81bf",
>          "tv": 1696318485140797000,
>          "txs": 96,
>          "size": 46642
>        }
>      ]
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Block Information

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query specified block information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | number    |  required | int                     | Block height  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Block details                                                       |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryBlock&number=12&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "parentHash": "0x84aaa1a6bb1eba0757a073d3170095c255f2afbf5a08db018df4ee60dc272d4d",
>        "miner": "0x8bc7c3cf1acd3df586f0f892279163f813a59c27",
>        "stateRoot": "0xe15028b14d674d1eedef5b4a40e74c77c4d75091632c15539c266e4029e4bfae",
>        "transactionsRoot": "0x5f43e0ebce13bad2ab3ce605a2a2698d8cd104ca6bc2ce962ad952d75dcc1b59",
>        "receiptsRoot": "0x703c035562d8e37c66f2f9461219b45c710e59c8d0d234f6b062107de627758c",
>        "Recno": 247,
>        "number": 59,
>        "timestamp": 1696318054669580400,
>        "Txns": [
>          "0x64e0a480debe89f94e5a55f3f7aa911a0c080dd6e3f4a7755bda2cca9ae77850"
>        ]
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Block Transactions

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query specified block transaction information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | number    |  required | int                     | Block height  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Transaction list array                                              |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryBlockTrans&number=12&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": [{
>        "nonce": "0x3df",
>        "type": "0x1",
>        "gas": "0x1406f40",
>        "to": "0x96947ca1dee5c34890a26ab3652360faf8771ab3",
>        "value": "0x0",
>        "input": "0x01fe01fe...",
>        "hash": "0x99e368a0ce33e478325dc120165009b18dd3375ab2967ae399e1e38cebbeced1"
>      }]
>    }
>  }
> ```

**Transaction Types:**
- `0x1` - Normal activity
- `0x2` - Transfer activity
- `0x3` - Device activity (hidden, to be released later)
- `0x4` - Content activity
- `0x5` - Platform activity

</details>

------------------------------------------------------------------------------------------

#### Address Query

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query address information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | value     |  required | string                  | Address  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Address details                                                     |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryAddress&value=0x053288e276ee77e231e306332b2c88283796be45<->latest&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "Nonce": 10013,
>        "Addrno": 5,
>        "Balance": 19790000000000,
>        "Root": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
>        "Type": 0,
>        "Owner": "0x0000000000000000000000000000000000000000",
>        "Grant": "0x0000000000000000000000000000000000000000",
>        "GasDate": 20231003,
>        "GasValue": 0,
>        "GasBuyValue": 0,
>        "Content": "{\"account\":\"00000000299\",\"content\":\"RH2SEoxp/69hTPn4auj+kQ==\"}"
>      }
>    }
>  }
> ```

**Type Field Description:**
- `0` - Control account
- `1` - Contract account
- `2` - Trust machine account
- `3` - Type account
- `4` - Product account
- `5` - Model account

</details>

------------------------------------------------------------------------------------------

#### Rewards Query

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query reward information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Reward details array                                                |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=rewards&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": [{
>        "high": 22893,
>        "nums": 2,
>        "amount": 914705537,
>        "level4": [],
>        "level3": [],
>        "level2": [{
>          "id": "b9c89aa675642858c9dcb4847017f4b9fbb9fcd3b1fc521c6d16aa421e958cc4",
>          "miner": "0x6d3da5167929a4b297df09325389d72f35327fa4",
>          "name": "hu2"
>        }],
>        "level1": {
>          "id": "4de9d41e32c30e40cb85ffddcdd543af1c8c7b61a3ef64a5527d58d24ea119c2",
>          "miner": "0xca2fad5ae97e9c154f7a9b362e20531393dd81bf",
>          "name": "hu1"
>        }
>      }]
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Account Check

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Check if account exists)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Account name to check  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Account existence status                                            |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=checkAccount&account=12","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "find": false,
>        "data": "",
>        "err": ""
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Token List Interface

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query available tokens)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | None      |  N/A      | N/A                     | No parameters required  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Token list array                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubTrustQuery","op=queryToken","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": [{
>        "name": "TChain",
>        "desc": "TChain platform coin",
>        "address": "",
>        "base_addr": ""
>      }]
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Transaction Result Query

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query transaction result)</code></summary>

**Note:** For any action that returns a `txhash` field, it indicates a chain update action. You need to query the action result every second to complete the interface submission process until it returns.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | hash      |  required | string                  | Transaction hash  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Transaction details                                                 |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=queryTx&hash=0xf8af2a6966c3......&sliceno=0","encryp=none"],
>    "id": "1"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": [{
>        "root": "0d233ef6a3ddfacdf46",
>        "status": 2,
>        "transactionHash": "0x414f5206c1bc79",
>        "contractAddress": "0x000000000000000",
>        "blockHash": "0x0e09ff036fad9e67da6a4b",
>        "blockNumber": 35,
>        "transactionIndex": 1,
>        "return_data": "",
>        "from": "0x000000000000000000000000000",
>        "to": "0xb880e69da1e4bfa1e4bbbbe5889be5",
>        "nonce": 0,
>        "txtype": 2,
>        "tx_content": "01fe01fe01fe01f",
>        "amount": 0,
>        "timeval": 43
>      }]
>    }
>  }
> ```

**Transaction Status:**
- `0` - Transaction still in transaction pool
- `1` - Transaction packaged and waiting for confirmation
- `2` - Confirmed and execution result returned
- `3` - Transaction failed and deleted

**Transaction Types:**
- `0x1` - Normal activity
- `0x2` - Transfer activity
- `0x3` - Device activity (hidden, to be released later)
- `0x4` - Content activity
- `0x5` - Platform activity

</details>

------------------------------------------------------------------------------------------
