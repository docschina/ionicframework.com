---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "fabcontainer"
title: "FabContainer"
header_sub_title: "Ionic API Documentation"
doc: "FabContainer"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/fab/www/"
angular_controller: APIDemoCtrl 
---









<h1 class="api-title">
<a class="anchor" name="fab-container" href="#fab-container"></a>

FabContainer
<h3><code>ion-fab</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/fab/fab-container.ts#L5">
Improve this doc
</a>






<p><code>&lt;ion-fab&gt;</code> 本身不是 FAB 按钮，而是一个辅助 fab 按钮（<code>&lt;button ion-fab&gt;</code>）的容器，可以将其放置在不随内容滚动的固定位置。它也被用来实现“ material 设计快速拨号（ speed dial ）”，即点击 FAB 按钮时会显示一小部分相关操作。</p>






<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;!-- 这个 fab 放在右上角 --&gt;
&lt;ion-content&gt;
 &lt;ion-fab top right&gt;
   &lt;button ion-fab&gt;Button&lt;/button&gt;
 &lt;/ion-fab&gt;

 &lt;!-- 这个 fab 放在内容视口的中心 --&gt;
 &lt;ion-fab center middle&gt;
   &lt;button ion-fab&gt;Button&lt;/button&gt;
 &lt;/ion-fab&gt;
&lt;/ion-content&gt;
</code></pre>
<p>Ionic 的 FAB 也支持“ material 设计的 fab快速拨号（ speed dial ）”。这是一个正常的 fab 按钮，显示点击时相关操作的列表。</p>
<p>相同的 <code>ion-fab</code> 容器可以包含几个不同的 <code>ion-fab-list</code> ：<code>top</code>, <code>bottom</code>, <code>left</code> 和 <code>right</code>。例如，如果你想要在主按钮顶部有一个按钮列表，则应该使用 <code>side=&quot;top&quot;</code> ，依此类推。默认情况下，如果 side 是省略的，那么 <code>side=&quot;bottom&quot;</code>。</p>



<pre><code class="lang-html">&lt;ion-content&gt;
 &lt;!-- 这个 fab 放在右下角 --&gt;
 &lt;ion-fab bottom right &gt;
   &lt;button ion-fab&gt;Share&lt;/button&gt;
   &lt;ion-fab-list side=&quot;top&quot;&gt;
     &lt;button ion-fab&gt;Facebook&lt;/button&gt;
     &lt;button ion-fab&gt;Twitter&lt;/button&gt;
     &lt;button ion-fab&gt;Youtube&lt;/button&gt;
   &lt;/ion-fab-list&gt;
   &lt;ion-fab-list side=&quot;left&quot;&gt;
     &lt;button ion-fab&gt;Vimeo&lt;/button&gt;
   &lt;/ion-fab-list&gt;
 &lt;/ion-fab&gt;
&lt;/ion-content&gt;
</code></pre>
<p>FAB 快速拨号（ speed dial ）也可以用编程方式关闭。</p>
<pre><code class="lang-html">&lt;ion-content&gt;
 &lt;ion-fab bottom right #fab&gt;
   &lt;button ion-fab&gt;Share&lt;/button&gt;
   &lt;ion-fab-list side=&quot;top&quot;&gt;
     &lt;button ion-fab (click)=&quot;share(&#39;facebook&#39;, fab)&quot;&gt;Facebook&lt;/button&gt;
     &lt;button ion-fab (click)=&quot;share(&#39;twitter&#39;, fab)&quot;&gt;Twitter&lt;/button&gt;
   &lt;/ion-fab-list&gt;
 &lt;/ion-fab&gt;
&lt;/ion-content&gt;
</code></pre>
<pre><code class="lang-ts">share(socialNet: string, fab: FabContainer) {
  fab.close();
  console.log(&quot;Sharing in&quot;, socialNet);
}
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
top
</td>



<td>
将 container 放置在内容的顶部
</td>
</tr>

<tr>
<td>
bottom
</td>



<td>
将 container 放置在内容的底部
</td>
</tr>

<tr>
<td>
left
</td>



<td>
将 container 放置在左边
</td>
</tr>

<tr>
<td>
right
</td>



<td>
将 container 放置在右边
</td>
</tr>

<tr>
<td>
middle
</td>



<td>
将 container 放置在垂直居中的位置
</td>
</tr>

<tr>
<td>
center
</td>



<td>
将 container 放置在水平居中的位置
</td>
</tr>

<tr>
<td>
edge
</td>



<td>
用于将 container 放置在内容和页眉/页脚之间

</td>
</tr>

</tbody>
</table>



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="close"></div>

<h3>
<a class="anchor" name="close" href="#close">
<code>close()</code>
  

</a>
</h3>

关闭一个激活的 FAB 列表 container











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

