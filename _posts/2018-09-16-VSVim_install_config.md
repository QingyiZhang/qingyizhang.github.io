---
layout: post
title: VSVim 安装及配置
categories: [VS2010, VSVim]
description: VS2010下配置使用VSVim
keywords: VSVim, shortcuts
---

# VSVim 安装及配置

已经习惯使用 Vim 了，奈何工作环境是 Windows 而且还基本限制在 VS2010 上，故配置一下 VSVim 提升一下
码代码的速度。

## VSVim 安装

1.VSVim 的安装包在巨硬的官网上有，此处不列举。下载下来后安装，提示安装包无效，通过巨硬网站看最新版本
的 VSVim 仅支持 VS2012 以上版本，故此路不通，通过提供的 GitHub 链接找到以往的 Release 版本下载即可。

2.[VSVim GitHub](https://github.com/jaredpar/VsVim), 通过 Release 页面[下载 VS2010 可用版本](https://github.com/jaredpar/VsVim/releases/download/VsVim-1.8.0.0/VsVim.vsix) , 
最后一个 VS2010 可用的 VSVim 版本[下载](https://vsvim.blob.core.windows.net/drops/VsVim-2.1.1.0.vsix)

3.在安装包VSVim.vsix 上右键 ‘安装’ 即可。

## VSVim 配置过程

1.在 VSVim 的命令行输入 :set 查看 vimrcPaths 所在位置

2.在 vimrcPaths 文件夹建立一个名为 _vsvimrc 的文件，没有扩展名

3.将要写的配置加入其中

4.重新启动 VS2010

## VSVim 配置文件

[一个配置的文档](https://fuqua.io/blog/2017/08/level-up-your-vsvim/)

    set ai
    
    "自动缩进宽度
    set sw=4
    set ts=4

    "关闭高亮显示
    set nohlsearch

    set is
    set ignorecase
    set backspace=indent,eol,start
    set clipboard=unnamed
    set number
    :nnoremap . .<Esc>
    "重新生成选中项目的解决方案快捷键
    :nnoremap ,b :vsc Build.RebuildSelection<CR>
    
    :inoremap jj <esc>
    :nnoremap <c-j> <c-w>j
    :nnoremap <c-k> <c-w>k
    :nnoremap <c-l> <c-w>l
    :nnoremap <c-h> <c-w>h
    
    :nnoremap <c-o> :vsc View.NavigateBackward<CR>
    :nnoremap <c-i> :vsc View.NavigateForward<CR>
    
    :nnoremap ,t :vsc Window.NextTab<CR>
    :nnoremap ,r :vsc Window.PreviousTab<CR>
    
    :nnoremap ,n :vsc Window.NextDocumentWindow<CR>
    :nnoremap ,p :vsc Window.PreviousDocumentWindow<CR>
    
    "显示错误列表的快捷键
    :nnoremap cl :vsc View.ErrorList<CR>
    :nnoremap cn :vsc View.NextError<CR>
    :nnoremap cp :vsc View.PreviousError<CR>
    
    "添加注释
    "vv是为了退出visual line模式
    :vnoremap ci :s/^/\/\/<cr>vv
    :vnoremap cu :s/\/\//<cr>vv
    :nnoremap ci :s/^/\/\/<cr>
    :nnoremap cu :s/\/\//<cr>
    
    "居中显示查找结果
    :nnoremap n nzz
    :nnoremap N Nzz
    :nnoremap * *zz
    :nnoremap # #zz
    "去定义
    :nnoremap gd <C-]>zz
    
    "gq->== 整理代码格式
    :nnoremap gq ==
    :vnoremap gq ==
    
    "format code
    :nnoremap == :vsc Edit.FormatDocument<CR>
    
    "重命名
    :nnoremap gr :vsc VAssistX.RefactorRename<CR>
    
    "查看函数列表 list methods
    :nnoremap zm :vsc VAssistX.ListMethodsInCurrentFile<CR>
    
    "查找所有引用--
    :nnoremap ca :vsc Edit.FindAllReferences<CR>
    "或者使用VA的命令（vs2017中使用va命令比较好）
    " :nnoremap ca :vsc VAssistX.FindReferences<CR>
    
    "打开查看类的对话框
    :nnoremap cs :vsc VAssistX.FindSymbolDialog<CR>
    
    "打开查看文件的对话框
    :nnoremap cf :vsc VAssistX.OpenFileInSolutionDialog<CR>
    
    "open VAOutline
    :nnoremap co :vsc VAssistX.VAOutline<CR>
    
    "打开解决方案资源管理器
    :nnoremap cv :vsc View.SolutionExplorer<CR>
    
    "查找在当前文件中的引用
    :nnoremap cj :vsc VAssistX.FindReferencesinFile<CR>
    
    "在文件中查找
    :nnoremap ck :vsc Edit.FindinFiles<CR>
    
    "打开文件所在文件夹
    :nnoremap cm :vsc File.OpenContainingFolder<CR>
    
    "快速查看方法定义
    :nnoremap zj :vsc Edit.QuickInfo<CR>
    
    "快速查看方法的所有定义,鼠标在方法parameter上的时候显示的东西
    :nnoremap zk :vsc Edit.ParameterInfo<CR>
    
    "打开查找符号结果
    :nnoremap zs :vsc View.FindSymbolResults<CR>
    
    "打开查找结果1
    :nnoremap zi :vsc View.FindResults1<CR>
    
    "打开查找结果2
    :nnoremap zu :vsc View.FindResults2<CR>
    
    "打开va的在本文件中查找结果
    :nnoremap ,i :vsc VAssistX.FindReferencesResults<CR>
    
    "实现interface接口
    :nnoremap zp :vsc VAssistX.RefactorImplementInterface<CR>
    
    "可视模式中，使用 * 和 # 查找
    :vnoremap * "/y/<C-r>/<CR>
    :vnoremap # "/y?<C-r>/<CR>
    
    "打开折叠或者关闭折叠
    :nnoremap <space> za
    
