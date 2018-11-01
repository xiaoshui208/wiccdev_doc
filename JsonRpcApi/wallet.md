
### encryptwallet
### walletpassphrase
### walletlock
### walletpassphrasechange
### dumpwallet
### importwallet

---

### encryptwallet
Encrypts the wallet with passphrase.

**Parameters**
1. passphrase, String - 本钱包加密的密码

**Returns**

encrypt, Boolean - 钱包加密是否成功

**Example**

```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"encryptwallet","params":["12345678"]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result": 
  {
    "encrypt":true
  },
  "error": null,
  "id": "curltext"
}
```


---


### walletpassphrase
Stores the wallet decryption key in memory for<timeout> seconds.

**Parameters**
1. passphrase, String - 本钱包加密的密码
2. timeout, Integer - 解密的时间,单位为秒

**Returns**

passphrase, Boolean - 修改密码是否成功 

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"registaccounttxraw","params":[10000,1284730,"031b52a8c4018bb8327c955e064c591b9992c84a305ba8c5ca2cb520290e594a9f"]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  {
    "rawtx":"0201cdb37a21031b52a8c4018bb8327c955e064c591b9992c84a305ba8c5ca2cb520290e594a9f00cd10463044022039d4769e2a541b3d06f1882ce092d49a63261e5eeca01de4d34bff53ccaefc890220376aebc33e7758585c72efa947f6ae1feb0560f440f6686bdf88a9bb3c04f873"
  },
  "error":null,
  "id":"curltext"
}
```


---


### walletlock
Removes the wallet encryption key from memory, locking the wallet. After calling this method, you will need to call walletpassphrase again before being able to call any methods which require the wallet to be unlocked.

**Parameters**

none

**Returns**

walletlock, Boolean - 是否锁定成功 

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"walletlock","params":[]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result": 
  {
    "walletlock":true
  },
  "error": null,
  "id": "curltext"
}

```

---


### walletpassphrasechange
Changes the wallet passphrase from <oldpassphrase> to <newpassphrase>.

**Parameters**
1. oldpassphrase, String - old passphrase
2. newpassphrase, String - new passphrase

**Returns**

chgpwd, Boolean - 密码是否修改成功

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"walletpassphrasechange","params":["123456789","1234567890"]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result": 
  {
    "chgpwd":true
  },
  "error": null,
  "id": "curltext"
}
```

---


### dumpwallet
Dumps all wallet keys in a human-readable format.And write to <filename>

**Parameters**
1. filename, String - the filename to dump wallet

**Returns**

info, String - 导出钱包的结果信息
key size, String - 导出钱包中包含的账号数量

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"dumpwallet","params":["walletfilename"]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result": 
  {
    "info":"dump ok",
    "key size":14
  },
  "error": null,
  "id": "curltext"
}

```

---


### importwallet
Import keys from a wallet dump file (see dumpwallet).

**Parameters**
1. filename, String - the filename from a wallet dump file

**Returns**

imorpt key size, String - 导入钱包中包含的账号数量

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"importwallet","params":["walletfilename"]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result": 
  {
    "imorpt key size":14
  },
  "error": null,
  "id": "curltext"
}


```