+++
menu = ""
comments = true
date = "2017-02-09T16:42:36+08:00"
slug = "rsync-fedora-repository"
title = "rsync fedora repository"
author = ""
share = true
draft = false
image = "images/cover.jpg"
tags = ["fedora","rsync"]

+++

USTC rsync 服务地址
```bash
rsync://rsync.mirrors.ustc.edu.cn （智能解析，推荐）
rsync://cernet.mirrors.ustc.edu.cn（仅解析教育网，推荐）
rsync://mobile.mirrors.ustc.edu.cn（仅解析中国移动）
```

USTC Repository 同步状态 
```bash
https://mirrors.ustc.edu.cn/status/
```

mirors for rpmfusion by rsync:
```bash
rsync -avrzP rsync://rsync.mirrors.ustc.edu.cn/rpmfusion/free/fedora/releases/24/Everything/x86_64/os/ ./os
```
mirrors for fc24 by rsync:
```bash
rsync -avrzP rsync://mirrors.tuna.tsinghua.edu.cn/fedora/releases/24/Everything/x86_64/os/ ./os
```
