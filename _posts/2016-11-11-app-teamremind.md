---
layout: post
title:  应用接入-团队消息提醒
date:   2016-11-11 14:00:00 +0800
categories: document
tag: 服务端开发文档
---

* content
{:toc}


## 1.	创建团队消息提醒

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/teamremind/create?accessToken=ACCESSTOKEN `

* POST消息体：

` {
	"requesterUid" : "",
	"requesterName" : "",
	"detail" : {
		"createTime" : "",
		"content" : "",
		"remindTime" : "", 
		"remindType" : "",
		"members" : [{
			"uid" : "", 
			"name" : ""
		}...
		]	
	}
}`

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
requesterName | 是 | 请求者name
detail | 是 |  团队提醒详细信息
createTime | 是 |  团队提醒创建时间戳
content | 是 |  团队提醒内容
remindTime | 是 |  提醒时间
remindType | 是 |  提醒类型 0:应用内, 1:sms
members | 是 |  提醒人员信息
uid | 是 |  提醒人员uid
name | 是 |  提醒人员name

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0,"data":{"teamRemindId":111234}}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
teamRemindId | 团队提醒id


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```

## 2.	取消团队消息提醒(仅限提醒创建者调用)

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/teamremind/cancel?accessToken=ACCESSTOKEN `


* POST消息体：

` {
	"requesterUid" : "",
	"teamRemindId" : ""
} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
teamRemindId | 是 | 团队提醒id

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

## 3.	删除团队消息提醒(将提醒标签从工作台移除)

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/teamremind/delete?accessToken=ACCESSTOKEN `

* POST消息体：

` {
	"requesterUid" : "",
	"teamRemindId" : ""
} `

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
teamRemindId | 是 | 团队提醒id

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

## 4.	更新团队消息提醒(仅限提醒创建者调用)

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/teamremind/update?accessToken=ACCESSTOKEN `

* POST消息体：

` {
	"requesterUid" : "",
	"teamRemindId" : "",
	"detail" : {
		"createTime" : "",
		"content" : "",
		"remindTime" : "", 
		"remindType" : "",
		"members" : [{
			"uid" : "", 
			"name" : ""
		}...
		]	
	}
}`

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
teamRemindId | 是 | 团队提醒id
detail | 是 |  团队提醒详细信息
createTime | 是 |  团队提醒创建时间戳
content | 是 |  团队提醒内容
remindTime | 是 |  提醒时间
remindType | 是 |  提醒类型 0:应用内, 1:sms
members | 是 |  提醒人员信息
uid | 是 |  提醒人员uid
name | 是 |  提醒人员name

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

## 5.	获取团队消息提醒详情

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/teamremind/detail?accessToken=ACCESSTOKEN `

* POST消息体：

` {
	"requesterUid" : "",
	"teamRemindId" : ""
} `


* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
teamRemindId | 是 | 团队提醒id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{
	"status":0,
	"data":{
		"createrId" : "",
		"createrName" : "",
		"pushStatus" : "",
		"detail" : {
			"createTime" : "",
			"content" : "",
			"remindTime" : "",
			"remindType" : "",
			"members" : [ 
			{ 
				"uid" : "", 
				"name" : "",
				"msgStatus" : "",
				"isRemind" : "" 
			}...
			]
		}
	}
}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
createrId | 提醒创建者uid
createrName | 提醒创建者name
pushStatus | 提醒状态 0:未推送, 1.已推送, 2.取消提醒
detail | 提醒详细信息
createTime | 提醒创建时间戳
content | 提醒内容
remindTime | 提醒开始时间戳
remindType | 提醒提醒类型 0:应用内, 1:sms
members | 提醒人员
uid | 提醒人员uid
name | 提醒人员name
msgStatus | 提醒消息状态：0-未读, 1-已读未操作, 2-确定, 3-拒绝
isRemind | true:允许消息提醒；false:不允许消息提醒


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```