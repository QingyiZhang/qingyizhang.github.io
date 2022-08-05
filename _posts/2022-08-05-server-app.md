---
layout: post
title: 开发服务器安装应用环境记录
categories: [server, apps]
description: redis poco server
keywords: redis, poco
---

## 开发服务器应用安装

### Redis数据库
* 下载[Redis](https://download.redis.io/redis-stable.tar.gz)
* 安装Redis
    * 解压 tar -zvxf redis-stable.tar.gz
    * cd redis-stable
    * make
    * make install
* 运行测试
    * redis-server 默认启动6379端口的standalone模式数据库
    * 采用配置文件启动，修改为后台启动模式
        *拷贝一份redis.conf文件至/etc/redis/redis.config下
        *修改redis.config 中的 daemonize 为yes
        * redis-server /etc/redis/redis.config 启动
    * redis-cli 链接
        * keys * 查看当前存在的key
