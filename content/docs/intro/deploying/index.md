---
layout: fluid/docs_base
category: intro
id: deploying
title: 部署
header_sub_title: Getting Started with Ionic
---


# 部署到设备

<a class="improve-v2-docs" href='https://github.com/docschina/ionicframework.com/edit/cn/content/docs/intro/migration/index.md'>改进这篇翻译</a>

虽然使用浏览器（配合 `ionic serve`）或者手机模拟器来测试你的应用不失为一种方便快捷的方式，但是你最终还是需要在真机上测试的。这不仅是唯一可以精准地测试你的应用的行为表现的方式，许多 [Ionic Native](https://ionicframework.com/docs//native/) 插件也只有部署到真实设备上才能正常运行。

## Android 设备

部署到 Android 设备的过程相当简单。如果你已配置好 Android 开发环境，那就可以开始了。

### 需要安装的软件

- [Java JDK](http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html)
- [Android Studio](https://developer.android.com/studio/index.html)
- 最新的 SDK 工具、平台和开发应用所需的其他组件。可以使用 Android Studio 自带的 [SDK 管理器](https://developer.android.com/studio/intro/update.html)来更新你的工具。

### 运行你的应用

若要运行应用，你首先要做的是在 Android 设备上启用 USB 调试以及开发者模式，然后在命令行里运行 `ionic cordova run android --device`。

这将同时在 Android 及 Ionic 代码层面为你的应用生成一份调试版本

启用 USB 调试及开发者模式的方法在不同的设备上可能不太一样，但是用 Google 搜一下就能很快找到。你也可以在 Android 官方文档里获取[启用开发者模式的方法](https://developer.android.com/studio/run/device.html#developer-device-options)。

### 生产模式构建

若要在生产模式下构建你的应用，运行

```bash
ionic cordova run android --prod --release
# 或
ionic cordova build android --prod --release
```

这将会像 Ionic 源码一样来压缩你的应用的源代码，并移除 APK 中所有用于调试的功能。通常在将应用部署到 Google Play 商店时会用到该功能。

### 对 Android APK 进行签名
如果你想要在 Google Play 商店发布你的应用，那就必须对你的 APK 文件进行签名。为此，您必须创建一个新的证书/密钥库。


让我们使用 JDK 自带的 teytool 命令来生成你的私钥：
```bash
keytool -genkey -v -keystore my-release-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias my-alias
```
你首先会被提示为密钥库创建一个密码。然后回答该工具问你的其他问题，当一切都结束时，你的当前目录里应该会生成一个叫 my-release-key.jks 的文件。

__注意__：确保将该文件保存到安全的地方，一旦丢失的话，你就不能为你的应用提交更新了！

若要签署未签名的 APK，需要运行 JDK 自带的 jarsigner 工具：

```bash
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.jks android-release-unsigned.apk my-alias
```

这样 APK 文件就签名完毕了。最后，我们还需要运行 zipalign 工具来优化 APK。zipalign 工具可以在 `/path/to/Android/sdk/build-tools/VERSION/zipalign` 路径下找到。举例来说，若是在已安装了 Android Studio 的 macOS 系统里，zipalign 就安装在 `~/Library/Android/sdk/build-tools/VERSION/zipalign`：

```bash
zipalign -v 4 android-release-unsigned.apk HelloWorld.apk
```

为了验证你的 apk 是否签名，运行 apksigner。apksigner 和 zipalign 工具在同一个路径下：

```bash
apksigner verify HelloWorld.apk
```

现在我们拥有了最终用来发布的名叫 HelloWorld.apk 的二进制包，接着就可以在 Google Play 商店里发布该应用，将其分享给全世界！

所有的步骤也都可以在 [Android SDK 官方文档](https://developer.android.com/studio/publish/app-signing.html#signing-manually)里找到。

## iOS 设备

和 Android 不同，iOS 开发者需要为应用生成一份配置文件（Provisioning Profile）来进行代码签名。好消息是，从 iOS 9 开始，你不需要 Apple 开发者账户就可以在你自己的 iOS 设备上开发并测试你的应用。这对于想要尝试使用 Ionic 进行移动端开发的开发者而言着实是个好消息（节省了购买开发者账户的钱），但是拥有一个完整的 Apple 开发者账户还是能多享受很多功能的。若要完整了解开发者账户包含了哪些功能，请查阅 [Apple 官方文档](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html#//apple_ref/doc/uid/TP40012582-CH38-SW1)。

### 需要安装的软件

- Xcode 7 或更高版本
- iOS 9
- 一个免费的 [Apple ID](https://appleid.apple.com/) 或者购买 Apple 开发者账户

### 创建配置文件（Provisioning Profile）

首先，你需要设置一份配置文件（Provisioning Profile）来为你的应用进行代码签名。

#### 使用 Apple ID

1. 打开 Xcode 设置（Xcode > Preferences...）
2. 点击 'Accounts' 选项卡
3. 登录你的 Apple ID (+ > Add Apple ID...)

成功登录之后，你的 Apple ID 下面会出现 'Personal Team' 和 'Free' 两条规则。

<img src="/img/docs/deploying/profiles.jpg" alt="profiles">

#### 使用 Apple 开发者账户

使用 Apple 开发者账户创建配置文件（Provisioning Profile）稍微有点小复杂。若要查看完整说明，请查看 Apple 开发者文档中的 [Launching Your App on Devices](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html) 这一章。

### 运行你的应用

1. 运行 `ionic cordova build ios --prod` 命令，进行生产环境构建
2. 在 Xcode 中打开 `platforms/ios/` 目录里后缀为 `.xcodeproj` 的工程目录
3. 使用 USB 线连接你的手机，并将其选为目标设备
4. 在 Xcode 中点击播放按钮，尝试运行你的应用

不好啦！代码签名报错啦！没关系（都是套路）。

### 对你的应用进行代码签名

下一步，你需要对你的应用进行代码签名。对于 Xcode 8 或更早的版本，你将要进行的操作会有些不同。

#### Xcode 7 及更早的版本 ####

如果你运行的是 Xcode 7 或更早的版本，那么当你尝试运行该应用程序时，会看到如下所示的代码签名错误：

<img src="/img/docs/deploying/sign-fail-1.jpg">

点击 'Fix Issue' 按钮，然后选择你的 'Personal Team' 配置。

<img src="/img/docs/deploying/team-menu-1.jpg">

#### Xcode 8 ####

如果你运行的是 Xcode 8，那么该代码签名错误会以生成时错误（buildtime error）的形式出现，而不是弹出框：

<img src="/img/docs/deploying/code-sign-err-xcode8.png">

若要选择为你的应用签名的证书，请按下列步骤操作：

1. 选择 'Project Navigator' 选项卡，然后点击你的项目名（即根目录），来到 'Project Editor' 界面
2. 选择 'General' 部分
3. 在 'Signing' 部分的 'Team' 下拉菜单中选择与你的签名证书关联的团队

<img src="/img/docs/deploying/code-sign-xcode8.png">

### 信任该证书 ###

当你对你的应用进行代码签名之后，你应该会得到一个如下图所示的启动报错。在 Xcode 7 及更低版本中你会自动地看到这条消息。在 Xcode 8 中会在你尝试运行应用时出现这个报错*（译者注：普通的 Apple ID 会有这个报错，但是 Apple 开发者账户则不会）*：

<img src="/img/docs/deploying/launch-fail-1.jpg">

为了搞定这个问题，我们需要告诉 iOS 设备去信任我们经过了代码签名的应用的证书：

1. 在你的 iOS 设备中打开「设置」应用
2. 进入「通用 > 设备管理」。你将会看到过去你所用来签名的与 Apple ID 所关联的电子邮箱地址。
3. 点击这个电子邮箱地址
4. 点击「信任“你的电子邮箱地址”」:

<img src="/img/docs/deploying/verify.jpg">

现在，回到 Xcode 点击播放按钮，或者在命令行里运行 `ionic cordova run ios --device`，以便在你的 iOS 设备中安装并启动你的应用。
