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




> Ionic 使用 TypeScript 来编写代码。如果你对 TypeScript 不太熟悉，别担心，它和普通的 JavaScript 非常相似。若是想进一步了解 TypeScript，可以看一看[这个页面](https://ionicframework.com/docs/resources/what-is/#typescript)。




### 创建一个新 Ionic 应用

To start a new app, open your terminal/command prompt and run:

```bash
$ ionic start MyIonicProject tutorial
```

* `start` will tell the CLI create a new app.
* `MyIonicProject` will be the directory name and the app name from your
  project.
* `tutorial` will be the starter template for your project.

Along with creating your project, this will also install [node
modules](../../resources/what-is/#npm) for the application, and prompt you if
you want [Cordova](../../resources/what-is/#cordova) set up.

Along with the tutorial template, Ionic also provide the follow official
templates:

* `tabs` : a simple 3 tab layout
* `sidemenu`: a layout with a swipable menu on the side
* `blank`: a bare starter with a single page
* `super`: starter project with over 14 ready to use page designs
* `tutorial`: a guided starter project

If you don't specify a template at the start, you will be prompted to pick one.

### Viewing the app in a browser

Now, you can `cd` into the folder that was created. To get a quick preview of
your app in the browser, use the `serve` command.

```bash
$ cd MyIonicProject/
$ ionic serve
```

<br/>
<center>
  <img src="/img/docs/tutorial-screen.png" style="max-width: 320px">
</center>
<br/>

In the next section, let's go over the project structure created by the `ionic
start` command.
