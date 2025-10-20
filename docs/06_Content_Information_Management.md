## Content Information Management

------------------------------------------------------------------------------------------

#### Create Address

<details>
 <summary><code>POST</code> <code><b>chain_address</b></code> <code>(Create type)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | name      |  required | string                  | Type name  |
> | content   |  required | string                  | Type description  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**Response Fields:**
- **txhash** - Current transaction hash
- After successful creation, the corresponding address is returned. You need to obtain it from the transaction result query (contractAddress field).

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_address",
>    "params": ["opcode=Iot&subcode=createaddress&name=soft&content=&sliceno=0", "encryp=none"],
>    "id": "291687c0293354a642e3eadf"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "c52ec4472ccfc12a04c544bf",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "txhash": "0x58e4e65d6fa48a79f874e6debe25039405d3702e0d65050ab64146fe8d58d5ee"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Update Address Content

<details>
 <summary><code>POST</code> <code><b>chain_updateContent</b></code> <code>(Update content)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address   |  required | string                  | Content address  |
> | name      |  required | string                  | Content name  |
> | content   |  required | string                  | Content  |
> | sliceno   |  required | int                     | Metaspace number (main metaspace number is 0)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"address":"...","txhash":"..."}`                                  |

**Response Fields:**
- **txhash** - Current transaction hash

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_updateContent",
>    "params": ["opcode=Iot&subcode=update&address=&name=&content=&sliceno=0", "encryp=none"],
>    "id": "291687c0293354a642e3eadf"
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
>        "address": "0x2c8e94bbe17cec95f21dfdb55e334cfd4effcd9d",
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
