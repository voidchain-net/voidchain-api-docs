## Cross-chain Circulation

------------------------------------------------------------------------------------------

#### Cross-chain Transfer Out

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Transfer assets out to another metaspace)</code></summary>

##### Parameters

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address     |  optional | string                  | Contract address (if platform asset TC, parameter is empty)  |
> | value       |  required | string (hex)            | Transfer asset quantity  |
> | destsliceno |  required | int                     | Receiving asset metaspace number  |
> | sliceno     |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Operation result                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=cross&subcode=transsend&address=&value=0x12&sliceno=10000&destsliceno=199", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Cross-chain Transfer In

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Receive transferred assets from another metaspace)</code></summary>

##### Parameters

> | name        |  type     | data type               | description                                                           |
> |-------------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sender      |  required | string                  | Transfer-out address  |
> | nonce       |  required | string                  | Transfer transaction identifier  |
> | address     |  optional | string                  | Contract address (if platform asset TC, parameter is empty)  |
> | value       |  required | string (hex)            | Transfer asset quantity  |
> | sousliceno  |  required | int                     | Transfer-out transaction original metaspace number  |
> | sliceno     |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Operation result                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=cross&subcode=transrecv&sender=0x...&nonce=&address=&value=0x12&sliceno=10000&sousliceno=199", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------
