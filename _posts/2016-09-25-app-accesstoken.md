---
layout: post
title:  应用接入-获取accessToken
date:   2016-09-25 01:08:00 +0800
categories: document
tag: 服务端开发文档
---

* content
{:toc}

## 1.	获取接口调用凭据（accessToken）
> accessToken是开放平台的全局唯一票据，开放平台各接口时都需使用accessToken。开发者需要进行妥善保存。accessToken的存储至少要保留512个字符空间。accessToken的有效期目前为2个小时，需定时刷新，重复获取将导致上次获取的accessToken失效。

* 2.1 为了保密appSecrect，第三方需要一个accessToken获取和刷新的中控服务器。而其他业务逻辑服务器所使用的accessToken均来自于该中控服务器，不应该各自去刷新，否则会造成accessToken覆盖而影响业务；
* 2.2 目前accessToken的有效期通过返回的expireIn来传达，目前是7200秒之内的值。中控服务器需要根据这个有效时间提前去刷新新accessToken。在刷新过程中，中控服务器对外输出的依然是老accessToken，此时公众平台后台会保证在刷新短时间内，新老accessToken都可用，这保证了第三方业务的平滑过渡；
* 2.3 accessToken的有效时间可能会在未来有调整，所以中控服务器不仅需要内部定时主动刷新，还需要提供被动刷新accessToken的接口，这样便于业务服务器在API调用获知accessToken已超时的情况下，可以触发accessToken的刷新流程。
使用AppID和AppSecret调用本接口来获取accessToken。AppID和AppSecret可在邮件回复中获得（需要提供上述的开发者信息邮件给超级管理员，且帐号没有异常状态）

**接口调用请求说明**


* https请求方式: GET


` https://api.open.jituancaiyun.com/openapi/token/get?appId=APPID&appSecret=APPSECRET`

* 参数说明：

参数 | 是否必须 | 描述
------------ | ------------- | -------------
appId | 是 | 应用注册成功后返回
appSecret | 是 | 应用注册成功后返回

* 返回说明：
正常情况下开放平台会返回下述JSON数据包给用户


```

{"status":0,"data":{"accessToken":"MDAwMjM0M0RBNjIwMURENDAxOTJDRkE0MkVGMDlERjQ5MjVFODAzQTlFMThERDBCMzNBNzFEMjBFMkRCNjExRDgxQjM3RkU0QzM1NkMwQzM5NkNCODUyN0JFQTE1OUE5OUUzMg==","expiresIn":7200}}

```

参数 | 描述
------------ | -------------
status | 开放平台处理状态
data | 处理成功后会把数据字段放到这里
accessToken | 访问凭据
expiresIn | 凭证有效时间，单位：秒

错误时开放平台会返回错误码等信息，JSON数据包示例如下（该示例为AppID无效错误）

```
{"status":4007,"message":"获取accessToken时appId或者appSecret错误"}

```