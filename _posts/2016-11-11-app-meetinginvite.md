---
layout: post
title:  应用接入-会议邀请
date:   2016-11-11 14:00:00 +0800
categories: document
tag: 服务端开发文档
---

* content
{:toc}

## 1.	创建会议邀请

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/meetinginvite/create?accessToken=ACCESSTOKEN `

* POST消息体：

```javascript 
{
	"requesterUid" : "",
	"requesterName" : "",
	"detail" : {
		"createTime" : "",
		"content" : "",
		"address" : "",
		"beginTime" : "",
		"endTime" : "",
		"remindMin" : "",
		"remindType" : "",
		"members" : [
		{ 
			"uid" : "",
			"name" : ""
		}
		]
	}
} 
```

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
requesterName | 是 | 请求者name
detail | 是 |  会议邀请详细信息
createTime | 是 |  会议创建时间戳
content | 是 |  会议内容
address | 是 |  会议地址
beginTime | 是 |  会议开始时间戳
endTime | 是 |  会议结束时间戳
remindMin | 是 |  会议前多少分钟提醒
remindType | 是 |  会议提醒类型 0:应用内, 1:sms
members | 是 |  参加会议人员信息
uid | 是 |  参会人员uid
name | 是 |  参会人员name

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```javascript
{
	"status":0,
	"data":{
		"meetingInviteId":111234
	}
}
```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
meetingInviteId | 会议邀请id


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```javascript
{
	"status":4003,
	"message":"accessToken超时，请重新获取"
}
```

## 2.	取消会议邀请(仅限会议创建者调用)

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/meetinginvite/cancel?accessToken=ACCESSTOKEN `

* POST消息体：

```javascript 
{
	"requesterUid" : "",
	"meetingInviteId" : ""
} 
```

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
meetingInviteId | 是 | 会议邀请id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```javascript
{
	"status":0
}
```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```javascript
{
	"status":4003,
	"message":"accessToken超时，请重新获取"
}
```

## 3.	删除会议邀请(将会议标签从工作台移除)

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/meetinginvite/delete?accessToken=ACCESSTOKEN `

* POST消息体：

```javascript 
{
	"requesterUid" : "",
	"meetingInviteId" : ""
} 
```

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
meetingInviteId | 是 | 会议邀请id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```javascript
{
	"status":0
}
```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```javascript
{
	"status":4003,
	"message":"accessToken超时，请重新获取"
}
```

## 4.	更新会议邀请详情(仅限会议创建者调用)

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/meetinginvite/update?accessToken=ACCESSTOKEN `

* POST消息体：

```javascript
{
	"requesterUid" : "",
	"meetingInviteId" : "",
	"detail" : {
		"createTime" : "", 
		"content" : "", 
		"address" : "", 
		"beginTime" : "", 
		"endTime" : "", 
		"remindMin" : "", 
		"remindType" : "", 
		"members" : [ 
		{ 
			"uid" : "", 
			"name" : "" 
		}
		]
	}
}
```

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
meetingInviteId | 是 | 会议邀请id
detail | 是 |  会议邀请详细信息
createTime | 是 |  会议创建时间戳
content | 是 |  会议内容
address | 是 |  会议地址
beginTime | 是 |  会议开始时间戳
endTime | 是 |  会议结束时间戳
remindMin | 是 |  会议前多少分钟提醒
remindType | 是 |  会议提醒类型 0:应用内, 1:sms
members | 是 |  参加会议人员信息
uid | 是 |  参会人员uid
name | 是 |  参会人员name

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```javascript
{
	"status":0
}
```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```javascript
{
	"status":4003,
	"message":"accessToken超时，请重新获取"
}
```

## 5.	获取会议邀请详情

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/workbench/meetinginvite/detail?accessToken=ACCESSTOKEN `

* POST消息体：

```javascript 
{
	"requesterUid" : "",
	"meetingInviteId" : ""
} 
```

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
requesterUid | 是 |  请求者id
meetingInviteId | 是 | 会议邀请id

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户

```javascript
{
	"status":0,
	"data":{
		"createrId" : "",
		"createrName" : "",
		"pushStatus" : "",
		"detail" : {
			"createTime" : "",
			"content" : "",
			"address" : "",
			"beginTime" : "",
			"endTime" : "",
			"remindMin" : "",
			"remindType" : "",
			"members" : [ 
			{ 
				"uid" : "", 
				"name" : "",
				"msgStatus" : "",
				"remind" : ""
			}
			]
		}
	}
}
```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
createrId | 会议创建者uid
createrName | 会议创建者name
pushStatus | 会议邀请状态 0:未推送, 1.已推送, 2.取消会议
detail | 会议详细信息
createTime | 会议创建时间戳
content | 会议内容
address | 会议地址
beginTime | 会议开始时间戳
endTime | 会议结束时间戳
remindMin | 会议前多少分钟提醒
remindType | 会议提醒类型 0:应用内, 1:sms
members | 参加会议人员
uid | 参会人员uid
name | 参会人员name
msgStatus | 会议消息状态：0-未读, 1-已读未操作, 2-确定, 3-拒绝
remind | true:允许消息提醒；false:不允许消息提醒


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```javascript
{
	"status":4003,
	"message":"accessToken超时，请重新获取"
}
```
