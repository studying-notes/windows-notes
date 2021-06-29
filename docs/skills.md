---
date: 2020-10-11T21:57:50+08:00  # 创建日期
author: "Rustle Karl"  # 作者

# 文章
title: "Windows 实用命令"  # 文章标题
url:  "posts/windows/skills"  # 设置网页永久链接
tags: [ "windows", "skills"]  # 标签
series: [ "Windows 常见问题与技巧"]  # 系列

# 章节
weight: 20 # 排序优先级
chapter: false  # 设置为章节

index: true  # 是否可以被索引
toc: true  # 是否自动生成目录
draft: false  # 草稿
---

## 快速删除大量文件

> cmd 下有效

```shell
DEL /F/Q/S *.*
```

## 正则匹配删除文件

```shell
rmdir -r "c:/path/to/folder/*/*/*.url"
rmdir -r "./*/*.url"
```

```shell
rmdir -r "c:/path/to/folder/*/*/*.txt"
```

## 复制文件夹

```shell
robocopy "e:/OneDrive" "h:/OneDrive" /s /mt:32
```

- /s 复制子目录，但不复制空的子目录
- /e 复制子目录，包括空的子目录
- /b 在备份模式下复制文件
- /xf 排除与给定名称/路径/通配符匹配的文件
- /xd 排除与给定名称/路径匹配的目录
- /mov 移动文件
- /move 移动文件和目录
- /r:3 失败副本的重试次数
- /w:3 两次重试间的等待时间
- /eta 显示复制文件的预期到达时间
- /mt:32 启动多线程任务

```shell

```

```shell

```

```shell

```

```shell

```

## 重启资源管理器

```shell
taskkill /f /im explorer.exe
explorer.exe
```

## 获取文件的 MD5 码

```shell
certutil -hashfile file_path MD5
```

## 打开休眠功能

```shell
powercfg -h on
powercfg /a
```
