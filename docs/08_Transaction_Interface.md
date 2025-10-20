## Transaction Interface

------------------------------------------------------------------------------------------

#### Transfer

<details>
 <summary><code>POST</code> <code><b>chain_sendTransaction</b></code> <code>(Transfer tokens)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | Sender  |
> | to        |  required | string                  | Receiver  |
> | value     |  required | string (hex)            | Amount  |
> | sliceno   |  required | string (hex)            | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**Response Fields:**
- **txhash** - Transaction hash

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_sendTransaction",
>    "params": [{
>      "from": "0xc3b6472d6370eaf4eb58fff19ce1724c9d61892c",
>      "to": "0x6268af5542c4b0ccbb650a0aaccbfcdfbabf6b52",
>      "value": "0x2E90EDD00",
>      "sliceno": "0x1"
>    }, "", "encryp=none"],
>    "id": "d2c8fe196f9f8d8ace952e9e"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "d2c8fe196f9f8d8ace952e9e",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Distribute Transactions

<details>
 <summary><code>POST</code> <code><b>chain_airDrop</b></code> <code>(Batch transfer)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | allocate  |  required | string                  | Batch transfer content (base64 encoded JSON)  |
> | sliceno   |  required | int                     | Metaspace number  |

**Content Format (before base64 encoding):**
```json
{
  "from": "0x4ace8d71fd08d72b467cabc607d9fe1adfc28a75",
  "total": 100,
  "dest": [{
    "addr": "0x35f4646842fc5Fe208b7D3fab125C8542be88324",
    "nums": 60
  },{
    "addr": "0xc94196d73E8eA564b1c753e07814Ee5635de7045",
    "nums": 40
  }]
}
```

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**Response Fields:**
- **txhash** - Transaction hash

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_airDrop",
>    "params": ["opcode=allocate&allocate=&sliceno=1", "encryp=none"],
>    "id": "d2c8fe196f9f8d8ace952e9e"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "d2c8fe196f9f8d8ace952e9e",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Deploy Contract

<details>
 <summary><code>POST</code> <code><b>chain_sendTransaction</b></code> <code>(Deploy smart contract)</code></summary>

**Programming Language:** Solidity  
**Compilation Version:** 0.8.1

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | Current logged-in account address  |
> | data      |  required | string (hex)            | Contract hex content  |
> | sliceno   |  required | string (hex)            | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**Response Fields:**
- **txhash** - Transaction hash

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_sendTransaction",
>    "params": [{
>      "from": "0x2c8e94bbe17cec95f21dfdb55e334cfd4effcd9d",
>      "data": "0x6008......",
>      "sliceno": "0x1"
>    }, "", "encryp=none"],
>    "id": "a3d18f63c99c7660c87c5f3e"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "d2c8fe196f9f8d8ace952e9e",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Execute Contract

<details>
 <summary><code>POST</code> <code><b>chain_sendTransaction</b></code> <code>(Execute contract function)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | Current logged-in account address  |
> | to        |  required | string                  | Contract address  |
> | data      |  required | string (hex)            | Hex content (function code and parameters)  |
> | sliceno   |  required | string (hex)            | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**Response Fields:**
- **txhash** - Transaction hash

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_sendTransaction",
>    "params": [{
>      "from": "0x2c8e94bbe17cec95f21dfdb55e334cfd4effcd9d",
>      "to": "0x61b3d1759e4d3bd238a2730cb1621fa542a771fd",
>      "data": "0x60086678",
>      "sliceno": "0x1"
>    }, "", "encryp=none"],
>    "id": "a3d18f63c99c7660c87c5f3e"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "d2c8fe196f9f8d8ace952e9e",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Contract Function Code Query

<details>
 <summary><code>POST</code> <code><b>chain_queryFuntionCode</b></code> <code>(Query function code)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | params    |  required | string                  | Function name  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Function code

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryFuntionCode",
>    "params": ["getTYpe()"],
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
>        "info": "0xae591f49"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
