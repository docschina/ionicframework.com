---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "icon"
title: "Icon"
header_sub_title: "Ionic API Documentation"
doc: "Icon"
docType: "class"
show_preview_device: true
preview_device_url: "/docs/demos/src/icon/www/"
angular_controller: APIDemoCtrl 
---









<h1 class="api-title">
<a class="anchor" name="icon" href="#icon"></a>

Icon
<h3><code>ion-icon</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/master/src/components/icon/icon.ts#L4">
Improve this doc
</a>






<p>Icons 可以单独使用，也可以在多个 Ionic 组件中使用。有关可用 Ionic 的完整列表，请查看 <a href="../../../../ionicons">Ionicons 文档</a>。</p>
<p>Ionicons 的一个功能是在设置图标名称时，渲染的实际图标可能会根据应用程序的运行模式而略有变化。例如，通过设置 <code>alarm</code> 的图标名称，在 iOS 上，图标将自动应用 <code>ios-alarm</code>，在 Material Design 上将自动应用 <code>md-alarm</code>。这允许开发者只标记一次，而 Ionic 就可以根据模式应用合适的图标。</p>











<!-- @usage tag -->

<h2><a class="anchor" name="usage" href="#usage">用法</a></h2>

<pre><code class="lang-html">&lt;!-- 根据模式自动使用正确的&quot;star&quot 图标 --&gt;
&lt;ion-icon name=&quot;star&quot;&gt;&lt;/ion-icon&gt;

&lt;!-- 明确设置每种模式的图标 --&gt;
&lt;ion-icon ios=&quot;ios-home&quot; md=&quot;md-home&quot;&gt;&lt;/ion-icon&gt;

&lt;!-- 无论使用什么模式，总是使用相同的图标 --&gt;
&lt;ion-icon name=&quot;ios-clock&quot;&gt;&lt;/ion-icon&gt;
&lt;ion-icon name=&quot;logo-twitter&quot;&gt;&lt;/ion-icon&gt;
</code></pre>




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
      <td>ios</td>
      <td><code>string</code></td>
      <td><p>指定在 <code>ios</code> 模式下使用哪个图标。</p>
</td>
    </tr>
    
    <tr>
      <td>isActive</td>
      <td><code>boolean</code></td>
      <td><p>如果为 true，则图标的样式为 <code>isActive</code> 的样式。激活的图标被填充，而未激活的图标是图标的轮廓。 <code>isActive</code> 属性主要由 tabbar 使用。只影响 <code>ios</code> 图标。</p>


</td>
    </tr>
    
    <tr>
      <td>md</td>
      <td><code>string</code></td>
      <td><p>指定在 <code>md</code> 模式下使用哪个图标。</p>
</td>
    </tr>
    
    <tr>
      <td>name</td>
      <td><code>string</code></td>
      <td><p> 指定使用哪个图标。根据模式使用合适的图标。欲了解更多信息，请参阅 <a href="/docs/ionicons/">Ionicons</a>。</p>

</td>
    </tr>
    
  </tbody>
</table>




<!-- related link -->

<h2><a class="anchor" name="related" href="#related">Related</a></h2>

<a href="/docs/components#icons">Icon Component Docs</a><!-- end content block -->


<!-- end body block -->

