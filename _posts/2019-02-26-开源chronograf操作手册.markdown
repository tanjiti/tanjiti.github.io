---
layout:     post
title:      "开源chronograf操作手册"
subtitle:   "时序数据可视化与kapacitor TICK编辑器"
date:       2019-02-26 15:00:00
author:     "tanjiti"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - telegraf
    - 时序数据可视化
---

# 基本概念

提供influxdb系统管理、kapacitor TICK脚本编辑与数据可视化。
我主要使用它进行tick脚本编辑，可视化的部分用的是鼎鼎有名的grafana




# 部署
## 安装

### mac

`brew install chronograf `

### centos

`wget https://dl.influxdata.com/chronograf/releases/chronograf-1.7.3.x86_64.rpm `

`sudo yum localinstall chronograf-1.7.3.x86_64.rpm`


## 启动

`brew services start chronograf `

`http://localhost:8888`

## 使用
### 数据源配置
#### 配置influxdb

![](/img/conf_chronograf_1.jpg)

#### 配置kapacitor

![](/img/conf-kapacitor.png)

### 报警编辑器

![](/img/alert_editor.png)

### TICK编辑器

![](/img/tick_editor.png)


### 数据可视化
#### 模版变量设置
[template-variables](https://docs.influxdata.com/chronograf/v1.7/guides/dashboard-template-variables/)

`show tag values on cpu_monitor from cpu  with key in ("cpu_id") where "machine_id" = :machine_id":`

### 数据库管理

![](/img/influxadmin.png)
