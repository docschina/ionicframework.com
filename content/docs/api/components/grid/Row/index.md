---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "row"
title: "Row"
header_sub_title: "Ionic API Documentation"
doc: "Row"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="row" href="#row"></a>

Row
<h3><code>ion-row, [ion-row]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/grid/row.ts#L0">
改进这篇文档
</a>






<p>Rows 是 <a href="../Grid">grid</a> 系统的水平组件， <a href="../Col">列</a> 。他们确保列正确排列。</p>
<h2 id="row-attributes">行属性</h2>
<p>默认情况下，列将伸展以填充行的整个高度，并在必要时进行换行。有几个属性可以添加到行中用来自定义此行为。</p>


<table>
<thead>
<tr>
<th>属性</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>nowrap</td>
<td>添加 <code>flex-wrap: nowrap</code>。强制所有列在单行内。</td>
</tr>
<tr>
<td>wrap-reverse</td>
<td>添加 <code>flex-wrap: wrap-reverse</code>。列将反转。</td>
</tr>
<tr>
<td>align-items-start</td>
<td>添加 <code>align-items: flex-start</code>。所有列将垂直居顶对齐，除非它们指定了自己的对齐方式。</td>
</tr>
<tr>
<td>align-items-center</td>
<td>添加 <code>align-items: center</code>。所有列将垂直居中对齐，除非它们指定了自己的对齐方式。</td>
</tr>
<tr>
<td>align-items-end</td>
<td>添加 <code>align-items: flex-end</code>。所有列将垂直居底对齐，除非它们指定了自己的对齐方式。</td>
</tr>
<tr>
<td>align-items-stretch</td>
<td>添加 <code>align-items: stretch</code>。所有列将被拉伸以占据该行的整个高度，除非它们指定了自己的对齐方式。</td>
</tr>
<tr>
<td>align-items-baseline</td>
<td>添加 <code>align-items: baseline</code>。所有列将在其基线上垂直对齐，除非它们指定了自己的对齐方式。</td>
</tr>
<tr>
<td>justify-content-start</td>
<td>添加<code>justify-content: start</code>。所有列将水平居始对齐。</td>
</tr>
<tr>
<td>justify-content-center</td>
<td>添加<code>justify-content: center</code>。所有列将水平居中对齐。</td>
</tr>
<tr>
<td>justify-content-end</td>
<td>添加<code>justify-content: end</code>。所有列将水平居尾对齐。</td>
</tr>
<tr>
<td>justify-content-around</td>
<td>添加<code>justify-content: space-around</code>。所有的列将水平对齐，并在其周围有相同的间隔空间。</td>
</tr>
<tr>
<td>justify-content-between</td>
<td>添加<code>justify-content: space-between</code>。所有列都将水平对齐，并在两端都有半尺寸（half-size）空间。</td>
</tr>
</tbody>
</table>




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

