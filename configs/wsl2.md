---
date: 2020-10-08T17:03:08+08:00  # 创建日期
author: "Rustle Karl"  # 作者
# cover: "/examples/imgs"  # 封面图，可以是相对于 static 的路径，也可以是相对于当前的路径

# 文章
title: "WSL2"  # 文章标题
url:  "posts/windows/wsl2"  # 设置网页链接，默认使用文件名
tags: [ "windows", "wsl2"]  # 自定义标签

# 章节
weight: 20 # 文章在章节中的排序优先级，正序排序
chapter: false  # 将页面设置为章节

index: true  # 文章是否可以被索引
draft: true  # 草稿
toc: true  # 是否自动生成目录
---

## 关闭 WSL

```powershell
wsl --shutdown
```

## 限制内存

```ini
[wsl2]
memory=12GB
```

```powershell

```
