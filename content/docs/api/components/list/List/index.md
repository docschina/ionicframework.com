---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "list"
title: "List"
header_sub_title: "Ionic API Documentation"
doc: "List"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/list/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="list" href="#list"></a>

List
<h3><code>ion-list</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/list/list.ts#L8">
改进这篇文档
</a>






<p>List 是几乎所有移动应用程序中广泛使用的界面元素，可以包括从基本文本到按钮，开关，图标和缩略图等各种内容。</p>
<p>包含 items 的列表和列表项本身可以是任何 HTML 元素。</p>
<p>使用 List 和 Item 组件可以轻松支持各种交互模式，例如滑动编辑，拖动重新排序和删除 items。</p>









<!-- @usage tag -->


<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="closeSlidingItems"></div>

<h3>
<a class="anchor" name="closeSlidingItems" href="#closeSlidingItems">
<code>closeSlidingItems()</code>


</a>
</h3>

关闭所有打开的滑动 items。









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
      <td>sliding</td>
      <td><code>boolean</code></td>
      <td><p>如果为 true，滑动的 items将被启用。</p>
</td>
    </tr>

  </tbody>
</table><h2><a class="anchor" name="advanced" href="#advanced">进阶</a></h2>
<p>启用滑动 items。</p>
<pre><code class="lang-ts">import { Component, ViewChild } from &#39;@angular/core&#39;;
import { List } from &#39;ionic-angular&#39;;

@Component({...})
export class MyClass {
  @ViewChild(List) list: List;

  constructor() { }

  stopSliding() {
    this.list.enableSlidingItems(false);
  }
}
</code></pre>



  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">



      <a ng-init="setSassPlatform('ios')" ng-class="{ active: active === 'ios' }" ng-click="setSassPlatform('ios')" >iOS</a>



      <a ng-class="{ active: active === 'md' }" ng-click="setSassPlatform('md')">Material Design</a>



      <a ng-class="{ active: active === 'wp' }" ng-click="setSassPlatform('wp')">Windows Platform</a>



  </div>



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
        <td><code>$list-ios-margin-top</code></td>

          <td><code>10px</code></td>

        <td><p>Margin top of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-margin-end</code></td>

          <td><code>$list-ios-margin-right</code></td>

        <td><p>Margin end of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-margin-bottom</code></td>

          <td><code>32px</code></td>

        <td><p>Margin bottom of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-margin-start</code></td>

          <td><code>$list-ios-margin-left</code></td>

        <td><p>Margin start of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-ios-margin-top</code></td>

          <td><code>16px</code></td>

        <td><p>Margin top of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-ios-margin-end</code></td>

          <td><code>$list-inset-ios-margin-right</code></td>

        <td><p>Margin end of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-ios-margin-bottom</code></td>

          <td><code>16px</code></td>

        <td><p>Margin bottom of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-ios-margin-start</code></td>

          <td><code>$list-inset-ios-margin-left</code></td>

        <td><p>Margin start of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-ios-border-radius</code></td>

          <td><code>4px</code></td>

        <td><p>Border radius of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-padding-start</code></td>

          <td><code>$list-ios-header-padding-left</code></td>

        <td><p>Padding start of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-border-bottom</code></td>

          <td><code>$hairlines-width solid $list-ios-border-color</code></td>

        <td><p>Border bottom of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-font-size</code></td>

          <td><code>1.2rem</code></td>

        <td><p>Font size of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-font-weight</code></td>

          <td><code>500</code></td>

        <td><p>Font weight of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-letter-spacing</code></td>

          <td><code>.1rem</code></td>

        <td><p>Letter spacing of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-text-transform</code></td>

          <td><code>uppercase</code></td>

        <td><p>Text transform of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-color</code></td>

          <td><code>#333</code></td>

        <td><p>Text color of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-ios-header-background-color</code></td>

          <td><code>transparent</code></td>

        <td><p>Background color of the header in a list</p>
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
        <td><code>$list-md-margin-top</code></td>

          <td><code>16px</code></td>

        <td><p>Margin top of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-margin-end</code></td>

          <td><code>$list-md-margin-right</code></td>

        <td><p>Margin end of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-margin-bottom</code></td>

          <td><code>16px</code></td>

        <td><p>Margin bottom of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-margin-start</code></td>

          <td><code>$list-md-margin-left</code></td>

        <td><p>Margin start of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-md-margin-top</code></td>

          <td><code>16px</code></td>

        <td><p>Margin top of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-md-margin-end</code></td>

          <td><code>$list-inset-md-margin-right</code></td>

        <td><p>Margin end of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-md-margin-bottom</code></td>

          <td><code>16px</code></td>

        <td><p>Margin bottom of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-md-margin-start</code></td>

          <td><code>$list-inset-md-margin-left</code></td>

        <td><p>Margin start of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-md-border-radius</code></td>

          <td><code>2px</code></td>

        <td><p>Border radius of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-header-margin-bottom</code></td>

          <td><code>13px</code></td>

        <td><p>Margin bottom of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-header-padding-start</code></td>

          <td><code>$list-md-header-padding-left</code></td>

        <td><p>Padding start of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-header-min-height</code></td>

          <td><code>4.5rem</code></td>

        <td><p>Minimum height of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-header-border-top</code></td>

          <td><code>1px solid $list-md-border-color</code></td>

        <td><p>Border top of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-header-font-size</code></td>

          <td><code>1.4rem</code></td>

        <td><p>Font size of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-md-header-color</code></td>

          <td><code>#757575</code></td>

        <td><p>Text color of the header in a list</p>
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
        <td><code>$list-wp-margin-top</code></td>

          <td><code>16px</code></td>

        <td><p>Margin top of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-margin-end</code></td>

          <td><code>$list-wp-margin-right</code></td>

        <td><p>Margin end of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-margin-bottom</code></td>

          <td><code>16px</code></td>

        <td><p>Margin bottom of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-margin-start</code></td>

          <td><code>$list-wp-margin-left</code></td>

        <td><p>Margin start of the list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-wp-margin-top</code></td>

          <td><code>16px</code></td>

        <td><p>Margin top of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-wp-margin-end</code></td>

          <td><code>$list-inset-wp-margin-right</code></td>

        <td><p>Margin end of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-wp-margin-bottom</code></td>

          <td><code>16px</code></td>

        <td><p>Margin bottom of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-wp-margin-start</code></td>

          <td><code>$list-inset-wp-margin-left</code></td>

        <td><p>Margin start of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-inset-wp-border-radius</code></td>

          <td><code>2px</code></td>

        <td><p>Border radius of the inset list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-header-padding-start</code></td>

          <td><code>$list-wp-header-padding-left</code></td>

        <td><p>Padding start of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-header-border-bottom</code></td>

          <td><code>1px solid $list-wp-border-color</code></td>

        <td><p>Border bottom of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-header-font-size</code></td>

          <td><code>2rem</code></td>

        <td><p>Font size of the header in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$list-wp-header-color</code></td>

          <td><code>$list-wp-text-color</code></td>

        <td><p>Text color of the header in a list</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#lists">List Component Docs</a><!-- end content block -->


<!-- end body block -->

