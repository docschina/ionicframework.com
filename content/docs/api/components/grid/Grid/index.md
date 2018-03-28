---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "grid"
title: "Grid"
header_sub_title: "Ionic API Documentation"
doc: "Grid"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="grid" href="#grid"></a>

Grid
<h3><code>ion-grid, [ion-grid]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/grid/grid.ts#L0">
改进这篇文档
</a>






<p>grid 是用于构建自定义布局的，功能强大的，移动端优先的弹性布局系统。它深受 <a href="http://v4-alpha.getbootstrap.com/layout/grid/">Bootstrap 网格系统</a> 的影响。</p>
<p> grid 由三个单元组成 — 一个网格，一个或多个行和一个或多个列。列会延伸来填充所在的行，并调整大小以适合其他的列。它是基于根据不同屏幕大小的不同断点的12列布局。使用 Sass 可以完全自定义列数和断点数。</p>




<ul>
<li><a href="#how-it-works">运行原理</a></li>
<li><a href="#grid-size">Grid 尺寸</a></li>
<li><a href="#grid-attributes">Grid 属性</a></li>
<li><a href="#default-breakpoints">默认断点</a></li>
<li><a href="#auto-layout-columns">自动布局的列</a><ul>
<li><a href="#equal-width">等宽</a></li>
<li><a href="#setting-one-column-width">设置一个列宽</a></li>
<li><a href="#variable-width">可变宽度</a></li>
</ul>
</li>
<li><a href="#responsive-attributes">响应式属性</a><ul>
<li><a href="#all-breakpoints">所有断点</a></li>
<li><a href="#stacked-to-horizontal">在水平堆叠</a></li>
</ul>
</li>
<li><a href="#reordering">重新排列</a><ul>
<li><a href="#offsetting-columns">偏移列</a></li>
<li><a href="#push-and-pull">Push 和 pull</a></li>
</ul>
</li>
<li><a href="#alignment">对齐</a><ul>
<li><a href="#vertical-alignment">垂直对齐</a></li>
<li><a href="#horizontal-alignment">水平对齐</a></li>
</ul>
</li>
<li><a href="#customizing-the-grid">定制化网格</a><ul>
<li><a href="#number-of-columns-and-padding">列数和填充</a></li>
<li><a href="#grid-tiers">网格层</a></li>
</ul>
</li>
</ul>
<h2 id="how-it-works">运行原理</h2>
<p> grid 是由任意数量的行和列组成的移动端优先系统。它使用弹性盒子（flexbox）构建，非常灵活。组成 grid 的组件可以写成一个元素（例如， <code>&lt;ion-grid&gt;</code>）或者作为属性添加到任何元素（例如， <code>&lt;div ion-row&gt;</code>）。</p>
<p>以下是它的运行原理：</p>



<ul>
<li>Grids 充当所有行和列的容器。Grids 会占据所在容器的整个宽度，但添加 <code>fixed</code> 属性将会指定每个屏幕大小的宽度，请参阅下面的<a href="#grid-size">网格尺寸</a>。</li>
<li>行是水平的列的集合，并将列排列适当。</li>
<li>内容应放置在列中，并且只有列可以是行的直接子节点。</li>
<li>没有指定宽度的 Grid 列将自动拥有相同的宽度。例如， <code>col-sm</code> 的四个实例每个都会自动设置为 small 断点25％的宽度。</li>
<li>列属性表明在每行默认为12的值之外使用的列数。因此，可以添加 <code>col-4</code> 以便具有三个等宽列。</li>
<li>列宽设置为百分比，所以它们始终是相对于其父元素的尺寸的流体。</li>
<li>列可以在单个列之间有 padding ，然而也可以通过在网格中添加 <code>no-padding</code> 来从网格和列中移除 padding。</li>
<li>默认情况下有五个网格层，每个响应式断点都有一个： all 断点（extra small），small，medium，large 和 extra large。</li>
<li>网格层基于最小宽度，这意味着它们适用于所在的层级和所有大于它的层级（例如， <code>col-sm-4</code> 适用于 small, medium, large, 和 extra large 设备）。</li>
<li>Grids 可以通过 Sass 变量轻松定制。请参阅<a href="#customizing-the-grid">自定义网格</a>。</li>






</ul>
<p>在使用 Ionic 创建问题之前，应该检查一些 <a href="https://github.com/philipwalton/flexbugs">已知的与 flexbox 有关的 bug</a>。</p>
<h2 id="grid-size">Grid 尺寸</h2>
<p>默认情况下， grid 将占用100％的宽度。要根据屏幕大小设置最大宽度，请添加 <code>fixed</code> 属性。每个断点的 grid 的最大宽度在 <code>$grid-max-widths</code> Sass 变量中定义。有关更多信息，请参阅<a href="#customizing-the-grid">自定义网格</a>。</p>




<table>
<thead>
<tr>
<th>名称</th>
<th>值</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>xs</td>
<td>auto</td>
<td>不为 xs 屏幕设置网格宽度</td>
</tr>
<tr>
<td>sm</td>
<td>540px</td>
<td>当（最小宽度：576px）时，设置网格宽度为540px</td>
</tr>
<tr>
<td>md</td>
<td>720px</td>
<td>当（最小宽度：768px）时，将网格宽度设置为720px</td>
</tr>
<tr>
<td>lg</td>
<td>960px</td>
<td>当（最小宽度：992px）时，将网格宽度设置为960px</td>
</tr>
<tr>
<td>xl</td>
<td>1140px</td>
<td>当（最小宽度：1200px）时，将网格宽度设置为1140px</td>
</tr>
</tbody>
</table>
<h2 id="grid-attributes">Grid 属性</h2>
<p> grid 占用全部宽度，并根据屏幕大小添加 padding。有两个属性可用于调整此行为。</p>

<table>
<thead>
<tr>
<th>属性</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>no-padding</td>
<td>从 grid 和是直接子节点的列中移除 padding。</td>
</tr>
<tr>
<td>fixed</td>
<td>根据屏幕尺寸设置最大宽度。</td>
</tr>
</tbody>
</table>
<h2 id="default-breakpoints">默认断点</h2>
<p>默认断点由 <code>$grid-breakpoints</code> Sass 变量定义。它可以被自定义为不同的断点值，重命名和添加/删除断点。有关更多信息，请参阅 <a href="#customizing-the-grid">自定义网格</a>。</p>


<table>
<thead>
<tr>
<th>名称</th>
<th>值</th>
<th>宽度前缀</th>
<th>偏移量前缀</th>
<th>Push 前缀</th>
<th>Pull 前缀</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>xs</td>
<td>0</td>
<td><code>col-</code></td>
<td><code>offset-</code></td>
<td><code>push-</code></td>
<td><code>pull-</code></td>
<td>当（最小宽度：0）设置列</td>
</tr>
<tr>
<td>sm</td>
<td>576px</td>
<td><code>col-sm-</code></td>
<td><code>offset-sm-</code></td>
<td><code>push-sm-</code></td>
<td><code>pull-sm-</code></td>
<td>当（最小宽度：576px）设置列</td>
</tr>
<tr>
<td>md</td>
<td>768px</td>
<td><code>col-md-</code></td>
<td><code>offset-md-</code></td>
<td><code>push-md-</code></td>
<td><code>pull-md-</code></td>
<td>当（最小宽度：768px）设置列</td>
</tr>
<tr>
<td>lg</td>
<td>992px</td>
<td><code>col-lg-</code></td>
<td><code>offset-lg-</code></td>
<td><code>push-lg-</code></td>
<td><code>pull-lg-</code></td>
<td>当（最小宽度：992px）设置列</td>
</tr>
<tr>
<td>xl</td>
<td>1200px</td>
<td><code>col-xl-</code></td>
<td><code>offset-xl-</code></td>
<td><code>push-xl-</code></td>
<td><code>pull-xl-</code></td>
<td>当（最小宽度：1200px）设置列</td>
</tr>
</tbody>
</table>
<p><em>注意：第一个断点必须将值设置为0，
并且所有断点值必须升序排列。</em></p>
<h2 id="auto-layout-columns">自动布局的列</h2>
<h3><a class="anchor" name="equal-width" href="#equal-width">等宽</a></h3>


<p>默认情况下，对于所有设备和屏幕大小，列的宽度将相等。</p>
<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
  &lt;ion-row&gt;
    &lt;ion-col&gt;
      1 of 3
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      2 of 3
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 3
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h3><a class="anchor" name="setting-one-column-width" href="#setting-one-column-width">设置一个列宽</a></h3>


<p>设置一列的宽度，其他列将自动调整其大小。这可以使用我们预定义的网格属性来完成。在下面的示例中，无论中心列的宽度如何，其他列都将调整大小。</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col&gt;
      1 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-8&gt;
      2 of 3 (wider)
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 3
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
  &lt;ion-row&gt;
    &lt;ion-col&gt;
      1 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-6&gt;
      2 of 3 (wider)
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 3
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h3><a class="anchor" name="variable-width" href="#variable-width">可变宽度</a></h3>


<p>使用 <code>col-{breakpoint}-auto</code> 属性，该列可以根据其内容的自然宽度自行调整大小。这对使用像素设置的列宽非常有用。可变宽度列旁边的列将调整大小以填充行。</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col&gt;
      1 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-auto&gt;
      Variable width content
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 3
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
  &lt;ion-row&gt;
    &lt;ion-col&gt;
      1 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      2 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-auto&gt;
      &lt;ion-input placeholder=&quot;Variable width input&quot;&gt;&lt;/ion-input&gt;
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      4 of 4
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h2 id="responsive-attributes">响应式属性</h2>
<h3><a class="anchor" name="all-breakpoints" href="#all-breakpoints">所有断点</a></h3>


<p>要为所有设备和屏幕自定义列的宽度，请添加 <code>col-*</code> 属性。这些属性告诉列从可用的列中占用 <code>*</code> 列。</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col col-4&gt;
      1 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-2&gt;
      2 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-2&gt;
      3 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-4&gt;
      4 of 4
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h3><a class="anchor" name="-stacked-to-horizontal" href="#-stacked-to-horizontal"> 在水平堆叠</a></h3>


<p>使用宽度和断点属性的组合来创建一个网格，该网格在 small 屏幕上是水平的，在 extra small 屏幕上会堆叠起来。</p>

<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col col-12 col-sm&gt;
      1 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-12 col-sm&gt;
      2 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-12 col-sm&gt;
      3 of 4
    &lt;/ion-col&gt;
    &lt;ion-col col-12 col-sm&gt;
      4 of 4
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h2 id="reordering">重新排列</h2>
<h3><a class="anchor" name="offsetting-columns" href="#offsetting-columns">偏移列</a></h3>


<p>通过添加 <code>offset-*</code> 属性将列移动到右侧。这些属性通过 <code>*</code> 列增加了列的 margin 起点 。例如，在下面的网格中，最后一列将偏移3列并占用3列：</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col col-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3 offset-3&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<p>也可以根据屏幕断点添加偏移量。
下面是一个网格的例子，其中最后一列将被 <code>md</code> 屏幕偏移3列，到这行的最后：</p>
<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col col-md-3&gt;
      1 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-md-3&gt;
      2 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-md-3 offset-md-3&gt;
      3 of 3
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h3><a class="anchor" name="push-and-pull" href="#push-and-pull">Push 和 pull</a></h3>


<p>通过添加 <code>push-*</code> 和 <code>pull-*</code> 属性使列重新排列。这些属性通过 <code>*</code> 列调整列的 <code>left</code> 侧和 <code>right</code> 侧，以便重新排列此列。例如，在下面的网格中，<code>第一列</code> 描述的列实际上是最后一列， <code>第二列</code> 将变成第一列。</p>



<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col col-9 push-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3 pull-9&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<p>Push 和 pull 也可以基于屏幕断点添加。在以下示例中， <code>第三列</code> 描述的列实际上是 <code>md</code> 屏幕的第一列：</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col col-md-6 push-md-3&gt;
      1 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-md-3 push-md-3&gt;
      2 of 3
    &lt;/ion-col&gt;
    &lt;ion-col col-md-3 pull-md-9&gt;
      3 of 3
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h2 id="alignment">对齐</h2>
<h3><a class="anchor" name="vertical-alignment" href="#vertical-alignment">垂直对齐</a></h3>


<p>通过向行（row）添加不同的属性，所有列可以在行内垂直对齐。有关可用属性的列表，请参阅<a href="../Row#row-attributes">行属性</a>。</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row align-items-start&gt;
    &lt;ion-col&gt;
      1 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      2 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      4 of 4 &lt;br&gt;#&lt;br&gt;#&lt;br&gt;#
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;

  &lt;ion-row align-items-center&gt;
    &lt;ion-col&gt;
      1 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      2 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      4 of 4 &lt;br&gt;#&lt;br&gt;#&lt;br&gt;#
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;

  &lt;ion-row align-items-end&gt;
    &lt;ion-col&gt;
      1 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      2 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      3 of 4
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      4 of 4 &lt;br&gt;#&lt;br&gt;#&lt;br&gt;#
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<p>通过将对齐（ alignment ）属性直接添加到列中，列也可以与其他列对齐。有关可用属性的列表，请参阅<a href="../Row#row-attributes">行属性</a>。</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row&gt;
    &lt;ion-col align-self-start&gt;
      &lt;div&gt;
        1 of 4
      &lt;/div&gt;
    &lt;/ion-col&gt;
    &lt;ion-col align-self-center&gt;
      &lt;div&gt;
        2 of 4
      &lt;/div&gt;
    &lt;/ion-col&gt;
    &lt;ion-col align-self-end&gt;
      &lt;div&gt;
        3 of 4
      &lt;/div&gt;
    &lt;/ion-col&gt;
    &lt;ion-col&gt;
      &lt;div&gt;
        4 of 4 &lt;br&gt;#&lt;br&gt;#&lt;br&gt;#
      &lt;/div&gt;
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h3><a class="anchor" name="horizontal-alignment" href="#horizontal-alignment">水平对齐</a></h3>


<p>通过向行（row）添加不同的属性，所有列可以在行内水平对齐。有关可用属性的列表，请参阅<a href="../Row#row-attributes">行属性</a>。</p>


<pre><code>&lt;ion-grid&gt;
  &lt;ion-row justify-content-start&gt;
    &lt;ion-col col-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;

  &lt;ion-row justify-content-center&gt;
    &lt;ion-col col-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;

  &lt;ion-row justify-content-end&gt;
    &lt;ion-col col-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;

  &lt;ion-row justify-content-around&gt;
    &lt;ion-col col-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;

  &lt;ion-row justify-content-between&gt;
    &lt;ion-col col-3&gt;
      1 of 2
    &lt;/ion-col&gt;
    &lt;ion-col col-3&gt;
      2 of 2
    &lt;/ion-col&gt;
  &lt;/ion-row&gt;
&lt;/ion-grid&gt;
</code></pre>
<h2 id="customizing-the-grid">定制化网格</h2>
<p>使用我们内置的网格 Sass 变量和地图，
可以完全自定义预先确定的网格属性。
更改断点的数量，媒体查询值，列数等等。</p>
<h3><a class="anchor" name="number-of-columns-and-padding" href="#number-of-columns-and-padding">列数和填充</a></h3>


<p>网格列的数量和 padding 可以通过 Sass 变量修改。 <code>$grid-columns</code> 用于生成每个单独列的宽度（以百分比表示）。 <code>$grid-padding-width</code> 用于网格上的 padding，而 <code>$grid-padding-widths</code> 允许在 <code>padding-left</code> 和 <code>padding-right</code> 以及 <code>padding-top</code> 和 <code>padding-bottom</code> 之间均匀划分的特定断点的宽度网格和列。</p>




<pre><code>$grid-columns:               12 !default;

$grid-padding-width:         10px !default;

$grid-padding-widths: (
  xs: $grid-padding-width,
  sm: $grid-padding-width,
  md: $grid-padding-width,
  lg: $grid-padding-width,
  xl: $grid-padding-width
) !default;
</code></pre>
<h3><a class="anchor" name="grid-tiers" href="#grid-tiers">网格层</a></h3>


<p>要定制断点及其值，请覆盖 <code>$grid-max-widths</code> 和 <code>$grid-max-widths</code> 的值。例如，要仅使用3个断点，可以写下以下内容：</p>


<pre><code>$grid-breakpoints: (
  sm: 0,
  md: 768px,
  lg: 1024px
);

$grid-max-widths: (
  sm: 420px,
  md: 720px,
  lg: 960px
);
</code></pre>




<!-- @usage tag -->


<!-- @property tags -->



<!-- instance methods on the class -->


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
        <td><code>$grid-breakpoints</code></td>

          <td><code>(&#10;  xs: 0,&#10;  sm: 576px,&#10;  md: 768px,&#10;  lg: 992px,&#10;  xl: 1200px&#10;)</code></td>

        <td><p>The minimum dimensions at which your layout will change,
adapting to different screen sizes, for use in media queries</p>
</td>
      </tr>

      <tr>
        <td><code>$grid-max-widths</code></td>

          <td><code>(&#10;  sm: 540px,&#10;  md: 720px,&#10;  lg: 960px,&#10;  xl: 1140px&#10;)</code></td>

        <td><p>Maximum width of the grid for different screen sizes</p>
</td>
      </tr>

      <tr>
        <td><code>$grid-columns</code></td>

          <td><code>12</code></td>

        <td><p>Number of columns for the grid</p>
</td>
      </tr>

      <tr>
        <td><code>$grid-padding-width</code></td>

          <td><code>10px</code></td>

        <td><p>Total width of the padding for the grid</p>
</td>
      </tr>

      <tr>
        <td><code>$grid-padding-widths</code></td>

          <td><code>(&#10;  xs: $grid-padding-width,&#10;  sm: $grid-padding-width,&#10;  md: $grid-padding-width,&#10;  lg: $grid-padding-width,&#10;  xl: $grid-padding-width&#10;)</code></td>

        <td><p>Padding for the columns for different screen sizes</p>
</td>
      </tr>

    </tbody>
  </table>

</div>



<!-- related link --><!-- end content block -->


<!-- end body block -->

