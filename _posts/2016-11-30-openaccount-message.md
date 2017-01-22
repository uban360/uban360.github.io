---
layout: post
title:  应用接入-服务号消息发送
date:   2016-11-30 11:00:00 +0800
categories: document
tag: 服务端开发文档
---

* content
{:toc}


## 1.	服务号发送消息

* https请求方式: POST


` https://api.open.jituancaiyun.com/openapi/openaccount/sendmsg?accessToken=ACCESSTOKEN `

* POST消息体：

` {
	"appId" : "",
	"msgType" : "",
	"msgBody" : {
		"content" : "",
		"picUrl" : "",
		"articleCount" : "", 
		"articles" : [{
			"title" : "", 
			"description" : "",
			"picUrl" : "",
			"url" : ""
		}...
		]	
	},
	"receivers" : [{
		"uid" : ""
	}...
	]
}`

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
appId | 是 |  应用Id
msgType | 是 | 发送消息类型
msgBody | 是 |  消息内容
content | 是 |  文字消息内容
picUrl | 是 |  图片消息内容
picUrl | 是 |  图片消息内容
articleCount | 是 |  图文消息内容数量
articles | 是 |  图文消息内容数组
title | 是 |  图文消息标题
description | 是 |  图文消息描述
picUrl | 是 |  图文消息图片
url | 是 |  图文消息内容链接地址
receivers | 是 |  消息接受者信息数组
uid | 是 |  消息接受者id

## 1.1 消息类型说明
## 1.1.1 文本消息

* POST消息体：

` {
	"appId" : "",
	"msgType" : "text",
	"msgBody" : {
		"content" : ""
	},
	"receivers" : [{
		"uid" : ""
	}...
	]
}`

## 1.1.2 图片消息

* POST消息体：

` {
	"appId" : "",
	"msgType" : "image",
	"msgBody" : {
		"picUrl" : ""
	},
	"receivers" : [{
		"uid" : ""
	}...
	]
}`

## 1.1.3 图文消息

* POST消息体：

` {
	"appId" : "",
	"msgType" : "news",
	"msgBody" : {
		"articleCount" : "1", 
		"articles" : [{
			"title" : "", 
			"description" : "",
			"picUrl" : "",
			"url" : ""
		}...
		]	
	},
	"receivers" : [{
		"uid" : ""
	}...
	]
}`

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态


错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为accessToken超时）

```
{"status":4003,"message":"accessToken超时，请重新获取"}

```
