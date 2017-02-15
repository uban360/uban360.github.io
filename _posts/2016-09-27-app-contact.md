---
layout: post
title:  应用接入-通讯录管理
date:   2016-08-27 01:08:00 +0800
categories: document
tag: 服务端开发文档
---

* content
{:toc}

## 1.	获取部门列表

* https请求方式: GET


` https://api.open.jituancaiyun.com/openapi/department/list?deptId=0&accessToken=ACCESSTOKEN`

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
deptId | 是 | 部门id(根部门传0)

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0,"data":{"departments":[{"id":1,name:"开发部","parentid":1}, {"id":2,name:"测试部","parentid":1}...]}}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
departments | 部门列表数据
id | 部门id
name | 部门名称
parentid | 父部门id(根部门为0)
sequence | 部门排序

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 2.	创建部门

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/department/create?accessToken=ACCESSTOKEN `

* POST消息体：

` {"name":"芒果医生", "parentid":"0"} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
name | 是 | 部门名称(长度限制为1~64个字符)
parentid | 是 | 父部门id(根部门为0)
sequence | 否 | 部门排序

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0,"data":{"id":"230332"}}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
id | 部门id

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 3.	更新部门

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/department/update?accessToken=ACCESSTOKEN `

* POST消息体：

` {"name":"芒果医生", "parentid":"0", "id":"23004"} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
name | 是 | 部门名称(长度限制为1~64个字符)
parentid | 是 | 父部门id(根部门为0)
id | 是 | 部门id
sequence | 否 | 部门排序

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 4.	删除部门

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/department/delete?accessToken=ACCESSTOKEN `

* POST消息体：

` {"id":"23004"} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
id | 是 | 部门id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 5.	获取部门下所有人员

* https请求方式: GET


` https://api.open.jituancaiyun.com/openapi/user/list?accessToken=ACCESSTOKEN&deptId=DEPTID `


* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
deptId | 是 | 部门id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0,"data":{
"users":
[{"id":123, "name":"张三", "mobile":"18268080277", "title":"我的职位", "sequence":"我的顺序"},
{"id":124, "name":"李四", "mobile":"18268080277", "title":"我的职位", "sequence":"我的顺序"},
...]}}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
id | 用户id
name | 名字
title | 职位
mobile | 手机号
sequence | 该人在该部门下的排序

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 6.	新增人员

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/user/create?accessToken=ACCESSTOKEN `

* POST消息体：

` {
    "deptId": 1,
    "mobile":"18806886887",
    "title":"销售小弟",
    "name":"旻浩1",
    "sequence":1
} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
name | 是 | 名字
title | 否 | 职位
deptId | 是 | 父部门id(根部门为0)
mobile | 是 | 手机号
sequence | 否 | 该人在该部门下的排序(为空则默认在最后一个)

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0,"data":{"id":"230332"}}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
id | 人员id

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 7.	修改人员

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/user/update?accessToken=ACCESSTOKEN `

* POST消息体：

` {
    "deptId": 1,
    "oldDeptId" : 1,
    "mobile":"18806886887",
    "id":"12",
    "title":"销售小弟",
    "name":"旻浩1",
    "sequence":1
} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
deptId | 否 | 部门id(为空则不修改)
oldDeptId | 否 | 老的部门id(为空则不修改)
mobile | 否 | 手机号(为空则不修改)
id | 是 | 人员id
title | 否 | 职位(为空则不修改)
name | 否 | 人员名字(为空则不修改)
sequence | 否 | 该人在该部门下的排序(为空则不修改)

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 8.	删除人员

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/user/delete?accessToken=ACCESSTOKEN `

* POST消息体：

` {"id":"23004", "deptId":"1232"} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
deptId | 是 | 父部门id(根部门为0)
id | 是 | 人员id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 9.   获取人员详细

* https请求方式: GET


` https://api.open.jituancaiyun.com/openapi/user/detail?accessToken=ACCESSTOKEN&deptId=DEPTID&uid=UID `


* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
token | 是 |  客户端拼接上的token
deptId | 是 | 部门id
uid | 是 | 人员id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{
    "status":0,
    "data":
        {
            "id":123, 
            "name":"张三", 
            "mobile":"18268080277", 
            "title":"我的职位", 
            "sequence":"我的顺序",
            "adminRole":"管理员角色"
        }
}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
id | 用户id
name | 名字
title | 职位
mobile | 手机号
sequence | 该人在该部门下的排序
adminRole | 管理员角色(1:超级管理员，2:企业管理员，0:普通员工，无角色)

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```