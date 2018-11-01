

### listaddr
### getnewaddress
### registaccounttx
### registaccounttxraw
### sendtoaddress
### sendtoaddresswithfee
### sendtoaddressraw
### getaccountinfo
### getbalance



---


### listaddr
Return Array containing address,balance,haveminerkey,regidinformation.

**Parameters**

none

**Returns**

rawtx, String - 创建交易签名产生的签名字段 

**Example**
```json
// Request 
curl -v -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"listaddr"}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  [
    {
      "addr":"WR4fyUnQKhrxgXuMnjMCea6TNjK29GgHnY",
      "balance":0.00000000,
      "haveminerkey":false,
      "regid":" "
    },
    {
      "addr":"WWnVCpn9j1udKcXFeHzPs55FL7yy7LYDSq",
      "balance":0.00000000,
      "haveminerkey":false,
      "regid":" "
    }
  ],
  "error":null,
  "id":"curltext"
}
```

---


### getnewaddress
Returns a new  address for receiving payments. If [isminer] is ture will create aminer key,otherwise will only return a new address.

**Parameters**

isminer, Boolean - 是否为旷工，(选填，建议一般用户不要填写，若不填，默认为fasle）

**Returns**

addr, String - 维基币地址
minerpubkey, String - 旷工pubkey,如果没有旷工pubkey，则为no

**Example**
```json
// Request
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","method":"getnewaddress","params":[],"id":174633286}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  {
    "addr":"wb5QZWr7PpTsoL6wBYsojfM3G4yaD5x1yA",
    "minerpubkey":"no"
  },
  "error":null,
  "id":174633286
}
```

---


### registaccounttx
register secure account

**Requires unlocked wallet**

Y

**Parameters**
1. address, String - 需要激活的地址
2. fee, Long - 激活使用的小费，带了10的8次方小数位

**Returns**

hash, String - 交易hash 

**Example**
```json
// Request
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"registaccounttx","params":["WR4fyUnQKhrxgXuMnjMCea6TNjK29GgHnY",1000000]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "hash" : "b93c02997cb71210b9b25969247416a7d31bd803526078f247db4624c14ed340"
}
```


---


### registaccounttxraw

create a register account transaction

**Requires unlocked wallet**

Y

**Parameters**
1. fee, BigInteger - 激活使用的小费，带了10的8次方小数位
2. height, BigInteger - 激活时的区块高度
3. publickey, String - 激活账户的公钥
4. minerpublickey， String 

**Returns**

hash, String - 交易hash 

**Example**
```json
// Request
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"registaccounttx","params":["WR4fyUnQKhrxgXuMnjMCea6TNjK29GgHnY",1000000]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "hash" : "b93c02997cb71210b9b25969247416a7d31bd803526078f247db4624c14ed340"
}
```


---


### sendtoaddress

Send an amount to a given address. The amount is a real andis rounded to the nearest 0.00000001. Returns the transaction ID <txhash>if successful.

**Parameters**
1. src address, String - 发送方地址（Optional），
2. recv address, String - 接收方地址
3. amout, BigInteger - 发送金额 （实际发送金额乘以10的8次方）

**Returns**

hash, String - 交易hash 

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","method":"sendtoaddress","params":["wTwrWser78mEa22f8mHfiHGrdKysTv8eBU","wXscdWVUN9irrLGvJJDZiaBoKXvat6Pqa9",1000000000],"id":168141569}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  {
    "hash":"c8260a08723192c74fb2025093bb876e6532baa5af952e6f7758a40c7f61c81f"
  },
  "error":null,
  "id":168141569
}
```

---


### sendtoaddresswithfee

Send an amount to a given address. The amount is a real andis rounded to the nearest 0.00000001. Returns the transaction ID <txhash>if successful.

**Parameters**
1. src address, String - 发送方地址（Optional）
2. recv address, String - 接收方地址
3. amout, BigInteger - 发送金额 （实际发送金额乘以10的8次方）
4. fee， BigInteger - 转账的小费 （实际转账的小费乘以10的8次方）

**Returns**

hash, String - 交易hash 

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","method":"sendtoaddress","params":["wTwrWser78mEa22f8mHfiHGrdKysTv8eBU","wXscdWVUN9irrLGvJJDZiaBoKXvat6Pqa9",1000000000,10000],"id":168141569}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  {
    "hash":"c8260a08723192c74fb2025093bb876e6532baa5af952e6f7758a40c7f61c81f"
  },
  "error":null,
  "id":168141569
}
```

---


### sendtoaddressraw

Send an amount to a given address. The amount is a real andis rounded to the nearest 0.00000001. Returns the transaction ID <txhash>if successful.

**Parameters**
1. src address, String - 发送方地址（Optional）
2. recv address, String - 接收方地址
3. amout, BigInteger - 发送金额 （实际发送金额乘以10的8次方）
4. fee， BigInteger - 转账的小费 （实际转账的小费乘以10的8次方）

**Returns**

rawtx, String - 创建交易签名产生的签名字段 

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","method":"sendtoaddressraw","params":[10000,100000,"wTwrWser78mEa22f8mHfiHGrdKysTv8eBU","wXscdWVUN9irrLGvJJDZiaBoKXvat6Pqa9",243038],"id":403309340}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  {
    "rawtx":"03018de95e0480c855010486db2601cd10858c20004630440220733eb4610e5cbb599ef409fd871cb1a999af2743f4d87b2c1f8e792c0c901f3a022000ce48fea9250faf25cc6a4bf19ec098a249a4f89116e2f033e60921c26fef55"
  },
  "error":null,
  "id":403309340
}
```

---


### getaccountinfo

Returns the account information  with the given address.

**Parameters**
1. address, String - 维基币地址

**Returns**

1. Address, String - 维基币地址
2. KeyID, String - 维基币公钥两次sha之后得到的pubKeyHash
3. RegID, String - 维基币地址对应的激活id号
4. PublicKey, String - 维基币地址公钥
5. MinerPKey, String - 旷工的Key (一般用户可以忽略该字段)
6. Balance, BigInteger - 维基币地址的余额,(实际金额乘以10的8次方）
7. Votes, BigInteger - 投票数量（涉及Dpos投票的参数）
8. UpdateHeight， BigInteger - TAB (一般用户可以忽略该字段)
9. voteFundList, ArrayList - 投票列表，
10. postion, String - 所在位置，（如果没有激活则是inwallet，如果激活了这是在inblock)

**Example**
```json
// Request 
curl -u wikichain:admin --data-binary '{"jsonrpc":"2.0","method":"getaccountinfo","params":["wTMrkcgbfFWEWQxBs1XHvGgyTkd5JenQxP"],"id":440924659}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result":
  {
    "Address":"wTMrkcgbfFWEWQxBs1XHvGgyTkd5JenQxP",
    "KeyID":"54cf13450d208867450785fca1ccba78813a9028",
    "RegID":"131232-1",
    "PublicKey":"02dae8a12b4b02da6d8bad5d2b04ac23fa8709fbf1016abb4cbed8303a695ab4d5",
    "MinerPKey":"",
    "Balance":499889929,
    "Votes":0,
    "UpdateHeight":0,
    "voteFundList":[],
    "postion":"inblock"
  },
  "error":null,
  "id":440924659
}

```

---


### getbalance

Returns the account information  with the given address.

**Parameters**
1. address, String - 本钱包里维基币地址 (Optional, 若不填写则为本钱包内所有余额)

**Returns**

Balance, BigDecimal - 维基币地址的余额,(该值为实际金额，没有乘以10的8次方) 

**Example**
```json
// Request 
curl -v -u wikichain:admin --data-binary '{"jsonrpc":"2.0","id":"curltext","method":"getbalance","params":["WR4fyUnQKhrxgXuMnjMCea6TNjK29GgHnY"]}' -H 'content-type:application/json;' http://127.0.0.1:6968

// Response
{
  "result": 
  {
    "balance": 1.00000000
  },
  "error": null,
  "id": "curltext"
}

```

**Comment**

该方法只能查询本钱包地址，而且改地址必须要有金额转入的记录时才能查询， 查询账号信息时尽量使用 getaccountinfo 方法

