---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "menu"
title: "Menu"
header_sub_title: "Ionic API Documentation"
doc: "Menu"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/menu/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="menu" href="#menu"></a>

Menu
<h3><code>ion-menu</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/menu/menu.ts#L17">
改进这篇文档
</a>






<p>Menu 组件是一个从当前视图侧面滑入的抽屉导航（navigation drawer）。默认情况下，它从左侧滑入，但侧面可以被覆盖。menu 将根据平台模式显示不同的样式，但显示类型也可以更改为任意可用的 <a href="#menu-types">菜单类型</a>。menu 元素应该是应用的 content 元素兄弟。可以有任意数量的菜单附加到 content。这些可以通过模板进行控制，也可以使用 <a href="../../app/MenuController">MenuController</a> 进行编程式控制。</p>









<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;ion-menu [content]=&quot;mycontent&quot;&gt;
  &lt;ion-content&gt;
    &lt;ion-list&gt;
      &lt;p&gt;some menu content, could be list items&lt;/p&gt;
    &lt;/ion-list&gt;
  &lt;/ion-content&gt;
&lt;/ion-menu&gt;

&lt;ion-nav #mycontent [root]=&quot;rootPage&quot;&gt;&lt;/ion-nav&gt;
</code></pre>
<p>要将 menu 添加到应用程序，应该将 <code>&lt;ion-menu&gt;</code> 元素作为相邻元素添加到它所属的 <code>ion-nav</code>。应该将一个 <a href="https://angular.io/docs/ts/latest/guide/user-input.html#local-variables">局部变量</a> 添加到 <code>ion-nav</code> 并传递给 <code>ion-menu</code> 的 <code>content</code> 属性。</p>
<p>这会告诉菜单它绑定的是什么以及要观察手势的元素。在下面的示例中，<code>content</code> 使用 <a href="https://angular.io/docs/ts/latest/guide/template-syntax.html#!#property-binding">属性绑定</a>，因为 <code>mycontent</code> 是对 <code>&lt;ion-nav&gt;</code> 元素的引用，而不是字符串。</p>
<h3 id="opening-closing-menus">打开/关闭菜单</h3>
<p>有几种方法可以打开或关闭菜单。菜单可以使用 <a href="../MenuToggle">MenuToggle</a> 指令从模板中切换打开或关闭的状态。它也可以使用 <a href="../MenuClose">MenuClose</a> 指令从模板中关闭菜单。要以编程方式显示菜单，请注入 <a href="../MenuController">MenuController</a> 服务商程序并调用任意的 <code>MenuController</code> 方法。</p>
<h3 id="menu-types">菜单类型</h3>
<p>该菜单支持多种显示类型：<code>overlay</code>, <code>reveal</code> 和 <code>push</code>。默认情况下，它将根据平台模式使用正确的类型，不过可以更改。Material 设计和 Windows 模式的默认类型为 <code>overlay</code>，而 <code>reveal</code> 为 iOS 模式的默认类型。菜单类型可以在应用程序的 <a href="../../config/Config">配置</a> 中通过 <code>menuType</code> 属性进行更改，也可以在 <code>&lt;ion-menu&gt;</code> 元素的 <code>type</code> 属性中传递。有关更改菜单类型的示例，请参阅下面的用法。</p>
<h3 id="navigation-bar-behavior">导航栏行为</h3>
<p>如果 <a href="../MenuToggle">MenuToggle</a> 按钮被添加到页面的 <a href="../../navbar/Navbar">Navbar</a> 中，则该按钮仅在它所在的页面是当前的根页面时才会显示。根页面是应用程序中加载的初始页面，或者是使用 <a href="../../navbar/Navbar">Navbar</a> 上的 <a href="../../nav/NavController/#setRoot">setRoot</a> 方法设置为根页面的页面。</p>
<p>例如，假设应用程序有两个页面，<code>Page1</code> 和 <code>Page2</code>，并且它们的导航栏中都有一个 <code>MenuToggle</code> 按钮。假设加载到应用程序中的初始页面是 <code>Page1</code>，使其成为根页面。<code>Page1</code>将显示 <code>MenuToggle</code> 按钮，但是一旦将 <code>Page2</code> 推入导航堆栈中，<code>MenuToggle</code> 将不会显示。</p>
<h3 id="persistent-menus">持久菜单</h3>
<p>持久性菜单在导航堆栈中的所有页面上的 <a href="../../navbar/Navbar">导航栏</a> 中显示 <a href="../MenuToggle">MenuToggle</a> 按钮。要在 <code>&lt;ion-menu&gt;</code> 元素上将菜单 <code>persistent</code> 设置保持为 <code>true</code>。请注意，这只会影响附加到 <code>菜单</code>的<code>导航栏</code> 中的 <code>MenuToggle</code> 按钮，其 <code>persistent</code> 设置为 <code>true</code>，其他任何 <code>MenuToggle</code> 按钮都不会受到影响。</p>
<h3 id="menu-side">菜单侧栏</h3>
<p>默认情况下，菜单从左侧滑入，但是可以通过将 <code>right</code> 属性传递给 <code>side</code> 来覆盖它：</p>























<pre><code class="lang-html">&lt;ion-menu side=&quot;right&quot; [content]=&quot;mycontent&quot;&gt;...&lt;/ion-menu&gt;
</code></pre>
<h3 id="menu-type">菜单类型</h3>
<p>通过在 <code>&lt;ion-menu&gt;</code> 上传递 <code>type</code> 值来更改菜单类型：</p>
<pre><code class="lang-html">&lt;ion-menu type=&quot;overlay&quot; [content]=&quot;mycontent&quot;&gt;...&lt;/ion-menu&gt;
</code></pre>
<p>它也可以在应用程序的配置中设置。下面将设置菜单类型来 <code>push</code> 所有模式，后续会将类型设置为 <code>overlay</code> 的 <code>ios</code> 模式。</p>

<pre><code class="lang-ts">// in NgModules

imports: [
  IonicModule.forRoot(MyApp,{
    menuType: &#39;push&#39;,
    platforms: {
      ios: {
        menuType: &#39;overlay&#39;,
      }
    }
  })
],
</code></pre>
<h3 id="displaying-the-menu">显示菜单</h3>
<p>要从模板中切换菜单，请在页面模板中的任意位置添加一个带 <code>menuToggle</code> 指令的按钮：</p>

<pre><code class="lang-html">&lt;button ion-button menuToggle&gt;Toggle Menu&lt;/button&gt;
</code></pre>
<p>要关闭菜单，请添加 <code>menuClose</code> 按钮。它可以添加到 content 的任何地方，甚至菜单本身。在它下面添加到菜单的内容：</p>


<pre><code class="lang-html">&lt;ion-menu [content]=&quot;mycontent&quot;&gt;
  &lt;ion-content&gt;
    &lt;ion-list&gt;
      &lt;ion-item menuClose detail-none&gt;Close Menu&lt;/ion-item&gt;
    &lt;/ion-list&gt;
  &lt;/ion-content&gt;
&lt;/ion-menu&gt;
</code></pre>
<p>有关这些指令的更多信息，请参阅 <a href="../MenuToggle">MenuToggle</a> 和 <a href="../MenuClose">MenuClose</a> 文档。</p>
<p>菜单也可以通过使用 <code>MenuController</code> 从页面进行控制。将 <code>MenuController</code> 提供商注入到页面，然后调用其任意方法。在下面的例子中，<code>openMenu</code> 方法会在调用它时打开菜单。</p>




<pre><code class="lang-ts">import { Component } from &#39;@angular/core&#39;;
import { MenuController } from &#39;ionic-angular&#39;;

@Component({...})
export class MyPage {
 constructor(public menuCtrl: MenuController) {}

 openMenu() {
   this.menuCtrl.open();
 }
}
</code></pre>
<p>有关所有方法和用法信息，请参阅 <a href="../../app/MenuController">MenuController</a> API 文档。</p>





<!-- @property tags -->



<!-- instance methods on the class -->
<!-- input methods on the class -->
<h2><a class="anchor" name="input-properties" href="#input-properties">输入属性</a></h2>
<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>属性</th>
      <th>类型</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>content</td>
      <td><code>any</code></td>
      <td><p>对菜单使用的 content 元素的引用。</p>
</td>
    </tr>

    <tr>
      <td>enabled</td>
      <td><code>boolean</code></td>
      <td><p>如果为 true，则启用该菜单。默认为 <code>true</code>。</p>
</td>
    </tr>

    <tr>
      <td>id</td>
      <td><code>string</code></td>
      <td><p>菜单的 id。</p>
</td>
    </tr>

    <tr>
      <td>persistent</td>
      <td><code>boolean</code></td>
      <td><p>如果为 true，菜单将保留在子页面上。</p>
</td>
    </tr>

    <tr>
      <td>side</td>
      <td><code>string</code></td>
      <td><p>菜单应放置在视图的哪一侧。默认 <code>&quot;left&quot;</code>。</p>
</td>
    </tr>

    <tr>
      <td>swipeEnabled</td>
      <td><code>boolean</code></td>
      <td><p>如果为 true，则启用滑动菜单。默认为 <code>true</code>。</p>
</td>
    </tr>

    <tr>
      <td>type</td>
      <td><code>string</code></td>
      <td><p>菜单的显示类型。默认值取决于模式，请参阅 <a href="../../config/Config">config</a> 中的 <code>menuType</code>。可用选项：<code>&quot;overlay&quot;</code>, <code>&quot;reveal&quot;</code>, <code>&quot;push&quot;</code>。</p>


</td>
    </tr>

  </tbody>
</table>
<!-- output events on the class -->
<h2><a class="anchor" name="output-events" href="#output-events">输出事件</a></h2>
<table class="table param-table" style="margin:0;">
  <thead>
    <tr>
      <th>属性</th>
      <th>详情</th>
    </tr>
  </thead>
  <tbody>

    <tr>
      <td>ionClose</td>
      <td><p>菜单关闭时触发。</p>
</td>
    </tr>

    <tr>
      <td>ionDrag</td>
      <td><p>当菜单被拖动着打开时触发。</p>
</td>
    </tr>

    <tr>
      <td>ionOpen</td>
      <td><p>菜单打开时触发。</p>
</td>
    </tr>

  </tbody>
</table>


  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">



      <a ng-init="setSassPlatform('base')" ng-class="{ active: active === 'base' }" ng-click="setSassPlatform('base')" >All</a>



      <a ng-class="{ active: active === 'ios' }" ng-click="setSassPlatform('ios')">iOS</a>



      <a ng-class="{ active: active === 'md' }" ng-click="setSassPlatform('md')">Material Design</a>



      <a ng-class="{ active: active === 'wp' }" ng-click="setSassPlatform('wp')">Windows Platform</a>



  </div>



  <table ng-show="active === 'base'" id="sass-base" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$menu-width</code></td>

          <td><code>304px</code></td>

        <td><p>Width of the menu</p>
</td>
      </tr>

      <tr>
        <td><code>$menu-small-width</code></td>

          <td><code>$menu-width - 40px</code></td>

        <td><p>Width of the menu on small devices (under 340px)</p>
</td>
      </tr>

    </tbody>
  </table>

  <table ng-show="active === 'ios'" id="sass-ios" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$menu-ios-background</code></td>

          <td><code>$background-ios-color</code></td>

        <td><p>Background of the menu</p>
</td>
      </tr>

      <tr>
        <td><code>$menu-ios-box-shadow-color</code></td>

          <td><code>rgba(0, 0, 0, .25)</code></td>

        <td><p>Box shadow color of the menu</p>
</td>
      </tr>

      <tr>
        <td><code>$menu-ios-box-shadow</code></td>

          <td><code>0 0 10px $menu-ios-box-shadow-color</code></td>

        <td><p>Box shadow of the menu</p>
</td>
      </tr>

    </tbody>
  </table>

  <table ng-show="active === 'md'" id="sass-md" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$menu-md-background</code></td>

          <td><code>$background-md-color</code></td>

        <td><p>Background of the menu</p>
</td>
      </tr>

      <tr>
        <td><code>$menu-md-box-shadow-color</code></td>

          <td><code>rgba(0, 0, 0, .25)</code></td>

        <td><p>Box shadow color of the menu</p>
</td>
      </tr>

      <tr>
        <td><code>$menu-md-box-shadow</code></td>

          <td><code>0 0 10px $menu-md-box-shadow-color</code></td>

        <td><p>Box shadow of the menu</p>
</td>
      </tr>

    </tbody>
  </table>

  <table ng-show="active === 'wp'" id="sass-wp" class="table param-table" style="margin:0;">
    <thead>
      <tr>
        <th>Property</th>
        <th>Default</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>

      <tr>
        <td><code>$menu-wp-background</code></td>

          <td><code>#f2f2f2</code></td>

        <td><p>Background of the menu</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#menus">Menu Component Docs</a>,
<a href="../../app/MenuController">MenuController API Docs</a>,
<a href="../../nav/Nav">Nav API Docs</a>,
<a href="../../nav/NavController">NavController API Docs</a><!-- end content block -->


<!-- end body block -->

