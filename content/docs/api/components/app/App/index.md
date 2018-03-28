---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "app"
title: "App"
header_sub_title: "Ionic API Documentation"
doc: "App"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="app" href="#app"></a>

App





</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/app/app.ts#L16">
改进这篇文档
</a>






<p>App 是 Ionic 的通用类，用于获取当前应用各个方面的信息。</p>




<!-- @usage tag -->


<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

<div id="getActiveNav"></div>

<h3>
<a class="anchor" name="getActiveNav" href="#getActiveNav">
<code>getActiveNav()</code>


</a>
</h3>








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>NavController</code> <p>从列表中返回第一个激活的 Nav Controller。此方法已弃用。</p>


</div>




<div id="getActiveNavContainers"></div>

<h3>
<a class="anchor" name="getActiveNavContainers" href="#getActiveNavContainers">
<code>getActiveNavContainers()</code>


</a>
</h3>











<div id="getActiveNavs"></div>

<h3>
<a class="anchor" name="getActiveNavs" href="#getActiveNavs">
<code>getActiveNavs()</code>


</a>
</h3>








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>NavController[]</code> <p>返回激活的 NavControllers。如果我们需要访问最高阶层的导航控制器，在外部视图和处理函数（如 <code>registerBackButtonAction()</code> ）上使用此方法。</p>


</div>




<div id="getNavByIdOrName"></div>

<h3>
<a class="anchor" name="getNavByIdOrName" href="#getNavByIdOrName">
<code>getNavByIdOrName()</code>


</a>
</h3>











<div id="getRootNav"></div>

<h3>
<a class="anchor" name="getRootNav" href="#getRootNav">
<code>getRootNav()</code>


</a>
</h3>











<div id="getRootNavById"></div>

<h3>
<a class="anchor" name="getRootNavById" href="#getRootNavById">
<code>getRootNavById()</code>


</a>
</h3>








<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>NavController</code> <p>返回根导航控制器。</p>


</div>




<div id="getRootNavs"></div>

<h3>
<a class="anchor" name="getRootNavs" href="#getRootNavs">
<code>getRootNavs()</code>


</a>
</h3>











<div id="isScrolling"></div>

<h3>
<a class="anchor" name="isScrolling" href="#isScrolling">
<code>isScrolling()</code>


</a>
</h3>

应用是否正在滚动或不滚动的布尔值。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>boolean</code> <p>返回 true 或 false 。</p>


</div>




<div id="setTitle"></div>

<h3>
<a class="anchor" name="setTitle" href="#setTitle">
<code>setTitle(val)</code>


</a>
</h3>

设置文档标题。


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
        val


      </td>
      <td>

  <code>string</code>
      </td>
      <td>
        <p>设置文档标题的值。</p>


      </td>
    </tr>

  </tbody>
</table>








<div id="viewDidEnter"></div>

<h3>
<a class="anchor" name="viewDidEnter" href="#viewDidEnter">
<code>viewDidEnter</code>


</a>
</h3>

在应用中进入任意视图后发出的可观察对象。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个可观察对象</p>


</div>




<div id="viewDidLeave"></div>

<h3>
<a class="anchor" name="viewDidLeave" href="#viewDidLeave">
<code>viewDidLeave</code>


</a>
</h3>

在应用中退出任意视图后发出的可观察对象。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个可观察对象</p>


</div>




<div id="viewDidLoad"></div>

<h3>
<a class="anchor" name="viewDidLoad" href="#viewDidLoad">
<code>viewDidLoad</code>


</a>
</h3>

在应用中加载任意视图后发出的可观察对象。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个可观察对象</p>


</div>




<div id="viewWillEnter"></div>

<h3>
<a class="anchor" name="viewWillEnter" href="#viewWillEnter">
<code>viewWillEnter</code>


</a>
</h3>

在应用中加载任意视图前发出的可观察对象。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个可观察对象</p>


</div>




<div id="viewWillLeave"></div>

<h3>
<a class="anchor" name="viewWillLeave" href="#viewWillLeave">
<code>viewWillLeave</code>


</a>
</h3>

在应用中退出任意视图前发出的可观察对象。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个可观察对象</p>


</div>




<div id="viewWillUnload"></div>

<h3>
<a class="anchor" name="viewWillUnload" href="#viewWillUnload">
<code>viewWillUnload</code>


</a>
</h3>

在应用中未加载任意视图前发出的可观察对象。






<div class="return-value">
<i class="icon ion-arrow-return-left"></i>
<b>返回：</b>
  <code>Observable</code> <p>返回一个可观察对象</p>


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



<!-- related link --><!-- end content block -->


<!-- end body block -->

