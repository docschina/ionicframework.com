---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "img"
title: "Img"
header_sub_title: "Ionic API Documentation"
doc: "Img"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="img" href="#img"></a>

Img
<h3><code>ion-img</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/img/img.ts#L6">
改进这篇文档
</a>






<p>两个最大的滚屏卡顿罪魁祸首是：启动一个新的HTTP请求和渲染图像。这是 <code>ion-img</code> 被创建的两个主要 的原因。标准的 HTML <code>img</code> 元素通常是这些问题的主要来源，更糟糕的是应用程序没有对每个 <code>img</code> 元素的请求和渲染进行深入的控制。</p>





<p> <code>ion-img</code> 组件与标准 <code>img</code> 元素类似，但它也增加了一些功能以改进性能。其功能包括只加载可见的图像，使用 web workers 进行 HTTP 请求，防止在滚动和内存缓存时出现乱码。</p>








<p>请注意，与标准 <code>img</code> 元素相比， <code>ion-img</code> 还具有更多的限制。一个很好的规则是，如果在页面上只显示少量图像，那么标准 <code>img</code> 可能是最好的。但是，如果一个页面在可滚动区域内有数百甚至数千个图像的可能性，那么 <code>ion-img</code> 会更适合这项工作。</p>
<blockquote>
<p>注意： <code>ion-img</code> 仅用于 <a href="/docs/api/components/virtual-scroll/VirtualScroll/">virtual-scroll</a> 内部。</p>
</blockquote>
<h3><a class="anchor" name="lazy-loading" href="#lazy-loading">懒加载</a></h3>


<p>懒加载图像是指只加载用户视口中实际可见的图像。
这也意味着在初始加载时不可见的图像将不会被下载或渲染。
接下来，随着用户滚动，
每个可见的图像才会被请求然后按需呈现。</p>
<p>这种方法的好处是，
不必要的和资源密集型的 HTTP 请求不会被启动，
宝贵的带宽不会被浪费，并且这使得浏览器可以释放资源，
这些资源会被浪费在根本不可见的图像上。
例如，动画 GIF 会造成巨大的性能消耗，
但是，通过 <code>ion-img</code> ，
该应用程序可以将资源专用于可见图像。
但是，如果上面列出的问题在你的应用程序中不存在，
那么标准 <code>img</code> 元素可能是最好的。</p>
<h3><a class="anchor" name="image-dimensions" href="#image-dimensions">图像尺寸</a></h3>


<p>通过预先提供图像尺寸，Ionic 能够准确地确定图像在视口内的位置，这有助于仅延迟加载可视图像。图像尺寸可以通过设置为属性，内联样式或外部样式来设置。使用哪种设置尺寸的方法并不重要，重要的是每个 <code>ion-img</code> 都得有一个确切的尺寸。</p>








<p>例如，默认情况下， <code>&lt;ion-avatar&gt;</code> 和 <code>&lt;ion-thumbnail&gt;</code>放置在 <code>&lt;ion-item&gt;</code> 中时，就已经有精确的尺寸了。通过给每个图像一个确切的尺寸，这将进一步锁定每个 <code>ion-item</code> 的大小，这有助于提高滚动性能。</p>
<pre><code class="lang-html">&lt;!-- 使用属性设置尺寸 --&gt;
&lt;ion-img width=&quot;80&quot; height=&quot;80&quot; src=&quot;...&quot;&gt;&lt;/ion-img&gt;

&lt;!-- 使用输入属性设置尺寸 --&gt;
&lt;ion-img [width]=&quot;imgWidth&quot; [height]=&quot;imgHeight&quot; src=&quot;...&quot;&gt;&lt;/ion-img&gt;

&lt;!-- 使用内联样式设置尺寸 --&gt;
&lt;ion-img style=&quot;width: 80px; height: 80px;&quot; src=&quot;...&quot;&gt;&lt;/ion-img&gt;
</code></pre>
<p>此外，每个 <code>ion-img</code> 都使用<code>object-fit: cover</code> CSS 属性。
这意味着实际呈现的图像会把自身置于其容器内。
或者要真正获得细节的话：
图像的尺寸可以保持其纵横比，
同时填充容器元素的整个内容框。
它的实际物体尺寸会被解析为对元素的使用宽度和高度的有效约束。</p>
<h3><a class="anchor" name="future-optimizations" href="#future-optimizations">未来的优化</a></h3>


<p>未来的目标是在 web workers 中放置图像请求，并将内存中的图像缓存为数据。这种方法已被证明是有效的，但是目前我们正在研究 Cordova ，目前还存在一些局限性。</p>







<!-- @usage tag -->


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
      <td>alt</td>
      <td><code>string</code></td>
      <td><p>设置分配给内部 <code>img</code> 元素的 <code>alt</code> 属性。</p>

</td>
    </tr>

    <tr>
      <td>bounds</td>
      <td><code>any</code></td>
      <td><p>设置元素相对于视口的边界矩形（bounding rectangle）。当使用 <code>VirtualScroll</code>时，每个虚拟物体都应该将其边界传递给每个 <code>ion-img</code>。传入的数据对象应包含 <code>top</code> 和 <code>bottom</code> 属性。</p>


</td>
    </tr>

    <tr>
      <td>cache</td>
      <td><code>boolean</code></td>
      <td><p>图像成功下载后，可以将其缓存在内存中。这对于 <code>VirtualScroll</code> 非常有用，它允许图像响应被缓存，而不是渲染，直到滚动完成后才允许更平滑的滚动。</p>



</td>
    </tr>

    <tr>
      <td>height</td>
      <td><code>string</code></td>
      <td><p>图像高度。如果未设置此属性，则仍旧使用 CSS，设置维度很重要。如果维度只是一个数字，它将假定 <code>px</code> 单位。</p>


</td>
    </tr>

    <tr>
      <td>src</td>
      <td><code>string</code></td>
      <td><p>图像的来源。</p>
</td>
    </tr>

    <tr>
      <td>width</td>
      <td><code>string</code></td>
      <td><p>图像宽度。如果未设置此属性，则仍然使用 CSS， 设置维度很重要。如果维度只是一个数字，它将假定 <code>px</code> 单位。</p>


</td>
    </tr>

  </tbody>
</table>


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
        <td><code>$img-placeholder-background</code></td>

          <td><code>#eee</code></td>

        <td><p>Color of the image when it hasn&#39;t fully loaded yet</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link --><!-- end content block -->


<!-- end body block -->

