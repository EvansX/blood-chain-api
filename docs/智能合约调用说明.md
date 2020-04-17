# 智能合约调用说明
通过本接口，可以读取和调用血液链智能合约。

## 1.使用前提
接入方需要首先申请血液链账号，血液链联盟管理委员会会审核接入请求，批准后，将下发具备查询和调用合约权限的账号、APIKEY及APISECRET。

## 2.创建账号
### 2.1 申请机构账号
通过api申请账号后，需等待联盟委员会审核。
返回的机构id可用来查询申请状态。

**调用方法**

HTTP POST

**请求地址**

http://139.159.199.162:8008/agency/addApply

参数：

- groupId:组id `int`
- agencyName:机构名称 `string`
- agencyIp:机构服务器ip（如无服务器填0.0.0.0） `string`
- address:机构所在地址，省市 `string`
- addressDetail:机构所在详细地址，区县门牌号等 `string`
- agencyUserName:机构用户在血液链中想使用的用户名 `string`
- agencyType:机构类型, 1为节点，0为非节点 `int`
- phone:联系电话 `string`

**返回：**

- code:返回码int
- message:提示信息 `string`
- data:返回数据 `Object`
  - agency_id: 机构id `int`
  - agency_status:机构状态，0-审核未通过，1-待审核，2-审核中，3-审核通过 `int`
  - api_key:`string`
  - api_secret:`string`
例

```  js
        {
          "code":0,
          "message":"success",
          "data":
            {
              "agency_status":1,
              "agency_id":1003,
              "group_id":1,
              "agency_name":"test",
              "agency_ip":"0.0.0.0",
              "address":"广东深圳",
              "address_detail":"福田保税区",
              "agency_user_name":"offical",
              "agency_type":1,
              "phone":"13800000000",
              "create_time":"2020-04-13T06:26:55.000Z",
              "modify_time":"2020-04-13T06:26:55.000Z",
              "api_key": "eAX7mjTqaQ21OAyeKOwrkBtb5Bhf",
              "api_secret": "08azNohkJDBF9DlZv4IbyWaXK5uPTg1ZgQGpGofil",
            }
        }
      
```

#### 2.1.1 查询申请结果
通过上个接口返回的机构id，查询申请结果。

**调用方法**

HTTP GET

**请求地址**

/agency/agencyInfo/`agency_id`

**请求头：**
```js
headers: {
        APIKEY: "",//申请时返回的
        APISECRET: ""//申请时返回的
}
```

**返回：**

- code:返回码int
- message:提示信息 `string`
- data:返回数据 `Object`
  - user_id: 用户id `int`
  - user_name: 用户名 `string`
  - account: 链上地址 `address`
例

```  js
{
    "code": 0,
    "message": "success",
    "data": [
        {
            "user_id": 700019,
            "user_name": "test",
            "account": "0xf51e0d2147ef7652da2a18b4fb5a1424124425",
            "agency_id": 1002,
            "agency_ip": "0.0.0.0",
            "agency_name": "official",
            "agency_type": 1,
            "phone": "13800000000",
            "agency_status": 3,
            "description": null
        }
    ]
}
      
```

### 2.2 申请普通账号
通过api申请普通献血者账号

**调用方法**

HTTP POST

**请求地址**

http://139.159.199.162:8008/user/addConsumer

**参数：**

- groupID: 1 `int`,
- userName: "asd" `string`,//账号名，例如原业务体系下的用户名
- description:"" `string` //备注。属于哪个机构下的用户，例如血液云

**请求头：**
```js
headers: {
        APIKEY: "",//上一步申请机构账号获得的APIKEY
        APISECRET: ""
}
```

**返回：**
- code返回码 `string`
- message提示信息 `string`
- data返回数据 `Object`
- user_id用户编号 `int`
- user_name用户名称 `string`
- address账户地址 `string`
- group_id群组id `int`


```  js
        {
          "code": 0,
          "message": "success",
          "data": {
              "user_id": 700024,
              "user_name": "test_consumer2",
              "group_id": 1,
              "address": "0xa8be5a90289c2111e9d7cb553d9b1518c6a9dc66"
    }
}
      
```

## 3.API
**调用方法**
HTTP POST

**请求地址：**

http://139.159.199.162:8008/transaction/trans/handle

**请求头：**

需传入合法的APIKEY和APISECRET
``` js
    
      headers:{
        APIKEY:"",
        APISECRET:""
      }
```
### addOrganizationAccount
用于设置机构账号为血站、医院等身份，然后该账号才可调用合约。
**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（account） `string`
- contractAddress:合约地址（0x87f635d1d3434f6a6bf442591d13d8eb20d4996f） `address`
- funcName:调用方法名（addOrganizationAccount） `string`
- funcParam:
  - 机构号 `string`
  - 账户地址 `address`
  - 账户类型，1为血站，2为医院，3为卫健委，4为其他 `int`

**返回：**
- code: 0
- message: "success"
- data:
  - status：0x0代表合约执行成功

例：
```js
    {
        "code":0,
        "message":"success",
        "data: {
            "transactionHash":"0x93d716d76eb3b8b9c843b1ebb61d827801085fa7741c5ef48b6858040d3f86af","transactionIndex":0,"blockHash":"0x77b74eb2df5de1c05c2ff1e6b2d3c56e4c404f8198cda6940f463cf5269b5d68","blockNumber":140,"gasUsed":155568,"contractAddress":"0x0000000000000000000000000000000000000000","root":"0x05e4c014d3c8989fcdb9b18fdbd576123b9a768532dd26d5769a8bf83d16335e","status":"0x0","message":null,"from":"0xf51e0d21477ef7652da21a18b4fb5a1424124425","to":"0x1cc24eb28fb610ca701c3968f3ef682635236aa9","input":"","output":"0x","logs":[{"removed":false,"logIndex":null,"transactionIndex":null,"transactionHash":null,"blockHash":null,"blockNumber":null,"address":"0x1cc24eb28fb610ca701c3968f3ef682635236aa9","data":"","type":null,"topics":["0xb1b9afe56e7ccf6464fc522f9a1ca49b0ab44cd1155dad192e9ed91f2f8362b3"],"logIndexRaw":null,"transactionIndexRaw":null,"blockNumberRaw":null}],"logsBloom":"","gasUsedRaw":"0x25fb0","statusOK":true,"transactionIndexRaw":"0x0","blockNumberRaw":"0x8c"}}
```
### addPersonalAccount
血站或管理员账号可调用，用于添加献血者信息
**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（account） `string`
- contractAddress:合约地址（0x87f635d1d3434f6a6bf442591d13d8eb20d4996f） `address`
- funcName:调用方法名（addPersonalAccount） `string`
- funcParam:
  - 身份证号 `string`
  - 要设置的账户地址 `address`
  - 账号类型 `int`
  - 生日 `int`
  - ABO血型 `string`
  - Rh血型 `string`
  - 性别 `int`

**返回：**
- code: 0
- message: "success"
- data:
  - status：0x0代表合约执行成功

### AddDonateInfo
血站或管理员账号可调用，添加采血信息。
**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（donateBlood） `string`
- contractAddress:合约地址（0x1cc24eb28fb610ca701c3968f3ef682635236aa9） `address`
- funcName:调用方法名（AddDonateInfo） `string`
- funcParam:
  - DN码 `string`
  - 献血者的身份证号 `string`
  - 献血地点 `string`
  - 采血类型 `string`
  - 采血量 `string`
  - 血量单位 `string`
  - 时间 `string`
  - 机构代码 `string`

### CreatBloodBag
血站或管理员账号可调用，添加采血信息。
**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（business） `string`
- contractAddress:合约地址（0x7d1b34e658ba9e2594d9e41d995880152afae298） `address`
- funcName:调用方法名（CreatBloodBag） `string`
- funcParam:
  - DN码 `string`
  - 产品码 `string`
  - 血液品种类别代码 `string`
  - 采集时间 `string`
  - 制备时间 `string`
  - 采集者工号 `string`
  - 制备者工号 `string`
  - 有效期 `string`
  - Abo血型 `string`
  - Rh血型 `string`

### bloodSend
血站或管理员账号可调用，添加发血信息。
**参数：**

- groupId:组idint
- userID:调用者账户的idint
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（business） `string`
- contractAddress:合约地址（0x7d1b34e658ba9e2594d9e41d995880152afae298） `address`
- funcName:调用方法名（bloodSend） `string`
- funcParam:
  - 发出机构代码 `string`
  - 发入机构代码 `string`
  - 发血业务单据号码 `string`
  - dn码 `string`
  - 产品码 `string`
  - 时间 `string`

### bloodSendBack
血站、医院或管理员账号可调用，添加退血信息。
**参数：**

- groupId:组idint
- userID:调用者账户的idint
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（business） `string`
- contractAddress:合约地址（0x7d1b34e658ba9e2594d9e41d995880152afae298） `address`
- funcName:调用方法名（bloodSendBack） `string`
- funcParam:
  - 发出机构代码 `string`
  - 发入机构代码 `string`
  - 业务单据号码 `string`
  - dn码 `string`
  - 产品码 `string`
  - 时间 `string`

### bloodDispatch
血站、医院或管理员账号可调用，添加调剂信息。
**参数：**

- groupId:组idint
- userID:调用者账户的idint
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（business） `string`
- contractAddress:合约地址（0x7d1b34e658ba9e2594d9e41d995880152afae298） `address`
- funcName:调用方法名（bloodDispatch） `string`
- funcParam:
  - 发出机构代码 `string`
  - 发入机构代码 `string`
  - 业务单据号码 `string`
  - dn码 `string`
  - 产品码 `string`
  - 时间 `string`

### dispatchAndChangeDn
血站或管理员账号可调用，添加调剂信息。
**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（business） `string`
- contractAddress:合约地址（0x7d1b34e658ba9e2594d9e41d995880152afae298） `address`
- funcName:调用方法名（dispatchAndChangeDn） `string`
- funcParam:
  - 机构代码 `string`
  - 原始dn码 `string`
  - 原始产品码 `string`
  - 新dn码 `string`
  - 新产品码 `string`
  - 更换时间 `string`

### getDonateResultByDn
传入献血者的献血码，获取献血记录和检测结果

**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:合约名称（donateBlood） `string`
- contractAddress:合约地址（0x1cc24eb28fb610ca701c3968f3ef682635236aa9） `address`
- funcName:调用方法名（getDonateResultByDn） `string`
- funcParam:献血码array


**返回：**

- code:返回码 `int`
- message:提示信息 `string`
- data:返回数据 `Object`
- DonateInfo
  - dn:dn码 `string`
  - uid:用户身份证号 `string`
  - place:献血地点 `string`
  - bloodType:献血类型 `string`
  - volume:献血量 `string`
  - volUnit:血量单位 `string`
  - makeTime:采集时间 `string`
  - fac:采集机构代码 `string`
例
```js
      
        {
          "code": 0,
          "message": "success",
          "data": {
            "DonateInfo":{
              "dn":"",
              "uid":"",
              "place":"",
              "bloodType":"",
              "volume":"",
              "volUnit":"",
              "makeTime":"",
              "fac":""
            }
          }
        }
```   
    
### getAllInfoByDn
传入血袋的献血码和产品码，获取献血记录和检测结果、血袋信息

**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:'business' `string`
- contractAddress:合约地址（0x7d1b34e658ba9e2594d9e41d995880152afae298） `address`
- funcName:'getAllInfoByDn' `string`
- funcParam:献血码、产品码array


**返回：**

- code:返回码 `int`
- message:提示信息 `string`
- data:返回数据 `Object`
- DonateInfo
  - dn:dn码 `string`
  - uid:用户身份证号 `string`
  - place:献血地点 `string`
  - bloodType:献血类型 `string`
  - volume:献血量 `string`
  - volUnit:血量单位 `string`
  - makeTime:采集时间 `string`
  - fac:采集机构代码 `string`
- BloodBag
  - code:血液品种类别代码 `string`
  - colTime:采集时间 `string`
  - prdTime:制备时间 `string`
  - colOp:采集者工号 `string`
  - prdOp:制备者工号 `string`
  - expTime:有效期 `string`
  - abo:血型 `string`
  - rh:rh血型 `string`


例
```js
      
  {
    "code": 0,
    "message": "success",
    "data": {
      "DonateInfo":{
        "dn":"",
        "uid":"",
        "place":"",
        "bloodType":"",
        "volume":"",
        "volUnit":"",
        "makeTime":"",
        "fac":""
      },
      "BloodBag"{
        "code":"",
        "colTime":"",
        "prdTime":"",
        "colOp":"",
        "prdOp":"",
        "expTime":"",
        "abo":"",
        "rh":""
    }
  }
```     
    
### getBloodOutboundInfoByDn
传入血袋的dn码和产品码，获取发血记录

**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:'business' `string`
- contractAddress:合约地址（0x5e90a3f03d598314bf53828b3e39a73621f0f24d） `address`
- funcName:'getBloodOutboundInfoByDn' `string`
- funcParam:献血码、产品码`array`


**返回：**

- code:返回码 `int`
- message:提示信息 `string`
- data:返回数据Object
  - bbfac:血站机构代码 `string`
  - medSsid:医院ssid `string`
  - billid:发血业务单据号码 `string`
  - time:时间 `string`
例

```js  
        {
          "code": 0,
          "message": "success",
          "data": {
            bbfac;//血站机构代码
            medSsid;//医院ssid
            billid; // 发血业务单据号码
            time；//时间
          }
        }
```    

### getBloodBackInfoByDn
传入血袋的dn码和产品码，获取退血记录

**参数：**

- groupId:组id `int`
- userID:调用者账户的id `int`
- userName:调用者账户的名称 `string`
- account:调用者账户公钥地址 `address`
- contractName:'business' `string`
- contractAddress:合约地址（0x5e90a3f03d598314bf53828b3e39a73621f0f24d） `address`
- funcName:'getBloodBackInfoByDn' `string`
- funcParam:献血码、产品码`array`


**返回：**

- code:返回码 `int`
- message:提示信息 `string`
- data:返回数据Object
  - bbfac:医院ssid `string`
  - medSsid:血站机构代码 `string`
  - billid:退血业务单据号码 `string`
  - time:时间 `string`
例

```js  
        {
          "code": 0,
          "message": "success",
          "data": {
            bbfac;//医院机构代码
            medSsid;//血站机构代码
            billid; // 退血业务单据号码
            time；//时间
          }
        }
```    