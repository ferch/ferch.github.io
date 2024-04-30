---
title: 各 android 模拟器 adb 连接端口
date: 2019-01-15 17:01:29
tags: android 
---

有时候手上没有真机，或者真机太慢。我们可以用 android 模拟器来完成开发测试，但是默认的 android 模拟器还是有点不太好用，太卡，内存占用大。所以我们可以选用一些其他的第三方模拟器，但是这些厂商一般会修改默认的 adb 连接端口。下面就是这些模拟器的连接端口一览。做个笔记，便于用到的时候查阅

* 夜神安卓模拟器 &nbsp;&nbsp;&nbsp;&nbsp;	 62001
* 逍遥安卓模拟器 &nbsp;&nbsp;&nbsp;&nbsp;	 21503
* BlueStacks（蓝叠安卓模拟器） 	5555
* 雷电安卓模拟器	&nbsp;&nbsp;&nbsp;&nbsp;5555
* 天天安卓模拟器 	&nbsp;&nbsp;&nbsp;&nbsp;5037
* 网易MuMu（安卓模拟器） 	7555
* 安卓模拟器大师 	&nbsp;&nbsp;&nbsp;&nbsp;54001
* Genymotion       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 5555

例如连接 MuMu 模拟器
```
adb connect 127.0.0.1:7555
```