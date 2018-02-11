---
layout: fluid/cli_docs_base
category: cli
id: cli-index
title: Ionic CLI Documentation
hide_header_search: true
dark_header: true
---


{% comment %}
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
DO NOT MODIFY THIS FILE DIRECTLY -- IT IS GENERATED FROM THE CLI REPO
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
{% endcomment %}


# Ionic CLI

Ionic 命令行界面（CLI）是开发 Ionic 应用的首选工具。您可以在 [Github](https://github.com/ionic-team/ionic-cli) 上关注CLI的开发。

{% include fluid/toc.html %}

## 安装

请确保安装了最新的 [Node](/docs/resources/what-is/#node) 6 LTS 和 [NPM](/docs/resources/what-is/#npm) 3+。

然后，全局安装CLI（您可能需要sudo）：

```bash
$ npm install -g ionic@latest
```

您可以使用`ionic --version`命令验证您的安装。

## 起步

使用`ionic start`开始一个新的 Ionic 项目：

```bash
$ ionic start myNewProject
```

`ionic start`将提示您选择“启动器”。我们建议使用 `tutorial` 启动器作为您的第一个应用程序。参考 [启动器模板](/docs/cli/starters.html) 来获取完整列表。

选择启动器后，CLI 将创建一个名为`myNewProject`的新应用程序。一旦你使用 `cd` 进入你的项目目录，你就可以使用一些新的命令，比如`ionic serve`：

```bash
$ cd ./myNewProject
$ ionic serve
```

在运行 `ionic serve` 时，您对应用代码进行的更改将自动刷新浏览器。如果你想在设备或模拟器上看到你的应用，你可以[使用 Cordova ](#using-cordova)。

您可以使用 `ionic --help` 命令列出可用命令。

## 使用 Cordova

将 [Cordova](https://cordova.apache.org/) 集成进 Ionic ，为您的应用带来原生功能。

```bash
$ npm install -g cordova
$ ionic cordova --help
$ ionic cordova run ios
```


`ionic cordova` 命令（除了 `ionic cordova resources` 外）对 Cordova CLI 进行了包装。您可以阅读每个命令的 `--help` 页面中的差异。要了解有关这些命令的更多信息，请参阅 [Cordova CLI Reference] (https://cordova.apache.org/docs/en/latest/reference/cordova-cli/)文档。

* 对于 iOS 开发，请参阅 [iOS Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/ios/index.html) 。
* 对于 Android 开发，请参阅 [Android Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html) 。

## Ionic 专业版

[Ionic 专业版](/pro)是一套强大的工具和服务套件，它专为完整应用而设计，并将所有的体验都集成在一起。 Ionic 专业版完全支持 Ionic CLI。 请参阅[专业版文档](/docs/pro//basics/getting-started/)起步。


Ionic 云（遗留产物）将支持到2018年1月31日。在此之前，您可以使用`ionic config set -g backend legacy`和`ionic config set -g backend pro`在 Ionic 云和 Ionic 专业版之间切换。不幸的是，每次切换后端模式时，您都需要使用 `ionic login` 重新进行身份验证。

## 故障排除

如果您在使用 Ionic CLI 时遇到问题，可以尝试以下操作：

* 确保您使用的是 CLI 的最新版本。用 `npm update -g ionic`  更新。
* 尝试使用`--verbose`标志运行命令，该标志将打印`DEBUG`消息。
