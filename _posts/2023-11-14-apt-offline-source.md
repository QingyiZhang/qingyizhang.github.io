---
layout: post
title: 创建apt离线源
categories: [apt, offline]
description: 创建apt离线源
keywords: apt, offline resp
---

使用google搜索关键词apt download package and dependencies终于找到了可以用的

创建一个目录如下：
```shell
mkdir -p /opt/offline-packages/archives
cd /opt/offline-packages/archives
```

执行如下命令会将vim的递归依赖都下载到/opt/offline-packages/archives目录内：
```shell
sudo apt-get download $(apt-cache depends --recurse --no-recommends --no-suggests --no-conflicts --no-breaks --no-replaces --no-enhances vim | grep "^\w" | sort -u)
```

**vim后可以跟其他要下载的包** 

建立依赖的命令
```shell
cd /opt/offline-packages
sudo dpkg-scanpackages -m . /dev/null | gzip -9c > Packages.gz
cp Packages.gz ./archives
```

带上-m，会将所有包全部建立依赖关系到 Packages.gz中，如此会有重复，但无需剔除重复的包

最后打包供其他服务器使用
```shell
tar -zcvf offline-apt-packages.tar.gz offline-packages
```

**打包的库记录** 
* vim
* python3.8
* python-dev
* python3-dev
* gcc
* g++
* git
* cmake
* zsh
* lib32stdc++6

**其他源码** 
* lazygit
* ranger
