ionic-site
==========

Repo for the ionicframework.com site.  To preview local Ionic changes, follow the instructions at the [Ionic repo](https://github.com/ionic-team/ionic#documentation).


gulp watch uses LiveReload. You may have to up your max file limit with the following command:

    ulimit -n 7000


## Local Build

1. Run `npm install`
2. Install gems (Jekyll and kramdown): `npm run bundle-install`

    > This will re-construct your `Gemfile.lock` for the specific platform you are developing on and exclude it from Git.  If you need to make a change to the `Gemfile`, or are updating gems, you will need to remove the `Gemfile.lock` from `.git/info/exclude`.

3. Run `gulp watch` (after the first run, this is the only step needed)

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
1. `gulp watch`（需要科学上网，并且第一次要等很久）

### 翻译暂定方案：

- 执行 `gulp watch` 命令启动服务，以 _site 作为服务根目录，访问 http://localhost:3000
- 共有三个源文件目录：`content`, `server`, `_site`
- 注意 `gulp watch` 中的 `build-prep` 任务下的 `images` 子任务耗时很久，第一次运行，之后运行时要注释掉
- **重要** 在 `content` 下翻译 html 和 markdown 文件
- 可能 `watch` 命令有报错，每次修改 html 和 markdown 文件后，需要手动执行 `jekyll-rebuild` 任务，可以将 content 文件夹下的文件，重新生成到 _site 文件夹下，刷新页面就可以看到效果，无须重新执行 `watch` 任务

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
- git 命令示意图：![git 命令示意图](https://camo.githubusercontent.com/6f9cc78d28f03cf60b148d368cf89160c807c08c/687474703a2f2f7030773575717736622e626b742e636c6f7564646e2e636f6d2f696d6167652f706e672f7765627061636b2545372542462542422545382541462539312545362542352538312545372541382538422545352539422542452e706e67)

## CI Explanation

Ionic v1 and v2 now automatically deploy their changes to an Ionic staging server. Ionic team members are given permission to the staging and production servers in Heroku. V1 and V2 docs changes go as follows:

1. Change the content of the docs as necessary.
2. Optionally preview the changes by running `gulp docs` in the Ionic v1/2 repo, and `gulp watch` in ionic site, which should be a sibling directory of the `ionic` and `ionic2` repos.
3. Commit and push changes
4. Sit back. The [Ionic v1 CI tasks](https://circleci.com/gh/ionic-team/ionic) and the [Ionic v2 CI tasks](https://circleci.com/gh/ionic-team/ionic2) will generate the new docs and push them to the `ionic-site` repo. The `ionic-site` CI tasks will then build them and automatically deploy them to the staging server.
5. Preview changes on the [staging server](https://ionic-site-staging.herokuapp.com/) and promote the changes to production if all looks well. Be sure to give the site a quick look over to make sure things look good.


## Third Party Libraries

3rd part libraries should be concatonated in to the site bundle by adding them via package.json and specifying what files to include in the `assets/3rd-party-libs.json` file. 


## Deploy

Changes to master are automatically deployed to  [ionic-site-staging.herokuapp.com/](https://ionic-site-staging.herokuapp.com/). Periodically, the core framework will inspect staging and promote it to [ionicframework.com](https://ionicframework.com).


## Troubleshooting

Occasionally, people get a Jekyll error the first time they run `gulp watch`. Try deleting `Gemfile.lock` and re-running `bundle install` and then try again. Be sure to set your local git to exclude the changed `Gemfile.lock` file. 


## Community

* Follow [@ionicframework on Twitter](https://twitter.com/ionicframework).
* Subscribe to the [Ionic Newsletter](https://ionicframework.com/subscribe/).
* Have a question that's not a feature request or bug report? [Discuss on the Ionic Forum](https://forum.ionicframework.com/).
* Read our [Blog](https://ionicframework.com/blog/).
* Have a feature request or find a bug? [Submit an issue](https://github.com/ionic-team/ionic/issues).
