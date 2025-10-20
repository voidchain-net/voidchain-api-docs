## Wallet Lock Interface

------------------------------------------------------------------------------------------

#### Lock Wallet

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Lock wallet)</code></summary>

Wallet locking is a self-operated action by the wallet owner, committing that received tokens will be released according to the locking rules.  
Cannot be locked repeatedly. If already locked, the lock button should be grayed out.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | nums      |  required | int                     | Token quantity  |
> | begin     |  required | int                     | Start date  |
> | days      |  required | int                     | Locked days  |
> | type      |  required | int                     | Lock type (0 - daily release, 1 - release at maturity)  |
> | sliceno   |  required | int                     | Metaspace number  |

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
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=lock&nums=123&begin=12345678&days=1&type=0&sliceno=0", "encryp=none"],
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
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Lock Information

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Query wallet lock information)</code></summary>

Wallet locking is a self-operated action by the wallet owner, committing that received tokens will be released according to the locking rules.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | addr      |  required | string                  | Query lock information of corresponding address  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Lock details                                                        |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["pubChainQuery","op=querylock&addr=0x...&sliceno=0","encryp=none"],
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
>        "Addr": "0x35f4646842fc5fe208b7d3fab125c8542be88324",
>        "Nums": 10000000000,
>        "Begin": 1711036800,
>        "Days": 48,
>        "LType": 0
>      }
>    }
>  }
> ```

**Field Description:**
- **Addr** - Locked address
- **Nums** - Quantity (divide by 9 zeros, keep 2 decimal places)
- **Begin** - Start date
- **Days** - Number of days (UI can calculate the end date)
- **LType** - Type (0 - linear release, 1 - release at maturity)

</details>

------------------------------------------------------------------------------------------

#### Unlock

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Unlock wallet)</code></summary>

Unlock can only be performed after the deadline.  
Before submitting unlock: must check if the deadline has passed, otherwise directly return unlock failure information.  
If the deadline has not passed, the unlock button should be grayed out.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | None      |  N/A      | N/A                     | No parameters required  |

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
>    "method": "chain_tvm",
>    "params": ["opcode=token&subcode=unlock", "encryp=none"],
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
>      "content": {
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
