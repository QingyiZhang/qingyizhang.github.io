---
layout: post
title: 开发服务器配置过程记录
categories: [server, config]
description: 服务器配置
keywords: vim, ranger, zsh, lazygit
---

# 开发服务器配置

## 准备

* 配置更新源
    * YH Kylin V10 Server 
        * 由于centos于2021年底停止维护，部分配置源的方式已失效
        * ~~银河麒麟所谓的官网打不开，更新不了 update.cs2c.com.cn 这个网址ping不通~~
        * 删除系统内置的更新源，更换为centos的源.具体参见[银河麒麟V10服务器版更新源](https://itcn.blog/p/2824309483.html)
    * Mac
        * 安装brew
* 配置zsh(无特殊说明，两个系统均一样)
    * 安装oh-my-zsh
        * 安装zsh: yum install zsh
        * 切换shell: chsh -s /bin/zsh
        * 安装oh-my-zsh: sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
        * 提示安装成功
    * 配置zsh
        * 配置参见 [配置oh-my-zsh](https://www.alicode.pro/blog/dev-tools/better-use-terminal-with-zsh)
        * 配置主题为: powerlevel10k, 然后按照提示进行配置
        * 配置插件：zsh-autosuggestions、zsh-highlighting、z、[thefuck](https://github.com/nvbn/thefuck)
* 配置VIM
    * 安装vimplus [vimplus](https://github.com/chxuan/vimplus)
    * **针对YHKylin** 修改 vimplus中的install.sh 将获取系统名称中，增加 kylin 返回 CentOS
    * 解决vim启动后报 ycmd server shutdown的问题: 在 .vim/plugged/YouCompleteMe下运行python install.py即可
* 配置Ranger
    * 在YHkylin下安装python后，没有安装pip，需要按照[YHkylin下手动安装pip](https://icode.best/i/19584245910097)
    * pip-2 install ranger-fm 即可安装
    * ranger --copy-config=all 拷贝ranger配置文件
    * 安装fzf搜索神器 [fzf安装](https://www.jianshu.com/p/aeebaee1dd2b)
    * 在ranger中配置命令直接打开lazygit等
        * 在ranger的rc.conf中添加 map git console shell lazygit即可 前面的git代表快捷键 后面console代表在命令行中运行shell的命令lazygit
* 配置lazygit
    * **MAC** brew install lazygit
    * **YHKylin** 采用二进制形式安装，从github上下载相应的安装包 [安装lazygit](https://www.igiftidea.com/article/10823887226.html)
* 其他
    * [命令行工具](https://blog.csdn.net/u012811805/article/details/118886814?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-118886814-blog-121925000.pc_relevant_multi_platform_featuressortv2dupreplace&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-118886814-blog-121925000.pc_relevant_multi_platform_featuressortv2dupreplace&utm_relevant_index=1)
