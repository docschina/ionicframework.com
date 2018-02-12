---
layout: fluid/cli_docs_base
category: cli
id: cli-projects
page_name: Project Types
title: Project Types - Ionic CLI Documentation
hide_header_search: true
dark_header: true
---


{% comment %}
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
DO NOT MODIFY THIS FILE DIRECTLY -- IT IS GENERATED FROM THE CLI REPO
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
{% endcomment %}


# 项目类型


{% include fluid/toc.html %}

Ionic CLI 适用于各种类型的 Ionic 项目。项目的类型作为`type`存储在项目的`ionic.config.json`文件中。以下是项目类型值列表：

* `ionic-angular`: [Ionic Angular](#ionic-angular)
* `ionic1`: [Ionic 1](#ionic-1)
* `custom`: 这种类型， CLI 不会调用任何构建或服务。参阅[钩子](/docs/cli/configuring.html#hooks)以在你自己的构建过程中使用`ionic build` 和 `ionic serve`。

## Ionic Angular

Ionic Angular ([`ionic-angular`](https://www.npmjs.com/package/ionic-angular)) 使用 [Angular 5](https://angular.io/) 和 [`@ionic/app-scripts`](https://github.com/ionic-team/ionic-app-scripts) 作为工具。

你可以使用以下命令启动一个新的 Ionic Angular 应用程序：

```bash
$ ionic start --type=ionic-angular
```

参阅 [Starter Templates](/docs/cli/starters.html#ionic-angular) 来获取 Ionic Angular 的启动器列表。

Ionic Angular 应用是用 [TypeScript](https://www.typescriptlang.org/) 和 [Sass](http://sass-lang.com/) 编写的。而且是用[`@ionic/app-scripts`](https://github.com/ionic-team/ionic-app-scripts)编译和构建的， 这是一个针对 Ionic Angular 而优化过的可配置构建系统。

`ionic build` 和 `ionic serve` 通过 `@ionic/app-scripts` 即可开箱即用， 所以没必要直接调用。它也带有默认值，但不妨碍通过各种方式进行配置。有关配置详细信息，请参阅 [`README.md`](https://github.com/ionic-team/ionic-app-scripts/blob/master/README.md)。

### 项目结构

```
project/
├─ ionic.config.json # Ionic 项目配置文件
├─ package.json
├─ src/
│  ├─ app/
│  │  ├─ app.component.ts # 你的应用的根组件
│  │  ├─ app.html # 应用组件模板
│  │  ├─ app.module.ts # 应用组件的 NgModule
│  │  ├─ app.scss # 全局 SCSS
│  │  └─ main.ts # 引导文件
│  ├─ assets/ # 放你的图片等
│  ├─ pages/ # 包含你应用的页面组件
│  ├─ theme/
│  │  └─ variables.scss # 参阅 https://ionicframework.com/docs/theming
│  └─ index.html # 主 html 文件
└─ www/ # 构建输出目录
```
## Ionic 1

Ionic 1 ([`ionic-v1`](https://github.com/ionic-team/ionic-v1/)) 使用 [AngularJS](https://angularjs.org/).

你可以使用以下命令启动一个新的 Ionic 1应用程序：

```bash
$ ionic start --type=ionic1
```

参阅 [启动器模板](/docs/cli/starters.html#ionic-1) 来获取 Ionic 1的启动器列表。

开箱即用， Ionic 1应用没有构建过程。`www/index.html`包含了`www/css/style.css`文件和三个在`www/js/`中提供好的JS文件。

### 项目结构

```
project/
├─ bower.json
├─ gulpfile.js
├─ ionic.config.json # Ionic 项目配置文件
├─ package.json
├─ scss/
│  └─ ionic.app.scss # 启用 sass 
└─ www/
   ├─ css/
   │  └─ style.css # vanilla CSS 源文件 
   ├─ js/
   │  ├─ app.js # 引导文件，包括`.config()`
   │  ├─ controllers.js # https://docs.angularjs.org/guide/controller
   │  └─ services.js # https://docs.angularjs.org/guide/services
   ├─ templates/ # AngularJS 模板
   └─ index.html # 主 html 文件
```

### 启用 Sass

你可以使用 [Sass](http://sass-lang.com/) 来改变使用了`www/index.html` 的 CSS 文件。(`css/style.css`是默认使用的样式文件， `css/ionic.app.css` 是被生成的样式文件，它包含了 Ionic 样式和你应用的样式)。

主 Sass 源文件位于`scss/ionic.app.scss`。

如果你的`gulpfile.js`包含`sass`任务，那么 CLI 将在`ionic build`和`ionic serve`命令期间自动运行它。

