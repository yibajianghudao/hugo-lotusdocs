---
weight: 200
title: Hugo_Lotusdocs
description: 
icon: menu_book
lead: ""
date: 2025-11-12T10:24:20+08:00
lastmod: 2025-11-12T10:24:20+08:00
draft: false
images: []
---

打算把文章从hexo框架迁移到hugo框架,使用lotusdocs主题,本地使用Obsidian编辑
## 安装
### 安装hugo
参考[Install Hugo on Linux](https://gohugo.io/installation/linux/)
### 安装lotusdocs
参考[How to deploy Lotus Docs on GitHub Pages](https://lotusdocs.dev/docs/deployment/platforms/github-pages/)
注意该教程漏写了一步
```
hugo mod tidy
```
在编辑`hugo.toml`之后,`hugo new docs/example-page.md`之前.参考这个[issue](https://github.com/colinwilson/lotusdocs/issues/220)
## 配置
存在两个文件夹:
- git仓库,我这里是`~/Code/yibajianghudao.github.io`
- Obsidian文档目录,我这里是`/home/mintuser/Code/obsidian`
整体思路:
1. 创建完仓库后,在Obsidian应用中打开该Obsidian文档目录,新建一个`docs`目录,在其中编写文章
2. 通过`~/Code/obsidian/copy.sh`脚步将`~/Code/obsidian/docs`目录下的所有文章复制到~/Code/yibajianghudao.github.io/content/docs`
3. 通过git命令推送到远程仓库
其中在Obsidian编写文章之前需要进行下面的配置:

在 设置-核心插件-模板-配置 中:
- `Template`目录设置为`~/Code/obsidian/Template` 
- `time`格式设置为`HH:mm:ssZ`,主要用于hugo的日期格式
在`~/Code/obsidian/Template`新建一个文件`hugo-lotusdocs`:
```
+++
weight = 100
title = '{{Title}}'
description = ''
icon = 'article'
date = {{date}}T{{time}}
lastmod = {{date}}T{{time}}
draft = false
toc = true
+++

```
在编写其他文章之前在左侧插入模板中选择`hugo-lotusdocs`.
>不要使用`---`替代`+++`,Obsidian会把`---`格式中的`true`转换为`"true"`,无法被`hugo`正常识别
## 参考
[My Obsidian + Hugo blogging setup](https://4rkal.com/posts/obsidianhugo/)