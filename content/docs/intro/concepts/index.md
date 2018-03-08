---
layout: fluid/docs_base
category: intro
id: concepts
title: 概念
header_sub_title: Getting Started with Ionic
---

# 核心概念

<a class="improve-v2-docs" href='https://github.com/docschina/ionicframework.com/edit/cn/content/docs/intro/concepts/index.md'>改进这篇文档</a>


如果你对 Ionic
以及混合移动应用开发完全陌生，这篇文章可以帮助你理解 Ionic
背后的哲学、概念以及工具。下面的信息有助于使你熟悉 Ionic
以及它是如何工作的。

### 什么是 Ionic 框架？

Ionic 框架是一套开源的
SDK，支持开发人员使用熟悉的网络技术（HTML, CSS
及 JavaScript）构建高性能、高质量的移动应用程序。

Ionic 主要专注于应用程序的视觉感知以及 UI 交互。这意味着它并不是
Cordova 或者你所喜欢的 JavaScript 框架的替代品。相反的是，Ionic
可以很好地适用于这些项目，以便简化应用程序开发流程中的一个大环节：前端开发。请阅读
[“Where
does the Ionic Framework fit
in?”](https://blog.ionicframework.com/where-does-the-ionic-framework-fit-in/)
这篇博文以便更好地理解 Ionic 的核心理念和目标。

### Ionic 是如何授权的？

Ionic 完全免费并开源，是基于较为宽松的
[MIT](http://opensource.org/licenses/MIT) 许可证发布的，这意味着你可以免费地将
Ionic 用于个人或商业用途。许多流行的项目，比如 jQuery 以及 Ruby on Rails 都是使用
MIT 许可进行授权的。

本网站及文档内容（位于
 [ionic-site](https://github.com/ionic-team/ionic-site) 仓库中）是基于
Apache 2 许可证授权的。

### 什么是 Ionic CLI？

[CLI](../../resources/what-is/#cli)（命令行界面）是一种用于为
Ionic 开发者提供许多实用命令的工具。除了安装和更新 Ionic
之外，CLI
还配备了内置的开发服务器，构建及调试工具等。如果你正在使用
[Ionic Pro](/pro)，CLI
还可以用于导出代码，乃至在命令行中操作你的帐号。

### 什么是组件？

Ionic 组件（Components）作为构建时的基础模块，是为移动应用所设计的可复用
UI 元素。组件由 HTML、CSS 以及
JavaScript 组成。每个
Ionic
组件都和你的应用所在的平台兼容。我们将其称为**平台连续性（Platform Continuity）**，请向下阅读主题化（Theming）部分以便深入了解它的工作方式。

### 什么是主题化？

主题是一套或多套应用在应用程序上的样式集。Ionic
默认使用浅色主题（同时随附一套深色主题）。除了主题外，Ionic
的**平台连续性（Platform Continuity）**还使得组件具有特定于平台的样式。这意味着应用程序的样式将根据其所运行的平台（iOS、Android
等）进行更改，从而为用户提供熟悉的体验。



### 导航（Navigation）是如何工作的？

导航（Navigation）的工作原理类似于栈
&mdash; 将需要显示的页面 **push** 进栈，然后使用
**pop** 以便返回。模态框和警告框同样可以通过 push 进导航栈的方式来显示。

### Ionic 的背后都有谁？

Ionic 最开始是由 [@benjsperry](https://twitter.com/benjsperry)、[@adamdbradley](https://twitter.com/adamdbradley)
以及 [@maxlynch](https://twitter.com/maxlynch)
开发的。在 2013 年 11 月发布 Ionic 的第一个 alpha 版本之后，我们在
2014 年 3 月发布了 1.0 beta 版，并在
2015 年 5 月发布 1.0 正式版。

如今，Ionic 拥有一个由开发人员和开源贡献者所组成并驱动的庞大国际社区。大小公司都在使用
Ionic 来更快更好地构建应用程序。据报道，在 2015
年 Ionic 开发者创造了超过 130 万个
Ionic 应用程序，而这个数字每天都在继续增长。

### 什么是 Angular？

[Angular](https://angular.io/) 是驱动 Ionic 的底层框架。它负责作为
Ionic 构建模块时的组件 API。有关
Angular 的概述，请查阅
[Angular 官方文档](https://angular.io/docs/ts/latest/)。
