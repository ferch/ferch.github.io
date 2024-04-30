---
title: Linux 删除目录下的某类型文件或文件夹
date: 2018-08-29 11:52:39
tags: Linux 
---

有这个问题是因为用vscode打开了android studio 项目后突然多了一些项目默认文件
例如.project .classpath和.setttings 文件夹，这些文件又会干扰到git的同步处理，
开始手动删除，觉得很费时费力，还有可能删错。然后就查了需要批量删除的命令。如下

<!-- more -->

```
 find . -name ".project" -print -exec rm -rf {} \;
```
```
 find . -name ".classpath" -print -exec rm -rf {} \;
```
```
 find . -name ".setttings" -print -exec rm -rf {} \;
```
- "."    表示从当前目录开始递归查找
- “ -name “*.*“” "根据名称来查找，要查找所有以.exe结尾的文件夹或者文件
- "-print" 输出查找的文件目录名
- 最主要的是是-exec了，-exec选项后边跟着一个所要执行的命令，表示将find出来的文件或目录执行该命令。
     exec选项后面跟随着所要执行的命令或脚本，然后是一对儿{}，一个空格和一个\，最后是一个分号