# 简介

**标题**：boot4j APIs

**简介**：接口调试系统

**HOST**:192.168.4.129:8088

**联系人**:岛主

**接口路径**：/v2/api-docs?group=员工之家
# <b style="color:green;">资源文件服务[陈志平]</b>

## 下载资源文件

**接口说明**:文件资源获取，注意采用的相对路径，防止code地址超长


**接口地址**:`/res/{code}`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|code| 资源Base58码  | query | true |string  |    |

**响应数据**:


```json

```

**响应参数说明**:


暂无




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  ||
# 企业管理[陈志平]

## 查询企业账户信息

**接口说明**:查询企业账户余额


**接口地址**:`/api/enterprise/account`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：
暂无


**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«EnterpriseAccount»|
## 现金加款(需admin权限)

**接口说明**:现金加款或资金充值


**接口地址**:`/api/enterprise/addCash`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|cash| cash  | query | false |number  |    |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«EnterpriseAccount»|
| -1 | 企业编码（enterpriseId）不能为空  ||
| -2 | 加款金额必须大于0  ||
| -3 | 企业账号不存在  ||
| -4 | 企业被禁用，不允许加款  ||
| -994 | 其他未知异常  ||
## 授信加款(需admin权限)

**接口说明**:授信加款


**接口地址**:`/api/enterprise/addCredits`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|credits| credits  | query | false |number  |    |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«EnterpriseAccount»|
| -1 | 企业编码（enterpriseId）不能为空  ||
| -2 | 加款金额必须大于0  ||
| -3 | 企业账号不存在  ||
| -4 | 企业被禁用，不允许授信加款  ||
| -994 | 其他未知异常  ||
## 提交企业认证申请

**接口说明**:提交企业认证申请，	
 -1 	
 -2 	
 -3


**接口地址**:`/api/enterprise/auditing`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterprise| 企业  | body | true |Enterprise  | Enterprise   |

**schema属性说明**



**Enterprise**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|account| 企业账户信息  | body | false |EnterpriseAccount  | EnterpriseAccount   |
|address| 详细地址  | body | false |string  |    |
|area| 区县  | body | false |string  |    |
|audit| 认证信息：通过、不通过  | body | false |string  |    |
|auditTime| 认证审核时间  | body | false |date-time  |    |
|auditingTime| 认证申请时间  | body | false |date-time  |    |
|auditorId| 认证人  | body | false |string  |    |
|bankCode| 银行基本户帐号  | body | false |string  |    |
|bankName| 银行基本户开户行  | body | false |string  |    |
|city| 城市  | body | false |string  |    |
|contact| 联系人（管理员）姓名  | body | false |string  |    |
|contactType| 用户类型(企业用户、员工用户)  | body | false |string  |    |
|creditCode| 统一社会信用代码  | body | false |string  |    |
|enterpriseId| 企业编码  | body | false |string  |    |
|industry| 所属行业  | body | false |string  |    |
|name| 企业名称  | body | false |string  |    |
|permitUrl| 营业执照图片地址，来自文件上传后的src属性  | body | false |string  |    |
|phone| 联系人（管理员）电话  | body | false |string  |    |
|place| 注册场所地址  | body | false |string  |    |
|province| 省份  | body | false |string  |    |
|registerId| 注册人  | body | false |string  |    |
|registerTime| 注册时间  | body | false |date-time  |    |
|scale| 企业规模  | body | false |string  |    |
|status| 企业状态  | body | false |string  |    |
|telephone| 注册固定电话  | body | false |string  |    |

**EnterpriseAccount**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|cashBalance| 资金余额：例子：100.99  | body | false |number  |    |
|cashCredits| 授信额度，例子：100.99  | body | false |number  |    |
|enterpriseId| 企业编码  | body | false |string  |    |
|giveTotalIntegral| 累积发放积分，例子：100  | body | false |number  |    |
|integralBalance| 积分余额，例子：100  | body | false |number  |    |
|serviceRate| 服务费，例子：0.08  | body | false |number  |    |
|status| 账户状态  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Enterprise»|
| -1 | 企业编码（enterpriseId）不能为空  ||
| -2 | 当前企业不是你注册的企业，你无权提交认证  ||
| -3 | 请上传营业执照，http链接地址来自文件上传后的src属性  ||
| -994 | 其他未知异常  ||
## 积分充值

**接口说明**:积分充值


**接口地址**:`/api/enterprise/buyIntegral`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|integral| integral  | query | false |number  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«EnterpriseAccount»|
| -1 | 企业编码不能为空  ||
| -2 | 充值积分必须大于0  ||
| -3 | 企业账号不存在  ||
| -4 | 只有企业管理员有权限积分充值  ||
| -5 | 只能给自己的企业充值积分  ||
| -6 | 账户可用现金额度不足，无法完成积分充值  ||
| -994 | 其他未知异常  ||
## 查看单次积分充值详情

**接口说明**:查看单次积分充值详情


**接口地址**:`/api/enterprise/buyIntegralDetail`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| id  | query | false |integer  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "accountId": 0,
        "amount": 0,
        "cashBalance": 0,
        "cashDetailId": 0,
        "createTime": "",
        "enterpriseId": "",
        "integral": 0,
        "integralBalance": 0,
        "oprId": "",
        "serviceRate": 0,
        "type": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |AccountIntegralDetail  | AccountIntegralDetail   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**AccountIntegralDetail**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|accountId | 账户编码   |int32  |    |
|amount | 支付余额：例子：100.99   |number  |    |
|cashBalance | 当前资金余额：例子：100.99   |number  |    |
|cashDetailId | 现金流水编码   |int32  |    |
|createTime | 操作时间   |date-time  |    |
|enterpriseId | 企业编码   |string  |    |
|integral | 积分，例子：100   |number  |    |
|integralBalance | 当前积分余额，例子：100   |number  |    |
|oprId | 操作员编码   |string  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|type | 操作类型(积分充值、积分发放)   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«AccountIntegralDetail»|
## 查询企业账户资金明细

**接口说明**:查询企业账户资金明细


**接口地址**:`/api/enterprise/cashDetail`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 企业现金明细查询参数  | body | true |AccountCashDetailDBParam  | AccountCashDetailDBParam   |

**schema属性说明**



**AccountCashDetailDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_dnl_receivedTime| 时间大于等于  | body | false |string  |    |
|_dnm_receivedTime| 时间小于等于  | body | false |string  |    |
|_se_enterpriseId| 企业编码等于  | body | false |string  |    |
|_se_type| 操作类型等于，用中文，数据：资金充值、资金减款、积分充值、全部  | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"accountId": 0,
"amount": 0,
"cashBalance": 0,
"enterpriseId": "",
"oprId": "",
"receivedTime": "",
"type": ""
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«AccountCashDetail»  | DBResult«AccountCashDetail»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«AccountCashDetail»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | AccountCashDetail   |

**AccountCashDetail**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|accountId | 账户编码   |int32  |    |
|amount | 金额：例子：100.99   |number  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|oprId | 操作员编码   |string  |    |
|receivedTime | 入账时间   |date-time  |    |
|type | 款项类型(资金充值、资金减款、积分发放)   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«DBResult«AccountCashDetail»»|
| -1 | 企业管理员才可以查看账户资金明细  ||
| -994 | 其他未知异常  ||
## 查询当前登录用户

**接口说明**:获取当前登录用户


**接口地址**:`/api/enterprise/current`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：
暂无


**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": "",
        "activate": "",
        "departmentId": 0,
        "enterpriseId": "",
        "identityId": 0,
        "name": "",
        "nickName": "",
        "oprId": "",
        "ownerIdentityId": 0,
        "password": "",
        "passwordType": "",
        "phone": "",
        "position": "",
        "roles": [
{
"id": 0,
"name": ""
}
        ],
        "status": "",
        "type": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Operator  | Operator   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Operator**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 账号，不能修改，长度小于等于128   |string  |    |
|activate | 是否激活(已激活、未激活)   |string  |    |
|departmentId | 部门编码   |int32  |    |
|enterpriseId | 企业编码   |string  |    |
|identityId | 身份编码   |int32  |    |
|name | 名称   |string  |    |
|nickName | 昵称   |string  |    |
|oprId | 操作员编码   |string  |    |
|ownerIdentityId | 归属商户身份编码   |int32  |    |
|password | 密码   |string  |    |
|passwordType | 密码类型 , @See PasswordEncoderEnum   |string  |    |
|phone | 手机号   |string  |    |
|position | 岗位   |string  |    |
|roles | 角色   |array  | Role   |
|status | 用户状态(启用，禁用)   |string  |    |
|type | 用户类型(企业管理员、普通员工)   |string  |    |

**Role**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|name |    |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«Operator»|
## <s style="color:#d0d0d0;">禁用企业(需admin权限)</s>

**接口说明**:禁用企业


**接口地址**:`/api/enterprise/disable`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": true,
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |boolean  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«boolean»|
## <s style="color:#d0d0d0;">启用企业(需admin权限)</s>

**接口说明**:启用企业


**接口地址**:`/api/enterprise/enable`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": true,
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |boolean  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«boolean»|
## <s style="color:#d0d0d0;">查询企业账户积分发放明细</s>

**接口说明**:查询企业账户积分发放明细


**接口地址**:`/api/enterprise/giveDetail`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 积分发放明细查询参数  | body | true |IntegralGiveDetailDBParam  | IntegralGiveDetailDBParam   |

**schema属性说明**



**IntegralGiveDetailDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_dnl_createTime| 时间大于等于  | body | false |string  |    |
|_dnm_createTime| 时间小于等于  | body | false |string  |    |
|_ne_integralDetailId| 企业账户积分明细编码  | body | false |string  |    |
|_se_activate| 账户状态，用中文，数据：已激活、未激活、全部  | body | false |string  |    |
|_se_enterpriseId| 企业编码等于  | body | false |string  |    |
|_se_reason| 发放理由等于，用中文，数据：员工生日福利、节假日福利、全部  | body | false |string  |    |
|_sk_name| 姓名  | body | false |string  |    |
|_sk_phone| 手机  | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"activate": "",
"createTime": "",
"deptName": "",
"enterpriseId": "",
"integral": 0,
"integralDetailId": 0,
"name": "",
"oprId": "",
"phone": "",
"position": "",
"reason": "",
"staffId": ""
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«IntegralGiveDetail»  | DBResult«IntegralGiveDetail»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«IntegralGiveDetail»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | IntegralGiveDetail   |

**IntegralGiveDetail**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|activate | 账户状态(已激活、未激活)   |string  |    |
|createTime | 操作时间   |date-time  |    |
|deptName | 所属部门   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|integral | 本次发放的积分，例子：100   |number  |    |
|integralDetailId | 积分操作编码   |int32  |    |
|name | 名称   |string  |    |
|oprId | 操作员编码   |string  |    |
|phone | 手机号   |string  |    |
|position | 岗位   |string  |    |
|reason | 发放理由   |string  |    |
|staffId | 员工编码   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«DBResult«IntegralGiveDetail»»|
## 积分发放

**接口说明**:积分发放


**接口地址**:`/api/enterprise/giveIntegral`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|integral| 积分数量  | query | true |string  |    |
|oprIdList| oprIdList  | body | true |array  |    |
|reason| 发放理由  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«EnterpriseAccount»|
## 积分发放批量导入

**接口说明**:积分发放批量导入


**接口地址**:`/api/enterprise/giveIntegral/excel`


**请求方式**：`POST`


**consumes**:`["multipart/form-data"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|file| Excel(.xls、xlsx)文件  | formData | true |array  | MultipartFile   |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«EnterpriseAccount»|
| -1 | 企业编码不能为空  ||
| -2 | 积分发放明细不能为空  ||
| -3 | 员工姓名不能为空  ||
| -4 | 员工手机号码不能为空  ||
| -5 | 给员工方法的积分必须大于0  ||
| -6 | 发放的总积分必须大于0  ||
| -7 | 只有企业管理员有权限发放积分  ||
| -8 | 只能给自己的企业发放积分  ||
| -9 | 企业账户积分余额不足  ||
| -994 | 其他未知异常  ||
## 查询当前用户企业资料

**接口说明**:查询“我的”企业资料，如：企业管理 / 企业资料


**接口地址**:`/api/enterprise/info`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：
暂无


**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«Enterprise»|
## 查询企业账户积分明细

**接口说明**:查询企业账户积分明细


**接口地址**:`/api/enterprise/integralDetail`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 企业账户积分明细查询参数  | body | true |AccountIntegralDetailDBParam  | AccountIntegralDetailDBParam   |

**schema属性说明**



**AccountIntegralDetailDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_dnl_createTime| 时间大于等于  | body | false |string  |    |
|_dnm_createTime| 时间小于等于  | body | false |string  |    |
|_se_enterpriseId| 企业编码等于  | body | false |string  |    |
|_se_type| 操作类型等于，用中文，数据：积分充值、积分发放、全部  | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"accountId": 0,
"amount": 0,
"cashBalance": 0,
"cashDetailId": 0,
"createTime": "",
"enterpriseId": "",
"integral": 0,
"integralBalance": 0,
"oprId": "",
"serviceRate": 0,
"type": ""
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«AccountIntegralDetail»  | DBResult«AccountIntegralDetail»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«AccountIntegralDetail»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | AccountIntegralDetail   |

**AccountIntegralDetail**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|accountId | 账户编码   |int32  |    |
|amount | 支付余额：例子：100.99   |number  |    |
|cashBalance | 当前资金余额：例子：100.99   |number  |    |
|cashDetailId | 现金流水编码   |int32  |    |
|createTime | 操作时间   |date-time  |    |
|enterpriseId | 企业编码   |string  |    |
|integral | 积分，例子：100   |number  |    |
|integralBalance | 当前积分余额，例子：100   |number  |    |
|oprId | 操作员编码   |string  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|type | 操作类型(积分充值、积分发放)   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«DBResult«AccountIntegralDetail»»|
## 现金减款(需admin权限)

**接口说明**:现金减款


**接口地址**:`/api/enterprise/minusCash`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|cash| cash  | query | false |number  |    |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«EnterpriseAccount»|
| -1 | 企业编码（enterpriseId）不能为空  ||
| -2 | 减款金额必须大于0  ||
| -3 | 企业账号不存在  ||
| -994 | 其他未知异常  ||
## 授信减款(需admin权限)

**接口说明**:授信减款


**接口地址**:`/api/enterprise/minusCredits`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|credits| credits  | query | false |number  |    |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "cashBalance": 0,
        "cashCredits": 0,
        "enterpriseId": "",
        "giveTotalIntegral": 0,
        "integralBalance": 0,
        "serviceRate": 0,
        "status": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |EnterpriseAccount  | EnterpriseAccount   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«EnterpriseAccount»|
| -1 | 企业编码（enterpriseId）不能为空  ||
| -2 | 减款金额必须大于0  ||
| -3 | 企业账号不存在  ||
| -4 | 企业被禁用，不允许授信减款  ||
| -994 | 其他未知异常  ||
## 修改当前用户的企业资料

**接口说明**:修改企业资料


**接口地址**:`/api/enterprise/modify`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterprise| 企业  | body | true |Enterprise  | Enterprise   |

**schema属性说明**



**Enterprise**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|account| 企业账户信息  | body | false |EnterpriseAccount  | EnterpriseAccount   |
|address| 详细地址  | body | false |string  |    |
|area| 区县  | body | false |string  |    |
|audit| 认证信息：通过、不通过  | body | false |string  |    |
|auditTime| 认证审核时间  | body | false |date-time  |    |
|auditingTime| 认证申请时间  | body | false |date-time  |    |
|auditorId| 认证人  | body | false |string  |    |
|bankCode| 银行基本户帐号  | body | false |string  |    |
|bankName| 银行基本户开户行  | body | false |string  |    |
|city| 城市  | body | false |string  |    |
|contact| 联系人（管理员）姓名  | body | false |string  |    |
|contactType| 用户类型(企业用户、员工用户)  | body | false |string  |    |
|creditCode| 统一社会信用代码  | body | false |string  |    |
|enterpriseId| 企业编码  | body | false |string  |    |
|industry| 所属行业  | body | false |string  |    |
|name| 企业名称  | body | false |string  |    |
|permitUrl| 营业执照图片地址，来自文件上传后的src属性  | body | false |string  |    |
|phone| 联系人（管理员）电话  | body | false |string  |    |
|place| 注册场所地址  | body | false |string  |    |
|province| 省份  | body | false |string  |    |
|registerId| 注册人  | body | false |string  |    |
|registerTime| 注册时间  | body | false |date-time  |    |
|scale| 企业规模  | body | false |string  |    |
|status| 企业状态  | body | false |string  |    |
|telephone| 注册固定电话  | body | false |string  |    |

**EnterpriseAccount**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|cashBalance| 资金余额：例子：100.99  | body | false |number  |    |
|cashCredits| 授信额度，例子：100.99  | body | false |number  |    |
|enterpriseId| 企业编码  | body | false |string  |    |
|giveTotalIntegral| 累积发放积分，例子：100  | body | false |number  |    |
|integralBalance| 积分余额，例子：100  | body | false |number  |    |
|serviceRate| 服务费，例子：0.08  | body | false |number  |    |
|status| 账户状态  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Enterprise»|
| -1 | 企业编码（enterpriseId）不能为空  ||
| -2 | 企业名称不能为空  ||
| -3 | 企业管理员姓名不能为空  ||
| -4 | 只能修改自己的企业信息  ||
| -5 | 企业不存在  ||
| -994 | 其他未知异常  ||
## <s style="color:#d0d0d0;">企业认证审核通过(需admin权限)</s>

**接口说明**:审核通过


**接口地址**:`/api/enterprise/pass`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseId| enterpriseId  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": true,
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |boolean  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«boolean»|
## <s style="color:#d0d0d0;">企业认证管理查询(需admin权限)</s>

**接口说明**:企业认证管理查询


**接口地址**:`/api/enterprise/query4Audit`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 企业查询参数  | body | true |EnterpriseDBParam  | EnterpriseDBParam   |

**schema属性说明**



**EnterpriseDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_dnl_registerTime| 注册时间大于等于  | body | false |string  |    |
|_dnm_registerTime| 注册时间小于等于  | body | false |string  |    |
|_se_enterpriseId| 企业编码等于  | body | false |string  |    |
|_se_status| 状态等于，用中文，数据：启用、禁用、全部  | body | false |string  |    |
|_sk_contact| 姓名  | body | false |string  |    |
|_sk_name| 公司名称  | body | false |string  |    |
|_sk_phone| 手机号  | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
},
"address": "",
"area": "",
"audit": "",
"auditTime": "",
"auditingTime": "",
"auditorId": "",
"bankCode": "",
"bankName": "",
"city": "",
"contact": "",
"contactType": "",
"creditCode": "",
"enterpriseId": "",
"industry": "",
"name": "",
"permitUrl": "",
"phone": "",
"place": "",
"province": "",
"registerId": "",
"registerTime": "",
"scale": "",
"status": "",
"telephone": ""
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«Enterprise»  | DBResult«Enterprise»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«Enterprise»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | Enterprise   |

**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«DBResult«Enterprise»»|
## <s style="color:#d0d0d0;">查询企业用户(需admin权限)</s>

**接口说明**:查询企业用户


**接口地址**:`/api/enterprise/queryEnterpriseUser`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 企业查询参数  | body | true |EnterpriseDBParam  | EnterpriseDBParam   |

**schema属性说明**



**EnterpriseDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_dnl_registerTime| 注册时间大于等于  | body | false |string  |    |
|_dnm_registerTime| 注册时间小于等于  | body | false |string  |    |
|_se_enterpriseId| 企业编码等于  | body | false |string  |    |
|_se_status| 状态等于，用中文，数据：启用、禁用、全部  | body | false |string  |    |
|_sk_contact| 姓名  | body | false |string  |    |
|_sk_name| 公司名称  | body | false |string  |    |
|_sk_phone| 手机号  | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
},
"address": "",
"area": "",
"audit": "",
"auditTime": "",
"auditingTime": "",
"auditorId": "",
"bankCode": "",
"bankName": "",
"city": "",
"contact": "",
"contactType": "",
"creditCode": "",
"enterpriseId": "",
"industry": "",
"name": "",
"permitUrl": "",
"phone": "",
"place": "",
"province": "",
"registerId": "",
"registerTime": "",
"scale": "",
"status": "",
"telephone": ""
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«Enterprise»  | DBResult«Enterprise»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«Enterprise»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | Enterprise   |

**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«DBResult«Enterprise»»|
## <s style="color:#d0d0d0;">查询员工用户(需admin权限)</s>

**接口说明**:查询员工用户


**接口地址**:`/api/enterprise/queryStaffUser`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 员工用户查询参数  | body | true |StaffUserDBParam  | StaffUserDBParam   |

**schema属性说明**



**StaffUserDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_dnl_registerTime| 注册时间大于等于  | body | false |string  |    |
|_dnm_registerTime| 注册时间小于等于  | body | false |string  |    |
|_ne_account|   | body | false |string  |    |
|_se_status| 状态，中文：启用、禁用、全部  | body | false |string  |    |
|_sk_enterpriseName| 公司名称  | body | false |string  |    |
|_sk_name| 姓名  | body | false |string  |    |
|_sk_phone| 手机号码  | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"account": "",
"activate": "",
"department": {
"id": 0,
"departmentCode": "",
"departmentName": "",
"enterpriseId": 0
},
"departmentId": 0,
"enterprise": {
"id": 0,
"account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
},
"address": "",
"area": "",
"audit": "",
"auditTime": "",
"auditingTime": "",
"auditorId": "",
"bankCode": "",
"bankName": "",
"city": "",
"contact": "",
"contactType": "",
"creditCode": "",
"enterpriseId": "",
"industry": "",
"name": "",
"permitUrl": "",
"phone": "",
"place": "",
"province": "",
"registerId": "",
"registerTime": "",
"scale": "",
"status": "",
"telephone": ""
},
"enterpriseId": "",
"identityId": 0,
"name": "",
"nickName": "",
"oprId": "",
"ownerIdentityId": 0,
"password": "",
"passwordType": "",
"phone": "",
"position": "",
"roles": [
{
"id": 0,
"name": ""
}
],
"staffAccount": {
"id": 0,
"enterpriseId": "",
"integralBalance": 0,
"staffId": "",
"status": ""
},
"status": "",
"type": ""
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«StaffUser»  | DBResult«StaffUser»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«StaffUser»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | StaffUser   |

**StaffUser**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 账号，不能修改，长度小于等于128   |string  |    |
|activate | 是否激活(已激活、未激活)   |string  |    |
|department | 部门   |HomeDepartment  | HomeDepartment   |
|departmentId | 部门编码   |int32  |    |
|enterprise | 员工所在企业   |Enterprise  | Enterprise   |
|enterpriseId | 企业编码   |string  |    |
|identityId | 身份编码   |int32  |    |
|name | 名称   |string  |    |
|nickName | 昵称   |string  |    |
|oprId | 操作员编码   |string  |    |
|ownerIdentityId | 归属商户身份编码   |int32  |    |
|password | 密码   |string  |    |
|passwordType | 密码类型 , @See PasswordEncoderEnum   |string  |    |
|phone | 手机号   |string  |    |
|position | 岗位   |string  |    |
|roles | 角色   |array  | Role   |
|staffAccount | 员工账号   |StaffAccount  | StaffAccount   |
|status | 用户状态(启用，禁用)   |string  |    |
|type | 用户类型(企业管理员、普通员工)   |string  |    |

**HomeDepartment**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|departmentCode | 部门编码   |string  |    |
|departmentName | 部门名称   |string  |    |
|enterpriseId | 企业Id   |int32  |    |

**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**Role**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|name |    |string  |    |

**StaffAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|enterpriseId | 企业编码   |string  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|staffId | 员工编码   |string  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«DBResult«StaffUser»»|
## <s style="color:#d0d0d0;">修改企业服务费率(需admin权限)</s>

**接口说明**:修改企业服务费率


**接口地址**:`/api/enterprise/rate`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseId| enterpriseId  | query | false |string  |    |
|rate| rate  | query | false |number  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": true,
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |boolean  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«boolean»|
## <s style="color:#d0d0d0;">企业认证审核不通过(需admin权限)</s>

**接口说明**:审核不通过


**接口地址**:`/api/enterprise/unpass`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseId| enterpriseId  | query | false |string  |    |
|reason| reason  | query | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": true,
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |boolean  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«boolean»|
## 营业执照等文件上传

**接口说明**:文件上传


**接口地址**:`/api/enterprise/upload/{type}`


**请求方式**：`POST`


**consumes**:`["multipart/form-data"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|file| 文件  | formData | true |array  | MultipartFile   |
|type| type,可用值:Image,File  | path | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "base58": "",
        "name": "",
        "path": "",
        "size": "",
        "src": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |UploadResult  | UploadResult   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**UploadResult**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|base58 | 资源base58码   |string  |    |
|name | 资源名称   |string  |    |
|path | 资源在服务器上的相对cache路径   |string  |    |
|size | 文件大小   |string  |    |
|src | 资源http绝对路径   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«UploadResult»|
## 查询企业资料(需要admin权限)

**接口说明**:根据enterpriseId查询企业信息


**接口地址**:`/api/enterprise/{enterpriseId}`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseId| enterpriseId  | path | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«Enterprise»|
# 登录注册[张雪峰]

## 获取登录短信验证码

**接口说明**:获取登录时短信验证码


**接口地址**:`/opr/getLoginMsgCode`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|loginMobile| 手机号  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {},
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |object  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«object»|
| -1 | 短信验证码为空  ||
| -2 | 手机号未注册  ||
| -994 | 其他未知异常  ||
## 获取图片验证码

**接口说明**:获取登录时图形码验证


**接口地址**:`/opr/getLoginPicCode`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：
暂无


**响应数据**:


```json

```

**响应参数说明**:


暂无




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  ||
## 获取注册短信验证码

**接口说明**:获取注册时短信验证码


**接口地址**:`/opr/getRegisterMsgCode`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|registerMobile| 手机号  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {},
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |object  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«object»|
| -1 | 短信验证码为空  ||
| -2 | 手机号已经被注册，不能再次注册  ||
| -994 | 其他未知异常  ||
## 获取员工激活短信验证码

**接口说明**:获取员工激活短信验证码


**接口地址**:`/opr/getStaffActivateMsgCode`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|loginMobile| 手机号  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {},
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |object  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«object»|
| -1 | 手机号为空  ||
| -2 | 手机号未被添加  ||
| -994 | 其他未知异常  ||
## 企业登录

**接口说明**:企业登录,phone必填,pwd和msgCode只填其一!


**接口地址**:`/opr/login`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|msgCode| 短信验证码  | query | true |string  |    |
|phone| 手机号码  | query | true |string  |    |
|pwd| 登录密码  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "access_token": "",
        "token_type": "",
        "refresh_token": "",
        "expires_in": 0,
        "scope": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Token  | Token   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Token**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|access_token | 访问令牌   |string  |    |
|token_type | 令牌类型   |string  |    |
|refresh_token | 刷新令牌   |string  |    |
|expires_in | 到期时长   |int32  |    |
|scope | 范围   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Token»|
| -1 | 用户名不能为空  ||
| -2 | 密码不能为空  ||
| -3 | 用户名不存在  ||
| -4 | 密码错误  ||
| -5 | 短信验证码不正确  ||
| -6 | 此账号不是企业用户  ||
| -994 | 其他未知异常  ||
## 企业注册

**接口说明**:企业注册


**接口地址**:`/opr/register`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterprise| 企业  | body | true |Enterprise  | Enterprise   |
|msgCode| 短信验证码  | query | true |string  |    |
|phone| 手机号码  | query | true |string  |    |
|picCode| 图片验证码  | query | true |string  |    |
|pwd| 登录密码  | query | true |string  |    |

**schema属性说明**



**Enterprise**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|account| 企业账户信息  | body | false |EnterpriseAccount  | EnterpriseAccount   |
|address| 详细地址  | body | false |string  |    |
|area| 区县  | body | false |string  |    |
|audit| 认证信息：通过、不通过  | body | false |string  |    |
|auditTime| 认证审核时间  | body | false |date-time  |    |
|auditingTime| 认证申请时间  | body | false |date-time  |    |
|auditorId| 认证人  | body | false |string  |    |
|bankCode| 银行基本户帐号  | body | false |string  |    |
|bankName| 银行基本户开户行  | body | false |string  |    |
|city| 城市  | body | false |string  |    |
|contact| 联系人（管理员）姓名  | body | false |string  |    |
|contactType| 用户类型(企业用户、员工用户)  | body | false |string  |    |
|creditCode| 统一社会信用代码  | body | false |string  |    |
|enterpriseId| 企业编码  | body | false |string  |    |
|industry| 所属行业  | body | false |string  |    |
|name| 企业名称  | body | false |string  |    |
|permitUrl| 营业执照图片地址，来自文件上传后的src属性  | body | false |string  |    |
|phone| 联系人（管理员）电话  | body | false |string  |    |
|place| 注册场所地址  | body | false |string  |    |
|province| 省份  | body | false |string  |    |
|registerId| 注册人  | body | false |string  |    |
|registerTime| 注册时间  | body | false |date-time  |    |
|scale| 企业规模  | body | false |string  |    |
|status| 企业状态  | body | false |string  |    |
|telephone| 注册固定电话  | body | false |string  |    |

**EnterpriseAccount**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|cashBalance| 资金余额：例子：100.99  | body | false |number  |    |
|cashCredits| 授信额度，例子：100.99  | body | false |number  |    |
|enterpriseId| 企业编码  | body | false |string  |    |
|giveTotalIntegral| 累积发放积分，例子：100  | body | false |number  |    |
|integralBalance| 积分余额，例子：100  | body | false |number  |    |
|serviceRate| 服务费，例子：0.08  | body | false |number  |    |
|status| 账户状态  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Enterprise»|
| -1 | 短信验证码不能为空  ||
| -2 | 短信验证码不正确  ||
| -3 | 手机号码已经被注册，不能再次注册  ||
| -4 | 企业名称不能为空  ||
| -5 | 企业联系人不能为空  ||
| -994 | 其他未知异常  ||
## 员工激活

**接口说明**:员工激活


**接口地址**:`/opr/staffActivate`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|msgCode| 短信验证码  | query | true |string  |    |
|phone| 手机号码  | query | true |string  |    |
|pwd| 登录密码  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Enterprise»|
| -1 | 手机号不能为空  ||
| -2 | 短信验证码不能为空  ||
| -3 | 密码不能为空  ||
| -4 | 短信验证码不正确  ||
| -5 | 手机号不存在  ||
| -6 | 密码长度应为6-20位  ||
| -994 | 发生各种其他的笼统的未知异常  ||
## 员工激活图片验证

**接口说明**:员工激活图片验证,忽略字母大小写


**接口地址**:`/opr/staffActivatePic`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|phone| 手机号码  | query | true |string  |    |
|picCode| 图片验证码  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Enterprise»|
| -1 | 短信验证码不能为空  ||
| -2 | 短信验证码不正确  ||
| -3 | 手机号码没有被添加，不能激活！  ||
| -4 | 企业名称不能为空  ||
| -5 | 企业联系人不能为空  ||
| -994 | 发生各种其他的笼统的未知异常  ||
## 员工登录

**接口说明**:员工登录,phone必填,pwd和msgCode只填其一!


**接口地址**:`/opr/staffLogin`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|msgCode| 短信验证码  | query | true |string  |    |
|phone| 手机号码  | query | true |string  |    |
|pwd| 登录密码  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "access_token": "",
        "token_type": "",
        "refresh_token": "",
        "expires_in": 0,
        "scope": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Token  | Token   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Token**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|access_token | 访问令牌   |string  |    |
|token_type | 令牌类型   |string  |    |
|refresh_token | 刷新令牌   |string  |    |
|expires_in | 到期时长   |int32  |    |
|scope | 范围   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Token»|
| -1 | 用户名不能为空  ||
| -2 | 密码不能为空  ||
| -3 | 用户名不存在  ||
| -4 | 密码错误  ||
| -5 | 短信验证码不正确  ||
| -6 | 此账号不是员工用户  ||
| -994 | 其他未知异常  ||
## 验证企业名称

**接口说明**:验证企业名称


**接口地址**:`/opr/validateEnterpriseName`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|enterpriseName| 企业名称  | query | true |string  |    |
|phone| 手机号码  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "account": {
"id": 0,
"cashBalance": 0,
"cashCredits": 0,
"enterpriseId": "",
"giveTotalIntegral": 0,
"integralBalance": 0,
"serviceRate": 0,
"status": ""
        },
        "address": "",
        "area": "",
        "audit": "",
        "auditTime": "",
        "auditingTime": "",
        "auditorId": "",
        "bankCode": "",
        "bankName": "",
        "city": "",
        "contact": "",
        "contactType": "",
        "creditCode": "",
        "enterpriseId": "",
        "industry": "",
        "name": "",
        "permitUrl": "",
        "phone": "",
        "place": "",
        "province": "",
        "registerId": "",
        "registerTime": "",
        "scale": "",
        "status": "",
        "telephone": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Enterprise  | Enterprise   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Enterprise**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|account | 企业账户信息   |EnterpriseAccount  | EnterpriseAccount   |
|address | 详细地址   |string  |    |
|area | 区县   |string  |    |
|audit | 认证信息：通过、不通过   |string  |    |
|auditTime | 认证审核时间   |date-time  |    |
|auditingTime | 认证申请时间   |date-time  |    |
|auditorId | 认证人   |string  |    |
|bankCode | 银行基本户帐号   |string  |    |
|bankName | 银行基本户开户行   |string  |    |
|city | 城市   |string  |    |
|contact | 联系人（管理员）姓名   |string  |    |
|contactType | 用户类型(企业用户、员工用户)   |string  |    |
|creditCode | 统一社会信用代码   |string  |    |
|enterpriseId | 企业编码   |string  |    |
|industry | 所属行业   |string  |    |
|name | 企业名称   |string  |    |
|permitUrl | 营业执照图片地址，来自文件上传后的src属性   |string  |    |
|phone | 联系人（管理员）电话   |string  |    |
|place | 注册场所地址   |string  |    |
|province | 省份   |string  |    |
|registerId | 注册人   |string  |    |
|registerTime | 注册时间   |date-time  |    |
|scale | 企业规模   |string  |    |
|status | 企业状态   |string  |    |
|telephone | 注册固定电话   |string  |    |

**EnterpriseAccount**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|cashBalance | 资金余额：例子：100.99   |number  |    |
|cashCredits | 授信额度，例子：100.99   |number  |    |
|enterpriseId | 企业编码   |string  |    |
|giveTotalIntegral | 累积发放积分，例子：100   |number  |    |
|integralBalance | 积分余额，例子：100   |number  |    |
|serviceRate | 服务费，例子：0.08   |number  |    |
|status | 账户状态   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 0 | 成功  ||
| 200 | OK  |JsonResult«Enterprise»|
| -1 | 手机号不能为空  ||
| -2 | 企业名称不能为空  ||
| -3 | 企业名称不正确  ||
| -4 | 企业全称错误  ||
| -994 | 发生各种其他的笼统的未知异常  ||
# 统一认证中心

## 验证token

**接口说明**:验证


**接口地址**:`/token/check`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|token| 令牌  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {},
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |object  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«object»|
## 认证，返回token

**接口说明**:获取


**接口地址**:`/token/get`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|password| 密码  | query | true |string  |    |
|username| 用户名  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "access_token": "",
        "token_type": "",
        "refresh_token": "",
        "expires_in": 0,
        "scope": ""
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |Token  | Token   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**Token**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|access_token | 访问令牌   |string  |    |
|token_type | 令牌类型   |string  |    |
|refresh_token | 刷新令牌   |string  |    |
|expires_in | 到期时长   |int32  |    |
|scope | 范围   |string  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«Token»|
## 刷新token

**接口说明**:刷新


**接口地址**:`/token/refresh`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|token| 令牌  | query | true |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {},
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |object  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«object»|
# 部门员工管理[朱标]

## create

**接口说明**:往数据库插入一条新的记录


**接口地址**:`/token/create`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|vo| 部门信息表  | body | true |HomeDepartment  | HomeDepartment   |

**schema属性说明**



**HomeDepartment**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|departmentCode| 部门编码  | body | false |string  |    |
|departmentName| 部门名称  | body | false |string  |    |
|enterpriseId| 企业Id  | body | false |int32  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "departmentCode": "",
        "departmentName": "",
        "enterpriseId": 0
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |HomeDepartment  | HomeDepartment   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**HomeDepartment**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|departmentCode | 部门编码   |string  |    |
|departmentName | 部门名称   |string  |    |
|enterpriseId | 企业Id   |int32  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«HomeDepartment»|
## deleteByPk

**接口说明**:从数据库删除一条记录


**接口地址**:`/token/deleteByPk`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|pk| pk  | query | false |integer  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": true,
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |boolean  |    |
|success| 是否成功  |boolean  |    |




**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«boolean»|
## findAll

**接口说明**:查询所有记录


**接口地址**:`/token/findAll`


**请求方式**：`GET`


**consumes**:``


**produces**:`["*/*"]`

**请求参数**：
暂无


**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": [
        {
"id": 0,
"departmentCode": "",
"departmentName": "",
"enterpriseId": 0
        }
    ],
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |array  | HomeDepartment   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**HomeDepartment**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|departmentCode | 部门编码   |string  |    |
|departmentName | 部门名称   |string  |    |
|enterpriseId | 企业Id   |int32  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«List«HomeDepartment»»|
## queryByPage

**接口说明**:分页查询消息配置


**接口地址**:`/token/queryByPage`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|param| 员工查询参数  | body | true |HomeDepartmentDBParam  | HomeDepartmentDBParam   |

**schema属性说明**



**HomeDepartmentDBParam**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|_se_departmentName|   | body | false |string  |    |
|_pageno| 页号:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[1,N]，从1开始</div>  | body | false |string  |    |
|_pagesize| 页宽:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认20，[1,10000]，上限1W，防止非法拖库查询</div>  | body | false |string  |    |
|_orderby| 排序字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">多个字段用英文逗号分割，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_desc| 排序方式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">[0,1]，默认升序0，降序1，用于SQL组装到order by的位置</div>  | body | false |string  |    |
|_pk| 主键:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用来按主键字段查询</div>  | body | false |string  |    |
|_queryParamOrders| 查询参数的属性顺序:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">排序在前的参数先组装；用于需要根据SQL的综合性能来调整查询参数的先后组装顺序；属性之间用英文逗号分割；比如：<br>setQueryParamOrders("\_se\_sex,\_sk\_name")；<br>那么生成的sql语句中关于\_se\_sex、\_sk\_name的条件（假如有值）就会组装在SQL语句Where条件的前面。</div>  | body | false |string  |    |
|selectFieldsString| 要查询的字段:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于不需要返回所有字段部分字段查询；多个字段英文逗号分割；空，则查询全部字段<br>注意：使用HQL进行查询时，如果设置了selectFieldsString属性，则对应的BaseVO.Class需要相应的构造方法；setSelectFieldsString("id,name,addr")</div>  | body | false |string  |    |
|selectFieldsUseVOType| 是否以BaseVO的结构返回:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">对应selectFieldsString，设置是否以BaseVO的结构返回</div>  | body | false |boolean  |    |
|queryAll| 是否查询所有记录:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，分页参数失效，默认false</div>  | body | false |boolean  |    |
|countOnly| 是否只做统计汇总:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">当设置为true时，只执行count查询语句，可以节约数据库开销，默认false</div>  | body | false |boolean  |    |
|queryConditions| 查询条件:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">用于获取所有设置的查询条件，可以用来添加或覆盖额外的条件设置：<br>getQueryConditions().put("sex", "M");<br>getQueryConditions().put("_se_sex", "F");</div>  | body | false |object  |    |
|cacheable| 是否使用查询缓存:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认使用Hibernate二级缓存，<br>org.hibernate.SQLQuery.setCacheable(true)</div>  | body | false |boolean  |    |
|cacheMode| 缓存模式:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;">默认缓存模式NORMAL，和cacheable配套使用<br>org.hibernate.SQLQuery.setCacheMode(true)<br>@See @enum org.hibernate.CacheMode</div>  | body | false |string  |    |
|contract| DBParam约定:<br><div style="line-height:1.2;color:#9B9B9B;font-size:9px;"><table style="margin:0px;"><tr><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th>    <th style="text-align:center;padding:0px 0px;color:#9B9B9B;">符号</th><th style="text-align:center;padding:0px 0px;color:#9B9B9B;">说明</th></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">n  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is null</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nn </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">is not null</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nm </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">l  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">e  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ne </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;"><></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nl </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">>=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">m  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">in</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nin</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not in</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">k  </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nk </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ei </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower=</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nei</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower<></td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sw </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">-%</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ew </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">%-</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">ki </td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower like</td>    <td style="text-align:center;padding:0px 0px;color:#9B9B9B;">nki</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">lower not like</td></tr><tr><td style="text-align:center;padding:0px 0px;color:#9B9B9B;">sql</td><td style="text-align:center;padding:0px 0px;color:#9B9B9B;" colspan=3>直接sql语句</td></tr></table>支持的类型：<br>String s{符号}，Number n{符号}，Date d{符号} <br>例子：<br>set\_lk\_name("岛主")：查询名称属性包含岛主的数据<br>set\_dnm\_registorTime("2018-01-01 12:00:00")：查询注册日期属性<=2018-01-01 12:00:00的数据<br>set\_ne\_id("10")：查询编号等于10的数据</div>  | body | false |string  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "rowCount": 0,
        "pageSize": 0,
        "pageNo": 0,
        "totalPage": 0,
        "datas": [
{
"id": 0,
"departmentCode": "",
"departmentName": "",
"enterpriseId": 0
}
        ]
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |DBResult«HomeDepartment»  | DBResult«HomeDepartment»   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**DBResult«HomeDepartment»**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|rowCount | 总记录数   |int32  |    |
|pageSize | 页宽   |int32  |    |
|pageNo | 页号   |int32  |    |
|totalPage | 总页数   |int32  |    |
|datas | 数据   |array  | HomeDepartment   |

**HomeDepartment**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|departmentCode | 部门编码   |string  |    |
|departmentName | 部门名称   |string  |    |
|enterpriseId | 企业Id   |int32  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«DBResult«HomeDepartment»»|
## update

**接口说明**:往数据库更新一条记录


**接口地址**:`/token/update`


**请求方式**：`POST`


**consumes**:`["application/json"]`


**produces**:`["*/*"]`

**请求参数**：

| 参数名称         | 说明     |     in |  是否必须      |  类型   |  schema  |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|vo| 部门信息表  | body | true |HomeDepartment  | HomeDepartment   |

**schema属性说明**



**HomeDepartment**

| 参数名称         | 说明    |     in |  是否必须   |  类型  |  schema |
| ------------ | -------------------------------- |-----------|--------|----|--- |
|id| 编码  | body | false |int32  |    |
|departmentCode| 部门编码  | body | false |string  |    |
|departmentName| 部门名称  | body | false |string  |    |
|enterpriseId| 企业Id  | body | false |int32  |    |

**响应数据**:


```json
{
    "code": 0,
    "type": "",
    "message": "",
    "exception": "",
    "data": {
        "id": 0,
        "departmentCode": "",
        "departmentName": "",
        "enterpriseId": 0
    },
    "success": true
}
```

**响应参数说明**:


| 参数名称         | 说明                             |    类型 |  schema |
| ------------ | -------------------|-------|----------- |
|code| 结果代码  |int32  |    |
|type| 结果类型  |string  |    |
|message| 错误信息  |string  |    |
|exception| 异常类  |string  |    |
|data| 结果数据  |HomeDepartment  | HomeDepartment   |
|success| 是否成功  |boolean  |    |



**schema属性说明**




**HomeDepartment**

| 参数名称         |  说明          |   类型  |  schema |
| ------------ | ------------------|--------|----------- |
|id | 编码   |int32  |    |
|departmentCode | 部门编码   |string  |    |
|departmentName | 部门名称   |string  |    |
|enterpriseId | 企业Id   |int32  |    |

**响应状态码说明**:


| 状态码         | 说明                             |    schema                         |
| ------------ | -------------------------------- |---------------------- |
| 200 | OK  |JsonResult«HomeDepartment»|
