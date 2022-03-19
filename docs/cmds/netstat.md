---
date: 2020-10-11T21:33:01+08:00  # 创建日期
author: "Rustle Karl"  # 作者

# 文章
title: "解决 Windows 端口占用类问题"  # 文章标题
# description: "文章描述"
url:  "posts/windows/netstat"  # 设置网页永久链接
tags: [ "windows", "netstat"]  # 标签
series: [ "Windows 常见问题与技巧"]  # 系列

# 章节
weight: 20 # 排序优先级
chapter: false  # 设置为章节

index: true  # 是否可以被索引
toc: true  # 是否自动生成目录
draft: false  # 草稿
---

## 查询端口占用

```shell
netstat -aon|findstr xxx
```

## 根据 PID 终止进程

```
taskkill -f -pid 13008
```

## 根据程序名终止进程

```shell
tasklist|findstr xxx
```

```shell
taskkill /f /t /im xxx.exe
```

## 端口占用但是查询不到

执行以下命令：

```shell
netsh interface ipv4 show excludedportrange protocol=tcp
```

```
协议 tcp 端口排除范围

开始端口    结束端口
----------    --------
      1026        1125
      1126        1225
      1226        1325
      1326        1425
      1461        1560
      1652        1751
      5357        5357
     13342       13441
     13442       13541
     13542       13641
     13642       13741
     13763       13862
     13863       13962
     50000       50059     *

* - 管理的端口排除。
```

这些是 Hyper-H 保留的端口范围，如果运行的程序恰好在这些范围就，可能就提示端口被占用。

## 修改保留端口范围

1. 关闭 Hyper-V

```shell
dism.exe /Online /Disable-Feature:Microsoft-Hyper-V
```

2. 排除某些端口

Jetbrains

```shell
netsh int ipv4 add excludedportrange protocol=tcp startport=6942 numberofports=200
```

Docker

```shell
netsh int ipv4 add excludedportrange protocol=tcp startport=14000 numberofports=100
```

1. 开启 Hyper-V

```shell
dism.exe /Online /Enable-Feature:Microsoft-Hyper-V /All
```

