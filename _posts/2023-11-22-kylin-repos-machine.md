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

* 编译python3.9

```shell
./configure --enable-shared --enable-optimizations --prefix=/usr/local/python3
make -j10
sudo make altinstall
```

* 编译vim9.0
```shell
CFLAGS=-fPIC ./configure --with-features=huge --enable-multibyte --enable-python3interp --enable-luainterp --enable-gui=gtk2 --enable-cscope --prefix=/usr
```

* 安装vimplus

* 编译YouCompleteMe
需要python、vim、gcc等具备相应的版本

下面是正常的编译
```shell
python3 install.py --clangd-completer
```

如果gcc版本不够，自行编译了gcc后，则用下面的命令编译ycm,下面的路径是编译的gcc的路径
```shell
CXX="/usr/local/gcc/bin/c++" ./install.py --clangd-completer
```

### 其他
* python多环境管理 pyenv [pyenv](https://blog.51cto.com/yangxingzhen/5980290) 
* 编译gcc 8.5 [参考](https://blog.csdn.net/ShenSeKyun/article/details/126280142?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-126280142-blog-132343133.235^v38^pc_relevant_anti_t3&spm=1001.2101.3001.4242.1&utm_relevant_index=3) 

```shell
sudo yum install bzip2 wget gcc gcc-c++ gmp-devel mpfr-devel libmpc-devel make
```

<++>
