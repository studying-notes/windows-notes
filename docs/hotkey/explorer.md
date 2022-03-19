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
