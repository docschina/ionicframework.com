---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "menucontroller"
title: "MenuController"
header_sub_title: "Ionic API Documentation"
doc: "MenuController"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/menu/www/"
angular_controller: APIDemoCtrl 
---









<h1 class="api-title">
<a class="anchor" name="menu-controller" href="#menu-controller"></a>

MenuController





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/app/menu-controller.ts#L2">
Improve this doc
</a>






<p> MenuController 是一个用来方便操控<a href="../../Menu/Menu/">菜单</a>的提供商（provider）。它的方法可以用来显示菜单，启用菜单，切换菜单等等。控制器将通过 <code>side</code>， <code>id</code> 获得菜单的引用，如果这些都不传递给它，它将获取它找到的第一个菜单。</p>







<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<p>首先添加一个基本菜单组件。有关添加菜单组件的更多信息，请参阅<a href="../../Menu/Menu/">菜单</a> API 文档。</p>

<pre><code class="lang-html">&lt;ion-menu [content]=&quot;mycontent&quot;&gt;
  &lt;ion-content&gt;
    &lt;ion-list&gt;
    ...
    &lt;/ion-list&gt;
  &lt;/ion-content&gt;
&lt;/ion-menu&gt;

&lt;ion-nav #mycontent [root]=&quot;rootPage&quot;&gt;&lt;/ion-nav&gt;
</code></pre>
<p>要调用控制器方法，请将 <code>MenuController</code> 提供商注入到页面。然后创建一些打开，关闭和切换菜单的方法。</p>


<pre><code class="lang-ts">import { Component } from &#39;@angular/core&#39;;
import { MenuController } from &#39;ionic-angular&#39;;

@Component({...})
export class MyPage {

 constructor(public menuCtrl: MenuController) {

 }

 openMenu() {
   this.menuCtrl.open();
 }

 closeMenu() {
   this.menuCtrl.close();
 }

 toggleMenu() {
   this.menuCtrl.toggle();
 }

}
</code></pre>
<p>由于只有一个菜单存在， <code>MenuController</code> 将获取正确的菜单并为这个菜单调用每个正确的方法。</p>
<h3 id="multiple-menus-on-different-sides">在不同侧栏的多个菜单</h3>
<p>对于既具有左也有右菜单的应用程序，可以通过传递菜单的 <code>side</code> 来获取所需的菜单。如果没有传递，它将默认为 <code>&quot;左&quot;</code> 菜单。</p>



<pre><code class="lang-html">&lt;ion-menu side=&quot;left&quot; [content]=&quot;mycontent&quot;&gt;...&lt;/ion-menu&gt;
&lt;ion-menu side=&quot;right&quot; [content]=&quot;mycontent&quot;&gt;...&lt;/ion-menu&gt;
&lt;ion-nav #mycontent [root]=&quot;rootPage&quot;&gt;&lt;/ion-nav&gt;
</code></pre>
<pre><code class="lang-ts">toggleLeftMenu() {
  this.menuCtrl.toggle();
}

toggleRightMenu() {
  this.menuCtrl.toggle(&#39;right&#39;);
}
</code></pre>
<h3 id="multiple-menus-on-the-same-side">在同一侧的多个菜单</h3>
<p>一个应用程序可以在同一侧有多个菜单。为了确定要控制的菜单，应该传递一个 <code>id</code> 。在下面的例子中，带有 <code>认证（authenticated）</code> id的菜单将被启用，并将具有 <code>未认证（unauthenticated）</code> id 的菜单禁用。</p>



<pre><code class="lang-html">&lt;ion-menu id=&quot;authenticated&quot; side=&quot;left&quot; [content]=&quot;mycontent&quot;&gt;...&lt;/ion-menu&gt;
&lt;ion-menu id=&quot;unauthenticated&quot; side=&quot;left&quot; [content]=&quot;mycontent&quot;&gt;...&lt;/ion-menu&gt;
&lt;ion-nav #mycontent [root]=&quot;rootPage&quot;&gt;&lt;/ion-nav&gt;
</code></pre>
<pre><code class="lang-ts">enableAuthenticatedMenu() {
  this.menuCtrl.enable(true, &#39;authenticated&#39;);
  this.menuCtrl.enable(false, &#39;unauthenticated&#39;);
}
</code></pre>
<p>注意：如果一个应用程序只有一个菜单，则没有理由传递一个 <code>id</code>。</p>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="close"></div>

<h3>
<a class="anchor" name="close" href="#close">
<code>close(menuId)</code>
  

</a>
</h3>

以编程方式关闭菜单。如果没有`menuId`作为第一个参数传递进来它就会关闭所有打开的菜单。如果有`menuId`
被给出它将根据这个参数准确关闭菜单。



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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Promise</code> <p>当菜单完全关闭时返回一个 promise。</p>


</div>




<div id="enable"></div>

<h3>
<a class="anchor" name="enable" href="#enable">
<code>enable(menuId)</code>
  

</a>
</h3>

用于启用或禁用菜单。例如，可能有多个左边的菜单，但同一时间只能有其中一个能够在相同的位置打开。如果同一侧有多个菜单，则只启用一个菜单，并自动禁用在同一边的所有其他菜单。





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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>
    
        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Menu</code> <p>返回菜单实例，这对链式调用很有帮助。</p>


</div>




<div id="get"></div>

<h3>
<a class="anchor" name="get" href="#get">
<code>get(menuId)</code>
  

</a>
</h3>

用于获取菜单实例。如果没有提供`menuId`，那么它会返回找到的第一个菜单。如果 `menuId` 是 `left` 或 `right`，那么它会返回启用的那个菜单。否则，如果`menuId`被提供了，那么它会尝试使用菜单的 `id` 属性找到菜单。如果找不到菜单，就会返回`null`。






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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Menu</code> <p>如果找到的话返回菜单的实例，否则返回 <code>null</code>。</p>


</div>




<div id="getMenus"></div>

<h3>
<a class="anchor" name="getMenus" href="#getMenus">
<code>getMenus()</code>
  

</a>
</h3>








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Array&lt;Menu&gt;</code> <p>返回一个由所有菜单实例的数组。</p>


</div>




<div id="getOpen"></div>

<h3>
<a class="anchor" name="getOpen" href="#getOpen">
<code>getOpen()</code>
  

</a>
</h3>








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Menu</code> <p>如果菜单已经打开返回菜单实例，否则返回 <code>null</code>。</p>


</div>




<div id="isEnabled"></div>

<h3>
<a class="anchor" name="isEnabled" href="#isEnabled">
<code>isEnabled(menuId)</code>
  

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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>boolean</code> <p>如果菜单当前是启用的，返回 true，否则返回 false</p>


</div>




<div id="isOpen"></div>

<h3>
<a class="anchor" name="isOpen" href="#isOpen">
<code>isOpen(menuId)</code>
  

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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>boolean</code> <p>如果指定的菜单当前是打开的返回 true，否则返回false。
如果 menuId 没有被指定，返回当前是否有任意菜单被打开的布尔值。</p>


</div>




<div id="open"></div>

<h3>
<a class="anchor" name="open" href="#open">
<code>open(menuId)</code>
  

</a>
</h3>

以编程方式打开菜单。


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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Promise</code> <p>在菜单完全打开时返回一个 promise 。</p>


</div>




<div id="swipeEnable"></div>

<h3>
<a class="anchor" name="swipeEnable" href="#swipeEnable">
<code>swipeEnable(shouldEnable,&nbsp;menuId)</code>
  

</a>
</h3>

用来启用或禁用滑动打开菜单的功能。


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
        shouldEnable
        
        
      </td>
      <td>
        
  <code>boolean</code>
      </td>
      <td>
        <p>如果想让菜单滑动则为 true，否则为 false。</p>

        
      </td>
    </tr>
    
    <tr>
      <td>
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Menu</code> <p>返回菜单实例，这对链式调用非常有帮助。</p>


</div>




<div id="toggle"></div>

<h3>
<a class="anchor" name="toggle" href="#toggle">
<code>toggle(menuId)</code>
  

</a>
</h3>

切换菜单。如果它是关闭的，则会被打开。如果它是打开的，则会被关闭。



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
        menuId
        
        
      </td>
      <td>
        
  <code>string</code>
      </td>
      <td>
        <p>可选地通过它的 id 或 side 来获取菜单。<strong class="tag">可选的</strong></p>

        
      </td>
    </tr>
    
  </tbody>
</table>





<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b> 
  <code>Promise</code> <p>在菜单被切换后返回一个 promise </p>


</div>





  <h2 id="sass-variable-header"><a class="anchor" name="sass-variables" href="#sass-variables">Sass Variables</a></h2>
  <div id="sass-variables" ng-controller="SassToggleCtrl">
  <div class="sass-platform-toggle">
    
    <h3 ng-init="setSassPlatform('base')">All</h3>
    
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
        <td><code>$font-size-root</code></td>
        
          <td><code>62.5%</code></td>
        
        <td><p>Font size of the root html</p>
</td>
      </tr>
      
      <tr>
        <td><code>$headings-font-weight</code></td>
        
          <td><code>500</code></td>
        
        <td><p>Font weight of all headings</p>
</td>
      </tr>
      
      <tr>
        <td><code>$headings-line-height</code></td>
        
          <td><code>1.2</code></td>
        
        <td><p>Line height of all headings</p>
</td>
      </tr>
      
      <tr>
        <td><code>$h1-font-size</code></td>
        
          <td><code>2.6rem</code></td>
        
        <td><p>Font size of heading level 1</p>
</td>
      </tr>
      
      <tr>
        <td><code>$h2-font-size</code></td>
        
          <td><code>2.4rem</code></td>
        
        <td><p>Font size of heading level 2</p>
</td>
      </tr>
      
      <tr>
        <td><code>$h3-font-size</code></td>
        
          <td><code>2.2rem</code></td>
        
        <td><p>Font size of heading level 3</p>
</td>
      </tr>
      
      <tr>
        <td><code>$h4-font-size</code></td>
        
          <td><code>2rem</code></td>
        
        <td><p>Font size of heading level 4</p>
</td>
      </tr>
      
      <tr>
        <td><code>$h5-font-size</code></td>
        
          <td><code>1.8rem</code></td>
        
        <td><p>Font size of heading level 5</p>
</td>
      </tr>
      
      <tr>
        <td><code>$h6-font-size</code></td>
        
          <td><code>1.6rem</code></td>
        
        <td><p>Font size of heading level 6</p>
</td>
      </tr>
      
      <tr>
        <td><code>$include-responsive-utilities</code></td>
        
          <td><code>true</code></td>
        
        <td><p>Whether to include all of the responsive utility attributes</p>
</td>
      </tr>
      
      <tr>
        <td><code>$include-text-alignment-utilities</code></td>
        
          <td><code>$include-responsive-utilities</code></td>
        
        <td><p>Whether to include all of the responsive text alignment attributes</p>
</td>
      </tr>
      
      <tr>
        <td><code>$include-text-transform-utilities</code></td>
        
          <td><code>$include-responsive-utilities</code></td>
        
        <td><p>Whether to include all of the responsive text transform attributes</p>
</td>
      </tr>
      
      <tr>
        <td><code>$include-float-element-utilities</code></td>
        
          <td><code>$include-responsive-utilities</code></td>
        
        <td><p>Whether to include all of the responsive float attributes</p>
</td>
      </tr>
      
      <tr>
        <td><code>$screen-breakpoints</code></td>
        
          <td><code>(&#10;  xs: 0,&#10;  sm: 576px,&#10;  md: 768px,&#10;  lg: 992px,&#10;  xl: 1200px&#10;)</code></td>
        
        <td><p>The minimum dimensions at which your layout will change,
adapting to different screen sizes, for use in media queries</p>
</td>
      </tr>
      
    </tbody>
  </table>
  
</div>



<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#menus">Menu Component Docs</a>,
<a href="../Menu">Menu API Docs</a><!-- end content block -->


<!-- end body block -->

