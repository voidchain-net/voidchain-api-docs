## Static Metaspace

------------------------------------------------------------------------------------------

#### Apply for Static Metaspace

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Apply for static metaspace)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number (0 for main metaspace)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

**Response Fields:**
- **Txhash** - Transaction hash

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=slice&subcode=applyStaticSlice&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "1726b2be8fef1ec6fa30ada2",
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

#### Get Metaspace Genesis Block

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Get genesis block content)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Genesis block content                                               |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=slice&subcode=getgenesis&sliceno=100", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "eb5c92f61656b259603a3ebe",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "config": {
>          "chainId": 100
>        },
>        "gasLimit": "0xffffffff",
>        "nonce": "0x0",
>        "timestamp": "0x0",
>        "alloc": {
>          "0x8236760883F693Ca6240098cFAEF42E4b76ad214": {
>            "balance": "0x0",
>            "content": "Dynamic sharding"
>          }
>        }
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Confirm Metaspace Validity

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Check metaspace validity)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | Metaspace type (1 - dynamic metaspace, other - static metaspace)  |
> | no        |  required | int                     | Metaspace number  |
> | sliceno   |  required | int                     | Metaspace number (0 for main metaspace)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Validity status                                                     |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=slice&subcode=checkslice&type=1&no=10000&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Dynamic Metaspace Query

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query dynamic metaspace information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | begin     |  required | int                     | Starting metaspace number  |
> | len       |  required | int                     | Number of metaspaces to query  |
> | sliceno   |  required | int                     | Metaspace number (0 for main metaspace)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | List of metaspace numbers and applicant addresses                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=slice&subcode=querySliceInfo&begin=0&len=1&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Deploy TRC100 Base Contract

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Deploy TRC100 base contract)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Deployment result                                                   |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=trc100&subcode=init&sliceno=10005", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Configure Incentive Token

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Set incentive token contract)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address   |  required | string                  | Contract incentive code  |
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Configuration result                                                |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=setCoinbase&address=0x...&sliceno=100", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Incentive Contract Query

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query incentive contract)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Incentive contract address                                          |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=coinbaseOf&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

### Node Management

#### Add Node

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Add a node)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | mark      |  required | string                  | First 24 characters of node ID  |
> | content   |  required | string                  | Node description  |
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Operation result                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=addnode&mark=&content=&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Batch Add Nodes

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Batch add nodes)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | file1     |  required | string                  | Full path, node information saved in separate lines in document  |
> | begin     |  required | int                     | Starting position  |
> | len       |  required | int                     | Number of entries  |
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Operation result                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=addnodes&file1=&begin=&len=&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Delete Node

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Delete a node)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | mark      |  required | string                  | First 24 characters of node ID  |
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Operation result                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=delnode&mark=&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Batch Delete Nodes

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Batch delete nodes)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | file1     |  required | string                  | Full path, node information saved in separate lines in document  |
> | begin     |  required | int                     | Starting position  |
> | len       |  required | int                     | Number of entries  |
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Operation result                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=delnodes&file1=&begin=&len=&sliceno=10000", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Nodes

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query node information)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | begin     |  required | int                     | Starting sequence number  |
> | len       |  required | int                     | Number of entries  |
> | sliceno   |  required | int                     | Target metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Node list                                                           |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=static&subcode=nodeinfo&begin=&len=&sliceno=10001", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

</details>

------------------------------------------------------------------------------------------
