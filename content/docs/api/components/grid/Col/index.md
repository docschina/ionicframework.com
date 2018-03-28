---
layout: "fluid/docs_base"
version: "3.9.2"
versionHref: "/docs"
path: ""
category: api
id: "col"
title: "Col"
header_sub_title: "Ionic API Documentation"
doc: "Col"
docType: "class"

---









<h1 class="api-title">
<a class="anchor" name="col" href="#col"></a>

Col
<h3><code>ion-col, [ion-col]</code></h3>






</h1>

<a class="improve-v2-docs" href="http://github.com/ionic-team/ionic/edit/v3/src/components/grid/col.ts#L0">
改进这篇文档
</a>






<p>列（Columns ）是 <a href="../Grid">网格（grid）</a> 系统的基本组成部分，并且置身于 <a href="../Row">行（row）</a> 中。他们会通过扩张来使所在的行变满。网格内的所有内容都应该放在列里面。</p>
<h2 id="column-attributes">列属性</h2>
<p>默认情况下，列将延伸填充行的整个高度。
有几个属性可以添加到列中来自定义此行为。</p>

<table>
<thead>
<tr>
<th>属性</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr>
<td>align-self-start</td>
<td>添加<code>align-self: flex-start</code>。该列将垂直居顶对齐。</td>
</tr>
<tr>
<td>align-self-center</td>
<td>添加<code>align-self: center</code>。该列将垂直居中对齐。</td>
</tr>
<tr>
<td>align-self-end</td>
<td>添加<code>align-self: flex-end</code>。该列将垂直居底对齐。</td>
</tr>
<tr>
<td>align-self-stretch</td>
<td>添加<code>align-self: stretch</code>。该列将被拉伸从而占据所在行的整个高度。</td>
</tr>
<tr>
<td>align-self-baseline</td>
<td>添加<code>align-self: baseline</code>。该列将垂直对齐其基线。</td>
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

