---
layout: post
title: 银河麒麟下编译python3.9
categories: [kylin, python]
description: 银河麒麟下编译python3
keywords: kylin, python
---

## 安装依赖
```shell
sudo apt-get update
sudo apt-get install build-essential zlib1g-dev libbz2-1.0 libssl-dev libncurses5-dev libsqlite3-dev libreadline-dev tk-dev libgdbm-dev libdb5.3 libpcap-dev xz-utils libexpat1-dev liblzma-dev openssl libffi-dev libc6-dev
```

## 编译过程
* 源码解压
```shell
tar -vxf Python-3.9.tar.xz
```

* 执行配置文件，安装
```shell
./configure --enable-shared --enable-optimizations --prefix=/usr/local/python3
make -j10
sudo make altinstall
```

* 建立软连接
```shell
sudo ln -s /usr/local/python3/bin/python3.9 /usr/bin/python39
sudo ln -s /usr/local/python3/bin/pip3.9 /usr/bin/pip3

```

## 其他
* python3: error while loading shared libraries: libpython3.9.so.1.0: cannot open shared
将python3.9的绝对路径加入ldconfig中
```shell
vim /etc/ld.so.conf.d/python3.conf

/usr/local/lib
ldconfig
```

