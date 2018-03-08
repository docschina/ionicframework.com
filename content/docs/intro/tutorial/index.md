---
layout: fluid/docs_base
category: intro
id: tutorial
subid: tutorial
title: 简易教程
header_sub_title: Getting Started with Ionic
prev_page_title: Installing Ionic
prev_page_link: /docs/intro/installation/
next_page_title: Project Structure
next_page_link: /docs/intro/tutorial/project-structure/
---

# Ionic 简易教程

<a class="improve-v2-docs" href='https://github.com/docschina/ionicframework.com/edit/cn/content/docs/intro/tutorial/index.md'>
  改进这篇翻译
</a>

假定你现在已经安装好了 [Ionic 和它的依赖项](../installation)，那就可以构建你的第一个应用了。本章节将指导你通过一系列步骤来创建一个全新的应用程序，并在其中增加若干个页面，然后在这些页面之间进行跳转。让我们开始吧！




> Ionic 使用 TypeScript 来编写代码。如果你对 TypeScript 不太熟悉，别担心，它和普通的 JavaScript 非常相似。若是想进一步了解 TypeScript，可以看一看[这个资源页面](https://ionicframework.com/docs/resources/what-is/#typescript)。




### 创建一个新 Ionic 应用

打开您的终端/命令提示符并运行如下命令，即可创建一个新的应用：

```bash
$ ionic start MyIonicProject tutorial
```

* `start` 会吩咐 CLI 去创建一个新的应用。
* `MyIonicProject` 将会是项目的目录名以及应用名。
* `tutorial` 则指定使用初学者模板来创建你的项目。


在创建项目的过程中，这条命令还会为该应用程序安装 
[node modules](../../resources/what-is/#npm)，并提示你是否要设置
Cordova。

除了初学者模板之外，Ionic
也提供了下列官方模板：

* `tabs` : 简单的 3 标签页布局
* `sidemenu`: 侧边带有可滑动菜单的布局
* `blank`: 只有一个页面的空白模板
* `super`: 一个已有超过 14 个现成页面的初始项目
* `tutorial`: 自带向导的初始项目

如果在开始时没有指定模板，则会提示你选一个。

### 在浏览器中查看应用

新项目创建好之后, 你就可以使用 `cd` 命令进入项目目录。若要在浏览器里快速预览你的应用，则使用 `serve` 命令。


```bash
$ cd MyIonicProject/
$ ionic serve
```

<br/>
<center>
  <img src="/img/docs/tutorial-screen.png" style="max-width: 320px">
</center>
<br/>

在下一节中，让我们回顾一下由
`ionic start` 命令创建的项目结构。
