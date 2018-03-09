---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "menuclose"
title: "MenuClose"
header_sub_title: "Ionic API Documentation"
doc: "MenuClose"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/menu/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="menu-close" href="#menu-close"></a>

MenuClose
<h3><code>[menuClose]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/menu/menu-close.ts#L2">
改进这篇文档
</a>






<p><code>menuClose</code> 指令可以放在任意按钮上去关闭已经打开的菜单。</p>




<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<p>一个简单的 <code>menuClose</code> 按钮可以使用下面的标记来添加：</p>
<pre><code class="lang-html">&lt;button ion-button menuClose&gt;Close Menu&lt;/button&gt;
</code></pre>
<p>要通过 id 或 side 关闭某个菜单，请给 <code>menuClose</code> 指令一个值。</p>

<pre><code class="lang-html">&lt;button ion-button menuClose=&quot;left&quot;&gt;Close Left Menu&lt;/button&gt;
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->


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

