---
layout: post
title: Mac下VSCode升级报错Cannot update while running on a read-only volume
categories: [VSCode, Mac]
description: Cannot update while running on a read-only volume
keywords: VSCode, read-only volume
---

*问题：*

在Mac下点击VSCode自动更新，在右下角提示“Cannot update while running on a read-only volume”错误。

*解决措施：*

运行如下命令行：

sudo chown $USER ~/Library/Caches/com.microsoft.VSCode.ShipIt

xattr -dr com.apple.quarantine /Applications/Visual\ Studio\ Code.app

*参考链接：*

https://github.com/Microsoft/vscode/issues/7426