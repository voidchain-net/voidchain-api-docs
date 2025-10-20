## Proposal Management Interface

------------------------------------------------------------------------------------------

#### TRC100 Address Query

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query TRC100 contract addresses)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | TRC100 contract addresses                                           |

**Returns the minimum TC holdings required for voting rights and proposal submission.**

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=trc100Addr&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "85c42ddbd83c301a0f1bdfc0",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "trc_100_root_addr": "0x2bff1665aef450f0d5a2681f5b2f3a5df00633a0",
>        "trc_100_addr": "0x8d5dd47712a9d4c7ebcb570498a30407fda9a19a",
>        "slice_addr": "0xb2b60dabde3f9acc042528d2665237ac36e23a2e",
>        "lock_addr": "0xeb93cc79834ff35f48d69324476c5c573dc2cdab",
>        "propose_addr": "0x1bd1c092d49548cceb295cf9d0e351c6489fb059",
>        "static_addr": "0x23ee58b0e6cca745a633ae9b4eaa87929b55c803",
>        "cross_addr": "0xc4bb216db77ea104bba866fd535456ce9bd65d2f"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Proposal Permission

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query proposal permission)</code></summary>

Participating in proposals will register the proposer's information in the proposal system.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Permission limits                                                   |

**Returns the minimum TC holdings required for voting rights and proposal submission.**

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=confiminfo&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "0549ba3bcd009e224f07e837",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "LimitVote": 30000,
>        "LimitSubmit": 50000
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Submit Proposal

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Submit proposal)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | address   |  required | string                  | Proposal content storage address  |
> | mark      |  required | string                  | Content hash  |
> | type      |  required | int                     | Proposal type (see below)  |
> | days      |  required | int                     | Voting valid days  |
> | sliceno   |  required | int                     | Metaspace number  |

**Proposal Types:**
- `0` - Foundation, community, public and private fundraising and other platform token pool (no private key) transfer proposal
- `1` - Gas price adjustment proposal
- `2` - Mainnet code upgrade proposal
- `3` - Self-contract upgrade proposal
- `4` - Token incentive miner proposal
- `5` - Agree metaspace proposal

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=submitpropose&address=0x...&mark=&type=&days=7&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
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
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Vote

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Vote on proposal)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | Proposal type (0-5, same as submit proposal)  |
> | optype    |  required | int                     | Vote intention (1 - agree, 2 - reject)  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=voteing&type=0&optype=1&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
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
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Execute Proposal

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Execute proposal)</code></summary>

Can only be submitted after the proposal deadline has passed. Once submitted, whether successful or failed, the proposal will be cleared.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | Proposal type  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=runpropose&type=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
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
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Proposal

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query proposal details)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | Proposal type (0-5)  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Proposal details                                                    |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=queryPropose&type=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "53d8f08dbd01b459f83d3101",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "Submit": "0x35f4646842fc5fe208b7d3fab125c8542be88324",
>        "Status": false,
>        "No": 4,
>        "ContentAddr": "0x22d728a900c13800f19d31f300c4ad65576c4200",
>        "Mark": "00c13800f19d31f300c4ad65576",
>        "Days": 7,
>        "Timeval": 1727226885526038300,
>        "VoteStatus": false
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Delete Proposal

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Delete proposal)</code></summary>

**Note:** Only the proposal initiator can delete the proposal.

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | Proposal type (0-5)  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"txhash":"..."}`                                                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=removePropose&type=0&sliceno=0", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
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
>        "txhash": "0x6885997ca51fa08ffded573088b0c5c294652ec842ac7f3182d32e30ce261025"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Query Vote Information

<details>
 <summary><code>POST</code> <code><b>chain_tvm</b></code> <code>(Query voting results)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | type      |  required | int                     | Proposal type (0-5)  |
> | sliceno   |  required | int                     | Metaspace number  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Vote statistics                                                     |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_tvm",
>    "params": ["opcode=propose&subcode=queryVote&type=0&sliceno=0", "encryp=none"],
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
>        "Pass": 1,
>        "Disagree": 0,
>        "PassTC": 523843176,
>        "DisagreeTC": 0
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
