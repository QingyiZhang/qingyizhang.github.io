---
layout: post
title: XX软件授权微信小程序
categories: [微信小程序, 授权]
description: 便于授权简单写了一个小程序
keywords: 小程序, 授权
---

为了随时随地能够快速授权，编写了一个微信小程序，主要是通过输入软件运行环境的机器码，通过sha1加密算法生成一个授权码，完成软件的的授权。
本阶段仅仅做了授权，未与服务器进行通信，由于未购买服务器，暂时仅仅是微信单机版本。后续计划配置服务器后，
用户可以通过微信输入机器码后，由管理员负责确认直接生成授权码发送给申请用户，同时也能够统计软件授权次数等等信息。

![授权小程序](/images/posts/00_mini_program.png)