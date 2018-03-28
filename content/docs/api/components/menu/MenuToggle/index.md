---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "menutoggle"
title: "MenuToggle"
header_sub_title: "Ionic API Documentation"
doc: "MenuToggle"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/menu/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="menu-toggle" href="#menu-toggle"></a>

MenuToggle
<h3><code>[menuToggle]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/menu/menu-toggle.ts#L5">
改进这篇文档
</a>






<p><code>menuToggle</code> 指令可以放在任何按钮上，用来打开或关闭菜单。如果将其添加到页面的 <a href="../../navbar/NavBar">NavBar</a> 中，则该按钮仅会在其所在页面是当前的根页面时才会显示。有关更多信息，请参阅 <a href="../Menu#navigation-bar-behavior">Menu Navigation Bar Behavior</a> 文档。</p>







<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<p>可以使用以下标记添加一个简单的 <code>menuToggle</code> 按钮：</p>
<pre><code class="lang-html">&lt;button ion-button menuToggle&gt;Toggle Menu&lt;/button&gt;
</code></pre>
<p>要通过其 id 或 side 切换特定的菜单，请给 <code>menuToggle</code> 指令一个值。</p>

<pre><code class="lang-html">&lt;button ion-button menuToggle=&quot;right&quot;&gt;Toggle Right Menu&lt;/button&gt;
</code></pre>
<p>如果将 <code>menuToggle</code> 放置在导航栏或工具栏中，它应该放置在 <code>&lt;ion-navbar&gt;</code> 或 <code>&lt;ion-toolbar&gt;</code> 的子元素中，而不是放在 <code>&lt;ion-buttons&gt;</code> 元素中：</p>


<pre><code class="lang-html">&lt;ion-header&gt;

  &lt;ion-navbar&gt;
    &lt;ion-buttons start&gt;
      &lt;button ion-button&gt;
        &lt;ion-icon name=&quot;contact&quot;&gt;&lt;/ion-icon&gt;
      &lt;/button&gt;
    &lt;/ion-buttons&gt;
    &lt;button ion-button menuToggle&gt;
      &lt;ion-icon name=&quot;menu&quot;&gt;&lt;/ion-icon&gt;
    &lt;/button&gt;
    &lt;ion-title&gt;
      Title
    &lt;/ion-title&gt;
    &lt;ion-buttons end&gt;
      &lt;button ion-button (click)=&quot;doClick()&quot;&gt;
        &lt;ion-icon name=&quot;more&quot;&gt;&lt;/ion-icon&gt;
      &lt;/button&gt;
    &lt;/ion-buttons&gt;
  &lt;/ion-navbar&gt;

&lt;/ion-header&gt;
</code></pre>
<p>类似于 <code>&lt;ion-buttons&gt;</code>，<code>menuToggle</code> 可以使用 <code>start</code>, <code>end</code>, <code>left</code>, 或 <code>right</code> 进行定位：</p>

<pre><code class="lang-html">&lt;ion-toolbar&gt;
  &lt;button ion-button menuToggle right&gt;
    &lt;ion-icon name=&quot;menu&quot;&gt;&lt;/ion-icon&gt;
  &lt;/button&gt;
  &lt;ion-title&gt;
    Title
  &lt;/ion-title&gt;
  &lt;ion-buttons end&gt;
    &lt;button ion-button (click)=&quot;doClick()&quot;&gt;
      &lt;ion-icon name=&quot;more&quot;&gt;&lt;/ion-icon&gt;
    &lt;/button&gt;
  &lt;/ion-buttons&gt;
&lt;/ion-toolbar&gt;
</code></pre>
<p>有关不同位置的更多信息，请参阅 <a href="../../toolbar/Toolbar">Toolbar API 文档</a>。</p>





<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="ngAfterContentInit"></div>

<h3>
<a class="anchor" name="ngAfterContentInit" href="#ngAfterContentInit">
<code>ngAfterContentInit()</code>


</a>
</h3>












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
<a href="../../menu/Menu">Menu API Docs</a><!-- end content block -->


<!-- end body block -->

