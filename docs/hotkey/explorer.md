---
date: 2022-03-19T11:54:14+08:00
author: "Rustle Karl"

title: "将 Win+E 改成指定的其他文件浏览器"
url:  "posts/windows/docs/hotkey/explorer"  # 永久链接
tags: [ "Windows", "README" ]  # 标签
series: [ "Windows 学习笔记" ]  # 系列
categories: [ "学习笔记" ]  # 分类

toc: true  # 目录
draft: false  # 草稿
---

## 改成指定的其他文件浏览器

- Create a backup of the registry.
- Open the registry editor.
- Navigate to Computer\HKEY_CLASSES_ROOT\Folder\shell\opennewwindow\command
- Set the default keys value to C:\Users\Admin\AppData\Local\Microsoft\WindowsApps\files.exe -Directory %1
- Delete the DelegateExecute key

## 文件夹双击打开异常的解决办法

### 问题表现

双击打开文件夹，会调用各种乱七八糟的程序来打开，包括但不限于：

- visual studio
- adobe bridge

打开“文件所在路径”，会调用各种乱七八糟的程序来打开。

使用一些其他软件打开文件夹时，会调用各种乱七八糟的程序来打开。

### 原因

注册表中文件夹的关联方式出现错误

### 解决办法

- win+R，regedit 打开注册表
- 注册表编辑器左侧定位到：HKEY_CLASSES_ROOT\Directory\shell。
- 查看 shell 的键值是否为：none，如果数值未设置或者不是 none，改成 none。
- 打开文件资源管理器检查是否解决问题。

### 分析

出错的主要原因是 shell 的键值为“数值未设置”。当 shell 键值为“数值未设置”时，系统会自动调用 shell 下的第一个项目来打开文件夹。
