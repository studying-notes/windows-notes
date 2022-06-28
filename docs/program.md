---
date: 2022-06-28T17:17:28+08:00
author: "Rustle Karl"

title: "获取正在运行的程序的启动命令"
url:  "posts/windows/docs/program"  # 永久链接
tags: [ "Windows", "README" ]
categories: [ "Windows 学习笔记" ]

toc: true  # 目录
draft: false  # 草稿
---

## 通过软件获取

https://download.sysinternals.com/files/ProcessExplorer.zip

## 通过 wmic 获取

> 必须以管理员运行

```cmd
wmic process where caption="nutsvpn.exe" get caption,commandline,ProcessId /value
```

```cmd
wmic process where caption="msedge.exe" get caption,commandline,ProcessId /value
```
