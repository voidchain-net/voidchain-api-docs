## Other Utilities

------------------------------------------------------------------------------------------

#### Get Content MD5

<details>
 <summary><code>POST</code> <code><b>chain_queryMd5</b></code> <code>(Calculate MD5 hash)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | content   |  optional | string                  | Get MD5 of content (base64 encoded)  |
> | file1     |  optional | string                  | Get MD5 of file content (complete file path)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - MD5 hash string

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryMd5",
>    "params": ["opcode=Other&subcode=Md5&content=&file1=", "encryp=none"],
>    "id": "7711b09d8b112406b4492e05"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1208117ccdc1b3975305901b",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "202cb962ac59075b964b0715"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Machine Code

<details>
 <summary><code>POST</code> <code><b>chain_queryHardId</b></code> <code>(Get hardware ID)</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Machine code string

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryHardId",
>    "params": [""],
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
>        "info": "37e4cb5903503f3c6d4f5a88"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
