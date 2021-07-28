---
title: "Android系统启动流程"
subtitle: ""
date: 2021-07-28T16:15:50+08:00
lastmod: 2021-07-28T16:15:50+08:00
draft: false
authors: []
description: "xxxx什么垃圾玩意儿，看的头疼"

tags: [Android]
categories: []
series: [AndroidFramework]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

<!--more-->
### 内核空间流程

1. 按下开机键。
2. 加载启动引导程序bootloader到内存并执行。
3. 拉起linux内核，设置缓存，加载驱动.

### 用户空间流程

4. 调用init(pid=1)方法，启动init进程，进程id=1。
5. 创建和挂载文件目录。
6. 初始化【属性服务】。
7. 解析init.rc，
8. 启动zygote（孵化器）
9. 启动MediaService
10. 创建launcher

### init.rc文件

由Android初始化语言（AIL）编写的脚本，

1. 挂载目录
2. 