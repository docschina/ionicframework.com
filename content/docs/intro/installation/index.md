---
layout: fluid/docs_base
category: intro
id: installation
title: Installing Ionic
header_sub_title: Getting Started with Ionic
next_page_title: Tutorial
next_page_link: /docs//intro/tutorial
---

# 安装 Ionic

<a class="improve-v2-docs" href='https://github.com/ionic-team/ionic-site/edit/master/content/docs/intro/installation/index.md'>Improve
this doc</a>

Ionic apps 主要通过 Ionic 命令行工具("CLI")来创建和开发，
并通过使用 Cordova 构建/部署为原生应用程序。
也就是说，我们还需要安装一些工具辅助开发。

### 获取 Node 和 NPM

CLI 中的大部分工具都基于 Node，并通过 npm 进行管理。
The quickest way to get Node and NPM installed on your machine is through the
[NodeJS installer](https://nodejs.org/). Be sure to install the LTS version of
Node. Close any terminals/command prompts you may have open, run the installer,
and launch a new terminal window. To verify you have everything installed
correctly, you can run `npm --version` and `node --version`. If this errors,
please resolve before moving on.

### Ionic CLI and Cordova

With Node and NPM setup, let's install the Ionic and Cordova CLI.

```bash
$ npm install -g ionic cordova
```

> Note: The `-g` means this is a global install, so for Window's you will need
> to open an Admin command prompt. For Mac/Linux, you'll need to run the command
> with `sudo`.

Once that's done, create your first Ionic app:

```bash
$ ionic start helloWorld blank
```

To run your app, `cd` into the directory that was created and then run the
`ionic serve` command to test your app right in the browser!

```bash
$ cd helloWorld
$ ionic serve
```
