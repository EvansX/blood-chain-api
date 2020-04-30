# 血液链浏览器
## 概要说明
血液链浏览器后台服务接口文档
## 接口说明
- url：全局的参数url为请求的http地址，例如http://127.0.0.1
- port：全局的参数url为请求的端口号，例如8000
- code：返回码，为0表示请求接口返回成功
- message：返回信息，为'success'代表成功
- data：返回的数据

### 1. 区块信息接口block
#### 1.1 getBlockByNumber

**接口描述**

根据区块高度获取区块信息

**接口url**

/mgr/block/getBlockByNumber/:groupID/:blockNumber

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 区块高度 |blockNumber  |string  | 是 | 区块高度十六进制形式 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/block/getBlockByNumber/1/0x8
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "dbHash": "0x7c39fcba6712e15a97a41cf9ad41bdd3c9ffc1a213ef06c510bc30f52f3e3bf1",
        "extraData": [],
        "gasLimit": "0x0",
        "gasUsed": "0x0",
        "hash": "0x3e74682ba88b01e6c3e824d4d4c3d3d3d04d402641e6d791021a733c0b55c3f8",
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "number": "0x8",
        "parentHash": "0x5cf76b1ff466eca364ae20f01073b2346232184861c6f3b9b25c78c578f07e57",
        "receiptsRoot": "0xd0c7c164ef9ac70221bb1d74914cc1b1bdf1b002fb50be7c0aa55a17fca0209a",
        "sealer": "0x1",
        "sealerList": [
            "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
            "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
            "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
            "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
            "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
            "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489"
        ],
        "stateRoot": "0x7c39fcba6712e15a97a41cf9ad41bdd3c9ffc1a213ef06c510bc30f52f3e3bf1",
        "timestamp": "0x1715416fb7d",
        "transactions": [
            {
                "blockHash": "0x3e74682ba88b01e6c3e824d4d4c3d3d3d04d402641e6d791021a733c0b55c3f8",
                "blockNumber": "0x8",
                "from": "0x5cf6c007effc5b3193d22f6ec34b9bb963237f7d",
                "gas": "0x419ce0",
                "gasPrice": "0x51f4d5c00",
                "hash": "0xd5d5ce05f3824c1a5c3f75e475bd16fc25123e4e3f4756ed9cd743b139ce1692",
                "input": "xxxxxxxxxxxxxxxxxxxxxxxxxx",
                "nonce": "0x39f605faaac198e8c89f7eda9ac147a0c2a6bc3b5ecd0a4a91aa3696b1bfd7e",
                "to": "0x0000000000000000000000000000000000001004",
                "transactionIndex": "0x0",
                "value": "0x0"
            }
        ],
        "transactionsRoot": "0x933cb774c1cf66bfe617163d52409bfc412da9fa86b2dcf83ef8e197acd88091"
    }
}
```
#### 1.2 getBlockByHash

**接口描述**

根据区块哈希获取区块信息

**接口url**

/mgr/block/getBlockByHash/:groupID/:blockHash/:includeTransactions

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 区块哈希 |blockHash  |string  | 是 | 区块哈希 |
| 3 | 是否包含交易信息 |includeTransactions  |bool  | 是 | 是否包含交易信息true、false |

**2）数据格式**
```
{{url}}:{{port}}/mgr/block/getBlockByHash/1/0x3e74682ba88b01e6c3e824d4d4c3d3d3d04d402641e6d791021a733c0b55c3f8/false
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "extraData": [],
        "gasLimit": "0x0",
        "gasUsed": "0x0",
        "hash": "0x3e74682ba88b01e6c3e824d4d4c3d3d3d04d402641e6d791021a733c0b55c3f8",
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
        "number": "0x8",
        "parentHash": "0x5cf76b1ff466eca364ae20f01073b2346232184861c6f3b9b25c78c578f07e57",
        "receiptsRoot": "0xd0c7c164ef9ac70221bb1d74914cc1b1bdf1b002fb50be7c0aa55a17fca0209a",
        "sealer": "0x1",
        "sealerList": [
            "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
            "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
            "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
            "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
            "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
            "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489"
        ],
        "stateRoot": "0x7c39fcba6712e15a97a41cf9ad41bdd3c9ffc1a213ef06c510bc30f52f3e3bf1",
        "timestamp": "0x1715416fb7d",
        "transactions": [
            "0xd5d5ce05f3824c1a5c3f75e475bd16fc25123e4e3f4756ed9cd743b139ce1692"
        ],
        "transactionsRoot": "0x933cb774c1cf66bfe617163d52409bfc412da9fa86b2dcf83ef8e197acd88091"
    }
}
```
#### 1.3 getBlockHashByNumber

**接口描述**

根据区块高度获取区块哈希

**接口url**

/mgr/block/getBlockHashByNumber/:groupID/:blockNumber

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 区块高度 |blockNumber  |number  | 是 | 区块高度 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/block/getBlockHashByNumber/1/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": "0xfcacaed54ef9c604bbd95db9fff4e02f6296b19ed5790bfe544ccec6829cf248"
}
```
#### 1.4 getBlockNumber

**接口描述**

根据群组id获取区块最新高度

**接口url**

/mgr/block/getBlockNumber/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/block/getBlockNumber/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": "0x33f"
}
```
#### 1.5 blockList

**接口描述**

根据群组id获取区块列表

**接口url**

/mgr/block/blockList/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |页码  | page | number |  是| 页码 |
| 3 |行数  | size | number |  是| 每页显示条数 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/block/blockList/1/1/2
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "pkHash": "0x8b2a9b6e9bddf9cfd8640eae81c1ae4304a7d590d4be0daa95b8a3259ddd9212",
            "blockNumber": 831,
            "blockTimestamp": "2020-04-17T18:19:30.000Z",
            "transCount": 1,
            "sealerIndex": 2,
            "sealer": "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
            "createTime": "2020-04-17T18:19:35.000Z",
            "modifyTime": "2020-04-17T18:19:35.000Z"
        },
        {
            "pkHash": "0xa0efdf2d3a6c54b2f578b23b9bfafa6392fe480866d83ecf6697ab7e7e845706",
            "blockNumber": 830,
            "blockTimestamp": "2020-04-17T18:19:29.000Z",
            "transCount": 2,
            "sealerIndex": 1,
            "sealer": "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489",
            "createTime": "2020-04-17T18:19:35.000Z",
            "modifyTime": "2020-04-17T18:19:35.000Z"
        }
    ],
    "totalCount": 832
}
```
### 2. 交易信息接口
#### 2.1 getTransactionByHash

**接口描述**

根据交易哈希获取交易信息

**接口url**

/mgr/getTransactionByHash/:groupID/:transactionHash

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 交易哈希 |transactionHash  |string  | 是 | 交易哈希 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/transaction/getTransactionByHash/1/0x4fa70ba7aedccb4892597a4cb9e66ed3080b1e8327e63ab9201e756dd3eafb39
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "blockHash": "0x8b2a9b6e9bddf9cfd8640eae81c1ae4304a7d590d4be0daa95b8a3259ddd9212",
        "blockNumber": "0x33f",
        "from": "0x6486ce0a319a264ef745c764bcf6085be8c37c95",
        "gas": "0x5f5e100",
        "gasPrice": "0x1",
        "hash": "0x4fa70ba7aedccb4892597a4cb9e66ed3080b1e8327e63ab9201e756dd3eafb39",
        "input": "0x96aade1500000000000000000000000000000000000000000000000000000000000000c000000000000000000000000000000000000000000000000000000000000001000000000000000000000000000000000000000000000000000000000000000140000000000000000000000000000000000000000000000000000000000000018000000000000000000000000000000000000000000000000000000000000001c00000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000000000ce59f8ee8a5bfe58cbbe999a2000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000053134303830000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000e464232303135303132302d303031000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000d3930303238313434303233373400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000845353437343030300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000013323031352d30312d32302030383a32313a333500000000000000000000000000",
        "nonce": "0x23d9b8d387fb8d49e876050bd2f54842c835cd2581b628464d30e44987f1a75",
        "to": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
        "transactionIndex": "0x0",
        "value": "0x0"
    }
}
```
#### 2.2 getTransactionReceipt

**接口描述**

根据交易哈希获取交易回执信息

**接口url**

/mgr/getTransactionReceipt/:groupID/:transactionHash

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 交易哈希 |transactionHash  |string  | 是 | 交易哈希 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/transaction/getTransactionReceipt/1/0x4fa70ba7aedccb4892597a4cb9e66ed3080b1e8327e63ab9201e756dd3eafb39
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "blockHash": "0x8b2a9b6e9bddf9cfd8640eae81c1ae4304a7d590d4be0daa95b8a3259ddd9212",
        "blockNumber": "0x33f",
        "contractAddress": "0x0000000000000000000000000000000000000000",
        "from": "0x6486ce0a319a264ef745c764bcf6085be8c37c95",
        "gasUsed": "0x20072",
        "input": "0x96aade1500000000000000000000000000000000000000000000000000000000000000c000000000000000000000000000000000000000000000000000000000000001000000000000000000000000000000000000000000000000000000000000000140000000000000000000000000000000000000000000000000000000000000018000000000000000000000000000000000000000000000000000000000000001c00000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000000000ce59f8ee8a5bfe58cbbe999a2000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000053134303830000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000e464232303135303132302d303031000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000d3930303238313434303233373400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000845353437343030300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000013323031352d30312d32302030383a32313a333500000000000000000000000000",
        "logs": [
            {
                "address": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
                "data": "0x00000000000000000000000000000000000000000000000000000000000000c000000000000000000000000000000000000000000000000000000000000001000000000000000000000000000000000000000000000000000000000000000140000000000000000000000000000000000000000000000000000000000000018000000000000000000000000000000000000000000000000000000000000001c00000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000000000d393030323831343430323337340000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000084535343734303030000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000ce59f8ee8a5bfe58cbbe999a2000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000053134303830000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000e464232303135303132302d3030310000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000013323031352d30312d32302030383a32313a333500000000000000000000000000",
                "topics": [
                    "0xfd0632e51eeab4dffe03665562b81a1f01dcc2a8375dc8c9bb78032910c5133f"
                ]
            }
        ],
        "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080000000000000000000010000000000000000000000000200000000000000000",
        "output": "0x",
        "root": "0x4b613c67e0ddcfc6fcbc835ebe303b8c4e34f74104e4183441b097a9ec6ce5d3",
        "status": "0x0",
        "to": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
        "transactionHash": "0x4fa70ba7aedccb4892597a4cb9e66ed3080b1e8327e63ab9201e756dd3eafb39",
        "transactionIndex": "0x0"
    }
}
```
#### 2.2 getPendingTransactions

**接口描述**

根据群组id获取正在打包的交易信息

**接口url**

/mgr/getPendingTransactions/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/transaction/getPendingTransactions/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": []
}
```
#### 2.4 getTotalTransactionCount

**接口描述**

获取交易总数

**接口url**

/mgr/transaction/getTotalTransactionCount/1

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
**2）数据格式**
```
{{url}}:{{port}}/mgr/transaction/getTotalTransactionCount/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "tx_count": "137"
        }
    ]
}
```
#### 2.5 transList

**接口描述**

获取交易列表

**接口url**

/mgr/transaction/transList/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |页码  | page | number |  是| 页码 |
| 3 |行数  | size | number |  是| 每页显示条数 |
**2）数据格式**
```
{{url}}:{{port}}/mgr/transaction/transList/1/1/2
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "transHash": "0x4fa70ba7aedccb4892597a4cb9e66ed3080b1e8327e63ab9201e756dd3eafb39",
            "transFrom": "0x6486ce0a319a264ef745c764bcf6085be8c37c95",
            "transTo": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
            "blockNumber": 831,
            "blockTimestamp": "2020-04-17T18:19:30.000Z",
            "statisticsFlag": 1,
            "createTime": "2020-04-17T18:19:35.000Z",
            "modifyTime": "2020-04-17T18:19:35.000Z"
        },
        {
            "transHash": "0xf8ddf1ff2a1662352185100d45404339f7a30da7c0bee1c5f8cc8f28ef3de792",
            "transFrom": "0x6486ce0a319a264ef745c764bcf6085be8c37c95",
            "transTo": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
            "blockNumber": 830,
            "blockTimestamp": "2020-04-17T18:19:29.000Z",
            "statisticsFlag": 1,
            "createTime": "2020-04-17T18:19:35.000Z",
            "modifyTime": "2020-04-17T18:19:35.000Z"
        }
    ],
    "totalCount": 1492
}
```
#### 2.6 blockTransList

**接口描述**

获取指定区块里的交易列表

**接口url**

/mgr/transaction/transList/:groupID/:page/:size?blockNumber=830

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |页码  | page | number |  是| 页码 |
| 3 |行数  | size | number |  是| 每页显示条数 |
| 4 |区块高度  | blockNumber | number |  是| 区块高度 |
**2）数据格式**
```
{{url}}:{{port}}/mgr/transaction/transList/1/1/10?blockNumber=830
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "transHash": "0x36e4af36955191e9f86919a9322d98beafd0cc1126772b668b110545172463cc",
            "transFrom": "0x6486ce0a319a264ef745c764bcf6085be8c37c95",
            "transTo": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
            "blockNumber": 830,
            "blockTimestamp": "2020-04-17T18:19:29.000Z",
            "statisticsFlag": 1,
            "createTime": "2020-04-17T18:19:35.000Z",
            "modifyTime": "2020-04-17T18:19:35.000Z"
        },
        {
            "transHash": "0xf8ddf1ff2a1662352185100d45404339f7a30da7c0bee1c5f8cc8f28ef3de792",
            "transFrom": "0x6486ce0a319a264ef745c764bcf6085be8c37c95",
            "transTo": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
            "blockNumber": 830,
            "blockTimestamp": "2020-04-17T18:19:29.000Z",
            "statisticsFlag": 1,
            "createTime": "2020-04-17T18:19:35.000Z",
            "modifyTime": "2020-04-17T18:19:35.000Z"
        }
    ],
    "totalCount": 2
}
```
### 3. 合约信息接口
#### 3.1 getCode

**接口描述**

根据合约地址获取合约代码

**接口url**

/mgr/getCode/:groupID/:address

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 合约地址 |address  |string  | 是 | 合约地址 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/contract/getCode/1/0x1cc24eb28asd10ca70sdf968f3ef682635236aa9
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": "0x9192919290803590602001908201803590602001908080601f0160208091040260200160405190810160405280939291908181526020018383808284378201915050505050509192919290803590602001908201803590602001908080601f0160208091040260200160405190810160405280939291908181526020018383808284378201915050505050509192919290803590602001908201803590602001908080601f0160208091040260200160405190810160405280939291908181526020018383808284378201915050505050509192919290803590602001908201803590602001908080601f01602080910402602001604051908101604052809392919081815260200183838082843782019150505050505091929192905050506109c7565b005b34801561042857600080fd5b5061045d600480360381019080803573ffffffffffffffffffffffffffffffffffffffff1690602001909291905050506117e4565b005b34801561046b57600080fd5b5061048a60048036038101908080359060200190929190505050611884565b6040518080191508051906020019080838360005b8381101561152c578082015181840152602081019050611511565b50505050905090810190601f1680156115595780820380516001836020036101000a031916815260200191505b5088810387528e818151815260200191508051906020019080838360005b83811015611592578082015181840152602081019050611577565b50505050905090810190601f1680156115bf5780820380516001836020036101000a031916815260200191505b5088810386528d818151815260200191508051906020019080838360005b838110156115f85780820151818401526020810190506115dd565b50505050905090810190601f168015611625578082038051600183"
}
```

### 4. 节点信息接口
#### 4.1 getNodeIDList

**接口描述**

获取节点id列表

**接口url**

/mgr/getNodeIDList/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/node/getNodeIDList/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489",
        "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
        "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
        "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
        "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
        "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff"
    ]
}
```
#### 4.2 getPeers

**接口描述**

获取peers节点列表

**接口url**

/mgr/getPeers/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/node/getPeers/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "Agency": "agencyC",
            "IPAndPort": "121.10.216.150:19208",
            "Node": "node_121.10.216.150_30300",
            "NodeID": "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
            "Topic": []
        },
        {
            "Agency": "agencyA",
            "IPAndPort": "139.159.199.162:49926",
            "Node": "node_139.159.199.162_8011",
            "NodeID": "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
            "Topic": []
        },
        {
            "Agency": "agencyB",
            "IPAndPort": "111.229.7.134:59840",
            "Node": "node_111.229.7.134_30300",
            "NodeID": "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
            "Topic": [
                "_block_notify_1"
            ]
        },
        {
            "Agency": "agencyC",
            "IPAndPort": "121.10.216.150:19209",
            "Node": "node_121.10.216.150_30301",
            "NodeID": "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
            "Topic": []
        },
        {
            "Agency": "agencyB",
            "IPAndPort": "111.229.7.134:59844",
            "Node": "node_111.229.7.134_30301",
            "NodeID": "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
            "Topic": []
        }
    ]
}
```
#### 4.3 getSealerList

**接口描述**

获取共识节点列表

**接口url**

/mgr/getSealerList/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/node/getSealerList/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
        "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489",
        "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
        "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
        "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
        "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94"
    ]
}
```
#### 4.4 getObserverList

**接口描述**

获取共识节点列表

**接口url**

/mgr/getObserverList/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/node/getObserverList/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": []
}
```
#### 4.5 nodeList

**接口描述**

获取共识节点列表

**接口url**

/mgr/nodeList/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |页码  | page | number |  是| 页码 |
| 3 |行数  | size | number |  是| 每页显示条数 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/node/nodeList/1/1/2
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "node_id": "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
            "group_id": 1,
            "node_name": "1_3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4d",
            "node_ip": "121.10.216.150",
            "p2p_port": 25102,
            "block_number": 831,
            "pbft_view": 993765,
            "node_active": 1,
            "description": null,
            "create_time": "2020-04-07T17:46:17.000Z",
            "modify_time": "2020-04-29T18:08:33.000Z"
        },
        {
            "node_id": "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
            "group_id": 1,
            "node_name": "1_55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a",
            "node_ip": "111.229.7.134",
            "p2p_port": 59840,
            "block_number": 831,
            "pbft_view": 993766,
            "node_active": 1,
            "description": null,
            "create_time": "2020-04-07T17:46:17.000Z",
            "modify_time": "2020-04-29T18:08:33.000Z"
        }
    ],
    "totalCount": 6
}
```
### 5. 群组信息
#### 5.1 getGroupList

**接口描述**

获取血液链的群组列表信息

**接口url**

/mgr/group/getGroupList

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |

**2）数据格式**
```
{{url}}:{{port}}/mgr/group/getGroupList
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        1
    ]
}
```
#### 5.2 getGroupList

**接口描述**

获取血液链的群组内节点信息

**接口url**

/mgr/group/getGroupPeers/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/group/getGroupPeers/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
        "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
        "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
        "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
        "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
        "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489"
    ]
}
```
#### 5.3 getConsensusStatus

**接口描述**

获取血液链的群组共识状态信息

**接口url**

/mgr/group/getConsensusStatus/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/group/getConsensusStatus/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "accountType": 1,
            "allowFutureBlocks": true,
            "cfgErr": false,
            "connectedNodes": 5,
            "consensusedBlockNumber": 832,
            "currentView": 994162,
            "groupId": 1,
            "highestblockHash": "0x8b2a9b6e9bddf9cfd8640eae81c1ae4304a7d590d4be0daa95b8a3259ddd9212",
            "highestblockNumber": 831,
            "leaderFailed": false,
            "max_faulty_leader": 1,
            "nodeId": "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489",
            "nodeNum": 6,
            "node_index": 5,
            "omitEmptyBlock": true,
            "protocolId": 65544,
            "sealer.0": "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
            "sealer.1": "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
            "sealer.2": "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
            "sealer.3": "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
            "sealer.4": "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
            "sealer.5": "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489",
            "toView": 994162
        },
        [
            {
                "nodeId": "3599631a4d83ee83ab4f3f75f836658eed2d0124720d2be65730f2aa7fc051a860247d4d79d01ea2211dc79ae3f2059d65a7e95c8bf8b6ec2dfb4de3c1cbb159",
                "view": 994161
            },
            {
                "nodeId": "55d8b0e4fc74c47659da3d03412c281c4d6850554c1b4c9d8158c7d0bbfa3ab4142a43b6309238b3f23272c80b373218a8b248f387e2c6d954369a247d890faa",
                "view": 994150
            },
            {
                "nodeId": "8a6226af90f4075c47523208c8c94a01653b2f544e478018557b35ede8af7c7167ca77db94429835c8605e070efd2ec7faa45f7ee8754e434c408de502ad8e94",
                "view": 994157
            },
            {
                "nodeId": "a7b08d2f5c3357e75112ae3826abe28d6d5a8196c8b9104f48b0915d02d70018ae8bcad9f7eb827a1e3cb5c4b1b31e1b02b682345484ffd916f03a1e189d78ff",
                "view": 994158
            },
            {
                "nodeId": "bdee74c70300273e84dc1abcaaa86964cd54e388276ebc80b121741f76ca7cd1415fef4e34265b409509908d1bb0050664682463a1922c7dce00e53ca09b7eae",
                "view": 994159
            },
            {
                "nodeId": "f8606bf8d9030a9b45060c7a522dc8a453c10049b478d33a461de551c4feb7752c52c2552d3105d19150336b80a760038fb8cfc7386bbe0a827306602038f489",
                "view": 994162
            }
        ]
    ]
}
```
#### 5.4 general

**接口描述**

获取血液链的群组综合信息

**接口url**

/mgr/group/general/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/group/general/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "groupId": 1,
        "orgCount": 0,
        "contractCount": 0,
        "nodeCount": 6,
        "transactionCount": 1507,
        "latestBlock": 831
    }
}
```
#### 5.5 transDaily

**接口描述**

获取血液链的群组每日交易信息

**接口url**

/mgr/group/transDaily/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/mgr/group/transDaily/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "day": "2020-04-07",
            "groupId": 1,
            "transCount": 2
        },
        {
            "day": "2020-04-08",
            "groupId": 1,
            "transCount": 1
        },
        {
            "day": "2020-04-10",
            "groupId": 1,
            "transCount": 24
        },
        {
            "day": "2020-04-14",
            "groupId": 1,
            "transCount": 42
        },
        {
            "day": "2020-04-15",
            "groupId": 1,
            "transCount": 41
        },
        {
            "day": "2020-04-16",
            "groupId": 1,
            "transCount": 11
        },
        {
            "day": "2020-04-17",
            "groupId": 1,
            "transCount": 1368
        }
    ]
}
```
### 6. 合约方法信息接口
#### 6.1 findById

**接口描述**

根据合约方法id获取合约方法信息

**接口url**

/mgr/findById/:groupID/:contractAddress/:methodId

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 合约地址 |contractAddress  |string  | 是 | 合约地址 |
| 3 | 方法id |methodId  |string  |是  |合约方法id  |

**2）数据格式**
```
{{url}}:{{port}}/mgr/method/findById/1/0x1cc24eb28fb610ca701c3968f3ef682635236aa9/0x8d524af6
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "constant": false,
        "inputs": [
            {
                "name": "_dn",
                "type": "string"
            },
            {
                "name": "_pid",
                "type": "string"
            },
            {
                "name": "_place",
                "type": "string"
            },
            {
                "name": "_type",
                "type": "string"
            },
            {
                "name": "_volume",
                "type": "string"
            },
            {
                "name": "_unit",
                "type": "string"
            },
            {
                "name": "_makeTime",
                "type": "string"
            },
            {
                "name": "_facNumber",
                "type": "string"
            }
        ],
        "name": "AddDonateInfo",
        "outputs": [],
        "payable": false,
        "stateMutability": "nonpayable",
        "type": "function",
        "methodId": "0x8d524af6"
    }
}
```
### 7 用户信息接口
#### 7.1 userList

**接口描述**

获取群组下用户信息

**接口url**

/mgr/userList/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |页码  | page | number |  是| 页码 |
| 3 |行数  | size | number |  是| 每页显示条数 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/user/userList/1/1/2
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "userId": 700226,
            "userName": "140502199412080011",
            "groupId": 1,
            "publicKey": "0x9251a9ce00ff348b813d2e85215b7913291595e53463adb1bca1f712c4f3d44e135e533310044b8c807c2b80858649529413a535be4195d78f641d7b9db6bb39",
            "userStatus": 1,
            "chainIndex": null,
            "userType": 1,
            "address": "0x813e9c897e7f1f9039aa8c756e652a8f4f1f6fbe",
            "hasPk": 1,
            "description": "血液云",
            "createTime": "2020-04-17T10:01:45.000Z",
            "modifyTime": "2020-04-17T10:01:45.000Z"
        },
        {
            "userId": 700022,
            "userName": "14080",
            "groupId": 1,
            "publicKey": "0xb54ff2e266d12ec51a5fa202bf9184bc4e8ebbab0fb6bf467928cb795c46e8f66c7565c6456d4f4f23d44528cc4b2e117ffefb5383dc3e9f5b5808ac50e5779e",
            "userStatus": 1,
            "chainIndex": null,
            "userType": 1,
            "address": "0x3b015bbad22546774912af5bd22eeeff4b6bc396",
            "hasPk": 1,
            "description": "南通市中心血站",
            "createTime": "2020-04-16T17:38:46.000Z",
            "modifyTime": "2020-04-16T17:38:46.000Z"
        }
    ],
    "totalCount": 222
}
```
### 8 解码相关接口
#### 8.1 decodeInput

**接口描述**

获取群组下用户信息

**接口url**

/mgr/decode/decodeInput

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |合约地址  | contractAddress | string |  是| 合约地址 |
| 3 |输入数据  | inputData | string |  是| 输入的input hex字符串 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/decode/decodeInput
{
  "groupID": 1,
  "contractAddress": "0x1cc24eb28fb610ca701c3968f3ef682635236aa9",
  "inputData": "0x8d524af60000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000000000000000000000000000000000014000000000000000000000000000000000000000000000000000000000000001a000000000000000000000000000000000000000000000000000000000000001e00000000000000000000000000000000000000000000000000000000000000220000000000000000000000000000000000000000000000000000000000000026000000000000000000000000000000000000000000000000000000000000002a000000000000000000000000000000000000000000000000000000000000002e0000000000000000000000000000000000000000000000000000000000000000d3930303238313430303036313100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000004062663061303031633735346437353634656133353861326335623030356336353131363431666135623834363565613834616436346433386331636362313662000000000000000000000000000000000000000000000000000000000000000ce5b7a5e8b4b8e5b9bfe59cba0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000357484200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000003333030000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000026d6c0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000013323031352d30312d30312031363a33353a30300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000053134303830000000000000000000000000000000000000000000000000000000"
}
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "0": "9002814000611",
        "1": "bf0a001c754d7564ea358a2c5b005c6511641fa5b8465ea84ad64d38c1ccb16b",
        "2": "工贸广场",
        "3": "WHB",
        "4": "300",
        "5": "ml",
        "6": "2015-01-01 16:35:00",
        "7": "14080",
        "__length__": 8,
        "_dn": "9002814000611",
        "_pid": "bf0a001c754d7564ea358a2c5b005c6511641fa5b8465ea84ad64d38c1ccb16b",
        "_place": "工贸广场",
        "_type": "WHB",
        "_volume": "300",
        "_unit": "ml",
        "_makeTime": "2015-01-01 16:35:00",
        "_facNumber": "14080"
    }
}
```
#### 8.2 decodeLog

**接口描述**

获取群组下用户信息

**接口url**

/mgr/decode/decodeLog

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 |合约地址  | contractAddress | string |  是| 合约地址 |
| 3 |日志数据  | logStr | string |  是| 日志log hex字符串 |
| 4 |方法id  | methodId | string |  是| 合约方法名 hex字符串 |

**2）数据格式**
```
{{url}}:{{port}}/mgr/decode/decodeLog
{
  "groupID": 1,
  "contractAddress": "0x1cc24eb28fb610ca701c3968f3ef682635236aa9",
  "logStr": "0x00000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000120000000000000000000000000000000000000000000000000000000000000018000000000000000000000000000000000000000000000000000000000000001c0000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000002400000000000000000000000000000000000000000000000000000000000000280000000000000000000000000000000000000000000000000000000000000000d3930303238313430303036313100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000004062663061303031633735346437353634656133353861326335623030356336353131363431666135623834363565613834616436346433386331636362313662000000000000000000000000000000000000000000000000000000000000000ce5b7a5e8b4b8e5b9bfe59cba000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000035748420000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000333303000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000013323031352d30312d30312031363a33353a30300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000053134303830000000000000000000000000000000000000000000000000000000",
  "methodId":"0x8d524af6"
}
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "dn": "9002814000611",
        "pid": "bf0a001c754d7564ea358a2c5b005c6511641fa5b8465ea84ad64d38c1ccb16b",
        "place": "工贸广场",
        "_type": "WHB",
        "volume": "300",
        "makeTime": "2015-01-01 16:35:00",
        "facNumber": "14080",
        "eventName": "AddDonateInfoLog"
    }
}
```
