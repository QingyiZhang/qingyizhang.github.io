---
layout: post
title: tar包按照指定大小压缩
categories: [tar, linux]
description: tar file as fixed size
keywords: tar, fixed size
---

## 按照指定大小压缩tar包
* 普通tar压缩命令
```
tar -zcvf test.tar.gz testfolder
```

* 将tar包拆分成指定大小
```
split -b 500M -d -a 1 test.tar.gz test.tar.gz.
```

* 直接压缩成指定大小的压缩包
```
tar -zcvf test.tar.gz testfolder | split -b 500M -d -a 1 -test.tar.gz.
```

* 普通解压命令
```
tar -zvxf test.tar.gz
```

* 分割后的压缩包解压命令
```
cat test.tar.gz.* | tar -zxv
```

