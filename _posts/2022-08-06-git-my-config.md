---
layout: post
title: 使用Git管理配置文件
categories: [git, config]
description: manage config files using git
keywords: git, config
---

# 使用Git管理配置文件
1. 新建bare仓库
    
在$HOME文件夹下新建一个文件夹用来存放 git 版本树。然后初始化为 bare 仓库。

```
mkdir ~/.qyconfig
git init --bare ~/.qyconfig
```

1. 创建git命令别名

直接在家目录运行git命令肯定是不行的，因为家目录不是一个 git repo，不包含 .git 文件夹。所以甚至命令别名如下：

```
alias config='/usr/bin/git --git-dir=$HOME/.qyconfig/ --work-tree=$HOME'
```

将别名写入.zshrc中，后续shell中都可以使用。config status 查看是否生效。

1. 使用.gitignore文件

在home目录下创建.gitignore文件
```
#! $HOME/.gitignore
#----[ ignore all ] -----
*
#---[ consider list ]---
!*.conf
!*.oh-my-zsh
!*.vimrc*
!*.zshrc
!*.config
#---[ ignore list ]---
```

1. 后续使用config (git)操作即可
