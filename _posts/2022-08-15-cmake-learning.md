---
layout: post
title: CMake使用学习
categories: [cmake, c++]
description: CMake使用
keywords: cmake
---

## CMake使用学习
### CMake关键字

* project关键字

    可以用来指定工程的名字和支持的语言，默认支持所有语言
    * project(hello) 工程名字为hello，支持所有语言
    * project(hello cxx) 工程名字为hello，支持c++语言
    * **默认生成了两个变量** hello_binary_dir, hello_source_dir
    * 可以使用系统自带的两个变量：project_binary_dir, project_source_dir

* set关键字
    * todo
