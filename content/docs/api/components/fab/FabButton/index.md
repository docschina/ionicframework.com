---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "fabbutton"
title: "FabButton"
header_sub_title: "Ionic API Documentation"
doc: "FabButton"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/fab/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="fab-button" href="#fab-button"></a>

FabButton
<h3><code>[ion-fab]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/fab/fab.ts#L3">
改进这篇文档
</a>






<p>FABs（浮动按钮 Floating Action Buttons）是标准的 material 设计组件。它们被塑造成一个代表促进行动的圈。
按下时，它可能包含更多相关的操作。顾名思义，FABs 就是以固定的位置浮在内容上的。这不是专门用 <code>&lt;button ion-fab&gt;Button&lt;/button&gt;</code> 实现的，但它必须用 <code>&lt;ion-fab&gt;</code> 组件包装，如下所示：</p>
<pre><code class="lang-html">&lt;ion-content&gt;
 &lt;!-- 真正的浮动行为按钮，固定着的。它不会随着内容滚动 --&gt;
 &lt;ion-fab&gt;
   &lt;button ion-fab&gt;Button&lt;/button&gt;
 &lt;/ion-fab&gt;

 &lt;!-- 按钮形状像一个正常的按钮，与内容一起滚动 --&gt;
 &lt;button ion-fab&gt;Button&lt;/button&gt;
&lt;/ion-content&gt;
</code></pre>
<p>如果按钮没有用 <code>&lt;ion-fab&gt;</code> 包装，fab 按钮的行为就像一个正常的按钮，随着内容滚动。</p>
<p>请参阅 [ion-fab] 了解更多关于如何定位 fab 按钮的信息。</p>




<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;!-- 颜色 --&gt;
&lt;ion-fab&gt;
  &lt;button ion-fab color=&quot;primary&quot;&gt;Button&lt;/button&gt;
&lt;/ion-fab&gt;

&lt;!-- 迷你尺寸 --&gt;
&lt;ion-fab&gt;
  &lt;button ion-fab mini&gt;Small&lt;/button&gt;
&lt;/ion-fab&gt;
</code></pre>




<!-- @property tags -->

<h2><a class="anchor" name="attributes" href="#attributes">属性</a></h2>
<table class="table" style="margin:0;">
<thead>
<tr>
<th>属性</th>







<th>描述</th>
</tr>
</thead>
<tbody>

<tr>
<td>
mini
</td>



<td>
制作缩小尺寸的 fab 按钮。

</td>
</tr>

</tbody>
</table>



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
        <td><code>$fab-size</code></td>

          <td><code>56px</code></td>

        <td><p>Width and height of the FAB button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-mini-size</code></td>

          <td><code>40px</code></td>

        <td><p>Width and height of the FAB button mini</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-content-margin</code></td>

          <td><code>10px</code></td>

        <td><p>Margin of the FAB Container</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-list-margin</code></td>

          <td><code>10px</code></td>

        <td><p>Margin of the FAB List</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-list-button-background-color</code></td>

          <td><code>#f4f4f4</code></td>

        <td><p>Background color of the button in a list</p>
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
        <td><code>$fab-ios-background-color</code></td>

          <td><code>color($colors-ios, primary)</code></td>

        <td><p>Background color of the button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-text-color</code></td>

          <td><code>color-contrast($colors-ios, $fab-ios-background-color)</code></td>

        <td><p>Text color of the button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-background-color-activated</code></td>

          <td><code>color-shade($fab-ios-background-color)</code></td>

        <td><p>Background color of the activated button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-list-button-background-color</code></td>

          <td><code>$fab-list-button-background-color</code></td>

        <td><p>Background color of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-list-button-text-color</code></td>

          <td><code>color-contrast($colors-ios, $fab-ios-list-button-background-color)</code></td>

        <td><p>Text color of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-list-button-background-color-activated</code></td>

          <td><code>color-shade($fab-ios-list-button-background-color)</code></td>

        <td><p>Background color of the activated button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-list-button-transition-duration</code></td>

          <td><code>200ms</code></td>

        <td><p>Transition duration of the transform and opacity of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-list-button-transition-timing-function</code></td>

          <td><code>ease</code></td>

        <td><p>Speed curve of the transition of the transform and opacity of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-ios-list-button-transition-delay</code></td>

          <td><code>10ms</code></td>

        <td><p>Transition delay of the transform and opacity of the button in a list</p>
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
        <td><code>$fab-md-box-shadow</code></td>

          <td><code>0 4px 6px 0 rgba(0, 0, 0, .14), 0 4px 5px rgba(0, 0, 0, .1)</code></td>

        <td><p>Box shadow of the FAB button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-box-shadow-activated</code></td>

          <td><code>0 5px 15px 0 rgba(0, 0, 0, .4), 0 4px 7px 0 rgba(0, 0, 0, .1)</code></td>

        <td><p>Box shadow of the activated FAB button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-background-color</code></td>

          <td><code>color($colors-md, primary)</code></td>

        <td><p>Background color of the button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-text-color</code></td>

          <td><code>color-contrast($colors-md, $fab-md-background-color)</code></td>

        <td><p>Text color of the button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-background-color-activated</code></td>

          <td><code>color-shade($fab-md-background-color)</code></td>

        <td><p>Background color of the activated button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-list-button-background-color</code></td>

          <td><code>$fab-list-button-background-color</code></td>

        <td><p>Background color of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-list-button-text-color</code></td>

          <td><code>color-contrast($colors-md, $fab-md-list-button-background-color)</code></td>

        <td><p>Text color of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-list-button-background-color-activated</code></td>

          <td><code>color-shade($fab-md-list-button-background-color)</code></td>

        <td><p>Background color of the activated button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-list-button-transition-duration</code></td>

          <td><code>200ms</code></td>

        <td><p>Transition duration of the transform and opacity of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-list-button-transition-timing-function</code></td>

          <td><code>ease</code></td>

        <td><p>Speed curve of the transition of the transform and opacity of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-md-list-button-transition-delay</code></td>

          <td><code>10ms</code></td>

        <td><p>Transition delay of the transform and opacity of the button in a list</p>
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
        <td><code>$fab-wp-background-color</code></td>

          <td><code>color($colors-wp, primary)</code></td>

        <td><p>Background color of the button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-text-color</code></td>

          <td><code>color-contrast($colors-wp, $fab-wp-background-color)</code></td>

        <td><p>Text color of the button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-background-color-activated</code></td>

          <td><code>color-shade($fab-wp-background-color)</code></td>

        <td><p>Background color of the activated button</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-list-button-background-color</code></td>

          <td><code>$fab-list-button-background-color</code></td>

        <td><p>Background color of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-list-button-text-color</code></td>

          <td><code>color-contrast($colors-wp, $fab-wp-list-button-background-color)</code></td>

        <td><p>Text color of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-list-button-background-color-activated</code></td>

          <td><code>color-shade($fab-wp-list-button-background-color)</code></td>

        <td><p>Background color of the activated button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-list-button-transition-duration</code></td>

          <td><code>200ms</code></td>

        <td><p>Transition duration of the transform and opacity of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-list-button-transition-timing-function</code></td>

          <td><code>ease</code></td>

        <td><p>Speed curve of the transition of the transform and opacity of the button in a list</p>
</td>
      </tr>

      <tr>
        <td><code>$fab-wp-list-button-transition-delay</code></td>

          <td><code>10ms</code></td>

        <td><p>Transition delay of the transform and opacity of the button in a list</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#fabs">FAB Component Docs</a><!-- end content block -->


<!-- end body block -->

