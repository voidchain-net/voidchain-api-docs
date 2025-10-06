## Login and Registration

**Request Format Description:**
- **D_Encryption** - Encryption method: rsa, pass, none. Use rsa encryption before successful login, use pass encryption after successful login.
- **Special Note:** If browser support is needed, you need to start an https server proxy locally to access the local trust machine interface through proxy, so the front end can use none mode communication without encryption.
- **D_Session** - The session ID returned from the first connection. All subsequent communications must include this ID to be recognized as the same connection.
- **Note:** In the documentation, all keywords starting with "D_" followed by an underscore are defined keywords that need to be replaced with corresponding definitions, which will not be explained one by one later.

------------------------------------------------------------------------------------------

#### Session ID

<details>
 <summary><code>POST</code> <code><b>chain_getKey</b></code> <code>(Get encryption public key)</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"session":"...","pubkey":"..."}`                                  |

**Response Fields:**
- **Session** - Subsequent connection session ID
- **pubkey** - Server-assigned communication public key for current connection

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_getKey",
>    "params": [],
>    "id": 1
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": 1,
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "session": "5cbb9dab5678e998670e9e61",
>        "pubkey": "q\r\nHQIDAQAB\r\n"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Register

<details>
 <summary><code>POST</code> <code><b>chain_register</b></code> <code>(Register account)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Registration account  |
> | pass      |  required | string                  | Password  |
> | refer     |  optional | string                  | Referrer (can be empty)  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"address":"...","txhash":"..."}`                                  |

**Response Fields:**
- **address** - Account address returned upon successful registration
- **txhash** - Transaction ID of current registration transaction

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_register",
>    "params": ["opcode=Account&subcode=Regsiter&account=wxl_test&pass=12345678&refer=", "encryp=none"],
>    "id": "5cbb9dab5678e998670e9e61"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "5cbb9dab5678e998670e9e61",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "address": "0x4a33283583fD797E42e9cB724fe01c09173Fc2db"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Login

<details>
 <summary><code>POST</code> <code><b>chain_logon</b></code> <code>(Login)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Account  |
> | pass      |  required | string                  | Password  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Account address returned after successful login

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_logon",
>    "params": ["opcode=Account&subcode=Logon&account=wxl_test&pass=12345678", "encryp=none"],
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
>        "info": "0x07fed20ff62d2082fd2da3c5e09b98b462b43d98"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Import Mnemonic

<details>
 <summary><code>POST</code> <code><b>chain_importKey</b></code> <code>(Import mnemonic)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Account  |
> | pass      |  required | string                  | Password  |
> | content   |  required | string                  | Mnemonic base64 encoded  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"address":"...","txhash":"..."}`                                  |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_importKey",
>    "params": ["opcode=Mnemonic&account=wxl_tellbiot1&pass=12345678&content=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "5cbb9dab5678e998670e9e61",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "address": "0x4a33283583fD797E42e9cB724fe01c09173Fc2db",
>        "txhash": "0xdaa7d74ac328fb0c0797e0be0745c2de9086ffb9c50948f2a726db180436bcc8"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Import Account Password

<details>
 <summary><code>POST</code> <code><b>chain_importKey</b></code> <code>(Import account)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Account  |
> | pass      |  required | string                  | Password  |
> | file1     |  required | string                  | First part of private key  |
> | file2     |  required | string                  | Second part of private key  |

**Note:** The order can be reversed, the backend will automatically recognize.

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Account address returned after successful import

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_importKey",
>    "params": ["opcode=Account&subcode=import&account=wxl_tellbiot1&pass=12345678&file1=&file2=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "06f050760369f78ec576c714",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "0x07fed20ff62d2082fd2da3c5e09b98b462b43d98"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Import Keystore

<details>
 <summary><code>POST</code> <code><b>chain_importKeystore</b></code> <code>(Import keystore file)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Account  |
> | pass      |  required | string                  | Password  |
> | file1     |  required | string                  | Keystore file, compatible with Ethereum accounts  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"address":"...","txhash":"..."}`                                  |

**Response Fields:**
- **address** - Account address returned after successful import

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_importKeystore",
>    "params": ["opcode=Account&subcode=importkey&account=test_tellbiot1&pass=12345678&file1=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "5cbb9dab5678e998670e9e61",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "address": "0x4a33283583fD797E42e9cB724fe01c09173Fc2db",
>        "txhash": "0xdaa7d74ac328fb0c0797e0be0745c2de9086ffb9c50948f2a726db180436bcc8"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Change Password

<details>
 <summary><code>POST</code> <code><b>chain_importPass</b></code> <code>(Change password)</code></summary>

##### Parameters

> | name      |  type     | data type               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | account   |  required | string                  | Account  |
> | pass      |  required | string                  | Current password  |
> | newpass   |  required | string                  | New password  |
> | file1     |  required | string                  | First part of private key  |
> | file2     |  required | string                  | Second part of private key  |

**Note:** The order can be reversed, the backend will automatically recognize.

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Account address returned after successful password change

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_importPass",
>    "params": ["opcode=Account&subcode=importpass&account=wxl_tellbiot1&pass=12345678&newpass=12345678&file1=&file2=", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "9027c8a66fc56aef90cb960a",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "0x07fed20ff62d2082fd2da3c5e09b98b462b43d98"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Export Account Password

<details>
 <summary><code>POST</code> <code><b>chain_exportKey</b></code> <code>(Export account private key)</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"file1":"...","file2":"..."}`                                     |

**Response Fields:**
- **file1** - First part of private key
- **file2** - Second part of private key

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_exportKey",
>    "params": ["opcode=Account&subcode=export", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "6b02424abc41bae813eb92ac",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "file1": "...",
>        "file2": "..."
>      }
>    }
>  }
> ```

**Note:** Save account, password, file1 content and file2 content separately. All four parts must be complete for import.

</details>

------------------------------------------------------------------------------------------

#### Export Keystore

<details>
 <summary><code>POST</code> <code><b>chain_exportKeystore</b></code> <code>(Export keystore)</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Base64 encrypted keystore content

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_exportKeystore",
>    "params": ["opcode=Account&subcode=exportkey", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "6b02424abc41bae813eb92ac",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "eyJhZGRy......"
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Export Mnemonic

<details>
 <summary><code>POST</code> <code><b>chain_exportKeystore</b></code> <code>(Export mnemonic)</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | `{"info":"..."}`                                                    |

**Response Fields:**
- **info** - Base64 encrypted mnemonic content

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_exportKeystore",
>    "params": ["opcode=Account&subcode=exportMnem", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "2ec689ba8b07f98ed9e6b504",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": {
>        "info": "cGxlYXNlIGF0aGxldGUgaGVhdnkgYXVndXN0IHRydXRoIHJvYXN0IG1pcmFjbGUgc3Ryb25nIGVsYm93IGRpc21pc3Mgc3BlbGwgY2hpY2tlbg=="
>      }
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------

#### Logout

<details>
 <summary><code>POST</code> <code><b>chain_logout</b></code> <code>(Logout)</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `0`           | `application/json`                | Success confirmation                                                |

##### Example cURL

> ```javascript
>  {
>    "jsonrpc": "3.0",
>    "method": "chain_logout",
>    "params": ["opcode=Account&subcode=Logout", "encryp=none"],
>    "id": "aa80aa0c6bb0c7d81ac7e5b3"
>  }
> ```

##### Response Example

> ```json
>  {
>    "jsonrpc": "3.0",
>    "id": "2ec689ba8b07f98ed9e6b504",
>    "result": {
>      "ret": "0",
>      "err": "",
>      "content": ""
>    }
>  }
> ```

</details>

------------------------------------------------------------------------------------------
