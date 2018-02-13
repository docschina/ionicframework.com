---
layout: fluid/cli_docs_base
category: cli
id: cli-configuration
page_name: Configuring
title: Configuring - Ionic CLI Documentation
hide_header_search: true
dark_header: true
---


{% comment %}
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
DO NOT MODIFY THIS FILE DIRECTLY -- IT IS GENERATED FROM THE CLI REPO
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
{% endcomment %}


# 配置


{% include fluid/toc.html %}

## 配置文件

配置值存储在 JSON 文件中。

* 全局配置文件(`~/.ionic/config.json`): 用于全局 CLI 配置和授权
* 项目配置文件(`ionic.config.json`): 用于 Ionic 项目配置

CLI 提供了用于从项目配置文件和全局 CLI 配置文件中设置和打印配置值的命令。参阅`ionic config set --help` 和 `ionic config get --help` 来使用。

## 集成

诸如 Cordova 的集成被检测到时会自动激活，但也可以轻松禁用。

集成钩子到 CLI 事件中。例如，启用 Cordova 集成后，`ionic cordova prepare`将会在`ionic build`运行后运行。见[钩子](#hooks)。

| 集成       | 当...时启用                                                 | 当...时禁用                                                |
| ------------|-------------------------------------------------------------|----------------------------------------------------------|
| Cordova     | `ionic cordova` 命令运行                          | `ionic config set integrations.cordova.enabled false`  |
| Gulp        | `gulp`存在于`package.json`的`devDependencies`中| `ionic config set integrations.gulp.enabled false` |

## 环境变量

CLI 将查找以下环境变量：

* `IONIC_CONFIG_DIRECTORY`: 全局 CLI 配置的目录。默认为`〜/ .ionic`。
* `IONIC_HTTP_PROXY`: 设置代理所有 CLI 请求的 URL 。参阅[使用一个代理](#using-a-proxy)。CLI 还会查找 npm 使用的`HTTP_PROXY`和 `HTTPS_PROXY`。
* `IONIC_EMAIL` / `IONIC_PASSWORD`: 通过环境变量自动登录。

### 命令选项

你可以使用环境变量来表示命令选项（通常使用`--opt=value`语法设置）。这些环境变量的命名遵循一种模式：以`IONIC_CMDOPTS_`开始， 添加命令名称（用下划线替换任何空格）, 添加选项名称（用下划线替换任何连字符）, 然后将所有内容大写。布尔标志（不带值的命令行选项）可以设置为“1”或“0”。例如，在布尔标志中删除`--no-`前缀（如果有的话） (`ionic serve`中的`--no-open`可以用`IONIC_CMDOPTS_SERVE_OPEN=0`表示).

例如，`ionic cordova run ios -lc --livereload-port=1234 --address=localhost`中的命令选项也可以用以下一系列环境变量来表示：

```bash
export IONIC_CMDOPTS_CORDOVA_RUN_LIVERELOAD=1
export IONIC_CMDOPTS_CORDOVA_RUN_CONSOLELOGS=1
export IONIC_CMDOPTS_CORDOVA_RUN_LIVERELOAD_PORT=1234
export IONIC_CMDOPTS_CORDOVA_RUN_ADDRESS=localhost
```

如果这些变量是在你的环境中设置的，`ionic cordova build ios`将会使用新的默认值。

## 标志

CLI 标志是改变 CLI 命令行为的全局选项。

* `--help`: 查看其帮助页面。
* `--verbose`: 显示所有日志信息来进行调试。
* `--quiet`: 只显示`WARN`和`ERROR`日志消息。
* `--no-interactive`: 关闭交互式提示和花哨的输出。如果检测到 CI 服务器(我们使用 [ci-info](https://www.npmjs.com/package/ci-info) ), 则 CLI 自动改为非交互式。
* `--confirm`: 打开确认提示的自动确认。*小心*： CLI 在做可能危险的事情之前会提示，而自动确认可能会有意想不到的结果。

## 钩子

CLI 钩子是你可以在 CLI 事件期间运行脚本的方式，例如 “watch” 和 “build” 。要在 CLI 中使用钩子,请在`package.json`文件中使用以下[ npm 脚本](https://docs.npmjs.com/misc/scripts)。

| npm 脚本             | 命令                                                                                                                              |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| `ionic:watch:before` | `ionic serve`, `ionic cordova run -l`, `ionic cordova emulate -l`                                                               |
| `ionic:build:before` | `ionic build`, `ionic upload`, `ionic package build`, `ionic cordova build`, `ionic cordova run`, `ionic cordova emulate` |
| `ionic:build:after`  | `ionic build`, `ionic upload`, `ionic package build`, `ionic cordova build`, `ionic cordova run`, `ionic cordova emulate` |

### 例子

```json
  "scripts": {
    "ionic:build:before": "cp somefile www/somefile",
  }
```

*注意：如果你使用 [gulp](https://gulpjs.com/)， CLI 会按照上面的 npm 脚本的名字运行 gulp 任务。*

## 服务代理

CLI 可以将代理添加到 HTTP 服务器，用于`ionic serve`和`ionic cordova run android -lc`等 “热更新” 命令。如果你正在浏览器中开发并且需要调用外部 API ，这些代理将非常有用。使用此功能，你可以通过 Ionic CLI 将请求委托给外部 API ，从而`防止在请求的资源错误中出现 No 'Access-Control-Allow-Origin' 标头`。

在`ionic.config.json`文件中，你可以添加一个包含你想添加的代理数组的属性。代理是具有以下属性的对象：

* `path`: 将与传入请求 URL 的开头匹配的字符串。
* `proxyUrl`: 一个代理请求应该到达的 url 的字符串。
* `proxyNoAgent`: （可选）true / false，如果为 true ，则退出连接池，请参阅[Http代理](https://nodejs.org/api/http.html#http_class_http_agent)

```json
{
  "name": "appname",
  "app_id": "",
  "type": "ionic-angular",
  "proxies": [
    {
      "path": "/v1",
      "proxyUrl": "https://api.instagram.com/v1"
    }
  ]
}
```

使用上述配置，你现在可以通过`http://localhost:8100/v1`向本地服务器发出请求，让它向`https://api.instagram.com/v1`请求代理请求。  

*注意：不要忘记将应用程序中请求的 URL 更改为本地 URL 。此外，必须重新启动 “livereload” 命令才能使代理配置生效。*

## 使用代理

要代理 CLI 执行的 HTTP 请求，你需要将 CLI 代理插件安装在与 Ionic CLI 相同的`node_modules`上下文中：

对于全局安装的 CLI ：

```bash
$ npm install -g @ionic/cli-plugin-proxy
```

对于本地安装的 CLI ：

```bash
$ cd myProject # cd into your project's directory
$ npm install --save-exact --save-dev @ionic/cli-plugin-proxy
```

然后，使用以下环境变量之一：

```bash
$ export HTTP_PROXY="http://proxy.example.com:8888" # also used by npm
$ export HTTPS_PROXY="https://proxy.example.com:8888" # also used by npm
$ export IONIC_HTTP_PROXY="http://proxy.example.com:8888"
```

### 其他 CLIs

你使用的每个 CLI 必须单独配置来代理网络请求。

#### npm

```bash
$ npm config set proxy http://proxy.company.com:8888
$ npm config set https-proxy https://proxy.company.com:8888
```

#### git

```bash
$ git config --global http.proxy http://proxy.example.com:8888
```

### SSL 配置

你可以配置 Ionic CLI 的 SSL（与配置 npm CLI 类似）：

```bash
$ ionic config set -g ssl.cafile /path/to/cafile # file path to your CA root certificate
$ ionic config set -g ssl.certfile /path/to/certfile # file path to a client certificate
$ ionic config set -g ssl.keyfile /path/to/keyfile # file path to a client key file
```

`cafile`，`certfile`和`keyfile`条目可以在`〜/ .ionic / config.json`中手动编辑为字符串数组来包含多个文件。

## 遥测

默认情况下，Ionic CLI 将发送使用的数据给 Ionic ，我们使用该数据来改善你的体验。要禁用此功能，你可以运行`ionic config set -g telemetry false`。
