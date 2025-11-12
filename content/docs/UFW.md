---
weight: 10
title: UFW
description: 
icon: menu_book
lead: ""
date: 2025-11-12T10:19:25+08:00
lastmod: 2025-11-12T10:19:45+08:00
draft: false
images: []
---

UFW是Ubuntu自带的防火墙工具,基于`iptables`,命令更加简化,更容易配置和使用
默认情况下`ufw`处于禁用状态(`inactive`)
```
root@lige:~# ufw status verbose
Status: inactive
```
可以通过下面的命令启用:
```bash
sudo ufw enable
```
启用前需要先添加一些规则
使用`sudo ufw app list`可以查看预定义的规则
```
$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
  Postfix
  Postfix SMTPS
  Postfix Submission
```
例如可以启用Openssh:
```bash
sudo ufw allow OpenSSH
```
也可以直接通过端口号开放:
```bash
sudo ufw allow 22
```
