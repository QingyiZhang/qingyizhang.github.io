---
layout: post
title: 麒麟V10离线仓库机器构建步骤
categories: [kylin, v10, offline, repos]
description: 构建麒麟V10的离线yum源机器
keywords: yun, kylin, offline
---

## 构建麒麟V10离线yum源
### 目的
用于构建离线yum源，用于作为无网络环境的麒麟V10的离线仓库
### 配置步骤
* 全新安装麒麟V10 Server SP2机器
* 修改yum配置，支持yum安装软件进行缓存，用于后面制作离线包
```shell
sudo vim /etc/dnf/dfn.conf

cachedir=/home/yum/$basearch/$releasever
keepcache=1
```

<++>
