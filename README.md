<div align="center">
  <a href="https://docschina.org">
    <img width="200" heigth="200" src="site.png">
  </a>
</div>

<h2 align="center">主要链接</h2>

* 首页链接：https://docschina.org
* git 仓库：https://github.com/docschina
* 群聊：https://docschina.org/talk
* 团队：https://docschina.org/team
* gitter：https://gitter.im/docschina
* slack：https://docschina.slack.com/

<h2 align="center">授权方式</h2>

- 印记中文所有的翻译文档，统一遵循 [“保留署名—非商用”创意共享 4.0 许可证（CC BY-NC 4.0）](https://creativecommons.org/licenses/by-nc/4.0/deed.zh) 授权方式。
- 你不用知会我们就可以转载，但**必须保持署名为“印记中文”，以及链接到 https://docschina.org ，并且不得去掉本页入口链接，也不得修改文档内容），并且不得用于商业目的**。
- 如果需要进行任何商业推广，请接洽 印记中文负责人李成熙(@lcxfs1991)（QQ: 249806703 && 邮箱：lcxfs1991@gmail.com），我们将给出积极的回应。

---

### 运行
```
1. gulp watch
2. http://localhost:3000
```


### Windows 环境下的安装

1. 修改 gulp-clean-css 的版本

> 在 package.json 修改 gulp-clean-css 的版本: `"gulp-clean-css": "2.0.3"`

2. 运行 `npm install`

3. 安装 rubyinstaller（2.3 以下）和 ruby-dev

> 因为 ruby-dev 只支持 2.3 以下的 ruby，
下载地址：https://rubyinstaller.org/downloads/
安装教程：http://jekyll-windows.juthilo.com/1-ruby-and-devkit/

4. gem换源

> 教程：http://gems.ruby-china.org/

5. 添加 tzinfo 和 tzinfo-data
> 在 gemfile 中添加 `gem 'tzinfo'` 和 `gem 'tzinfo-data'`

6. 运行 `bundle`

7. 运行 `gulp watch`

#### Windows环境下可能会遇到的问题：

1. Cannot read property 'line' of undefined 问题：按照 Windows 安装步骤第一步锁版本
2. Broken @import declaration 问题：注释 content 和 asset 文件夹下的字体引用或替换成国内字体地址
3. spawn bundle ENOENT，将 Gulpfile 第174行 bundle 加上 bat 后缀
```
gulp.task('jekyll-build', [], function(done) {
  browserSync.notify(messages.jekyllBuild);
  return cp.spawn('bundle.bat',
    ['exec', 'jekyll', 'build', '-I', '--config', '_config.yml'],
    {stdio: 'inherit'})
  .on('close', function() {
    done();
  }).on('error', function(err) {throw err; });
});
```
4. tzinfo 问题，按照 Windows 安装步骤第五步即可

### macOS 环境下的安装

#### 测试版本

- macOS version: `10.13.3`
- Ruby version: `2.3.3`（系统自带）
- Bundler version: `1.16.1`
- 其余软件的版本都是配置文件里面的（安装完之后运行 `git status` 依然显示 `working tree clean`）

#### macOS 环境下安装步骤

> 很多时候 gem 的操作都会提示你没权限（用 Sass 官网的话说就是 [It's pretty magical.](https://sass-lang.com/install)），这时需要在前面加 `sudo`

1. `npm install`
1. macOS 自带了 Ruby，但是[需要换一下 RubyGems 的源](https://gems.ruby-china.org/)（更新 RubyGems 时需要科学上网）
1. 更新 RubyGems 并换源之后，安装 [Bundler](http://bundler.io/) 并[换 Bundler 的源](https://gems.ruby-china.org/)（没错要换两次源）
1. `bundle install`（中间可能会要求权限，让你输密码）
1. `npm run bundle-install`
1. `gulp watch`（<del>需要科学上网，并且第一次要等很久</del>。***2018/03/11 更新：将 Google Fonts 换成 75CDN 后，如今已不需要科学上网***）

### 翻译暂定方案：

- 执行 `gulp watch` 命令启动服务，以 _site 作为服务根目录，访问 http://localhost:3000
- 共有三个源文件目录：`content`, `server`, `_site`
- 注意 `gulp watch` 中的 `build-prep` 任务下的 `images` 子任务耗时很久，第一次运行，之后运行时要注释掉
- **重要** 在 `content` 下翻译 html 和 markdown 文件
- 可能 `watch` 命令有报错，每次修改 html 和 markdown 文件后，需要手动执行 `jekyll-rebuild` 任务，可以将 content 文件夹下的文件，重新生成到 _site 文件夹下，刷新页面就可以看到效果，无须重新执行 `watch` 任务
- WebStorm 用户可以排除掉 `_site` 文件夹

```
[17:06:41] Starting 'watch'...
[17:06:46] 'watch' errored after 4.48 s
[17:06:46] RangeError: Maximum call stack size exceeded
    at Gaze._pollFile (/Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:331:19)
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:411:12
    at Array.forEach (<anonymous>)
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:409:11
    at iterate (/Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:52:5)
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:61:11
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:420:5
    at iterate (/Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:52:5)
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:61:11
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:420:5
    at iterate (/Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:52:5)
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:61:11
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:420:5
    at iterate (/Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:52:5)
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/helper.js:61:11
    at /Users/lizhihua/ionicframework.com/node_modules/gaze/lib/gaze.js:420:5
[17:06:46] Development server listening. (PID:14135)
```

### 分支管理
- 合并分支：http://mp.weixin.qq.com/s/_ricIlWhDbRZW-CmH0Ik5w
- 翻译流程：https://github.com/webpack-china/webpack.js.org
- git 命令示意图：![git 命令示意图](ionic-git-flow.png)
