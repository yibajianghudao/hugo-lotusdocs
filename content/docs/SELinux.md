---
weight: 200
title: SELinux
description: 
icon: menu_book
lead: ""
date: 2025-11-12T10:24:27+08:00
lastmod: 2025-11-12T10:24:27+08:00
draft: false
images: []
---

## 关闭selinux
临时关闭
```
# 切换为 Permissive（警告模式，不拦截）
sudo setenforce 0
# 验证
getenforce
# 输出: Permissive
```
永久关闭
```
sudo vim /etc/selinux/config
# 把enforcing改成disabled
SELINUX=disabled
sudo reboot
```
> 修改为permissive可以允许但保留日志
