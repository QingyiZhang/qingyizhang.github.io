---
layout: post
title: 基于银河麒麟V10服务器版yum官方源搭建离线源
categories: [kylin, offline, yum, repo]
description: build offline kylin v10 server repo base on offical repo
keywords: repo, offline, yum, kylin 
---

基于官方源搭建银河麒麟V10服务器版(x86)离线源

## 准备工作
* 准备一台安装Kylin server V10的虚拟机
* 安装创建yum仓库使用的软件工具
```
sudo yum install createrepo yum-utils -y
```

* 移除其他软件镜像，在/etc/yum.repos.d/下仅保留一个.repo
* 修改kylin_v10_server.repo的内容，将url更改为官方源地址
```
[base]
name= cs2c base repo
baseurl=https://update.cs2c.com.cn/NS/V10/V10SP1/os/adv/lic/base/x86_64/
gpgcheck=0
enable=1
```

* 清除缓存
```
sudo yum clean all
sudo yum makecache
```

## 同步银河麒麟官方源的yum源到本地
* 找一个空间足够大(约20GB)的目录,如 ~/kylin_repo
* 同步镜像至本地目录
```
reposync
```

## 创建本地yum仓库
* 为本地仓库，生成新的repo文件
```
cd ~/kylin_repo/base
createrepo ./

```

