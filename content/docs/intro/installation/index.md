---
layout: fluid/docs_base
category: intro
id: installation
title: Installing Ionic
header_sub_title: Getting Started with Ionic
next_page_title: Tutorial
next_page_link: /docs//intro/tutorial
---

<!-- # Installing Ionic -->
# 安装 Ionic

<a class="improve-v2-docs" href='https://github.com/ionic-team/ionic-site/edit/master/content/docs/intro/installation/index.md'>Improve
this doc</a>

<!-- Ionic apps are created and developed primarily through the Ionic command line
utility (the "CLI"), and use Cordova to build/deploy as a native app. This means
we need to install a few utilities to get developing. -->
Ionic 应用主要通过 Ionic 命令行工具（即 "CLI"）创建和开发，
然后使用 Cordova 构建/部署为一个原生应用。
这意味着我们需要安装几个命令行工具来进行开发。

<!-- ### Getting Node and NPM -->
### 获取 Node 和 NPM

<!-- Most of the tooling in the CLI is based on Node and is managed through npm. The
quickest way to get Node and NPM installed on your machine is through the
[NodeJS installer](https://nodejs.org/). Be sure to install the LTS version of
Node. Close any terminals/command prompts you may have open, run the installer,
and launch a new terminal window. To verify you have everything installed
correctly, you can run `npm --version` and `node --version`. If this errors,
please resolve before moving on. -->
Ionic CLI 中的大部分工具都基于 Node，并通过 npm 来管理。
在你的机器上安装 Node 和 NPM 的最快捷的方式就是[去官网下载 NodeJS 安装包](https://nodejs.org/)。
请确认安装的是 Node 的长期支持版（LTS version）。
安装前关闭已开启的所有命令行界面，运行安装包，
然后启动一个新的命令行窗口。为了确认所有软件都已正确安装，
你可以运行 `npm --version` 和 `node --version`。
如果这时出现了报错，请在向下看之前解决完毕。

<!-- ### Ionic CLI and Cordova -->
### Ionic CLI 和 Cordova

<!-- With Node and NPM setup, let's install the Ionic and Cordova CLI. -->
Node 和 NPM 设定好之后，就可以开始安装 Ionic 和 Cordova CLI 了。

```bash
$ npm install -g ionic cordova
```

<!-- > Note: The `-g` means this is a global install, so for Window's you will need
> to open an Admin command prompt. For Mac/Linux, you'll need to run the command
> with `sudo`. -->
> 注意：`-g` 选项意味着这是一次全局（global）安装，
> 所以你需要以管理员权限来开启命令行窗口。
> 对于 Mac/Linux，你需要在这条命令前加上 `sudo`。

<!-- Once that's done, create your first Ionic app: -->
完成之后，创建你的第一个 Ionic 应用：

```bash
$ ionic start helloWorld blank
```

<!-- To run your app, `cd` into the directory that was created and then run the
`ionic serve` command to test your app right in the browser! -->
为了运行你的应用，使用 `cd` 命令进入刚才创建的目录，
然后运行 `ionic serve` 命令以便在浏览器中测试该应用！

```bash
$ cd helloWorld
$ ionic serve
```
