# 血液链监控大屏
## 概要说明
血液链监控大屏后台服务接口文档
## 接口说明
- url：全局的参数url为请求的http地址，例如http://127.0.0.1
- port：全局的参数url为请求的端口号，例如8000
- code：返回码，为0表示请求接口返回成功
- message：返回信息，为'success'代表成功
- data：返回的数据

### 1. 用户合约日志接口
#### 1.1 addPersonalAccountLog

**接口描述**

获取添加个人用户的日志记录信息

**接口url**

/addPersonalAccountLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/account/addPersonalAccountLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [],
    "totalCount": 0
}
```
### 2. 区块信息接口
#### 2.1 blocks

**接口描述**

获取所有区块信息并分页显示

**接口url**

/block/blocks/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/block/blocks/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "pk_id": 138,
            "block_hash": "0x9bfc15a120b187fe57ea7dd1da47d58bae5d7321b901f7741baa67e88c026fe2",
            "block_height": 142,
            "block_timestamp": "2020-04-17T14:34:10.287Z",
            "depot_updatetime": "2020-04-17T14:34:13.899Z",
            "status": 1,
            "tx_count": 1
        },
        {
            "pk_id": 137,
            "block_hash": "0xe41b9d7645bcc06739c8844c7a617614c81d53daa9927ab8b3a00bcf2e30701b",
            "block_height": 141,
            "block_timestamp": "2020-04-17T14:33:31.603Z",
            "depot_updatetime": "2020-04-17T14:33:33.935Z",
            "status": 1,
            "tx_count": 1
        }
    ],
    "totalCount": 138
}
```
#### 2.2 blocksTxDetail

**接口描述**

获取所有区块交易详情

**接口url**

/block/blocksTxDetail/:groupID/:page/:size？contractName=xx&methodName=xx

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |
| 4 | 合约名 |contractName  |string  |是  |合约的名称  |
| 5 | 方法名 |methodName  |string  |是  |合约中的方法名称  |

**2）数据格式**
```
{{url}}:{{port}}/block/blocksTxDetail/1/1/10?contractName=DonateBlood&methodName=AddDonateInfo
```
**响应参数**

**1)数据格式**
```js

{
    "code": 0,
    "message": "success",
    "data": [
        {
            "pk_id": 31,
            "block_hash": "0x77b74eb2df5de1c05c2ff1e6b2d3c56e4c404f8198cda6940f463cf5269b5d68",
            "block_height": 140,
            "block_timestamp": "2020-04-17T10:50:38.549Z",
            "contract_name": "DonateBlood",
            "depot_updatetime": "2020-04-17T10:50:40.178Z",
            "method_name": "AddDonateInfo",
            "tx_from": "0xf51e0d21477ef7652da21a18b4fb5a1424124425",
            "tx_hash": "0x93d716d76eb3b8b9c843b1ebb61d827801085fa7741c5ef48b6858040d3f86af",
            "tx_to": "0x1cc24eb28fb610ca701c3968f3ef682635236aa9"
        },
        {
            "pk_id": 30,
            "block_hash": "0xd5a3b2fae2f61b541a5b077428e63b90c7aed2d0d151434bff2afa2bf2a6efc8",
            "block_height": 139,
            "block_timestamp": "2020-04-16T17:29:09.767Z",
            "contract_name": "DonateBlood",
            "depot_updatetime": "2020-04-16T17:29:12.638Z",
            "method_name": "AddDonateInfo",
            "tx_from": "0xf51e0d21477ef7652da21a18b4fb5a1424124425",
            "tx_hash": "0x1bf62228f4c3025ac292a171932a3be7ec2d4b87ef36f9143e309b0b031f74aa",
            "tx_to": "0x1cc24eb28fb610ca701c3968f3ef682635236aa9"
        }
    ],
    "totalCount": 2
}
```
#### 2.3 latestBlock

**接口描述**

获取最新的区块高度

**接口url**

{{url}}:{{port}}/block/latestBlock/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/block/latestBlock/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "block_height": 142
        }
    ]
}
```
#### 2.4 totalTxCount

**接口描述**

获取交易总数

**接口url**

{{url}}:{{port}}/block/totalTxCount/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
**2）数据格式**
```
{{url}}:{{port}}/block/totalTxCount/1
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
### 3. 业务日志信息接口
#### 3.1 createBloodBagLog

**接口描述**

获取创建血袋记录并分页显示

**接口url**

/business/createBloodBagLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/business/createBloodBagLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "pk_id": 1,
            "_abo": "A",
            "block_height": 129,
            "block_timestamp": "2020-04-16T11:35:06.428Z",
            "_code": "全血",
            "_col_time": "2020/4/15",
            "depot_updatetime": "2020-04-16T11:35:09.135Z",
            "_dn": "dn1",
            "event_contract_address": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
            "_prd_time": "2020/4/15",
            "_product_id": "prd1",
            "_rh": "R",
            "tx_hash": "0x82bf43fd3d9761e1b8b6801c03785b5473f518f3e8fe4aa538f7a4d6e8ede277"
        }
    ],
    "totalCount": 1
}
```
#### 3.2 sendBloodLog

**接口描述**

获取发血记录并分页显示

**接口url**

/business/sendBloodLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/business/sendBloodLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "pk_id": 1,
            "_b_i_l_l_n_u_m": "order1",
            "_d_e_s_t_f_a_c_c_o_d_e": "南宁医院",
            "_f_a_c_c_o_d_e": "南宁血站",
            "block_height": 142,
            "block_timestamp": "2020-04-17T14:34:10.287Z",
            "depot_updatetime": "2020-04-17T14:34:13.916Z",
            "_dn": "dn5",
            "event_contract_address": "0x7d1b34e658ba9e2594d9e41d995880152afae298",
            "_prd": "prd5",
            "_time": "2020/4/20",
            "tx_hash": "0x5702b5ebf2f721ec05abc5957f78c7d0bb538aa7acb231a72f9a02696864828a"
        }
    ],
    "totalCount": 1
}
```
#### 3.3 dispatchBloodLog

**接口描述**

获取血液调剂的信息记录

**接口url**

/business/dispatchBloodLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/business/dispatchBloodLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [],
    "totalCount": 0
}
```
#### 3.4 useBloodLog

**接口描述**

获取用血的信息记录

**接口url**

/business/useBloodLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**


**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/business/useBloodLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [],
    "totalCount": 0
}
```
### 4. 献血日志信息接口
#### 4.1 donateInfoLog

**接口描述**

获取献血日志记录并分页显示

**接口url**

/donateBlood/donateInfoLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/donateBlood/donateInfoLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "pk_id": 8,
            "_type": "12",
            "block_height": 140,
            "block_timestamp": "2020-04-17T10:50:38.549Z",
            "depot_updatetime": "2020-04-17T10:50:40.188Z",
            "_dn": "ddd",
            "event_contract_address": "0x1cc24eb28fb610ca701c3968f3ef682635236aa9",
            "_fac_number": "12",
            "_make_time": "12",
            "_pid": "55211eabcb7c20a0979285f51eb5a9c992d7b2f0edb5eee35fe194bba4307135",
            "_place": "12",
            "tx_hash": "0x93d716d76eb3b8b9c843b1ebb61d827801085fa7741c5ef48b6858040d3f86af",
            "_volume": "12"
        }
    ],
    "totalCount": 1
}
```
#### 4.2 donateResultLog

**接口描述**

获取献血检验结果日志记录并分页显示

**接口url**

/donateBlood/donateResultLog/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/donateBlood/donateResultLog/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [],
    "totalCount": 0
}
```
### 5. 血液链节点信息
#### 5.1 nodeInfo

**接口描述**

获取血液链的节点相关信息

**接口url**

/node/nodeInfo/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/node/nodeInfo/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": {
        "nodeCount": 6,
        "activeCount": 6
    }
}
```
### 6. 溯源相关接口
#### 6.1 traceInfo

**接口描述**

获取溯源日志记录并分页显示

**接口url**

/trace/traceInfo/:groupID/:page/:size

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |
| 2 | 页码 |page  |number  | 是 | 分页数据的页码 |
| 3 | 用户id |size  |number  |是  |每一页显示的行数  |

**2）数据格式**
```
{{url}}:{{port}}/trace/traceInfo/1/1/10
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "_dn": "dn5",
            "time": "2020/4/20",
            "fac_code": "南宁血站",
            "product_id": "prd5",
            "type": "sendBlood"
        },
        {
            "_dn": "dn5",
            "time": "2020/4/13",
            "fac_code": "北海血站",
            "product_id": "",
            "type": "donateBlood"
        },
        {
            "_dn": "dnc",
            "time": "2020/04/12",
            "fac_code": "fac1",
            "product_id": "",
            "type": "donateBlood"
        },
        {
            "_dn": "ddd",
            "time": "12",
            "fac_code": "12",
            "product_id": "",
            "type": "donateBlood"
        }
    ]
}
```
#### 6.2 traceCount

**接口描述**

获取溯源总条目

**接口url**

/trace/traceCount/:groupID

**调用方法**

HTTP GET

**请求参数**

**1）参数表**

| 序号 |中文  |参数名  | 类型 |必填  |说明  |
| --- | --- | --- | --- | --- | --- |
| 1 |群组id  | groupID | number |  是| 血液链的群组id |

**2）数据格式**
```
{{url}}:{{port}}/trace/traceCount/1
```
**响应参数**

**1)数据格式**
```js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "trace_count": 4
        }
    ]
}
```
