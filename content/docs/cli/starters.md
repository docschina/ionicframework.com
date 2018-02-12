---
layout: fluid/cli_docs_base
category: cli
id: cli-starter-list
page_name: Starter Templates
title: Starter Templates - Ionic CLI Documentation
hide_header_search: true
dark_header: true
---


{% comment %}
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
DO NOT MODIFY THIS FILE DIRECTLY -- IT IS GENERATED FROM THE CLI REPO
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
{% endcomment %}


# 启动器模板


{% include fluid/toc.html %}

这是官方的 Ionic 初学者模板列表，它是你的下一个 Ionic 应用随时可用的入门套件。参阅[`ionic start`](/docs/cli/start/)文档来使用。

## 启动器类型


### Ionic Angular

启动器 | 描述
--------|------------
`tabs` | 一个带有简单选项卡界面的启动项目
`blank` | 一个空白的启动项目
`sidemenu` | 一个在内容区中带有导航侧面菜单的启动项目
`super` | 一个完成了预构建页面，服务和 Ionic 开发最佳实践的启动项目
`conference` | 一个示范性的真实应用项目
`tutorial` | 一个与 Ionic 文档一起使用的基于教程的项目
`aws` | AWS 移动 Hub 启动器


### Ionic 1

启动器 | 描述
--------|------------
`tabs` | 一个使用简单的标签界面 Ionic 启动项目
`blank` | 一个空白的 Ionic 启动项目
`sidemenu` | 一个在内容区中带有导航侧面菜单的 Ionic 启动项目
`maps` | 一个使用谷歌地图和侧边菜单的 Ionic 启动器项目



## 工作原理

启动器在 [Ionic Starters](https://github.com/ionic-team/starters) 仓库中将启动器应用覆盖到一组基本文件上进行构建，然后将构建文件压缩存档，将其上传。之后，Ionic CLI 下载并提取存档的启动器模板文件，并为每个新应用创建个性化的文件。
