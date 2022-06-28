---
date: 2021-01-23T14:03:24+08:00  # 创建日期
author: "Rustle Karl"  # 作者

title: "Windows 上四种不同的文件链接方式"
url:  "posts/windows/docs/link"
tags: [ "windows", "mklink"]
categories: [ "Windows 常见问题与技巧"]

index: true  # 是否可以被索引
toc: true  # 是否自动生成目录
draft: false  # 草稿
---

## 不同的链接方式

使用 mklink 命令，可以创建“硬链接（Hard Link）”、“目录联接（Junction Point）”和“符号链接（Symbolic Link）”。

```cmd
MKLINK [[/D] | [/H] | [/J]] Link Target

        /D        创建目录符号链接。默认为文件符号链接。
        /H        创建硬链接而非符号链接。
        /J         创建目录联接。
        Link      指定新的符号链接名称。
        Target  指定新链接引用的路径 (相对或绝对)。
```

## 快捷方式

快捷方式是一个单纯 Windows 操作系统用户层面的功能，与 NTFS 文件系统没有什么关系。不过其也能实现链接到另一个文件的功能。

快捷方式的本质是一个 lnk 后缀的文件，这个文件里面指向了如何打开目标文件或文件夹的一些参数，于是当在文件资源管理器中打开快捷方式时，就直接打开了目标文件或文件夹。

| | 硬链接（Hard Link） | 目录联接（Junction Point） | 符号链接（Symbolic Link） |
| --------------- | ----------------- | ---------------- | ---------------- |
| 命令 | `mklink /H Link Target` | `mklink /J Link Target` | `mklink /D Link Target` |
| 作用 | 为某文件创建别名，可让不同的路径对应同一个文件的数据。 | | |
| 链接到文件 | ✔️ | ❌ | ❌ |
| 链接到文件夹 | ❌ | ✔️ | ✔️ |
| 需要提升为管理员权限 | 需要 | 不需要 | 通常需要 |
| 跨驱动器卷（盘符） | ❌ | ✔️（仅本地计算机） | ✔️（包括 SMB 文件或路径） |
| 操作系统支持 | Windows NT 3.1 开始支持 Windows 2000 开始有 API `CreateHardLink()` Windows NT 6.0 开始能使用 `mklink /H` | Windows 2000+ | Windows Vista+ |
| 可链接到不存在的目标 | ❌ | ✔️ | ✔️ |
| 可链接到相对目录 | ❌ | ❌（可以使用相对路径创建，但创建完即变绝对路径） | ✔️ |
| 删除方法 | del | rd | rd / del |
| 当链接被单独删除后 | 只有所有指向原始文件的硬链接和原始文件全部删除后文件数据才会被删除。 | Windows Vista 之后原始文件夹不受影响；Windows 2000/XP/2003 会导致原始子文件夹被删除。 | 原始文件夹不受影响。 |
| 当原始文件被单独删除后 | 硬链接依然能正常访问到文件的数据。 | 目录联接失效，指向不存在的目录。 | 符号链接失效，指向不存在的目录。 |
