## Transaction Monitoring

**Note:** This function is generally executed by the wallet backend program to avoid data confusion caused by other user operations. Only addresses specified in the local configuration file `/etc/listenEvent.conf` can operate.

------------------------------------------------------------------------------------------

#### Set Monitoring

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Register address monitoring)</code></summary>

**Description:**  
This action is generally executed by the wallet backend to register the wallet's concerned address information. Submit registered address information synchronously when adding accounts.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | data      |  required | string                  | Parameter description, serialize array []RegisterEvent to JSON then base64 encode  |
> | clear     |  required | boolean                 | If true, will clear existing configuration information  |

**RegisterEvent Structure:**
```go
type RegisterEvent struct{
  Address   string  `json:"address"`
  Funccode  string  `json:"funccode"`
}
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Registration result                                                 |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=registerEvent&data=&clear=false", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "aa80aa0c6bb0c7d81ac7e5b3",
>    "result": {
>      "ret": "0",
>      "err": ""
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Transaction Actions

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query transaction actions)</code></summary>

**Description:**  
This action is generally executed by the wallet backend periodically to traverse chain transaction data and record transfer information related to currently registered information.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Transaction item array                                              |

**Response Structure (TransItem):**
```go
type TransItem struct {
  From     string  `json:"from"`
  To       string  `json:"to"`
  Funccode string  `json:"funccode"`  // Contract transaction function code
  Data     string  `json:"data"`      // Contract transaction data
  Amount   uint64  `json:"amount"`    // Platform coin quantity
  High     uint64  `json:"high"`      // Block height
  TxHash   string  `json:"txHash"`    // Transaction hash
}
```

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=scanBlock&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "aa80aa0c6bb0c7d81ac7e5b3",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {}
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Blockchain Traversal Interface

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Traverse blockchain)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | begin     |  required | int                     | Starting block height, maximum 100 blocks returned at once  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Block array                                                         |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=scanBlock&begin=&sliceno=0","encryp=none"],
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
>        "parentHash": "0xcfee308a28697bafef2f635c2c67272a65eab1996c93aebac2bcb29155d5bc77",
>        "miner": "0x6d3da5167929a4b297df09325389d72f35327fa4",
>        "stateRoot": "0x670a4e6f9262854a889e36dd766c6942780a6a9c74840fcbe2a9fde1e4f2c36b",
>        "transactionsRoot": "0xb0ef76de17cce27b75554325e7cba7f22eb3238fb642f35b174c885ae86f1987",
>        "receiptsRoot": "0xbc86b068c10758ec5e644d81b530038b31e6da3450892c7a3dcb6e9a0488c1e8",
>        "Recno": 2,
>        "number": 1,
>        "timestamp": 1742515456744655700,
>        "Txns": [
>          "0xd56f8fd299e309598752d54576395f15d403f2eb274d163e4eaf9e103cf64828"
>        ],
>        "Senders": [
>          "0x35f4646842fc5fe208b7d3fab125c8542be88324"
>        ],
>        "Data": ""
>      }]
>    }
>  }
> ```

**Field Descriptions:**
- **Txns** - Transaction hash array
- **Senders** - Transaction submitter array
- **Data** - Transaction content (base64 encoded)

</details>

------------------------------------------------------------------------------------------
