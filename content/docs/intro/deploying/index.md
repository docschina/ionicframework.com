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

<!-- To verify that your apk is signed run apksigner. The apksigner can be also found in the same path as the zipalign tool: -->
为了验证你的 apk 是否签名，运行 apksigner。apksigner 和 zipalign 工具在同一个路径下：

```bash
apksigner verify HelloWorld.apk
```

现在我们拥有了最终用来发布的名叫 HelloWorld.apk 二进制包，接着就可以在 Google Play 商店里发布该应用，将其分享给全世界！

所有的步骤也都可以在 [Android SDK 官方文档](https://developer.android.com/studio/publish/app-signing.html#signing-manually)里找到。

## iOS Devices

Unlike Android, iOS developers need to generate a provisioning profile to code sign their apps for testing. The good news is that, as of iOS9, you can develop and test your apps on your iOS device without a paid Apple Developer account. This is particularly great for developers who want to try out mobile development with Ionic, since it saves the cost but still provides a lot of the features of having a full Apple Developer account. For a full breakdown of the features included, check out [Apple's docs](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html#//apple_ref/doc/uid/TP40012582-CH38-SW1).

### Requirements

- Xcode 7 or higher
- iOS 9
- A free [Apple ID](https://appleid.apple.com/) or paid Apple Developer account

### Creating a Provisioning Profile

To start, you'll need to set up a provisioning profile to code sign your apps.

#### Using an Apple ID

1. Open Xcode preferences (Xcode > Preferences...)
2. Click the 'Accounts' tab
3. Login with your Apple ID (+ > Add Apple ID...)

Once you've successfully logged in, a new 'Personal Team' with the role 'Free' will appear beneath your Apple ID.

<img src="/img/docs/deploying/profiles.jpg" alt="profiles">

#### Using an Apple Developer Account

Creating a provisioning profile with a paid Apple Developer account is a little bit more involved. For full instructions, check out [Launching Your App on Devices](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html) in the Apple Developer docs.

### Running Your App

1. Run a production build of your app with `ionic cordova build ios --prod`
2. Open the `.xcodeproj` file in `platforms/ios/` in Xcode
3. Connect your phone via USB and select it as the run target
4. Click the play button in Xcode to try to run your app

Oops, code signing error! No problem.

### Code Signing Your App

Next, you'll need to code sign your app. How you do this will depend on if you are running Xcode 8 or an earlier version.

#### Xcode 7 and Earlier ####

If you are running Xcode 7 or earlier, you'll get a code signing error that looks like this when you try to run the app:

<img src="/img/docs/deploying/sign-fail-1.jpg">

Click the 'Fix Issue' button, then select your 'Personal Team' profile.

<img src="/img/docs/deploying/team-menu-1.jpg">

#### Xcode 8 ####

If you are running Xcode 8, the code signing error will appear as a buildtime error, rather than as a pop-up:

<img src="/img/docs/deploying/code-sign-err-xcode8.png">

To select the certificate to sign your app with, do the following:

1. Go to the 'Project Editor' by clicking the name or your project in the 'Project Navigator'
2. Select the 'General' section
3. Select the team associate with your signing certificate from the 'Team' dropdown in the 'Signing' section

<img src="/img/docs/deploying/code-sign-xcode8.png">

### Trusting the Certificate ###

Once you've code signed your app, you should get a launch error that looks like this. On Xcode 7 and below you'll see this automatically. On Xcode 8 it will appear the next time you try to run the app:

<img src="/img/docs/deploying/launch-fail-1.jpg">

To get past this, we have to tell our iOS device to trust the certificate we code signed our app with:

1. Open the 'Settings' app on your iOS device
2. Go to 'General > Device Management'. You'll see the email address associated with the Apple ID or Apple Developer account you used to code sign your app.
3. Tap the email address
4. Tap 'Trust &lt;your_email&gt;':

<img src="/img/docs/deploying/verify.jpg">

Now, go back to Xcode and hit that play button or run `ionic cordova run ios --device` from the command line to install and launch your app on your iOS device.
