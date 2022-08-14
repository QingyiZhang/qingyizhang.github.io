---
layout: post
title: Vim下采用vimspector调试C++程序
categories: [vim, debug, c++]
description: debug cpp under vim
keywords: vim, cpp, debugger
---

# Vim下采用Vimspector调试C++
## 安装vimspector
在vimrc中添加如下配置(插件管理采用Plug)：
```
Plug 'puremourning/vimspector'
let g:vimspector_enable_mappings = 'HUMAN'
```

执行:PlugInstall 安装即可。

上面的HUMAN是vimspector自带的一套快捷键，如下：

| 按键         | 功能                     | 备注                          |
|--------------|--------------------------|-------------------------------|
|              |                          |                               |
| F5           | 启动调试或继续调试       | vimspector#Contiune()         |
| F3           | 停止调试                 | vimspector#Stop()             |
| F4           | 以相同的配置重新启动调试 | vimspector#Restart()          |
| F6           | 暂停调试                 | vimspector#Pause()            |
| F9           | 当前行增加一个断点       | vimspector#ToggleBreakPoint() |
| \<leader> F9 | 在当前行增加一个条件断点 |                               |
| F10          | Step Over跳过            |                               |
| F11          | Step Into进入            | vimspector#StepInto()         |
| F12          | 跳出当前函数             |                               |

**安装调试语言C++** 

在~/.vim/plugged/vimspector目录下执行
```
./install.py --enable-c
```

即可下载相应系统下的cpp-tools.vsix

## 配置vimspector
在~/.vim/plugged/vimspector/gadgets/macos下添加.gadgets.json文件
```
{
    "adapters": {
        "vscode-cpptools": {
            "attach": {
                "pidProperty": "processId",
                "pidSelect": "ask"
            },
        "command": [
            "${gadgetDir}/vscode-cpptools/debugAdapters/OpenDebugAD7"
        ],
        "name": "cppdbg"
        }
    }
}
```
## 项目配置

在项目下添加.vimspector.json
```
{
  "configurations": {
    "cpp:launch": {
      "adapter": "vscode-cpptools",
      "configuration": {
        "name": "cpp",
        "type": "cppdbg",
        "request": "launch",
        "program": "${fileDirname}/a.out",
        "args": ["*${ProgramArgs}"],
        "cwd": "${workspaceRoot}",
        "environment": [],
        "externalConsole": false,
        "stopAtEntry": true,
        "MIMode": "lldb",
        "logging": {
          "engineLogging": true
        }
      }
    }
  }
}
```

其中program是本地的项目编译后的文件。

## 调试C++程序

vim打开xxx.cpp文件 F9添加断点 F5进入调试,F11逐步调试即可。
