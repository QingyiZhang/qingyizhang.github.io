---
layout: post
title: 配置Ngnix为银河麒麟局域网更新源
categories: [ngnix, kylin]
description: using ngnix as a http kylin resp
keywords: ngnix, kylin
---

## 配置ngnix为银河麒麟局域网更新源

* 安装ngnix
    * 通过源码、rpm包或yum install ngnix安装即可
* 配置ngnix

修改ngnix的配置如下：
```
server {
    listen 80;
    listen [::]:80;
    server_name 192.168.100.15  update.mysofts.com;
    location / {
        root /data/yum_data/;
        autoindex on; #开启目录浏览功能
    }
 }
```

