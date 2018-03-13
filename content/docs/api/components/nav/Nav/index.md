---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "nav"
title: "Nav"
header_sub_title: "Ionic API Documentation"
doc: "Nav"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/navigation/www/"
angular_controller: APIDemoCtrl
---









<h1 class="api-title">
<a class="anchor" name="nav" href="#nav"></a>

Nav
<h3><code>ion-nav</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/nav/nav.ts#L14">
改进这篇文档
</a>






<p><code>ion-nav</code> 是 <a href="../../../navigation/NavController/">NavController</a> 的声明性组件。</p>
<p>有关使用 Nav 或 <a href="../../Tabs/Tab/">Tab</a> 等导航控制器的更多信息，请查看 <a href="../../../navigation/NavController/">NavController API 文档</a>。</p>





<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<p>你必须使用 'root' 属性设置一个根页面，以便你创建的任意 Nav 初始化加载：</p>

<pre><code class="lang-ts">import { Component } from &#39;@angular/core&#39;;
import { GettingStartedPage } from &#39;./getting-started&#39;;

@Component({
  template: `&lt;ion-nav [root]=&quot;root&quot;&gt;&lt;/ion-nav&gt;`
})
class MyApp {
  root = GettingStartedPage;

  constructor(){
  }
}
</code></pre>




<!-- @property tags -->



<!-- instance methods on the class -->

<h2><a class="anchor" name="instance-members" href="#instance-members">实例成员</a></h2>

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











<div id="goToRoot"></div>

<h3>
<a class="anchor" name="goToRoot" href="#goToRoot">
<code>goToRoot()</code>


</a>
</h3>











<div id="initPane"></div>

<h3>
<a class="anchor" name="initPane" href="#initPane">
<code>initPane()</code>


</a>
</h3>











<div id="ngAfterViewInit"></div>

<h3>
<a class="anchor" name="ngAfterViewInit" href="#ngAfterViewInit">
<code>ngAfterViewInit()</code>


</a>
</h3>











<div id="paneChanged"></div>

<h3>
<a class="anchor" name="paneChanged" href="#paneChanged">
<code>paneChanged()</code>


</a>
</h3>










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
      <td>name</td>
      <td><code>string</code></td>
      <td><p>导航元素的唯一名称</p>
</td>
    </tr>

    <tr>
      <td>root</td>
      <td><code>Page</code></td>
      <td><p>加载页面组件作为此导航中的根页面。</p>
</td>
    </tr>

    <tr>
      <td>rootParams</td>
      <td><code>object</code></td>
      <td><p>传递给此导航的根页面任意的 nav-params。</p>
</td>
    </tr>

  </tbody>
</table>




<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#navigation">Navigation Component Docs</a><!-- end content block -->


<!-- end body block -->

