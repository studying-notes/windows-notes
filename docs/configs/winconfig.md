---
date: 2020-09-05T11:01:49+08:00  # 创建日期
author: "Rustle Karl"  # 作者

# 文章
title: " Windows 系统重装后的基本配置"  # 文章标题
description: "每次系统重装、更换新的系统/硬件，开发环境的重新搭建都是一个巨大的工程"
url:  "posts/windows/winconfig"  # 设置网页链接，默认使用文件名
tags: [ "windows", "config", "wsl2", "docker"]  # 自定义标签
series: [ "系统重装基础配置"]  # 文章主题/文章系列
categories: [ "基础配置"]  # 文章分类

# 章节
weight: 20 # 文章在章节中的排序优先级，正序排序
chapter: false  # 将页面设置为章节

index: true  # 文章是否可以被索引
draft: false  # 草稿
---

## Windows Terminal

建议搜索 WT 相关文章。

## PowerShell Core

## WSL 2.0

Setp 0 - 查询现有 WSL

```shell
wsl -l -v
```

```shell
  NAME                   STATE           VERSION
* docker-desktop         Running         2
  docker-desktop-data    Running         2
  Ubuntu                 Running         1
```

将 WSL 1 转换为 WSL 2

```shell
wsl --set-version Ubuntu 2
```

Setp 1 - 启用适用于 Linux 的 Windows 子系统

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Setp 2 - 启用虚拟机功能

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Setp 3 - 下载安装 Linux 内核更新包

**[wsl_update_x64.exe](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)**

Setp 4 - 将 WSL 2 设置为默认版本

```powershell
wsl --set-default-version 2
```

**[官网文档](https://docs.microsoft.com/zh-cn/windows/wsl/install-win10)**

### Ubuntu WSL

在 Microsoft Store 下载启动，设置用户名、密码即可。

详细配置请搜索相关文章。

## Docker & WSL2

WSL2 仍必须下载安装 Docker Desktop：

**[Latest](https://download.docker.com/win/stable/Docker%20Desktop%20Installer.exe)**

Docker 官网有关 WSL 的文档说明 https://docs.docker.com/docker-for-windows/wsl/ 。

关键在于开启下图所示的功能：

![](https://i.loli.net/2020/12/05/XIy9j64MzxvKWmw.png)

## GCC

移动目录后运行安装程序进行修复即可。

```ini
C:\Developer\tdm64-gcc\bin
```

## Python3 / Anaconda3

https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive

```shell
pip install toolkit-py # 个人工具包
```

```shell
chs # 换源
```

## GO

### 下载安装

[Download Page](https://studygolang.com/dl)

### 目录设置

```shell
go env -w GOBIN=C:\Developer\go\bin
```

```shell
go env -w GOPATH=C:\Developer\gopath
```

> `go env` 设置死循环的问题：通过设置 Windows 系统的环境变量解决。

### 模块代理

```shell
go env -w GOPROXY=https://goproxy.cn,direct
go env -w GOSUMDB=off
go env -w GO111MODULE=on
```

```shell

```

```shell

```

```shell

```

```shell

```

```shell

```

```shell

```

```shell

```
