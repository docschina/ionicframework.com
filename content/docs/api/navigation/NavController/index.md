---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "navcontroller"
title: "NavController"
header_sub_title: "Ionic API Documentation"
doc: "NavController"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="nav-controller" href="#nav-controller"></a>

NavController





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/navigation/nav-controller.ts#L6">
改进这篇文档
</a>






<p>NavController 是 <a href="../../components/nav/Nav/"><code>Nav</code></a> 和 <a href="../../components/tabs/Tab/"><code>Tab</code></a> 等导航控制器组件的基类。你可以使用导航控制器导航到你的应用中的<a href="#view-creation">页面</a>。在基本范畴内，导航控制器是代表特定 history 记录（例如 Tab）的页面数组。通过推入和弹出页面或在 history 中的任意位置插入和删除它们，可以操纵该数组在整个应用中导航。</p>
<p>当前页面是数组中的最后一页，或者我们可以这样想，当前页面在堆栈的顶部。将新页面 <a href="#push">Pushing</a> 到导航堆栈的顶部会导致新页面加载动画，而 <a href="#pop">popping</a> 当前页面将导航到堆栈中的上一页面。</p>
<p>除非你使用像 <a href="../../components/nav/NavPush/">NavPush</a> 这样的指令，或者需要特定的 NavController，否则大多数时候你会注入并使用对最近的 NavController 的引用来操纵导航堆栈。</p>
<h2 id="basic-usage">基本用法</h2>
<p>通过应用程序导航的最简单方法是使用 <code>&lt;ion-nav&gt;</code> 组件创建和初始化新的导航控制器。<code>ion-nav</code> 扩展了 <code>NavController</code> 类。</p>













<pre><code class="lang-typescript">import { Component } from `@angular/core`;
import { StartPage } from &#39;./start-page&#39;;

@Component(
  template: `&lt;ion-nav [root]=&quot;rootPage&quot;&gt;&lt;/ion-nav&gt;`
})
class MyApp {
  // 将 rootPage 设置为我们想要显示的第一页
  public rootPage: any = StartPage;

  constructor(){
  }
}
</code></pre>
<h3><a class="anchor" name="injecting-navcontroller" href="#injecting-navcontroller">注入 NavController</a></h3>

<p>注入 NavController 将始终为你提供最近 NavController 的实例，而不管它是 Tab 还是 Nav。</p>
<p>在后台，当 Ionic 实例化一个新的 NavController 时，它会创建一个 NavController 绑定到该实例的注入器（通常是 Nav 或 Tab），并将注入器添加到它自己的提供商中。有关提供商程序和依赖注入的更多信息，请参阅<a href="https://angular.io/docs/ts/latest/guide/dependency-injection.html">依赖注入</a>。</p>
<p>作为替代，你可以注入 NavController，并知道它在大多数情况下是正确的导航控制器（对于更高级的情况，请参阅 <a href="../../menu/Menu/">Menu</a> 和 <a href="../../tab/Tab/">Tab</a>）</p>






<pre><code class="lang-ts">import { NavController } from &#39;ionic-angular&#39;;

class MyComponent {
  constructor(public navCtrl: NavController) {

  }
}
</code></pre>
<h3><a class="anchor" name="navigating-from-the-root-component" href="#navigating-from-the-root-component">从根组件导航</a></h3>

<p>如果你想要控制根应用程序组件的导航，该怎么办？你无法注入 <code>NavController</code>，因为导航控制器的任何组件都是根组件的 <em>子组件</em>，因此它们无法注入。</p>
<p>通过向 <code>ion-nav</code> 添加一个引用变量，可以使用 <code>@ViewChild</code> 获取导航控制器（它扩展了 <code>NavController</code>）的 Nav 组件实例：</p>





<pre><code class="lang-typescript">import { Component, ViewChild } from &#39;@angular/core&#39;;
import { NavController } from &#39;ionic-angular&#39;;

@Component({
   template: &#39;&lt;ion-nav #myNav [root]=&quot;rootPage&quot;&gt;&lt;/ion-nav&gt;&#39;
})
export class MyApp {
   @ViewChild(&#39;myNav&#39;) nav: NavController
   public rootPage: any = TabsPage;

   // 等待 MyApp 模板中的组件被初始化
   // 在这种情况下，我们正在等待引用变量 “#myNav”
   ngOnInit() {
      // 让我们从 TabsPage 导航到 Page1
      this.nav.push(Page1);
   }
}
</code></pre>
<h3><a class="anchor" name="navigating-from-an-overlay-component" href="#navigating-from-an-overlay-component">从叠加组件导航</a></h3>

<p>如果你想从叠加组件（popover，modal，alert等）导航，该怎么办？在这个例子中，我们在应用中显示了一个弹出窗口。从 popover 中，我们将使用 <code>getRootNav()</code> 方法获取应用程序中的根 <code>NavController</code> 的引用。</p>


<pre><code class="lang-typescript">import { Component } from &#39;@angular/core&#39;;
import { App, ViewController } from &#39;ionic-angular&#39;;

@Component({
    template: `
    &lt;ion-content&gt;
      &lt;h1&gt;My PopoverPage&lt;/h1&gt;
      &lt;button ion-button (click)=&quot;pushPage()&quot;&gt;Call pushPage&lt;/button&gt;
     &lt;/ion-content&gt;
    `
  })
  class PopoverPage {
    constructor(
      public viewCtrl: ViewController
      public appCtrl: App
    ) {}

    pushPage() {
      this.viewCtrl.dismiss();
      this.appCtrl.getRootNav().push(SecondPage);
    }
  }
</code></pre>
<h2 id="view-creation">视图创建</h2>
<p>将视图添加到导航堆栈时创建视图。对于像 <a href="#push">push()</a> 这样的方法，NavController 接受任何用 <code>@Component</code> 装饰的组件类作为它的第一个参数。然后，NavController 将编译该组件，将其添加到应用程序中并将其移动到视图中。</p>
<p>默认情况下，页面被缓存并留在 DOM 中，如果他们被导航离开，但仍然在导航栈中（例如 <code>push()</code> 上的退出页面）。从导航堆栈中删除时（在 <a href="#pop">pop()</a> 或 <a href="#setRoot">setRoot()</a> 上）它们会被销毁。</p>
<h2 id="pushing-a-view">推入视图</h2>
<p>要将新视图推入导航堆栈，请使用 <code>push</code> 方法。如果页面有 <a href="../../navbar/Navbar/"><code>&lt;ion-navbar&gt;</code></a>，则后退按钮会自动添加到推入的视图中。</p>
<p>通过将对象传递给 <code>push</code> 方法，也可以将数据传递给视图。然后推入的视图可以通过 <code>NavParams</code> 类访问数据。
</p>









<pre><code class="lang-typescript">import { Component } from &#39;@angular/core&#39;;
import { NavController } from &#39;ionic-angular&#39;;
import { OtherPage } from &#39;./other-page&#39;;
@Component({
   template: `
   &lt;ion-header&gt;
     &lt;ion-navbar&gt;
       &lt;ion-title&gt;Login&lt;/ion-title&gt;
     &lt;/ion-navbar&gt;
   &lt;/ion-header&gt;

   &lt;ion-content&gt;
     &lt;button ion-button (click)=&quot;pushPage()&quot;&gt;
       Go to OtherPage
     &lt;/button&gt;
   &lt;/ion-content&gt;
   `
})
export class StartPage {
  constructor(public navCtrl: NavController) {
  }

  pushPage(){
    // 将另一个页面推入导航堆栈
    // 导致导航控制器转换到新页面
    // 可选数据也可以传递到推送页面。
    this.navCtrl.push(OtherPage, {
      id: &quot;123&quot;,
      name: &quot;Carl&quot;
    });
  }
}

import { NavParams } from &#39;ionic-angular&#39;;

@Component({
  template: `
  &lt;ion-header&gt;
    &lt;ion-navbar&gt;
      &lt;ion-title&gt;Other Page&lt;/ion-title&gt;
    &lt;/ion-navbar&gt;
  &lt;/ion-header&gt;
  &lt;ion-content&gt;I&#39;m the other page!&lt;/ion-content&gt;`
})
class OtherPage {
  constructor(private navParams: NavParams) {
     let id = navParams.get(&#39;id&#39;);
     let name = navParams.get(&#39;name&#39;);
  }
}
</code></pre>
<h2 id="removing-a-view">删除视图</h2>
<p>要从堆栈中删除视图，请使用 <code>pop</code> 方法。弹出一个视图将转换到前一个视图。</p>

<pre><code class="lang-ts">import { Component } from &#39;@angular/core&#39;;
import { NavController } from &#39;ionic-angular&#39;;

@Component({
  template: `
  &lt;ion-header&gt;
    &lt;ion-navbar&gt;
      &lt;ion-title&gt;Other Page&lt;/ion-title&gt;
    &lt;/ion-navbar&gt;
  &lt;/ion-header&gt;
  &lt;ion-content&gt;I&#39;m the other page!&lt;/ion-content&gt;`
})
class OtherPage {
   constructor(public navCtrl: NavController ){
   }

   popView(){
     this.navCtrl.pop();
   }
}
</code></pre>
<h2 id="lifecycle-events">生命周期事件</h2>
<p>生命周期事件在导航的各个阶段被触发。它们可以在从 <code>NavController</code> 推入/弹出的任意组件类型中定义。</p>

<pre><code class="lang-ts">import { Component } from &#39;@angular/core&#39;;

@Component({
  template: &#39;Hello World&#39;
})
class HelloWorld {
  ionViewDidLoad() {
    console.log(&quot;I&#39;m alive!&quot;);
  }
  ionViewWillLeave() {
    console.log(&quot;Looks like I&#39;m about to leave :(&quot;);
  }
}
</code></pre>
<table>
<thead>
<tr>
<th>页面事件</th>
<th>返回</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>ionViewDidLoad</code></td>
<td>void</td>
<td>加载页面时运行。该事件仅在每个页面创建时发生一次。如果页面离开但被缓存，则此事件在后续查看时不会再次触发。<code>ionViewDidLoad</code> 事件是放置页面组织代码的好地方。</td>
</tr>
<tr>
<td><code>ionViewWillEnter</code></td>
<td>void</td>
<td>页面即将进入并成为激活页面时运行。</td>
</tr>
<tr>
<td><code>ionViewDidEnter</code></td>
<td>void</td>
<td>页面完全进入并且现在是激活页面时运行。无论是第一次加载还是缓存页面，此事件都会触发。</td>
</tr>
<tr>
<td><code>ionViewWillLeave</code></td>
<td>void</td>
<td>页面即将离开并不再是激活页面时运行。</td>
</tr>
<tr>
<td><code>ionViewDidLeave</code></td>
<td>void</td>
<td>页面完成离开并不再是激活页面时运行。</td>
</tr>
<tr>
<td><code>ionViewWillUnload</code></td>
<td>void</td>
<td>当页面即将被销毁并删除其元素时运行。</td>
</tr>
<tr>
<td><code>ionViewCanEnter</code></td>
<td>boolean/Promise&lt;void&gt;</td>
<td>在视图能够进入之前运行。这可以用作认证视图中的一种“守卫”，你需要在视图进入之前检查权限。</td>
</tr>
<tr>
<td><code>ionViewCanLeave</code></td>
<td>boolean/Promise&lt;void&gt;</td>
<td>在视图能够离开之前运行。这可以用作认证视图中的一种“守卫”，你需要在视图离开之前检查权限。</td>
</tr>
</tbody>
</table>
<h2 id="nav-guards">导航守卫</h2>
<p>在某些情况下，开发人员应该能够控制离开和进入的视图。为了做到这一点，NavController 具有 <code>ionViewCanEnter</code> 和 <code>ionViewCanLeave</code> 方法。类似于 Angular 的路由守卫，但更多地与 NavController 集成。例如，如果你想阻止用户离开视图：</p>

<pre><code class="lang-ts">export class MyClass{
 constructor(
   public navCtrl: NavController
  ){}

  pushPage(){
    this.navCtrl.push(DetailPage);
  }

  ionViewCanLeave(): boolean{
   // 这里我们可以返回 true 或 false 
   // 取决于我们是否想离开这个视图
   if(isValid(randomValue)){
      return true;
    } else {
      return false;
    }
  }
}
</code></pre>
<p>我们需要确保我们的 <code>navCtrl.push</code> 有捕获和处理错误的能力。如果你需要阻止视图进入，则可以执行相同的操作。</p>

<pre><code class="lang-ts">export class MyClass{
 constructor(
   public navCtrl: NavController
  ){}

  pushPage(){
    this.navCtrl.push(DetailPage);
  }

}

export class DetailPage(){
  constructor(
    public navCtrl: NavController
  ){}
  ionViewCanEnter(): boolean{
   // 这里我们可以返回 true 或 false
   // 取决于我们是否想离开这个视图
   if(isValid(randomValue)){
      return true;
    } else {
      return false;
    }
  }
}
</code></pre>
<p>与 <code>ionViewCanLeave</code> 类似，我们仍然需要捕获原始 <code>navCtrl.push</code> 以正确处理它。在处理 <code>ion-navbar</code> 中的后退按钮时，框架已经为你抓住了猎物。</p>

<h2 id="navoptions">NavOptions</h2>
<p><code>NavController</code> 上的一些方法允许自定义当前的过渡效果。要做到这一点，我们可以传递一个修改过的对象。</p>

<table>
<thead>
<tr>
<th>属性</th>
<th>值</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>animate</td>
<td><code>boolean</code></td>
<td>过渡效果是否应用动画。</td>
</tr>
<tr>
<td>animation</td>
<td><code>string</code></td>
<td>应该使用什么样的动画。</td>
</tr>
<tr>
<td>direction</td>
<td><code>string</code></td>
<td>用户正在浏览的导航方向。例如，用户是 <code>forward</code>, 还是 <code>back</code>？</td>
</tr>
<tr>
<td>duration</td>
<td><code>number</code></td>
<td>动画应持续的时长，以毫秒为单位。</td>
</tr>
<tr>
<td>easing</td>
<td><code>string</code></td>
<td>动画的缓动。</td>
</tr>
</tbody>
</table>
<p>属性的'动画'理解以下值： <code>md-transition</code>, <code>ios-transition</code> 和 <code>wp-transition</code>。</p>




<!-- @usage tag -->


<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="canGoBack"></div>

<h3>
<a class="anchor" name="canGoBack" href="#canGoBack">
<code>canGoBack()</code>


</a>
</h3>

如果存在我们可以弹出的有效的上一页，则返回 `true`。否则返回 `false`。







<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>boolean</code>

</div>




<div id="canSwipeBack"></div>

<h3>
<a class="anchor" name="canSwipeBack" href="#canSwipeBack">
<code>canSwipeBack()</code>


</a>
</h3>

是否可以使用向后滑动。如果无法后退，或者没有启用滑动，则返回 `false`。如果可以后退，并且允许向后滑动，则返回 `true`。









<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>boolean</code>

</div>




<div id="first"></div>

<h3>
<a class="anchor" name="first" href="#first">
<code>first()</code>


</a>
</h3>

返回此导航控制器堆栈中的第一个视图控制器。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>ViewController</code>

</div>




<div id="getActive"></div>

<h3>
<a class="anchor" name="getActive" href="#getActive">
<code>getActive()</code>


</a>
</h3>








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>ViewController</code> <p>返回激活的页面视图控制器。</p>


</div>




<div id="getActiveChildNav"></div>

<h3>
<a class="anchor" name="getActiveChildNav" href="#getActiveChildNav">
<code>getActiveChildNav()</code>


</a>
</h3>

返回激活的子导航。










<div id="getActiveChildNavs"></div>

<h3>
<a class="anchor" name="getActiveChildNavs" href="#getActiveChildNavs">
<code>getActiveChildNavs()</code>


</a>
</h3>

返回激活的子导航列表。










<div id="getAllChildNavs"></div>

<h3>
<a class="anchor" name="getAllChildNavs" href="#getAllChildNavs">
<code>getAllChildNavs()</code>


</a>
</h3>

返回所有子导航容器的列表。










<div id="getByIndex"></div>

<h3>
<a class="anchor" name="getByIndex" href="#getByIndex">
<code>getByIndex(index)</code>


</a>
</h3>




<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        index


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>要获取的页面的索引。</p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>ViewController</code> <p>返回与给定索引匹配的视图控制器。</p>


</div>




<div id="getPrevious"></div>

<h3>
<a class="anchor" name="getPrevious" href="#getPrevious">
<code>getPrevious(view)</code>


</a>
</h3>

返回给定视图控制器之前的视图控制器。如果没有视图控制器被传入，那么它将默认为激活的视图。



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        view


      </td>
      <td>

  <code>ViewController</code>
      </td>
      <td>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>viewController</code>

</div>




<div id="getSecondaryIdentifier"></div>

<h3>
<a class="anchor" name="getSecondaryIdentifier" href="#getSecondaryIdentifier">
<code>getSecondaryIdentifier()</code>


</a>
</h3>











<div id="getType"></div>

<h3>
<a class="anchor" name="getType" href="#getType">
<code>getType()</code>


</a>
</h3>











<div id="getViews"></div>

<h3>
<a class="anchor" name="getViews" href="#getViews">
<code>getViews()</code>


</a>
</h3>

返回此导航控制器中当前的视图堆栈。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Array&lt;ViewController&gt;</code> <p>此导航控制器中的视图控制器堆栈。</p>


</div>




<div id="goToRoot"></div>

<h3>
<a class="anchor" name="goToRoot" href="#goToRoot">
<code>goToRoot()</code>


</a>
</h3>











<div id="indexOf"></div>

<h3>
<a class="anchor" name="indexOf" href="#indexOf">
<code>indexOf(view)</code>


</a>
</h3>

返回给定视图控制器的索引。


<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        view


      </td>
      <td>

  <code>ViewController</code>
      </td>
      <td>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code>

</div>




<div id="insert"></div>

<h3>
<a class="anchor" name="insert" href="#insert">
<code>insert(insertIndex,&nbsp;page,&nbsp;params,&nbsp;opts)</code>


</a>
</h3>

将组件插入到指定索引处的导航堆栈中。如果你需要在导航堆栈中的任意位置添加组件，这非常有用。





<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        insertIndex


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>索引插入页面的位置。</p>


      </td>
    </tr>

    <tr>
      <td>
        page


      </td>
      <td>

  <code>Page</code>|<code>string</code>
      </td>
      <td>
        <p>要推入导航堆栈的组件类或深层链接（deeplink）名称。</p>


      </td>
    </tr>

    <tr>
      <td>
        params


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>你想要传递给下一个视图的任意 NavParams <strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>导航选项去与它的过渡效果。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="insertPages"></div>

<h3>
<a class="anchor" name="insertPages" href="#insertPages">
<code>insertPages(insertIndex,&nbsp;insertPages,&nbsp;opts)</code>


</a>
</h3>

将指定索引处的组件数组插入到导航堆栈中。数组中的最后一个组件将被实例化为一个视图，并生成动画来成为活动视图。





<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        insertIndex


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>你想要插入页面的索引。</p>


      </td>
    </tr>

    <tr>
      <td>
        insertPages


      </td>
      <td>

  <code>array</code>
      </td>
      <td>
        <p>一组对象，每个对象都有一个 <code>page</code> 和可选的 <code>params</code> 属性。</p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>导航选项与它的过渡效果。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="isActive"></div>

<h3>
<a class="anchor" name="isActive" href="#isActive">
<code>isActive(view)</code>


</a>
</h3>

返回给定视图是否为激活视图。


<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        view


      </td>
      <td>

  <code>ViewController</code>
      </td>
      <td>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>boolean</code>

</div>




<div id="isTransitioning"></div>

<h3>
<a class="anchor" name="isTransitioning" href="#isTransitioning">
<code>isTransitioning()</code>


</a>
</h3>

返回导航控制器是否正在过渡。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>boolean</code>

</div>




<div id="last"></div>

<h3>
<a class="anchor" name="last" href="#last">
<code>last()</code>


</a>
</h3>

返回此导航控制器堆栈中的最后一个页面。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>ViewController</code>

</div>




<div id="length"></div>

<h3>
<a class="anchor" name="length" href="#length">
<code>length()</code>


</a>
</h3>

返回此导航控制器中的视图数量。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>number</code> <p>此堆栈中的视图数量，包括当前视图。</p>


</div>




<div id="parent"></div>

<h3>
<a class="anchor" name="parent" href="#parent">
<code>parent</code>


</a>
</h3>

父导航实例。如果这是根导航，那么它将为 `null`。一个 `Tab` 实例的父项是 `Tabs`，否则父项将是另一个 nav，如果它不是根 nav 的话。












<div id="pop"></div>

<h3>
<a class="anchor" name="pop" href="#pop">
<code>pop(opts)</code>


</a>
</h3>

从当前组件调用导航来返回。与 `push()` 类似，你也可以传递导航选项。




<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>导航选项与它的过渡效果。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="popToRoot"></div>

<h3>
<a class="anchor" name="popToRoot" href="#popToRoot">
<code>popToRoot(opts)</code>


</a>
</h3>

返回到堆栈的根目录，不管它有多远。



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>导航选项与它的过渡效果。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="push"></div>

<h3>
<a class="anchor" name="push" href="#push">
<code>push(page,&nbsp;params,&nbsp;opts)</code>


</a>
</h3>

将新组件推入到当前导航堆栈里。将任何附加信息作为对象传递。这些附加信息可通过 NavParams 访问




<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        page


      </td>
      <td>

  <code>Page</code>|<code>string</code>
      </td>
      <td>
        <p>要推入导航堆栈的组件类或深层链接（deeplink）名称。</p>


      </td>
    </tr>

    <tr>
      <td>
        params


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>任意你想传递给下一个视图的 NavParams。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>导航选项与它的过渡效果。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="remove"></div>

<h3>
<a class="anchor" name="remove" href="#remove">
<code>remove(startIndex,&nbsp;removeCount,&nbsp;opts)</code>


</a>
</h3>

从指定索引的导航堆栈中移除页面。



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        startIndex


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>从堆栈中删除页面的起始索引。默认值是最后一页的索引。</p>


      </td>
    </tr>

    <tr>
      <td>
        removeCount


      </td>
      <td>

  <code>number</code>
      </td>
      <td>
        <p>要删除的页面数量，默认为删除 <code>1</code> <strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>任何你想使用的选项都可以通过过渡。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="removeView"></div>

<h3>
<a class="anchor" name="removeView" href="#removeView">
<code>removeView(viewController,&nbsp;opts)</code>


</a>
</h3>

从导航堆栈中移除指定的视图控制器。



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        viewController


      </td>
      <td>

  <code>ViewController</code>
      </td>
      <td>
        <p>The viewcontroller to remove.<strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>Any options you want to use pass to transtion.<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="setPages"></div>

<h3>
<a class="anchor" name="setPages" href="#setPages">
<code>setPages(pages,&nbsp;opts)</code>


</a>
</h3>

Set the views of the current navigation stack and navigate to the
last view. By default animations are disabled, but they can be enabled
by passing options to the navigation controller.You can also pass any
navigation params to the individual pages in the array.



<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        pages


      </td>
      <td>

  <code>Array&lt;{page:any, params: any}&gt;</code>
      </td>
      <td>
        <p>An array of objects, each with a <code>page</code> and optionally <code>params</code> property to load in the stack.</p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>Object</code>
      </td>
      <td>
        <p>导航选项与它的过渡效果。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="setRoot"></div>

<h3>
<a class="anchor" name="setRoot" href="#setRoot">
<code>setRoot(pageOrViewCtrl,&nbsp;params,&nbsp;opts,&nbsp;done)</code>


</a>
</h3>

设置当前导航堆栈的根目录。


<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>参数</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>
        pageOrViewCtrl


      </td>
      <td>

  <code>Page</code>|<code>string</code>|<code>ViewController</code>
      </td>
      <td>
        <p>你要在导航堆栈上推入的组件名称。</p>


      </td>
    </tr>

    <tr>
      <td>
        params


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>任意你想传递给下一个视图的 NavParams。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        opts


      </td>
      <td>

  <code>object</code>
      </td>
      <td>
        <p>任意你想可以通过过渡使用的选项。<strong class="tag">可选的</strong></p>


      </td>
    </tr>

    <tr>
      <td>
        done


      </td>
      <td>

  <code>Function</code>
      </td>
      <td>
        <p>回调函数完成。</p>


      </td>
    </tr>

  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Promise</code> <p>返回过渡完成时 resolved 的 promise。</p>


</div>




<div id="swipeBackEnabled"></div>

<h3>
<a class="anchor" name="swipeBackEnabled" href="#swipeBackEnabled">
<code>swipeBackEnabled</code>


</a>
</h3>











<div id="viewDidEnter"></div>

<h3>
<a class="anchor" name="viewDidEnter" href="#viewDidEnter">
<code>viewDidEnter</code>


</a>
</h3>

当组件完全成为激活的组件时，可以作为可观察对象被订阅。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个 observable</p>


</div>




<div id="viewDidLeave"></div>

<h3>
<a class="anchor" name="viewDidLeave" href="#viewDidLeave">
<code>viewDidLeave</code>


</a>
</h3>

当组件即将离开并且不再激活时，可以作为可观察对象被订阅。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个 observable</p>


</div>




<div id="viewDidLoad"></div>

<h3>
<a class="anchor" name="viewDidLoad" href="#viewDidLoad">
<code>viewDidLoad</code>


</a>
</h3>

当组件被加载时，可以作为可观察对象被订阅。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个 observable</p>


</div>




<div id="viewWillEnter"></div>

<h3>
<a class="anchor" name="viewWillEnter" href="#viewWillEnter">
<code>viewWillEnter</code>


</a>
</h3>

当组件即将被加载时，可以作为可观察对象被订阅。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个 observable</p>


</div>




<div id="viewWillLeave"></div>

<h3>
<a class="anchor" name="viewWillLeave" href="#viewWillLeave">
<code>viewWillLeave</code>


</a>
</h3>

当组件即将离开并不再激活时，可以作为可观察对象被订阅。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个 observable</p>


</div>




<div id="viewWillUnload"></div>

<h3>
<a class="anchor" name="viewWillUnload" href="#viewWillUnload">
<code>viewWillUnload</code>


</a>
</h3>

当组件被卸载和销毁时，可以作为可观察对象被订阅。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个 observable</p>


</div>







<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#navigation">Navigation Component Docs</a><!-- end content block -->


<!-- end body block -->

