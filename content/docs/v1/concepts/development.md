---
layout: docs_concepts
title: "Ionic 概念"
header_title: Ionic Concepts
header_sub_title: The bigger picture of an Ionic App
---

### App 开发流程

Ionic 是 Angular.js，UI Router，Angular 指令，Angular 服务，JS 工具库，以及专注于移动端的 CSS 样式的集合体。将这些打包在一起，就是 ionic.bundle.js 和 ionic.css。

First, you must install the ionic CLI with npm:

```bash
npm install -g ionic
```

After that, you can start an app using one of our starter templates, or start from scratch, using the command 

```bash
ionic start myApp blank --type ionic1
ionic start myApp tabs --type ionic1
ionic start myApp sidemenu --type ionic1
```

You can also use a github or codepen URL to start a project from a cool example you may find. 

During the development process, be sure to test on devices often. While Ionic makes it significantly easier to create performant mobile apps, it does not stop you from adding features that are buggy or slow. Please see Caching and Optimization for more tips and tricks for creating performant apps. 

To test on a device, first add the platform:

```bash
ionic cordova platform add ios 
# or 
ionic cordova platform add android
```

Then run the command `ionic cordova run android` or `ionic cordova run ios`. If you have the device plugged in, it will run on the device. Otherwise, it will start the respective device’s emulator. Note that the npm package `ios-sim` must be installed for the iOS simulator to be started from the command line.
