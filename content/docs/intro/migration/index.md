---
layout: fluid/docs_base
category: intro
id: migration
title: 迁移
header_sub_title: Getting Started with Ionic
---


# 迁移：核心概念

<a class="improve-v2-docs" href='https://github.com/docschina/ionicframework.com/edit/cn/content/docs/intro/migration/index.md'>改进这篇翻译</a>

Ionic 建立在 Angular 之上，而 Angular 的原始框架已经被完全重写了一遍。老 Angular 原有的所有部分仍然存在，但是开发人员需要注意的语法和结构有了新的改变。有关 Angular 中的更改的概述，请参阅 [Learn Angular](http://learnangular2.com/)。

在 Ionic 中，所有的东西和之前也差不太多。Ionic v1 中所有的概念依然是最新的，虽然它们会看上去和之前略有不同。你依然拥有类似于 v2 中的视图和控制器，但它们如今已经合并到一个实例中。

来看看这个基于 v1 的例子。


v1

```
.config(function($stateProvider){
  $stateProvider
  .state('main', {
    url: '/',
    templateUrl: 'templates/main.html',
    controller: 'MainCtrl'
  })
})

.controller('MainCtrl', function(){

})
```

你现在可以使用最新的 Ionic 将其重写为如下代码：

```
@Component({
  templateUrl:'main/main.html'
})
export class MainCmp {
  constructor() {

  }
}
```

至于其他改变（诸如导航的变化）就有很大不同了，不过我们承诺，所有的这些改变都是为了你好。如今你可以将组件视为任意视图，并以任何你想要的方式导航到它们上。这使得导航变得更加的灵活，并允许使用更多基于元素样式的导航栈。

# 从 Angular 1 迁移

虽然 Angular 2 需要更新应用程序以进行语法更改，但开发人员可以采取积极主动的措施，通过遵循最佳做法并使用 [John Papa 的 Angular Style 指南](https://github.com/johnpapa/angular-styleguide)或 [Todd Motto 的 Angular Style 指南](https://github.com/toddmotto/angularjs-styleguide)来确保其应用程序可升级。这两种方法都为你提供了一系列用于准备迁移代码的步骤。

### ControllerAs 语法

ControllerAs 语法是 Angular 1.x 中的一项功能，你可以将数据绑定到 controller 的直接实例，而不是将其绑定到 `$scope`。这使得将 Angular 1.x 的 controller 迁移到 Angular 2 的 class 变得更容易。从传统的 controller 迁移到 `controllerAs` 是相当简单的：

_index.html_

```html
{% raw %}
    <ion-content ng-controller="MainCtrl">
      <ion-item>
        {{data.text}}
      </ion-item>
    </ion-content>
{% endraw %}
```

_app.js_

```javascript
    .controller('MainCtrl', function($scope){
      $scope.data ={
        text: 'Hello World'
      }
    })
```

要将其转换为 `controllerAs` 语法，你只需更改其中的一部分内容即可。

_index.html_

```html
{% raw %}
    <ion-content ng-controller="MainCtrl as main">
      <ion-item>
        {{main.data.text}}
      </ion-item>
    </ion-content>
{% endraw %}
```

_app.js_

```javascript
    .controller('MainCtrl', function(){
      this.data ={
        text: 'Hello World'
      }
    })

```

### TypeScript

TypeScript 是 JavaScript 的超集，可以在你的代码中提供 ES6 Classes 语法以及静态类型系统。通过采用 TypeScript，如今你可以将代码编写为易于迁移至 Ionic 的 ES6 Classes。因为 TypeScript 中同样支持 JavaScript，所以你可以一点一点地将代码转换过来。如果你使用了前面的方法转换 controller，那就可以很容易地将其进一步转换为如下所示的 TypeScript 类。

_app.js_

```javascript
    .controller('MainCtrl', function(){
      this.data ={
        text: 'Hello World'
      }
    })

```

_app.ts_

```javascript

    export class MainCtrl{
      constructor(){
        this.data ={
          text: 'Hello World'
        }
      }
    }

```

### 项目结构

使用 Angular 1 时，将所有的 JavaScript 都放在在一起并与模板分离是一种惯例。由于 Ionic 和 Angular 2 将转向组件化的基础思路，因此你可以重新组织您的项目以便在精神上实施该理念。所以一个长得像这样的项目目录。。。

```
    |-www/
    |
    |--js/
    |--|-app.js
    |--|-HomeCtrl.js
    |--|-DetailCtrl.js
    |
    |--templates/
    |--|-Home.html
    |--|-Detail.html
    |
    |-index.html

```

可能会被重新组织成如下所示：

```
    |-www/
    |
    |--Home/
    |--|-HomeCtrl.js
    |--|-Home.html
    |
    |--Detail/
    |--|-DetailCtrl.js
    |--|-Detail.html
    |
    |-index.html
    |-app.js
```

这样组织项目可以帮助你理解每个应用程序的视图/状态是一个组件，而该组件包含一个模板和一个控制器。
