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

# Migrating from Angular 1


While Angular 2 requires apps to be updated for the syntax change, developers can be proactive and make sure their app is upgradable by following best practices and working with [John Papa's Angular Style guide](https://github.com/johnpapa/angular-styleguide) or [Todd Motto's Angular Style guide](https://github.com/toddmotto/angularjs-styleguide). Both of these will provide you with steps you can take to prepare your code for migration.

### ControllerAs Syntax

ControllerAs Syntax is a feature in Angular 1.x where, instead of binding data to `$scope`, you can bind to the direct instance of the controller. This makes migrating a Angular 1.x controller to an Angular 2 class much easier. It's fairly easy to migrate to `controllerAs` from a traditional controller:

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

To convert this to `controllerAs` syntax, you only have to change a few things.

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

TypeScript is a superset of JavaScript that provides ES6 Classes and type annotations in your code. By adopting TypeScript now, you can write your code as ES6 Classes that will be easy to move to Ionic. The best part is that any valid JavaScript is also valid TypeScript, so you can convert your code piece by piece. If you take your controller from before, you can easily convert it to a TypeScript class like this.

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

### Project Structure

With Angular 1, it was a practice to keep all your JavaScript together and separate from your templates. Since Ionic and Angular 2 will be moving to a component base setup, you can reorganize your project to help mentally enforce that concept. So a project whose directory looks like this...

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

could start to be reorganized to look like this:

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

Organizing your project like this can help get you in the mindset that each of your app's views/states are a component, with a template and a controller.
