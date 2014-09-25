---
layout: post
title: Linux中的一些点
category: 技术
tags: Linux
keywords: Linux
---

## 前言 ##
本文记录一些日常使用linux的一些点。

## Linux中的引号 ##

首先，单引号和双引号，都是为了解决中间有空格的问题。

- 单引号

	当shell碰到第一个单引号时，它忽略掉其后直到右引号的所有特殊字符

- 双引号

	双引号只要求忽略大多数，具体说，括在双引号中的三种特殊字符不被忽略：美元符号，反斜杠和反引号

- 反引号

	命令替换：在执行一条命令时，会先将其中反引号之间的语句，或者是`$()`中的语句当作命令执行一遍，再将结果加入到原命令中重新执行。其中，`$()`格式受到POSIX标准支持，也利于嵌套。

## pid文件 ##

- pid文件内容：pid文件为文本文件，内容只有一行, 记录了该进程的ID。 

- pid文件作用：防止进程启动多个副本。只有获得pid文件(固定路径固定文件名)写入权限(F_WRLCK)的进程才能正常启动并把自身的PID写入该文件中。其它同一个程序的多余进程则自动退出。

## socket文件 ##

## source和**.** 命令##

未完待续