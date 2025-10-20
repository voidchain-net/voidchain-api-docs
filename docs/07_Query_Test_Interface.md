## Query and Test Interface

------------------------------------------------------------------------------------------

#### Query and Test Interface

<details>
 <summary><code>POST</code> <code><b>chain_queryTransaction</b></code> <code>(Test transaction execution)</code></summary>

**Interface Purpose:**
- Test transactions are executed in a single machine trial to decide whether to actually submit the transaction to the network based on the returned results.
- Query result operations are uniformly executed through the trial interface, which can return results immediately without gas fees.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | from      |  required | string                  | Sender address  |
> | to        |  required | string                  | Receiver address  |
> | value     |  required | string (hex)            | Transaction value  |
> | sliceno   |  required | string (hex)            | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"ret_data":"...","err":"..."}`                                    |

**Response Fields:**
- **ret_data** - Transaction execution return value (hex encoded)
- **err** - Transaction execution return error

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryTransaction",
>    "params": [{
>      "from": "0xc3b6472d6370eaf4eb58fff19ce1724c9d61892c",
>      "to": "0x6268af5542c4b0ccbb650a0aaccbfcdfbabf6b52",
>      "value": "0x2E90EDD00",
>      "sliceno": "0x2"
>    }, "", "encryp=none"],
>    "id": "d2c8fe196f9f8d8ace952e9e"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "055169b80c4e2ef96c2b2cbb",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "ret_data": "",
>        "err": ""
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
