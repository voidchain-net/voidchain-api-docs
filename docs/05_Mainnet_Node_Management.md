## Mainnet Node Management

------------------------------------------------------------------------------------------

#### Configure Management Password

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Set management password)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | pass      |  required | string                  | Original password  |
> | newpass   |  required | string                  | New password  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Success message                                                     |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["updateTmac","op=setpass&pass=&newpass=123","encryp=none"],
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
>      "content": "setpass successful"
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Exit Vacuum Network

<details>
 <summary><code>POST</code> <code><b>chain_queryInfo</b></code> <code>(Exit vacuum network for remote maintenance)</code></summary>

After exiting the vacuum network, you can perform remote maintenance on the mainnet node via SSH.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | pass      |  required | string                  | Password  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Success message                                                     |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_queryInfo",
>    "params": ["updateTmac","op=stop&pass=123","encryp=none"],
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
>      "content": "StopMac Successful! and Maintain through SSH connection"
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
