

### getblockcount
### getblockhash
### getblockchaininfo
### getblock

---


### getblockcount
Returns the number of blocks in the longest block chain.

**Parameters**

none

**Returns**

result, Integer - 最新的区块高度

**Example**

```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"getblockcount"}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":1284292,
  "error": null,
  "id": "curltext"
}
```

---


### getblockhash
Returns hash of block in best-block-chain at <index>;index 0 is the genesis block

**Parameters**

index, Integer - Block height

**Returns**

result, Integer - 最新的区块高度

**Example**

```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"getblockhash","params":[1284292]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
    "result":
    {
        "hash":"c4d4886eb31a54609306362dabdb8e59165957b0afb1900c3cf2234211ff39f7"
    },
    "error":null,
    "id":"curltext"
}
```

---


### getblockchaininfo
Returns an object containing various state info regardingblock chain processing.

**Parameters**

none

**Returns**

1. chain, String - main(主链) or testnet(测试链)
2. blocks, Integer - 区块链最新高度
3. bestblockhash, String - TAB
4. verificationprogress, BigDecimal - TAB
5. chainwork, String - TAB

**Example**

```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"getblockchaininfo"}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
    "result":
    {
        "chain":"main",
        "blocks":1284655,
        "bestblockhash":"cbfda69d79ec829a399d78242824f5338a6980e850ef323239ca0f6afeace2fa",
        "verificationprogress":1.00000000,
        "chainwork":"0000000000000000000000000000000000000000000000000000000000139a2f"
    },
    "error":null,
    "id":"curltext"
}
```



---


### getblock
Returns information about the block with the given hash orindex. If verbose is true,return a json object, false return the hex encoded data

**Parameters**
1. hash, String - 区块hash
   (,or)index, Integer - 区块高度
2. verbose, Boolean (Optional) - 区块显示选项，如果是true,则显示区块json数据详情，如果是fasle,则显示 区块信息 16进制编码的数据，所以对于一般用户，请直接不填这个参数。

**Returns**

1. hash, String - the block hash (same as provided)
2. confirmations, numeric - The number of confirmations
3. size, numeric - The block size
4. height, numeric - The block height or index
5. version, numeric - The block version
6. merkleroot, String - The merkle root
7. txnumber, numeric - The transaction number
8. tx, array of string:
​     transactionid, String - The transaction id
9. time, numeric - The block time in seconds since epoch (Jan 1 1970 GMT)
10. nonce, numeric - The nonce
11. difficulty, numeric - The difficulty
12. previousblockhash, String - The hash of the previous block
13. nextblockhash, String - The hash of the next block

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getblock", "params": [246412] }' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":1284292,
  "error": null,
  "id": "curltext"
}

{
    "result":
    {
        "hash":"f700adb00ef9fa652b242698eae6c3f5066b6f1e8f6cb1f52d8683a6811e48fe",
        "confirmations":11,
        "size":174,
        "height":246412,
        "version":1,
        "merkleroot":"d38e093bec35d86cf0e715689c7a41adeadb06db59169fa082da26dea71448f5",
        "txnumber":1,
        "tx":["d38e093bec35d86cf0e715689c7a41adeadb06db59169fa082da26dea71448f5"],
        "time":1540461840,
        "nonce":191,
        "chainwork":"000000000000000000000000000000000000000000000000000000000003c28c",
        "fuel":0,
        "fuelrate":1,
        "previousblockhash":"b4bf3e6238ecaea8f616074481851fd6e18858c93dfdc16f28ee9c9075d0ea13","nextblockhash":"f2c2aa3491619bc8985c7398b6695919443d97db2e38d672240a1f16a94cd437"
    },
    "error":null,
    "id":"curltest"}

```

---

